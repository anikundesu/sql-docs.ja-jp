---
title: "PDW の証明書 (Analytics Platform System) のプロビジョニング"
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
ms.assetid: 0a423b7d-c6ea-45c1-80b0-26758170594c
caps.latest.revision: "22"
ms.openlocfilehash: 9abee9638492368fe407f98a81beea2a48148971
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="pdw-certificate-provisioning"></a>PDW 証明書のプロビジョニング
**PDW 証明書のプロビジョニング**Analytics Platform System のページ**Configuration Manager**をインポートまたは PDW 地域で使用される証明書を削除します。 使用して、接続の暗号化に証明書は SQL Server クライアント、SQL Server PDW ドライバーを使用するツールを使ってコントロール ノードをセキュリティで保護された通信を支援できます、[管理コンソール](monitor-the-appliance-by-using-the-admin-console.md)、Integration Services で読み込まれるとします。  
  
## <a name="prerequisites"></a>Prerequisites  
証明書をインストールする前に、次の操作を行います。  
  
1.  セキュリティで保護された証明書を取得します。 セキュリティで保護された証明書を取得する方法の詳細については、必要がある場合は、Microsoft サポートに問い合わせてください。  
  
2.  証明書をパスワードで保護された PFX ファイルでコントロールのノードに保存します。  
  
## <a name="for-security-reasons-obtain-a-trusted-certificate"></a>セキュリティ上の理由から、信頼された証明書を取得します  
SQL Server PDW は、コントロールのノードへの接続の暗号化に証明書の使用をサポートしています接続など、**管理コンソール**です。  
  
既定では、**管理コンソール**、お客様のプライバシーがいないサーバー認証を提供する自己署名証明書が含まれています。 通信が仲介の攻撃に対して脆弱にままことができます。 ユーザーは、自己署名証明書を使用して、管理コンソールに接続するとき、Internet Explorer は、エラーを返します。"この web サイトのセキュリティ証明書に問題がある"です。  
  
自己署名証明書を使用して接続は、クライアントとサーバー間のインフライトのデータを暗号化、接続が攻撃者からリスクのままであります。  
  
> [!WARNING]  
> アプライアンスの管理者は、セキュリティで保護された接続があるし、Internet Explorer でレポートされるエラーを削除するために、クライアントによって認識される信頼された証明機関にチェーンされている証明書をすぐに取得する必要があります。  
  
証明書のパスは、コントロールのノード (推奨)、クラスター IP アドレスにマップされる完全修飾ドメイン名またはユーザーにアクセスする、ブラウザーのアドレス バーに入力する名前を含める必要があります、**管理コンソール**です。  
  
Analytics Platform System を使用して**Configuration Manager**を追加または信頼された証明書を削除します。 Microsoft Windows HTTP サービス証明書の構成ツールを使用して直接 (**winHttpCertCfg.exe**)、証明書の管理にはサポートされていません。  
  
## <a name="import-or-remove-the-certificate"></a>インポートまたは証明書を削除します。  
次の手順では、インポートまたはアプライアンス証明書を削除する方法を示しています。  
  
### <a name="to-import-the-certificate"></a>証明書をインポートするには  
  
1.  起動して、 **Configuration Manager**です。 詳細については、次を参照してください[構成マネージャー &#40; を起動。Analytics Platform System &#41;](launch-the-configuration-manager.md).  
  
2.  左側のウィンドウで、 **Configuration Manager**、展開**並列データ ウェアハウスのトポロジ**、クリックして**証明書**です。  
  
3.  選択**証明書をインポートし、それを使用するアプライアンスを構成**、順にクリック**参照**を参照し、証明書ファイルを選択します。  
  
4.  内の証明書のパスワードを入力、**パスワード**フィールドです。  
  
5.  をクリックして**適用**アプライアンスの証明書を構成します。  
  
SQL Server PDW では、インポートした証明書を使用して、現在の接続は暗号化されませんが、新しい接続に対して、証明書を使用します。  
  
### <a name="to-remove-the-previously-imported-certificate"></a>以前にインポートした証明書を削除するには  
  
1.  起動して、 **Configuration Manager**です。 詳細については、次を参照してください[構成マネージャー &#40; を起動。Analytics Platform System &#41;](launch-the-configuration-manager.md).  
  
2.  左側のウィンドウで、 **Configuration Manager**、展開**並列データ ウェアハウスのトポロジ**、クリックして**証明書**です。  
  
3.  選択**アプライアンスで提供された証明書を削除する**です。  
  
4.  をクリックして**適用**アプライアンスから以前にインポートした証明書を削除します。  
  
SQL Server PDW では、現在の接続の暗号化に続行されますが、新しい接続を削除した証明書を使用しません。  
  
![DWConfig アプライアンス PDW の証明書](./media/pdw-certificate-provisioning/SQL_Server_PDW_DWConfig_ApplPDWCert.png "SQL_Server_PDW_DWConfig_ApplPDWCert")  
  
## <a name="see-also"></a>参照  
[構成マネージャー &#40; を起動します。Analytics Platform System &#41;](launch-the-configuration-manager.md)  
<!-- MISSING LINKS [HDInsight Certificate Provisioning &#40;Analytics Platform System&#41;](hdinsight-certificate-provisioning.md)  -->  
  
