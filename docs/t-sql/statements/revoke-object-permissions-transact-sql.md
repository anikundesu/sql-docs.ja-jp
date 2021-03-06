---
title: "取り消すオブジェクト権限 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- table permissions [SQL Server], revoking
- REVOKE statement, objects
- revoking permissions to access tables
- object permissions [SQL Server], revoking
ms.assetid: 99c7146e-d2e7-4f1a-80ff-21a05bc5e8bb
caps.latest.revision: "33"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 1d75af81016de00d7d76b95a1ea721b3c9ac87e3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="revoke-object-permissions-transact-sql"></a>REVOKE (オブジェクトの権限の取り消し) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  テーブル、ビュー、テーブル値関数、ストアド プロシージャ、拡張ストアド プロシージャ、スカラー関数、集計関数、サービス キュー、またはシノニムに対する権限を取り消します。 
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
REVOKE [ GRANT OPTION FOR ] <permission> [ ,...n ] ON   
    [ OBJECT :: ][ schema_name ]. object_name [ ( column [ ,...n ] ) ]  
        { FROM | TO } <database_principal> [ ,...n ]   
    [ CASCADE ]  
    [ AS <database_principal> ]  
  
<permission> ::=  
    ALL [ PRIVILEGES ] | permission [ ( column [ ,...n ] ) ]  
  
<database_principal> ::=   
        Database_user   
    | Database_role   
    | Application_role   
    | Database_user_mapped_to_Windows_User   
    | Database_user_mapped_to_Windows_Group   
    | Database_user_mapped_to_certificate   
    | Database_user_mapped_to_asymmetric_key   
    | Database_user_with_no_login      
