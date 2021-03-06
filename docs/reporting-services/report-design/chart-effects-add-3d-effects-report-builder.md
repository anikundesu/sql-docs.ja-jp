---
title: "グラフへの 3D 効果の追加 (レポート ビルダーおよび SSRS) | Microsoft Docs"
ms.custom: 
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-design
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ab9625d8-6557-4a4d-8123-eefa7c066ff5
caps.latest.revision: "7"
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 8d9e23f2274189f355e92c1db1463b58b823e2eb
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="chart-effects---add-3d-effects-report-builder"></a>グラフの効果 - 3D 効果の追加 (レポート ビルダー)
  3 次元 (3D) 効果を使用すると、グラフに奥行を与え、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の改ページ調整されたグラフの視覚的な効果を高めることができます。 たとえば、分割円グラフの特定のスライスを強調する場合は、そのスライスが最初に目に留まるように、グラフのパースペクティブを回転および変更することができます。 グラフに 3D 効果を適用すると、グラデーションの色および陰影のスタイルはすべて無効になります。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-apply-3d-effects-to-a-range-area-line-scatter-or-polar-chart"></a>範囲グラフ、面グラフ、折れ線グラフ、散布図、または極座標グラフに 3D 効果を適用するには  
  
1.  グラフ領域内の任意の場所を右クリックし、 **[3D 効果]**をクリックします。 **[グラフ領域のプロパティ]** ダイアログ ボックスが表示されます。  
  
2.  **[3D オプション]**で、 **[3D の有効化]** チェック ボックスをオンにします。  
  
3.  (省略可) **[3D オプション]**では、3D の角度とシーンのオプションに関連するさまざまなプロパティを設定できます。 これらのプロパティの詳細については、「 [グラフに対する 3D、傾斜、およびその他の効果 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/chart-effects-3d-bevel-and-other-report-builder.md)をクリックします。  
  
4.  **[OK]**をクリックします。  
  
## <a name="to-apply-3d-effects-to-a-funnel-chart"></a>じょうごグラフに 3D 効果を適用するには  
  
1.  グラフ領域内の任意の場所を右クリックし、 **[3D 効果]**をクリックします。 **[グラフ領域のプロパティ]** ダイアログ ボックスが表示されます。  
  
2.  **[3D オプション]**で、 **[3D の有効化]** チェック ボックスをオンにします。 **[OK]**をクリックします。  
  
3.  (省略可) じょうごグラフの外観をカスタマイズするには、[プロパティ] ペインに移動し、じょうごグラフ固有のプロパティを変更できます。  
  
    1.  プロパティ ペインを開きます。  
  
    2.  デザイン画面で、じょうごグラフの任意の場所をクリックします。 じょうごグラフの系列のプロパティが [プロパティ] ペインに表示されます。  
  
    3.  **[全般]** セクションで、 **[CustomAttributes]** ノードを展開します。  
  
    4.  **[Funnel3DDrawingStyle]** プロパティでは、じょうごグラフを四角形と円形のどちらで表示するかを選択します。  
  
    5.  **[Funnel3DRotationAngle]** プロパティでは、-10 ～ 10 の値を設定します。 これにより、3D じょうごグラフで表示する傾きの角度が決まります。  
  
## <a name="to-apply-3d-effects-to-a-pie-chart"></a>円グラフに 3D 効果を適用するには  
  
1.  グラフ領域内の任意の場所を右クリックし、[3D 効果] をクリックします。 **[グラフ領域のプロパティ]** ダイアログ ボックスが表示されます。  
  
2.  **[3D オプション]**で、 **[3D の有効化]** チェック ボックスをオンにします。 **[OK]**をクリックします。  
  
3.  (省略可) **[回転]**ボックスに、円グラフの左右反転を表す整数値を入力します。  
  
4.  (省略可) **[傾斜]**ボックスに、円グラフの上下反転の傾斜を表す整数値を入力します。  
  
5.  **[OK]**をクリックします。  
  
## <a name="to-apply-3d-effects-to-a-bar-or-column-chart"></a>横棒グラフまたは縦棒グラフに 3D 効果を適用するには  
  
1.  グラフ領域内の任意の場所を右クリックし、 **[3D 効果]**をクリックします。 **[グラフ領域のプロパティ]** ダイアログ ボックスが表示されます。  
  
2.  **[3D の有効化]** オプションをオンにします。 **[OK]**をクリックします。  
  
3.  (省略可) **[系列のクラスタリングを有効にする]** チェック ボックスをオンにします。 グラフに横棒グラフまたは縦棒グラフの系列が複数含まれている場合、このチェック ボックスをオンにすると系列がクラスター化されて表示されます。 既定では、横棒グラフまたは縦棒グラフの複数の系列は並んで表示されます。  
  
4.  **[OK]**をクリックします。  
  
5.  (省略可) 横棒グラフまたは縦棒グラフに円柱の効果を追加するには、次の手順を実行します。  
  
    1.  プロパティ ペインを開きます。  
  
    2.  デザイン画面で、系列内のいずれかの棒をクリックします。 系列のプロパティが [プロパティ] ペインに表示されます。  
  
    3.  **[全般]** セクションで、 **[CustomAttributes]** ノードを展開します。  
  
    4.  **[DrawingStyle]** プロパティで、値に **[Cylinder]** を指定します。  
  
## <a name="see-also"></a>参照  
 [グラフに対する 3D、傾斜、およびその他の効果 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/chart-effects-3d-bevel-and-other-report-builder.md)   
 [グラフの書式設定 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
 [グラフ &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)  
  
  
