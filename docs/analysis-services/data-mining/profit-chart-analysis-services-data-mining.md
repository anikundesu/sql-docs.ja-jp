---
title: "利益チャート (Analysis Services - データ マイニング) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
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
- accuracy, charting
- revenue, estimating
- benefits, estimating
- charts [Analysis Services]
- profit charts [Analysis Services]
ms.assetid: 760ee051-6fd8-48e3-8d2e-82db3ab45e45
caps.latest.revision: "23"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ddde9150e2e748e75cef8fb25f16377c9dcea4b0
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="profit-chart-analysis-services---data-mining"></a>利益チャート (Analysis Services - データ マイニング)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]利益チャートは、マイニング モデルを使用すると推定される収益性を表示します。 たとえば、あるビジネス シナリオに応じて、会社がどの顧客に連絡を取る必要があるかを、モデルで予測するとしましょう。 この場合、利益チャートに対して、ターゲット メーリング キャンペーンの実施コストに関する情報を追加します。 その後、完成したチャートで、ランダムに顧客に連絡を取った場合と比較して、顧客を正しくターゲット指定した場合に推定される利益を表示できます。  
  
## <a name="build-a-profit-chart"></a>利益チャートの作成  
 利益チャートは、リフト チャートに似ています。 最初にリフト チャートを作成し、その後にコスト情報と利益情報を追加します。  
  
 利益チャートを作成するには、既存のモデルを使用する必要があります。  
  
 この例では、絞り込みメールのデシジョン ツリー モデルを使用しました。 このモデルでは、自転車を購入する可能性がある顧客を識別します。 **[利益チャート]** を適用して、利益を最大化するためにターゲット指定する顧客の数を判断することができます。  
  
 サンプル モデルが存在しない場合は、「 [基本的なデータ マイニング チュートリアル](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)」を使用してそのモデルを作成できます。  
  
1.  マイニング精度チャート ビルダーを開きます。  
  
    -   SQL Server Management Studio でモデルを右クリックし、 **[リフト チャートの表示]**をクリックします。  
  
    -   SQL Server Data Tools で、モデルを作成したときに使用したプロジェクトを開き、 **[マイニング精度チャート]** タブをクリックします。  
  
2.  **[入力の選択]** タブでモデルを選択し、予測可能な属性値を選択します。  
  
     この特定のシナリオでは、[Bike Buyer] =1 という 1 つの値のみを正確に予測した状況の収益性のみに関心があります。  
  
     ただし、他のシナリオでは、false 値を正しく予測した状況にも同様の関心を持つことがあります。 たとえば、医療検診で偽陰性 (実際は兆候があるものを見逃す) のコストに比較して、偽陽性 (実際は兆候がないものを誤って有意と判定する) のコストが非常に高く、予測の収益性の一部として考慮する必要が生じることがあります。 このようなシナリオでは、すべての結果を測定することになります。  
  
3.  テストに使用するデータ セットを選択します。 この例では、テスト用のデータ セットを選択します。  
  
4.  次に、 **[リフト チャート]** タブをクリックします。  
  
     リフト チャートが自動的に生成されます。  
  
5.  このチャートを利益チャートに変換するには、 **[グラフの種類]** の一覧から **[利益チャート]** を選択します。  
  
6.  グラフの種類として利益チャートを選択するとすぐに、 **[利益チャートの設定]** ダイアログ ボックスが自動的に開きます。  
  
     このダイアログ ボックスは、ターゲット メーリング キャンペーンに関連付けられているコストと利益を指定するときに役立ちます。 これらの例のグラフでは、次の値を使用しました。  
  
    |設定|値|コメント|  
    |-------------|-----------|--------------|  
    |**[母集団]**|20,000|対象になる母集団の合計に対する値の設定<br /><br /> データベースに多くの顧客が含まれている可能性もありますが、郵送料を抑えるために、最も反応がありそうな上位 20,000 人の顧客のみをターゲットにすると想定します。 予測クエリを実行し、予測モデルによって出力された確率で並べ替えると、この一覧を取得できます。|  
    |**[固定コスト]**|500|20,000 人の顧客に対するターゲット メーリング キャンペーンの準備にかかる 1 回限りのコストを入力します。 このコストには、印刷コスト、または電子メール キャンペーンの準備コストが含まれる可能性があります。|  
    |**変動コスト**|3|ターゲット メーリング キャンペーンの単位あたりのコストの入力<br /><br /> この金額に 20,000 以下の数 (実際の数は、モデルで適切な見込み客として予測された顧客の数によって決まります) を掛けた値を計算します。|  
    |**[個人ごとの収益]**|400|成功した場合に期待できる利益または収入の金額を表す値の入力 このシナリオでは、カタログを発送した場合に、付属品または自転車の平均購入額が 400 ドルであると想定しています。<br /><br /> この金額を使用して、可能性が高いケースに関連する利益総額が算出されます。|  
  
