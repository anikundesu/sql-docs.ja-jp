---
title: "データベース エンジンのアップグレード計画の策定およびテスト | Microsoft Docs"
ms.custom: 
ms.date: 07/20/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: install-windows
ms.reviewer: 
ms.suite: sql
ms.technology: server-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19c5b725-7400-4881-af8f-fd232ca28234
caps.latest.revision: "16"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.openlocfilehash: ef0de3c547ac843807bf9e8e906ea19fa1e3a5b5
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="plan-and-test-the-database-engine-upgrade-plan"></a>データベース エンジンのアップグレード計画の策定およびテスト
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] のアップグレードを成功させるには、どんな手法であろうと、適切な計画を立てる必要があります。  
  
## <a name="release-notes-and-known-upgrade-issues"></a>リリース ノートとアップグレードの既知の問題  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] をアップグレードする前に次を確認してください。

- [SQL Server 2017 リリース ノート](../../sql-server/sql-server-2017-release-notes.md) 
- [SQL Server 2016 リリース ノート](../../sql-server/sql-server-2016-release-notes.md) 
- [SQL Server データベース エンジンの旧バージョンとの互換性](../../database-engine/sql-server-database-engine-backward-compatibility.md)トピック。  
  
## <a name="pre-upgrade-planning-checklist"></a>アップグレード前の計画チェックリスト  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]をアップグレードする前に、次のチェックリストと関連するトピックを確認します。 これらのトピックは、アップグレードの方法に関係なく、すべてのアップグレードに適用され、ローリング アップグレード、新しいインストールのアップグレード、またはインプレース アップグレードの中から最適なアップグレード方法を決定するのに役立ちます。 たとえば、オペレーティング システムのアップグレード、SQL Server 2005 からのアップグレード、または SQL Server の 32 ビット バージョンからアップグレードの場合、インプレース アップグレードまたはローリング アップグレードは実行できない場合があります。 デシジョン ツリーについては、「 [Choose a Database Engine Upgrade Method](../../database-engine/install-windows/choose-a-database-engine-upgrade-method.md)」を参照してください。  
  
-   **ハードウェアとソフトウェアの要件:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をインストールするためのハードウェアおよびソフトウェア要件を確認してください。 これらの要件は、「[SQL Server のインストールに必要なハードウェアおよびソフトウェア](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)」に掲載されています。 アップグレードの計画サイクルの一環として、ハードウェアのアップグレード (ハードウェアが新しくなると、速度も速くなり、またプロセッサ数の不足またはデータベースとサーバーの統合が原因でライセンス処理が低下する場合があります) およびオペレーティング システムのアップグレードを検討する必要があります。 この種のハードウェアとソフトウェアの変更は、アップグレード方法の種類の選定に影響を与えます。  
  
