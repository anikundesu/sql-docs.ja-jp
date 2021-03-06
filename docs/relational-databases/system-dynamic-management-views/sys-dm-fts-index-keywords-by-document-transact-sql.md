---
title: "sys.dm_fts_index_keywords_by_document (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_fts_index_keywords_by_document_TSQL
- dm_fts_index_keywords_by_document_TSQL
- sys.dm_fts_index_keywords_by_document
- dm_fts_index_keywords_by_document
dev_langs: TSQL
helpviewer_keywords:
- full-text search [SQL Server], troubleshooting
- sys.dm_fts_index_keywords_by_document dynamic management function
- full-text search [SQL Server], viewing keywords
ms.assetid: 793b978b-c8a1-428c-90c2-a3e49d81b5c9
caps.latest.revision: "40"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5db2c784b48c6a1c9ef97f11fb0fbb7903bc85e4
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmftsindexkeywordsbydocument-transact-sql"></a>sys.dm_fts_index_keywords_by_document (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  指定されたテーブルに関連付けられているフルテキスト インデックスのドキュメント レベルのコンテンツに関連する情報を返します。  
  
 sys.dm_fts_index_keywords_by_document は動的管理関数です。  
  
 **上位レベルのフルテキスト インデックス情報を表示するには**  
  
-   [sys.dm_fts_index_keywords &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql.md)  
  
 **ドキュメント プロパティに関連するプロパティ レベルのコンテンツに関する情報を表示するには**  
  
