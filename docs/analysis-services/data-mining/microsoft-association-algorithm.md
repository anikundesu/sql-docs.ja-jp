---
title: "Microsoft アソシエーション アルゴリズム |Microsoft ドキュメント"
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
- MinimumProbability property
- itemsets [Analysis Services]
- MaximumItemsetCount property
- MinimumSupport property
- OPTIMIZED_PREDICTION_COUNT
- OptimizedPredictionCount property
- MaximumSupport property
- MINIMUM_PROBABILITY
- algorithms [data mining]
- association algorithms [Analysis Services]
- rules [Data Mining]
- association rules
- MinimumItemsetSize property
- market basket analysis [Analysis Services]
- associations [Analysis Services]
- MINIMUM_SUPPORT
- MAXIMUM_SUPPORT
- MINIMUM_ITEMSET_SIZE
- MaximumItemsetSize property
ms.assetid: 8b6b8247-62f9-4f6f-b1af-d01dab290e4c
caps.latest.revision: "55"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8d68a5b94df379a3ab19d4df5d4621c986762473
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="microsoft-association-algorithm"></a>Microsoft アソシエーション アルゴリズム
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)][!INCLUDE[msCoName](../../includes/msconame-md.md)]アソシエーション アルゴリズムは推奨エンジンの多くの場合、使用されるアルゴリズム。 推奨エンジンでは、顧客が既に購入した製品または興味を示した製品に基づいて、顧客に製品が推奨されます。 また、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション アルゴリズムは、マーケット バスケット分析にも使用できます。   
  
 アソシエーション モデルは、個々のケースの識別子とケース内のアイテムの識別子を含んでいるデータセットに基づいて作成されています。 ケース内のアイテムのグループは、 *アイテムセット*と呼ばれます。 アソシエーション モデルは、一連のアイテムセットと、ケース内でアイテムをグループ化する方法を示すルールで構成されています。 アルゴリズムによって識別されるルールは、顧客の買い物かごに既に存在する製品に基づいて、顧客の将来の購入を予測するために使用できます。 次の図は、アイテムセットの一連のルールを示しています。  
  
 ![アソシエーション モデルのルール セット](../../analysis-services/data-mining/media/association.gif "アソシエーション モデルのルール セット")  
  
 図のように、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション アルゴリズムによって、データセット内で多数のルールが検出される可能性があります。 このアルゴリズムでは、アルゴリズムで生成されるアイテムセットおよびルールを示すためにサポートと確率という 2 つのパラメーターが使用されます。 たとえば、X と Y が、買い物かごにある 2 つの製品を表す場合、サポート パラメーターは X と Y というアイテムの組み合わせを含んでいるデータセット内のケースの数になります。サポート パラメーターをユーザー定義パラメーターの *MINIMUM_SUPPORT* および *MAXIMUM_SUPPORT* と組み合わせて使用することによって、アルゴリズムは生成されるアイテムセットの数を制御します。 確率パラメーターは、" *信頼度*" とも呼ばれ、X と Y を含んでいるデータセット内のケースの割合を表します。確率パラメーターを *MINIMUM_PROBABILITY* パラメーターと組み合わせて使用することによって、アルゴリズムは生成されるルールの数を制御します。  
  
## <a name="example"></a>例  
 [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] Cycle 社では、Web サイトの機能を再設計しています。 再設計の目的は、製品の販売を増やすことです。 この会社ではトランザクション データベースで各売上を記録しているので、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション アルゴリズムを使用して、一緒に購入される傾向がある製品のセットを特定できます。 その後、顧客の買い物かごに既にある製品に基づいて、顧客が興味を持ちそうな他の製品を予測できます。  
  
## <a name="how-the-algorithm-works"></a>アルゴリズムの動作  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション アルゴリズムでは、データセットをスキャンして、ケース内で一緒に表示するアイテムが検索されます。 このアルゴリズムは、少なくとも *MINIMUM_SUPPORT* パラメーターで指定された数のケースに表示される関連アイテムをアイテムセットにグループ化します。 たとえば、アイテムセットが "Mountain 200=Existing, Sport 100=Existing" であり、サポートが 710 であるとします。 その場合、アルゴリズムはアイテムセットからルールを生成します。 これらのルールは、アルゴリズムが重要と識別する他の特定のアイテムの存在に基づいて、データベース内のアイテムの存在を予測するために使用されます。 たとえば、ルールが "if Touring 1000=existing and Road bottle cage=existing, then Water bottle=existing" であり、確率が 0.812 であるとします。 この例では、アルゴリズムは買い物かごに、Touring 1000 と water bottle cage が入っていることを識別し、買い物かごに water bottle も入っている可能性があることを予測します。  
  
 アルゴリズムの詳細と、アルゴリズムの動作のカスタマイズやマイニング モデルの結果の制御のためのパラメーターの一覧については、「 [Microsoft アソシエーション アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md)」を参照してください。  
  
