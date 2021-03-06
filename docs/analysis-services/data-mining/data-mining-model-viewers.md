---
title: "データ マイニング モデル ビューアー |Microsoft ドキュメント"
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
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- displaying data mining models
- mining models [Analysis Services], viewing
- data mining [Analysis Services], models
- viewing data mining models
- mining model content
- support [data mining]
- exploring data mining models [Analysis Services]
ms.assetid: 14c8e656-f63c-4e8a-a3af-1d580e823d28
caps.latest.revision: "41"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2b065a7c059cf4c3e7ba79c0c03ef7b96d4928bf
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="data-mining-model-viewers"></a>データ マイニング モデル ビューアー
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]データ マイニング モデルをトレーニングした後[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、興味深い傾向を探すモデルを調べることができます。 マイニング モデルの結果は複雑で、生データの形式では理解しにくいので、通常は視覚的なデータを調査することで、アルゴリズムによってデータ内で発見されたルールや関係を最も簡単に理解できます。  
  
 モデルの作成に使用する各アルゴリズムからは、異なる種類の結果が返されます。 このため、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] にはアルゴリズムごとに個別のビューアーが用意されています。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でマイニング モデルを参照すると、モデルに適したビューアーを使用して、データ マイニング デザイナーの **[マイニング モデル ビューアー]** タブにモデルが表示されます。  
  
## <a name="how-to-use-the-model-viewers"></a>モデル ビューアーの使用方法  
 最初にマイニング モデルを選択してから、ビューアーを選択します。 各モデルでは、常に、複数のタブを表示できるカスタム ビューアーと汎用ビューアーの 2 種類のビューアーを使用できます。  
  
 選択したモデルの種類に応じて、モデルを検証するために表示されるオプションは非常に異なります。 各種類のモデルに関連付けられているカスタム ビューアーは、選択したデータ マイニング モデルの作成に使用したアルゴリズムに合わせて調整されます。 各カスタム ビューアーには、モデルの統計とパターンの調査、グラフの表示、確率のしきい値の対話的な操作、または名前に基づくアイテムの除外に役立つさまざまなツールやダイアログ ボックスがあります。  
  
 次の図は、同じモデルでカスタム ビューアーを選択した場合と汎用ビューアーを選択した場合の違いを示しています。  
  
1.  最初に、Microsoft タイム シリーズ アルゴリズムに基づくマイニング モデルを選択すると表示されるカスタム ビューアーを示します。  
  
     この特定のカスタム ビューアーによってタイム シリーズのグラフが自動的に作成され、5 つの予測が提供されます。  
  
2.  次に、 **Microsoft 汎用コンテンツ ツリー ビューアー**を使用して表示される同じモデルを示します。  
  
     左側の汎用ビューアーには、モデルのノードの一覧が表示されます。 ノードをクリックして、その内容を右側のペインに表示できます。  
  
 ![マイニング モデル デザイナーの概要](../../analysis-services/data-mining/media/generic-mining-model-tab1.gif "マイニング モデル デザイナーの概要")  
  
## <a name="more-about-the-microsoft-generic-content-tree-viewer"></a>Microsoft 汎用コンテンツ ツリー ビューアーの詳細  
 各モデルは [Microsoft 汎用コンテンツ ツリー ビューアー (データ マイニング)](http://msdn.microsoft.com/library/751b4393-f6fd-48c1-bcef-bdca589ce34c) でも表示できます。 このビューアーは、標準 HTML テーブル形式に従ってマイニング モデルのコンテンツを表示します。 ただし、ノードの配置と各ノードのコンテンツは、結果の生成に使用されたアルゴリズムに応じて大きく異なります。  
  
 カスタム ビューアーはモデルを調査して理解するために設計されていますが、モデルについて既に理解しており、特定のノードから統計またはルールを抽出する場合は、汎用ビューアーの方が適しています。 たとえば、分析中に [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によってキャプチャされたパターンと統計 (ノードの確率や回帰式など) に関する詳細情報を表示する場合は汎用ビューアーを使用します。  
  
 DMX を使用して*コンテンツ クエリ*を作成し、このビューアーに表示されるすべての情報を取得することもできます。 詳細については、「[コンテンツ クエリ (データ マイニング)](../../analysis-services/data-mining/content-queries-data-mining.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 次の各トピックでは、各ビューアーの詳細と、各ビューアーで情報がどのように解釈されるかを説明します。  
  
 [Microsoft ツリー ビューアーを使用したモデルの参照](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-tree-viewer.md)  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ツリー ビューアーについて説明します。 このビューアーには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリー アルゴリズムと [!INCLUDE[msCoName](../../includes/msconame-md.md)] 線形回帰アルゴリズムを使用して作成されたマイニング モデルが表示されます。  
  
 [Microsoft クラスター ビューアーを使用したモデルの参照](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] クラスター ビューアーについて説明します。 このビューアーには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] クラスタリング アルゴリズムを使用して作成されたマイニング モデルが表示されます。  
  
 [Microsoft タイム シリーズ ビューアーを使用したモデルの参照](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-time-series-viewer.md)  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] タイム シリーズ ビューアーについて説明します。 このビューアーには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] タイム シリーズ アルゴリズムを使用して作成されたマイニング モデルが表示されます。  
  
 [Microsoft Naive Bayes ビューアーを使用したモデルの参照](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes ビューアーについて説明します。 このビューアーには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes アルゴリズムを使用して作成されたマイニング モデルが表示されます。  
  
 [Microsoft シーケンス クラスター ビューアーを使用したモデルの参照](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] シーケンス クラスター ビューアーについて説明します。 このビューアーには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] シーケンス クラスター アルゴリズムを使用して作成されたマイニング モデルが表示されます。  
  
 [Microsoft アソシエーション ルール ビューアーを使用したモデルの参照](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション ルール ビューアーについて説明します。 このビューアーには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション アルゴリズムを使用して作成されたマイニング モデルが表示されます。  
  
 [Microsoft ニューラル ネットワーク ビューアーを使用したモデルの参照](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ニューラル ネットワーク ビューアーについて説明します。 このビューアーには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ロジスティック回帰アルゴリズムを使用するモデルなど、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ニューラル ネットワーク アルゴリズムを使用して作成されたマイニング モデルが表示されます。  
  
 [Microsoft 汎用コンテンツ ツリー ビューアーを使用したモデルの参照](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)  
 すべてのデータ マイニング モデルの汎用ビューアーで確認できる詳細情報について説明します。また、各アルゴリズムの情報を解釈する方法の例を示します。  
  
## <a name="see-also"></a>参照  
 [データ マイニング アルゴリズム (Analysis Services - データ マイニング)](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [データ マイニング デザイナー](../../analysis-services/data-mining/data-mining-designer.md)  
  
  
