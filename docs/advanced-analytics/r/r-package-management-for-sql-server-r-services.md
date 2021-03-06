---
title: "SQL Server の R パッケージの管理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/09/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: R
ms.assetid: 98c14b05-750e-44f9-8531-1298bf51e8d2
caps.latest.revision: "7"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 2b421ea34185f483bac0b9f3bd2527d68428bf50
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2017
---
# <a name="r-package-management-for-sql-server"></a>SQL Server の R パッケージの管理

この記事では、SQL Server 2017 と SQL Server 2016 での R パッケージを管理するための機能について説明します。

+ 2016 と 2017 年 1 の間で R パッケージのインストール方法の変更
+ R パッケージを管理するための推奨事項
+ SQL Server 2017 でパッケージの管理のため、新しいデータベース ロール
+ SQL Server 2017 でパッケージの管理のための新しい T-SQL ステートメント

**適用されます:** SQL Server 2016 の R Services、SQL Server 2017 機械学習のサービス

## <a name="differences-in-package-management-between-sql-server-2016-and-sql-server-2017"></a>SQL Server 2016 および SQL Server 2017 パッケージの管理での違い

**SQL Server 2017**、インスタンス レベルでは、パッケージの管理を有効にし、データベース レベルでのパッケージを追加するユーザーのアクセス許可を管理できます。

これは、データベース管理者が必要なデータベース オブジェクトを作成するスクリプトを実行して、パッケージの管理機能を有効にする必要があります。 詳細については、次を参照してください。 [R パッケージの管理を有効にする方法](r-package-how-to-enable-or-disable.md)です。

**SQL Server 2016**管理者は、インスタンスに関連付けられた R ライブラリで R パッケージをインストールする必要があります。 インスタンスで R コードを実行しているすべてのユーザーは、これらのパッケージを使用します。 SQL server で実行されている R コードでは、ユーザーのライブラリでインストールされているパッケージを使用できません。 ただし、管理者を許可できます個々 のユーザーを特定のデータベース内の R スクリプトを実行する機能。

**利点との違いの概要**

+ SQL Server 2017 で Machine Learning のサービスを使用している場合は、管理および新しいデータベース ロールと T-SQL ステートメントを使用して R ツールに基づく従来の方法のいずれかを使用して R パッケージをインストールできます。

+ 後者の方法では、管理者の詳細に制御を提供するためと組み合わせるとユーザーの自由度が高くすることをお勧めします。 たとえば、ユーザー パッケージをインストールできます独自、ストアド プロシージャを使用するか、または R コード、および他のユーザーと共有のパッケージを使用します。 

    パッケージは、データベースにスコープすることができます、各ユーザー分離のパッケージのサンド ボックスを取得するため、別のバージョンの同じ R パッケージをインストールする簡単です。 コピーまたは、データベース間でユーザーと、パッケージを移動することができますも簡単にします。 

+ SQL server パッケージ管理機能の使用によってバックアップおよび復元操作、簡単にします。 作業データベースを新しいサーバーに移行するときに、すべてのパッケージの一覧を読み取るし、新しいサーバー上のデータベースにインストールを行うパッケージ同期関数を使用できます。

+ Machine learning のジョブのサーバーを使用する場合は、従来の R ツールを使用して、コンピューターの管理者として R パッケージをインストールする方が便利あります。

+ SQL Server 2016 の R Services を使用している場合は、R ツールを使用して、インスタンスで使用される R パッケージのインストールを続行する必要があります > のインスタンスに関連付けられた R ライブラリを使用してください。

次のセクションでは、パッケージの管理の方法についての詳細を提供するこれら 2 つのオプションを使用して実行します。

## <a name="r-package-management-using-t-sql"></a>T-SQL を使用して R パッケージの管理

SQL Server 2017 には、DBA は、データベース レベルでの R パッケージより詳細に制御を提供する新しい T-SQL ステートメントが含まれています。 同時に、DBA は、ユーザーができるよう必要があるあり、他のユーザーと共有するパッケージをインストールする機能。

