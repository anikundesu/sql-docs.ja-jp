---
title: "sys.dm_fts_index_keywords_position_by_document (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
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
- sys.dm_fts_index_keywords_position_by_document_TSQL
- dm_fts_index_keywords_position_by_document_TSQL
- dm_fts_index_keywords_position_by_document
- sys.dm_fts_index_keywords_position_by_document
dev_langs: TSQL
helpviewer_keywords: sys.dm_fts_index_keywords_position_by_document dynamic management view
ms.assetid: 0d70184f-baa2-411b-a32d-a4c5af890edd
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c9fc96c8db1521ac99601312869146290a622147
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmftsindexkeywordspositionbydocument-transact-sql"></a>sys.dm_fts_index_keywords_position_by_document (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  インデックス付きのドキュメントでは、位置指定のキーワードを使用する情報を返します。  
  
## <a name="syntax"></a>構文  
  
```  
sys.dm_fts_index_keywords_position_by_document  
(   
    DB_ID('database_name'),   
OBJECT_ID('table_name')   
)  
```  
  
## <a name="arguments"></a>引数  
 db_id ('*database_name*')  
 呼び出し、 [DB_ID()](../../t-sql/functions/db-id-transact-sql.md)関数。 この関数は、データベースの名前を受け付けますをデータベースの ID、どの sys.dm_fts_index_keywords_position_by_document を使用して、指定されたデータベースの検索を返します。  
  
 object_id ('*table_name*')  
 呼び出し、 [OBJECT_ID()](../../t-sql/functions/object-id-transact-sql.md)関数。 この関数はテーブル名を受け取り、調べるフルテキスト インデックスが含まれているテーブルのテーブル ID を返します。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列|データ型|Description|  
|------------|---------------|-----------------|  
|キーワード (keyword)|**varbinary (128)**|キーワードを表すバイナリ文字列。|  
|display_term|**nvarchar (4000)**|人間が判読できる形式のキーワードです。 この形式は、フルテキスト インデックスに格納されている内部形式から派生しています。|  
|column_id|**int**|現在のキーワードのフルテキスト インデックスが作成された列の ID です。|  
|document_id|**bigint**|現在の用語のフルテキスト インデックスが作成されたドキュメントまたは行の ID です。 この ID は、ドキュメントまたは行のフル テキスト キー値に対応します。|  
|position|**int**|ドキュメント内のキーワードの位置。|  
  
## <a name="remarks"></a>解説  
 DMV を使用すると、インデックス付きドキュメント内のインデックス付けされた単語の場所を識別できます。 この DMV のトラブルシューティングに使用できる発行するときに**sys.dm_fts_index_keywords_by_document**単語は、フルテキスト インデックスが、それらの単語を使用してクエリを実行すると、ドキュメントは返されませんを示します。  
  
## <a name="permissions"></a>Permissions  
 フルテキスト インデックスに含まれる列に対する SELECT 権限と、CREATE FULL TEXT CATALOG 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、キーワードを返してのフルテキスト インデックスから、`Production.Document`のテーブル、`AdventureWorks`サンプル データベース。  
  
```  
USE AdventureWorks2012;  
GO   
  
SELECT * FROM sys.dm_fts_index_keywords_position_by_document  
(   
    DB_ID('AdventureWorks2012'),  
    OBJECT_ID('AdventureWorks2012.Production.Document')   
);   
GO  
```  
  
 次のクエリ、さらに、場所を特定するのと同様に、その他の columns_id では、述語を追加できます。  
  
```  
SELECT * FROM sys.dm_fts_index_keywords_position_by_document  
(   
    DB_ID('AdventureWorks2012'),  
    OBJECT_ID('AdventureWorks2012.Production.Document')   
)  
WHERE document_id = 7 AND display_term = 'performance';  
```  
  
## <a name="see-also"></a>参照  
 [フルテキスト検索](../../relational-databases/search/full-text-search.md)   
 [フルテキスト インデックスのパフォーマンスを向上させる](../../relational-databases/search/improve-the-performance-of-full-text-indexes.md)   
 [フルテキスト検索およびセマンティック検索関数 &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/full-text-search-and-semantic-search-functions-transact-sql.md)   
 [フルテキスト検索およびセマンティック検索の動的管理ビューおよび関数 &#40;TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [フルテキスト検索およびセマンティック検索ストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)   
 [検索プロパティ リストを使用したドキュメント プロパティの検索](../../relational-databases/search/search-document-properties-with-search-property-lists.md)   
 [sys.dm_fts_index_keywords_by_document &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)  
  
  
