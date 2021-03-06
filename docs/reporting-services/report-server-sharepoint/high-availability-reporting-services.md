---
title: "SQL Server Reporting Services での高可用性 | Microsoft Docs"
ms.custom: 
ms.date: 10/05/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-server-sharepoint
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: bd80adaa7776e9325fd387516700aa723e6a24a0
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="high-availability-in-sql-server-reporting-services"></a>SQL Server Reporting Services での高可用性

[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーは、アプリケーションのデータ、コンテンツ、プロパティ、およびセッション情報を 2 つの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リレーショナル データベースに格納するステートレス サーバーです。 したがって、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の可用性を確保するには、次のことを検討する必要があります。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] の高可用性機能を使用して、レポート サーバー データベースの稼働時間を最大限に保つ。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスをフェールオーバー クラスターで実行するように構成した場合、そのインスタンスをレポート サーバー データベースの作成時に選択できます。  
  
-   できるだけ、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] を、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] データベースと共に、またデータ ソース用に使用する。 詳細については、「[Reporting Services と Always On 可用性グループ](../../database-engine/availability-groups/windows/reporting-services-with-always-on-availability-groups-sql-server.md)」を参照してください。  
  
-   複数のレポート サーバーをスケールアウト配置で実行するように構成する。この場合、すべてのサーバーは単一のレポート サーバー データベースを共有することになります。 複数のレポート サーバー インスタンスを (可能であれば異なるサーバーに) スケールアウト配置することにより、いずれかのレポート サーバー インスタンスがダウンした場合でも、サービスの中断を効果的に防ぐことができます。  
  
 スケールアウト配置により、データベースの共有が可能となります。 どれか 1 つのレポート サーバーがダウンしても、同じ配置内の他のサーバーが処理を続行します。  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] はクラスターに対応していません。 スケールアウト配置自体は負荷分散機能を備えていないため、レポート サーバーの処理負荷を検出したり、新しい処理要求を最も負荷の低いサーバーにルーティングしたりすることはできません。 エラーが発生して完了しなかった処理要求が再ルーティングされることもありません。 負荷分散機能を実現するためには、レポート サーバーをホストする Web サーバーに対して負荷分散を構成し、それらのレポート サーバーが同じレポート サーバー データベースを共有するようにスケールアウト配置で構成する必要があります。  
  
 レポート サーバーの Web サービスと Windows サービスは単一のレポート サーバー インスタンスとして緊密に統合され、互いに連携して動作します。 どちらか一方のサービスに対して個別に可用性を構成することはできません。  

その他の質問 [Reporting Services のフォーラムに質問してみてください](http://go.microsoft.com/fwlink/?LinkId=620231)
