---
title: "参照リレーションシップの定義 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
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
ms.assetid: 4a34ba52-e3b3-4e8a-8e55-73e0cd5a97bd
caps.latest.revision: "17"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 8dd3250558baf193890bee80ca272de30510dc5b
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="lesson-5-1---defining-a-referenced-relationship"></a>レッスン 5-1-参照されているリレーションシップを定義します。
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]チュートリアルのこの時点までは、各キューブ ディメンションを定義は、外部キー リレーションシップに主キーによって、メジャー グループのファクト テーブルに直接リンクが、テーブルに基づいていました。 このトピックの実習では、 **Reseller** ディメンションを介し、 **Geography** ディメンションを再販業者販売のファクト テーブルにリンクさせます。このようにリンクを中継するディメンションを、 *参照ディメンション*といいます。 参照ディメンションにより、販売店の売上と地域を関連付けることができます。 詳細については、「 [参照リレーションシップと参照リレーションシップのプロパティの定義](../analysis-services/multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md)」を参照してください。  
  
## <a name="dimensioning-reseller-sales-by-geography"></a>販売店の売上と地域を関連付ける  
  
1.  ソリューション エクスプローラーで、 **[キューブ]** フォルダー内にある **[Analysis Services Tutorial]** を右クリックし、 **[参照]**をクリックします。  
  
2.  データ ペインからすべての階層を削除します。次に、データ ペインのデータ領域に **Reseller Sales-Sales Amount** メジャーが表示されていることを確認します。 表示されていない場合は、このメジャーをデータ ペインに追加します。  
  
3.  メタデータ ペインで **Geography** ディメンションを展開し、 **[Geographies]** ユーザー定義階層を、データ ペインの **[ここに行のフィールドをドロップします]** 領域までドラッグします。  
  
    **Reseller Sales-Sales Amount** メジャーは、 **Regions** 階層の **Country-Region** 属性メンバーによって正しく多次元化されていないことに注意してください。 **Reseller Sales-Sales Amount** の値が、各 **Country-Region** 属性メンバーで繰り返されています。  
  
    ![Reseller Sales-sales Amount メジャーの次元は](../analysis-services/media/l5-referencedrelationship-1.gif "次元 Reseller Sales-sales Amount メジャー")  
  
4.  データ ソース ビュー デザイナーを開き、 **Adventure Works DW 2012** データ ソース ビューを表示します。  
  
5.  **[ダイアグラム オーガナイザー]** ペインで、 **Geography** テーブルと **ResellerSales** テーブルの間のリレーションシップを確認します。  
  
    2 つのテーブルの間には直接的なリンクが存在しません。 一方、 **Reseller** テーブル、または **SalesTerritory** テーブルを介した間接的なリンクは存在します。  
  
6.  **Geography** テーブルと **Reseller** テーブルの間のリレーションシップを表す矢印をダブルクリックします。  
  
    **[リレーションシップの編集]** ダイアログ ボックスで、 **GeographyKey** 列は **Geography** テーブルで主キー、 **Reseller** テーブルでは外部キーとなっていることがわかります。  
  
7.  **[キャンセル]**をクリックします。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブのキューブ デザイナーに切り替え、 **[ディメンションの使用法]** タブをクリックします。  
  
    現在、 **Geography** キューブ ディメンションには、 **Internet Sales** メジャー グループ、または **Reseller Sales** メジャー グループとのリレーションシップがありません。  
  
8.  **Customer**ディメンションと **Internet Sales** メジャー グループが交差する位置にある **Full Name** セルで、参照ボタン ( **[...]** ) をクリックします。  
  
    **[リレーションシップの編集]** ダイアログ ボックスが表示されます。設定内容を確認すると、 **DimCustomer** ディメンション テーブルと **FactInternetSales** メジャー グループ テーブルの間には、これら 2 つのテーブルの **CustomerKey** 列に基づいて " **標準** " リレーションシップが定義されていることがわかります。 これまでに定義したリレーションシップは、すべて "標準" リレーションシップです。  
  
    次の図は、 **DimCustomer** ディメンション テーブルと、 **FactInternetSales** メジャー グループ テーブルの間に "標準" リレーションシップが定義されている **[リレーションシップの定義]** ダイアログ ボックスです。  
  
    ![定義するリレーションシップ ダイアログ ボックス](../analysis-services/media/l5-referencedrelationship-4.gif "リレーションシップの定義 ダイアログ ボックス")  
  
9. **[キャンセル]**をクリックします。  
  
10. **Geography**ディメンションと **Reseller Sales** メジャー グループが交差する位置の名称未設定セルで、参照ボタン ( **[...]** ) をクリックします。  
  
    **[リレーションシップの定義]** ダイアログ ボックスを確認すると、現在のところ、Geography キューブ ディメンションと Reseller Sales メジャー グループの間には、リレーションシップが何も定義されていません。 Geography ディメンションのディメンション テーブルと Reseller Sales メジャー グループのファクト テーブルの間には直接的なリレーションシップがないため、"標準" リレーションシップは定義できません。  
  
11. **[リレーションシップの種類の選択]** ボックスの一覧から **[参照対象]**をクリックします。  
  
    *中間テーブル*と呼ばれる、メジャー グループ テーブルに直接接続しているディメンションを指定することにより、参照リレーションシップを定義します。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] は、この中間テーブルを使用して参照ディメンションをファクト テーブルにリンクします。 次に、参照ディメンションを中間ディメンションにリンクさせるために使用する属性を指定します。  
  
12. **[中間ディメンション]** ボックスの一覧から **[Reseller]**を選択します。  
  
    Reseller ディメンションの基となるテーブルを介して、Geography ディメンションの基となるテーブルがファクト テーブルにリンクされます。  
  