```  
  
## <a name="arguments"></a>引数  
 *アクセス許可*  
 スキーマに含まれるオブジェクトで取り消すことができる権限を指定します。 権限の一覧については、後の「解説」を参照してください。  
  
 ALL  
 ALL を指定しても、可能な権限がすべて取り消されるわけではありません。 ALL を指定すると、指定したオブジェクトに適用されるすべての [!INCLUDE[vcpransi](../../includes/vcpransi-md.md)]-92 権限を取り消すことになります。 ALL の意味は、状況に応じて次のようになります。  
  
 スカラー関数の権限の場合は、EXECUTE、REFERENCES。  
  
 テーブル値関数の権限の場合は、DELETE、INSERT、REFERENCES、SELECT、UPDATE。  
  
 ストアド プロシージャの権限: を実行します。  
  
 テーブルの権限の場合は、DELETE、INSERT、REFERENCES、SELECT、UPDATE。  
  
 ビューの権限の場合は、DELETE、INSERT、REFERENCES、SELECT、UPDATE。  
  
 PRIVILEGES  
 含まれる[!INCLUDE[vcpransi](../../includes/vcpransi-md.md)]-92 準拠。 ALL の動作は変更されません。  
  
 *列*  
 権限を取り消すテーブル、ビュー、またはテーブル値関数内の列の名前を指定します。 かっこ () は、必要があります。 列で拒否できるのは、SELECT、REFERENCES、および UPDATE の各権限だけです。 *列*permissions 句内、またはセキュリティ保護可能な名前の後に指定することができます。  
  
 ON [オブジェクト::] [ *schema_name* ] です。 *object_name*  
 これで、権限を取り消すオブジェクトを指定します。 OBJECT 句は省略可能な場合は*schema_name*を指定します。 OBJECT 句を使用する場合は、スコープ修飾子 (::) が必要です。 場合*schema_name*が指定されていない、既定のスキーマを使用します。 場合*schema_name*を指定すると、スキーマ スコープ修飾子 (.) が必要です。  
  
 {から |} \<Database_principal > 元となる、権限を取り消すプリンシパルを指定します。  
  
 GRANT OPTION  
 指定した権限を他のプリンシパルに許可するための権利が、取り消されます。 その権限自体は失効しません。  
  
> [!IMPORTANT]  
>  指定した権限が GRANT オプションなしでプリンシパルに許可されている場合は、その権限自体が取り消されます。  
  
 CASCADE  
 このプリンシパルによって権限が許可または拒否されている他のプリンシパルからも、同じ権限が取り消されることを示します。  
  
> [!CAUTION]  
>  WITH GRANT OPTION で許可されている権限を CASCADE で取り消すと、その権限の GRANT および DENY の両方が取り消されます。  
  
 AS \<database_principal > このクエリを実行するプリンシパルの権限を取り消す権利の派生元のプリンシパルを指定します。  
  
 *Database_user*  
 データベース ユーザーを指定します。  
  
 *Database_role*  
 データベース ロールを指定します。  
  
 *Application_role*  
 アプリケーション ロールを指定します。  
  
 *Database_user_mapped_to_Windows_User*  
 Windows ユーザーにマップされているデータベース ユーザーを指定します。  
  
 *Database_user_mapped_to_Windows_Group*  
 Windows グループにマップされているデータベース ユーザーを指定します。  
  
 *Database_user_mapped_to_certificate*  
 証明書にマップされているデータベース ユーザーを指定します。  
  
 *Database_user_mapped_to_asymmetric_key*  
 非対称キーにマップされているデータベース ユーザーを指定します。  
  
 *Database_user_with_no_login*  
 対応するサーバー レベルのプリンシパルがないデータベース ユーザーを指定します。  
  
## <a name="remarks"></a>解説  
 オブジェクトに関する情報は、各種カタログ ビューに表示されます。 詳細については、次を参照してください。[オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md).  
  
 オブジェクトは、スキーマ レベルのセキュリティ保護可能なリソースで、権限の階層で親となっているスキーマに含まれています。 次の表に、オブジェクトで取り消すことができる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に示します。  
  
|オブジェクト権限|権限が含まれるオブジェクト権限|権限が含まれるスキーマ権限|  
|-----------------------|----------------------------------|----------------------------------|  
|ALTER|CONTROL|ALTER|  
|CONTROL|CONTROL|CONTROL|  
|DELETE|CONTROL|DELETE|  
|CREATE ステートメントを実行する前に、|CONTROL|CREATE ステートメントを実行する前に、|  
|INSERT|CONTROL|INSERT|  
|RECEIVE|CONTROL|CONTROL|  
|REFERENCES|CONTROL|REFERENCES|  
|SELECT|RECEIVE|SELECT|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|UPDATE|CONTROL|UPDATE|  
|VIEW CHANGE TRACKING|CONTROL|VIEW CHANGE TRACKING|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 オブジェクトに対する CONTROL 権限が必要です。  
  
 AS 句を使用する場合、指定されるプリンシパルは、権限が取り消されるオブジェクトを所有している必要があります。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-revoking-select-permission-on-a-table"></a>A. テーブルの SELECT 権限を取り消す  
 次の例では、`SELECT` データベースのテーブル `RosaQdM` に対する `Person.Address` 権限を、ユーザー `AdventureWorks2012` から取り消します。  
  
```  
USE AdventureWorks2012;  
REVOKE SELECT ON OBJECT::Person.Address FROM RosaQdM;  
GO  
```  
  
### <a name="b-revoking-execute-permission-on-a-stored-procedure"></a>B. ストアド プロシージャの EXECUTE 権限を取り消す  
 次の例では失効`EXECUTE`ストアド プロシージャに対する権限`HumanResources.uspUpdateEmployeeHireInfo`をアプリケーション ロールからという`Recruiting11`です。  
  
```  
USE AdventureWorks2012;  
REVOKE EXECUTE ON OBJECT::HumanResources.uspUpdateEmployeeHireInfo  
    FROM Recruiting11;  
GO   
```  
  
### <a name="c-revoking-references-permission-on-a-view-with-cascade"></a>C. CASCADE を指定してビューの REFERENCES 権限を取り消す  
 次の例では、ビュー `REFERENCES` 内の列 `BusinessEntityID` の `HumanResources.vEmployee` 権限を、ユーザー `Wanida` から取り消します。ここでは `CASCADE` を使用します。  
  
```  
USE AdventureWorks2012;  
REVOKE REFERENCES (BusinessEntityID) ON OBJECT::HumanResources.vEmployee   
    FROM Wanida CASCADE;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [GRANT (オブジェクトの権限の許可) &#40;Transact-SQL&#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)   
 [DENY (オブジェクトの権限の拒否) &#40;Transact-SQL&#41;](../../t-sql/statements/deny-object-permissions-transact-sql.md)   
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [アクセス許可 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Securables](../../relational-databases/security/securables.md)   
 [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/has-perms-by-name-transact-sql.md)   
 [sys.fn_my_permissions &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)  
  
  

