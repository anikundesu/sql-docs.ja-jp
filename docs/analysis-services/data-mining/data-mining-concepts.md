---
title: "データ マイニングの概念 |Microsoft ドキュメント"
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
- SQL Server Analysis Services, data mining
- cleaning data
- predictive analytics
- learning algorithms
- data mining [Analysis Services], concepts
- inductive learning
- data mining [Analysis Services], about data mining
- mining models [Analysis Services]
- data access [Analysis Services]
- machine learning algorithms [Analysis Services]
- mining models [Analysis Services], about data mining
- SSAS, data mining
- Analysis Services, data mining
ms.assetid: 6da6c26b-7809-415c-b5dd-bb642b51c194
caps.latest.revision: "48"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 905a45d6852a7e5e1ed469e65f6082f0282de985
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="data-mining-concepts"></a>データ マイニングの概念
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]データ マイニングは、大量のデータ セットから実用的な情報を検出するプロセスです。 データ マイニングでは、数学的分析を使用して、データに内在するパターンおよび傾向を抽出します。 通常、これらのパターンは、従来のデータ探索では検出できません。これは、リレーションシップが非常に複雑であるか、またはデータ量が多すぎるためです。  
  
 これらのパターンと傾向を合わせて収集し、 *データ マイニング モデル*として定義できます。 マイニング モデルは、次のような特定のシナリオに適用できます。  
  
-   **予測**: 販売予測、サーバー負荷またはサーバーのダウンタイムの予測  
  
-   **リスクおよび確率**: 対象を絞ったダイレクト メールに最適な顧客の選定、リスク シナリオでの確率の高い損益分岐点の判定、診断や他の結果への確率の割り当て  
  
-   **推奨設定**: 一緒に販売できる可能性の高い製品の判定、推奨設定の作成  
  
-   **シーケンスの発見**: ショッピング カート内の顧客の選択の分析、次に発生する可能性の高いイベントの予測  
  
-   **グループ化**: 顧客やイベントを関連する項目のクラスターに分離、親和性の分析と予測  
  
 マイニング モデルの作成は、データに関する質問の提示およびそれらの質問に回答するモデルの作成から、作業環境へのモデルの配置までのすべてを含む大きなプロセスの一部です。 このプロセスは、次の 6 つの基本的な手順に従って定義できます。  
  
