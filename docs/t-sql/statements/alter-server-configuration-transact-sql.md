---
title: "ALTER SERVER CONFIGURATION (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER SERVER CONFIGURATION
- ALTER_SERVER_CONFIGURATION_TSQL
dev_langs: TSQL
helpviewer_keywords:
- SERVER CONFIGURATION, ALTER
- process affinity, setting
- ALTER SERVER CONFIGURATION statement
- setting process affinity
ms.assetid: f3059e42-5f6f-4a64-903c-86dca212a4b4
caps.latest.revision: "72"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 4489934ad1bb21c79cbb0ece01e7d061fd794c2a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="alter-server-configuration-transact-sql"></a>ALTER SERVER CONFIGURATION (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で現在のサーバーのグローバル構成設定を変更します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
ALTER SERVER CONFIGURATION  
SET <optionspec>   
[;]  
  
<optionspec> ::=  
{  
     <process_affinity>  
   | <diagnostic_log>  
   | <failover_cluster_property>  
   | <hadr_cluster_context>  
   | <buffer_pool_extension>  
   | <soft_numa>  
}  
  
<process_affinity> ::=   
   PROCESS AFFINITY   
   {  
     CPU = { AUTO | <CPU_range_spec> }   
   | NUMANODE = <NUMA_node_range_spec>   
   }  
   <CPU_range_spec> ::=   
      { CPU_ID | CPU_ID  TO CPU_ID } [ ,...n ]   
  
   <NUMA_node_range_spec> ::=   
      { NUMA_node_ID | NUMA_node_ID TO NUMA_node_ID } [ ,...n ]  
  
<diagnostic_log> ::=   
   DIAGNOSTICS LOG   
   {   
     ON    
   | OFF    
   | PATH = { 'os_file_path' | DEFAULT }    
   | MAX_SIZE = { 'log_max_size' MB | DEFAULT }    
   | MAX_FILES = { 'max_file_count' | DEFAULT }    
   }  
  
<failover_cluster_property> ::=   
   FAILOVER CLUSTER PROPERTY <resource_property>  
   <resource_property> ::=  
      {  
        VerboseLogging = { 'logging_detail' | DEFAULT }    
      | SqlDumperDumpFlags = { 'dump_file_type' | DEFAULT }  
      | SqlDumperDumpPath = { 'os_file_path'| DEFAULT }  
      | SqlDumperDumpTimeOut = { 'dump_time-out' | DEFAULT }  
      | FailureConditionLevel = { 'failure_condition_level' | DEFAULT }  
      | HealthCheckTimeout = { 'health_check_time-out' | DEFAULT }  
      }  
  
<hadr_cluster_context> ::=  
   HADR CLUSTER CONTEXT = { 'remote_windows_cluster' | LOCAL }  
  
<buffer_pool_extension>::=  
    BUFFER POOL EXTENSION   
    { ON ( FILENAME = 'os_file_path_and_name' , SIZE = <size_spec> )   
    | OFF }  
  
    <size_spec> ::=  
        { size [ KB | MB | GB ] }  
  
<soft_numa> ::=  
    SET SOFTNUMA  
    { ON | OFF }  
```  
  
## <a name="arguments"></a>引数  
 **\<process_affinity >:: =**  
  
 PROCESS AFFINITY  
 CPU へのハードウェア スレッドの関連付けを有効にします。  
  
 CPU = {自動 |\<CPU_range_spec >}  
 指定された範囲内の個々の CPU に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のワーカー スレッドを配分します。 指定された範囲外の CPU にはスレッドの割り当ては行われません。  
  
 AUTO  
 CPU へのスレッドの割り当てを一切行いません。 サーバーのワークロードに基づいて、オペレーティング システムが複数の CPU 間で自由にスレッドを移動できます。 これは既定値であり、推奨される設定。  
  
 \<CPU_range_spec >:: =  
 スレッドを割り当てる CPU または CPU の範囲を指定します。  
  
 { CPU_ID | CPU_ID  TO  CPU_ID } [ ,...n ]  
 1 つ以上の CPU の一覧を指定します。 CPU Id は 0 から始まる**整数**値。  
  
 NUMANODE = \<NUMA_node_range_spec >  
 指定された NUMA ノードまたはノードの範囲に属しているすべての CPU にスレッドを割り当てます。  
  
 \<NUMA_node_range_spec >:: =  
 NUMA ノードまたは NUMA ノードの範囲を指定します。  
  
 { NUMA_node_ID | NUMA_node_ID  TO NUMA_node_ID } [ ,...n ]  
 1 つ以上の NUMA ノードの一覧を指定します。 NUMA ノード Id は 0 から始まる**整数**値。  
  
 **\<diagnostic_log >:: =**  
  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 DIAGNOSTICS LOG  
 sp_server_diagnostics プロシージャによってキャプチャされた診断データのログ記録を開始または停止し、SQLDIAG ログの構成パラメーター (ログ ファイルのロールオーバー回数、ログ ファイルのサイズ、ファイルの場所など) を設定します。 詳細については、「 [フェールオーバー クラスター インスタンスの診断ログを表示して読む方法](../../sql-server/failover-clusters/windows/view-and-read-failover-cluster-instance-diagnostics-log.md)」を参照してください。  
  
 ON  
 開始[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]PATH ファイル オプションで指定した場所に診断データのログ記録します。 これは既定値です。  
  
 OFF  
 診断データのログ記録を停止します。  
  
 PATH = { 'os_file_path' | DEFAULT }  
 診断ログの場所を示すパス。 既定の場所は\<\MSSQL\Log > のインストール フォルダー内で、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]フェールオーバー クラスター インスタンス。  
  
 MAX_SIZE = { 'log_max_size' MB | DEFAULT }  
 各診断ログを拡張できるメガバイト単位で最大サイズ。 既定値は 100 MB です。  
  
 MAX_FILES = { 'max_file_count' | DEFAULT }  
 新しい診断ログとして再利用されるまでにコンピューターに格納できる診断ログ ファイルの最大数。  
  
 **\<failover_cluster_property >:: =**  
  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 FAILOVER CLUSTER PROPERTY  
 SQL Server リソース プライベート フェールオーバー クラスターのプロパティを変更します。  
  
 VERBOSE LOGGING = { 'logging_detail' | DEFAULT }  
 SQL Server フェールオーバー クラスタリングのログ記録レベルを設定します。 オンにすると、トラブルシューティングを目的とした詳細情報をエラー ログに追加できます。  
  
-   0: ログ記録はオフです (既定)。  
  
-   1: エラーのみ。  
  
-   2: エラーおよび警告。  
  
SQLDUMPEREDUMPFLAGS  
 SQL Server の SQLDumper ユーティリティによって生成されるダンプ ファイルの種類を決定します。 既定の設定は 0 です。 詳細については、次を参照してください。 [SQL Server Dumper ユーティリティ サポート技術情報の記事](http://go.microsoft.com/fwlink/?LinkId=206173)です。  
  
 SQLDUMPERDUMPPATH = { 'os_file_path' | DEFAULT }  
 SQLDumper ユーティリティがダンプ ファイルを保存する場所。 詳細については、次を参照してください。 [SQL Server Dumper ユーティリティ サポート技術情報の記事](http://go.microsoft.com/fwlink/?LinkId=206173)です。  
  
 SQLDUMPERDUMPTIMEOUT = { 'dump_time-out' | DEFAULT }  
 SQL Server でエラーが発生した場合の、SQLDumper ユーティリティによるダンプの生成のタイムアウト値 (ミリ秒単位)。 既定値は 0 で、ダンプの完了に時間制限がないことを示します。 詳細については、次を参照してください。 [SQL Server Dumper ユーティリティ サポート技術情報の記事](http://go.microsoft.com/fwlink/?LinkId=206173)です。  
  
 FAILURECONDITIONLEVEL = { 'failure_condition_level' | DEFAULT }  
 SQL Server フェールオーバー クラスター インスタンスがフェイルオーバーまたは再起動する必要がある状態。 既定値は 3 で、重大なサーバー エラーの発生時に SQL Server リソースがフェールオーバーまたは再起動することを示します。 この構成およびその他のエラー条件レベルの詳細については、次を参照してください。 [FailureConditionLevel プロパティ設定の構成](../../sql-server/failover-clusters/windows/configure-failureconditionlevel-property-settings.md)です。  
  
 HEALTHCHECKTIMEOUT = { 'health_check_time-out' | DEFAULT }  
 SQL Server データベース エンジンのリソース DLL が、サーバーの状態情報を待機する時間のタイムアウト値です。この待機時間を経過すると、SQL Server のインスタンスが応答不能と見なされます。 このタイムアウト値は、ミリ秒単位で指定します。 既定値は 60,000 ミリ秒 (60 秒) です。  
  
 **\<hadr_cluster_context >:: =**  
  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 HADR クラスター コンテキスト **=**  { **'***remote_windows_cluster***'** |ローカル}  
 サーバー インスタンスの HADR クラスター コンテキストを、指定した Windows Server フェールオーバー クラスタリング (WSFC) クラスターに切り替えます。 *HADR クラスター コンテキスト*どのような Windows Server フェールオーバー クラスタ リング (WSFC) クラスターを管理サーバーのインスタンスによってホストされる可用性レプリカのメタデータを決定します。 クラスター間で移行中にのみの SET HADR CLUSTER CONTEXT オプションを使用して[!INCLUDE[ssHADR](../../includes/sshadr-md.md)]のインスタンスに[!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]新しい WSFC クラスター上の以降のバージョン。  
  
 HADR クラスター コンテキストの切り替えは、ローカル WSFC クラスターとリモート クラスター間でのみ実行できます。 HADR クラスター コンテキストは、リモート クラスターに切り替えることがされる場合にのみのインスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は任意の可用性レプリカをホストしていません。  
  
 リモート HADR クラスター コンテキストは、いつでもローカル クラスターに切り替えることができます。 ただし、コンテキストは、サーバー インスタンスが可用性レプリカをホストしている限り、再度切り替えることはできません。  
  
 切り替え先のクラスターを識別するには、次のいずれかの値を指定します。  
  
 *windows_cluster*  
 WSFC クラスターのクラスター オブジェクト名 (CON)。 短い名前または完全なドメイン名を指定できます。 短い名前のターゲット IP アドレスを検出するために、ALTER SERVER CONFIGURATION は DNS 解決を使用します。 ある種の状況では、短い名前を使用すると混乱が生じ、DNS から誤った IP アドレスが返されることがあります。 そのため、完全なドメイン名を指定することをお勧めします。  
  
 LOCAL  
 ローカル WSFC クラスター。  
  
 詳細については、次を参照してください[、HADR クラスター コンテキストのサーバー インスタンス &#40; を変更する。SQL Server &#41;](../../database-engine/availability-groups/windows/change-the-hadr-cluster-context-of-server-instance-sql-server.md).  
  
 **\<buffer_pool_extension >:: =**  
  
**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 ON  
 バッファー プール拡張オプションを有効にします。 このオプションは、ソリッドステート ドライブ (SSD) などの不揮発性ストレージを使用してクリーン データ ページをプールに保持することで、バッファー プールのサイズを拡張します。 この機能の詳細については、次を参照してください。[バッファー プール拡張](../../database-engine/configure-windows/buffer-pool-extension.md)です。バッファー プール拡張機能では、すべての SQL Server エディションで使用できません。 詳細については、次を参照してください。[エディションと SQL Server 2016 のサポートされる機能](../../sql-server/editions-and-supported-features-for-sql-server-2016.md)します。  
  
 FILENAME = 'os_file_path_and_name'  
 バッファー プール拡張キャッシュ ファイルのディレクトリ パスと名前を定義します。 ファイル拡張子は .BPE と指定する必要があります。 FILENAME を変更する前に BUFFER POOL EXTENSION を無効にする必要があります。  
  
 サイズ =*サイズ*[ **KB** |MB |GB]  
 キャッシュのサイズを定義します。 既定のサイズの指定は KB です。 最小サイズは最大サーバー メモリのサイズです。 最大値は最大サーバー メモリのサイズの 32 倍です。 最大サーバー メモリの詳細については、次を参照してください。 [sp_configure &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
 ファイルのサイズを変更する前に BUFFER POOL EXTENSION を無効にする必要があります。 現在のサイズより小さいサイズを指定するには、SQL Server のインスタンスを再起動してメモリを再利用する必要があります。 これを行わない場合は、現在のサイズのままにしておくか、現在のサイズより大きいサイズを指定する必要があります。  
  
 OFF  
 バッファー プール拡張オプションを無効にします。 ファイルのサイズや名前など、関連するパラメーターを変更する場合は、事前にバッファー プール拡張オプションを無効にする必要があります。 このオプションを無効にすると、関連するすべての構成情報がレジストリから削除されます。  
  
> [!WARNING]  
>  バッファー プール拡張を無効にすると、バッファー プールのサイズが大幅に縮小されるため、サーバー パフォーマンスにマイナスの影響がある場合があります。  
  
 **\<ソフト numa >**  

**適用対象**: [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 ON  
 小規模な NUMA ノードに大規模な NUMA ハードウェアのノードを分割する自動パーティション分割を使用できます。 実行中の値を変更するには、データベース エンジンの再起動が必要です。  
  
 OFF  
 大規模な NUMA ハードウェア ノードの小規模な NUMA ノードへのソフトウェアの自動がパーティション分割を無効にします。 実行中の値を変更するには、データベース エンジンの再起動が必要です。  

> [!WARNING]  
> 既知の問題は、ALTER SERVER CONFIGURATION ステートメント、ソフト NUMA オプションと SQL Server エージェントの動作とします。  推奨される操作のシーケンスを次に示します。  
> 1) SQL Server エージェントのインスタンスを停止します。  
> 2) サーバー構成ソフト NUMA を変更するオプションを実行します。  
> 3) SQL Server インスタンスを再開します。  
> 4) SQL Server エージェントのインスタンスを起動します。  
  
**詳細情報:**は戻ること T-SQL 再構成コマンドを実行、SQL Server サービスの再起動前に、SQL Server エージェント サービスが停止したときに、ALTER SERVER CONFIGURATION SET SOFTNUMA コマンドを使用してを実行する場合、SOFTNUMA 設定は、ALTER SERVER CONFIGURATION 前の状態に戻します。 
  
## <a name="general-remarks"></a>全般的な解説  
 このステートメントでは、再起動は必要ありません[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]明記しない限り、します。 場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]フェールオーバー クラスター インスタンスでは不要の再起動、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クラスター リソースです。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 このステートメントは、DDL トリガーをサポートしません。  
  
## <a name="permissions"></a>Permissions  
 プロセス関係オプションに対する ALTER SETTINGS 権限が必要です。 診断ログとフェールオーバー クラスター プロパティ オプションに対する ALTER SETTINGS 権限と VIEW SERVER STATE 権限、および HADR クラスター コンテキスト オプションに対する CONTROL SERVER 権限。  
  
 バッファー プール拡張オプションに対する ALTER SERVER STATE 権限が必要です。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]リソース DLL は、ローカル システム アカウントで実行します。 そのため、ローカル システム アカウントには、診断ログ オプションで指定されたパスに対する読み取りアクセス権および書き込みアクセス権が必要です。  
  
## <a name="examples"></a>使用例  
  
|カテゴリ|主な構文要素|  
|--------------|------------------------------|  
|[プロセス関係の設定](#Affinity)|CPU、NUMANODE、AUTO|  
|[診断ログ オプションの設定](#Diagnostic)|ON、OFF、PATH、MAX_SIZE|  
|[フェールオーバー クラスターのプロパティを設定](#Failover)|HealthCheckTimeout|  
|[可用性レプリカのクラスター コンテキストを変更します。](#ChangeClusterContextExample)|**'** *windows_cluster* **'**|  
|[バッファー プール拡張の設定](#BufferPoolExtension)|BUFFER POOL EXTENSION|  
  
###  <a name="Affinity"></a>プロセス関係の設定  
 このセクションの例では、CPU および NUMA ノードにプロセス関係を設定する方法を示します。 この例では、256 個の CPU が、4 つのグループから成る NUMA ノード構成 (4 グループ合計 16 ノード) でサーバーに搭載されていることを想定しています。 NUMA ノードにも CPU にもスレッドは割り当てられていません。  
  
-   ～ 3 では、0 ～ 63 の Cpu グループ 0: NUMA ノード 0  
-   グループ 1: NUMA ノード 4 ～ 7、64 ～ 127 の Cpu  
-   NUMA ノードのグループ 2: 8 ～ 12、128 ～ 191 の Cpu  
-   グループ 3: NUMA ノード 13 ～ 16、CPU 192 ～ 255  
  
#### <a name="a-setting-affinity-to-all-cpus-in-groups-0-and-2"></a>A. グループ 0 とグループ 2 のすべての CPU に関係を設定する  
 次の例では、グループ 0 とグループ 2 のすべての CPU に関係を設定します。  
  
```  
ALTER SERVER CONFIGURATION   
SET PROCESS AFFINITY CPU=0 TO 63, 128 TO 191;  
```  
  
#### <a name="b-setting-affinity-to-all-cpus-in-numa-nodes-0-and-7"></a>B. NUMA ノード 0 と NUMA ノード 7 のすべての CPU に関係を設定する  
 次の例は、ノードに CPU 関係を設定`0`と`7`のみです。  
  
```  
ALTER SERVER CONFIGURATION   
SET PROCESS AFFINITY NUMANODE=0, 7;  
```  
  
#### <a name="c-setting-affinity-to-cpus-60-through-200"></a>C. CPU 60 ～ 200 に関係を設定する  
 次の例では、CPU 60 ～ 200 に関係を設定します。  
  
```  
ALTER SERVER CONFIGURATION   
SET PROCESS AFFINITY CPU=60 TO 200;  
```  
  
#### <a name="d-setting-affinity-to-cpu-0-on-a-system-that-has-two-cpus"></a>D. CPU が 2 個搭載されたシステムの CPU 0 に関係を設定する  
 次の例では、CPU を 2 個搭載しているコンピューターの `CPU=0` に関係を設定します。 次のステートメントを実行する前の内部的な関係ビットマスク (affinity bitmask) は 00 です。  
  
```  
ALTER SERVER CONFIGURATION SET PROCESS AFFINITY CPU=0;  
```  
  
#### <a name="e-setting-affinity-to-auto"></a>E. 関係を AUTO に設定する  
 次の例では、関係を `AUTO` に設定します。  
  
```  
ALTER SERVER CONFIGURATION  
SET PROCESS AFFINITY CPU=AUTO;  
```  
  
###  <a name="Diagnostic"></a> Setting diagnostic log options  
  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 このセクションの例では、診断ログ オプションの値を設定する方法を示します。  
  
#### <a name="a-starting-diagnostic-logging"></a>A. 診断ログの記録を開始する  
 次の例では、診断データのログ記録を開始します。  
  
```  
ALTER SERVER CONFIGURATION SET DIAGNOSTICS LOG ON;  
```  
  
#### <a name="b-stopping-diagnostic-logging"></a>B. 診断ログの記録を停止する  
 次の例では、診断データのログ記録を停止します。  
  
```  
ALTER SERVER CONFIGURATION SET DIAGNOSTICS LOG OFF;  
```  
  
#### <a name="c-specifying-the-location-of-the-diagnostic-logs"></a>C. 診断ログの場所を指定する  
 次の例では、診断ログの場所を、指定されたファイル パスに設定します。  
  
```  
ALTER SERVER CONFIGURATION  
SET DIAGNOSTICS LOG PATH = 'C:\logs';  
```  
  
#### <a name="d-specifying-the-maximum-size-of-each-diagnostic-log"></a>D. 各診断ログの最大サイズを指定する  
 次の例では、各診断ログの最大サイズを 10 MB に設定します。  
  
```  
ALTER SERVER CONFIGURATION   
SET DIAGNOSTICS LOG MAX_SIZE = 10 MB;  
```  
  
###  <a name="Failover"></a>フェールオーバー クラスターのプロパティを設定  
  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 次の例の値の設定、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]フェイル オーバー クラスター リソースのプロパティです。  
  
#### <a name="a-specifying-the-value-for-the-healthchecktimeout-property"></a>A. HealthCheckTimeout プロパティの値を指定する  
 次の例のセット、`HealthCheckTimeout`オプションを 15,000 ミリ秒 (15 秒)。  
  
```  
ALTER SERVER CONFIGURATION   
SET FAILOVER CLUSTER PROPERTY HealthCheckTimeout = 15000;  
```  
  
###  <a name="ChangeClusterContextExample"></a> B. 可用性レプリカのクラスター コンテキストを変更する  
 次の例のインスタンスの HADR クラスター コンテキストを変更する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 変更先の WSFC クラスターである `clus01` を指定するため、この例では、完全なクラスター オブジェクト名である `clus01.xyz.com` を指定します。  
  
```  
ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT = 'clus01.xyz.com';  
```  
  
### <a name="setting-buffer-pool-extension-options"></a>バッファー プール拡張オプションを設定する  
  
####  <a name="BufferPoolExtension"></a> A. バッファー プール拡張オプションを設定  
  
**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 次の例では、バッファー プール拡張オプションを有効にし、ファイル名とサイズを指定します。  
  
```  
ALTER SERVER CONFIGURATION   
SET BUFFER POOL EXTENSION ON  
    (FILENAME = 'F:\SSDCACHE\Example.BPE', SIZE = 50 GB);  
```  
  
#### <a name="b-modifying-buffer-pool-extension-parameters"></a>B. バッファー プール拡張パラメーターを変更する  
 次の例は、バッファー プール拡張ファイルのサイズを変更します。 いずれかのパラメーターを変更する場合は、バッファー プール拡張オプションを事前に無効にする必要があります。  
  
```  
ALTER SERVER CONFIGURATION   
SET BUFFER POOL EXTENSION OFF;  
GO  
EXEC sp_configure 'max server memory (MB)', 12000;  
GO  
RECONFIGURE;  
GO  
ALTER SERVER CONFIGURATION  
SET BUFFER POOL EXTENSION ON  
    (FILENAME = 'F:\SSDCACHE\Example.BPE', SIZE = 60 GB);  
GO  
  
```  
  
## <a name="see-also"></a>参照  
 [ソフト NUMA &#40;です。SQL Server &#41;](../../database-engine/configure-windows/soft-numa-sql-server.md)   
 [サーバー インスタンス &#40; の HADR クラスター コンテキストを変更します。SQL Server &#41;](../../database-engine/availability-groups/windows/change-the-hadr-cluster-context-of-server-instance-sql-server.md)   
 [sys.dm_os_schedulers &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md)   
 [sys.dm_os_memory_nodes &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-nodes-transact-sql.md)   
 [sys.dm_os_buffer_pool_extension_configuration &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-buffer-pool-extension-configuration-transact-sql.md)   
 [バッファー プール拡張](../../database-engine/configure-windows/buffer-pool-extension.md)  
  
  
