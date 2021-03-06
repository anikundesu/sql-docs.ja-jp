---
title: "ジョブの作成 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- jobs [SQL Server Agent], creating
- SQL Server Agent jobs, creating
ms.assetid: b35af2b6-6594-40d1-9861-4d5dd906048c
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 04fb45c80033381fdd8ab4e824bc1f93df23bfa7
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="create-a-job"></a>ジョブの作成
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] このトピックでは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]、[!INCLUDE[tsql](../../includes/tsql_md.md)]、または SQL Server 管理オブジェクト (SMO) を使用して、[!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] で SQL Server エージェント ジョブを作成する方法について説明します。  
  
オペレーターに送信できるジョブ ステップ、スケジュール、警告、および通知を追加するには、「参照」セクションのトピックをご覧ください。  
  
-   **作業を開始する準備:**  
  
    [制限事項と制約事項](#Restrictions)  
  
    [Security](#Security)  
  
-   **ジョブを作成する方法:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
    [SQL Server 管理オブジェクト](#SMOProcedure)  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Restrictions"></a>制限事項と制約事項  
  
-   ジョブを作成するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント固定データベース ロールか **sysadmin** 固定サーバー ロールのメンバーである必要があります。 ジョブの編集は、ジョブの所有者または **sysadmin** ロールのメンバーのみが行うことができます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント固定データベース ロールの詳細については、「 [SQL Server エージェントの固定データベース ロール](../../ssms/agent/sql-server-agent-fixed-database-roles.md)」を参照してください。  
  
-   別のログインにジョブを割り当てた場合に、新しい所有者がそのジョブを正常に実行できる十分な権限を持っていないこともあります。  
  
-   ローカル ジョブはローカル [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントによってキャッシュに格納されます。 したがって、ジョブを変更すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントは暗黙的にジョブをキャッシュに再登録します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] sp_add_jobserver **が呼び出されるまで** エージェントはジョブをキャッシュに格納しないので、 **sp_add_jobserver** を最後に呼び出す方が効率的です。  
  
### <a name="Security"></a>Security  
  
-   ジョブの所有者を変更するには、システム管理者でなければなりません。  
  
-   セキュリティを確保するため、ジョブの所有者または **sysadmin** ロールのメンバーだけがジョブの定義を変更できます。 **sysadmin** 固定サーバー ロールのメンバーのみが別のユーザーにジョブの所有権を割り当てることができ、ジョブの所有者とは無関係にジョブを実行できます。  
  
    > [!NOTE]  
    > ジョブの所有権を **sysadmin** 固定サーバー ロールのメンバーでないユーザーに変更し、そのジョブがプロキシ アカウントを必要とするジョブ ステップを実行する ( [!INCLUDE[ssIS](../../includes/ssis_md.md)] パッケージの実行など) 場合は、ユーザーがそのプロキシ アカウントにアクセスできることを確認してください。アクセスできない場合、ジョブは失敗します。  
  
#### <a name="Permissions"></a>Permissions  
詳細については、「 [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md)」をご覧ください。  
  
## <a name="SSMSProcedure"></a>SQL Server Management Studio の使用  
  
#### <a name="to-create-a-sql-server-agent-job"></a>SQL Server エージェントのジョブを作成するには  
  
1.  **オブジェクト エクスプローラー**で、SQL Server エージェント ジョブを作成するサーバーをプラス記号をクリックして展開します。  
  
2.  プラス記号をクリックして **[SQL Server エージェント]**を展開します。  
  
3.  **[ジョブ]** フォルダーを右クリックし、 **[新しいジョブ]**を選択します。  
  
4.  **[新しいジョブ]** ダイアログ ボックスの **[全般]** ページで、ジョブの全般的なプロパティを変更します。 このページで利用可能なオプションの詳細については、「[ジョブのプロパティ - [新しいジョブ] ([全般] ページ)](../../ssms/agent/job-properties-new-job-general-page.md)」を参照してください。  
  
5.  **[ステップ]** ページで、ジョブ ステップを編成します。 このページで利用可能なオプションの詳細については、「[ジョブのプロパティ - [新しいジョブ] ([全般] ページ)](../../ssms/agent/job-properties-new-job-steps-page.md)」を参照してください。  
  
6.  **[スケジュール** ] ページで、ジョブのスケジュールを編成します。 このページで利用可能なオプションの詳細については、「[ジョブのプロパティ - [新しいジョブ] ([スケジュール] ページ)](../../ssms/agent/job-properties-new-job-schedules-page.md)」を参照してください。  
  
7.  **[警告]** ページで、ジョブの警告を編成します。 このページで利用可能なオプションの詳細については、「[ジョブのプロパティ - [新しいジョブ] ([警告] ページ)](../../ssms/agent/job-properties-new-job-alerts-page.md)」を参照してください。  
  
8.  **[通知]** ページで、ジョブの完了時に [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントが実行するアクションを設定します。 このページで利用可能なオプションの詳細については、「[ジョブのプロパティ - [新しいジョブ] ([通知] ページ)](../../ssms/agent/job-properties-new-job-notifications-page.md)」を参照してください。  
  
9. **[ターゲット]** ページで、ジョブの対象サーバーを管理します。 このページで利用可能なオプションの詳細については、「[ジョブのプロパティ - [新しいジョブ] ([対象サーバー] ページ)](../../ssms/agent/job-properties-new-job-targets-page.md)」を参照してください。  
  
10. 完了したら、 **[OK]**をクリックします。  
  
## <a name="TsqlProcedure"></a>Transact-SQL の使用  
  
#### <a name="to-create-a-sql-server-agent-job"></a>SQL Server エージェントのジョブを作成するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde_md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。  
  
    ```  
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_job  
        @job_name = N'Weekly Sales Data Backup' ;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',  
        @freq_type = 1,  
        @active_start_time = 233000 ;  
    USE msdb ;  
    GO  
    EXEC sp_attach_schedule  
       @job_name = N'Weekly Sales Data Backup',  
       @schedule_name = N'RunOnce';  
    GO  
    EXEC dbo.sp_add_jobserver  
        @job_name = N'Weekly Sales Data Backup';  
    GO  
    ```  
  
詳細については、以下をご覧ください。  
  
-   [sp_add_job (Transact-SQL)](http://msdn.microsoft.com/en-us/6ca8fe2c-7b1c-4b59-b4c7-e3b7485df274)  
  
-   [sp_add_jobstep (Transact-SQL)](http://msdn.microsoft.com/en-us/97900032-523d-49d6-9865-2734fba1c755)  
  
-   [sp_add_schedule (Transact-SQL)](http://msdn.microsoft.com/en-us/9060aae3-3ddd-40a5-83bb-3ea7ab1ffbd7)  
  
-   [sp_attach_schedule (Transact-SQL)](http://msdn.microsoft.com/en-us/80c80eaf-cf23-4ed8-b8dd-65fe59830dd1)  
  
-   [sp_add_jobserver (Transact-SQL)](http://msdn.microsoft.com/en-us/485252cc-0081-490a-9bd1-cbbd68eea286)  
  
## <a name="SMOProcedure"></a>SQL Server 管理オブジェクトの使用  
**SQL Server エージェントのジョブを作成するには**  
  
Visual Basic、Visual C#、PowerShell などの選択したプログラミング言語で **Job** クラスの **Create** メソッドを呼び出します。 コード例については、「 [SQL Server エージェントでの自動管理タスクのスケジュール設定](http://msdn.microsoft.com/en-us/900242ad-d6a2-48e9-8a1b-f0eea4413c16)」を参照してください。  
  
