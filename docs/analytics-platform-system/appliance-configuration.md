---
title: "アプライアンスの構成 (Analytics Platform System)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 064e7485-7026-4acf-8084-f5d30757d177
caps.latest.revision: "43"
ms.openlocfilehash: 05670f1727691b1abc0fd98dd5970c7697725b8e
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="appliance-configuration"></a>アプライアンスの構成
ご使用の環境の分析プラットフォーム システムを構成するために必要なタスクのチェックリストを提供します。 アプライアンスを使用する前に、これらの構成タスクが必要です。  
  
> [!WARNING]  
> Analytics Platform System を使用して**Configuration Manager**最善の方法は、サポートされる唯一の方法は、ツールで使用可能なタスクを実行します。  
  
## <a name="BeforeTasks"></a>はじめに  
  
### <a name="prerequisites"></a>Prerequisites  
  
1.  アプライアンスをデータ センターにインストールされ、電源をオンにする必要があります。  
  
2.  IHV によって提供される、次の情報を確認してください。  
  
    -   PDW 管理ノードの外部 IP アドレス (*PDW_region-*CTL01)  
  
    -   アプライアンスのドメイン名  
  
    -   アプライアンスのドメイン管理者のユーザー名とパスワード  
  
3.  信頼された証明書を取得します。 クライアントへの接続に使用できるように、後の手順ではインポート、**管理コンソール**セキュリティで保護された接続を使用します。 証明書をパスワードで保護された PFX ファイルでコントロールのノードに保存します。  
  
4.  起動して、 **Configuration Manager**、次の手順を使用します。  
  
    1.  使用して**リモート デスクトップ**PDW 管理ノードに接続する (*PDW_region*-CTL01)。 (CTL01 の外部 IP アドレスで接続する必要があります)。  
  
    2.  起動して、 **Configuration Manager**から、**開始**PDW 管理ノードのメニュー。 最初の画面の Configuration Manager では、IHV によって作成された、アプライアンス トポロジが表示されます。 これは、アプライアンスの一部として、SQL Server PDW ソフトウェアで認識されるハードウェア ノードの一覧です。 アプライアンス トポロジ画面の任意の設定を変更する必要はありません。  
  
## <a name="CMTasks"></a>Configuration Manager のタスクを実行します。  
SQL Server PDW**Configuration Manager** (PDWCM) は、アプライアンス レベルの操作を実行するアプライアンス レベルの設定を変更して、SQL Server PDW システム管理者が使用しているアプライアンスの管理ツールです。 たとえば、パスワードをリセット、タイム ゾーンの設定、IP アドレスを変更、SSL 証明書を構成、ファイアウォール経由のリモート アクセスを有効にする、開始するか、アプライアンスの停止をファイルの瞬時初期化を設定 PDWCM を使用します。  
  
使用して**Configuration Manager**次の構成タスクを実行します。  
  
