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
ms.assetid: 465fb7fc-7622-4252-a178-ea51691c935b
caps.latest.revision: "3"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 9b8a6a9fdae56ee2c0c73966e44182dafbceb5f9
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="create-jobs"></a>ジョブの作成
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] ジョブとは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントによって順番に実行される一連の操作です。 ジョブは、 [!INCLUDE[tsql](../../includes/tsql_md.md)] スクリプト、コマンド プロンプト アプリケーション、Microsoft ActiveX スクリプト、Integration Services パッケージ、Analysis Services コマンドおよびクエリ、レプリケーション タスクの実行など、広範な操作を実行できます。 ジョブは、反復的なタスクやスケジュール可能なタスクを実行でき、警告を発生させてジョブのステータスをユーザーに自動的に通知できるので、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] の管理が非常に簡単になります。  
  
ジョブを作成するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント固定データベース ロールか **sysadmin** 固定サーバー ロールのメンバーである必要があります。 ジョブの編集は、ジョブの所有者または **sysadmin** ロールのメンバーのみが行うことができます。 **sysadmin** ロールのメンバーは、別のユーザーにジョブの所有権を割り当てることができ、そのユーザーはジョブの所有者とは無関係にジョブを実行できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント固定データベース ロールの詳細については、「 [SQL Server エージェントの固定データベース ロール](../../ssms/agent/sql-server-agent-fixed-database-roles.md)」を参照してください。  
  
ジョブは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] のローカル インスタンスまたは企業全体の複数のインスタンスで実行するように記述できます。 複数のサーバーでジョブを実行するには、最低 1 つのマスター サーバーと 1 つ以上の対象サーバーをセットアップする必要があります。 マスター サーバーと対象サーバーの詳細については、「 [エンタープライズ全体の管理の自動化](../../ssms/agent/automated-administration-across-an-enterprise.md)」をご覧ください。  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントにより、ジョブとジョブ ステップの情報がジョブ履歴に記録されます。  
  
## <a name="related-tasks"></a>Related Tasks  
  
|||  
|-|-|  
|**[説明]**|**トピック**|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント ジョブを作成する方法について説明します。|[ジョブの作成](../../ssms/agent/create-a-job.md)|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントのジョブの所有権を他のユーザーに再割り当てする方法について説明します。|[Give Others Ownership of a Job](../../ssms/agent/give-others-ownership-of-a-job.md)|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントのジョブ履歴ログをセットアップする方法について説明します。|[Set Up the Job History Log](../../ssms/agent/set-up-the-job-history-log.md)|  
  
## <a name="see-also"></a>参照  
[ジョブ ステップの管理](../../ssms/agent/manage-job-steps.md)  
[エンタープライズ全体の管理の自動化](../../ssms/agent/automated-administration-across-an-enterprise.md)  
[スケジュールの作成とジョブへのアタッチ](../../ssms/agent/create-and-attach-schedules-to-jobs.md)  
[ジョブの実行](../../ssms/agent/run-jobs.md)  
[ジョブの表示または変更](../../ssms/agent/view-or-modify-jobs.md)  
  
