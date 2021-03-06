---
title: "Red Hat Enterprise Linux に SQL Server 2017 の概要 |Microsoft ドキュメント"
description: "このクイック スタート チュートリアルでは、Red Hat Enterprise Linux に SQL Server 2017 をインストールし、作成し、sqlcmd によるデータベースのクエリを実行する方法を示します。"
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 92503f59-96dc-4f6a-b1b0-d135c43e935e
ms.workload: Active
ms.openlocfilehash: 42bcabc32c3a47c09bc8c3dd116403163faa2071
ms.sourcegitcommit: 085dd05d56afecbb454206ed8402cfbaa597cfbe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="install-sql-server-and-create-a-database-on-red-hat"></a>SQL Server をインストールし、Red Hat でデータベースを作成

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

このクイック スタート チュートリアルではまず Red Hat Enterprise Linux (RHEL) 7.3 以降に SQL Server 2017 をインストールします。その後 **sqlcmd** を使って接続し、 最初のデータベースを作成し、クエリを実行します。

> [!TIP]
> このチュートリアルでは、ユーザー入力と、インターネット接続が必要です。 [無人](sql-server-linux-setup.md#unattended)または[オフライン](sql-server-linux-setup.md#offline)インストール手順に興味のある場合、[Linux 上の SQL Server のインストールのガイダンス](sql-server-linux-setup.md)を参照してください。

## <a name="prerequisites"></a>前提条件

RHEL 7.3 または 7.4 マシンで**少なくとも 2 GB** のメモリが必要です。

自分のコンピューター上に Red Hat Enterprise Linux をインストールする場合は[http://access.redhat.com/products/red-hat-enterprise-linux/evaluation](http://access.redhat.com/products/red-hat-enterprise-linux/evaluation)を参照してください。 Azure で RHEL 仮想マシンを作成することもできます。 [Azure CLI を使用した Linux VM の作成と管理](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm)を参照し、`az vm create`を呼び出す際に`--image RHEL`を利用してください。

その他のシステム要件については、[SQL Server on Linux のシステム要件](sql-server-linux-setup.md#system)を参照してください。

## <a id="install"></a>SQL Server をインストールします。

RHEL で SQL Server を構成するためには、ターミナルで次のコマンドを実行して**mssql サーバー**パッケージをインストールします。

> [!IMPORTANT]
> 既に SQL Server 2017 の CTP または RC リリースをインストールしている場合は、GA リポジトリを登録する前に、古いリポジトリを削除する必要があります。 詳細については、「[プレビュー リポジトリからリポジトリを GA リポジトリに変更](sql-server-linux-change-repo.md)」を参照してください。

1. Microsoft SQL Server の Red Hat リポジトリの構成ファイルをダウンロードします。

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo
   ```

   > [!NOTE]
   > これは、累積的な更新プログラム (CU) リポジトリです。 リポジトリ オプションとそれらの相違点の詳細については、[ソース リポジトリを変更](sql-server-linux-setup.md#repositories)を参照してください。

1. SQL Server をインストールするには、次のコマンドを実行します。

   ```bash
   sudo yum install -y mssql-server
   ```

1. パッケージのインストールが完了した後、**mssql-conf setup** を実行し、プロンプトに従って SA パスワードを設定し、エディションを選択します。

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```
   > [!TIP]
   > このチュートリアルで SQL Server 2017 を試す場合、次のエディションのライセンスはフリーです: Evaluation、Developer、およびExpress。

   > [!NOTE]
   > SA アカウントのパスワードは十分に強力なもの(大文字と小文字のアルファベット、十進数の数字および／もしくは英数字以外の記号を含む、8文字以上の文字列)を指定するようにしてください。

1. 構成を完了したら、サービスが実行されていることを確認します。

   ```bash
   systemctl status mssql-server
   ```
   
1. リモート接続を許可するには、RHEL 上のファイアウォールで SQL Server のポートを開きます。 SQL Server の既定ポートは、TCP 1433 です。 ファイアウォールとして **FirewallD** を使用している場合、次のコマンドを使用することができます。

   ```bash
   sudo firewall-cmd --zone=public --add-port=1433/tcp --permanent
   sudo firewall-cmd --reload
   ```

この時点で、SQL Server はRHEL コンピューター上で実行されており、使用する準備ができました!

## <a id="tools"></a>SQL Server コマンド ライン ツールをインストールします。

データベースを作成するには、SQL Server で TRANSACT-SQL ステートメントを実行できるツールを使用して接続する必要があります。 次の手順で、SQL Server コマンド ライン ツール: [sqlcmd](../tools/sqlcmd-utility.md)と[bcp](../tools/bcp-utility.md) をインストールします。

1. Microsoft の Red Hat リポジトリの構成ファイルをダウンロードします。

   ```bash
   sudo curl -o /etc/yum.repos.d/msprod.repo https://packages.microsoft.com/config/rhel/7/prod.repo
   ```

1. インストールされている**mssql ツール**の以前のバージョンがあれば、古い unixODBC パッケージを削除します。

   ```bash
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel
   ```

1. 次のコマンドを実行して **mssql-tools** を unixODBC 開発者パッケージとともにインストールします。

   ```bash
   sudo yum install -y mssql-tools unixODBC-devel
   ```

1. 利便性のために、`/opt/mssql-tools/bin/`を**PATH**環境変数に追加します。 これにより完全なパスを指定せずにツールを実行することができます。 **PATH**環境変数をログイン セッションと対話型/ログイン以外のセッション両方で変更するには、次のコマンドを実行します。

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

> [!TIP]
> **Sqlcmd**はSQL Server に接続し、クエリを実行し、管理と開発タスクを実行するツールの 1 つにすぎません。 その他のツールの中には[SQL Server Management Studio](sql-server-linux-develop-use-ssms.md)や[Visual Studio Code](sql-server-linux-develop-use-vscode.md)が含まれています。

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