7.  これらの必要なパラメーターを設定した後、 **[OK]**をクリックします。  
  
8.  チャートが更新され、利益曲線が表示されます。  
  
## <a name="understanding-the-profit-chart"></a>利益チャートについて  
 次の図は、これらのパラメーターに基づくグラフを示しています。 このチャートの Y 軸は利益を、X 軸はターゲット メーリング キャンペーンによってコンタクトした顧客が、顧客リスト全体に占める割合を示します。  
  
 ここで示したように、複数のモデルが同じ不連続属性を予測する場合は、1 つの利益チャートを使用してそれらを比較することができます。  
  
 ![利益チャートの 3 つのモデルを比較する](../../analysis-services/data-mining/media/dm14-profitchartupdated.gif "利益グラフの 3 つのモデルを比較します。")  
  
 チャート内にある灰色の垂直線に注意してください。 この線をクリックしてドラッグすると、現在のポイントで、対象になる母集団の何パーセントが曲線の下に含まれているかを示すツールヒントが表示されます。  
  
 線をドラッグすると **[マイニング凡例]** も更新されて、割合の値、利益のスコア、および灰色の垂直線が示す母集団の割合に関連付けられている予測確率が表示されます。  
  
 たとえば、このモデルを使用してプロモーション資料の送付先を決定する場合は、予測確率に基づいて母集団全体のうち 25% をターゲットにする方針を決定する可能性があります。一方、チャートの利益曲線より下側にある面積は 40 ～ 70% の間で最大になっており、より多くの顧客に資料を送付すると、全体の反応率が低下するとはいえ、利益を最大化できることを示しています。  
  
## <a name="saving-charts"></a>チャートの保存  
 精度チャートまたは利益チャートを作成する場合、サーバー上では何もオブジェクトが作成されません。 代わりに、既存のモデルに対してクエリが実行され、結果がビューアー内で表示されます。 結果を保存する必要がある場合は、チャートまたは結果を Excel または別のファイルにコピーする必要があります。  
  
## <a name="related-content"></a>関連コンテンツ  
 次のトピックには、精度チャートの構築方法と使用方法に関する詳細な情報が含まれています。  
  
|トピック|リンク|  
|------------|-----------|  
|Targeted Mailing モデルのリフト チャートの作成方法に関するチュートリアルが含まれています。|[基本的なデータ マイニング チュートリアル](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)<br /><br /> [リフト チャートを使用した精度テスト (基本的なデータ マイニング チュートリアル)](http://msdn.microsoft.com/library/822d414b-4a39-473f-80c3-53476e30655a)|  
|関連するグラフの種類について説明します。|[リフト チャート (Analysis Services - データ マイニング)](../../analysis-services/data-mining/lift-chart-analysis-services-data-mining.md)<br /><br /> [分類マトリックス (Analysis Services - データ マイニング)](../../analysis-services/data-mining/classification-matrix-analysis-services-data-mining.md)<br /><br /> [散布図 (Analysis Services - データ マイニング)](../../analysis-services/data-mining/scatter-plot-analysis-services-data-mining.md)|  
|マイニング モデルとマイニング構造の相互検証について説明します。|[相互検証 (Analysis Services - データ マイニング)](../../analysis-services/data-mining/cross-validation-analysis-services-data-mining.md)|  
|リフト チャートおよびその他の精度チャートを作成する手順について説明します。|[テストおよび検証タスク、および操作方法 (データ マイニング)](../../analysis-services/data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md)|  
  
## <a name="see-also"></a>参照  
 [テストおよび検証 (データ マイニング)](../../analysis-services/data-mining/testing-and-validation-data-mining.md)   
 [リフト チャートを使用した精度テスト (基本的なデータ マイニング チュートリアル)](http://msdn.microsoft.com/library/822d414b-4a39-473f-80c3-53476e30655a)  
  
  
