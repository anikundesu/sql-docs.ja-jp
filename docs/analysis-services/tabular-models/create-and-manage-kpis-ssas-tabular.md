---
title: "作成および管理 Kpi (SSAS テーブル) |Microsoft ドキュメント"
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
f1_keywords: sql13.asvs.bidtoolset.kpi.f1
ms.assetid: c96026c2-4394-4c3c-986b-4c95a4421900
caps.latest.revision: "15"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e0ce1f0c25e472fff95781e2257ddf198ba00a0f
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="create-and-manage-kpis-ssas-tabular"></a>KPI の作成および管理 (SSAS テーブル)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]このトピックでは、作成、編集、または表形式モデルで KPI (主要業績評価指標) を削除する方法について説明します。 KPI を作成するには、評価結果が KPI のベース値になるメジャーを選択します。 次に、[主要業績評価指標] ダイアログ ボックスで、評価結果が対象の値になる 2 番目のメジャーまたは絶対値を選択します。 ベース メジャーと対象のメジャーの間のパフォーマンスを測定する、状態のしきい値を定義します。  
  
 このトピックでは、次のタスクについて説明します。  
  
-   [KPI を作成するには](#bkmk_create_KPI)  
  
-   [KPI を編集するには](#bkmk_edit_KPI)  
  
-   [KPI とベース メジャーを削除するには](#bkmk_delete)  
  
-   [ベース メジャーは削除せずに KPI を削除するには](#bkmk_delete_KPI)  
  
## <a name="tasks"></a>処理手順  
  
> [!IMPORTANT]  
>  KPI を作成する前に、値を評価するベース メジャーを作成する必要があります。 次に、ベース メジャーを KPI に拡張します。 メジャーの作成方法は、別のトピック (「 [メジャーを作成および管理する &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/create-and-manage-measures-ssas-tabular.md)」) に説明があります。 KPI には対象の値も必要です。 この値には事前定義された別のメジャーまたは絶対値を使用できます。 ベース メジャーを KPI に拡張すると、[主要業績評価指標] ダイアログ ボックスで対象の値を選択し、状態のしきい値を定義できます。  
  
###  <a name="bkmk_create_KPI"></a> KPI を作成するには  
  
1.  メジャー グリッドで、ベース メジャー (値) となるメジャーを右クリックし、 **[KPI の作成]**をクリックします。  
  
2.  **[主要業績評価指標]** ダイアログ ボックスの **[ターゲット値の定義]**で、次のいずれかを選択します。  
  
     **[メジャー]**を選択し、リスト ボックスから対象のメジャーを選択します。  
  
     **[絶対値]**を選択し、数値を入力します。  
  
3.  **[状態のしきい値の定義]**で、低いしきい値および高いしきい値をクリックしてスライドします。  
  
4.  **[アイコンのスタイルの選択]**で画像の種類をクリックします。  
  
5.  **[説明]**をクリックして KPI、値、状態、および対象の説明を入力します。  
  
> [!TIP]  
>  Excel で分析機能を使用して、KPI をテストできます。 詳しくは、後の「 [Excel で分析 &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md)で [ロール マネージャー] ダイアログ ボックスを使用してロールを定義するテーブル モデル作成者向けです。  
  
###  <a name="bkmk_edit_KPI"></a> KPI を編集するには  
  
-   メジャー グリッドで、KPI のベース メジャー (値) となるメジャーを右クリックし、 **[KPI 設定の編集]**をクリックします。  
  
###  <a name="bkmk_delete"></a> KPI とベース メジャーを削除するには  
  
-   メジャー グリッドで、KPI のベース メジャー (値) となるメジャーを右クリックし、 **[削除]**をクリックします。  
  
###  <a name="bkmk_delete_KPI"></a> ベース メジャーは削除せずに KPI を削除するには  
  
-   メジャー グリッドで、KPI のベース メジャー (値) となるメジャーを右クリックし、 **[KPI の削除]**をクリックします。  
  
## <a name="alt-shortcuts"></a>Alt ショートカット  
  
|UI セクション|キー コマンド|  
|----------------|-----------------|  
|KPI ベース メジャー|Alt + B|  
|KPI ステータス|Alt + S|  
|[メジャー]|Alt + M|  
|[絶対値]|Alt + A|  
|[状態のしきい値の定義]|Alt + U|  
|[アイコンのスタイルの選択]|Alt&lt;/localizedText&gt; + &lt;localizedText&gt;I|  
|傾向|Alt + T|  
|[説明]|Alt + D|  
|傾向|Alt + T|  
  
## <a name="see-also"></a>参照  
 [KPI &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/kpis-ssas-tabular.md)   
 [メジャー &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/measures-ssas-tabular.md)   
 [メジャーを作成および管理する (SSAS テーブル)](../../analysis-services/tabular-models/create-and-manage-measures-ssas-tabular.md)  
  
  
