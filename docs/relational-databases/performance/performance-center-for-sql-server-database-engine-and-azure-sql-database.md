---
title: "SQL Server データベース エンジンと Azure SQL Database のパフォーマンス センター | Microsoft Docs"
ms.custom: 
ms.date: 04/08/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.reviewer: 
ms.service: 
ms.component: performance
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Performance (SQL Server)
- Performance (SQL Database)
helpviewer_keywords:
- SQL Server, performance
- performance (SQL Server)
- database performance (SQL Server)
- SQL Database (Performance)
- performance (SQL Database)
- database performance (SQL Database)
ms.assetid: 301204b2-140d-4495-98ed-021a9b5025f5
caps.latest.revision: "14"
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 0b635fc2b91f8ad068b2c44d0926824b9676aad0
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="performance-center-for-sql-server-database-engine-and-azure-sql-database"></a>SQL Server データベース エンジンと Azure SQL Database のパフォーマンス センター
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] このページでは、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] および [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)] でのパフォーマンスに関して必要になる情報の検索に役立つリンクを示します。  
  
 **凡例**  
  
 ![security-center-legend](../../relational-databases/performance/media/security-center-legend.PNG "security-center-legend")  
  
## <a name="this-is-a-work-in-process-does-this-performance-center-help-you-how-can-we-improve-it"></a>まだ開発中です。 このパフォーマンス センターはお役に立ちますか。 どうすればもっとよくなりますか。  
 どのような情報をお探しでしたか? お探しの情報は見つかりましたか? 何が抜けていますか。 どのような情報を見たいですか。 コンテンツ改善のため、フィードバックをお待ちしています。 [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Temporal%20Tables%20page) にコメントをお送りください  
  
## <a name="configuration-options-for-performance"></a>パフォーマンスの構成オプション  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] レベルのさまざまな構成オプションを使用してデータベース エンジンのパフォーマンスを制御できます。 [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)]、これらの最適化のすべてではありませんがほとんどが自動的に行われます。  
  