パッケージを他のユーザーと共有する必要があります。 または、パッケージの管理を有効にすることをお勧め複数のユーザーは、サーバーで machine learning のジョブを実行する必要がある場合、データベース ロールにユーザーの割り当てし、ユーザーが共有できるようにパッケージをアップロードします。

SQL Server 2017 でパッケージの管理は、これらの新しいデータベース オブジェクトと機能に依存します。

+ パッケージのアクセスと使用を管理するための新しいデータベース ロール
+ 別の共有とプライベートのパッケージのパッケージのスコープ
+ サーバーに新しいコード ライブラリをアップロードするための外部ライブラリの作成ステートメント
+ SQL Server で、パッケージのインストールをサポートするために、RevoScaleR に新しい R 関数の計算コンテキスト
+ パッケージの簡単なバックアップと復元を確認するため、パッケージ同期

### <a name="database-roles-for-package-management"></a>パッケージ管理のデータベース ロール

データベース管理者は、パッケージの管理を実行して、スクリプトの説明に従ってここで使用されるロールを作成する必要があります:[を有効にするか、パッケージの管理を無効にする](r-package-how-to-enable-or-disable.md)です。

このスクリプトを実行した後は、次の新しいデータベース ロールが表示されます。

+ `rpkgs-users`: このロールのメンバー パッケージを使用して、共有別にインストールされた`rpkgs-shared`ロールのメンバーです。

+ `rpkgs-private`: このロールのメンバーのメンバーと同じ権限での共有パッケージへのアクセスがある、`rpkgs-users`ロール。 このロールのメンバーことができますもインストール、削除、およびスコープを持つ個別のパッケージを使用します。

+ `rpkgs-shared`: このロールのメンバーのメンバーと同じアクセス許可がある、`rpkgs-private`ロール。 さらに、このロールのメンバーは、インストールまたは共有のパッケージを削除します。

+ `db_owner`: このロールのメンバーのメンバーと同じアクセス許可がある、`rpkgs-shared`ロール。 さらに、このロールのメンバーが**付与**他のユーザーが、インストール、または両方を削除する権利を共有およびプライベート パッケージです。

DBA は、パッケージをインストールするためのユーザーの権限を制御する、データベースごとにロールにユーザーを追加します。

### <a name="package-scope"></a>パッケージのスコープ

新しいパッケージ管理機能は、これらは、プライベート、または複数のユーザーで共有できるかどうかによってパッケージを区別します。

+ **共有スコープ**

    *共有範囲*意味共有スコープのロールの権限が与えられているユーザー (`rpkgs-shared`) インストールして、指定したデータベースへのパッケージをアンインストールします。 共有スコープ ライブラリにインストールされたパッケージは、インストールされた R パッケージの使用を許可されたユーザーであれば、SQL Server 上のデータベースの他のユーザーが使用できます。

+ **プライベート スコープ**

    *プライベート スコープ*意味プライベート スコープのロールのメンバーシップが与えられたユーザー (`rpkgs-private`) インストールしたり、ユーザーごとに定義されたプライベートなライブラリの場所にパッケージをアンインストールします。 そのため、プライベート スコープにインストールされているすべてのパッケージは、そのパッケージをインストールしたユーザーのみが使用できます。 言い換えると、SQL Server 上のユーザーは、他のユーザーがインストールしたプライベート パッケージを使用できません。

SQL Server 上のパッケージの展開と管理のために、 *共有* スコープと *プライベート* スコープのモデルを組み合わせてカスタムのセキュア システムを開発できます。

たとえば、共有スコープを使用して、データ サイエンティストのグループのリーダーやマネージャーにパッケージをインストールするアクセス許可を付与し、同じ SQL Server インスタンスの他のすべてのユーザーまたはデータ サイエンティストがそれらのパッケージを使用することができます。

