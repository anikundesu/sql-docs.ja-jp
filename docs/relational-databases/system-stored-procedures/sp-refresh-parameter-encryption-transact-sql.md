---
title: "sp_refresh_parameter_encryption (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/11/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sp_refresh_parameter_encryption
- sp_refresh_parameter_encryption_TSQL
- sys.sp_refresh_parameter_encryption
- sys.sp_refresh_parameter_encryption_TSQL
helpviewer_keywords:
- sp_refresh_parameter_encryption
- Always Encrypted, sp_refresh_parameter_encryption
ms.assetid: 00b44baf-fcf0-4095-aabe-49fa87e77316
caps.latest.revision: "3"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 31dd44920c1bc814985cd0391f52e035621de89f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sprefreshparameterencryption-transact-sql"></a>sp_refresh_parameter_encryption (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

指定された非スキーマ バインド ストアド プロシージャ、ユーザー定義関数、ビュー、DML トリガー、データベース レベルの DDL トリガー、または現在のデータベース内のサーバー レベルの DDL トリガーのパラメーターの場合は常に暗号化メタデータを更新します。 

 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
sys.sp_refresh_parameter_encryption [ @name = ] 'module_name' 
    [ , [ @namespace = ] '<class>' ]
[ ; ]

<class> ::=
{ DATABASE_DDL_TRIGGER | SERVER_DDL_TRIGGER }
```

## <a name="arguments"></a>引数

[  **@name =** ] **'***モジュール名***'**   
ストアド プロシージャ、ユーザー定義関数、ビュー、DML トリガー、データベース レベルの DDL トリガー、またはサーバー レベルの DDL トリガーの名前を指定します。 *モジュール名*共通言語ランタイム (CLR) ストアド プロシージャまたは CLR 関数にすることはできません。 *モジュール名*スキーマ バインドをすることはできません。 *モジュール名*は`nvarchar`、既定値はありません。 *モジュール名*マルチパートの識別子を指定できますが、現在のデータベース内のオブジェクトに参照できるのみです。

[  **@namespace =** ] **'** < クラス > **'**   
指定されたモジュールのクラスです。 ときに*モジュール名*、DDL トリガーは、`<class>`が必要です。 `<class>`is `nvarchar(20)`. 有効な入力は`DATABASE_DDL_TRIGGER`と`SERVER_DDL_TRIGGER`です。    

## <a name="return-code-values"></a>リターン コードの値  

0 (成功) または 0 以外の数値 (失敗)


## <a name="remarks"></a>解説

場合、モジュールのパラメーターの暗号化メタデータが古く、なることができます。   
* 暗号化プロパティ テーブルの列のモジュールの参照が更新されました。 たとえば、列は削除されました。 し、同じ名前が、異なる暗号化の種類、暗号化キー暗号化アルゴリズムと新しい列が追加されました。  
* モジュールは、古いパラメーター暗号化メタデータを持つ別のモジュールを参照します。  

テーブルの暗号化プロパティが変更されると、`sp_refresh_parameter_encryption`直接的または間接的には、テーブルを参照するすべてのモジュールを実行する必要があります。 このストアド プロシージャは、その呼び出し元に移動する前にユーザーが内部のモジュールの最初の更新を必要とせずに任意の順序でこれらのモジュールで呼び出せます。

`sp_refresh_parameter_encryption`拡張プロパティ、どのアクセス許可には影響しませんまたは`SET`オブジェクトに関連付けられているオプションです。 

サーバー レベルの DDL トリガーを更新するには、このストアド プロシージャをデータベースのコンテキストから実行します。

>  [!NOTE]   
>  実行すると、オブジェクトに関連付けられている署名は削除`sp_refresh_parameter_encryption`です。

## <a name="permissions"></a>Permissions

必要があります`ALTER`モジュールに対する権限と`REFERENCES`任意の CLR ユーザー定義型と、オブジェクトによって参照されている XML スキーマ コレクションに対する権限。   

指定されたモジュールがデータベース レベルの DDL トリガーの場合は、必要`ALTER ANY DATABASE DDL TRIGGER`現在のデータベースの権限です。    

指定されたモジュールは、サーバー レベルの DDL トリガーが、必要`CONTROL SERVER`権限です。

定義されているモジュールに対して、`EXECUTE AS`句、`IMPERSONATE`指定したプリンシパルに権限が必要です。 一般に、オブジェクトを更新する変わらないその`EXECUTE AS`モジュールが定義していない限り、プリンシパル`EXECUTE AS USER`と別のユーザーに解決されると比べて時に、モジュールが作成された現在のプリンシパルのユーザー名。
 
## <a name="examples"></a>使用例

次の例は、テーブルとテーブルを参照するプロシージャを作成し、Always Encrypted を構成し、テーブルを変更して、実行を示しています、`sp_refresh_parameter_encryption`プロシージャです。  

まず最初のテーブルとテーブルを参照するストアド プロシージャを作成します。
```tsql
CREATE TABLE [Patients]([PatientID] [int] IDENTITY(1,1) NOT NULL,
    [SSN] [char](11), 
    [FirstName] [nvarchar](50) NULL,
    [LastName] [nvarchar](50) NOT NULL,
    [MiddleName] [nvarchar](50) NULL,
    [StreetAddress] [nvarchar](50) NOT NULL,
    [City] [nvarchar](50) NOT NULL,
    [ZipCode] [char](5) NOT NULL,
    [State] [char](2) NOT NULL,
    [BirthDate] [date] NOT NULL,
 CONSTRAINT [PK_Patients] PRIMARY KEY CLUSTERED 
(
    [PatientID] ASC
) WITH 
    (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, 
     IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, 
     ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY];
GO

CREATE PROCEDURE [find_patient] @SSN [char](11)
AS
BEGIN
    SELECT * FROM [Patients] WHERE SSN=@SSN
END;
GO
```

Always Encrypted キーを設定しています。
```tsql
CREATE COLUMN MASTER KEY [CMK1]
WITH
(
       KEY_STORE_PROVIDER_NAME = N'MSSQL_CERTIFICATE_STORE',
    KEY_PATH = N'CurrentUser/my/A66BB0F6DD70BDFF02B62D0F87E340288E6F9305'
);
GO

CREATE COLUMN ENCRYPTION KEY [CEK1]
WITH VALUES
(
       COLUMN_MASTER_KEY = [CMK1],
    ALGORITHM = 'RSA_OAEP',
    ENCRYPTED_VALUE = 
       0x016E000001630075007200720065006E00740075007300650072002F006D0079002F006100360036006200620030006600360064006400370030006200640066006600300032006200360032006400300066003800370065003300340030003200380038006500360066003900330030003500CA0D0CEC74ECADD1804CF99137B4BD06BBAB15D7EA74E0C249A779C7768A5B659E0125D24FF827F5EA8CA517A8E197ECA1353BA814C2B0B2E6C8AB36E3AE6A1E972D69C3C573A963ADAB6686CF5D24F95FE43140C4F9AF48FBA7DF2D053F3B4A1F5693A1F905440F8015BDB43AF8A04BE4E045B89876A0097E5FBC4E6A3B9C3C0D278C540E46C53938B8C957B689C4DC095821C465C73117CBA95B758232F9E5B2FCC7950B8CA00AFE374DE42847E3FBC2FDD277035A2DEF529F4B735C20D980073B4965B4542A34723276A1646998FC6E1C40A3FDB6ABCA98EE2B447F114D2AC7FF8C7D51657550EC5C2BABFFE8429B851272086DCED94332CF18FA854C1D545A28B1EF4BE64F8E035175C1650F6FC5C4702ACF99850A4542B3747EAEC0CC726E091B36CE24392D801ECAA684DE344FECE05812D12CD72254A014D42D0EABDA41C89FC4F545E88B4B8781E5FAF40D7199D4842D2BFE904D209728ED4F527CBC169E2904F6E711FF81A8F4C25382A2E778DD2A58552ED031AFFDA9D9D891D98AD82155F93C58202FC24A77F415D4F8EF22419D62E188AC609330CCBD97CEE1AEF8A18B01958833604707FDF03B2B386487CC679D7E352D0B69F9FB002E51BCD814D077E82A09C14E9892C1F8E0C559CFD5FA841CEF647DAB03C8191DC46B772E94D579D8C80FE93C3827C9F0AE04D5325BC73111E07EEEDBE67F1E2A73580085
);
GO
```


最後に、SSN 列し実行して、暗号化された列で置換、 `sp_refresh_parameter_encryption` Always Encrypted は、コンポーネントを更新する手順。
```tsql
ALTER TABLE [Patients] DROP COLUMN [SSN];
GO

ALTER TABLE [Patients] 
    ADD [SSN] [char](11) COLLATE Latin1_General_BIN2 
    ENCRYPTED WITH 
        (COLUMN_ENCRYPTION_KEY = [CEK1], 
        ENCRYPTION_TYPE = Deterministic, 
        ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') 
    NOT NULL;
GO

EXEC sp_refresh_parameter_encryption [find_patient];
GO
```

## <a name="see-also"></a>参照 

[Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
[Always Encrypted ウィザード](../../relational-databases/security/encryption/always-encrypted-wizard.md)   

