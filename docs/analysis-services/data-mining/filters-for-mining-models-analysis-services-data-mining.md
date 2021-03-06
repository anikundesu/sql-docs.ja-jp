---
title: "マイニング モデルのフィルター選択 (Analysis Services - データ マイニング) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/20/2017
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
- attributes [data mining]
- filter syntax [data mining]
- models [Analysis Services], filtering
- filters [data mining]
- filtering data [Analysis Services]
ms.assetid: 0f29c19c-4be3-4bc7-ab60-f4130a10d59c
caps.latest.revision: "27"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: de1d81ae0dba51e98cb8d883ca5e7ae22eb4314b
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="filters-for-mining-models-analysis-services---data-mining"></a>マイニング モデルのフィルター選択 (Analysis Services - データ マイニング)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]データに基づくモデル フィルターでは、マイニング構造でデータのサブセットを使用するマイニング モデルを作成できます。 フィルターを使用すると、包括的なデータ ソース ビューに基づいて 1 つのマイニング構造を作成できるため、マイニング構造とデータ ソースを柔軟に設計できます。 つまり、さまざまなモデルのトレーニングとテストを行う場合に、データの各サブセットに対して個別の構造と関連モデルを作成する代わりに、データの一部だけを使用するためのフィルターを作成することができます。  
  
 たとえば、Customers テーブルと関連テーブルに、データ ソース ビューを定義します。 次に、必要とするすべてのフィールドを含むマイニング構造を 1 つ定義します。 最後に、Region などの特定の顧客属性に基づいてフィルター処理されるモデルを作成します。 その後、このモデルをコピーし、フィルター条件を変更するだけで、別の地域に基づく新しいモデルを生成できます。  
  
 この機能が役立つ実際的なシナリオには、次のような場合があります。  
  
-   性別や地域など、複数の不連続値に対して個別のモデルを作成する場合。 たとえば、衣料品店では、1 つのデータ ソースにすべての顧客の売上データが含まれていても、顧客の統計区分を使用して性別に基づく個別のモデルを作成できます。  
  
-   20 ～ 30 才、20 ～ 40 才、20 ～ 25 才など、同じデータの複数のグループ分けを作成およびテストして、モデルを試す場合。  
  
-   特定の品目を 2 個以上購入した顧客のケースのみをモデルに含めるようにするなど、入れ子になったテーブルの内容に複雑なフィルターを指定する場合。  
  
 ここでは、マイニング モデルのフィルターを作成、使用、および管理する方法について説明します。  
  
## <a name="creating-model-filters"></a>モデル フィルターの作成  
 フィルターは、次の方法で作成および適用できます。  
  
-   データ マイニング デザイナーの **[マイニング モデル]** タブで、フィルター エディターのダイアログ ボックスを利用して条件を作成します。  
  
-   マイニング モデルの **Filter** プロパティにフィルター式を直接入力します。  
  
-   AMO を使用して、モデルのフィルター条件をプログラムによって設定します。  
  
