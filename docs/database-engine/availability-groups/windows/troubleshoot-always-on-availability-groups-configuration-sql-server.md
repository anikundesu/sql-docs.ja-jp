---
title: "Always On 可用性グループの構成のトラブルシューティング (SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: availability-groups
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting [SQL Server], deploying
- Availability Groups [SQL Server], troubleshooting
- Availability Groups [SQL Server], configuring
ms.assetid: 8c222f98-7392-4faf-b7ad-5fb60ffa237e
caps.latest.revision: "39"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 51429ad63e04893c26a6bf9213809060780aebba
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="troubleshoot-always-on-availability-groups-configuration-sql-server"></a>Always On 可用性グループの構成のトラブルシューティング (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  このトピックでは、サーバー インスタンスでの [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]の構成に関する一般的な問題のトラブルシューティングに役立つ情報を提供します。 構成に関する一般的な問題には、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] が無効になっている、アカウントが適切に構成されていない、データベース ミラーリング エンドポイントが存在しない、エンドポイントにアクセスできない (SQL Server エラー 1418)、ネットワーク アクセスが存在しない、データベース参加コマンドが失敗する (SQL Server エラー 35250) などがあります。  
  
> [!NOTE]  
>  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] の前提条件を満たしていることを確認してください。 詳細については、「 [Always On 可用性グループの前提条件、制限事項、および推奨事項 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md)の構成に関する一般的な問題のトラブルシューティングに役立つ情報を提供します。  
  
 **このトピックの内容**  
  
