---
title: "SQL Server Profiler による Analysis Services の監視の概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Profiler, Analysis Services
- monitoring Analysis Services [SQL Server]
- performance [Analysis Services]
- performance [Analysis Services], SQL Server Profiler
- Profiler [SQL Server Profiler], Analysis Services
ms.assetid: 568ec549-5ddc-493a-b9f8-3bdc548b562e
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2156c8c1135cf0c6cd9c3a514143dedbfcd1a387
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="introduction-to-monitoring-analysis-services-with-sql-server-profiler"></a>SQL Server Profiler による Analysis Services の監視の概要
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]使用することができます[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]のインスタンスによって生成されたイベントを監視する[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]です。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用すると、次の操作を実行できます。  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスのパフォーマンスの監視。  
  
-   多次元式 (MDX) ステートメントのデバッグ。  
  
-   実行速度が遅い MDX ステートメントの特定。  
  
-   ステートメントをステップ実行してコードが期待どおりに機能するかどうかを確認する、プロジェクトの開発段階での MDX ステートメントのテスト。  
  
-   実稼動システムでイベントをキャプチャし、テスト システムでそのイベントを再生することによって行う [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の問題のトラブルシューティング。 この方法はテストまたはデバッグのときに便利です。ユーザーは実稼動システムの使用を中断しなくて済みます。  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスで発生した利用状況の監査と検討。 セキュリティ管理者は、すべての監査イベントを確認できます。 これには、ログイン試行の成否や、ステートメントおよびオブジェクトへのアクセス権チェックの成否が含まれます。  
  
-   キャプチャされたイベントに関するデータの画面表示、各イベントに関するデータのキャプチャ、および今後の分析や再生を目的としたファイルまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルへのデータの保存。 データを再生する場合は、保存されているイベントを当初の発生時と同じ状態で、リアルタイムまたは 1 ステップずつ再実行できます。  
  
## <a name="using-sql-server-profiler"></a>SQL Server Profiler の使用  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用してトレースを作成または再生するには、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバー ロールのメンバーでなければなりません。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバー ロールのメンバーであれば、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] [スタート] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]   **プログラム グループから** を起動できます。  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用する場合は、次の点に注意してください。  
  
-   トレース定義は、CREATE ステートメントを使用して [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースに保存されます。  
  
-   複数のトレースを同時に実行できます。  
  
-   複数の接続を使用して、同じトレースからイベントを受け取ることができます。  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を停止しても、再起動するとトレースを続行できます。  
  
    > [!NOTE]  
    >  パスワードはトレース イベントに表示されず、****** に置換されます。  
  
 パフォーマンスを最適化するために、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用する場合は、最も関心のあるイベントだけを監視してください。 監視するイベントが多すぎると、特に監視が長時間に及ぶ場合は、オーバーヘッドが増加し、トレース ファイルやトレース テーブルが非常に大きくなる可能性があります。 また、フィルター機能を使用して、収集するデータの量を制限し、トレースがあまり大きくならないようにしてください。  
  
## <a name="see-also"></a>参照  
 [Analysis Services トレース イベント](../../analysis-services/trace-events/analysis-services-trace-events.md)   
 [再生用のプロファイラー トレースの作成 &#40;Analysis Services&#41;](../../analysis-services/instances/create-profiler-traces-for-replay-analysis-services.md)  
  
  
