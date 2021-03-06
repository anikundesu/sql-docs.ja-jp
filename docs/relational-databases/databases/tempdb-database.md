---
title: "tempdb データベース | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: databases
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- temporary tables [SQL Server], tempdb database
- tempdb database [SQL Server], about tempdb
- temporary stored procedures [SQL Server]
- tempdb database [SQL Server]
ms.assetid: ce4053fb-e37a-4851-b711-8e504059a780
caps.latest.revision: "66"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.openlocfilehash: 6d71dcbda413d604c2c6ac2e4d85a815a4aa3719
ms.sourcegitcommit: ef1fa818beea435f58986af3379853dc28f5efd8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="tempdb-database"></a>tempdb データベース
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] **tempdb** システム データベースは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続しているすべてのユーザーが使用できるグローバル リソースであり、以下のものを保持するために使用されます。  
  
- グローバルまたはローカルな一時テーブルおよびインデックス、一時ストアド プロシージャ、テーブル変数、テーブル値関数で返されるテーブル、カーソルなど、明示的に作成された一時的な**ユーザー オブジェクト**。  
- [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] によって作成された **内部オブジェクト**。 たとえば、次のオブジェクトにアクセスできます。
  - スプール、カーソル、並べ替え、および一時的なラージ オブジェクト (LOB) 記憶域の中間結果を格納する作業テーブル。
  - ハッシュ結合操作またはハッシュ集計操作用の作業ファイル
  - インデックスの作成または再構築などの操作 (SORT_IN_TEMPDB を指定した場合) や、GROUP BY、ORDER BY、または UNION クエリにおける並べ替えの中間結果

  > [!NOTE]
  > 各内部オブジェクトでは、少なくとも 9 つのページが使用されます (1 つの IAM ページと 8 ページ分のエクステント)。 ページとエクステントの詳細については、「[ページとエクステント](../../relational-databases/pages-and-extents-architecture-guide.md#pages-and-extents)」を参照してください。

- **バージョン ストア**。これは行のバージョン管理を使用する機能のサポートに必要なデータ行を保持するデータ ページのコレクションです。 共通バージョン ストアとオンライン インデックス構築用のバージョン ストアの 2 つのバージョン ストアがあります。 バージョン ストアには、次の内容が保持されます。
  - 行のバージョン管理を伴う READ COMMITTED 分離トランザクションまたはスナップショット分離トランザクションを使用するデータベースで、データ変更トランザクションによって生成される行バージョン。  
  - オンライン インデックス操作、複数のアクティブな結果セット (MARS)、AFTER トリガーなどの機能に対してデータ変更トランザクションによって生成される行バージョン。  
  
**tempdb** 内の操作は、最低限必要な情報だけがログに記録されます。 これにより、トランザクションをロールバックできます。 **が起動されるたびに** tempdb [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が再作成され、システムが常にデータベースのクリーンなコピーで起動されるようにします。 一時テーブルと一時ストアド プロシージャは、切断時に自動的に削除され、システムのシャットダウン時にアクティブな接続はありません。 そのため、 **tempdb** には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のあるセッションから別のセッションに保存されるものは一切含まれません。 **tempdb**では、バックアップ操作と復元操作は実行できません。  
  
## <a name="physical-properties-of-tempdb"></a>tempdb の物理プロパティ  
 次の表は、**tempdb** のデータ ファイルとログ ファイルの初期構成値 (Model データベースの既定値に基づく) の一覧です。 これらのファイルのサイズは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のエディションによって多少異なる場合があります。  
  
|ファイル|論理名|物理名|初期サイズ|ファイル拡張|  
|----------|------------------|-------------------|------------------|-----------------|  
|プライマリ データ|tempdev|tempdb.mdf|8 MB|ディスクがいっぱいになるまで 64 MB ずつ自動拡張|  
|セカンダリ データ ファイル*|temp#|tempdb_mssql_#.ndf|8 MB|ディスクがいっぱいになるまで 64 MB ずつ自動拡張|  
|Log|templog|templog.ldf|8 MB|最大 2 TB まで 64 MB ずつ自動拡張|  
  
 \* コンピューター上の (論理) プロセッサの数に依存するファイル数です。 一般的なルールとして、論理プロセッサの数が 8 以下の場合、論理プロセッサと同じ数のデータ ファイルを使用します。 論理プロセッサの数が 8 より大きい場合、8 つのデータ ファイルを使用し、競合が続く場合、競合が許容できるレベルに減少するまでデータ ファイルの数を 4 の倍数分ずつ増やすか、ワークロード/コードを変更します。

> [!NOTE]
> データ ファイルの数の既定値は、 [KB 2154845](http://support.microsoft.com/kb/2154845/)の一般的なガイドラインに基づいています。  
  
### <a name="moving-the-tempdb-data-and-log-files"></a>tempdb のデータ ファイルとログ ファイルの移動  
 **tempdb** データ ファイルとログ ファイルを移動するには、「 [システム データベースの移動](../../relational-databases/databases/move-system-databases.md)」を参照してください。  
  
### <a name="database-options"></a>データベース オプション  
 **tempdb** データベースの各データベース オプションの既定値とそのオプションを変更できるかどうかを次の表に示します。 これらのオプションの現在の設定を表示するには、 [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) カタログ ビューを使用します。  
  
|データベース オプション|既定値|変更可否|  
|---------------------|-------------------|---------------------|  
|ALLOW_SNAPSHOT_ISOLATION|OFF|はい|  
|ANSI_NULL_DEFAULT|OFF|はい|  
|ANSI_NULLS|OFF|はい|  
|ANSI_PADDING|OFF|はい|  
|ANSI_WARNINGS|OFF|はい|  
|ARITHABORT|OFF|はい|  
|AUTO_CLOSE|OFF|いいえ|  
|AUTO_CREATE_STATISTICS|ON|はい|  
|AUTO_SHRINK|OFF|いいえ|  
|AUTO_UPDATE_STATISTICS|ON|はい|  
|AUTO_UPDATE_STATISTICS_ASYNC|OFF|はい|  
|CHANGE_TRACKING|OFF|いいえ|  
|CONCAT_NULL_YIELDS_NULL|OFF|はい|  
|CURSOR_CLOSE_ON_COMMIT|OFF|はい|  
|CURSOR_DEFAULT|GLOBAL|はい|  
|データベース可用性オプション|ONLINE<br /><br /> MULTI_USER<br /><br /> READ_WRITE|いいえ<br /><br /> いいえ<br /><br /> いいえ|  
|DATE_CORRELATION_OPTIMIZATION|OFF|はい|  
|DB_CHAINING|ON|いいえ|  
|ENCRYPTION|OFF|いいえ|  
|MIXED_PAGE_ALLOCATION|OFF|いいえ|  
|NUMERIC_ROUNDABORT|OFF|はい|  
|PAGE_VERIFY|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の新規インストールの場合は CHECKSUM<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のアップグレードの場合は NONE|はい|  
|PARAMETERIZATION|SIMPLE|はい|  
|QUOTED_IDENTIFIER|OFF|はい|  
|READ_COMMITTED_SNAPSHOT|OFF|いいえ|  
|RECOVERY|SIMPLE|いいえ|  
|RECURSIVE_TRIGGERS|OFF|はい|  
|Service Broker のオプション|ENABLE_BROKER|はい|  
|TRUSTWORTHY|OFF|いいえ|  
  
 これらのデータベース オプションの説明は、「[ALTER DATABASE の SET オプション &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)」を参照してください。  
  
## <a name="restrictions"></a>制限  
 **tempdb** データベースでは、次の操作は実行できません。  
  
- ファイル グループの追加。  
- データベースのバックアップまたは復元。  
- 照合順序の変更。 既定の照合順序はサーバーの照合順序です。  
- データベース所有者の変更。 **tempdb** は **sa**が所有します。  
- データベース スナップショットの作成。  
- データベースの削除。  
- データベースからの **guest** ユーザーの削除。  
- 変更データ キャプチャの有効化。  
- データベース ミラーリングへの参加。  
- プライマリ ファイル グループ、プライマリ データ ファイル、またはログ ファイルの削除。  
- データベース名またはプライマリ ファイル グループ名の変更。  
- DBCC CHECKALLOC の実行。  
- DBCC CHECKCATALOG の実行。  
- データベースの OFFLINE への設定。  
- データベースまたはプライマリ ファイル グループの READ_ONLY への設定。  
  
## <a name="permissions"></a>権限  
 すべてのユーザーが tempdb 内に一時オブジェクトを作成できます。 ユーザーは追加の権限を付与されない限り、自分で作成したオブジェクトにしかアクセスできません。 ユーザーが tempdb を使用できないように tempdb への接続権限を取り消すことはできますが、一部のルーチン処理で tempdb を使用する必要があるためお勧めしません。  

## <a name="optimizing-tempdb-performance"></a>tempdb のパフォーマンスの最適化
 tempdb データベースのサイズと物理的な配置場所は、システムのパフォーマンスに影響を与える可能性があります。 たとえば、tempdb に定義されているサイズが小さすぎると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを再起動するたびに、tempdb のサイズがワークロードのサポートに必要なサイズまで自動的に拡張されるので、システムの処理負荷の一部が占有されます。

 可能な場合は、[データベースのファイルの瞬時初期化](../../relational-databases/databases/database-instant-file-initialization.md)を使用して、データ ファイル拡張操作のパフォーマンスを向上します。
 
 すべての tempdb ファイルに対する領域をあらかじめ割り当てるには、環境における一般的なワークロードに十分に対応できる大きさの値にファイル サイズを設定します。 これにより、パフォーマンスに影響を与える可能性がある tempdb の過度に頻繁な拡張が回避されます。 tempdb データベースは自動拡張が行われるように設定する必要がありますが、これは想定外の例外に対してディスク領域を増加するために使用する必要があります。 

 各[ファイル グループ](../../relational-databases/databases/database-files-and-filegroups.md#filegroups)内でデータ ファイルのサイズは等しくする必要があります。これは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がより多くの空き領域を持つファイル内の割り当てを優先する比例配分アルゴリズムを使用していることによります。 サイズの等しい複数のデータ ファイルに tempdb を分割すると、tempdb を使用する操作において効率の高い並列処理を実現できます。 
 
 tempdb データベース ファイルの拡張単位が小さすぎることのないように、ファイル拡張の増分値を妥当なサイズに設定します。 tempdb に書き込まれたデータ量と比較してファイルの拡張単位が小さすぎると、tempdb を頻繁に拡張する必要が生じる場合があります。 このことは、パフォーマンスに影響します。
 
 現在の tempdb のサイズと拡張パラメーターを確認するには、次のクエリを使用します。
 ```t-sql
 SELECT name AS FileName, 
    size*1.0/128 AS FileSizeinMB,
    CASE max_size 
        WHEN 0 THEN 'Autogrowth is off.'
        WHEN -1 THEN 'Autogrowth is on.'
        ELSE 'Log file will grow to a maximum size of 2 TB.'
    END,
    growth AS 'GrowthValue',
    'GrowthIncrement' = 
        CASE
            WHEN growth = 0 THEN 'Size is fixed and will not grow.'
            WHEN growth > 0 AND is_percent_growth = 0 
                THEN 'Growth value is in 8-KB pages.'
            ELSE 'Growth value is a percentage.'
        END
FROM tempdb.sys.database_files;
GO
```
 
 高速な I/O サブシステムに tempdb データベースを配置します。 直接アタッチされたディスクが多数ある場合は、ディスク ストライピングを使用します。 I/O ボトルネックが発生しない限り、tempdb データ ファイルの個々またはグループを必ずしも別々のディスクまたはスピンドルに配置する必要はありません。
 
 ユーザー データベースによって使用されるディスクとは異なるディスクに tempdb データベースを配置します。

## <a name="performance-improvements-in-tempdb"></a>tempdb でのパフォーマンスの強化  
 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 以降では、**tempdb** のパフォーマンスが次の方法でさらに最適化されています。  
  
- 一時テーブルとテーブル変数はキャッシュされます。 キャッシュを使用することで、一時オブジェクトを削除および作成する操作を非常に高速に実行でき、ページ割り当ての競合が減少します。  
- 割り当てページ ラッチ プロトコルが強化されています。 これにより、使用される UP (更新) ラッチの数が減少します。  
- **tempdb** に対するログ記録のオーバーヘッドが削減されています。 これにより、 **tempdb** ログ ファイルでのディスク I/O 帯域幅の消費量が減少します。  
- セットアップによって、新しいインスタンスのインストール中に複数の tempdb データ ファイルが追加されます。 この操作を実行するには、 **[データベース エンジンの構成]** セクションの新しい UI 入力コントロールまたはコマンド ライン パラメーター /SQLTEMPDBFILECOUNT を使用します。 既定では、セットアップ時に、論理プロセッサ数または 8 のいずれか小さい方と同数の tempdb データ ファイルが追加されます。  
- 複数の **tempdb** データ ファイルがある場合は、拡張設定に応じて、すべてのファイルが同時に同量ずつ自動拡張されます。 トレース フラグ 1117 は必須ではなくなりました。  
- **tempdb** 内のすべての割り当てで単一エクステントが使用されます。 [トレース フラグ 1118](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) は必須ではなくなりました。  
- プライマリ ファイル グループの場合は、AUTOGROW_ALL_FILES プロパティがオンで、プロパティは変更できません。 

## <a name="capacity-planning-for-tempdb"></a>tempdb に使用するディスク領域の計画
 運用環境での tempdb の適切なサイズを判断するには、多くの要因が関係します。 このトピックで前述されているように、これらの要因には既存のワークロードや使用されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の機能などがあります。 SQL Server のテスト環境で次のタスクを実行して、既存のワークロードを分析することをお勧めします。
- tempdb に自動拡張を設定する。
- 個々のクエリまたはワークロード トレース ファイルを実行し、tempdb 領域の使用を監視する。
- インデックスの再構築などのインデックス メンテナンス操作を実行し、tempdb 領域を監視する。 
- 前の手順の使用領域値を使用してワークロード全体の使用量を予測し、予測される同時処理に合わせてこの値を調整し、それに応じて tempdb のサイズを設定する。

## <a name="how-to-monitor-tempdb-use"></a>tempdb の使用状況を監視する方法
  tempdb のディスク領域が不足すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の運用環境で重大な障害が発生したり、実行中のアプリケーションの操作を完了できなくなったりする場合があります。 [sys.dm_db_file_space_usage](../../relational-databases/system-dynamic-management-views/sys-dm-db-session-space-usage-transact-sql.md) 動的管理ビューを使用して、tempdb ファイルで使用されているディスク領域を監視できます。
  
 ```t-sql
 -- Determining the Amount of Free Space in tempdb
 SELECT SUM(unallocated_extent_page_count) AS [free pages], 
  (SUM(unallocated_extent_page_count)*1.0/128) AS [free space in MB]
 FROM sys.dm_db_file_space_usage;
 ```
 
 ```t-sql
 -- Determining the Amount Space Used by the Version Store
 SELECT SUM(version_store_reserved_page_count) AS [version store pages used],
  (SUM(version_store_reserved_page_count)*1.0/128) AS [version store space in MB]
 FROM sys.dm_db_file_space_usage;
 ```
 
 ```t-sql
 -- Determining the Amount of Space Used by Internal Objects
 SELECT SUM(internal_object_reserved_page_count) AS [internal object pages used],
  (SUM(internal_object_reserved_page_count)*1.0/128) AS [internal object space in MB]
 FROM sys.dm_db_file_space_usage;
 ```
 
 ```t-sql
 -- Determining the Amount of Space Used by User Objects
 SELECT SUM(user_object_reserved_page_count) AS [user object pages used],
  (SUM(user_object_reserved_page_count)*1.0/128) AS [user object space in MB]
 FROM sys.dm_db_file_space_usage;
 ```
  
  また、tempdb のページの割り当てや割り当て解除の状態をセッション レベルまたはタスク レベルで監視するには、[sys.dm_db_session_space_usage](../../relational-databases/system-dynamic-management-views/sys-dm-db-session-space-usage-transact-sql.md) 動的管理ビューと [sys.dm_db_task_space_usage](../../relational-databases/system-dynamic-management-views/sys-dm-db-task-space-usage-transact-sql.md) 動的管理ビューを使用できます。 これらのビューを使用すると、tempdb のディスク領域を大量に使用している大きなクエリ、一時テーブル、またはテーブル変数を特定できます。 さらに、tempdb で使用できる空き領域と tempdb を使用しているリソースの監視に使用できるいくつかのカウンターもあります。 詳細については、次のセクションを参照してください。

 ```t-sql
 -- Obtaining the space consumed by internal objects in all currently running tasks in each session
 SELECT session_id, 
  SUM(internal_objects_alloc_page_count) AS task_internal_objects_alloc_page_count,
  SUM(internal_objects_dealloc_page_count) AS task_internal_objects_dealloc_page_count 
 FROM sys.dm_db_task_space_usage 
 GROUP BY session_id;
 ```
 
 ```t-sql
 -- Obtaining the space consumed by internal objects in the current session for both running and completed tasks
 SELECT R2.session_id,
  R1.internal_objects_alloc_page_count 
  + SUM(R2.internal_objects_alloc_page_count) AS session_internal_objects_alloc_page_count,
  R1.internal_objects_dealloc_page_count 
  + SUM(R2.internal_objects_dealloc_page_count) AS session_internal_objects_dealloc_page_count
 FROM sys.dm_db_session_space_usage AS R1 
 INNER JOIN sys.dm_db_task_space_usage AS R2 ON R1.session_id = R2.session_id
 GROUP BY R2.session_id, R1.internal_objects_alloc_page_count, 
  R1.internal_objects_dealloc_page_count;;
 ```

## <a name="related-content"></a>関連コンテンツ  
 [インデックスの SORT_IN_TEMPDB オプション](../../relational-databases/indexes/sort-in-tempdb-option-for-indexes.md)  
 [システム データベース](../../relational-databases/databases/system-databases.md)  
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
 [データベース ファイルの移動](../../relational-databases/databases/move-database-files.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server 2005 での tempdb の使用](http://go.microsoft.com/fwlink/?LinkId=81216)  
 [tempdb のディスク領域の不足に関するトラブルシューティング](http://msdn.microsoft.com/library/ms176029.aspx) 
