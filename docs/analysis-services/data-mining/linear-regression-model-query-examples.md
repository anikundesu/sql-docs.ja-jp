---
title: "線形回帰モデルのクエリ例 |Microsoft ドキュメント"
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
- linear regression algorithms [Analysis Services]
- linear regression [Analysis Services]
- content queries [DMX]
ms.assetid: fd3cf312-57a1-44b6-b772-fce6fc1c26d7
caps.latest.revision: "21"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b0f34af9c1c466f09040c7915f53b993cb04ac1b
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="linear-regression-model-query-examples"></a>線形回帰モデルのクエリ例
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]データ マイニング モデルに対するクエリを作成するときに、分析で検出されたパターンの詳細情報を提供するには、コンテンツのクエリを作成するまたはパターンを使用して、モデルに新しいデータについて予測する予測クエリを作成することができます。 たとえばコンテンツ クエリを使用すると、回帰式に関する追加情報を取得できるのに対し、予測クエリを使用すると、新しいデータ ポイントがモデルに適合するかどうかを調べることができます。 クエリを使用してモデルに関するメタデータを取得することもできます。  
  
 ここでは、Microsoft 線形回帰アルゴリズムに基づいたモデルに対するクエリの作成方法について説明します。  
  
> [!NOTE]  
>  線形回帰アルゴリズムは、Microsoft デシジョン ツリー アルゴリズムの特殊なケースに基づいているため、これと多くの類似点があります。また、連続する予測可能属性を使用する一部のデシジョン ツリーには、回帰式を含めることができます。 詳細については、「 [Microsoft デシジョン ツリー アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-decision-trees-algorithm-technical-reference.md)」を参照してください。  
  
 **コンテンツ クエリ**  
  
 [データ マイニング スキーマ行セットを使用してモデルに対して使用されたパラメーターを特定する](#bkmk_Query1)  
  
 [DMX を使用してモデルの回帰式を取得する](#bkmk_Query2)  
  
 [モデルの係数のみを取得する](#bkmk_Query3)  
  
 **予測クエリ**  
  
 [単一クエリを使用して収入を予測する](#bkmk_Query4)  
  
 [回帰モデルで予測関数を使用する](#bkmk_Query5)  
  
##  <a name="bkmk_top"></a> 線形回帰モデルに関する情報の入手  
 線形回帰モデルの構造は非常に単純であり、マイニング モデルではデータを単一のノードとして表現されます。このノードは回帰式を定義します。 詳細については、「 [ロジスティック回帰モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング)](../../analysis-services/data-mining/mining-model-content-for-logistic-regression-models.md)」を参照してください。  
  
 [トップに戻る](#bkmk_top)  
  
###  <a name="bkmk_Query1"></a> サンプル クエリ 1: データ マイニング スキーマ行セットを使用してモデルに対して使用されたパラメーターを特定する  
 データ マイニング スキーマ行セットに対してクエリを実行すると、モデルに関するメタデータを取得できます。 このメタデータには、モデルが作成された日時、モデルが最後に処理された日時、モデルの基になるマイニング構造の名前、予測可能な属性として使用されている列の名前などが含まれます。 モデルが最初に作成されたときに使用されたパラメーターを取得することもできます。  
  
```  
SELECT MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM_PredictIncome'  
```  
  
 サンプルの結果 :  
  
|MINING_PARAMETERS|  
|------------------------|  
|COMPLEXITY_PENALTY=0.9,<br /><br /> MAXIMUM_INPUT_ATTRIBUTES=255,<br /><br /> MAXIMUM_OUTPUT_ATTRIBUTES=255,<br /><br /> MINIMUM_SUPPORT=10,<br /><br /> SCORE_METHOD=4,<br /><br /> SPLIT_METHOD=3,<br /><br /> FORCE_REGRESSOR=|  
  
> [!NOTE]  
>  パラメーター設定 "`FORCE_REGRESSOR =` " は、FORCE_REGRESSOR パラメーターの現在の値が NULL であることを示します。  
  
 [トップに戻る](#bkmk_top)  
  
###  <a name="bkmk_Query2"></a> サンプル クエリ 2: モデルの回帰式を取得する  
 次のクエリでは、「 [Basic Data Mining Tutorial](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)」で使用したものと同じ Targeted Mailing データ ソースを使用して作成された線形回帰モデルのマイニング モデル コンテンツを返します。 このモデルでは、年齢に基づいて顧客の収入を予測します。  
  
 このクエリは、回帰式を含むノードのコンテンツを返します。 各変数と係数は、入れ子になった NODE_DISTRIBUTION テーブルの個別の行に保存されます。 完全な回帰式を表示する場合は、 [Microsoft ツリー ビューアー](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-tree-viewer.md)を使用します。 **[(すべて)]** ノードをクリックして **[マイニング凡例]**を開くと表示されます。  
  
```  
SELECT FLATTENED NODE_DISTRIBUTION as t  
FROM LR_PredictIncome.CONTENT  
```  
  
> [!NOTE]  
>  `SELECT <column name> from NODE_DISTRIBUTION`のようなクエリを使用して入れ子になったテーブルの個々の列を参照する場合、 **SUPPORT** や **PROBABILITY**などの一部の列名は、同名の予約済みキーワードと区別するために角かっこで囲む必要があります。  
  
 期待される結果:  
  
|t.ATTRIBUTE_NAME|t.ATTRIBUTE_VALUE|t.SUPPORT|t.PROBABILITY|t.VARIANCE|t.VALUETYPE|  
|-----------------------|------------------------|---------------|-------------------|----------------|-----------------|  
|Yearly Income|Missing|0|0.000457142857142857|0|1|  
|Yearly Income|57220.8876687257|17484|0.999542857142857|1041275619.52776|3|  
|Age|471.687717702463|0|0|126.969442359327|7|  
|Age|234.680904692439|0|0|0|8|  
|Age|45.4269617936399|0|0|126.969442359327|9|  
||35793.5477381267|0|0|1012968919.28372|11|  
  
 一方、 **[マイニング凡例]**では、回帰式は次のように表示されます。  
  
 `Yearly Income = 57,220.919 + 471.688 * (Age - 45.427)`  
  
 **[マイニング凡例]**ではいくつかの数字が丸められますが、NODE_DISTRIBUTION テーブルと **[マイニング凡例]** には基本的に同じ値が格納されます。  
  
 VALUETYPE 列の値を参照すると、各行に含まれている情報の種類がわかるため、結果をプログラムで処理する場合に役に立ちます。 次の表に、線形回帰式の出力となる値の種類を示します。  
  
|VALUETYPE|  
|---------------|  
|1 (Missing: 不足)|  
|3 (Continuous: 連続)|  
|7 (Coefficient: 係数)|  
|8 (Score Gain: スコア ゲイン)|  
|9 (Statistics: 統計)|  
|7 (Coefficient: 係数)|  
|8 (Score Gain: スコア ゲイン)|  
|9 (Statistics: 統計)|  
|11 (Intercept: 切片)|  
  
 回帰モデルの各値の種類の意味については、「 [線形回帰モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)」を参照してください。  
  
 [トップに戻る](#bkmk_top)  
  
###  <a name="bkmk_Query3"></a> サンプル クエリ 3: モデルの係数のみを取得する  
 VALUETYPE 列挙を使用すると、次のクエリに示すように回帰式の係数のみを返すことができます。  
  
```  
SELECT FLATTENED MODEL_NAME,  
    (SELECT ATTRIBUTE_VALUE, VALUETYPE  
     FROM NODE_DISTRIBUTION  
     WHERE VALUETYPE = 11)   
AS t  
FROM LR_PredictIncome.CONTENT  
```  
  
 このクエリでは、マイニング モデル コンテンツの行と、係数を含む入れ子になったテーブルの行の 2 つの行が返されます。 ATTRIBUTE_NAME 列は、係数に対して常に空であるためここには含まれていません。  
  
|MODEL_NAME|t.ATTRIBUTE_VALUE|t.VALUETYPE|  
|-----------------|------------------------|-----------------|  
|LR_PredictIncome|||  
|LR_PredictIncome|35793.5477381267|11|  
  
 [トップに戻る](#bkmk_top)  
  
## <a name="making-predictions-from-a-linear-regression-model"></a>線形回帰モデルから予測を作成する  
 データ マイニング デザイナーの [マイニング モデル予測] タブを使用して、線形回帰モデルに対する予測クエリを作成します。 予測クエリ ビルダーは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] と [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]の両方で使用できます。  
  
> [!NOTE]  
>  また、Excel 用 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] データ マイニング アドインまたは Excel 用 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] データ マイニング アドインを使用して回帰モデルに対するクエリを作成することもできます。 Excel 用 データ マイニング アドインでは回帰モデルが作成されませんが、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに格納されているマイニング モデルを参照したり、照会したりすることはできます。  
  
 [トップに戻る](#bkmk_top)  
  
###  <a name="bkmk_Query4"></a> サンプル クエリ 4: 単一クエリを使用して収入を予測する  
 回帰モデルで単一クエリを作成する最も簡単な方法は、 **[単一クエリ入力]** ダイアログ ボックスを使用することです。 たとえば次の DMX クエリを作成するには、適切な回帰モデルを選択し、 **[単一クエリ]**を選択して、 **Age** の値として「 **20**」を入力します。  
  
```  
SELECT [LR_PredictIncome].[Yearly Income]  
From   [LR_PredictIncome]  
NATURAL PREDICTION JOIN  
(SELECT 20 AS [Age]) AS t  
```  
  
 サンプルの結果 :  
  
|Yearly Income|  
|-------------------|  
|45227.302092176|  
  
 [トップに戻る](#bkmk_top)  
  
###  <a name="bkmk_Query5"></a> サンプル クエリ 5: 回帰モデルで予測関数を使用する  
 線形回帰モデルでは多くの標準の予測関数を使用できます。 次の例は、予測クエリの結果にいくつかの説明的な統計情報を追加する方法を示しています。 これらの結果から、このモデルの平均からの偏差が相当あることがわかります。  
  
```  
SELECT  
  ([LR_PredictIncome].[Yearly Income]) as [PredIncome],  
  (PredictStdev([LR_PredictIncome].[Yearly Income])) as [StDev1]  
From  
  [LR_PredictIncome]  
NATURAL PREDICTION JOIN  
(SELECT 20 AS [Age]) AS t  
```  
  
 サンプルの結果 :  
  
|Yearly Income|StDev1|  
|-------------------|------------|  
|45227.302092176|31827.1726561396|  
  
 [トップに戻る](#bkmk_top)  
  
## <a name="list-of-prediction-functions"></a>予測関数の一覧  
 すべての [!INCLUDE[msCoName](../../includes/msconame-md.md)] アルゴリズムでは、共通の関数セットがサポートされています。 これに加え、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 線形回帰アルゴリズムでは、次の表に示す関数もサポートされています。  
  
|||  
|-|-|  
|予測関数|使用方法|  
|[IsDescendant &#40;DMX&#41;](../../dmx/isdescendant-dmx.md)|あるノードがモデル内の別のノードの子であるかどうかを示します。|  
|[IsInNode &#40;DMX&#41;](../../dmx/isinnode-dmx.md)|指定されたノードが現在のケースを含んでいるかどうかを示します。|  
|[PredictHistogram &#40;DMX&#41;](../../dmx/predicthistogram-dmx.md)|指定された列に対して、予測された値、または値のセットを返します。|  
|[PredictNodeId &#40;DMX&#41;](../../dmx/predictnodeid-dmx.md)|各ケースの Node_ID を返します。|  
|[PredictStdev &#40;DMX&#41;](../../dmx/predictstdev-dmx.md)|予測された値の標準偏差を返します。|  
|[PredictSupport &#40;DMX&#41;](../../dmx/predictsupport-dmx.md)|指定された状態に対するサポート値を返します。|  
|[PredictVariance &#40;DMX&#41;](../../dmx/predictvariance-dmx.md)|指定された列の分散を返します。|  
  
 すべての [!INCLUDE[msCoName](../../includes/msconame-md.md)] アルゴリズムに共通する関数の一覧は、「[データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)」を参照してください。 これらの関数の使用方法については、「[データ マイニング拡張機能 &#40;DMX&#41; 関数リファレンス](../../dmx/data-mining-extensions-dmx-function-reference.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Microsoft 線形回帰アルゴリズム](../../analysis-services/data-mining/microsoft-linear-regression-algorithm.md)   
 [データ マイニング クエリ](../../analysis-services/data-mining/data-mining-queries.md)   
 [Microsoft 線形回帰アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-linear-regression-algorithm-technical-reference.md)   
 [線形回帰モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)  
  
  