13. **[参照ディメンションの属性]** ボックスの一覧から **[Geography Key]**を選択します。次に、 **[中間ディメンションの属性]** ボックスの一覧から **[Geography Key]** を選択してみてください。  
  
    **[中間ディメンションの属性]** ボックスの一覧には **[Geography Key]** が表示されません。 これは、 **GeographyKey** 列が **Reseller** ディメンションの属性として定義されていないためです。  
  
14. **[キャンセル]**をクリックします。  
  
次の実習では、GeographyKey 列に基づく属性を Reseller ディメンションに定義し、この問題を解決します。  
  
## <a name="defining-the-intermediate-dimension-attribute-and-the-referenced-dimension-relationship"></a>中間ディメンション属性と参照ディメンション リレーションシップの定義  
  
1.  **Reseller** ディメンションのディメンション デザイナーを開き、 **[データ ソース ビュー]** ペインで **Reseller** テーブルの各列を確認します。さらに、 **[属性]** ペインの **Reseller** ディメンションに定義されている属性を確認します。  
  
    Reseller テーブルでは、GeographyKey が列として定義されています。この列に基づく Reseller ディメンションには、ディメンション定義が何も定義されていません。 Geography ディメンションでは、Geography がディメンション属性として定義されています。Geography が、そのディメンションの基となるテーブルをファクト テーブルにリンクするキー列であるためです。  
  
2.  **Geography Key** 属性を **Reseller** ディメンションに追加するには、 **[データ ソース ビュー]** ペインで **[GeographyKey]** を右クリックし、 **[列から新しい属性を作成]**をクリックします。  
  
3.  **[属性]** ペインで、 **[Geography Key]**をクリックします。次に、[プロパティ] ウィンドウで **AttributeHierarchyOptimizedState** プロパティを **NotOptimized**に設定します。さらに、 **AttributeHierarchyOrdered** プロパティを **False**に設定し、 **AttributeHierarchyVisible** プロパティを **False**に設定します。  
  
    Reseller ディメンションの Geography Key 属性は、Geography ディメンションを Reseller Sales ファクト テーブルにリンクするためにのみ使用されます。 Geography Key 属性は表示しないため、この属性階層の表示を定義する値はありません。 また、この属性階層の並べ替えや最適化を行っても、処理パフォーマンスを低下させるだけです。 しかし、2 つのディメンション間を結ぶリンクとしてのみ機能するように、この属性を有効にする必要があります。  
  
4.  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブのキューブ デザイナーに切り替え、 **[ディメンションの使用法]** タブをクリックします。次に、**Reseller Sales**メジャー グループと **Geography** キューブ ディメンションが交差する位置にある参照ボタン ( **[...]** ) をクリックします。  
  
5.  **[リレーションシップの種類の選択]** ボックスの一覧から **[参照対象]**をクリックします。  
  
6.  **[中間ディメンション]** ボックスの一覧から **[Reseller]**を選択します。  
  
7.  **[参照ディメンションの属性]** ボックスの一覧から **[Geography Key]**を選択します。次に、 **[中間ディメンションの属性]** ボックスの一覧から **[Geography Key]** を選択します。  
  
    **[具体化する]** チェック ボックスがオンになっています。 これは、MOLAP ディメンションの既定設定です。 ディメンション属性のリンクを具体化すると、各行のファクト テーブルおよび参照ディメンション間のリンクの値が具体化され、処理中にディメンションの MOLAP 構造に格納されます。 この操作は、処理パフォーマンスやストレージの要件に少しだけ影響しますが、クエリ パフォーマンスを (場合により大幅に) 向上させます。  
  
8.  **[OK]**をクリックします。  
  
    **Geography** キューブ ディメンションが **Reseller Sales** メジャー グループにリンクされました。 このアイコンは、リレーションシップが参照ディメンションのリレーションシップであることを表します。  
  
9. **[ディメンションの使用法]** タブを開き、 **[ディメンション]** の一覧で **[Geography]**を右クリックし、 **[名前の変更]**をクリックします。  
  
10. このキューブ ディメンションの名前を **Reseller Geography**に変更します。  
  
    このキューブ ディメンションを **Reseller Sales** メジャー グループにリンクしたので、以降は同キューブ ディメンションを明示的にキューブ内で使用できます。これにより、ユーザーの混乱を避けることができます。  
  
## <a name="successfully-dimensioning-reseller-sales-by-geography"></a>販売店の売上と地域の関連付け  
  
1.  **[ビルド]** メニューの **[Analysis Services Tutorial の配置]**をクリックします。  
  
2.  配置が正常に完了したら、 **Tutorial キューブのキューブ デザイナーで** [ブラウザー] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] タブをクリックし、 **[再接続]** ボタンをクリックします。  
  
3.  メタデータ ペインで **[Reseller Geography]**を展開し、 **[Geographies]**を右クリックして、 **[行領域に追加]**をクリックします。  
  
    次の図を見ると、 **Reseller Sales-Sales Amount** メジャーが、 **Geographies** ユーザー定義階層の **Country-Region** 属性によって正しく多次元化されたことがわかります。  
  
    ![定義するリレーションシップ ダイアログ ボックス](../analysis-services/media/l5-referencedrelationship-5.gif "リレーションシップの定義 ダイアログ ボックス")  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[ファクト リレーションシップの定義](../analysis-services/lesson-5-2-defining-a-fact-relationship.md)  
  
## <a name="see-also"></a>参照  
[属性リレーションシップ](../analysis-services/multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)  
[参照リレーションシップと参照リレーションシップのプロパティの定義](../analysis-services/multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md)  
  
  
  