|セクション|説明|  
|-------------|-----------------|  
|[Always On 可用性グループが有効になっていない](#IsHadrEnabled)|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスで [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]が有効になっていない場合、そのインスタンスでは可用性グループの作成がサポートされず、可用性レプリカをホストできません。|  
|[Accounts](#Accounts)|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を実行しているアカウントを適切に構成するための要件について説明します。|  
|[エンドポイント](#Endpoints)|サーバー インスタンスのデータベース ミラーリング エンドポイントに関する問題の診断方法について説明します。|  
|[システム名](#SystemName)|エンドポイントの URL でサーバー インスタンスのシステム名を指定するためのその他の方法について概要を説明します。|  
|[ネットワーク アクセス](#NetworkAccess)|可用性レプリカをホストしている各サーバー インスタンスが TCP で他の各サーバー インスタンスのポートにアクセスできる必要があるという要件について説明します。|  
|[エンドポイント アクセス (SQLServer エラー 1418)](#Msg1418)|この [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エラー メッセージに関する情報が含まれます。|  
|[データベースの参加の失敗 (SQL Server エラー 35250)](#JoinDbFails)|プライマリ レプリカへの接続がアクティブでないためにセカンダリ データベースを可用性グループに参加させることができない問題について、考え得る原因と解決策について説明します。|  
|[読み取り専用ルーティングが正常に動作しない](#ROR)||  
|[関連タスク](#RelatedTasks)|[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] オンライン ブックの中の、可用性グループ構成のトラブルシューティングに特に関連するタスク指向のトピックの一覧が含まれます。|  
|[関連コンテンツ](#RelatedContent)|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オンライン ブックの外部にある関連したリソースの一覧が含まれます。|  
  
##  <a name="IsHadrEnabled"></a> Always On 可用性グループが有効になっていない  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 機能は、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]の各インスタンスで有効になっている必要があります。 詳細については、「[Always On 可用性グループの有効化と無効化 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)」を参照してください。  
  
##  <a name="Accounts"></a> Accounts  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の実行に使用するアカウントは、正しく構成されている必要があります。  
  
1.  アカウントに適切な権限が与えられていることを確認します。  
  
    1.  パートナーを同じドメイン ユーザー アカウントで実行している場合は、両方の **master** データベースに正しいユーザー ログインが自動的に存在します。 この場合は、データベースのセキュリティ構成が単純になるため、望ましいといえます。  
  
    2.  2 つのサーバー インスタンスが別々のアカウントで実行されている場合、リモート サーバー インスタンスの **master** にそれぞれのアカウントのログインを作成する必要があります。また、そのログインには、対応するサーバー インスタンスのデータベース ミラーリング エンドポイントに接続するための CONNECT 権限を付与する必要があります。 詳細については、「[データベース ミラーリングまたは Always On 可用性グループのログイン アカウントの設定 &#40;SQL Server&#41;](../../../database-engine/database-mirroring/set-up-login-accounts-database-mirroring-always-on-availability.md)」を参照してください。  
  
2.  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] がビルトイン アカウント (Local System、Local Service、Network Service など) で実行されている場合または非ドメイン アカウントで実行されている場合は、エンドポイント認証に証明書を使用する必要があります。 サービス アカウントで同じドメインのドメイン アカウントを使用している場合は、すべてのレプリカの場所の各サービス アカウントに対して CONNECT アクセスを付与するか、証明書を使用できます。 詳細については、「[データベース ミラーリング エンドポイントでの証明書の使用 &#40;Transact-SQL&#41;](../../../database-engine/database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)」を参照してください。  
  
##  <a name="Endpoints"></a> エンドポイント  
 エンドポイントが正しく構成されている必要があります。  
  
1.  可用性レプリカ (各 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] レプリカの場所 *) をホストする*の各インスタンスにデータベース ミラーリング エンドポイントがあることを確認します。 データベース ミラーリング エンドポイントが特定のサーバー インスタンスに存在するかどうかを確認するには、[sys.database_mirroring_endpoints](../../../relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql.md) カタログ ビューを使用します。 詳細については、「[Windows 認証でのデータベース ミラーリング エンドポイントの作成 &#40;Transact-SQL&#41;](../../../database-engine/database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)」または「[データベース ミラーリング エンドポイントで発信接続に証明書を使用できるようにする &#40;Transact-SQL&#41;](../../../database-engine/database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)」を参照してください。  
  
2.  ポート番号が適切であることを確認します。  
  
     サーバー インスタンスのデータベース ミラーリング エンドポイントに現在関連付けられているポートを識別するには、次の [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを使用します。  
  
    ```  
    SELECT type_desc, port FROM sys.tcp_endpoints;  
    GO  
    ```  
  
3.  説明が困難な [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] のセットアップに関する問題については、各サーバー インスタンスを調査して、それぞれが正しいポートでリッスンしているかどうかを確認することをお勧めします。  
  
4.  エンドポイントが開始されていること (STATE = STARTED) を確認します。 各サーバー インスタンスで、次の [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを使用します。  
  
    ```  
    SELECT state_desc FROM sys.database_mirroring_endpoints  
    ```  
  
     **state_desc** 列の詳細については、「[sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql.md)」を参照してください。  
  
     エンドポイントを開始するには、次の [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを使用します。  
  
    ```  
    ALTER ENDPOINT Endpoint_Mirroring   
    STATE = STARTED   
    AS TCP (LISTENER_PORT = <port_number>)  
    FOR database_mirroring (ROLE = ALL);  
    GO  
    ```  
  
     詳細については、「[ALTER ENDPOINT &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-endpoint-transact-sql.md)」を参照してください。  
  
5.  他のサーバーからのログインに、CONNECT 権限があることを確認します。 あるエンドポイントに対して CONNECT 権限のあるユーザーを確認するには、各サーバー インスタンスで、次の [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを使用します。  
  
    ```  
    SELECT 'Metadata Check';  
    SELECT EP.name, SP.STATE,   
       CONVERT(nvarchar(38), suser_name(SP.grantor_principal_id))   
          AS GRANTOR,   
       SP.TYPE AS PERMISSION,  
       CONVERT(nvarchar(46),suser_name(SP.grantee_principal_id))   
          AS GRANTEE   
       FROM sys.server_permissions SP , sys.endpoints EP  
       WHERE SP.major_id = EP.endpoint_id  
       ORDER BY Permission,grantor, grantee;   
    GO  
  
    ```  
  
##  <a name="SystemName"></a> System Name  
 エンドポイントの URL におけるサーバー インスタンスのシステム名には、システムを明確に識別できる任意の名前を使用できます。 サーバー アドレスには、システム名 (システムが同じドメインに存在する場合)、完全修飾ドメイン名、または IP アドレス (可能であれば静的 IP アドレス) を使用できます。 完全修飾ドメイン名を使用すると動作が保証されます。 詳細については、「 [可用性レプリカを追加または変更する場合のエンドポイント URL の指定 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md)の構成に関する一般的な問題のトラブルシューティングに役立つ情報を提供します。  
  
##  <a name="NetworkAccess"></a> Network Access  
 可用性レプリカをホストしている各サーバー インスタンスは、TCP で他の各サーバー インスタンスのポートにアクセスできる必要があります。 これは、サーバー インスタンスが相互に信頼関係を持たない別のドメイン (信頼されていないドメイン) に存在する場合に特に重要になります。  
  
##  <a name="Msg1418"></a> エンドポイント アクセス (SQLServer エラー 1418)  
 この [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] メッセージは、エンドポイントの URL で指定されたサーバー ネットワーク アドレスに到達できないか、そのアドレスが存在しないことを意味し、ネットワーク アドレス名を確認してコマンドを再実行するように示しています。  
  
##  <a name="JoinDbFails"></a> データベースの参加の失敗 (SQL Server エラー 35250)  
 ここでは、プライマリ レプリカへの接続がアクティブでないためにセカンダリ データベースを可用性グループに参加させることができない問題について、考え得る原因と解決策について説明します。  
  
 **解決方法:**  
  
1.  ファイアウォールの設定を調べて、プライマリ レプリカをホストするサーバー インスタンスとセカンダリ レプリカをホストするサーバー インスタンス (既定ではポート 5022) の間でエンドポイント ポート通信が許可されているかどうかを確認します。  
  
2.  ネットワーク サービス アカウントにエンドポイントへの接続権限があるかどうかを確認します。  
  
##  <a name="ROR"></a> 読み取り専用ルーティングが正常に動作しない  
 次の構成値の設定を確認し、必要に応じて修正します。  
  
||項目|操作|コメント|リンク|  
|------|---------|------------|--------------|----------|  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|現在のプライマリ レプリカ|可用性グループ リスナーがオンラインであることを確認します。|**リスナーがオンラインになっているかどうかを確認するには:**<br /><br /> `SELECT * FROM sys.dm_tcp_listener_states;`<br /><br /> **オフラインのリスナーを再起動するには:**<br /><br /> `ALTER AVAILABILITY GROUP myAG RESTART LISTENER 'myAG_Listener';`|[sys.dm_tcp_listener_states &#40;Transact-SQL&#41;](../../../relational-databases/system-dynamic-management-views/sys-dm-tcp-listener-states-transact-sql.md)<br /><br /> [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-availability-group-transact-sql.md)|  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|現在のプライマリ レプリカ|READ_ONLY_ROUTING_LIST に、読み取り可能なセカンダリ レプリカをホストしているサーバー インスタンスだけが含まれていることを確認します。|**読み取り可能なセカンダリ レプリカを識別するには:** sys.availability_replicas  (**secondary_role_allow_connections_desc** 列)<br /><br /> **読み取り専用ルーティング リストを表示するには:** sys.availability_read_only_routing_lists<br /><br /> **読み取り専用ルーティング リストを変更するには:** ALTER AVAILABILITY GROUP|[sys.availability_replicas &#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/sys-availability-replicas-transact-sql.md)<br /><br /> [sys.availability_read_only_routing_lists &#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/sys-availability-read-only-routing-lists-transact-sql.md)<br /><br /> [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-availability-group-transact-sql.md)|  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|read_only_routing_list にあるすべてのレプリカ|READ_ONLY_ROUTING_URL ポートが Windows ファイアウォールでブロックされていないことを確認します。|—|[データベース エンジン アクセスを有効にするための Windows ファイアウォールを構成する](../../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)|  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|read_only_routing_list にあるすべてのレプリカ|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 構成マネージャーで次のことを確認します:<br /><br /> SQL Server のリモート接続が有効になっている。<br /><br /> TCP/IP が有効になっている。<br /><br /> IP アドレスが正しく構成されている。|—|[サーバー プロパティの表示または変更 &#40;SQL Server&#41;](../../../database-engine/configure-windows/view-or-change-server-properties-sql-server.md)<br /><br /> [特定の TCP ポートで受信待ちするようにサーバーを構成する方法 &#40;SQL Server 構成マネージャー&#41;](../../../database-engine/configure-windows/configure-a-server-to-listen-on-a-specific-tcp-port.md)|  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|read_only_routing_list にあるすべてのレプリカ|READ_ONLY_ROUTING_URL (TCP**://***system-address***:***port*) に正しい完全修飾ドメイン名 (FQDN) とポート番号が含まれていることを確認します。|—|[Always On の read_only_routing_url の計算](http://blogs.msdn.com/b/mattn/archive/2012/04/25/calculating-read-only-routing-url-for-Always%20On.aspx)<br /><br /> [sys.availability_replicas &#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/sys-availability-replicas-transact-sql.md)<br /><br /> [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-availability-group-transact-sql.md)|  
|![チェック ボックス](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|クライアント システム|クライアント ドライバーが読み取り専用のルーティングをサポートしていることを確認します。|—|[Always On クライアント接続 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/always-on-client-connectivity-sql-server.md)|  
  
##  <a name="RelatedTasks"></a> 関連タスク  
  
-   [可用性グループの作成と構成 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/creation-and-configuration-of-availability-groups-sql-server.md)  
  
-   [Windows 認証でのデータベース ミラーリング エンドポイントの作成 &#40;Transact-SQL&#41;](../../../database-engine/database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [可用性レプリカを追加または変更する場合のエンドポイント URL の指定 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [失敗したファイルの追加操作のトラブルシューティング &#40;Always On 可用性グループ&#41;](../../../database-engine/availability-groups/windows/troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
-   [可用性グループのデータベースのためのログインとジョブの管理 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/logins-and-jobs-for-availability-group-databases.md)  
  
-   [データベースを別のサーバー インスタンスで使用できるようにするときのメタデータの管理 &#40;SQL Server&#41;](../../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)  
  
##  <a name="RelatedContent"></a> 関連コンテンツ  
  
-   [フェールオーバー クラスターのイベントおよびログを表示する](http://technet.microsoft.com/library/cc772342\(WS.10\).aspx)  
  
-   [Get-ClusterLog フェールオーバー クラスター コマンドレット](http://technet.microsoft.com/library/ee461045.aspx)  
  
-   [SQL Server Always On チームのブログ: SQL Server Always On チームのオフィシャル ブログ](https://blogs.msdn.microsoft.com/sqlalwayson/)  
  
## <a name="see-also"></a>参照  
 [データベース ミラーリングと Always On 可用性グループのトランスポート セキュリティ &#40;SQL Server&#41;](../../../database-engine/database-mirroring/transport-security-database-mirroring-always-on-availability.md)   
 [クライアント ネットワーク構成](../../../database-engine/configure-windows/client-network-configuration.md)   
 [AlwaysOn 可用性グループの前提条件、制限事項、および推奨事項 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md)  
  
  
