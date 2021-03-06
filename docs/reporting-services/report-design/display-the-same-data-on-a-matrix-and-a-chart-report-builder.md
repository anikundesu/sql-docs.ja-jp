---
title: "マトリックスとグラフでの同じデータの表示 (レポート ビルダー) | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
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
ms.assetid: 1262f283-9fc2-4bc1-9c79-457f7642abc7
caps.latest.revision: "6"
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 40d6f3c22ced149953bf672e6efc903510163403
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="display-the-same-data-on-a-matrix-and-a-chart-report-builder"></a>マトリックスとグラフでの同じデータの表示 (レポート ビルダー)
  マトリックスとグラフで同じデータを表示するには、フィルター、グループ、並べ替え、およびデータに対して同じデータセットを指定するだけでなく、同じ式も指定するプロパティを両方のデータ領域に対して設定する必要があります。  
  
 両方のデータ領域が同じデータ先祖 (レポート データセット) を持つようになるので、対話的な並べ替えボタンをマトリックスに追加することにより、ユーザーがこのボタンをクリックしたときに、マトリックスとグラフの両方の並べ替え順序を変更できるようになります。 詳細については、「 [テーブルまたはマトリックスへの対話的な並べ替えの追加 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs.md)」を参照してください。  
  
 マトリックスの列グループの値をグラフの凡例として使用するには、グラフ上の系列データの色を指定してから、グループ値を表示するマトリックス セル内のテキスト ボックスの背景を塗りつぶす色として、それと同じ色を使用する必要があります。 詳細については、「[複数の図形グラフでの色の統一 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/specify-consistent-colors-across-multiple-shape-charts-report-builder-and-ssrs.md)」を参照してください。  
  
 グループ定義に関するグループ値が多すぎると、実行時にレポートが煩雑な外観になる場合があります。 このような場合は、値をフィルター選択したり、グループを組み合わせたり、グループが自動的に結合されるようにしきい値を調整したりすることが必要となります。 詳細については、「 [同じデータセットへの複数のデータ領域のリンク (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md)  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-matrix-and-chart-to-display-the-same-data"></a>マトリックスとグラフを追加して同じデータを表示するには  
  
1.  デザイン ビューでレポートを開きます。  
  
2.  **[挿入]** タブの **[データ領域]** グループで **[マトリックス]**をクリックし、レポート本文またはレポート本文内の四角形の中をクリックします。 マトリックスがレポートに追加されます。  
  
3.  **[挿入]** タブの **[データ領域]** グループで **[グラフ]**をクリックし、グラフの種類を選択します。 グラフがレポートに追加されます。  
  
4.  (省略可) **[挿入]** タブの **[レポート アイテム]** グループで **[四角形]**をクリックし、レポートをクリックします。 四角形がレポートに追加されます。 手順 2. および 3. で追加したマトリックスとグラフを四角形にドラッグします。  
  
     四角形のコンテナーに複数のデータ領域を配置すると、レポートを確認するときに、マトリックスとグラフの表示方法を制御できます。  
  
     次に示す手順では、マトリックスとグラフで表示する同じデータセット フィールドを選択します。  
  
5.  レポート データ ペインから、数値データセット フィールドをマトリックス内のデータ セルにドラッグします。  
  
     既定で、グループ値の計算には、集計関数 Sum が使用されます。 マトリックス内の集計関数を変更した場合は、グラフの集計関数も変更する必要があります。  
  
6.  マトリックスで、データが含まれたセルを右クリックして、 **[テキスト ボックスのプロパティ]**、 **[数値]**の順にクリックします。 データセット フィールド値の適切な形式を選択します。  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
8.  手順 3. で選択したのと同じデータセット フィールドをグラフの **[値]** 領域にドラッグします。  
  
9. グラフで Y 軸を右クリックして、 **[軸のプロパティ]**、 **[数値]**の順にクリックします。 手順 4. で使用したのと同じデータ形式を選択します。  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     次に示す手順では、マトリックスの行グループとグラフの系列グループを同じ式に設定し、グラフの系列グループの並べ替え順序を設定します。  
  
11. レポート データ ペインから、マトリックス行に関してグループ化するデータセット フィールドを行グループ ペインにドラッグします。  
  
     既定では、マトリックス行グループによって、グループ式と同じ並べ替え式が追加されます。  
  
12. 手順 9. で使用したのと同じデータセット フィールドをグラフの **[系列グループ]** 領域にドラッグします。  
  
13. **[系列グループ]** 領域内のグループを右クリックし、 **[系列グループのプロパティ]**をクリックします。  
  
14. **[並べ替え]**をクリックします。  
  
15. **[追加]**をクリックします。 新しい行が並べ替え式のグリッドに表示されます。  
  
16. **[並べ替え]**のドロップダウン リストから、手順 9 でグループ化に使用するように選択したデータセット フィールドを選択します。  
  
17. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     次に示す手順では、マトリックスの列グループとグラフのカテゴリ グループを同じ式に設定し、グラフのカテゴリ グループの並べ替え順序を設定します。  
  
18. レポート データ ペインから、マトリックス列に関してグループ化するデータセット フィールドを列グループ ペインにドラッグします。  
  
     既定では、マトリックス列グループによって、グループ式と同じ並べ替え式が追加されます。  
  
19. 手順 16. で使用したのと同じデータセット フィールドをグラフの **[カテゴリ グループ]** 領域にドラッグします。  
  
20. **[カテゴリ グループ]** 領域内のグループを右クリックして、 **[カテゴリ グループのプロパティ]**をクリックします。  
  
21. **[並べ替え]**をクリックします。  
  
22. **[追加]**をクリックします。 新しい行が並べ替え式のグリッドに表示されます。  
  
23. **[並べ替え]**のドロップダウン リストから、手順 16 でグループ化に使用するように選択したデータセット フィールドを選択します。  
  
24. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
25. 結果をプレビューします。 マトリックスの行グループと列グループに、グラフの系列グループとカテゴリ グループと同じデータが表示されます。  
  
## <a name="see-also"></a>参照  
 [同じデータセットへの複数のデータ領域のリンク (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md)   
 [データセット フィルター、データ領域フィルター、およびグループ フィルターの追加 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/add-dataset-filters-data-region-filters-and-group-filters.md)   
 [テーブル、マトリックス、および一覧 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [グラフ &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)  
  
  