### <a name="creating-model-filters-using-data-mining-designer"></a>データ マイニング デザイナーによるモデル フィルターの作成  
 データ マイニング デザイナーでは、マイニング モデルの **Filter** プロパティを変更することによってモデルをフィルター処理します。 **[プロパティ]** ペインにフィルター式を直接入力することも、フィルターのダイアログ ボックスを開いて条件を作成することもできます。  
  
 フィルターのダイアログ ボックスは 2 つあります。 最初のダイアログ ボックスでは、ケース テーブルに適用する条件を作成できます。 データ ソースに複数のテーブルが含まれる場合は、まずテーブルを選択してから列を選択し、その列に適用する演算子と条件を指定します。 **AND**/**OR** 演算子を使用すると、複数の条件を結合できます。 値の定義に使用できる演算子は、列に含まれている値が不連続値か連続値かによって異なります。 たとえば、連続値には、 **greater than** 演算子および **less than** 演算子を使用できます。 一方、不連続値に対しては、 **= (等しい)**演算子、 **!= (等しくない)**演算子、および **is null** 演算子のみを使用できます。  
  
> [!NOTE]  
>  **LIKE** キーワードはサポートされません。 複数の不連続属性を含める場合は、個々の条件を作成し、それらを **OR** 演算子で結合する必要があります。  
  
 条件が複雑な場合、2 番目のフィルター ダイアログ ボックスを使用して、一度に 1 つのテーブルを処理するように設定できます。 2 番目のフィルター ダイアログ ボックスを閉じると、式が評価された後、ケース テーブルの他の列で設定されたフィルター条件と結合されます。  
  
### <a name="creating-filters-on-nested-tables"></a>入れ子になったテーブルに対するフィルターの作成  
 入れ子になったテーブルがデータ ソース ビューに含まれている場合は、2 番目のフィルター ダイアログ ボックスを使用して、入れ子になったテーブル内の行に対する条件を作成できます。  
  
 たとえば、顧客に関連したケース テーブルがあり、入れ子になったテーブルに顧客が購入した製品が表示されている場合、入れ子になったテーブルのフィルターで `[ProductName]=’Water Bottle’ OR ProductName=’Water Bottle Cage'`という構文を使用すると、特定の品目を購入した顧客を選択するフィルターを作成できます。  
  
 また、 **EXISTS** または **NOT EXISTS** のキーワードとサブクエリを使用すると、入れ子になったテーブルに特定の値があるかどうかに基づいてフィルター処理を行うことができます。 これにより、 `EXISTS (SELECT * FROM Products WHERE ProductName=’Water Bottle’)`のような条件を作成できます。 入れ子になったテーブルに値 `EXISTS SELECT(<subquery>)` を持つ行が 1 つ以上含まれている場合、 **から** true `Water Bottle`が返されます。  
  
 ケース テーブルに対する条件と入れ子になったテーブルに対する条件は、結合することができます。 たとえば、次の構文には、ケース テーブルに対する条件 (`Age > 30` )、入れ子になったテーブルに対するサブクエリ (`EXISTS (SELECT * FROM Products)`)、および入れ子になったテーブルに対する複数の条件 (`WHERE ProductName=’Milk’  AND Quantity>2`) が含まれています。  
  
```  
(Age > 30 AND EXISTS (SELECT * FROM Products WHERE ProductName=’Milk’  AND Quantity>2) )  
```  
  
 フィルターの作成が完了したら、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]によってフィルター テキストが評価され、DMX 式に変換された後、モデルと共に保存されます。  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のフィルター ダイアログ ボックスの使用方法については、「 [マイニング モデルへのフィルターの適用](../../analysis-services/data-mining/apply-a-filter-to-a-mining-model.md)」を参照してください。  
  
## <a name="managing-mining-model-filters"></a>マイニング モデルのフィルターの管理  
 データに基づくモデル フィルターを使用すると、同一の構造に基づく複数のモデルを簡単に作成できるため、マイニング構造とマイニング モデルの管理作業が大幅に簡素化されます。 既存のマイニング モデルをすばやくコピーして、フィルター条件だけを変更することもできます。 ただし、フィルターは混乱を招くこともあります。  
  
 ここでは、マイニング モデルに対するフィルターを管理し解釈する方法について、よくされる質問とその回答を示します。  
  
### <a name="how-can-i-tell-whether-a-filter-is-being-used"></a>フィルターが使用されているかどうか確認する方法は?  
 フィルターがモデルに適用されているかどうか判断する方法はいくつかあります。  
  
-   デザイナーで、 **[マイニング モデル]** タブをクリックし、 **[プロパティ]**を開いて、マイニング モデルの **Filter** プロパティを確認します。  
  
-   DMV (DMSCHEMA_MINING_MODELS) はフィルターのテキストを含む列を出力します。 DMV に対して次のクエリを使用して、モデルとフィルターの名前を返すことができます。  
  
    ```  
    SELECT MODEL_NAME, [FILTER]   
    FROM $SYSTEM.DMSCHEMA_MINING_MODELS  
  
    ```  
  
-   AMO で MiningModel オブジェクトの Filter プロパティの値を取得するか、XMLA で Filter 要素を検査することができます。  
  
 フィルターの内容を反映するように、モデルの名前付け規則を決めることもできます。 こうすると、関連する複数のモデルどうしを区別しやすくなります。  
  
### <a name="how-can-i-save-a-filter"></a>フィルターを保存する方法は?  
 フィルター式はスクリプトとして保存され、関連付けられたマイニング モデルまたは入れ子になったテーブルと共に格納されます。 フィルター テキストを削除した場合、復元するにはフィルター式を手動で再作成するしかありません。 このため、複雑なフィルター式を作成する場合は、フィルター テキストのバックアップ コピーを作成することをお勧めします。  
  
### <a name="why-cant-i-see-any-effects-from-the-filter"></a>フィルターの効果を確認できないのはなぜですか?  
 フィルター式の変更や追加を行った場合、フィルターの効果を確認するには、構造およびモデルを再処理する必要があります。  
  
### <a name="why-do-i-see-filtered-attributes-in-prediction-query-results"></a>フィルター選択された属性が予測クエリの結果に表示されるのはなぜですか?  
 フィルターをモデルに適用すると、フィルターはモデルをトレーニングする際に使用するケースの選択にのみ影響します。 フィルターはモデルにとって既知の属性には影響しません。また、データ ソースに存在するデータを変更したり抑制することもありません。 その結果、モデルに対するクエリは、その他の種類のケースに関する予測を返すことができ、モデルで使用される値のドロップダウン リストには、フィルターによって除外された属性値が表示されます。  
  
 たとえば、20 ～ 30 歳の女性が関係するケースだけを使用して [Bike Buyer] モデルをトレーニングするとします。 その場合でも、自転車を購入する男性の確率を予測する予測クエリを実行したり、年齢が 30 ～ 40 歳の女性の結果を予測することができます。 これは、データ ソースに存在する属性と値は理論的に可能な項目を定義し、ケースはトレーニングに使用される実際に発生した項目を定義するためです。 ただし、トレーニング データにターゲット値を持つケースが含まれないため、このクエリは非常に小さな確率を返します。  
  
 モデルの属性値を完全に隠すか匿名化する必要がある場合は、さまざまな選択肢があります。  
  
-   入力されるデータに、データ ソース ビューまたはリレーショナル データ ソースの定義の一部としてフィルターを適用します。  
  
-   属性値をマスクまたはエンコードします。  
  
-   除外された値をマイニング構造定義の一部としてカテゴリに折りたたみます。  
  
## <a name="related-resources"></a>関連リソース  
 フィルター構文の詳細およびフィルター式の例については、「 [モデル フィルターの構文と例 (Analysis Services - データ マイニング)](../../analysis-services/data-mining/model-filter-syntax-and-examples-analysis-services-data-mining.md)という構文を使用すると、特定の品目を購入した顧客を選択するフィルターを作成できます。  
  
 マイニング モデルのテスト時にモデル フィルターを使用する方法については、「 [精度チャートの種類の選択とグラフのオプションの設定](../../analysis-services/data-mining/choose-an-accuracy-chart-type-and-set-chart-options.md)」を参照してください。  
  
## <a name="see-also"></a>「  
 [モデル フィルターの構文と例 (Analysis Services - データ マイニング)](../../analysis-services/data-mining/model-filter-syntax-and-examples-analysis-services-data-mining.md)   
 [テストおよび検証 (データ マイニング)](../../analysis-services/data-mining/testing-and-validation-data-mining.md)  
  
  
