---
title: "sys.dm_exec_background_job_queue (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2016
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
- dm_exec_background_job_queue
- sys.dm_exec_background_job_queue_TSQL
- dm_exec_background_job_queue_TSQL
- sys.dm_exec_background_job_queue
dev_langs: TSQL
helpviewer_keywords: sys.dm_exec_background_job_queue dynamic management function
ms.assetid: 05d9884f-b74c-4e3c-a23b-c90c1ea5ef02
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a19fc2817900e8f3c2e618296d650ac92ec2b6fa
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmexecbackgroundjobqueue-transact-sql"></a>sys.dm_exec_background_job_queue (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  非同期 (バックグラウンド) で実行するようスケジュール設定されたクエリ プロセッサ ジョブごとに 1 行のデータを返します。  
  
> **注:** これから **[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]** または **[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]** 、名前を使用して**sys.dm_pdw_nodes_exec_background_job_queue**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**time_queued**|**datetime**|ジョブがキューに追加された時刻。|  
|**job_id**|**int**|ジョブ識別子。|  
|**database_id**|**int**|ジョブが実行されるデータベース。|  
|**object_id1**|**int**|値はジョブの種類によって異なります。 詳細については、「解説」を参照してください。|  
|**object_id2**|**int**|値はジョブの種類によって異なります。 詳細については、「解説」を参照してください。|  
|**object_id3**|**int**|値はジョブの種類によって異なります。 詳細については、「解説」を参照してください。|  
|**object_id4**|**int**|値はジョブの種類によって異なります。 詳細については、「解説」を参照してください。|  
|**error_code**|**int**|ジョブが失敗し、再挿入された場合のエラー コード。 ジョブが中断したか、取得されていないか、完了している場合は NULL です。|  
|**request_type**|**smallint**|ジョブ要求の種類。|  
|**retry_count**|**smallint**|ジョブがキューから取得され、リソース不足またはその他の理由で再挿入された回数。|  
|**in_progress**|**smallint**|ジョブが実行を開始したかどうかを示します。<br /><br /> 1 = 開始<br /><br /> 0 = 待機中|  
|**session_id**|**smallint**|セッション識別子。|  
|**pdw_node_id**|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Premium 階層には、データベースの VIEW DATABASE STATE 権限が必要です。 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Standard および Basic 階層が必要です、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]管理者アカウントです。  
  
## <a name="remarks"></a>解説  
 このビューは、統計の非同期更新ジョブに関する情報のみを返します。 統計の非同期更新の詳細については、次を参照してください。[統計](../../relational-databases/statistics/statistics.md)です。  
  
 値**object_id1**を通じて**object_id4**ジョブ要求の種類によって異なります。 次の表は、それぞれのジョブの種類の列に関する説明です。  
  
|要求の種類|object_id1|object_id2|object_id3|object_id4|  
|------------------|-----------------|-----------------|-----------------|-----------------|  
|統計の非同期更新|テーブルまたはビュー ID|統計 ID|使用しない|使用しない|  
  
## <a name="examples"></a>使用例  
 次の例では、アクティブな非同期ジョブの数を返しますのインスタンス内の各データベースのバック グラウンド キューに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
```  
SELECT DB_NAME(database_id) AS [Database], COUNT(*) AS [Active Async Jobs]  
FROM sys.dm_exec_background_job_queue  
WHERE in_progress = 1  
GROUP BY database_id;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [実行関連の動的管理ビューおよび関数 &#40;TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [統計情報](../../relational-databases/statistics/statistics.md)   
 [KILL STATS JOB と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/kill-stats-job-transact-sql.md)  
  
  



