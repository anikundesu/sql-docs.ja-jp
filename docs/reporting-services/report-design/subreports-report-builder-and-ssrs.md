---
title: "サブレポート (レポート ビルダーおよび SSRS) | Microsoft Docs"
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
ms.assetid: ab5bea3a-109e-4c25-92d9-494df7c52dd8
caps.latest.revision: "10"
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 41f4a2d11e3eb3200ddd992c6321cca242c8bb2c
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="subreports-report-builder-and-ssrs"></a>サブレポート (レポート ビルダーおよび SSRS)
  サブレポートは、メインのレポート本文内に別のレポートを表示するレポート アイテムです。 概念上、レポート内のサブレポートは Web ページ内のフレームとほぼ同じです。 これは、レポートをレポート内に埋め込むために使用されます。 サブレポートには、任意のレポートを使用できます。 サブレポートとして表示されるレポートは、レポート サーバー上に保存され、通常は親レポートと同じフォルダーに置かれます。 親レポートからサブレポートにパラメーターを渡すようにも設定できます。 パラメーターを使用してサブレポートの各インスタンスのデータをフィルター処理することにより、サブレポートをデータ領域内で繰り返し使用することができます。  
  
> [!NOTE]  
>  Tablix データ領域でサブレポートを使用する場合は、サブレポートとそのパラメーターが行ごとに処理されます。 多くの行がある場合、詳細レポートが適切なものであるかどうかを確認する必要があります。  
  
 ![rs_Subreport](../../reporting-services/report-design/media/rs-subreport.gif "rs_Subreport")  
  
 この図の Sales Order メイン レポートに表示されている連絡先情報は、実際には Contacts サブレポートから取得されたものです。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="comparing-subreports-and-nested-data-regions"></a>サブレポートと入れ子になったデータ領域の比較  
 サブレポートを使用してさまざまなデータ グループを表示しようと考えている場合は、代わりにテーブル、マトリックス、グラフなどのデータ領域を使用することを検討してください。 データ領域を使用しているレポートの方が、サブレポートを使用しているレポートよりもパフォーマンスが優れている可能性があります。  
  
 同じデータ領域内の同じデータ ソースから取得されるデータ グループを入れ子にする場合は、データ領域を使用してください。 同じデータ領域内の異なるデータ ソースから取得されるデータのグループを入れ子にしたり、複数の親レポートで同じサブレポートを再利用したり、別のレポート内にスタンドアロンのレポートを表示する場合は、サブレポートを使用してください。 たとえば、別のレポートの本文内に複数のサブレポートを配置して、"抄録ファイル" を作成することもできます。  
  
 データ領域はサブレポートと同じ機能の多くが提供され、柔軟性も同等ですが、パフォーマンスの点で優れています。 サブレポートは、それぞれのインスタンスが個別のレポートとして処理されるので、レポート サーバーのパフォーマンスに影響することがあります。 詳細については、「 [入れ子になったデータ領域 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/nested-data-regions-report-builder-and-ssrs.md)」を参照してください。  
  
## <a name="using-parameters-in-subreports"></a>サブレポートでのパラメーターの使用  
 親レポートからサブレポートにパラメーターを渡すには、サブレポートとして使用するレポートでレポート パラメーターを定義します。 親レポートにサブレポートを配置するときに、レポート パラメーターと、親レポートからサブレポート内のレポート パラメーターに渡す値を選択できます。  
  
> [!NOTE]  
>  サブレポートから選択するパラメーターは、クエリ パラメーターではなくレポート パラメーターです。  
  
 サブレポートは、レポート本文内またはデータ領域内に配置できます。 データ領域にサブレポートを配置する場合、同じサブレポートがグループのインスタンスまたはデータ領域の行ごとに配置されます。 グループまたは行からサブレポートに値を渡すには、サブレポートの値のプロパティで、サブレポート パラメーターに渡す値を含むフィールド用のフィールド式を使用します。  
  
 サブレポートの操作方法の詳細については、「[サブレポートおよびパラメーターの追加 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/add-a-subreport-and-parameters-report-builder-and-ssrs.md)」を参照してください。  
  
## <a name="specifying-subreport-names-and-locations"></a>サブレポートの名前と場所の指定  
 同じレポート サーバー上の異なるフォルダーにあるサブレポートを指定するようにメイン レポートを設定できます。  
  
 サブレポートを指定する構文は、レポート サーバーがネイティブ モードで動作しているか、SharePoint 統合モードで動作しているかによって異なります。 詳細については、「[外部アイテムへのパスの指定 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md)」を参照してください。  
  
 レポート ビルダーからメイン レポートのサブレポートをプレビューするには、両方のレポートが同じレポート サーバーに存在するか、サブレポートの完全なパスを指定する必要があります。  
  
## <a name="see-also"></a>参照  
 [ドリルスルー、ドリルダウン、サブレポート、および入れ子になったデータ領域 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/drillthrough-drilldown-subreports-and-nested-data-regions.md)  
  
  