|||  
|-|-|  
|**ディスク構成オプション**|-   ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [ディスクのストライピングと RAID](https://technet.microsoft.com/library/ms190764\(v=sql.105\).aspx)|  
|**データとログ ファイルの構成オプション**|-   ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [別々のドライブへのデータ ファイルとログ ファイルの配置](../../relational-databases/policy-based-management/place-data-and-log-files-on-separate-drives.md)<br />-   ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [データ ファイルとログ ファイルの既定の場所の表示または変更 &#40;SQL Server Management Studio&#41;](../../database-engine/configure-windows/view-or-change-the-default-locations-for-data-and-log-files.md)|  
|**TempDB の構成オプション**|-   ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [TempDB でのパフォーマンスの強化](https://msdn.microsoft.com/library/ms190768.aspx#Anchor_1)<br />-   ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [データベース エンジンの構成 - TempDB](http://msdn.microsoft.com/library/7aabd304-f3c9-4c2d-bf9d-5479ee2498da)<br />-   ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [SQL Server TempDB およびバッファー プール拡張域を格納するための Azure VM での SSD の使用](http://blogs.technet.com/b/dataplatforminsider/archive/2014/09/25/using-ssds-in-azure-vms-to-store-sql-server-tempdb-and-buffer-pool-extensions.aspx)<br />-   ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [Azure Virtual Machines での SQL Server 用一時ディスクに関するディスクとパフォーマンスのベスト プラクティス](https://azure.microsoft.com/documentation/articles/virtual-machines-sql-server-performance-best-practices/)|  
|![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") **サーバー構成オプション**|<ul><li>**プロセッサ構成オプション**<br /><br /> <ul><li>![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [affinity mask サーバー構成オプション](../../database-engine/configure-windows/affinity-mask-server-configuration-option.md)</li><li>![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [affinity Input-Output mask サーバー構成オプション](../../database-engine/configure-windows/affinity-input-output-mask-server-configuration-option.md)</li><li>![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [affinity64 mask サーバー構成オプション](../../database-engine/configure-windows/affinity64-mask-server-configuration-option.md)</li><li>![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [affinity64 Input-Output mask サーバー構成オプション](../../database-engine/configure-windows/affinity64-input-output-mask-server-configuration-option.md)</li><li>![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [max worker threads サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-max-worker-threads-server-configuration-option.md)</li></ul></li><li>**メモリ構成オプション**<br /><br /> <ul><li>![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [サーバー メモリに関するサーバー構成オプション](../../database-engine/configure-windows/server-memory-server-configuration-options.md)</li></ul></li><li>**インデックス構成オプション**<br /><br /> <ul><li>![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [fill factor サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-fill-factor-server-configuration-option.md)</li><li></li></ul></li><li>**クエリ構成オプション**<br /><br /> <ul><li>![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [min memory per query サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-min-memory-per-query-server-configuration-option.md)</li><li>![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [query governor cost limit サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-query-governor-cost-limit-server-configuration-option.md)</li><li>![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [max degree of parallelism サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)</li><li>![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [cost threshold for parallelism サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-cost-threshold-for-parallelism-server-configuration-option.md)</li><li>![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [optimize for ad hoc workloads サーバー構成オプション](../../database-engine/configure-windows/optimize-for-ad-hoc-workloads-server-configuration-option.md)</li></ul></li><li>**バックアップ構成オプション**<br /><br /> <ul><li>![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [backup compression default サーバー構成オプションの表示または構成](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)</li></ul></li></ul>|  
|**データベース構成最適化オプション**|-   ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [データの圧縮](../../relational-databases/data-compression/data-compression.md)<br />-   ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") [データベースの互換性レベルの表示または変更](../../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md)<br />-   ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)|  
|**テーブル構成最適化**|-   ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [パーティション テーブルとパーティション インデックス](../../relational-databases/partitions/partitioned-tables-and-indexes.md)<br />-|  
|**Azure Virtual Machine でのデータベース エンジンのパフォーマンス**|-   ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [簡易チェック一覧](https://azure.microsoft.com/documentation/articles/virtual-machines-sql-server-performance-best-practices/)<br />-   ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [仮想マシンのサイズとストレージ アカウントに関する考慮事項](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-sql-server-performance-best-practices/)<br />-   ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [ディスクとパフォーマンスに関する考慮事項](https://azure.microsoft.com/documentation/articles/virtual-machines-sql-server-performance-best-practices/)<br />-   ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [I/O パフォーマンスに関する考慮事項](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-sql-server-performance-best-practices/)<br />-   ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [機能固有のパフォーマンスに関する考慮事項](https://azure.microsoft.com/documentation/articles/virtual-machines-sql-server-performance-best-practices/)|  
  
## <a name="query-performance-options"></a>クエリ パフォーマンス オプション  
  
|||  
|-|-|  
|![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both")  **[インデックス](../../relational-databases/indexes/indexes.md)**|-   [インデックスの再編成と再構築](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)<br />-   [インデックスの FILL FACTOR の指定](../../relational-databases/indexes/specify-fill-factor-for-an-index.md)<br />-   [並列インデックス操作の構成](../../relational-databases/indexes/configure-parallel-index-operations.md)<br />-   [インデックスの SORT_IN_TEMPDB オプション](../../relational-databases/indexes/sort-in-tempdb-option-for-indexes.md)<br />-   [フルテキスト インデックスのパフォーマンスの向上](../../relational-databases/search/improve-the-performance-of-full-text-indexes.md)|  
|![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both")  **[パーティション テーブルとパーティション インデックス](../../relational-databases/partitions/partitioned-tables-and-indexes.md)**|-   [パーティション分割の利点](https://msdn.microsoft.com/library/ms190787.aspx#Anchor_0)|  
|![security-center-both](../stored-procedures/stored-procedures-database-engine.md)|  
|![security-center-both](../user-defined-functions/user-defined-functions.md)|  
|![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") **並列処理の最適化**|-   [max worker threads サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-max-worker-threads-server-configuration-option.md)<br />-   [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)|  
|![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") **クエリ オプティマイザーの最適化**|-   [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)|  
|![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both")  **[統計](../../relational-databases/statistics/statistics.md)**|-   [統計を更新する場合](https://msdn.microsoft.com/library/ms190397.aspx#Anchor_3)<br />-   [統計の更新](../../relational-databases/statistics/update-statistics.md)|  
|![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both")  **[インメモリ OLTP &#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)**|-   [メモリ最適化テーブル](../../relational-databases/in-memory-oltp/memory-optimized-tables.md)<br />-   [ネイティブ コンパイル ストアド プロシージャ](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)<br />-   [ネイティブ コンパイル ストアド プロシージャからの TempDB 内のテーブルの作成およびアクセス](../../relational-databases/in-memory-oltp/create-and-access-tables-in-tempdb-from-stored-procedures.md)<br />-   [メモリ最適化されたハッシュ インデックスのパフォーマンスに関する一般的な問題のトラブルシューティング](http://msdn.microsoft.com/library/1954a997-7585-4713-81fd-76d429b8d095)<br />-   [実証: インメモリ OLTP によるパフォーマンスの向上](../../relational-databases/in-memory-oltp/demonstration-performance-improvement-of-in-memory-oltp.md)|  
  
## <a name="see-also"></a>参照  
 [パフォーマンスの監視とチューニング](../../relational-databases/performance/monitor-and-tune-for-performance.md)   
 [クエリのストアを使用した、パフォーマンスの監視](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [単一データベースの Azure SQL Database パフォーマンス ガイダンス](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/)   
 [エラスティック プールを使用した Azure SQL Database のパフォーマンスの最適化](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool-guidance/)   
 [Azure Query Performance Insight](https://azure.microsoft.com/documentation/articles/sql-database-query-performance/)  
  
  