## <a name="data-required-for-association-models"></a>アソシエーション モデルに必要なデータ  
 アソシエーション ルール モデルで使用するデータを用意する際には、必要なデータ量やデータの使用方法など、このアルゴリズムにおける要件を把握しておいてください。  
  
 アソシエーション ルール モデルの要件は次のとおりです。  
  
-   **単一キー列** : それぞれのモデルには、各レコードを一意に識別する数値列またはテキスト列が 1 つ含まれている必要があります。 複合キーは使用できません。  
  
-   **1 つの予測可能列** : アソシエーション モデルで使用できる予測可能列は 1 つだけで、 通常は、入れ子になったテーブルのキー列 (購入された製品の一覧を含むフィールドなど) になります。 値は不連続値または分離された値である必要があります。  
  
-   **入力列** : 入力列は不連続である必要があります。 アソシエーション モデルの入力データは、通常 2 つのテーブルに格納されています。 たとえば、1 つのテーブルに顧客情報が格納されており、もう 1 つのテーブルに顧客が購入した製品が格納されている場合があります。 入れ子になったテーブルを使用して、このデータをモデルに入力できます。 入れ子になったテーブルの詳細については、「[入れ子になったテーブル &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/nested-tables-analysis-services-data-mining.md)」を参照してください。  
  
 アソシエーション モデルでサポートされるコンテンツの種類とデータ型の詳細については、「[Microsoft アソシエーション アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md)」の「必要条件」を参照してください。  
  
## <a name="viewing-an-association-model"></a>アソシエーション モデルの表示  
 モデルを参照するには、 **Microsoft アソシエーション ビューアー**を使用します。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、アソシエーション モデルを表示すると、さまざまな角度から相関関係が示されるため、データ内で見つかった関係とルールをより深く理解することができます。 ビューアーの **[アイテムセット]** ペインには、最も一般的な組み合わせ (アイテムセット) の詳細な内訳が表示されます。 **[ルール]** ペインには、データから導き出されたルールの一覧が表示され、確率の計算が追加されます。また、ルールが相対的な重要度で順位付けされます。 依存関係ネットワーク ビューアーを使用すると、個々のアイテムがどのように関連付けられているのかを視覚的に調べることができます。 詳細については、「 [Microsoft クラスター ビューアーを使用したモデルの参照](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)」を参照してください。  
  
 特定のアイテムセットやルールの詳細を調べるには、 [Microsoft 汎用コンテンツ ツリー ビューアー](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)でモデルを参照してください。 モデルに保存される内容には、各アイテムセットのサポートや、各ルールのスコアなどの統計情報などが含まれます。 詳細については、「 [アソシエーション モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md)と呼ばれます。  
  
## <a name="creating-predictions"></a>予測の作成  
 モデルの処理が完了したら、ルールとアイテムセットを使用して予測を実行できます。 アソシエーション モデルでは、指定したアイテムが存在する場合に発生する可能性があるアイテムを予測できます。この予測には、確率、サポート、重要度などの情報を含めることができます。 アソシエーション モデルに対するクエリの作成方法の例については、「 [結合モデルのクエリ例](../../analysis-services/data-mining/association-model-query-examples.md)」を参照してください。  
  
 データ マイニング モデルに対するクエリの作成方法については、「 [データ マイニング クエリ](../../analysis-services/data-mining/data-mining-queries.md)」を参照してください。  
  
## <a name="performance"></a>パフォーマンス  
 アイテムセットを作成して相関関係をカウントするというプロセスには時間がかかる場合があります。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション ルール アルゴリズムでは、領域の節約と処理の高速化のための最適化の手法が使用されていますが、次のような状況ではパフォーマンスの問題が発生する可能性があります。  
  
-   多数のアイテムを含む大きなデータセットを使用する場合。  
  
-   アイテムセットの最小サイズの設定が低すぎる場合。  
  
 処理時間を最小限に抑え、アイテムセットの複雑さを軽減するには、データを分析する前に、関連するアイテムをカテゴリ別にグループ化してみてください。  
  
## <a name="remarks"></a>解説  
  
-   Predictive Model Markup Language (PMML) を使用したマイニング モデルの作成はサポートされていません。  
  
-   ドリルスルーがサポートされています。  
  
-   OLAP マイニング モデルの使用がサポートされています。  
  
-   データ マイニング ディメンションの作成がサポートされています。  
  
## <a name="see-also"></a>参照  
 [データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Microsoft アソシエーション ルール ビューアーを使用してモデルを参照します。](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)   
 [アソシエーション モデル &#40; のマイニング モデル コンテンツAnalysis Services - データ マイニング &#41;](../../analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md)   
 [Microsoft アソシエーション アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md)   
 [結合モデルのクエリ例](../../analysis-services/data-mining/association-model-query-examples.md)  
  
  
