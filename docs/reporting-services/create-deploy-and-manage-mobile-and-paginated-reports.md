---
title: Reporting Services (SSRS) | Microsoft Docs
description: "オンプレミスのモバイル レポートやページ分割された Reporting Services レポートや Power BI レポートに使用するツールやサービスについて説明します。"
ms.custom: 
ms.date: 07/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: reporting-services
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- reporting-services-native
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- reports [Reporting Services]
- SSRS
- reports [Reporting Services], about reports
- Reporting Services
- SQL Server Reporting Services
ms.assetid: b8d18d3d-9db0-43e7-8286-7b46cc3a37ed
caps.latest.revision: "70"
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Active
ms.openlocfilehash: 5c137c75219c088f54130ace7fa1f466ecff1a7e
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="what-is-sql-server-reporting-services-ssrs"></a>SQL Server Reporting Services (SSRS) とは

[!INCLUDE [ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2016-and-later](../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../includes/ssrs-previous-versions.md)]

SQL Server Reporting Services (SSRS) と Power BI のすぐに使えるさまざまなツールやサービスで、オンプレミスのモバイル レポートやページ分割された Reporting Services レポートや Power BI レポートを作成、配置、管理します。

![SQL Server Reporting Services 一式](../reporting-services/media/ss-reporting-services-all-together.png "SQL Server Reporting Services 一式")

## <a name="create-deploy-and-manage-mobile-and-paginated-reports"></a>モバイル レポートやページ分割されたレポートを作成、配置、管理する

SQL Server Reporting Services は、レポートを作成、パブリッシュ、管理し、Web ブラウザー、モバイル デバイス、受信トレイ内のメールなどで表示できるようにさまざまな方法で適切なユーザーに提供するための、ユーザーのオンプレミスに配置されるソリューションです。

SQL Server 2016 の Reporting Services では、更新された製品スイートが提供されます。

* 更新されたツールと新しい作成機能で現代風のレポートを作成できる、新しくなった**"従来の" ページ分割されたレポート** 。
* さまざまなデバイスと持ち方に適応できる対応性の高いレイアウトの**新しいモバイル レポート** 。
* 最新のブラウザーで表示できる**新しい Web ポータル** 。 新しいポータルで、モバイルやページ分割された Reporting Services レポートや KPI に加えて、Power BI Desktop レポートを整理および表示することができます。 ポータルで Excel ブックを保存することもできます。

以降ではそれぞれについて詳しく説明します。

