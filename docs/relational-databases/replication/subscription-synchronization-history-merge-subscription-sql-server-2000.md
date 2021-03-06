---
title: "サブスクリプション、[同期の履歴](マージ サブスクリプション、SQL Server 2000) | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.monitor.subscription.downlevelsynchhistory.f1
ms.assetid: 0a0deab2-1c08-4371-9681-d9403e0236cc
caps.latest.revision: "19"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 66c6a085eb2879d9ad9d7ee19036d64af553fea5
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="subscription-synchronization-history-merge-subscription-sql-server-2000"></a>サブスクリプション、[同期の履歴] (マージ サブスクリプション、SQL Server 2000)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] **[同期の履歴]** タブには、マージ エージェントの状態、履歴、情報メッセージ、エラー メッセージなどの詳細情報が表示されます。  
  
## <a name="options"></a>オプション  
 表示するマージ エージェント セッションを **[表示]** メニューで選択した後、 **[マージ エージェントのセッション]**という名前のグリッドで特定のセッションを選択します。 このセッションの詳細情報は、 **[選択されたセッションのアクション]**というラベルのグリッドに表示されます。 選択したセッションがエラーで終了した場合は、 **[選択されたセッションのエラーの詳細またはメッセージ]** というラベルのテキスト領域も表示されます。  
  
 **[表示]**  
 表示するマージ エージェント セッションを選択します。 一般的に、マージ エージェントは継続的に実行されるため、表示されるセッションが 1 つのみである場合もあります。  
  
 **[状態]**  
 マージ エージェントの状態です。 表示される状態の種類を、次に示します。  
  
-   [エラー]  
  
-   [完了]  
  
-   [再試行中]  
  
-   実行中  
  
 **Start Time**  
 セッションの開始時刻です。  
  
 **[終了時刻]**  
 セッションの終了時刻です。 エージェントが停止していない場合は、このフィールドは空になっています。  
  
 **Duration**  
 このセッションでマージ エージェントが実行された時間の合計です。 エージェントが現在実行中の場合、経過時間を表します。エージェントが終了している場合、セッションの合計時間を表します。  
  
 **エラー メッセージ**  
 セッションがエラーで終了した場合、このフィールドにはマージ エージェントによってログに記録された最後のエラー メッセージが表示されます。 セッションがエラーで終了しなかった場合は、このフィールドは空白です。  
  
 **[動作メッセージ]**  
 選択したセッション中にマージ エージェントによって記録された、すべての情報メッセージとエラー メッセージです。  
  
 **[動作時間]**  
 **[動作メッセージ]** 列で説明されたアクションが実行された時間です。  
  
 **[選択されたセッションのエラーの詳細またはメッセージ]**  
 選択したセッションの **[状態]** 列に **[エラー]** の値が表示されている場合にのみ表示されます。 このテキスト領域では、エラーの詳細情報とエラーの発生時に試行されたコマンドが表示されます。 エラーに関連する追加コンテンツへのリンクも含まれます。  
  
## <a name="see-also"></a>参照  
 [レプリケーション モニターの開始](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [サブスクリプションに関連付けられているエージェントの情報を表示し、タスクを実行する &#40;レプリケーション モニター&#41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-subscription-agents.md)   
 [レプリケーションの監視](../../relational-databases/replication/monitor/monitoring-replication-overview.md)   
 [Replication Agents Overview](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  
