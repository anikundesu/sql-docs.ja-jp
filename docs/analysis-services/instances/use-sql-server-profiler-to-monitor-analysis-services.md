---
title: "SQL Server Profiler を使用して、Analysis Services の監視を |Microsoft ドキュメント"
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
- performance [Analysis Services], SQL Server Profiler
- Profiler [SQL Server Profiler], Analysis Services
ms.assetid: 8b77dafc-4584-4e93-8ad7-299304391bfd
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 7373a2d4933ddfab5d784a90422df83d985d01ca
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="use-sql-server-profiler-to-monitor-analysis-services"></a>SQL Server Profiler を使用した Analysis Services の監視
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)][!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]ので (ユーザー クエリまたはログインの利用状況など) は、サーバーとデータベースの動作を監視できるように、それらのイベントに関するデータをキャプチャするバッチまたはトランザクションの開始などのエンジン プロセス イベントを追跡します。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] のデータを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルまたはファイルにキャプチャして、後で分析できます。また、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の同じインスタンスまたは別のインスタンスでキャプチャしたイベントを再生して、何が起こったかを正確に確認することもできます。 イベントはリアルタイムまたはステップごとに再生できます。 また、同じコンピューター上のパフォーマンス カウンターと共にトレース イベントを実行すると非常に役立ちます。 このプロファイラーでは、これらの 2 つを時間に基づいて関連付けることができます。また、1 つの時間軸で同時に表示できます。 パフォーマンス カウンターは集計を表示しますが、トレース イベントではより詳細なデータが得られます。 トレースを作成および実行する方法については、「 [再生用のプロファイラー トレースの作成 &#40;Analysis Services&#41;](../../analysis-services/instances/create-profiler-traces-for-replay-analysis-services.md)」を参照してください。  
  
 このトピックでは、次の内容について紹介します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[SQL Server Profiler による Analysis Services の監視の概要](../../analysis-services/instances/introduction-to-monitoring-analysis-services-with-sql-server-profiler.md)|[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用して [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスを監視する方法について説明します。|  
|[再生用のプロファイラー トレースの作成 &#40;Analysis Services&#41;](../../analysis-services/instances/create-profiler-traces-for-replay-analysis-services.md)|[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して再生用トレースを作成するための要件について説明します。|  
|[Analysis Services トレース イベント](../../analysis-services/trace-events/analysis-services-trace-events.md)|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のイベント クラスについて説明します。 これらのイベント クラスは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって生成されるアクションにマップされ、トレースの再生に使用されます。|  
  
## <a name="see-also"></a>参照  
 [Analysis Services インスタンスの監視](../../analysis-services/instances/monitor-an-analysis-services-instance.md)  
  
  
