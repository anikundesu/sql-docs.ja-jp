---
title: "[データベース構成] ページ (Master Data Services 構成マネージャー) | Microsoft Docs"
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.mds.configmanager.dbpg.f1
ms.assetid: dd72220e-a599-465d-8b84-9bb6a7433216
caps.latest.revision: "8"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ac732f7d981c1183dccc56df7ec9cb31b4eea307
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="database-configuration-page-master-data-services-configuration-manager"></a>[データベース構成] ページ (Master Data Services 構成マネージャー)
  **[データベース構成]** ページを使用すると、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースのシステム設定を編集できます。 システム設定は、選択した [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースに関連付けられている Web アプリケーションおよび Web サービスすべてに影響します。 システム設定を有効にして構成できるようにするには、事前に [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースを選択または作成する必要があります。  
  
## <a name="current-database"></a>現在のデータベース  
 システム設定の編集を行う、既存の [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースを選択するか、新しいデータベースを作成します。 新しいデータベースは、作成後に選択されます。  
  
|コントロール名|Description|  
|------------------|-----------------|  
|**SQL Server インスタンス (SQL Server instance)**|選択した [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスの名前が表示されます。 これは、インスタンスに接続して、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースを選択または作成するまで、空白です。|  
|**[Master Data Services データベース]**|選択した [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースの名前が表示されます。 これは、インスタンスに接続して、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースを選択または作成するまで、空白です。|  
|**[Master Data Services データベース バージョン]**|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベース スキーマのバージョン。|  
|**[データベースの作成]**|**データベースの作成** ウィザードを開きます。このウィザードから、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスに接続し、そのインスタンス用の [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースを作成できます。|  
|**[データベースの選択]**|**[データベースへの接続]** ダイアログ ボックスを開きます。このダイアログ ボックスで、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスに接続して、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースを選択できます。|  
|**[データベースのアップグレード]**|ウィザードを開き、指定した [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースをアップグレードできます。 このボタンは指定したデータベースでアップグレードが必要な場合にのみ使用できます。|  
|**[修復]**|MDS データベースが正しくインストールされていることを確認するには、このボタンをクリックします。 これは、MDS データベースをホストしたことがない [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスに MDS データベースをバックアップおよび復元する場合に便利です。|  
  
## <a name="system-settings"></a>システム設定  
 選択した [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースに関連付けられている Web アプリケーションおよび Web サービスすべてのシステム設定を編集します。  
  
 これらの設定は、[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]で使用することができ、データベースの System Settings テーブル (mdm.tblSystemSetting) に格納されます。 すべての設定の一覧については、「[システム設定 (マスター データ サービス)](../master-data-services/system-settings-master-data-services.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[マスター データ サービスのインストールと構成](../master-data-services/master-data-services-installation-and-configuration.md) [データベース要件 &#40;マスター データ サービス&#41;](../master-data-services/install-windows/database-requirements-master-data-services.md)  
  
  
