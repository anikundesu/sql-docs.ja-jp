---
title: "マスター データ サービスのインストール作業 | Microsoft Docs"
ms.custom: 
ms.date: 03/24/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: install-windows
ms.reviewer: 
ms.suite: sql
ms.technology: setup-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb7aa3e7-8807-42c8-884f-0e41d7a20837
caps.latest.revision: "32"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d26d76d4f363a5ae77c9c10cedd85afac56ffd81
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="installation-tasks-for-master-data-services"></a>マスター データ サービスのインストール作業
  この記事では、インストール作業の概要と手順へのリンクを提供します。 インストールとマスター データ サービスの構成のチュートリアルは、「[マスター データ サービスのイントールと構成](../../master-data-services/master-data-services-installation-and-configuration.md)」を参照してください。 
  
-   [インストール前の作業](#preinstall): [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]をインストールする前に、システム要件を確認します。  
  
-   [インストールの操作](#install): [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] セットアップまたはコマンド プロンプトを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をインストールします。  
  
-   [インストール後の作業](#postinstall): [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] を開き、インストール後の操作を実行できるようにします。 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベース、 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーション、および Web サービスの作成と構成を行い、サンプル モデルを配置します。  
  
##  <a name="preinstall"></a> インストール前の作業  
  
|操作|詳細|関連項目|  
|------------|-------------|--------------------|  
|インストール要件を確認する|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップを実行するコンピューターは、次の最小要件を満たしている必要があります。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップ<br /><br /> [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションおよび Web サービス<br /><br /> Web アプリケーションと同じコンピューター上でデータベースをホストする場合は、 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベース<br /><br /> <br /><br /> Web サーバーのコンピューターとデータベース サーバーのコンピューターを分離するには、Web サーバー コンピューターでのみセットアップを実行し、サポート対象となる [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] のバージョンやエディションを実行するリモート コンピューターで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースを作成します。|[SQL Server 2016 の各エディションでサポートされる機能](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)<br /><br /> [SQL Server 2016 のインストールに必要なハードウェアおよびソフトウェア](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)<br /><br /> [Web アプリケーションの要件 &#40;マスター データ サービス&#41;](../../master-data-services/install-windows/web-application-requirements-master-data-services.md)<br /><br /> [データベース要件 &#40;マスター データ サービス&#41;](../../master-data-services/install-windows/database-requirements-master-data-services.md)|  
|必要なロール、ロール サービス、および機能を構成する|セットアップを実行する前に、必要な Windows ロール、ロール サービス、および機能でコンピューターを構成します。<br /><br /> 注: この手順はワークフローの後半で実行することもできますが、インストールに引き続いてすぐに Web 構成タスクを実行できるよう、セットアップを実行する前にこの構成を行うことをお勧めします。|[Web アプリケーションの要件 &#40;マスター データ サービス&#41;](../../master-data-services/install-windows/web-application-requirements-master-data-services.md)|  
|言語サポートの注意事項を確認する|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] をインストールして実行する言語を決定します。|[多言語配置とグローバル配置 &#40;Master Data Services&#41;](../../master-data-services/install-windows/multi-lingual-and-global-deployments-master-data-services.md)|  
  
##  <a name="install"></a> インストールの操作  
  
|操作|詳細|関連項目|  
|------------|-------------|--------------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップを実行する|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションおよび [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web サービスがホストされるコンピューターで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップまたはコマンド プロンプトを使用して、 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]をインストールします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップを使用する場合、 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] は **[共有機能]** の **[機能の選択]**ページから使用できるようになります。 コマンド プロンプトを使用する場合、 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] は機能パラメーターとして使用できるようになります。 コマンド ライン セットアップ プロセスによって [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]はインストールされますが、構成されないことに注意してください。 マスター データ サービス構成マネージャーを使用して構成する必要があります。<br /><br /> インストール プロセス:<br /><br /> 共有機能用に指定する場所に [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] のフォルダーおよびファイルをインストールし、これらのオブジェクトに権限を割り当てます。<br /><br /> [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] アセンブリをグローバル アセンブリ キャッシュ (GAC) に登録します。<br /><br /> [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]をインストールします。|[インストール ウィザードからの SQL Server 2016 のインストール &#40;セットアップ&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)<br /><br /> [フォルダーとファイルの権限 &#40;マスター データ サービス&#41;](../../master-data-services/folder-and-file-permissions-master-data-services.md)|  
  
##  <a name="postinstall"></a> インストール後の作業  
  
|操作|詳細|関連項目|  
|------------|-------------|--------------------|  
|[!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] を開き、インストール後の操作を実行できるようにします。|セットアップが完了すると、 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]が開きます。 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] では、次に示すインストール後の操作がローカル コンピューターで実行されます。<br /><br /> アプリケーション プールの **サービス アカウントを含めるための Windows グループ**MDS_ServiceAccounts [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] を作成します。<br /><br /> [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] インストール パスの下に MDSTempDir フォルダーを作成し、権限を **MDS_ServiceAccounts**に割り当てます。 このフォルダーは、一時的なコンパイル ファイルが [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーション用にコンパイルされる場所です。<br /><br /> [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web.config ファイルでは、**\<compilation>** 要素の **tempDirectory** 属性が MDSTempDir フォルダーへのパスにより構成されます。|[フォルダーとファイルの権限 &#40;マスター データ サービス&#41;](../../master-data-services/folder-and-file-permissions-master-data-services.md)<br /><br /> [Web 設定リファレンス &#40;Master Data Services&#41;](../../master-data-services/web-configuration-reference-master-data-services.md)|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースを作成する|[!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] を使用して、マスター データの [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースを作成します。|[マスター データ サービス データベースの作成](../../master-data-services/install-windows/create-a-master-data-services-database.md)|  
|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションを作成する|[!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] を使用して、 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]をホストする Web アプリケーションを作成して構成します。|[マスター データ マネージャー Web アプリケーションの作成 &#40;マスター データ サービス&#41;](../../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md)|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースを Web アプリケーションに関連付ける|[!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] を使用して、 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションを [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースに関連付けます。|[Master Data Services データベースと Web アプリケーションの関連付け](../../master-data-services/install-windows/associate-a-master-data-services-database-and-web-application.md)|  
|Internet Explorer セキュリティ強化を構成する|Windows Server 2012 コンピューターに [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] をインストールするときに、 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] アプリケーション サイトでスクリプトを許可するように Internet Explorer セキュリティ強化を構成しなければならない場合があります。 そうしないと、サーバー コンピューター上の [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] アプリケーション サイトの参照が失敗します。|[Internet Explorer: セキュリティ強化の構成](http://go.microsoft.com/fwlink/p/?LinkId=223869)|  
|をインストールする [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]|[!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]は、マスター データを操作するユーザーがインストールできます。|[http://go.microsoft.com/fwlink/?LinkID=398159](http://go.microsoft.com/fwlink/?LinkID=398159)|  
|Data Quality Services (DQS) の統合の有効化|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]のユーザーは、DQS 機能との統合を有効にして、類似データの照合に使用できます。|[マスター データ サービスを使用した Data Quality Services 統合の有効化](../../master-data-services/install-windows/enable-data-quality-services-integration-with-master-data-services.md)|  
|サンプル モデルを配置します。|サンプル モデル パッケージはマスター データ サービスと共にインストールされており、MDSModelDeploy.exe を使用して配置できます。|[SQL Server 2012 の MDS サンプルの配置](~/master-data-services/sql-server-samples-model-deployment-packages-mds.md)|
  
 インストール プロセスまたは初期構成時に問題が発生した場合は、TechNet Wiki の「 [インストールおよび構成の問題のトラブルシューティング](http://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-installation-and-configuration-issues-master-data-services.aspx) 」を参照してください。  
  
 コンピューター上の [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] が不要になった場合は、 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] をアンインストールしたうえで、アンインストール プロセスの影響を受けない項目を削除するかどうかを判断できます。 詳細については、「 [マスター データ サービスのアンインストールと削除](../../sql-server/install/uninstall-and-remove-master-data-services.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server 2016 のインストール](../../database-engine/install-windows/install-sql-server.md)  
  
  