また、ユーザー間をさらに厳格に分離するシナリオや、複数のバージョンのパッケージを使用するシナリオがあります。 この場合、プライベート スコープを使用して、個別のアクセス許可をデータ サイエンティストに付与し、必要なパッケージについてのみインストールと使用を許可することができます。 パッケージはユーザーごとにインストールされるため、1 人のユーザーがインストールしたパッケージは、同じ SQL Server データベースを使用する他のユーザーの作業に影響はありません。

### <a name="create-external-library"></a>外部ライブラリを作成します。

[外部ライブラリの作成](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)データベース管理者がユーザーの R ツールをしなくてもパッケージを操作に役立つ SQL Server 2017 に導入された新しい T-SQL ステートメントです。 

使用する、**外部ライブラリの作成**zip 形式のファイル形式でインスタンス外部のライブラリにアップロードするステートメント。 承認されたユーザー、ライブラリにアクセスし、自分で使用するためをインストールします。

たとえば、R プロジェクトごとに異なるバージョンの複数のコピーを作成できます。 別個のライブラリとしてアップロードするには、いくつかのバージョンをプライベートに保持し、いくつかのバージョンを他のユーザーと共有することができます。

"Library"は、基本的に、1 つの名前のユーザーを使用できるようにする外部のパッケージのコレクションです。 たとえば、外部ライブラリとして SQL Server に、次のいずれかを公開する可能性があります。

+ 依存関係のないと、作成した 1 つの R パッケージ
+ をインストールするパッケージとインストールに必要な依存関係
+ 特定のタスクまたはその依存関係と、プロジェクトに関連する R パッケージのコレクション

ライブラリの名前は、パッケージまたは SQL Server でパッケージのコレクションを管理するためと、インストールされているパッケージから独立していることができます。 ただし、ライブラリ名は、インスタンス間で一意である必要があります。

このステートメントを使用するには、パッケージ管理機能をインスタンスで有効にする必要があります。 詳細については、次を参照してください。[外部ライブラリの作成](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)です。

> [!NOTE]
> 現在このステートメントを使用して、r です。 サポートが将来的に Python パッケージと、Linux などの他のプラットフォームで実行されるパッケージで計画的なだけの Windows ベースのライブラリを作成することができます。

外部のライブラリは、サーバーにアップロードされている、インスタンスに関連付けられた R パッケージのライブラリをインストールする必要があります。 これにはこれを行ういくつかの方法があります。

+ 標準的な R コマンドを実行`install.packages`sp_execute_external_script 内です。 パッケージをインストールするアクセス許可を持つアカウントを使用して接続をしてください。

+ リモート R クライアントから SQL Server に接続し、実行[rxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages) SQL Server のコンピューティング コンテキストでします。 もう一度、アクセス許可が必要パッケージのインストールにこれを行うプライベートまたは共有のスコープのいずれか。

R と T-SQL の両方を使用してインストール例を参照してください[SQL Server の他のパッケージをインストール](install-additional-r-packages-on-sql-server.md)です。

### <a name="new-r-functions-for-package-installation"></a>パッケージのインストール用の新しい R 関数

ユーザーがの新しい関数を使用してもパッケージの管理用のデータベース ロールを有効にすると、 [ **RevoScaleR** ](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)パッケージを SQL Server のコンピューティング コンテキストとして指定されたインスタンスにインストールします。

+ データ サイエンティストは、SQL Server コンピューターに直接アクセスしなくても、SQL Server に必要な R パッケージをインストールできます。

+ ユーザーは、パッケージをインストールし、共有スコープを持つパッケージをインストールすることによって、他のユーザーと共有できます。 同じ SQL Server データベースの権限のある他のユーザーは、パッケージにアクセスできます。

+ ユーザーは、プライベート sandbox R パッケージを作成、他のユーザーに表示されていないプライベート パッケージをインストールできます。

次のパッケージ管理機能は、指定された計算コンテキストでパッケージのインストールと削除のための RevoScaleR で提供されます。

-   [rxInstalledPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxinstalledpackages): 指定された計算コンテキストでインストールされているパッケージに関する情報を確認します。

