---
title: "sys.dm_fts_index_keywords_by_property (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_fts_index_keywords_by_property
- dm_fts_index_keywords_by_property_TSQL
- sys.dm_fts_index_keywords_by_property
- sys.dm_fts_index_keywords_by_property_TSQL
dev_langs: TSQL
helpviewer_keywords:
- full-text search [SQL Server], troubleshooting
- search property lists [SQL Server], viewing keywords by property
- full-text search [SQL Server], viewing keywords
- sys.dm_fts_index_keywords_by_property dynamic management view
ms.assetid: fa41e052-a79a-4194-9b1a-2885f7828500
caps.latest.revision: "14"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4eeeebce0c0a7f70cbd4ac94413b213776f6d97a
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="sysdmftsindexkeywordsbyproperty-transact-sql"></a>sys.dm_fts_index_keywords_by_property (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  特定のテーブルのフルテキスト インデックスのプロパティに関連するコンテンツを返します。 これには、フルテキスト インデックスに関連付けられた検索プロパティ リストによって登録されたすべてのプロパティに属するすべてのデータが含まれます。  
  
 sys.dm_fts_index_keywords_by_property は、どのような登録済みプロパティが各インデックス付きドキュメントのすべてのプロパティの正確なコンテンツと同様に、インデックス時に IFilters によって出力されるを参照することができます動的管理関数です。  
  
 **(プロパティに関連するコンテンツを含む) すべてのドキュメント レベルのコンテンツを表示するには**  
  
-   [sys.dm_fts_index_keywords_by_document &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)  
  
 **上位レベルのフルテキスト インデックス情報を表示するには**  
  
-   [sys.dm_fts_index_keywords &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql.md)  
  
> [!NOTE]  
>  検索プロパティ リストについては、次を参照してください。[検索プロパティ リストとドキュメント プロパティの検索](../../relational-databases/search/search-document-properties-with-search-property-lists.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.dm_fts_index_keywords_by_property  
(   
    DB_ID('database_name'),   
OBJECT_ID('table_name')   
)  
```  
  
## <a name="arguments"></a>引数  
 db_id ('*database_name*')  
 呼び出し、 [DB_ID()](../../t-sql/functions/db-id-transact-sql.md)関数。 この関数は、データベースの名前を受け付けますをデータベースの ID、どの sys.dm_fts_index_keywords_by_property を使用して、指定されたデータベースの検索を返します。 場合*database_name*は省略すると、現在のデータベース ID が返されます。  
  
 object_id ('*table_name*')  
 呼び出し、 [OBJECT_ID()](../../t-sql/functions/object-id-transact-sql.md)関数。 この関数はテーブル名を受け取り、調べるフルテキスト インデックスが含まれているテーブルのテーブル ID を返します。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列|データ型|Description|  
|------------|---------------|-----------------|  
|キーワード (keyword)|**nvarchar (4000)**|フルテキスト インデックスに格納されているキーワードの 16 進数表記です。<br /><br /> 注: 0 Xff は、ファイルまたはデータセットの終了を示す特殊文字を表します。|  
|display_term|**nvarchar (4000)**|人間が判読できる形式のキーワードです。 この形式は、フルテキスト インデックスに格納されている内部形式から派生しています。<br /><br /> 注: 0 Xff は、ファイルまたはデータセットの終了を示す特殊文字を表します。|  
|column_id|**int**|現在のキーワードのフルテキスト インデックスが作成された列の ID です。|  
|document_id|**int**|現在の用語のフルテキスト インデックスが作成されたドキュメントまたは行の ID です。 この ID は、ドキュメントまたは行のフル テキスト キー値に対応します。|  
|property_id|**int**|OBJECT_ID で指定したテーブルのフルテキスト インデックス内の検索プロパティの内部プロパティ ID ('*table_name*') のパラメーターです。<br /><br /> 特定のプロパティが検索プロパティ リストに追加されると、Full-Text Engine はプロパティを登録し、このプロパティ リストに固有の内部プロパティ ID を、そのプロパティに割り当てます。 内部プロパティ ID は、特定の検索プロパティ リストに固有の整数です。 特定のプロパティを複数の検索プロパティ リストに登録した場合、検索プロパティ リストごとに異なる内部プロパティ ID が割り当てられる可能性があります。<br /><br /> 注: 内部プロパティ ID とは異なりますが、検索プロパティ リストに、プロパティを追加するときに指定されているプロパティ整数識別子。 詳細については、「 [検索プロパティ リストを使用したドキュメント プロパティの検索](../../relational-databases/search/search-document-properties-with-search-property-lists.md)」を参照してください。<br /><br /> Property_id とプロパティ名の間の関連付けを表示します。<br />                    [sys.registered_search_properties &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md)|  
  
## <a name="remarks"></a>解説  
 この動的管理ビューは、次のような質問に応答できます。  
  
-   特定の DocID の特定のプロパティにどのようなコンテンツが格納されているか。  
  
-   特定のプロパティが、インデックス付きの文書間でどの程度一般的か。  
  
-   特定のプロパティを実際に含むドキュメントは何か。 これは、特定の検索プロパティへのクエリによって、見つかると想定していたドキュメントが返されなかった場合に役立ちます。  
  
 フルテキスト キー列が整数データ型 (推奨されるデータ型) の場合、document_id はベース テーブルのフルテキスト キー値に直接マップされます。  
  
 一方、フルテキスト キー列で整数データ型以外のデータ型が使用されている場合は、document_id はベース テーブルのフルテキスト キーを表しません。 この例では、によって返された結果をこのビューを結合する必要が dm_fts_index_keywords_by_property によって返されるベース テーブルの行を識別するため[sp_fulltext_keymappings](../../relational-databases/system-stored-procedures/sp-fulltext-keymappings-transact-sql.md)です。 結合の前に、このストアド プロシージャの出力を一時テーブルに格納します。 このストアド プロシージャによって返される DocId 列を含む dm_fts_index_keywords_by_property の document_id 列を結合することができます。 なお、**タイムスタンプ**列は、によって自動生成されるために、挿入時にの値を受け取ることはできません[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 したがって、**タイムスタンプ**に列を変換する必要があります**varbinary (8)**列です。 次の例はこれらの手順を示しています。 この例では*table_id* 、テーブルの id を指定します*database_name* 、データベースの名前を指定し、 *table_name*テーブルの名前を指定します。  
  
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
SELECT * FROM sys.dm_fts_index_keywords_by_property   
   ( @db_id, @table_id ) kbd  
   INNER JOIN #MyTempTable tt ON tt.[docid]=kbd.document_id;  
GO  
  
```  
  
## <a name="permissions"></a>Permissions  
 フルテキスト インデックスに含まれる列に対する SELECT 権限と、CREATE FULL TEXT CATALOG 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、`Author` サンプル データベースの `Production.Document` テーブルのフルテキスト インデックスにある `AdventureWorks` プロパティからキーワードが返されます。 例では、エイリアスを使用して`KWBPOP`によって返されるテーブルの**sys.dm_fts_index_keywords_by_property**です。 例では、内部結合を使用して、列から結合[sys.registered_search_properties](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md)と[sys.fulltext_indexes](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)です。  
  
```  
-- Once the full-text index is configured to support property searching  
-- on the Author property, return any keywords indexed for this property.  
USE AdventureWorks2012;  
GO   
SELECT KWBPOP.* FROM   
   sys.dm_fts_index_keywords_by_property( DB_ID(),   
   object_id('Production.Document') ) AS KWBPOP  
   INNER JOIN  
      sys.registered_search_properties AS RSP ON(   
         (KWBPOP.property_id = RSP.property_id)   
         AND (RSP.property_name = 'Author') )  
   INNER JOIN  
      sys.fulltext_indexes AS FTI ON(   
         (FTI.[object_id] = object_id('Production.Document'))   
         AND (RSP.property_list_id = FTI.property_list_id) );  
GO  
```  
  
## <a name="see-also"></a>参照  
 [フルテキスト検索](../../relational-databases/search/full-text-search.md)   
 [フルテキスト インデックスのパフォーマンスを向上させる](../../relational-databases/search/improve-the-performance-of-full-text-indexes.md)   
 [sp_fulltext_keymappings &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-fulltext-keymappings-transact-sql.md)   
 [sys.dm_fts_index_keywords_by_document &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)   
 [sys.dm_fts_index_keywords &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql.md)   
 [sys.registered_search_properties &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md)   
 [sys.registered_search_property_lists &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)   
 [検索プロパティ リストを使用したドキュメント プロパティの検索](../../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
  
