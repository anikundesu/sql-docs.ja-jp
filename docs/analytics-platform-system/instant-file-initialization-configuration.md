---
title: "ファイルの瞬時初期化構成 (Analytics Platform System)"
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
ms.assetid: 58be8982-4d2e-4aa3-bcdd-874a062d2f9d
caps.latest.revision: "20"
ms.openlocfilehash: b7dda4bb925e08f49409ea1950cfe3649b4db3e0
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="instant-file-initialization-configuration"></a>ファイルの瞬時初期化の構成
ファイルの瞬時初期化は、データ ファイルの操作をより迅速に実行を許可する SQL Server 機能です。 チェック ボックスをファイルの瞬時初期化を有効にすると、SQL Server PDW のパフォーマンスが向上します。 ただし、ビジネスのセキュリティ上のリスクを伴いますこの場合、オフのままにします。  
  
> [!IMPORTANT]  
> ファイルの瞬時初期化を有効にすると、SQL Server は削除されたビットをゼロで上書きされません。  この動作は、承認されていないユーザーが削除されたデータにアクセスした場合、セキュリティの脆弱性を作成可能性があります。 ただし、SQL Server のインスタンスに、SQL Server データベースとバックアップ ファイルが常に接続されていることを確認して、SQL Server PDW がこのリスクを軽減するSQL Server サービス アカウントのみおよびローカルの管理者は、SQL Server PDW では削除されたデータにアクセスできます。  
  
ファイルの瞬時初期化は、TDE が有効になっている場合は使用できません。  
  
## <a name="add-permission-for-the-backup-account"></a>バックアップのアカウントのアクセス許可を追加します。  
バックアップ プロセスでは、バックアップ記憶域の場所にアクセスできるネットワーク資格情報 (Windows ユーザー アカウント) が必要です。 使用してアカウントを使用する PDW を承認する、 [sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md)プロシージャです。 参照してください[データベースのバックアップ](../t-sql/statements/backup-database-parallel-data-warehouse.md)全体のバックアップ プロセスにします。 ファイルの瞬時初期化を使用するのには、バックアップするアカウントを付与する必要があります、`Perform volume maintenance tasks`権限です。  
  
1.  サーバーのバックアップで開く、**ローカル セキュリティ ポリシー**アプリケーション (`secpol.msc`)。  
  
2.  左側のペインで **[ローカル ポリシー]**を展開し、 **[ユーザー権利の割り当て]**をクリックします。  
  
3.  右側のペインで、 **[ボリュームの保守タスクを実行]**をダブルクリックします。  
  
4.  **[ユーザーまたはグループの追加]** をクリックし、バックアップに使用される任意のユーザー アカウントを追加します。  
  
5.  **[適用]**をクリックし、 **[ローカル セキュリティ ポリシー]** ダイアログ ボックスをすべて閉じます。  
  
## <a name="to-turn-instant-file-initialization-on-or-off"></a>ファイルの瞬時初期化を有効または無効にする  
  
1.  構成マネージャーを起動します。 詳細については、次を参照してください[構成マネージャー &#40; を起動。Analytics Platform System &#41;](launch-the-configuration-manager.md).  
  
2.  構成マネージャーの左側のウィンドウでをクリックして**ファイルの瞬時初期化**です。  
  
3.  ファイルの瞬時初期化を有効にする場合は、横に、ボックスを選択して**Enable Instant File Initialization すべてのノードで**です。 ファイルの瞬時初期化をオフにボックスをオフにします の横に**Enable Instant File Initialization すべてのノードで**です。  
  
    > [!WARNING]  
    > ファイルの瞬時初期化を無効にすると、機能の上で説明したセキュリティの考慮事項もファイルの瞬時初期化が有効化中に削除されたファイルに適用されます。  
  
4.  **[適用]**をクリックします。 変更は、アプライアンスのサービスが再起動したときに、SQL Server PDW では、SQL Server インスタンスを介して反映されます。 アプライアンスのサービスを今すぐ再起動するには、次を参照してください。 [PDW サービスの状態と #40 です。Analytics Platform System &#41;](pdw-services-status.md).  
  
5.  上記の手順を繰り返すことができます**バックアップ アカウントのアクセス許可の追加**を削除する、**ボリュームの保守タスクを実行**権限です。  
  
![DWConfig アプライアンス PDW の瞬時ファイル初期化](./media/instant-file-initialization-configuration/SQL_Server_PDW_DWConfig_ApplPDWInstant.png "SQL_Server_PDW_DWConfig_ApplPDWInstant")  
  
ファイルの瞬時初期化に関する詳細については、次を参照してください。[ファイルの瞬時初期化](http://technet.microsoft.com/en-us/library/ms175935(v=SQL.105).aspx)です。  
  
