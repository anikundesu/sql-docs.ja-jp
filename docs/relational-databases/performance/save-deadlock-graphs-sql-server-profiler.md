---
title: "Deadlock Graph の保存 (SQL Server Profiler) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deadlocks [SQL Server], saving deadlock graphs
- graphs [SQL Server]
- saving deadlock graphs
ms.assetid: bf1fc906-abd6-4a89-842e-da0d66b2defe
caps.latest.revision: "26"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 92eecce1715fa172a17b849711ba6f9cc09cfbb8
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="save-deadlock-graphs-sql-server-profiler"></a>Deadlock Graph の保存 (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] このトピックでは、[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用して Deadlock Graph を保存する方法について説明します。 Deadlock Graph は XML ファイルとして保存されます。  
  
## <a name="save-deadlock-graph-events-separately"></a>Deadlock Graph のイベントを個別に保存する  
  
1. **[ファイル]** メニューの **[新しいトレース]** を選択し、SQL Server のインスタンスに接続します。  
  
     **[トレースのプロパティ]** ダイアログ ボックスが表示されます。  
  
    > [!NOTE]  
    >  **[接続の確立直後にトレースを開始する]** チェック ボックスがオンになっている場合、**[トレースのプロパティ]** ダイアログ ボックスは表示されず、すぐにトレースが開始されます。 この設定を無効にするには、**[ツール]** メニューの **[オプション]** を選択し、**[接続の確立直後にトレースを開始する]** チェック ボックスをオフにします。  
  
2. **[トレースのプロパティ]** ダイアログ ボックスの **[トレース名]** ボックスに、トレースの名前を入力します。  
  
3. **[使用するテンプレート]** の一覧から、トレースの基にするトレース テンプレートを選択します。 テンプレートを使用しない場合は **[空白]** を選択します。  
  
4. 次のいずれかの操作を行います。  
  
    -   トレースをファイルにキャプチャするには、**[ファイルに保存]** チェック ボックスをオンにします。 **[最大ファイル サイズの設定]**ボックスに値を指定します。  
  
         必要に応じて、 **[ファイル ロールオーバーを有効にする]** および **[サーバーがトレース データを処理する]** チェック ボックスをオンにします。 
  
    -   トレースをデータベース テーブルにキャプチャするには、**[テーブルに保存する]** チェック ボックスをオンにします。  
  
         必要に応じて、**[最大行数の設定 (1000 行単位)]** チェック ボックスをオンにし、値を指定します。  
  
5. 必要に応じて、 **[トレース停止時刻を有効にする]** チェック ボックスをオンにして、停止日時を指定します。 
  
6. **[イベントの選択]** タブを選択します。  
  
7. **[Events]** データ列で、**[Locks]** イベント カテゴリを展開し、**[Deadlock graph]** チェック ボックスをオンにします。 **Locks** イベント カテゴリが表示されない場合は、**[すべてのイベントを表示する]** チェック ボックスをオンにして表示します。  
  
     **[トレースのプロパティ]** ダイアログ ボックスに **[イベント抽出の設定]** タブが追加されます。  
  
8. **[イベント抽出の設定]** タブで、**[デッドロック XML イベントを個別に保存する]** を選択します。  
  
9. **[名前を付けて保存]** ダイアログ ボックスで、Deadlock Graph のイベントを格納するファイル名を入力します。  
  
10. 1 つの XML ファイルにすべての Deadlock Graph イベントを保存するには、**[1 つのファイルにすべてのデッドロック XML バッチを保存する]** を選択します。 または、Deadlock Graph ごとに新しい XML ファイルを作成するには、**[個別のファイルに各デッドロック XML バッチを保存する]** を選択します。  
  
 デッドロック ファイルを保存した後は、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でファイルを開くことができます。 詳細については、「[デッドロック ファイルを開く、表示、および印刷する方法 &#40;SQL Server Management Studio&#41;](../../relational-databases/performance/open-view-and-print-a-deadlock-file-sql-server-management-studio.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server Profiler を使用したデッドロックの分析](../../tools/sql-server-profiler/analyze-deadlocks-with-sql-server-profiler.md)  
  
  