|構成タスク|Description|  
|----------------------|---------------|  
|コンポーネントの物理名を理解します。|[PDW とアプライアンス ファブリックの物理的なコンポーネントと #40 です。Analytics Platform System &#41;](pdw-and-appliance-fabric-physical-components.md)|  
|SQL Server PDW 構成マネージャーを起動します。|[構成マネージャー &#40; を起動します。Analytics Platform System &#41;](launch-the-configuration-manager.md)|  
|ドメイン管理者のパスワードを変更します。|アプライアンスには、プライベート Windows Active Directory ドメイン サービス、アプライアンス内のノードを認証するために使用します。<br /><br />IHV は、アプライアンスの既定のドメイン管理者のパスワードを設定します。 これは、セキュリティで保護されているパスワードを変更する必要があります。<br /><br />**Configuration Manager**は、唯一サポートされているドメイン管理者のパスワードを変更する方法です。<br /><br />詳細については、次を参照してください。[パスワード リセット (&) #40 です。Analytics Platform System &#41;](password-reset.md).|  
|パスワードを変更、 **sa**ログオン|SQL Server PDW がという名前のシステム管理者ログオン**sa**です。 **Sa**ログオンがすべての特権を持っています。 付与、拒否、または権限を取り消すことできます。 すべてのシステム ビューを表示することもできます。<br /><br />詳細については、次を参照してください。[パスワード リセット (&) #40 です。Analytics Platform System &#41;](password-reset.md).|  
|アプライアンスのタイム ゾーンを設定します。|アプライアンスのすべてのノードの時間 (ローカルまたはその他の目的の時間) を設定します。<br /><br />詳細については、次を参照してください。[アプライアンス タイム ゾーンの構成 &#40;です。Analytics Platform System &#41;](appliance-time-zone-configuration.md).|  
|SQL Server PDW アプライアンスの外部に公開されたネットワーク設定を指定します。|[アプライアンス ネットワークの構成 &#40;です。Analytics Platform System &#41;](appliance-network-configuration.md)|  
|管理コンソールのセキュリティ証明書をインポートします。|証明書が HTTPS 経由で Secure Sockets Layer (SSL) 接続を提供できる、[アプライアンスを管理コンソール &#40; を使用して監視します。Analytics Platform System &#41;](monitor-the-appliance-by-using-the-admin-console.md). 既定では、**管理コンソール**、お客様のプライバシーがいないサーバー認証を提供する自己署名証明書が含まれています。 この証明書エラーを返しますという内容の Internet Explorer:「この web サイトのセキュリティ証明書に問題がある」ユーザーが接続する場合。 この接続は、クライアントとサーバー間のインフライトのデータを暗号化、接続が攻撃者からリスクのままであります。<br /><br />SQL Server PDW の管理者は、セキュリティで保護された接続があるし、Internet Explorer でレポートされるエラーを削除するために、クライアントによって認識される信頼された証明機関にチェーンされている証明書をすぐに取得する必要があります。 (推奨) 管理 ノードの仮想 IP アドレスをマップする完全修飾ドメイン名が必要ですか、管理者コンソールにアクセスするバーは、ブラウザーのアドレスに入力された値に一致する証明書の名前。<br /><br />使用して、 **Configuration Manager**を追加または信頼された証明書を削除します。 Microsoft Windows HTTP サービス証明書の構成ツールを使用して直接 (`winHttpCertCfg.exe`) 証明書の管理はサポートされていません。<br /><br />詳細については、次を参照してください。 [PDW 証明書のプロビジョニング (&) #40 です。Analytics Platform System &#41;](pdw-certificate-provisioning.md).|  
|有効にするにまたは許可するか、SQL Server PDW アプライアンス上の特定のポートにアクセスできないようにする Windows ファイアウォールの規則を無効にします。|IHV は構成し、正常に動作するアプライアンスに必要なファイアウォール規則を有効にします。 ほとんどの場合をいません有効にするにまたはファイアウォール ルールを無効にします。<br /><br />詳細については、次を参照してください。 [PDW のファイアウォールの構成 &#40;です。Analytics Platform System &#41;](pdw-firewall-configuration.md).|  
|開始し、停止、SQL Server PDW アプライアンス|停止するか、SQL Server PDW アプライアンスを開始します。 詳細については、次を参照してください。 [PDW サービスの状態と #40 です。Analytics Platform System &#41;](pdw-services-status.md).|  
|使用してファイルの瞬時初期化オプションの確認、**特権** ダイアログ ボックス|ファイルの瞬時初期化は、データ ファイルの操作をより迅速に実行を許可する SQL Server 機能です。 有効にするか SQL Server PDW Network Service アカウントに SE_MANAGE_VOLUME_NAME 特権が付与されている場合にのみです。 既定でオフになっているがします。<br /><br />詳細については、次を参照してください。[瞬時ファイル初期化の構成 &#40;です。Analytics Platform System &#41;](instant-file-initialization-configuration.md).|  
|バックアップから master データベースを復元します。|現在の削除**マスター**データベースにあり、バックアップに置き換えられます。 詳細については、次を参照してください[マスター データベース &#40; を復元。Analytics Platform System &#41;](restore-the-master-database.md).|  
  
## <a name="AddTasks"></a>追加の構成タスクを実行します。  
実行した後、 **Configuration Manager**のタスクは、次の追加の構成タスクの一覧を実行します。 これらのタスクの一部は省略できます。  
  
|構成タスク|Description|  
|----------------------|---------------|  
|サード パーティ製のウイルス対策ソフトウェアをインストールして、外部向けのノードの SQL Server PDW アプライアンス上で構成できます。<br /><br />(オプション)|詳細については、次を参照してください。[ウイルス対策ソフトウェア &#40;です。Analytics Platform System &#41;](antivirus-software.md).|  
|DSRM のパスワードを変更できます。<br /><br />(オプション)|詳細については、次を参照してください[ディレクトリ サービス復元モード (&) #40 です。 DSRM &#41; &#40; 内の AD のノードにログオンするための管理者パスワードの設定。Analytics Platform System &#41;](set-admin-password-for-logging-on-to-ad-nodes-in-directory-services-restore-mode.md).|  
|ソフトウェア更新プログラムを受信するアプライアンスを構成します。<br /><br />(推奨)|アプライアンスは、SQL Server PDW および基になるソフトウェアの更新プログラムを受信するように構成する必要があります。<br /><br />詳細については、次を参照してください。 [Windows Server Update Services の構成 &#40;です。WSUS&#41;&#40;です。Analytics Platform System &#41;](configure-windows-server-update-services-wsus.md). WSUS については、次を参照してください。[ソフトウェア サービス (&) #40 です。Analytics Platform System &#41;](software-servicing.md).|  
|Hadoop または Azure blob ストレージなどの外部のデータへの接続を構成します。<br /><br />(オプション)|詳細については、次を参照してください[外部データ &#40; への PolyBase 接続を構成する。Analytics Platform System &#41;](configure-polybase-connectivity-to-external-data.md).|  
|ウイルス対策ソフトウェアを構成します。<br /><br />(オプション)|サード パーティ製のウイルス対策ソリューションでは、外部に公開されたノードを保護に使用できますが、必須ではありません。 」のガイドラインに従います。|  
|バックアップおよびサーバーの読み込みの InfiniBand ネットワーク アダプターを構成します。<br /><br />(オプション)|InfiniBand ネットワークを使用して SQL Server PDW に接続するバックアップおよびサーバーに負荷を構成するのには、アプライアンス、現在アクティブな InfiniBand ネットワークに InfiniBand 接続を解決するのには DNS を許可するネットワーク アダプターを構成する必要があります。|  
|製品利用統計情報をマイクロソフトに送信するように構成します。<br /><br />(オプション)|遠隔測定データを Microsoft に送信する分析プラットフォーム システムを構成するのには、[管理] ノードで PowerShell スクリプトを実行する必要があります。 具体的な手順については、次を参照してください[Microsoft &#40; をの製品利用統計情報フィードバックの送信。SQL Server PDW &#41;](send-telemetry-feedback-to-microsoft-sql-server-pdw.md).|  
  
## <a name="see-also"></a>参照  
[ウイルス対策ソフトウェア &#40;です。Analytics Platform System &#41;](antivirus-software.md)  
[InfiniBand ネットワーク アダプター &#40; を構成します。SQL Server PDW &#41;](configure-infiniband-network-adapters.md)  
  
