---
title: "SQL Server 構成マネージャー ヘルプ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQL Server Configuration Manager, help
ms.assetid: 6e909911-39a6-469b-b22a-3afdfd08a30b
caps.latest.revision: "28"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 06fa3ef8d6b7f34f31b21685a1ba5b543f0fb6a6
ms.sourcegitcommit: 16347f3f5ed110b5ce4cc47e6ac52b880eba9f5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="sql-server-configuration-manager-help"></a>SQL Server 構成マネージャーのヘルプ
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Configuration Manager を構成する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サービスし、ネットワーク接続を構成します。 データベース オブジェクトの作成または管理、セキュリティの構成、 [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリの作成には、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ツールを使用します。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]の詳細については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックを参照してください。  
  
 ここでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーの各ダイアログ ボックスの F1 ヘルプ トピックについて紹介します。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Configuration Manager のバージョンを構成できません[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]よりも前[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]です。  
  
## <a name="services"></a>サービス  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に関連する各種サービスを管理します。 これらのタスクの多くは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows の [サービス] ダイアログ ボックスからも実行できますが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーでは、管理対象のサービスに関して追加の操作を実行できます。たとえば、サービス アカウントの変更時に正しい権限を適用することなどが可能です。 また、Windows の通常の [サービス] ダイアログ ボックスから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各種サービスを構成すると、そのサービスが正しく機能しないことがあります。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーでは、各種サービスに関する以下のタスクを実行できます。  
  
-   サービスの開始、停止、一時停止  
  
-   サービスの開始を自動にするか手動にするかの構成、サービスの無効化、サービスの他の設定の変更  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各種サービスが使用するアカウントのパスワードの変更  
  
-   トレース フラグ (コマンド ライン パラメーター) を使用した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の開始  
  
-   サービスのプロパティの表示  
  
## <a name="sql-server-network-configuration"></a>SQL Server のネットワーク構成  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用して、このコンピューター上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各種サービスに関する以下のタスクを実行できます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ネットワーク プロトコルの有効化または無効化  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ネットワーク プロトコルの構成  
  
> [!NOTE]  
>  プロトコルを構成して [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]に接続する方法に関する簡単なチュートリアルについては、「 [チュートリアル:データベース エンジンの概要](../../relational-databases/tutorial-getting-started-with-the-database-engine.md)」を参照してください。  
  
## <a name="sql-server-native-client-configuration"></a>SQL Server Native Client の構成  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアントは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ネットワーク ライブラリを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用して、このコンピューター上のクライアント アプリケーションに関する以下のタスクを実行できます。  
  
-   このコンピューター上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアント アプリケーションに関して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続するときのプロトコルの順序を指定できます。  
  
-   クライアント接続プロトコルを構成できます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアント アプリケーションに関して、クライアントからカスタム接続文字列を使用して接続するための [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスの別名を作成できます。  
  
 各タスクの詳細については、各タスクに関する F1 ヘルプを参照してください。  
  
#### <a name="to-open-sql-server-configuration-manager"></a>構成マネージャーを開くには、以下の手順を実行します。  
  
-   **[スタート]** ボタンをクリックし、 **[すべてのプログラム]**、 **[Microsoft SQL Server]** (バージョン)、 **[構成ツール]**の順にポイントして、 **[SQL Server 構成マネージャー]**をクリックします。  
  
  
 **アクセスする[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Configuration Manager を使用します。[!INCLUDE[win8](../../includes/win8-md.md)]**  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーは [!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理コンソール プログラムのスナップインであり、スタンドアロン プログラムではありません。そのため、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行している場合、[!INCLUDE[win8](../../includes/win8-md.md)] 構成マネージャーはアプリケーションとして表示されません。 開くには[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Configuration Manager で、**検索**チャームで、**アプリ**、型**SQLServerManager12.msc** (の[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]) または**「Sqlservermanager11.msc」** (の[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)])、キーを押します**Enter**です。  
  

## <a name="see-also"></a>参照  
 [[SQL Server のサービス]](../../tools/configuration-manager/sql-server-services.md)   
 [SQL Server ネットワークの構成](../../tools/configuration-manager/sql-server-network-configuration.md)   
 [SQL Native Client 11.0 の構成](../../tools/configuration-manager/sql-native-client-11-0-configuration.md)   
 [ネットワーク プロトコルの選択](http://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)  
  
  