1.  [問題の定義](#DefiningTheProblem)  
  
2.  [データの準備](#PreparingData)  
  
3.  [データの探索](#ExploringData)  
  
4.  [モデルの作成](#BuildingModels)  
  
5.  [モデルの調査と検証](#ValidatingModels)  
  
6.  [モデルの配置と更新](#DeployingandUpdatingModels)  
  
 次の図では、プロセスの各手順の関係と、各手順の実行に使用できる [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のテクノロジについて説明します。  
  
 ![データ マイニング プロセスの主なステップ](../../analysis-services/data-mining/media/data-mining-process.gif "データ マイニング プロセスの主なステップ")  
  
 図ではプロセスが循環的であることが示されています。これはデータ マイニング モデルの作成が、動的かつ反復的なプロセスであることを意味します。 データを探索した後、適切なマイニング モデルを作成するためにデータが不十分であることがわかれば、さらに多くのデータを探索する必要があります。 また、いくつかのモデルを作成した後で、定義した問題がそれらのモデルで適切に解決されないことがわかれば、問題を再定義する必要があります。 モデルを配置した後、より多くのデータが使用可能になったために、モデルを更新することが必要になる場合があります。 適切なモデルを作成するためには、プロセスの各手順を何度も繰り返すことが必要になる場合もあります。  
  
 Microsoft SQL Server データ マイニングでは、データ マイニング モデルを作成および操作するための統合環境が提供されています。 この環境には、さまざまなプロジェクト用の広範なソリューションを簡単に作成できるデータ マイニング アルゴリズムとクエリ ツールを持つ SQL Server Development Studio、およびモデルの参照とデータ マイニング オブジェクトの管理のためのツールを持つ [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]が含まれています。 詳細については、「[SQL Server データ ツール (SSDT) を使用した多次元モデルの作成](../../analysis-services/multidimensional-models/creating-multidimensional-models-using-sql-server-data-tools-ssdt.md)」を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ツールをビジネス シナリオに適用する方法の例については、「 [基本的なデータ マイニング チュートリアル](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)」を参照してください。  
  
##  <a name="DefiningTheProblem"></a> 問題の定義  
 次の図で示すように、データ マイニング プロセスの最初の手順では、問題を明確に定義し、その問題の解決のためにデータを利用する方法について検討します。  
  
 ![データ マイニング手順 1: 問題の定義](../../analysis-services/data-mining/media/dmprocess-defining.gif "データ マイニング手順 1: 問題の定義")  
  
 この手順には、ビジネス要件の分析、問題の範囲の定義、モデルを評価する基準の定義、およびデータ マイニング プロジェクトの特定の目的の定義が含まれます。 これらのタスクは、次のような質問に言い換えることができます。  
  
-   どのような情報を検索しますか? 検索するリレーションシップの種類は何ですか?  
  
-   解決しようとしている問題は、ビジネス ポリシーまたはビジネス プロセスを反映しているのか。  
  
-   データ マイニング モデルから予測するのか、興味深いパターンおよび関連付けを特定したいだけか。  
  
-   予測したいのは結果か、それとも属性か。  
  
-   どの型のデータがあり、各列にはどのような種類の情報があるか。 複数のテーブルがある場合、各テーブルはどのように関連しているのか。 データを使用可能にするために、クレンジング、集計、または処理を実行する必要があるか。  
  
-   データはどのように分布していますか? データは季節的なものか。 データはビジネス プロセスを正確に表しているか。  
  
 これらの質問に答えるには、データの可用性を調べ、使用可能なデータについてビジネス ユーザーのニーズを調査することが必要な場合があります。 そのデータでユーザーのニーズがサポートされない場合は、プロジェクトの再定義が必要な場合があります。  
  
 また、ビジネスの進捗状況の測定に使用される主要業績評価指標 (KPI) にモデルの結果を組み込む方法についても検討する必要があります。  
  
##  <a name="PreparingData"></a> データの準備  
 次の図で強調表示されている、データ マイニング プロセスの 2 番目の手順では、「 [問題の定義](#DefiningTheProblem) 」の手順で示したデータの統合および削除を行います。  
  
 ![データ マイニング手順 2: データの準備](../../analysis-services/data-mining/media/dmprocess-preparing.gif "データ マイニング手順 2: データの準備")  
  
 データは会社全体に分散して異なる形式で保存されたり、間違ったエントリや欠落しているエントリなどの矛盾を含んだりしている場合があります。 たとえば、製品が市場で提供される前に製品を購入していたり、自宅から 2,000 マイル離れたところにある店で定期的に買い物をしていたりという矛盾を示す場合があります。  
  
 データのクリーニングでは、不良データの削除や不足値の補間だけでなく、データ内の隠れた相関関係の検出、最も正確なデータ ソースの特定、および分析に最適な列の決定も行います。 たとえば、出荷日と受注日のどちらを使用するか、 販売に最も大きく影響するのは、数量か、合計金額か、割引価格か、などを考慮します。 不完全なデータ、間違ったデータ、および一見無関係に見えるものの、実際にはすべて強い相関関係にある入力は、予期しない形でモデルの結果に影響を及ぼす可能性があります。  
  
 したがって、マイニング モデルの作成を開始する前に、これらの問題を特定し、その解決方法を決定する必要があります。 データ マイニングでは通常、操作するデータセットが非常に大きいため、すべてのトランザクションでデータ品質を検証することはできません。そのため、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]、 [!INCLUDE[ssMDSlong](../../includes/ssmdslong-md.md)]、または [!INCLUDE[ssDQSnoversionLong](../../includes/ssdqsnoversionlong-md.md)] で提供されているような、データ プロファイル ツールやフィルター ツールを使用して、データを調べ矛盾を見つける必要があります。 詳細については、次のリソースをご覧ください。  
  
-   [Business Intelligence Development Studio の Integration Services](https://technet.microsoft.com/library/ms174181\(v=sql.110\).aspx)  
  
-   [マスター データ サービスの概要 (MDS)](../../master-data-services/master-data-services-overview-mds.md)  
  
-   [Data Quality Services](../../data-quality-services/data-quality-services.md)  
  
 データ マイニングに使用するデータは、オンライン分析処理 (OLAP) キューブまたはリレーショナル データベースに格納されている必要はないという点に注意する必要があります。ただし、これらは両方ともデータ ソースとして使用できます。 データ マイニングは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ ソースとして定義されている任意のデータ ソースを使用して行うことができます。 これには、テキスト ファイル、Excel ブック、他の外部プロバイダーからのデータなどが含まれます。 詳細については、「[サポートされるデータ ソース (SSAS - 多次元)](../../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md)」を参照してください。  
  
##  <a name="ExploringData"></a> データの探索  
 次の図で強調されているように、データ マイニング プロセスの 3 番目の手順では、準備されたデータを探索します。  
  
 ![データ マイニング手順 3: データの探索](../../analysis-services/data-mining/media/dmprocess-exploring.gif "データ マイニング手順 3: データの探索")  
  
 マイニング モデルの作成時に適切な決定を行うために、データを理解する必要があります。 調査方法には、最小値および最大値の計算、平均偏差および標準偏差の計算、およびデータの分布の確認が含まれます。 たとえば、最大値、最小値、および平均値を調べることで、データが顧客またはビジネス プロセスを表していないことが判明し、その結果、よりバランスの取れたデータを取得するか、予測の基礎となっている前提条件を見直す必要があることが明らかになる場合があります。 標準偏差などの分布値には、結果の安定性および正確性に関する有用な情報が含まれていることがあります。 標準偏差が大きい場合、データを追加することでモデルを改善できる可能性があります。 標準分布から大きく逸脱したデータは、実際の問題を反映していない可能性があります。また、実際の問題を正確に表している可能性もありますが、このようなデータにモデルを適合させるのは困難です。  
  
 ビジネス上の問題に関する自分自身の理解に照らしてデータを探索することで、欠陥のあるデータがデータセットに含まれているかどうかを判断し、問題を解決するための戦略を構築したり、ビジネスの典型的な動きについての理解を深めたりできます。  
  
 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] などのツールを使用して使用可能なデータ ソースを詳細に調査し、データ マイニングの使用可能性を判断します。 [!INCLUDE[ssDQSnoversionLong](../../includes/ssdqsnoversionlong-md.md)]や Integration Services の Data Profiler などのツールを使用すると、データ内の値の分布を分析し、間違ったデータや不足データを修復することができます。  
  
 ソースの定義が完了した後、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]でデータ ソース ビュー デザイナーを使用して、データ ソース ビューでそれらのソースを組み合わせることができます。 詳細については、「 [多次元モデルのデータ ソース ビュー](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)」を参照してください。 このデザイナーには、データを調べたり、データがモデルの作成に役立つことを確認したりするための複数のツールが含まれています。 詳細については、「[データ ソース ビューでのデータの検索 (Analysis Services)](../../analysis-services/multidimensional-models/explore-data-in-a-data-source-view-analysis-services.md)」を参照してください。  
  
 モデルを作成すると、モデルに含まれるデータの統計サマリが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって自動的に作成されます。この統計サマリに対してクエリを実行することで、レポートや詳細な分析で使用するデータを取得できます。 詳細については、「 [データ マイニング クエリ](../../analysis-services/data-mining/data-mining-queries.md)」を参照してください。  
  
##  <a name="BuildingModels"></a> モデルの作成  
 次の図で強調されているように、データ マイニング プロセスの 4 番目の手順では、マイニング モデルまたはモデルを作成します。 「 [データの探索](#ExploringData) 」の手順から得た知識を使用すると、モデルの定義および作成に役立ちます。  
  
 ![データ マイニング手順 4: マイニング モデルの構築](../../analysis-services/data-mining/media/dmprocess-building.gif "データ マイニング手順 4: マイニング モデルの構築")  
  
 マイニング構造を作成して、使用するデータ列を定義します。 マイニング構造では、データ ソースがリンクされますが、処理が完了するまで実際のデータは格納されません。 マイニング構造を処理すると、分析に使用できる集計およびその他の統計情報が [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって生成されます。 この情報は、マイニング構造に基づくすべてのマイニング モデルで使用できます。 マイニング構造とマイニング モデルの関係の詳細については、「[論理アーキテクチャ (Analysis Services - データ マイニング)](../../analysis-services/data-mining/logical-architecture-analysis-services-data-mining.md)」を参照してください。  
  
 構造とモデルを処理する前のデータ マイニング モデルもまた、入力用の列、予測対象の属性、およびデータの処理アルゴリズムを示すパラメーターを指定するコンテナーにすぎません。 モデルの処理は、通常、 *トレーニング*と呼ばれます。 トレーニングとは、パターンを抽出するために、マイニング構造のデータに特定の数学的アルゴリズムを適用するプロセスのことです。 トレーニング処理で検出されるパターンは、トレーニング データの選択、使用するアルゴリズム、およびアルゴリズムの構成方法に応じて異なります。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] には、各種の作業に適したさまざまなアルゴリズムが用意されています。各アルゴリズムは、異なる種類のモデルを生成します。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] に用意されているアルゴリズムの一覧については、「[データ マイニング アルゴリズム (Analysis Services - データ マイニング)](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)」を参照してください。  
  
 また、パラメーターを使用して各アルゴリズムを調整したり、トレーニング データにフィルターを適用してデータのサブセットを使用したりすることで、さまざまな結果を生成できます。 モデルにデータを渡すと、クエリを実行したり予測に使用したりできるサマリおよびパターンがマイニング モデル オブジェクトに格納されます。  
  
 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] のデータ マイニング ウィザードまたはデータ マイニング拡張機能 (DMX) 言語を使用すると、新しいモデルを定義できます。 データ マイニング ウィザードの使用方法の詳細については、「[データ マイニング ウィザード (Analysis Services - データ マイニング)](../../analysis-services/data-mining/data-mining-wizard-analysis-services-data-mining.md)」を参照してください。 DMX の使用方法の詳細については、「[データ マイニング拡張機能 (DMX) リファレンス](../../dmx/data-mining-extensions-dmx-reference.md)」を参照してください。  
  
 データが変更されるたびに、マイニング構造とマイニング モデルの両方を更新する必要があることに注意してください。 再処理を行ってマイニング構造を更新すると、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によってソースからデータが取得され (ソースが動的に更新される場合は、新しいデータも取得されます)、マイニング構造が再作成されます。 マイニング構造に基づくモデルが存在する場合は、そのモデルを更新するか (新しいデータに基づいて再トレーニングされます)、または更新せずにそのままにしておくかを選択できます。 詳細については、「[処理の要件および注意事項 (データ マイニング)](../../analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)」を参照してください。  
  
##  <a name="ValidatingModels"></a> モデルの調査と検証  
 次の図で強調されているように、データ マイニング プロセスの 5 番目の手順では、作成したマイニング モデルを調査して、その効果をテストします。  
  
 ![データ マイニング手順 5: マイニング モデルの検証](../../analysis-services/data-mining/media/dmprocess-validating.gif "データ マイニング手順 5: マイニング モデルの検証")  
  
 モデルを運用環境に配置する前に、モデルのパフォーマンスをテストする必要があります。 また、モデルを作成する場合、通常は構成が異なる複数のモデルを作成し、どのモデルが問題およびデータに最も適した結果をもたらすかを調べるためにすべてのモデルをテストします。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] には、データをトレーニング データセットとテスト データセットに分割できるツールがあります。これにより、すべてのモデルのパフォーマンスを同じデータに対して正確に評価できます。 トレーニング データセットを使用してモデルを作成し、テスト データセットを使用して予測クエリを作成することによってモデルの精度をテストします。 このパーティション分割を行うことができます、マイニング モデルの作成中に自動的にします。 詳細については、「 [テストおよび検証 (データ マイニング)](../../analysis-services/data-mining/testing-and-validation-data-mining.md)" テンプレートを使用して、データ マイニング プロジェクトを作成します。  
  
 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]のデータ マイニング デザイナーのビューアーを使用して、アルゴリズムで検出された傾向およびパターンを調べることができます。 詳細については、「 [データ マイニング モデル ビューアー](../../analysis-services/data-mining/data-mining-model-viewers.md)」を参照してください。 また、リフト チャートや分類マトリックスなどのデザイナーのツールを使用して、モデルがどの程度予測を作成できるかをテストすることもできます。 モデルがデータに固有のものであるか、一般的な母集団の推定に使用できるものであるかを確認する場合は、*クロス検証*と呼ばれる統計手法を使用できます。この手法を使用すると、データのサブセットが自動的に作成され、各サブセットに対してモデルがテストされます。 詳細については、「[テストおよび検証 (データ マイニング)](../../analysis-services/data-mining/testing-and-validation-data-mining.md)」を参照してください。  
  
 「 [モデルの作成](#BuildingModels) 」の手順で作成したモデルのパフォーマンスがいずれもよくない場合は、プロセスの前の手順に戻り、問題を再定義するか、元のデータセットのデータを再調査する必要が生じることもあります。  
  
##  <a name="DeployingandUpdatingModels"></a> モデルの配置と更新  
 次の図で強調されているように、データ マイニング プロセスの最後の手順では、最適なパフォーマンスを示したモデルを運用環境に配置します。  
  
 ![データ マイニング手順 6: マイニング モデルの配置](../../analysis-services/data-mining/media/dmprocess-deploying.gif "データ マイニング手順 6: マイニング モデルの配置")  
  
 マイニング モデルを運用環境に配置すると、必要に応じて多くのタスクを実行できます。 次のようなタスクを実行できます。  
  
-   モデルを使用して予測を作成します。これは、業務上の意思決定に使用できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、予測クエリを作成するための DMX 言語と、クエリを作成するための予測クエリ ビルダーが提供されています。 詳細については、「[データ マイニング拡張機能 (DMX) リファレンス](../../dmx/data-mining-extensions-dmx-reference.md)」を参照してください。  
  
-   モデルから統計情報、ルール、または数式を取得するコンテンツ クエリを作成します。 詳細については、「 [データ マイニング クエリ](../../analysis-services/data-mining/data-mining-queries.md)」を参照してください。  
  
-   データ マイニング機能をアプリケーションに直接埋め込みます。 マイニング構造とマイニング モデルを作成、変更、処理、および削除するためにアプリケーションで使用できる一連のオブジェクトを含んでいる分析管理オブジェクト (AMO) を含めることができます。 XML for Analysis (XMLA) メッセージを [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに直接送信することもできます。 詳細については、「 [開発 (Analysis Services - データ マイニング)](https://technet.microsoft.com/library/bb522473\(v=sql.110\).aspx)」を参照してください。  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] を使用してパッケージを作成します。ここで、マイニング モデルは、入力されたデータを複数のテーブルに適切に分割するために使用されます。 たとえば、潜在的な顧客に関してデータベースが継続的に更新される場合は、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] と共にマイニング モデルを使用して、製品を購入する可能性のある顧客と製品を購入する可能性のない顧客に入力データを分割できます。 詳細については、「 [Integration Services の典型的な使用方法](http://msdn.microsoft.com/en-us/3b97897a-d418-4ef4-b5a4-5aabf4fa6bca)」を参照してください。  
  
-   ユーザーが既存のマイニング モデルに対して直接クエリを実行できるレポートを作成します。 詳細については、「[SQL Server データ ツールの Reporting Services (SSDT)](../../reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt.md)」を参照してください。  
  
-   レビューおよび分析を行った後、モデルを更新します。 モデルを更新する場合、モデルの再処理が必要になります。 詳しくは、「 [Processing Data Mining Objects](../../analysis-services/data-mining/processing-data-mining-objects.md)」をご覧ください。  
  
-   組織が新しいデータを入手したときに、モデルを動的に更新します。ソリューションの有効性を向上させるための継続的な変更は、配置戦略の一環として実行する必要があります。 詳細については、「 [データ マイニング ソリューションおよびオブジェクトの管理](../../analysis-services/data-mining/management-of-data-mining-solutions-and-objects.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [データ マイニング ソリューション](../../analysis-services/data-mining/data-mining-solutions.md)   
 [データ マイニング ツール](../../analysis-services/data-mining/data-mining-tools.md)  
  
  