> [!NOTE]
> Power BI Report Server が見つからない場合は、 「[Power BI Report Server の概要](https://powerbi.microsoft.com/documentation/reportserver-get-started/)」を参照してください。

### <a name="whats-new-in-reporting-services"></a>Reporting Services の新機能

これらのリソースで SQL Server 2016 Reporting Services の新機能に関する最新情報をご確認いただけます。

* [Reporting Services の新機能](../reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md)
* [SQL Server Reporting Services チームのブログ](https://blogs.msdn.microsoft.com/sqlrsteamblog/)
* [Guy in a Cube YouTube チャンネル](https://www.youtube.com/channel/UCFp1vaKzpfvoGai0vE5VJ0w)

## <a name="paginated-reports"></a>ページ分割されたレポート

![ssrs-paginated-reports](../reporting-services/media/ssrs-paginated-reports.png)

Reporting Services は "従来の" ページ分割されたドキュメント スタイルのレポートと関連付けられており、データ、テーブルの行、レポートのページをより多く提供できます。 PDF ファイルや Word ファイルのような印刷用に最適化された固定レイアウトで完全なピクセルのドキュメントの生成に最適です。

その中核となる BI ワークロードは最新のものになっています。 [レポート ビルダー](../reporting-services/report-builder/report-builder-in-sql-server-2016.md)または [SQL Server Data Tools (SSDT) のレポート デザイナー](../reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt.md)を使って、更新された新しい機能でモダンな外観のレポートを作成できます。

* 既定のスタイルとカラー パレットはすべて更新されており、既定の設定で最新のミニマリズム スタイルのレポートを作成できます。
* 更新された [パラメーター] ウィンドウでは、必要に応じてパラメーターを調整できます。
* PowerPoint などの新しい形式にエクスポートできます。 PowerPoint での Reporting Services の視覚化は、単なるスクリーンショットではなく、ライブ表示であり編集可能です。
* Power BI と Reporting Services のハイブリッド エクスペリエンスを作成できます。オンプレミスの Reporting Services を Power BI で作成し直すのではなく、レポートのビジュアルを Power BI ダッシュボードにピン留めすることができます。 その後は、Power BI ダッシュボードだけですべての情報を監視できます。

## <a name="mobile-reports"></a>モバイル レポート

![ssrs-mobile-reports](../reporting-services/media/ssrs-mobile-reports.png)

モバイル コンピューティングによって使用する必要のあるデバイスが変化し、現在では異なるレポート ニーズが生まれています。 タブレットや携帯電話を導入すると、固定レイアウトのレポート エクスペリエンスではうまく機能しません。 PC のワイド画面用に設計されたレポートは、小さいだけでなく縦方向または横方向のスマートフォンの画面では最適なエクスペリエンスになりません。

このように大きく異なる画面フォーム ファクターに必要なものは固定レイアウトではなく、さまざまなデバイスと持ち方に適応する対応性の高いレイアウトです。 そのため、新しいレポートの種類であるモバイル レポートを追加しました。これは、約 1 年前に買収して製品に統合した Datazen のテクノロジが基になっています。 [SQL Server Migration Assistant for Datazen](https://www.microsoft.com/download/details.aspx?id=53128)を使って、既存の Datazen レポートを Reporting Services に移行できます。 

モバイル レポートは新しい [Mobile Report Publisher](../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md) アプリで作成します。 その後、Windows 10、iOS、Android、HTML5 用のネイティブな [モバイル デバイス用 Power BI アプリ](https://powerbi.microsoft.com/documentation/powerbi-power-bi-apps-for-mobile-devices/) で、クラウドの Power BI データやオンプレミスの SQL Server 2016 Reporting Services データにアクセスできます。 視覚エフェクトを作成すると、Mobile Report Publisher によりサンプル データが自動的に生成されるので、実際のデータでの視覚エフェクトの見え方や、各視覚エフェクトに適したデータの種類を確認できます。

## <a name="web-portal"></a>Web ポータル

![ssrs-web-portal](../reporting-services/media/ssrs-web-portal.png)

ネイティブ モードの Reporting Services のエンド ユーザーの入り口は、最新のブラウザーで表示できる最新の Web ポータルです。 新しいポータルから Reporting Services のモバイルやページ分割されたレポート、KPI に加えて、Power BI Desktop レポートのすべてにアクセスできます。 詳細については、「[Reporting Services の Power BI レポート](../reporting-services/power-bi-reports-in-reporting-services.md)」を参照してください。  

独自のカスタム ブランドを Web ポータルに適用することができます。 また、Web ポータルでは KPI の権限を作成できます。 KPI を使うと、レポートを開かなくても、主要なビジネス指標をブラウザーで簡単に見ることができます。 

新しい Web サイトは、レポート マネージャーを完全に書き直したものです。 単一ページで標準ベースの HTML5 アプリであり、Edge、Internet Explorer 10 と 11、Chrome、Firefox、Safari などのすべての主要な最新ブラウザーが最適化されています。

Web ポータルのコンテンツは、Reporting Services のモバイルやページ分割されたレポート、KPI に加えて、レポートの構成要素として使用される Power BI Desktop レポート、Excel ブック、共有データセット、共有データ ソースなどの種類別に整理されます。 従来のフォルダー階層で、ここから安全に保存および管理することができます。 お気に入りのタグを付けることができ、管理者はコンテンツを管理できます。

また、レポート処理のスケジュール設定、オンデマンドでのレポート アクセス、新しい Web ポータルでパブリッシュされたレポートのサブスクライブも、引き続き可能です。

詳細については、「[Web ポータル (SSRS ネイティブ モード)](../reporting-services/web-portal-ssrs-native-mode.md)」を参照してください。

## <a name="reporting-services-in-sharepoint-integrated-mode"></a>Reporting Services の SharePoint 統合モード

SharePoint 統合モードで Reporting Services にレポートをパブリッシュします。 レポート処理のスケジュール設定、レポートへのオンデマンド アクセス、パブリッシュされたレポートのサブスクライブ、他のアプリケーション (Microsoft Excel など) へのレポートのエクスポートを実行できます。 SharePoint サイトにパブリッシュされたレポートに対してデータ警告を作成したり、レポートのデータが変化したときに電子メール メッセージを受信できます。  

詳しくは、「 [Reporting Services Report Server (SharePoint Mode)](../reporting-services/report-server-sharepoint/reporting-services-report-server-sharepoint-mode.md)」をご覧ください。

## <a name="includessrsnoversionincludesssrsnoversion-mdmd-programming-features"></a>[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のプログラミング機能

[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のプログラミング機能を活用し、API を使用してカスタム アプリケーションのデータ処理とレポート処理を統合または拡張して、レポート作成機能を拡張およびカスタマイズできます。

詳しくは、「 [開発者ガイド (Reporting Services)](../reporting-services/reporting-services-developer-documentation.md)」をご覧ください。 

## <a name="next-steps"></a>次の手順

* [Reporting Services のインストール](../reporting-services/install-windows/install-reporting-services.md)  
* [レポート ビルダーをインストールする](../reporting-services/install-windows/install-report-builder.md)   
* [SQL Server Data Tools (SSDT) のダウンロード](http://go.microsoft.com/fwlink/?LinkID=616714)  
* [Reporting Services の Power BI レポート](../reporting-services/power-bi-reports-in-reporting-services.md)

その他の質問 [Reporting Services のフォーラムに質問してみてください](http://go.microsoft.com/fwlink/?LinkId=620231)