-   [rxInstallPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxinstallpackages): パッケージの zip 形式を指定したリポジトリから、またはローカルに保存されたを読み取ることにより、コンピューティング コンテキストにパッケージをインストールします。

-   [rxRemovePackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxremovepackages): インストール済みパッケージのコンピューティング コンテキストから削除します。

-   [rxFindPackage](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxfindpackage): 指定された計算コンテキストで 1 つまたは複数のパッケージのパスを取得します。

-   [rxSyncPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsyncpackages): 指定された計算のコンテキストで、ファイル システムおよびデータベース間でパッケージのライブラリにコピーします。

-   [rxSqlLibPaths](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqllibpaths): SQL Server 内で実行中にパッケージのライブラリ ツリーの検索パスを取得します。

これらの関数を使用するには、必要なアクセス許可のある、SQL Server のコンピューティング コンテキストを使用して SQL Server のインスタンスに接続します。 接続するときに、資格情報は、サーバーで、操作を完了できるかどうかを決定します。

パッケージのインストール関数では、依存関係を確認し、ローカル計算コンテキストでの R パッケージのインストールなど、関連するパッケージを SQL Server にインストールできることを確認します。 パッケージをアンインストールする関数では、依存関係を計算し、SQL Server の他のパッケージで使用されなくなったパッケージが削除されていることを確認し、リソースを解放します。

> [!NOTE]
> 
> SQL Server 2017 で既定では、これらの新しい関数が含まれています。 Microsoft R Server では、Microsoft R Server 9.0.1 などの以降のバージョンを使用するインスタンスをアップグレードすることによってこれらの関数を取得する RevoScaleR のバージョンを更新することができます。
> 
> 詳細については、次を参照してください。[アップグレード プログラムを使用して SqlBindR.exe](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)です。

### <a name="synchronization-of-r-package-libraries"></a>R パッケージのライブラリの同期

SQL Server 2017 (および Microsoft R Server の 2017 年 4 月リリース) の CTP 2.0 リリースでは、新しい R 関数の*パッケージを同期する*です。

パッケージの同期では、データベース エンジンがパッケージを特定の所有者と、グループによって使用され、必要な場合、それらのパッケージをファイル システムに記述できますを追跡することを意味します。 これらのシナリオでは、パッケージの同期を使用できます。

+ SQL Server のインスタンス間で R パッケージを移動するには。
+ 特定のユーザー用のパッケージを再インストールするか、データベースを復元した後にグループ化する必要があります。

有効にして、この機能を使用する方法の詳細については、次を参照してください。 [for SQL Server の R パッケージ同期](package-install-uninstall-and-sync.md)です。

## <a name="r-package-management-using-traditional-r-tools"></a>従来の R ツールを使用して R パッケージの管理

インスタンス上の R パッケージを管理するための従来の方法をインストールして、R のツールとコマンドを使用してパッケージを一覧表示します。 

+ このオプションは、SQL Server 2016 の初期のリリースを使用している場合、唯一のオプションにすることがあります。  
+ R パッケージの唯一のユーザーは、し、サーバーに管理者としてアクセスしても、このオプションが便利な可能性があります。
+ R パッケージのバージョンの管理を容易にするを使用することができます[miniCRAN](create-a-local-package-repository-using-minicran.md)をローカル リポジトリを作成し、インスタンス間で共有します。

詳細については、次の記事を参照してください。

+ [SQL Server に追加の R パッケージをインストールします。](install-additional-r-packages-on-sql-server.md)
+ [SQL Server にインストールされているパッケージの確認](determine-which-packages-are-installed-on-sql-server.md)

SQL Server の 2017 のことをお勧め外部ライブラリの作成に使用することをユーザーと、R パッケージを管理するデータベース ロールを提供します。

## <a name="next-steps"></a>次の手順

[有効にするにまたは R パッケージの管理を無効にする方法](../r/r-package-how-to-enable-or-disable.md)
