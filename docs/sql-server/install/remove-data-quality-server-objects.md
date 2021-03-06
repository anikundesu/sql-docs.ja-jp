---
title: "Data Quality Server オブジェクトの削除 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: install
ms.prod_service: sql-non-specified
ms.service: database-engine
ms.component: 
ms.reviewer: 
ms.suite: sql
ms.technology: setup-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b7c6dbb-b40e-4822-9caa-608e1056af8e
caps.latest.revision: "14"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 966a649d7dc0a4d54e008132764c313f9db9f6b3
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="remove-data-quality-server-objects"></a>Data Quality Server オブジェクトの削除
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスから [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] をアンインストールしても、[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] を持つ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを完全に削除しても、DQS データベースを含む一部の [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] オブジェクトは削除されません。 これは、SQL Server セットアップを使用して [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] をアンインストールする場合、DQS データが失われないことを意味します。 このような [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] オブジェクトは、アンインストール プロセスの完了後に手動で削除する必要があります。  
  
> [!NOTE]  
>  -   [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]をアンインストールする前に、既存のすべてのナレッジ ベースを .dqsb ファイルにエクスポートしてバックアップするよう検討します。後からそのファイルを使用して、すべてのナレッジ ベースを [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] の新しいインストールにインポートします。 DQS のすべてのナレッジ ベースのエクスポートとインポートを行うには、コマンド プロンプトから適切なコマンド ライン パラメーターを使用して DQSInstaller.exe を実行する必要があります。 詳細については、「 [Export and Import DQS Knowledge Bases Using DQSInstaller.exe](../../data-quality-services/install-windows/export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md)」を参照してください。  
> -   データベースを保持して後からデータの復元に使用する必要がある場合は、DQS データベースを削除する前にデータベースのバックアップを検討します。 詳細については、「 [DQS データベースの管理](../../data-quality-services/manage-dqs-databases.md)」を参照してください。  
  
## <a name="uninstall-data-quality-server-from-a-sql-server-instance"></a>SQL Server インスタンスからの Data Quality Server のアンインストール  
 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] インスタンスから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をアンインストールするだけの場合、 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] のアンインストール プロセスの完了後に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの次の [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] オブジェクトを手動で削除する必要があります。  
  
-   DQS_MAIN、DQS_PROJECTS、および DQS_STAGING_DATA データベース。  
  
-   \##MS_dqs_db_owner_login## と ##MS_dqs_service_login## ログイン。  
  
-   master データベースの DQInitDQS_MAIN ストアド プロシージャ。  
  
 SQL Server Management Studio でこれらのオブジェクトを削除するには、オブジェクトを右クリックして、ショートカット メニューの **[削除]** をクリックします。  
  
> [!IMPORTANT]  
>  コマンド プロンプトで [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] コマンド ライン パラメーターを使用して SQL サーバー インスタンスから `–uninstall` をアンインストールするだけで、アンインストール プロセスの一部としてすべての DQS オブジェクトが削除されます。 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]のアンインストール後に手動でそれらを削除する必要はありません。 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] をコマンド プロンプトからアンインストールするには、コマンド プロンプトで次のコマンドを入力し、Enter キーを押します。   
> `dqsinstaller.exe -uninstall`  
  
## <a name="uninstall-sql-server-instance-containing-data-quality-server"></a>Data Quality Server を含む SQL Server インスタンスのアンインストール  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を含む [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]インスタンスを完全にアンインストールする場合、アンインストール プロセスの完了後に、コンピューターから DQS_MAIN データベース、DQS_PROJECTS データベース、および DQS_STAGING_DATA データベースを手動で削除する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定のインストールでは、DQS_MAIN、DQS_PROJECTS、および DQS_STAGING_DATA のデータベース ファイルは C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA にあります。  
  
## <a name="see-also"></a>参照  
 [SQL Server の既存のインスタンスのアンインストール &#40;セットアップ&#41;](../../sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md)   
 [SQL Server 2016 のアンインストール](../../sql-server/install/uninstall-sql-server.md)  
  
  
