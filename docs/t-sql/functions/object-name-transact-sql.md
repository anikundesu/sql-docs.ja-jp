---
title: "OBJECT_NAME (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OBJECT_NAME
- OBJECT_NAME_TSQL
dev_langs: TSQL
helpviewer_keywords:
- OBJECT_NAME function
- viewing database object names
- objects [SQL Server], names
- database objects [SQL Server], names
- displaying database object names
- database objects [SQL Server]
- names [SQL Server], database objects
ms.assetid: 7d5b923f-0c3e-4af9-b39b-132807a6d5b3
caps.latest.revision: "45"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 0e6f583fb5fa20c8686343ee4d87e9f4b369183c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="objectname-transact-sql"></a>OBJECT_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  スキーマ スコープ オブジェクトのデータベース オブジェクト名を返します。 スキーマ スコープ オブジェクトの一覧は、次を参照してください。 [sys.objects &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
OBJECT_NAME ( object_id [, database_id ] )  
```  
  
## <a name="arguments"></a>引数  
 *object_id*  
 使用するオブジェクトの ID を指定します。 *object_id*は**int**または現在のデータベース コンテキストで指定されたデータベースでは、スキーマ スコープ オブジェクトであると見なされます。  
  
 *database_id*  
 オブジェクトを検索するデータベースの ID を指定します。 *database_id*は**int**です。  
  
## <a name="return-types"></a>戻り値の型  
 **sysname**  
  
## <a name="exceptions"></a>例外  
 エラーが発生した場合、または呼び出し元にオブジェクトの表示権限がない場合は、NULL が返されます。 呼び出し先データベースの AUTO_CLOSE オプションが ON に設定されている場合、データベースが開きます。  
  
 ユーザーが所有しているか、または権限を与えられている、セキュリティ保護可能なリソースのメタデータのみを表示できます。 つまり、オブジェクトに対する権限がユーザーに与えられていない場合、メタデータを生成する組み込み関数 (OBJECT_NAME など) が NULL を返す可能性があります。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="permissions"></a>Permissions  
 オブジェクトに対する ANY 権限が必要です。 データベース ID を指定するには、そのデータベースの CONNECT 権限を持っているか、ゲスト アカウントが有効である必要があります。  
  
## <a name="remarks"></a>解説  
 システム関数は、選択リストの中、WHERE 句の中、また、式を使える所ならどこにでも使用できます。 詳細については、次を参照してください。[式](../../t-sql/language-elements/expressions-transact-sql.md)と[場所](../../t-sql/queries/where-transact-sql.md)です。  
  
 このシステム関数が返す値には、現在のデータベースの照合順序が使用されます。  
  
 既定では、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]であると推定*object_id*は、現在のデータベースのコンテキストでします。 参照するクエリ、 *object_id*別のデータベースでは、NULL または不適切な結果を返します。 たとえば、次のクエリでは、現在のデータベースのコンテキストは[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]します。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]は、クエリの FROM 句に指定されたデータベースではなく、このデータベースの指定されたオブジェクト ID のオブジェクト名を返します。 したがって、正しくない情報が返されます。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT DISTINCT OBJECT_NAME(object_id)  
FROM master.sys.objects;  
GO  
```  
  
 データベース ID を指定することで、別のデータベースのコンテキストにあるオブジェクト名を解決できます。 次の例では、`master` 関数で `OBJECT_SCHEMA_NAME` データベースのデータベース ID を指定し、正確な結果を返します。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT DISTINCT OBJECT_SCHEMA_NAME(object_id, 1) AS schema_name  
FROM master.sys.objects;  
GO  
```  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-objectname-in-a-where-clause"></a>A. WHERE 句で OBJECT_NAME を使用する  
 この例では、`sys.objects` ステートメントの `OBJECT_NAME` 句の `WHERE` で指定されたオブジェクトの `SELECT` カタログ ビューから列を返します。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @MyID int;  
SET @MyID = (SELECT OBJECT_ID('AdventureWorks2012.Production.Product',  
    'U'));  
SELECT name, object_id, type_desc  
FROM sys.objects  
WHERE name = OBJECT_NAME(@MyID);  
GO  
```  
  
### <a name="b-returning-the-object-schema-name-and-object-name"></a>B. オブジェクト スキーマ名とオブジェクト名を取得する  
 この例では、アドホック ステートメントでも準備されたステートメントでもない、キャッシュされたすべてのクエリ プランについて、オブジェクト スキーマ名、オブジェクト名、SQL テキストを返します。  
  
```  
SELECT DB_NAME(st.dbid) AS database_name,   
    OBJECT_SCHEMA_NAME(st.objectid, st.dbid) AS schema_name,  
    OBJECT_NAME(st.objectid, st.dbid) AS object_name,   
    st.text AS query_text  
FROM sys.dm_exec_query_stats AS qs  
CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS st  
WHERE st.objectid IS NOT NULL;  
GO  
```  
  
### <a name="c-returning-three-part-object-names"></a>C. 3 つの要素で構成されたオブジェクト名を取得する  
 この例では、データベース名、スキーマ名、およびオブジェクト名と共に、すべてのデータベースのすべてのオブジェクトの統計を示す `sys.dm_db_index_operational_stats` 動的管理ビューの残りのすべての列を返します。  
  
```  
SELECT QUOTENAME(DB_NAME(database_id))   
    + N'.'   
    + QUOTENAME(OBJECT_SCHEMA_NAME(object_id, database_id))   
    + N'.'   
    + QUOTENAME(OBJECT_NAME(object_id, database_id))  
    , *   
FROM sys.dm_db_index_operational_stats(null, null, null, null);  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-using-objectname-in-a-where-clause"></a>D. WHERE 句で OBJECT_NAME を使用する  
 この例では、`sys.objects` ステートメントの `OBJECT_NAME` 句の `WHERE` で指定されたオブジェクトの `SELECT` カタログ ビューから列を返します。 (、オブジェクト数 (次の例では 274100017) は変更されます。  この例をテストする番号を調べる、有効なオブジェクトを実行して`SELECT name, object_id FROM sys.objects;`データベースにします)。  
  
```  
SELECT name, object_id, type_desc  
FROM sys.objects  
WHERE name = OBJECT_NAME(274100017);  
```  
  
## <a name="see-also"></a>参照  
 [メタデータ関数 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [OBJECT_DEFINITION &#40;Transact-SQL&#41;](../../t-sql/functions/object-definition-transact-sql.md)   
 [OBJECT_ID &#40;Transact-SQL&#41;](../../t-sql/functions/object-id-transact-sql.md)  
  
  

