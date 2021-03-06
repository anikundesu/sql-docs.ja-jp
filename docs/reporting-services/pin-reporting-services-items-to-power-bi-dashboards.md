---
title: "Power BI ダッシュボードへの Reporting Services のアイテムのピン留め | Microsoft Docs"
ms.custom: 
ms.date: 09/16/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: reporting-services
ms.reviewer: 
ms.suite: pro-bi
ms.technology: reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pbi
- dashboard
- pin
- powerbi
- power bi integration
ms.assetid: 1d96c3f7-2fd4-40f7-8d1c-14a7f54cdb15
caps.latest.revision: "23"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 13af28f9c90f848c77a1709bbac115a0e70943b9
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="pin-reporting-services-items-to-power-bi-dashboards"></a>Power BI ダッシュボードへの Reporting Services のアイテムのピン留め
  [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] では、レポート ビューアー ツール バーから [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のレポート アイテムを [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] ダッシュボードに新しいタイルとしてピン留めできます。   ピン留めするには、管理者がレポート サーバーを Azure Active Directory および [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]と統合しておく必要があります。  
  
 ![rs_powerbi_icon](../reporting-services/media/ssrs-powerbi-icon.png "rs_powerbi_icon")  
  
 [!INCLUDE[applies](../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ネイティブ モード
  
##  <a name="bkmk_requirements_to_pin"></a> ピン留めの要件  
  
-   レポート サーバーが [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] 統合用に構成されている必要があります。 詳細については、「 [Power BI レポート サーバーの統合 (構成マネージャー)](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md)と統合しておく必要があります。 レポート サーバーが構成されていない場合、ツール バーに **[Power BI ダッシュボードにピン留めする]** ボタンは表示されません。  
  
     ![ssRS_Report_PowerBI](../reporting-services/media/ssrs-report-powerbi.png)  
  
-   ピン留めは、[!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] の[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]レポート ビューアー (例: `http://myserver/Reports`) から実行します。  [!INCLUDE[ssRBnoversion](../includes/ssrbnoversion-md.md)]、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]のレポート デザイナー、またはレポート サーバーの URL  たとえば、`http://myserver/ReportServer` のようにします。  
  
-   レポート サーバー サイトからのポップアップを許可するようにブラウザーを構成する必要があります。  
  
-   ピン留めしたアイテムを更新する場合は、保存された資格情報を使用するようにレポートを構成する必要があります。  アイテムをピン留めすると、ダッシュボードでのアイテムのデータ更新を管理するために、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サブスクリプションが自動的に作成されます。  レポートで保存された資格情報を使用していない場合、サブスクリプションの実行時に、 **[個人用サブスクリプション]** ページに次のようなエラー メッセージが表示されます。  
  
        PowerBI Delivery error: dashboard: IT Spend Analysis Sample, visual: Chart2, error: The current action cannot be completed. The user data source credentials do not meet the requirements to run this report or shared dataset. Either the user data source credential.
 
    資格情報を保存する方法の詳細については、「 [Reporting Services データ ソースに資格情報を保存する](../reporting-services/report-data/store-credentials-in-a-reporting-services-data-source.md)」の「レポート固有のデータ ソース用の保存された資格情報を構成する (ネイティブ モード)」を参照してください。  
  
##  <a name="bkmk_supported_items"></a> ピン留めできるアイテム  
 次のレポート アイテムは、 [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] ダッシュボードにピン留めできます。  データ領域内で入れ子になっているアイテムをピン留めすることはできません。 たとえば、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のテーブルまたはリスト内で入れ子になっているアイテムはピン留めできません。  
  
-   グラフ  
  
-   ゲージ パネル  
  
-   マップ  
  
-   画像  
  
-   アイテムはレポート本文に含まれている必要があります。  ページ ヘッダーまたはページ フッター内のアイテムをピン留めすることはできません。  
  
-   最上位の四角形内の個々のアイテムはピン留めできますが、そのすべてのアイテムを 1 つのグループとしてピン留めすることはできません。  
  
##  <a name="bkmk_to_pin"></a> レポート アイテムをピン留めするには  
  
1. [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]にサインインしていることを確認します。 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]で、メニュー項目の **[個人用設定]** を選択し、サインインします。 詳細については、「  [Power BI 統合の個人用設定 &#40;Web ポータル&#41;](http://msdn.microsoft.com/en-us/85c2fac7-80bf-45b7-8654-764b5f5231f5) 」を参照してください。

    ![ssRS_WebPortal_MySettings](../reporting-services/media/ssrs-webportal-mysettings.png)  
  
2. レポートが含まれた [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] のフォルダーに移動し、レポートを表示します。  
  
3. レポートの表示中に、ツール バーの **[Power BI にピン留め]** ボタンをクリックします。  まだサインインしていない場合は、サインインするよう求められます。  [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] ボタンが表示されていない場合は、レポート サーバーが [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]と統合されていません。 詳細については、「 [Power BI レポート サーバーの統合 (構成マネージャー)](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md)と統合しておく必要があります。  
  
    ![ssRS_Report_PowerBI](../reporting-services/media/ssrs-report-powerbi.png)  
  
4. [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]にピン留めするレポート アイテムをクリックします。 ピン留めできるアイテムは一度に 1 つに限られます。  レポート ビューアーにレポートの影付きのビューが表示されます。ピン留めできるレポート アイテムは強調表示され、ピン留めできないアイテムは濃い影付きになります。  
  
    **(1)** ピン留めするダッシュボードを含むグループを選択し、 **(2)** アイテムをピン留するダッシュボードも選択して、 **(3)** ダッシュボードでのタイルの更新頻度を選択します。   ![注:](../analysis-services/instances/install-windows/media/ssrs-fyi-note.png "注:") 更新は [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サブスクリプションによって管理されます。アイテムをピン留めした後に、サブスクリプションを編集し、別の更新スケジュールを構成できます。  
  
    ![ssRS_Pin_to_PowerBI](../reporting-services/media/ssrs-pin-to-powerbi.png)  
  
5. **[ピン留め]**の選択  
  
    **[正常にピン留めされました]** ダイアログで、 **[Power BI で確認する]** リンクをクリックすると、ダッシュボードに移動し、ピン留めしたアイテムを確認できます。  
  
6. **[閉じる]** をクリックして、レポートを通常のビューに戻します。  
  
##  <a name="bkmk_in_the_dashboard"></a> ダッシュ ボードでの操作

ダッシュボードにレポート アイテムをピン留めすると、そのタイルは他のダッシュボード タイルと同様に表示され、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]からピン留めされたタイルであることを示すものは表示されません。 タイルのプロパティがレポート アイテムからどのように設定されるのかを以下に示します。  
  
[!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] ダッシュボードでは、ピン留めされたレポート アイテムは他のタイルと同様に動作します。

**(1)** タイルを他のダッシュボードにピン留めできます。

**(2)** **[タイルの詳細]** で、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のレポート タイトルがタイルの既定のタイトルとして使用されていることがわかります。

**(3)** タイルのサブタイトルは、タイルがピン留めされた日時、または [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]からデータが最後に更新された日時に基づいています。 更新スケジュールは、レポート アイテムをピン留めしたときに自動的に作成された [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サブスクリプションによって管理されます。

**(4)** タイル自体をクリックすると、 [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] は **(3) カスタム リンク** を使用して登録済みのレポート サーバーの [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] ページに移動します。 このリンクは、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]からアイテムをピン留めしたときに設定されます。 レポート サーバーにインターネット接続していない場合、ブラウザーにエラーが表示されます。  

![ssrs_pinned_tile_details](../reporting-services/media/ssrs-pinned-tile-details.png "ssrs_pinned_tile_details")  
  
##  <a name="bkmk-troubleshoot"></a> 問題のトラブルシューティング  
  
-   **レポート ビューアー ツール バーに [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] ボタンがない:**  これは、レポート サーバーが [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] と統合されていないことを示しています。 詳細については、「 [Power BI レポート サーバーの統合 (構成マネージャー)](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md)と統合しておく必要があります。  
  
- **ピン留めできない**: アイテムをピン留めしようとすると、次のエラー メッセージが表示されます。「 [ピン留めできるアイテム](#bkmk_supported_items)」を参照してください。  
  
      Cannot Pin: There are no report items on this page that you can pin to [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)].  
  
-   [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] ダッシュボードで**ピン留めされたアイテムに古いデータが表示され**、一定期間更新されなかった:   ユーザーの資格情報トークンの有効期限が切れているので、もう一度サインインする必要があります。  Azure と [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] へのユーザーの資格情報登録の有効期間は 90 日間です。 [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]で、 **[個人用設定]**をクリックします。 詳細については、「 [Power BI 統合の個人用設定 &#40;Web ポータル&#41;](http://msdn.microsoft.com/en-us/85c2fac7-80bf-45b7-8654-764b5f5231f5)」を参照してください。  
  
-   [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] ダッシュボードで**ピン留めされたアイテムに古いデータが表示され**、一度も更新されていない:   問題は、保存された資格情報を使用するようにレポートが構成されていないことです。 レポート アイテムのピン留め操作により、タイルの更新スケジュールを管理する [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サブスクリプションが作成されるため、レポートでは保存された資格情報を使用する必要があります。 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サブスクリプションでは、保存された資格情報が必要です。 **[個人用サブスクリプション]** ページを確認すると、次のようなエラー メッセージが表示されます。  
  
        PowerBI Delivery error: dashboard: SSRS items, visual: Image3, error: The current action cannot be completed. The user data source credentials do not meet the requirements to run this report or shared dataset. Either the user data source credentials are not stored in the report server database, or the user data source is configured not to require credentials but the unattended execution account is not specified. (rsInvalidDataSourceCredentialSetting)
  
-   **Power BI の資格情報の有効期限が切れている:**  アイテムをピン留めしようとすると、次のエラー メッセージが表示されます。 [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]で、 **[個人用設定]** をクリックし、[個人用設定] ページで **[サインイン]**をクリックします。 詳細については、「  [Power BI 統合の個人用設定 &#40;Web ポータル&#41;](http://msdn.microsoft.com/en-us/85c2fac7-80bf-45b7-8654-764b5f5231f5) 」を参照してください。  
  
        Cannot Pin : Unexpected Server Error: Missing, invalid or expired Power BI credentials.  
  
-   **ピン留めできない**: 読み取り専用状態のダッシュボードにアイテムをピン留めしようとすると、次のようなエラー メッセージが表示されます。  
  
        Server Error : The item 'Dashboard deleted 015cf022-8e2f-462e-88e5-75ab0a04c4d0' cannot be found. (rsItemNotFound)  
  
##  <a name="bkmk_subscription_management"></a> サブスクリプション管理  
 トラブルシューティングのセクションで説明したサブスクリプション関連の問題に加え、 [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] 関連のサブスクリプションを維持する際に次の情報も役立ちます。
  
-   **アイテム名の変更:** ピン留めされたレポート アイテムの名前を変更したり、アイテムを削除したりすると、 [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] のタイルが更新されなくなり、次のようなエラー メッセージが表示されます。  アイテムを元の名前に戻すと、サブスクリプションが再び機能し始め、サブスクリプションのスケジュールどおりにタイルが更新されるようになります。  
  
        PowerBI Delivery error: dashboard: SSRS items, visual: Image1, error: Error: Report item 'Image1' cannot be found.  
  
     サブスクリプションのプロパティを編集し、 **レポートのビジュアル名** を適切なレポート アイテム名に変更することもできます。 ![power bi の更新に使用する、ビジュアルの変更](../reporting-services/media/ssrs-powerbi-subscription-visual.png "power bi の更新に使用する、ビジュアルの変更")  
  
-   **タイルの削除**: [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]でタイルを削除しても、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] と **[個人用サブスクリプション]**ページで関連するサブスクリプションが削除されず、次のようなエラー メッセージが表示されます。 サブスクリプションを削除できます。  
  
        PowerBI Delivery error: dashboard: SSRS items, visual: Image3, error: The item 'Tile deleted af7131d9-5eaf-480f-ba45-943a07d19c9f' cannot be found.  

## <a name="video"></a>ビデオ

<iframe width="560" height="315" src="https://www.youtube.com/embed/QhPQObqmMPc" frameborder="0" allowfullscreen></iframe>

## <a name="see-also"></a>参照  
 [Power BI レポート サーバーの統合 (構成マネージャー)](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md)   
 [Power BI 統合の個人用設定 &#40;Web ポータル&#41;](http://msdn.microsoft.com/en-us/85c2fac7-80bf-45b7-8654-764b5f5231f5)  
 [Power BI のダッシュボード](https://powerbi.microsoft.com/documentation/powerbi-service-dashboards/)  
  
  
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../includes/feedback-stackoverflow-msdn-connect-md.md)]

