---
title: "sys.dm_db_session_space_usage (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/16/2015
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_db_session_space_usage_TSQL
- dm_db_session_space_usage
- sys.dm_db_session_space_usage
- sys.dm_db_session_space_usage_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_db_session_space_usage dynamic management view
ms.assetid: a67a6045-8e14-460a-9fe3-912b846c08c1
caps.latest.revision: "34"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: aa15cafb701cc1b21d6e8f821805a12cb96eba9f
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmdbsessionspaceusage-transact-sql"></a>sys.dm_db_session_space_usage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  データベースの各セッションで割り当てられた、または割り当て解除されたページの数を返します。  
  
> [!NOTE]  
>  このビューはのみに適用できる、 [tempdb データベース](../../relational-databases/databases/tempdb-database.md)です。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_db_session_space_usage**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**smallint**|セッション ID。<br /><br /> **session_id**にマップ**session_id**で[sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)です。|  
|**database_id**|**smallint**|データベース ID。|  
|**user_objects_alloc_page_count**|**bigint**|セッションで、ユーザー オブジェクトに予約された、または割り当てられたページの数。|  
|**user_objects_dealloc_page_count**|**bigint**|セッションで、ユーザー オブジェクトへの割り当てが解除され、予約されなくなったページの数。|  
|**internal_objects_alloc_page_count**|**bigint**|セッションで、内部オブジェクトに予約された、または割り当てられたページの数。|  
|**internal_objects_dealloc_page_count**|**bigint**|セッションで、内部オブジェクトへの割り当てが解除され、予約されなくなったページの数。|  
|**user_objects_deferred_dealloc_page_count**|**bigint**|遅延割り当て解除のマークされているページ数です。<br /><br /> **注:**のサービス パックで導入された[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]と[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]です。|  
|**pdw_node_id**|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Premium 階層には、データベースの VIEW DATABASE STATE 権限が必要です。 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Standard および Basic 階層が必要です、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]管理者アカウントです。  
  
## <a name="remarks"></a>解説  
 このビューでレポートされる割り当てまたは割り当て解除の数に、IAM ページは含まれません。  
  
 ページ カウンターはセッションの開始時に 0 に初期化されます。 このカウンターによって、セッションで完了したタスクに割り当てられた、または割り当て解除されたページの合計数が記録されます。 カウンターはタスクが終了したときにだけ更新され、実行中のタスクは反映されません。  
  
 1 つのセッションでは同時に複数の要求をアクティブにできます。 要求が並列クエリの場合、複数のスレッドやタスクを開始できます。  
  
 セッション、要求、およびタスクの詳細については、次を参照してください。 [sys.dm_exec_sessions &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)、 [sys.dm_exec_requests &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)、および[sys.dm_os_tasks と組み合わせます &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md).  
  
## <a name="user-objects"></a>ユーザー オブジェクト  
 次のオブジェクトは、ユーザー オブジェクト ページ カウンターに含まれます。  
  
-   ユーザー定義テーブルとインデックス  
  
-   システム テーブルとインデックス  
  
-   グローバル一時テーブルとインデックス  
  
-   ローカル一時テーブルとインデックス  
  
-   テーブル変数  
  
-   テーブル値関数で返されるテーブル  
  
## <a name="internal-objects"></a>内部オブジェクト  
 内部オブジェクトにのみ含まれる**tempdb**です。 次のオブジェクトは、内部オブジェクト ページ カウンターに含まれます。  
  
-   カーソルまたはスプール操作と一時的なラージ オブジェクト (LOB) の記憶域用の作業テーブル  
  
-   ハッシュ結合などの操作用の作業ファイル  
  
-   並べ替え実行結果  
  
## <a name="physical-joins"></a>物理結合  
 ![Sys.dm_db_session_space_usage の物理結合](../../relational-databases/system-dynamic-management-views/media/join-dm-db-session-space-usage-1.gif "sys.dm_db_session_space_usage の物理の結合")  
  
## <a name="relationship-cardinalities"></a>リレーションシップの基数  
  
|From|変換先|リレーションシップ|  
|----------|--------|------------------|  
|dm_db_session_space_usage.session_id|dm_exec_sessions.session_id|一対一|  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [データベース関連の動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_exec_sessions &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)   
 [sys.dm_exec_requests &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [sys.dm_os_tasks と組み合わせます &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md)   
 [sys.dm_db_task_space_usage &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-db-task-space-usage-transact-sql.md)   
 [sys.dm_db_file_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-file-space-usage-transact-sql.md)  
  
  



