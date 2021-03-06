---
title: "sys.dm_os_sys_info (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_os_sys_info_TSQL
- dm_os_sys_info
- dm_os_sys_info_TSQL
- sys.dm_os_sys_info
dev_langs: TSQL
helpviewer_keywords:
- sys.dm_os_sys_info dynamic management view
- time [SQL Server], instance started
- starting time
ms.assetid: 20f6bc9c-839a-4fa4-b3f3-a6c47d1b69af
caps.latest.revision: "57"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 7cc99a6d0f31d19909d41bde4dcd354d1e045215
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmossysinfo-transact-sql"></a>sys.dm_os_sys_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  使用できるとによって消費された有用な情報、コンピューターおよびリソースについての他のセットを返します[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]です。  
  
> **注:**これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_os_sys_info**です。  
  
|列名|データ型|説明とバージョン固有の注意事項 |  
|-----------------|---------------|-----------------|  
|**cpu_ticks**|**bigint**|現在の CPU のティック数を指定します。 CPU のティックは、プロセッサの RDTSC カウンターから取得されます。 この数値は単純に増加します。 Null を許容しません。|  
|**ms_ticks**|**bigint**|コンピューターを起動した時点から経過した時間を指定します (ミリ秒単位)。 Null を許容しません。|  
|**cpu_count**|**int**|システム上の論理 CPU の数を指定します。 Null を許容しません。|  
|**hyperthread_ratio**|**int**|1 つの物理プロセッサ パッケージによって公開されている論理コアまたは物理コアの数の比率を指定します。 Null を許容しません。|  
|**physical_memory_in_bytes**|**bigint**|**適用されます:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]**です。<br /><br /> コンピューターに搭載されている物理メモリの合計を指定します。 Null を許容しません。|  
|**physical_memory_kb**|**bigint**|**適用されます:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**です。<br /><br /> コンピューターに搭載されている物理メモリの合計を指定します。 Null を許容しません。|  
|**virtual_memory_in_bytes**|**bigint**|**適用されます:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]**です。<br /><br /> ユーザー モードのプロセスで使用できる仮想メモリの量。 これを使用すると、SQL Server が 3-GB スイッチを使用して起動されたかどうかを判別できます。|  
|**virtual_memory_kb**|**bigint**|**適用されます:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**です。<br /><br /> ユーザー モードのプロセスで使用できる仮想アドレス空間の合計量を指定します。 Null を許容しません。|  
|**bpool_commited**|**int**|**適用されます:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]**です。<br /><br /> メモリ マネージャーでコミット済みのメモリの量を表します (KB 単位)。 メモリ マネージャー内の予約済みメモリは含まれません。 Null を許容しません。|  
|**committed_kb**|**int**|**適用されます:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**です。<br /><br /> メモリ マネージャーでコミット済みのメモリの量を表します (KB 単位)。 メモリ マネージャー内の予約済みメモリは含まれません。 Null を許容しません。|  
|**bpool_commit_target**|**int**|**適用されます:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]**です。<br /><br /> SQL Server のメモリ マネージャーによって使用できるメモリの量を表します (KB 単位)。|  
|**committed_target_kb**|**int**|**適用されます:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**です。<br /><br /> SQL Server のメモリ マネージャーによって使用できるメモリの量を表します (KB 単位)。 ターゲットの量は、次のような各種の入力を使用して計算されます。<br /><br /> 負荷を含むシステムの現在の状態<br /><br /> -現在のプロセスが要求するメモリ<br /><br /> -コンピューターにインストールされているメモリの量<br /><br /> 構成パラメーター<br /><br /> 場合**committed_target_kb**よりも大きい**committed_kb**、メモリ マネージャーは追加のメモリを獲得しようとしています。 場合**committed_target_kb**よりも小さい**committed_kb**、メモリ マネージャーは、コミットされているメモリの量を縮小しようとしています。 **Committed_target_kb**盗難にあったと予約済みのメモリが必ず含まれます。 Null を許容しません。|  
|**bpool_visible**|**int**|**適用されます:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]**です。<br /><br /> プロセス仮想アドレス空間内で直接アクセスできる、バッファー プールの 8 KB バッファーの数。 AWE (Address Windowing Extensions) を使用していない状態で、バッファー プールで目標とするメモリが確保された場合 (bpool_committed = bpool_commit_target)、bpool_visible の値は bpool_committed の値に等しくなります。SQL Server の 32 ビット環境で AWE を使用している場合、bpool_visible は、バッファー プールによって割り当てられている物理メモリへのアクセスに使用される AWE マッピング ウィンドウのサイズを表します。 このマッピング ウィンドウのサイズはプロセスのアドレス空間にバインドされています。したがって、参照可能なメモリの量はコミット済みメモリの量よりも小さくなります。また、データベース ページ以外の目的でメモリを使用する初期コンポーネントによって、さらに小さくなる可能性があります。 bpool_visible の値が小さ過ぎる場合は、メモリ不足のエラーが返されることがあります。|  
|**visible_target_kb**|**int**|**適用されます:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**です。<br /><br /> 同じ**committed_target_kb**です。 Null を許容しません。|  
|**stack_size_in_bytes**|**int**|によって作成された各スレッドの呼び出し履歴のサイズを指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 Null を許容しません。|  
|**os_quantum**|**bigint**|非プリエンプティブ タスクのクォンタムを表します (ミリ秒単位)。 クォンタム (秒) = **os_quantum** /CPU のクロック速度。 Null を許容しません。|  
|**os_error_mode**|**int**|エラー モードを指定、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]プロセスです。 Null を許容しません。|  
|**os_priority_class**|**int**|優先度クラスを指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]プロセスです。 Null 値を許容します。<br /><br /> 32 = 通常 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は通常の優先度ベース (= 7) で起動しています)。<br /><br /> 128 = 高 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は高い優先度ベースで実行しています。  (=13).)<br /><br /> 詳細については、「 [priority boost サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-priority-boost-server-configuration-option.md)」を参照してください。|  
|**max_workers_count**|**int**|作成可能なワーカーの最大数を表します。 Null を許容しません。|  
|**scheduler_count**|**int**|構成されたユーザー スケジューラの数を表す、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]プロセスです。 Null を許容しません。|  
|**scheduler_total_count**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内のスケジューラの総数を表します。 Null を許容しません。|  
|**deadlock_monitor_serial_number**|**int**|現在のデッドロック監視シーケンスの ID を指定します。 Null を許容しません。|  
|**sqlserver_start_time_ms_ticks**|**bigint**|表す、 **ms_tick**数と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]最後に起動します。 現在の ms_ticks 列と比較します。 Null を許容しません。|  
|**sqlserver_start_time**|**datetime**|日付と時刻を示す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]最後に起動します。 Null を許容しません。|  
|**affinity_type**|**int**|**適用されます: [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]** を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。<br /><br /> 現在使用中のサーバー CPU プロセス関係の種類を指定します。 Null を許容しません。 詳細については、次を参照してください。 [ALTER SERVER CONFIGURATION &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-server-configuration-transact-sql.md).<br /><br /> 1 = MANUAL<br /><br /> 2 = AUTO|  
|**affinity_type_desc**|**varchar(60)**|**適用されます:[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**です。<br /><br /> について説明します、 **affinity_type**列です。 Null を許容しません。<br /><br /> MANUAL = 少なくとも 1 台の CPU に関係が設定されています。<br /><br /> 自動 =[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]自由にスレッドを Cpu 間で移動できます。|  
|**process_kernel_time_ms**|**bigint**|**適用されます:[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]から [です。INCLUDE [ssCurrent]**(../Token/ssCurrent_md.md)] です。<br /><br /> すべてにかかったミリ秒単位で時間の合計[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]スレッドがカーネル モード。 この値にはサーバー上のすべてのプロセッサの時間が含まれるため、単一のプロセッサ クロックより大きくなる場合があります。 Null を許容しません。|  
|**process_user_time_ms**|**bigint**|**適用されます:[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**です。<br /><br /> すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] スレッドがユーザー モードで費やした合計時間 (ミリ秒)。 この値にはサーバー上のすべてのプロセッサの時間が含まれるため、単一のプロセッサ クロックより大きくなる場合があります。 Null を許容しません。|  
|**time_source**|**int**|**適用されます:[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**です。<br /><br /> API を示すを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ウォール クロック時間を取得するを使用します。 Null を許容しません。<br /><br /> 0 = QUERY_PERFORMANCE_COUNTER<br /><br /> 1 = MULTIMEDIA_TIMER|  
|**time_source_desc**|**nvarchar (60)**|**適用されます:[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**です。<br /><br /> について説明します、 **time_source**列です。 Null を許容しません。<br /><br /> QUERY_PERFORMANCE_COUNTER =、 [QueryPerformanceCounter](http://go.microsoft.com/fwlink/?LinkId=163095) API がウォール クロック時間を取得します。<br /><br /> MULTIMEDIA_TIMER =、[マルチ メディア タイマー](http://go.microsoft.com/fwlink/?LinkId=163094) API がウォール クロック時間を取得します。|  
|**virtual_machine_type**|**int**|**適用されます:[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**です。<br /><br /> 示すかどうか[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を仮想環境で実行しています。  Null を許容しません。<br /><br /> 0 = NONE<br /><br /> 1 = HYPERVISOR<br /><br /> 2 = OTHER|  
|**virtual_machine_type_desc**|**nvarchar (60)**|**適用されます:[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**です。<br /><br /> について説明します、 **virtual_machine_type**列です。 Null を許容しません。<br /><br /> NONE =[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]仮想マシンが実行されていません。<br /><br /> ハイパーバイザー =[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]がハードウェア依存の仮想化を意味するハイパーバイザー内で実行されています。 Hyper_V ロールがインストールされている場合、ホストの OS で実行されているインスタンスが、ハイパーバイザーで実行されるように、ハイパーバイザーは、OS をホストします。<br /><br /> その他の =[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が Microsoft Virtual PC などのハードウェアの支援を採用していない仮想マシンの内部で実行されています。|  
|**softnuma_configuration**|**int**|**適用されます:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**です。<br /><br /> 方法の NUMA ノードが構成されているを指定します。 Null を許容しません。<br /><br /> 0 = OFF ハードウェアの既定値を示します<br /><br /> 1 = 自動のソフト NUMA<br /><br /> 2 = レジストリを介して手動ソフト NUMA|  
|**softnuma_configuration_desc**|**nvarchar (60)**|**適用されます:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**です。<br /><br /> ソフト NUMA をオフ = 機能はオフ<br /><br /> SQL Server を自動的に = ソフト NUMA の NUMA ノードのサイズを決定します。<br /><br /> 手動ソフト NUMA を手動で構成したを =|
|**process_physical_affinity**|**nvarchar(3072)** |**適用されます: で始まる[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]**です。<br /><br />今後登場する情報です。 |
|**sql_memory_model**|**int**|**適用されます: [!INCLUDE[sssql11](../../includes/sssql11-md.md)] SP4 以降[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]SP1**です。<br /><br />メモリの割り当てに SQL Server で使用されるメモリ モデルを指定します。 Null を許容しません。<br /><br />1 = コンベンショナル メモリ モデル<br />2 = lock Pages in Memory<br /> 3 = メモリ内のラージ ページ|
|**sql_memory_model_desc**|**nvarchar(120)**|**適用されます: [!INCLUDE[sssql11](../../includes/sssql11-md.md)] SP4 以降[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]SP1**です。<br /><br />メモリの割り当てに SQL Server で使用されるメモリ モデルを指定します。 Null を許容しません。<br /><br />**従来**= SQL Server は、コンベンショナル メモリ モデルを使用してメモリを割り当てることができます。 これは、SQL Server サービス アカウントがないときのページのロック メモリ特権での起動中に、既定の sql メモリ モデルです。<br />**LOCK_PAGES** = SQL server が Lock Pages メモリ内の使用メモリを割り当てられません。 これは、SQL Server サービス アカウントは、SQL Server の起動中に Memory 特権でのページのロックを所有しているときの既定の sql のメモリ マネージャーです。<br /> **LARGE_PAGES** = SQL Server がサイズの大きなページ メモリ内の使用メモリを割り当てられません。 SQL Server では、大きなページ アロケーターを使用して、サーバーの起動時に、トレース フラグ 834 がオンにすると、SQL Server サービス アカウントが Memory 特権でのページのロックを持つときに、Enterprise edition でのみメモリを割り当てます。|
|**pdw_node_id**|**int**|**適用されます: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]**<br /><br /> この分布はでは、ノードの識別子。|  
|**socket_count** |**int** | **適用されます: で始まる[!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)]**です。<br /><br />システム上の利用可能なプロセッサ ソケット数を指定します。 |  
|**cores_per_socket** |**int** | **適用されます: で始まる[!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)].**です。<br /><br />システム上の 1 つのソケットの使用可能なプロセッサの数を指定します。 |  
|**numa_node_count** |**int** | **適用されます: で始まる[!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)].**です。<br /><br />システムで使用可能な numa ノードの数を指定します。 この列には、ソフト numa ノードだけでなく、物理 numa ノードが含まれています。 |  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]必要があります`VIEW SERVER STATE`サーバーに対する権限。  
  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Premium 階層が必要です、`VIEW DATABASE STATE`データベースの権限です。 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Standard および Basic 階層が必要です、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]管理者アカウントです。  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [SQL Server オペレーティング システム関連の動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  



