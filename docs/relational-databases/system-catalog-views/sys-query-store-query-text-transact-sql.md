---
title: "sys.query_store_query_text (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SYS.QUERY_STORE_QUERY_TEXT
- QUERY_STORE_QUERY_TEXT
- SYS.QUERY_STORE_QUERY_TEXT_TSQL
- QUERY_STORE_QUERY_TEXT_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sys.query_store_query_text catalog view
- query_store_query_text catalog view
ms.assetid: f7032fa0-7c16-4492-bb82-685806c63a8c
caps.latest.revision: "9"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d3e008c9ad9e48d5e76af2ab8e61ff26ae9bdede
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysquerystorequerytext-transact-sql"></a>sys.query_store_query_text (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  含まれています、[!INCLUDE[tsql](../../includes/tsql-md.md)]テキストとクエリの SQL ハンドル。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**query_text_id**|**bigint**|主キー。|  
|**query_sql_text**|**nvarchar(max)**|ユーザーから提供されるため、クエリの SQL テキスト。 ある空白文字、ヒント、およびコメントが含まれています。|  
|**statement_sql_handle**|**vabinary(64)**|個別のクエリの SQL ハンドル。|  
|**is_part_of_encrypted_module**|**bit**|クエリ テキストは、暗号化されたモジュールの一部です。|  
|**has_restricted_text**|**bit**|クエリ テキストには、パスワードまたはその他の unmentionable 単語が含まれています。|  
  
## <a name="permissions"></a>Permissions  
 必要があります、 **VIEW DATABASE STATE**権限です。  
  
## <a name="see-also"></a>参照  
 [sys.database_query_store_options &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys.query_context_settings &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys.query_store_plan &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [sys.query_store_query &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)   
 [sys.query_store_runtime_stats &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)   
 [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [sys.query_store_runtime_stats_interval &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [クエリのストアを使用した、パフォーマンスの監視](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [クエリ ストアのストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)   
 [sys.fn_stmt_sql_handle_from_sql_stmt &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql.md)  
  
  