-   **現在の環境:** 現在の環境を調査して、使用されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントと、実際の環境に接続されているクライアントを把握します。  
  
    -   **クライアント プロバイダー:** アップグレード中はクライアントごとにプロバイダーを更新する必要はありませんが、更新してもかまいません。 [!INCLUDE[sql14](../../includes/sssql14-md.md)] 以前からアップグレードする場合、次の [!INCLUDE[sql15](../../includes/sssql15-md.md)] 機能を使用するには、クライアントごとにプロバイダーの更新が必要です。プロバイダーの更新により次の追加機能が利用できるようになります。  
  
       -   [Always Encrypted &#40;データベース エンジン&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)  
  
       -   [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
       -   [可用性グループ リスナー、クライアント接続、およびアプリケーションのフェールオーバー &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md)  
  
       -   SSL セキュリティ更新プログラム  

   >[!NOTE]
   >上記のリストは [!INCLUDE[sscurrent](../../includes/sscurrent-md.md)] にも適用されます。
  
-   **サードパーティ コンポーネント:** 統合バックアップなどのサードパーティ製のコンポーネントの互換性を確認します。  
  
-   **ターゲット環境:** ターゲット環境がハードウェアとソフトウェアの要件を満たしていること、さらに元のシステム要件をサポートしていることを確認します。 たとえば、アップグレードでは、複数の SQL Server インスタンスを 1 つの新しい [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] インスタンスに統合すること、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 環境をプライベートまたはパブリック クラウドに対して仮想化することが必要な場合があります。  
  
-   **エディション:** アップグレードで必要な [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] の適切なエディションを決定し、アップグレードのための有効なアップグレード パスを決定します。 詳細については、「 [Supported Version and Edition Upgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)」をご覧ください。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のいずれかのエディションから別のエディションへアップグレードする前に、現在使用している機能がアップグレード先のエディションでサポートされているかどうかを確認します。  
  
    > [!NOTE]  
    >  以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise Edition から [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] をアップグレードする場合は、"Enterprise Edition: コアベースのライセンス" または "Enterprise Edition" を選択してください。 これらの Enterprise エディションは、ライセンス モードのみが異なります。 詳細については、「 [Compute Capacity Limits by Edition of SQL Server](../../sql-server/compute-capacity-limits-by-edition-of-sql-server.md)」を参照してください。  
  
-   **下位互換性:** [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] データベース エンジンの下位互換性に関するトピックを参照して、 [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] とアップグレード対象の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バージョンとの間の動作の違いについて確認します。 「 [SQL Server Database Engine Backward Compatibility](../../database-engine/sql-server-database-engine-backward-compatibility.md)」を参照してください。  
  
-   **アップグレード アドバイザー:**  アップグレード プロセスを妨げるおそれのある問題、または既存のスクリプトまたはアプリケーションを修正しなければならない可能性がある重大な変更については、 [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] を実行して診断を行うことができます。 [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] には、顧客が既存のシステムのアップグレード準備を行う際に役立つアップグレード アドバイザーの新しいバージョンが搭載されています。  このツールには、アップグレード完了後に、テーブルの拡張などの新機能を利用できるかどうかについて、既存のデータベースを調べる機能も含まれます。   
    [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)]アップグレード アドバイザー  [こちら](https://www.microsoft.com/en-us/download/details.aspx?id=48119)からダウンロードできます。  
  
-   **システム構成チェッカー:**  アップグレードを実際にスケジュールする前に、 [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] システム構成チェッカー (SCC) を実行して、SQL Server セットアップ プログラムでセットアップに支障をきたす問題が検出されていないか判定します。 詳細については、「 [Check Parameters for the System Configuration Checker](../../database-engine/install-windows/check-parameters-for-the-system-configuration-checker.md)」を参照してください。  
  
-   **メモリ最適化テーブルのアップグレード:** メモリ最適化テーブルを含む SQL Server 2014 データベース インスタンスを SQL Server 2016 にアップグレードする場合、アップグレード プロセスでは、メモリ最適化テーブルをディスク上の新しいフォーマットに変換するために余分な時間が必要となります (これらの手順が実行されている間、データベースはオフラインになります)。   所要時間は、メモリ最適化テーブルのサイズと、I/O サブシステムの速度によって異なります。 インプレース アップグレードと新規インストール アップグレードの場合は、3 種類のデータ操作が必要です (ローリング アップグレードでは手順 1 は不要、手順 2 と手順 3 は必要です)。  
  
    1.  古いディスク上のフォーマットを使用してデータベースの回復を実行する (これには、メモリ最適化テーブル内のすべてのデータを、ディスクからメモリに読み込み操作が含まれる)  
  
    2.  データを新しいディスク上のフォーマットでディスクにシリアル化する  
  
    3.  新しいフォーマットを使用してデータベースの回復を実行する (これには、メモリ最適化テーブル内のすべてのデータを、ディスクからメモリに読み込み操作が含まれる)  
  
     さらに、このプロセス中にディスク上に十分な空き領域がないと、回復は失敗します。 既存のデータベースを格納するのに十分な領域がディスク上に存在することに加えて、インプレース アップグレードを実行するとき、または SQL Server 2016 インスタンスに SQL Server 2014 データベースをアタッチするときは MEMORY_OPTIMIZED_DATA ファイル グループ内のコンテナーの現在のサイズと同じ容量のストレージが別途存在することを確認します。次のクエリを使用すると、MEMORY_OPTIMIZED_DATA ファイル グループ用に現在必要なディスク領域と、アップグレードが成功するために必要なディスクの空き領域を確認できます。  
  
    ```  
    select cast(sum(size) as float)*8/1024/1024 'size in GB'   
    from sys.database_files  
    where data_space_id in (select data_space_id from sys.filegroups where type=N'FX')  
    ```  
  
## <a name="develop-and-test-the-upgrade-plan"></a>アップグレード計画の作成とテスト  
 最良の手法は、IT プロジェクトの場合と同様に、アップグレードを処理することです。 アップグレードを行う上で必要なスキル (データベース管理、ネットワーク、抽出、変換、読み込み (ETL) など) を備えたアップグレード チームを編成してください。 チームは次のことを行う必要があります。  
  
-   **アップグレード方法を選択する:** 「 [データベース エンジンのアップグレード方法の選択](../../database-engine/install-windows/choose-a-database-engine-upgrade-method.md)」を参照してください。  
  
-   **ロールバック計画を作成する:** ロールバックする必要がある場合、この計画を実行すると、元の環境を復元できます。  
  
-   **受け入れ基準を決定する:** アップグレードが正常に完了したことを把握した上で、ユーザーをアップグレードされた環境にカットオーバーします。  
  
-   **アップグレード計画をテストする:** 実際のワークロードを使用してパフォーマンスをテストするには、Microsoft SQL Server 分散再生ユーティリティを使用します。 このユーティリティでは、複数のコンピューターを使用してトレース データを再生し、ミッションクリティカルなワークロードをシミュレートできます。 SQL Server のアップグレードの前後でテスト サーバーの再生を実行することで、パフォーマンスの差を測定したり、アップグレード時にアプリケーションに非互換性が発生するかどうかを調べたりすることができます。 詳細については、「[SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md)」と「[管理ツール コマンド ライン オプション &#40;Distributed Replay Utility&#41;](../../tools/distributed-replay/administration-tool-command-line-options-distributed-replay-utility.md)」を参照してください。  
  
## <a name="next-steps"></a>次の手順  
 [データベース エンジンのアップグレード](../../database-engine/install-windows/upgrade-database-engine.md)  
  
  
