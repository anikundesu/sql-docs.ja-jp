---
title: "sp_changedynamicsnapshot_job (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_changedynamicsnapshot_job
- sp_changedynamicsnapshot_job_TSQL
helpviewer_keywords: sp_changedynamicsnapshot_job
ms.assetid: ea0dacd2-a5fd-42f4-88dd-7d289b0ae017
caps.latest.revision: "28"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3c7c2aaa546d1951117c39835ae2a285d3533a78
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spchangedynamicsnapshotjob-transact-sql"></a>sp_changedynamicsnapshot_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パブリケーションへのサブスクリプション用にスナップショットを生成するエージェント ジョブを、パラメーター化された行フィルターを使って変更します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_changedynamicsnapshot_job [ @publication = ] 'publication'  
    [ , [ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname' ]  
    [ , [ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid' ]  
    [ , [ @frequency_type = ] frequency_type ]   
    [ , [ @frequency_interval = ] frequency_interval ]   
    [ , [ @frequency_subday = ] frequency_subday ]   
    [ , [ @frequency_subday_interval = ] frequency_subday_interval ]   
    [ , [ @frequency_relative_interval = ] frequency_relative_interval ]   
    [ , [ @frequency_recurrence_factor = ] frequency_recurrence_factor ]   
    [ , [ @active_start_date = ] active_start_date ]   
    [ , [ @active_end_date = ] active_end_date ]   
    [ , [ @active_start_time_of_day = ] active_start_time_of_day ]   
    [ , [ @active_end_time_of_day = ] active_end_time_of_day ]   
    [ , [ @job_login = ] 'job_login' ]   
    [ , [ @job_password = ] 'job_password' ]   
```  
  
## <a name="arguments"></a>引数  
 [  **@publication =** ] **'***パブリケーション***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@dynamic_snapshot_jobname =** ] **'***dynamic_snapshot_jobname***'**  
 変更するスナップショット ジョブの名前を指定します。 *dynamic_snapshot_jobname*は**sysname**既定値は N '%' です。 場合*dynamic_snapshot_jobid*を指定すると、既定値を使用する必要があります*dynamic_snapshot_jobname*です。  
  
 [  **@dynamic_snapshot_jobid =** ] **'***dynamic_snapshot_jobid***'**  
 変更するスナップショット ジョブの ID を指定します。 *dynamic_snapshot_jobid*は**uniqueidentifier**既定値は NULL です。 場合*dynamic_snapshot_jobname*を指定すると、既定値を使用する必要があります*dynamic_snapshot_jobid*です。  
  
 [  **@frequency_type =** ] *frequency_type*  
 エージェントをスケジュールに組み込む頻度を指定します。 *frequency_type*は**int**値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|指定日時|  
|**2**|[要求時]|  
|**4**|毎日。|  
|**8**|毎週。|  
|**16**|毎月。|  
|**32**|月単位|  
|**64**|自動的に起動|  
|**128**|定期的|  
|NULL (既定値)||  
  
 [  **@frequency_interval =** ] *frequency_interval*  
 エージェントを実行する日を指定します。 *frequency_interval*は**int**値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|日曜日|  
|**2**|月曜日|  
|**3**|火曜日|  
|**4**|水曜日|  
|**5**|木曜日|  
|**6**|金曜日|  
|**7**|土曜日|  
|**8**|日|  
|**9**|平日|  
|"**10**"|週末の曜日|  
|NULL (既定値)||  
  
 [  **@frequency_subday =** ] *frequency_subday*  
 定義した期間にスケジュールを組み直す頻度を指定します。 *frequency_subday*は**int**値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|1 回。|  
|**2**|第 2 週|  
|**4**|Minute|  
|**8**|Hour|  
|NULL (既定値)||  
  
 [  **@frequency_subday_interval =** ] *frequency_subday_interval*  
 間隔は、 *frequency_subday*です。 *frequency_subday_interval*は**int**、既定値は NULL です。  
  
 [  **@frequency_relative_interval =** ] *frequency_relative_interval*  
 マージ エージェントを実行する日付を指定します。 このパラメーターが使用されるときに*frequency_type*に設定されている**32** (月単位)。 *frequency_relative_interval*は**int**値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|First|  
|**2**|第 2 週|  
|**4**|第 3 週|  
|**8**|第 4 週|  
|**16**|Last|  
|NULL (既定値)||  
  
 [  **@frequency_recurrence_factor =** ] *frequency_recurrence_factor*  
 によって使用される定期実行係数*frequency_type*です。 *frequency_recurrence_factor*は**int**、既定値は NULL です。  
  
 [  **@active_start_date =** ] *active_start_date*  
 マージ エージェントを最初にスケジュール設定する日付を YYYYMMDD 形式で指定します。 *active_start_date*は**int**、既定値は NULL です。  
  
 [  **@active_end_date =** ] *active_end_date*  
 マージ エージェントのスケジュール設定を停止する日付を YYYYMMDD 形式で指定します。 *active_end_date*は**int**、既定値は NULL です。  
  
 [  **@active_start_time_of_day =** ] *active_start_time_of_day*  
 マージ エージェントを最初にスケジュール設定する時刻を HHMMSS 形式で指定します。 *active_start_time_of_day*は**int**、既定値は NULL です。  
  
 [  **@active_end_time_of_day =** ] *active_end_time_of_day*  
 マージ エージェントのスケジュール設定を停止する時刻を HHMMSS 形式で指定します。 *active_end_time_of_day*は**int**、既定値は NULL です。  
  
 [  **@job_login=** ] **'***job_login***'**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)]パラメーター化された行フィルターを使用してサブスクリプションのスナップショットを生成するときに、スナップショット エージェントを実行する Windows アカウントです。 *job_login*は**nvarchar (257)**既定値は NULL です。  
  
 [  **@job_password=** ] **'***job_password***'**  
 パラメーター化された行フィルターを使ってサブスクリプション用のスナップショットを生成するときに、スナップショット エージェントを実行する Windows アカウントのパスワードを指定します。 *job_password*は**nvarchar (257)**既定値は NULL です。  
  
> [!IMPORTANT]  
>  可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_changedynamicsnapshot_job**はパブリケーションのパラメーター化された行フィルターを使用してマージ レプリケーションで使用します。  
  
 エージェントのログインまたはパスワードを変更した後、変更を有効にするには、エージェントを停止して再起動する必要があります。  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_changedynamicsnapshot_job**です。  
  
## <a name="see-also"></a>参照  
 [レプリケーションのセキュリティ設定の表示および変更](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [パラメーター化されたフィルターを使用したマージ パブリケーションのスナップショット](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)  
  
  
