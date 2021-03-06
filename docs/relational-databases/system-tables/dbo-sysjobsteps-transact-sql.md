---
title: "dbo.sysjobsteps (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.sysjobsteps
- dbo.sysjobsteps_TSQL
- sysjobsteps
- sysjobsteps_TSQL
dev_langs: TSQL
helpviewer_keywords: sysjobsteps system table
ms.assetid: 978b8205-535b-461c-91f3-af9b08eca467
caps.latest.revision: "28"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 4f316e40cc6bf89cf7296b5a2d864406142f7f87
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="dbosysjobsteps-transact-sql"></a>dbo.sysjobsteps (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによって実行されるジョブ内の各ステップに関する情報を格納します。 次の表は、 **msdb**データベース。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|ジョブの ID です。|  
|**step_id**|**int**|ジョブ ステップの ID。|  
|**step_name**|**sysname**|ジョブ ステップの名前です。|  
|**サブシステム**|**nvarchar (40)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントがジョブ ステップを実行するために使用するサブシステムの名前。|  
|**command**|**nvarchar(max)**|によって実行されるコマンド**サブシステム**です。|  
|**フラグ**|**int**|予約されています。|  
|**@additional_parameters**|**ntext**|予約されています。|  
|**cmdexec_success_code**|**int**|によって返されるエラー レベル値**CmdExec**サブシステム ステップが成功を示します。|  
|**on_success_action**|**tinyint**|ステップが正常に実行されたときに行う操作。|  
|**on_success_step_id**|**int**|ステップが正常に実行されたときに実行する次のステップの ID。|  
|**on_fail_action**|**tinyint**|ステップが正常に実行されないときに行う操作。|  
|**on_fail_step_id**|**int**|ステップが正常に実行されないときに実行する次のステップの ID。|  
|**サーバー (server)**|**sysname**|予約されています。|  
|**database_name**|**sysname**|対象となるデータベースの名前**コマンド**場合に実行される**サブシステム**TSQL がします。|  
|**@database_user_name**|**sysname**|ステップを実行するときにアカウントが使用されるデータベース ユーザー名。|  
|**retry_attempts**|**int**|ステップが失敗するときに行う再試行の回数。|  
|**retry_interval**|**int**|再試行の間隔。|  
|**os_run_priority**|**int**|予約されています。|  
|**output_file_name**|**nvarchar (200)**|ステップの出力ファイルの名前が保存された**サブシステム**が TSQL、PowerShell、または**CmdExec***です。*|  
|**last_run_outcome**|**int**|ジョブ ステップの前回の実行結果。<br /><br /> **0** = に失敗しました<br /><br /> **1** = に成功しました<br /><br /> **2** = 再試行<br /><br /> **3** = キャンセル<br /><br /> **5** = unknown|  
|**last_run_duration**|**int**|前回実行時のステップの実行時間 (hhmmss)。|  
|**last_run_retries**|**int**|ジョブ ステップの前回の実行で行われた再試行の回数。|  
|**last_run_date**|**int**|ステップの実行を最後に開始した日付 (yyyymmdd)。|  
|**last_run_time**|**int**|ステップの実行を最後に開始した時刻 (hhmmss)。|  
|**proxy_id**|**int**|ジョブ ステップのプロキシ。|  
|**step_uid**|**uniqueidentifier**|ジョブ ステップの識別子。|  
  
## <a name="see-also"></a>参照  
 [SQL Server エージェント テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)  
  
  
