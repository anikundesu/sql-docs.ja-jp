---
title: "R データ型の処理 | Microsoft Docs"
ms.custom: SQL2016_New_Updated
ms.date: 01/31/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5df99e1c-a89a-42c1-9d68-ffe8d9577c94
caps.latest.revision: "16"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e72c4a984359230ace9f800e8ac4efbfcfe5f2a1
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2017
---
# <a name="r-libraries-and-r-data-types"></a>R ライブラリと R データ型

このトピックでは、R ライブラリに含まれていると、次の製品でサポートされているデータ型について説明します。

+ SQL Server 2016 R Services (In-database)
+ SQL Server コンピューターのサービス (In-database) を学習

このトピックは、サポートされていないデータ型も一覧表示されます。 とリスト、データ型の変換 R と SQL Server の間でデータが渡されるときに暗黙的に実行することができます。

## <a name="r-libraries"></a>R ライブラリ

Microsoft R Open の特定のリリースでは、両方の製品では、R Services およびの R、マシン学習サービスを配置します。 たとえば、最新のリリースでは、SQL Server 2017 Machine Learning サービスは Microsoft R Open 上に構築された 3.3.3 です。

SQL Server の特定のインスタンスに関連付けられた R のバージョンを表示するには、RGui を開きます。

1. 既定のインスタンスのパスはとおりなります。`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64\`
2. R ディストリビューションおよび Microsoft R Open のバージョン番号を示すメッセージが表示されます。

Microsoft R Server の特定のバージョンに含まれている R のバージョンを検索するには、次を参照してください。 [R Server の新機能](https://msdn.microsoft.com/microsoft-r/rserver-whats-new#new-and-updated-packages)します。

SQL server パッケージ管理システムでは、複数のユーザー、同じパッケージの共有または同じパッケージの別のバージョンを使用して、R パッケージの複数のバージョンが、同じコンピューターにインストールできますということに注意してください。 詳細については、次を参照してください。 [SQL Server で R パッケージの管理](../r/r-package-management-for-sql-server-r-services.md)です。

## <a name="r-and-sql-data-types"></a>R と SQL データ型

一方[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]いくつかの十種類データ型をサポートしている R が限定された数のスカラー データ型 (数値、整数、複合、論理、文字、日付/時刻と生) です。 データを使用する場合にその結果、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] R スクリプトでデータが暗黙的に変換を互換性のあるデータ型にします。 ただし、正確な変換が自動的に実行できない多くの場合、「未処理の SQL データ型」など、エラーが返されます。

このセクションでは、暗黙の変換についても説明し、サポートされていないデータ型の一覧を示します。 R と SQL Server の間のデータ型のマッピングのガイダンスは提供されます。

## <a name="implicit-data-type-conversions-between-r-and-sql-server"></a>R と SQL Server 間の暗黙のデータ型変換

次の表は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータを R スクリプトで使用する場合と、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に返された場合のデータ型と値の変化の一覧です。

|SQL 型|R クラス|RESULT SET の型|コメント|
|-|-|-|-|
|**bigint**|`numeric`|**float**||
|**binary(n)**<br /><br /> n <= 8000|`raw`|**varbinary(max)**|入力パラメーターと出力にのみ使用できます。|
|**bit**|`logical`|**bit**||
|**char(n)**<br /><br /> n <= 8000|`character`|**varchar(max)**||
|**datetime**|`POSIXct`|**datetime**|GMT として表現されます|
|**date**|`POSIXct`|**datetime**|GMT として表現されます|
|**decimal(p,s)**|`numeric`|**float**||
|**float**|`numeric`|**float**||
|**int**|`integer`|**int**||
|**money**|`numeric`|**float**||
|**numeric(p,s)**|`numeric`|**float**||
|**real**|`numeric`|**float**||
|**smalldatetime**|`POSIXct`|**datetime**|GMT として表現されます|
|**smallint**|`integer`|**int**||
|**smallmoney**|`numeric`|**float**||
|**tinyint**|`integer`|**int**||
|**uniqueidentifier**|`character`|**varchar(max)**||
|**varbinary(n)**<br /><br /> n <= 8000|`raw`|**varbinary(max)**|入力パラメーターと出力にのみ使用できます。|
|**varbinary(max)**|`raw`|**varbinary(max)**|入力パラメーターと出力にのみ使用できます。|
|**varchar(n)**<br /><br /> n <= 8000|`character`|**varchar(max)**||


## <a name="data-types-not-supported-by-r"></a>R でサポートされていないデータ型

[SQL Server 型システム](../../t-sql/data-types/data-types-transact-sql.md)でサポートされるデータ型のカテゴリのうち、次の型は R コードに渡されるときに問題が発生する可能性があります。

+ 示されたデータ型、**他**SQL 型システム」の「:**カーソル**、**タイムスタンプ**、 **hierarchyid**、 **uniqueidentifier**、 **sql_variant**、 **xml**、**テーブル**
+ すべての空間型
+ **image**

## <a name="data-types-that-might-convert-poorly"></a>適切に変換できない可能性があるデータ型

+ **datetimeoffset** 以外のほとんどの日時型は動作します 
+ ほとんどの数値データ型はサポートされますが、**money** と **smallmoney** は変換が失敗することがあります
+ **varchar** はサポートされますが、SQL Server では原則として Unicode を使用するため、可能な場合には **nvarchar** とその他の Unicode テキスト データ型の使用をお勧めします。
+ RevoScaleR ライブラリの先頭に rx が付く関数は、SQL バイナリ データ型 (**バイナリ**と **varbinary**) を処理できますが、ほとんどのシナリオでは、これらの型に対して特別な処理が必要になります。 R コードの大部分は、バイナリ列で動作しません。

  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ型について詳しくは、「[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)」をご覧ください

## <a name="changes-in-data-types-between-sql-server-2016-and-earlier-versions"></a>SQL Server 2016 とそれより前のバージョンの間でのデータ型の変更

Microsoft SQL Server 2016 と Microsoft Azure SQL Database には、データ型変換とその他のいくつかの操作の改善が含まれています。 これらの改善のほとんどでは、浮動小数点型を処理する場合の精度が向上し、従来の**日時**型に対する操作が若干変更されています。

これらの改善は、データベース互換性レベル 130 またはそれ以降を使用する場合に既定ですべて使用可能になります。 ただし、別の互換性レベルを使用しているか、以前のバージョンを使用してデータベースに接続する場合は、数値またはその他の結果の精度が異なる可能性があります。 

詳しくは、「[SQL Server 2016 improvements in handling some data types and uncommon operations](https://support.microsoft.com/help/4010261/sql-server-2016-improvements-in-handling-some-data-types-and-uncommon-)」(いくつかのデータ型と一般的でない操作を処理するときの SQL Server の 2016 の機能強化) をご覧ください。
 

## <a name="verify-r-and-sql-data-schemas-in-advance"></a>R と SQL のデータ スキーマを事前に確認する 

一般的に、特定のデータ型またはデータ構造を R で使用する方法についてわからない点がある場合は、  `str()` 関数を使用して内部構造と R オブジェクトの種類を取得してください。 この関数の結果は R コンソールに出力され、 **の** [メッセージ] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]タブのクエリ結果で確認することもできます。 

R コードで使用するためのデータをデータベースから取得する場合、R で使用できない列だけでなく、GUID (一意識別子)、タイムスタンプ、監査に使用されるその他の列など、分析に使用できない列と、ETL プロセスによって作成された系列情報を常に除外する必要があります。 

不要な列を含めると、基数の大きい列が係数として使用されている場合には特に、R コードのパフォーマンスが大幅に低下することがあります。 そのため、SQL Server システム ストアド プロシージャと情報ビューを使用して、事前に特定のテーブルのデータ型を取得し、互換性のない列を排除または変換することをお勧めします。 詳しくは、「[システム情報スキーマ ビュー (TRANSACT-SQL)](../../relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)」をご覧ください

特定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型が R でサポートされておらず、R スクリプトでデータの列を使用する必要がある場合、R スクリプトでデータを使用する前に、[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md) 関数を使用してデータ型変換が意図したとおりに実行されることを確認することをお勧めします。  

> [!WARNING]
データの移動中に **rxDataStep** を使用して互換性のない列を削除する場合、引数 "_varsToKeep_" と "_varsToDrop_" は **RxSqlServerData** データ ソース型としてサポートされないことにご注意ください。


## <a name="examples"></a>使用例

### <a name="example-1-implicit-conversion"></a>例 1: 暗黙の変換

次の例では、SQL Server と R の間を往復するときにデータを変換する方法を示しています。

クエリが、一連から値を取得、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル、およびストアド プロシージャを使用して[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) R ランタイムを使用して値を出力します。

```SQL
CREATE TABLE MyTable (    
 c1 int,    
 c2 varchar(10),    
 c3 uniqueidentifier    
);    
go    
INSERT MyTable VALUES(1, 'Hello', newid());    
INSERT MyTable VALUES(-11, 'world', newid());    
SELECT * FROM MyTable;    
  
