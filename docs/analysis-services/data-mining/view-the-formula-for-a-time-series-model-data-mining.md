---
title: "タイム シリーズの式の表示モデル (データ マイニング) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data mining [Analysis Services], how-to topics
- ARTXP
- time series algorithms [Analysis Services]
- ARIMA
- time series [Analysis Services]
- Time Series Viewer [Analysis Services]
ms.assetid: 825ef719-2f44-4979-be01-5a81f54e1a53
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: bb044b96eecbbb5c6eb18dcc33eae1807b2fe8b4
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="view-the-formula-for-a-time-series-model-data-mining"></a>タイム シリーズ モデルの式の表示 (データ マイニング)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]タイム シリーズ モデルを使用して、作成した場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Data Mining、モデルは、使用するは、回帰式を表示する最も簡単な方法、**マイニング凡例**の[Microsoft タイム シリーズ ビューアー](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-time-series-viewer.md)、すべての定数を判読可能な形式で表示します。  
  
### <a name="to-view-the-artxp-regression-formula-for-a-time-series-model"></a>タイム シリーズ モデルの ARTXP 回帰式を表示するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、表示するタイム シリーズ モデルを選択して、 **[参照]**をクリックします。  
  
     -- または --  
  
     [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、タイム シリーズ モデルを選択して、 **[マイニング モデル ビューアー]** タブをクリックします。  
  
2.  **[モデル]** タブをクリックします。  
  
3.  モデルに複数のツリーが含まれる場合は、 **[ツリー]** ボックスの一覧で 1 つのツリーを選択します。  
  
    > [!NOTE]  
    >  複数のデータ系列がある場合、モデルには必ず複数のツリーが含まれます。 ただし、 **タイム シリーズ ビューアー** では、 [Microsoft 汎用コンテンツ ツリー ビューアー](http://msdn.microsoft.com/library/751b4393-f6fd-48c1-bcef-bdca589ce34c)ほど多くのツリーは表示されません。 これは、タイム シリーズ ビューアーが、データ系列ごとに ARIMA と ARTXP の情報を 1 つの表現にまとめるためです。  
  
4.  ツリーの任意のリーフ ノードをクリックします。  
  
     **[データ系列]** というラベルのノードは常にリーフ ノードであり、式を含むことができます。 **[(すべて)]** ノードに子ノードがない場合も、式を含むことができます。  
  
5.  **[マイニング凡例]** が表示されない場合は、ノードを右クリックし、 **[凡例の表示]**をクリックします。  
  
     ARTXP 式は、 **[マイニング凡例]**の前半に、 **[ツリー ノード式]**として表示されます。  
  
     ![タイム シリーズ式の凡例に表示](../../analysis-services/data-mining/media/ssdm-timeserieslegend.png "凡例でタイム シリーズ式の表示")  
  
### <a name="to-view-the-arima-formula-for-a-time-series-model"></a>タイム シリーズ モデルの ARIMA 式を表示するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、表示するタイム シリーズ モデルを選択して、 **[参照]**をクリックします。  
  
     -- または --  
  
     [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、タイム シリーズ モデルを選択して、 **[マイニング モデル ビューアー]** タブをクリックします。  
  
2.  **[モデル]** タブをクリックします。  
  
3.  モデルに複数のツリーが含まれる場合は、 **[ツリー]** ボックスの一覧で 1 つのツリーを選択します。  
  
    > [!NOTE]  
    >  複数のデータ系列がある場合、モデルには必ず複数のツリーが含まれます。  
  
4.  ツリーの任意のノードをクリックします。  
  
     ARIMA 式は、 **[マイニング凡例]**の後半に、 **[ARIMA 式]**として表示されます。  
  
5.  **[マイニング凡例]** が表示されない場合は、ノードを右クリックし、 **[凡例の表示]**をクリックします。  
  
### <a name="to-get-the-coefficients-and-terms-for-the-equation"></a>式の係数と項を取得するには  
  
1.  モデル コンテンツに **コンテンツ クエリ** を作成することで、タイム シリーズ モデルの回帰式の項と係数を取得することもできます。  
  
     詳細については、「 [タイム シリーズ モデルのクエリ例](../../analysis-services/data-mining/time-series-model-query-examples.md)」を参照してください。  
  
2.  [Microsoft 汎用コンテンツ ツリー ビューアー](http://msdn.microsoft.com/library/751b4393-f6fd-48c1-bcef-bdca589ce34c)を使用することで、タイム シリーズ モデルを参照して項や係数を探すこともできます。  
  
     詳細については、「[タイム シリーズ モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md)」を参照してください。  
  
    > [!NOTE]  
    >  ARIMA モデルと ARTXP モデルの両方を使用する混在モデルのコンテンツを参照すると、2 つのモデルは別のツリーにあり、モデルを表すルート ノードで結合されています。 ARIMA モデルと ARTXP モデルは便宜上 1 つのビューアーで表示されますが、式と同様に構造はまったく異なり、結合も比較もできません。 ARTXP ツリーはデシジョン ツリーにより近く、ARIMA ツリーは一連の移動平均を表します。  
  
## <a name="see-also"></a>参照  
 [マイニング モデル ビューアーのタスクと操作方法](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [Microsoft タイム シリーズ ビューアーを使用したモデルの参照](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-time-series-viewer.md)  
  
  