-   [sys.dm_fts_index_keywords_by_property &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-property-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.dm_fts_index_keywords_by_document  
(   
    DB_ID('database_name'),     OBJECT_ID('table_name')   
)  
```  
  
## <a name="arguments"></a>引数  
 db_id ('*database_name*')  
 呼び出し、 [DB_ID()](../../t-sql/functions/db-id-transact-sql.md)関数。 この関数は、データベース名を受け取り、データベース ID を返します。sys.dm_fts_index_keywords_by_document はこの ID を使用して指定されたデータベースを検索します。 場合*database_name*は省略すると、現在のデータベース ID が返されます。  
  
 object_id ('*table_name*')  
 呼び出し、 [OBJECT_ID()](../../t-sql/functions/object-id-transact-sql.md)関数。 この関数はテーブル名を受け取り、調べるフルテキスト インデックスが含まれているテーブルのテーブル ID を返します。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列|データ型|Description|  
|------------|---------------|-----------------|  
|キーワード (keyword)|**nvarchar (4000)**|フルテキスト インデックスに格納されているキーワードの 16 進数表記です。<br /><br /> 注: 0 Xff は、ファイルまたはデータセットの終了を示す特殊文字を表します。|  
|display_term|**nvarchar (4000)**|人間が判読できる形式のキーワードです。 この形式は、フルテキスト インデックスに格納されている内部形式から派生しています。<br /><br /> 注: 0 Xff は、ファイルまたはデータセットの終了を示す特殊文字を表します。|  
|column_id|**int**|現在のキーワードのフルテキスト インデックスが作成された列の ID です。|  
|document_id|**int**|現在の用語のフルテキスト インデックスが作成されたドキュメントまたは行の ID です。 この ID は、ドキュメントまたは行のフル テキスト キー値に対応します。|  
|occurrence_count|**int**|ドキュメントまたは行で示されている現在のキーワードのオカレンス数**document_id**です。 ときに '*search_property_name*' が指定されている occurrence_count ドキュメントまたは行内の指定した検索プロパティの現在のキーワードのオカレンス数のみが表示されます。|  
  
## <a name="remarks"></a>解説  
 sys.dm_fts_index_keywords_by_document から返される情報は、特に次の項目を確認するのに役立ちます。  
  
-   フルテキスト インデックスに格納されているキーワードの合計数。  
  
-   キーワードが特定のドキュメントまたは行の一部であるかどうか。  
  
-   フルテキスト インデックス全体にキーワードが出現する回数。次のようになります。  
  
     ([合計](../../t-sql/functions/sum-transact-sql.md)(**occurrence_count**)、**キーワード**=*keyword_value* )  
  
-   特定のドキュメントまたは行にキーワードが出現する回数。  
  
-   特定のドキュメントまたは行に含まれているキーワードの数。  
  
 また、sys.dm_fts_index_keywords_by_document が提供する情報を使用して、特定のドキュメントまたは行に属しているすべてのキーワードを取得することもできます。  
  
 フルテキスト キー列が整数データ型 (推奨されるデータ型) の場合、document_id はベース テーブルのフルテキスト キー値に直接マップされます。  
  
 一方、フルテキスト キー列で整数データ型以外のデータ型が使用されている場合は、document_id はベース テーブルのフルテキスト キーを表しません。 この例では、によって返された結果をこのビューを結合する必要が dm_fts_index_keywords_by_document から返されるベース テーブルの行を識別するため[sp_fulltext_keymappings](../../relational-databases/system-stored-procedures/sp-fulltext-keymappings-transact-sql.md)です。 結合の前に、このストアド プロシージャの出力を一時テーブルに格納します。 その後、dm_fts_index_keywords_by_document の document_id 列と、このストアド プロシージャから返される DocId 列を結合します。 なお、**タイムスタンプ**列は、によって自動生成されるために、挿入時にの値を受け取ることはできません[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 したがって、**タイムスタンプ**に列を変換する必要があります**varbinary (8)**列です。 次の例はこれらの手順を示しています。 この例では*table_id* 、テーブルの id を指定します*database_name* 、データベースの名前を指定し、 *table_name*テーブルの名前を指定します。  
  
```  
USE database_name;  
GO  
CREATE TABLE #MyTempTable   
   (  
      docid INT PRIMARY KEY ,  
      [key] INT NOT NULL  
   );  
DECLARE @db_id int = db_id(N'database_name');  
DECLARE @table_id int = OBJECT_ID(N'table_name');  
INSERT INTO #MyTempTable EXEC sp_fulltext_keymappings @table_id;  
SELECT * FROM sys.dm_fts_index_keywords_by_document   
   ( @db_id, @table_id ) kbd  
   INNER JOIN #MyTempTable tt ON tt.[docid]=kbd.document_id;  
GO  
  
```  
  
## <a name="permissions"></a>Permissions  
 フルテキスト インデックスに含まれる列に対する SELECT 権限と、CREATE FULL TEXT CATALOG 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-displaying-full-text-index-content-at-the-document-level"></a>A. ドキュメント レベルでフルテキスト インデックス コンテンツを表示する  
 次の例は、ドキュメント レベルでフルテキスト インデックスのコンテンツを表示、`HumanResources.JobCandidate`のテーブル、`AdventureWorks2012`サンプル データベース。  
  
> [!NOTE]  
>  提示された例を実行することによってこのインデックスを作成することができます、`HumanResources.JobCandidate`テーブルに[CREATE FULLTEXT INDEX &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-fulltext-index-transact-sql.md).  
  
```  
SELECT * FROM sys.dm_fts_index_keywords_by_document(db_id('AdventureWorks'),   
object_id('HumanResources.JobCandidate'));  
GO  
```  
  
## <a name="see-also"></a>参照  
 [フルテキスト検索およびセマンティック検索の動的管理ビューおよび関数 &#40;TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [フルテキスト検索](../../relational-databases/search/full-text-search.md)   
 [sys.dm_fts_index_keywords &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql.md)   
 [sys.dm_fts_index_keywords_by_property &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-property-transact-sql.md)   
 [sp_fulltext_keymappings &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-fulltext-keymappings-transact-sql.md)   
 [フルテキスト インデックスのパフォーマンスの向上](../../relational-databases/search/improve-the-performance-of-full-text-indexes.md)  
  
  