EXECUTE sp_execute_external_script    
 @language = N'R'    
 , @script = N'    
inputDataSet["cR"] <- c(4, 2)    
str(inputDataSet)    
outputDataSet <- inputDataSet'    
 , @input_data_1 = N'SELECT c1, c2, c3 FROM MyTable'    
 , @input_data_1_name = N'inputDataSet'    
 , @output_data_1_name = N'outputDataSet'    
 WITH RESULT SETS((C1 int, C2 varchar(max), C3 varchar(max), C4 float));  
```

**結果**

||||||
|-|-|-|-|-|
||C1|C2|C3|C4|
|@shouldalert|@shouldalert|Hello|6e225611-4b58-4995-a0a5-554d19012ef1|4|
|@shouldalert|-11|world|6732ea46-2d5d-430b-8ao1-86e7f3351c3e|2|

R で `str` 関数を使用すると、出力データのスキーマが取得されます。 この関数からは、次の情報が返されます。

<code>'data.frame':2 obs. of  4 variables:</code>
<code> $ c1: int  1 -11</code>
<code> $ c2: Factor w/ 2 levels "Hello","world": 1 2</code>
<code> $ c3: Factor w/ 2 levels "6732EA46-2D5D-430B-8A01-86E7F3351C3E",..: 2 1</code>
<code> $ cR: num  4 2</code>

その結果から、次のデータ型の変換がこのクエリの一部として暗黙的に実行されたことがわかります。

-   **列 C1**。 この列は **ssNoversion** では [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、R では `integer` 、出力結果セットでは **ssNoversion** と表現されます。  
  
     型変換は実行されていません。  
  
-   **列 C2**。 この列は **ssNoversion** では [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、R では `factor` 、出力結果セットでは **varchar(max)** と表現されます。  
  
     出力の変化に注目してください。文字列の長さにかかわらず、R の文字列 (係数または通常の文字列) は **varchar(max)**と表現されます。  
  
-   **列 C3**。  この列は **ssNoversion** では [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、R では `character` 、出力結果セットでは **varchar(max)** と表現されます。
  
     発生したデータ型の変換に注目してください。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は **ssNoversion** をサポートしていますが、R はサポートしていません。そのため、識別子は文字列として表されます。
  
-   **列 C4**。 この列には、元のデータには存在しない、R スクリプトで生成された値が含まれます。


## <a name="example-2-dynamic-column-selection-using-r"></a>例2: R を使用した動的な列の選択

次の例では、R コードを使用して無効な列の型をチェックする方法を示します。 指定されたテーブルのスキーマを SQL Server システム ビューを使用して取得し、指定された無効な型を持つ列をすべて削除します。

```R
connStr <- "Server=.;Database=TestDB;Trusted_Connection=Yes"
data <- RxSqlServerData(connectionString = connStr, sqlQuery = "SELECT COLUMN_NAME FROM TestDB.INFORMATION_SCHEMA.COLUMNS WHERE TABLE_NAME = N'testdata' AND DATA_TYPE <> 'image';")
columns <- rxImport(data)
columnList <- do.call(paste, c(as.list(columns$COLUMN_NAME), sep = ","))
sqlQuery <- paste("SELECT", columnList, "FROM testdata")
```

## <a name="see-also"></a>参照

[Python ライブラリとデータ型](../python/python-libraries-and-data-types.md)
