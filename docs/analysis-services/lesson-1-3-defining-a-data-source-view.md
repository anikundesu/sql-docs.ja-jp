---
title: "ソース ビューのデータを定義する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: af00938a-5a06-4fae-b2fc-f3fb0ca3cea5
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: fb0297f91f6a7b3cac69e262eac707cdc59040bd
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="lesson-1-3---defining-a-data-source-view"></a>レッスン 1 ~ 3-データ ソース ビューを定義します。
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]使用するデータ ソースを定義した後、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]プロジェクトでは、次の手順は一般に、プロジェクトのデータ ソース ビューを定義します。 データ ソース ビューは、指定したテーブルのメタデータと、プロジェクトのデータ ソースによって定義されているビューを 1 つに統合したものです。 データ ソース ビューにメタデータを格納すると、基になるデータ ソースへの接続を開かなくても、開発時にメタデータを操作することができます。 詳細については、 [「多次元モデルのデータ ソース ビュー」](../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)を参照してください。  
  
次の実習では、 **AdventureWorksDW2012** データ ソースの 5 つのテーブルを含むデータ ソース ビューを定義します。  
  
### <a name="to-define-a-new-data-source-view"></a>新しいデータ ソース ビューを定義するには  
  
1.  ソリューション エクスプローラー (Microsoft Visual Studio ウィンドウの右側) で、**[データ ソース ビュー]** を右クリックし、**[新しいデータ ソース ビュー]** をクリックします。  
  
2.  **[データ ソース ビュー ウィザードへようこそ]** ページで **[次へ]**をクリックします。 **[データ ソースの選択]** ページが表示されます。  
  
3.  **[リレーショナル データ ソース]** の一覧で、**[Adventure Works DW 2012]** データ ソースが選択されていることを確認します。 **[次へ]**をクリックします。  
  
    > [!NOTE]  
    > 複数のデータ ソースに基づくデータ ソース ビューを作成するには、まず、1 つのデータ ソースに基づくデータ ソース ビューを定義します。 このデータ ソースをプライマリ データ ソースと呼びます。 次に、2 番目のデータ ソースのテーブルとビューを追加します。 複数のデータ ソースの関連するテーブルに基づいた属性を含むディメンションを設計する場合は、分散クエリ エンジン機能を使用するために、 [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データ ソースをプライマリ データ ソースとして定義する必要があります。  
  
4.  **[テーブルとビューの選択]** ページには、選択したデータ ソース内で使用できるオブジェクトの一覧が表示されます。この一覧からテーブルとビューを選択します。 この一覧をフィルター処理すれば、目的のテーブルとビューを簡単に選択できるようになります。  
  
    > [!NOTE]  
    > 右上隅の最大化ボタンをクリックして、ウィンドウを全画面表示にします。 これによって、使用できるオブジェクトの一覧全体を簡単に確認できるようになります。  
  
    **[使用できるオブジェクト]** ボックスの一覧で、次のオブジェクトを選択します。 Ctrl キーを押しながらクリックすると、複数のテーブルを選択できます。  
  
    -   **DimCustomer (dbo)**  
  
    -   **DimDate (dbo)**  
  
    -   **DimGeography (dbo)**  
  
    -   **DimProduct (dbo)**  
  
    -   **FactInternetSales (dbo)**  
  
5.  選択したテーブルを [ **>** 含まれているオブジェクト **] の一覧に追加するには、** をクリックします。  
  
6.  **[次へ].**  
  
7.  [名前] フィールドに **Adventure Works DW 2012** と表示されていることを確認し、**[完了]** をクリックします。  
  
    ソリューション エクスプローラーの **[データ ソース ビュー]** フォルダーに、 **Adventure Works DW 2012** データ ソース ビューが表示されます。 データ ソース ビューの内容は、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]のデータ ソース ビュー デザイナーにも表示されます。 このデザイナーは次の要素で構成されています。  
  
    -   **[ダイアグラム]** ウィンドウ: テーブルおよびテーブル間のリレーションシップがグラフィカルに表示されます。  
  
    -   **[テーブル]** ウィンドウ: テーブルとそのスキーマ要素が表示されます。  
  
    -   **[ダイアグラム オーガナイザー]** ウィンドウ: サブダイアグラムを作成して、データ ソース ビューのサブセットを表示できます。  
  
    -   データ ソース ビュー デザイナーのツール バー  
  
8.  [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 開発環境を最大化するには、**[最大化]** ボタンをクリックします。  
  
9. **[ダイアグラム]** ウィンドウ内のテーブルを 50% の大きさで表示するには、データ ソース ビュー デザイナーのツール バーにある **[ズーム]** アイコンをクリックします。 表示サイズを 50% にすると、各テーブルの列の詳細が非表示になります。  
  
10. ソリューション エクスプローラーを非表示にするには、**[自動的に隠す]** ボタン (タイトル バーの押しピン アイコン) をクリックします。 再びソリューション エクスプローラーを表示するには、開発環境の右側に表示されているソリューション エクスプローラーのタブの上にポインターを置きます。 ソリューション エクスプローラーの非表示を解除するには、**[自動的に隠す]** ボタンを再びクリックします。  
  
11. ウィンドウが既定で非表示になっていない場合は、[プロパティ] ウィンドウと [ソリューション エクスプローラー] ウィンドウのタイトル バーで **[自動的に隠す]** ボタンをクリックします。  
  
    これで、**[ダイアグラム]** ウィンドウ内に、すべてのテーブルとそのリレーションシップを表示できるようになりました。 FactInternetSales テーブルと DimDate テーブルの間には 3 つのリレーションシップがあることがわかります。 各売上には、それぞれ 3 つの日付が関連付けられています。受注日、期日、出荷日の 3 つです。 リレーションシップの詳細を表示するには、**[ダイアグラム]** ウィンドウで、リレーションシップの矢印をダブルクリックします。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[既定のテーブル名の変更](../analysis-services/lesson-1-4-modifying-default-table-names.md)  
  
## <a name="see-also"></a>参照  
[「多次元モデルのデータ ソース ビュー」](../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)  
  
  
  
