---
title: "テーブル (SSAS テーブル) 内のデータをフィルター処理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
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
f1_keywords:
- sql13.asvs.bidtoolset.notallitemsshowing.f1
- sql13.asvs.bidtoolset.autofiltermenu.f1
- sql13.asvs.bidtoolset.customfilterdb.f1
ms.assetid: 3223059d-f525-4835-bf88-ebc195d9dbdc
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 775a79fb6130bd8504efa7f05778b2690afb5803
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="filter-data-in-a-table-ssas-tabular"></a>テーブル内のデータのフィルター処理 (SSAS テーブル)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]テーブルに読み込まれている行を制御するデータをインポートするときに、フィルターを適用することができます。 データをインポートした後、行を個別に削除することはできません。 ただし、カスタム フィルターを適用して行の表示方法を制御することは可能です。 フィルター条件を満たしていない行は非表示になります。 1 行以上の列を基準にしてフィルター処理を行うことができます。 フィルター処理は追加型です。つまり、新しいフィルターによる処理は、前のフィルター処理の結果に対して行われます。したがって、フィルターを適用するごとにデータのサブセットは減っていきます。  
  
> [!NOTE]  
>  フィルターのプレビュー ウィンドウでは、表示される異なる値の数が制限されます。 制限を超えた場合は、メッセージが表示されます。  
  
### <a name="to-filter-data-based-on-column-values"></a>列の値を基準にしてデータをフィルター処理するには  
  
1.  モデル デザイナーでテーブルを選択し、フィルター処理の基準にする列の見出しの矢印をクリックします。  
  
2.  [オートフィルター] メニューで次のいずれかの操作を行います。  
  
    -   列の値の一覧で、フィルター処理の基準にする 1 つ以上の値を選択するか、選択を解除し、 **[OK]**をクリックします。  
  
         値の数が極端に多い場合、個々のアイテムが一覧に表示されないことがあります。 その場合は、"アイテムが多すぎるため、表示できません" というメッセージが表示されます。  
  
    -   列の種類に応じて **[数値フィルター]** または **[テキスト フィルター]** をクリックし、比較演算子コマンド ( **[等しい]**など) のいずれかをクリックするか、 **[カスタム フィルター]**をクリックします。 **[カスタム フィルター]** ダイアログ ボックスで、フィルターを作成し、 **[OK]**をクリックします。  
  
### <a name="to-clear-a-filter-for-a-column"></a>列のフィルターをクリアするには  
  
1.  フィルターをクリアする列の見出しの矢印をクリックします。  
  
2.  をクリックして**からフィルターをクリア\<列名 >**です。  
  
### <a name="to-clear-all-filters-for-a-table"></a>テーブルのすべてのフィルターをクリアするには  
  
1.  モデル デザイナーで、フィルターをクリアするテーブルを選択します。  
  
2.  **[列]** メニューをクリックし、 **[すべてのフィルターをクリア]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [データのフィルター処理と並べ替え (SSAS テーブル)](http://msdn.microsoft.com/library/55ebd7a6-2458-4398-911f-fcfeb2413f1b)   
 [パースペクティブ (SSAS テーブル)](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [ロール (SSAS テーブル)](../../analysis-services/tabular-models/roles-ssas-tabular.md)  
  
  
