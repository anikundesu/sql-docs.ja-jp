---
title: "レプリケーション スナップショット エージェント | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Snapshot Agent, executables
- agents [SQL Server replication], Snapshot Agent
- command prompt [SQL Server replication]
- Snapshot Agent, parameter reference
ms.assetid: 2028ba45-4436-47ed-bf79-7c957766ea04
caps.latest.revision: "41"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 368401643f14af5c3f59621ce5ef6180305318cb
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="replication-snapshot-agent"></a>レプリケーション スナップショット エージェント
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] レプリケーション スナップショット エージェントは、パブリッシュされたテーブルおよびデータベース オブジェクトのスキーマとデータを含むスナップショット ファイルを作成し、これらのファイルをスナップショット フォルダーに格納し、同期ジョブをディストリビューション データベースに記録する実行可能ファイルです。  
  
> [!NOTE]  
>  パラメーターは任意の順序で指定できます。  
  
## <a name="syntax"></a>構文  
  
```  
  
snapshot [ -?]   
-Publisher server_name[\instance_name]   
-Publication publication_name   
[-70Subscribers]   
[-BcpBatchSize bcp_batch_size]  
[-DefinitionFile def_path_and_file_name]  
[-Distributor server_name[\instance_name]]  
[-DistributorDeadlockPriority [-1|0|1] ]  
[-DistributorLogin distributor_login]  
[-DistributorPassword distributor_password]  
[-DistributorSecurityMode [0|1] ]  
[-DynamicFilterHostName dynamic_filter_host_name]  
[-DynamicFilterLogin dynamic_filter_login]  
[-DynamicSnapshotLocation dynamic_snapshot_location]   
[-EncryptionLevel [0|1|2]]  
[-FieldDelimiter field_delimiter]  
[-HistoryVerboseLevel [0|1|2|3] ]  
[-HRBcpBlocks number_of_blocks ]  
[-HRBcpBlockSize block_size ]  
[-HRBcpDynamicBlocks ]  
[-KeepAliveMessageInterval keep_alive_interval]  
[-LoginTimeOut login_time_out_seconds]  
[-MaxBcpThreads number_of_threads ]  
[-MaxNetworkOptimization [0|1]]  
[-Output output_path_and_file_name]  
[-OutputVerboseLevel [0|1|2] ]  
[-PacketSize packet_size]  
[-ProfileName profile_name]  
[-PublisherDB publisher_database]  
[-PublisherDeadlockPriority [-1|0|1] ]  
[-PublisherFailoverPartner server_name[\instance_name] ]  
[-PublisherLogin publisher_login]  
[-PublisherPassword publisher_password]   
[-PublisherSecurityMode [0|1] ]  
[-QueryTimeOut query_time_out_seconds]  
[-ReplicationType [1|2] ]  
[-RowDelimiter row_delimiter]  
[-StartQueueTimeout start_queue_timeout_seconds]  
[-UsePerArticleContentsView use_per_article_contents_view]  
```  
  
## <a name="arguments"></a>引数  
 **-?**  
 使用できるすべてのパラメーターを表示します。  
  
 **-Publisher**  *server_name*[**\\***instance_name*]  
 パブリッシャーの名前です。 サーバー上の [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定のインスタンスの場合は、server_name を指定します。 サーバー上の *server_name***\\***instance_name* instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定のインスタンスの場合は、server_name を指定します。  
  
 **-Publication** *publication*  
 パブリケーションの名前です。 このパラメーターは、新規または再初期化されたサブスクリプションのスナップショットを常に利用できるようにパブリケーションを設定している場合にのみ有効です。  
  
 **-70Subscribers**  
 いずれかのサブスクライバーで [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 7.0 が動作している場合に、必ず使用します。  
  
 **-BcpBatchSize** *bcp*_ *batch*\_ *size*  
 一括コピー操作によって送られる行の数です。 **bcp in** 操作を実行する場合、バッチ サイズは 1 つのトランザクションとしてサーバーに送る行数です。ディストリビューション エージェントが **bcp** 実行状況メッセージをログに記録する前に、これらの行数を送る必要があります。 **bcp out** 操作を実行する場合は、固定バッチ サイズ 1000 が使用されます。 値 0 は、メッセージをログに記録しないことを示します。  
  
 **-DefinitionFile** *def_path_and_file_name*  
 エージェント定義ファイルのパスです。 エージェント定義ファイルには、エージェントのコマンド ライン引数が含まれます。 ファイルの内容は実行可能ファイルとして解析されます。 二重引用符 (") を使用して、任意の文字を含む引数値を指定します。  
  
 **-Distributor** *server_name*[**\\***instance_name*]  
 ディストリビューターの名前です。 サーバー上の *の既定のインスタンスの場合は、* server_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を指定します。 サーバー上の *server_name***\\***instance_name* instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定のインスタンスの場合は、server_name を指定します。  
  
 **-DistributorDeadlockPriority** [**-1**|**0**|**1**]  
 デッドロックが発生した場合のディストリビューターへのスナップショット エージェント接続の優先度です。 このパラメーターは、スナップショットの生成中にスナップショット エージェントとユーザー アプリケーション間で発生する可能性のあるデッドロックを解決するために指定します。  
  
|DistributorDeadlockPriority の値|説明|  
|---------------------------------------|-----------------|  
|**-1**|ディストリビューター側でデッドロックが発生した場合、スナップショット エージェント以外のアプリケーションが優先されます。|  
|**0** (既定値)|優先度は割り当てられません。|  
|**1**|ディストリビューター側でデッドロックが発生した場合、スナップショット エージェントが優先されます。|  
  
 **-DistributorLogin** *distributor_login*  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用してディストリビューターに接続するときに使用されるログインです。  
  
 **-DistributorPassword** *distributor_password*  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用してディストリビューターに接続するときに使用されるパスワードです。 」を参照してください。  
  
 **-DistributorSecurityMode** [ **0**| **1**]  
 ディストリビューターのセキュリティ モードを指定します。 値 **0** は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証モード (既定値) を示し、値 **1** は Windows 認証モードを示します。  
  
 **-DynamicFilterHostName** *dynamic_filter_host_name*  
 動的スナップショットの作成時に、フィルター選択用の [HOST_NAME &#40;Transact-SQL&#41;](../../../t-sql/functions/host-name-transact-sql.md) の値を設定するために使用されます。 たとえば、アーティクルに対してサブセット フィルター句 `rep_id = HOST_NAME()` を指定し、 **DynamicFilterHostName** プロパティを "FBJones" に設定した後でマージ エージェントを呼び出すと、 **rep_id** 列に "FBJones" が含まれる行だけがレプリケートされます。  
  
 **-DynamicFilterLogin** *dynamic_filter_login*  
 動的スナップショットの作成時に、フィルター選択用の [SUSER_SNAME &#40;Transact-SQL&#41;](../../../t-sql/functions/suser-sname-transact-sql.md) の値を設定するために使用されます。 たとえば、アーティクルに対してサブセット フィルター句 `user_id = SUSER_SNAME()` を指定し、 **DynamicFilterLogin** プロパティを "rsmith" に設定した後で、 **SQLSnapshot** オブジェクトの **Run** メソッドを呼び出すと、 **user_id** 列に "rsmith" を含む行だけがスナップショットに含められます。  
  
 **-DynamicSnapshotLocation** *dynamic_snapshot_location*  
 動的スナップショットの生成先の場所です。  
  
 **-EncryptionLevel** [ **0** | **1** | **2** ]  
 スナップショット エージェントが接続時に使用する SSL (Secure Sockets Layer) 暗号化レベルです。  
  
|EncryptionLevel の値|説明|  
|---------------------------|-----------------|  
|**0**|SSL は使用されません。|  
|**1**|SSL は使用されますが、信頼できる発行者によって SSL サーバー証明が署名されているかどうかを検証しません。|  
|**2**|SSL が使用され、証明書の確認が行われます。|  
  
 詳細については、「[セキュリティの概要 &#40;レプリケーション&#41;](../../../relational-databases/replication/security/security-overview-replication.md)」を参照してください。  
  
 **-FieldDelimiter** *field_delimiter*  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 一括コピーで扱うデータ ファイルのフィールドの末尾を示す 1 文字または文字列です。 既定値は \n\<x$3>\n です。  
  
 **-HistoryVerboseLevel** [ **1**| **2**| **3**]  
 スナップショット操作中にログに記録する履歴の量を指定します。 **1**を選択すれば、ログへの履歴の記録がパフォーマンスに与える影響を最小限に抑えることができます。  
  
|HistoryVerboseLevel の値|説明|  
|-------------------------------|-----------------|  
|**0**|進行状況メッセージがコンソールまたは出力ファイルに書き込まれます。 履歴レコードは、ディストリビューション データベースのログに記録されません。|  
|**1**|同じ状態 (startup、progress、success など) を示している以前の履歴メッセージを常に更新します。 前回の記録に同じ状態がない場合は、新しい記録を挿入します。|  
|**2** (既定値)|アイドル状態や長時間実行を示すメッセージでない場合、新しい履歴レコードを挿入します。アイドル状態などを示すメッセージの場合には、以前のレコードを更新します。|  
|**3**|アイドル状態を示すメッセージの場合以外は、常に新しいレコードを挿入します。|  
  
 **-HRBcpBlocks** *number_of_blocks*  
 ライター スレッドとリーダー スレッド間でキューに格納される **bcp** データ ブロックの数です。 既定値は 50 です。 **HRBcpBlocks** は、Oracle パブリケーションでのみ使用されます。  
  
> [!NOTE]  
>  このパラメーターは、Oracle パブリッシャーから **bcp** パフォーマンスのチューニングを行う場合に使用されます。  
  
 -**HRBcpBlockSize***block_size*  
 各 **bcp** データ ブロックのサイズ (KB) です。 既定値は 64 KB です。 **HRBcpBlocks** は、Oracle パブリケーションでのみ使用されます。  
  
> [!NOTE]  
>  このパラメーターは、Oracle パブリッシャーから **bcp** パフォーマンスのチューニングを行う場合に使用されます。  
  
 **-HRBcpDynamicBlocks**  
 各 **bcp** データ ブロックのサイズが動的に拡張可能かどうかを示します。 **HRBcpBlocks** は、Oracle パブリケーションでのみ使用されます。  
  
> [!NOTE]  
>  このパラメーターは、Oracle パブリッシャーから **bcp** パフォーマンスのチューニングを行う場合に使用されます。  
  
 **-KeepAliveMessageInterval** *keep_alive_interval*  
 [MSsnapshot_history](../../../relational-databases/system-tables/mssnapshot-history-transact-sql.md) テーブルに "waiting for backend message" が記録されるまでのスナップショット エージェントの待機時間 (秒) です。 既定値は 300 秒です。  
  
 **-LoginTimeOut** *login_time_out_seconds*  
 ログインがタイムアウトになるまでの秒数です。既定値は **15** 秒です。  
  
 **-MaxBcpThreads** *number_of_threads*  
 並列実行できる一括コピーの操作数を指定します。 同時に存在するスレッドと ODBC 接続の最大数は、 **MaxBcpThreads** の値と、ディストリビューション データベースの同期トランザクションに示されている一括コピー要求の数の小さい方の値になります。 **MaxBcpThreads** は **0** よりも大きくする必要があり、上限はありません。 既定値は **1**です。  
  
 \- **MaxNetworkOptimization** [ **0**| **1**]  
 無関係な削除がサブスクライバーに送られたかどうかを示します。 無関係な削除とは、サブスクライバーのパーティションに属さない行に対する DELETE コマンドがサブスクライバーに送られたことを表します。 無関係な削除はデータの整合性や収束には影響しませんが、不要なネットワーク トラフィックを生じます。 **MaxNetworkOptimization** の既定値は **0**です。 **MaxNetworkOptimization** を **1** に設定すると、無関係な削除が発生する可能性が最小限に抑えられ、ネットワーク トラフィックが減少し、最もネットワークが最適化されます。 ただし、このパラメーターを **1** に設定するとメタデータの保存領域が増加するため、複数レベルの結合フィルターと複雑なサブセット フィルターが存在する場合、パブリッシャーのパフォーマンスが低下します。 レプリケーション トポロジを慎重に評価する必要があります。無関係な削除によるネットワーク トラフィックが容認できないほど大きい場合に限り、 **MaxNetworkOptimization** を **1** に設定してください。  
  
> [!NOTE]  
>  このパラメーターを **1** に設定することが役立つのは、マージ パブリケーションの同期最適化オプション ([sp_addmergepublication &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md) の **@keep_partition_changes** パラメーター) が **true** に設定されている場合のみです。  
  
 **-Output** *output_path_and_file_name*  
 エージェントの出力ファイルのパスです。 ファイル名が指定されていない場合、出力はコンソールに送られます。 指定された名前のファイルが存在する場合、出力はそのファイルに追加されます。  
  
 **-OutputVerboseLevel** [ **0**| **1**| **2**]  
 出力を詳細表示にするかどうかを指定します。  
  
|OutputVerboseLevel の値|説明|  
|------------------------------|-----------------|  
|**0**|エラー メッセージのみが記録されます。|  
|**1** (既定値)|すべての進行状況レポート メッセージが出力されます (既定)。|  
|**2**|すべてのエラー メッセージと進行状況レポート メッセージが出力されます。これはデバッグの際に役立ちます。|  
  
 **-PacketSize** *packet_size*  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]への接続中にスナップショット エージェントが使用するパケット サイズ (バイト) です。 既定値は 8,192 バイトです。  
  
> [!NOTE]  
>  パフォーマンスの向上が明確でない限り、パケット サイズは変更しないでください。 多くのアプリケーションでは、既定のパケット サイズが最適です。  
  
 **-ProfileName** *profile_name*  
 エージェント パラメーターに使用するエージェント プロファイルを指定します。 **ProfileName** が NULL の場合、このエージェント プロファイルは無効になります。 **ProfileName** を指定しない場合、エージェントの種類に応じた既定のプロファイルが使われます。 詳細については、「[レプリケーション エージェント プロファイル](../../../relational-databases/replication/agents/replication-agent-profiles.md)」を参照してください。  
  
 **-PublisherDB** *publisher_database*  
 パブリケーション データベースの名前です。 *このパラメーターは、Oracle パブリッシャーについてはサポートされません。*  
  
 **-PublisherDeadlockPriority** [**-1**|**0**|**1**]  
 デッドロックが発生した場合のパブリッシャーへのスナップショット エージェント接続の優先度です。 このパラメーターは、スナップショットの生成中にスナップショット エージェントとユーザー アプリケーション間で発生する可能性のあるデッドロックを解決するために指定します。  
  
|PublisherDeadlockPriority の値|説明|  
|-------------------------------------|-----------------|  
|**-1**|パブリッシャー側でデッドロックが発生した場合、スナップショット エージェント以外のアプリケーションが優先されます。|  
|**0** (既定値)|優先度は割り当てられません。|  
|**1**|パブリッシャー側でデッドロックが発生した場合、スナップショット エージェントが優先されます。|  
  
 **-PublisherFailoverPartner** *server_name*[**\\***instance_name*]  
 パブリケーション データベースとのデータベース ミラーリング セッションに参加する、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー パートナー インスタンスを指定します。 詳細については、「[データベース ミラーリングとレプリケーション &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)」を参照してください。  
  
 **-PublisherLogin** *publisher_login*  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用してパブリッシャーに接続するときに使用されるログインです。  
  
 **-PublisherPassword**  *publisher_password*  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用してパブリッシャーに接続するときに使用されるパスワードです。 」を参照してください。  
  
 **-PublisherSecurityMode** [ **0**| **1**]  
 パブリッシャーのセキュリティ モードを指定します。 値 **0** は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証モード (既定値) を示し、値 **1** は Windows 認証モードを示します。  
  
 **-QueryTimeOut** *query_time_out_seconds*  
 クエリがタイムアウトになるまでの秒数です。既定値は 1800 秒です。  
  
 **-ReplicationType** [ **1**| **2**]  
 レプリケーションの種類を指定します。 値 **1** はトランザクション レプリケーションを示し、値 **2** はマージ レプリケーションを示します。  
  
 **-RowDelimiter** *row_delimiter*  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 一括コピーで扱うデータ ファイルの各行の末尾を示す 1 文字または文字列です。 既定値は \n\<,@g>\n です。  
  
 **-StartQueueTimeout** *start_queue_timeout_seconds*  
 実行中の同時実行動的スナップショット処理のメンバー数が、[sp_addmergepublication &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md) の **@max_concurrent_dynamic_snapshots** プロパティの設定による制限に達している場合に、スナップショット エージェントの最大待機時間を秒単位で指定します。 最大秒数に達したときにスナップショット エージェントがまだ待機している場合、スナップショット エージェントは待機を終了します。 値が 0 の場合は、このエージェントが無期限に待機することを意味しますが、取り消すこともできます。  
  
 \- **UsePerArticleContentsView** *use_per_article_contents_view*  
 このパラメーターは推奨されません。旧バージョンとの互換性のためにサポートされています。  
  
## <a name="remarks"></a>解説  
  
> [!IMPORTANT]  
>  ドメイン ユーザー アカウント (既定値) ではなくローカル システム アカウントで実行するように [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェントをインストールした場合、サービスはローカル コンピューターにだけアクセスできます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェント下で実行するスナップショット エージェントで、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]へのログイン時に Windows 認証モードを使用するように構成すると、スナップショット エージェントは異常終了します。 既定の設定は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証です。  
  
 スナップショット エージェントを開始するには、コマンド プロンプトから **snapshot.exe** を実行します。 詳細については、「 [レプリケーション エージェント実行可能ファイルのプログラミング](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [レプリケーション エージェントの管理](../../../relational-databases/replication/agents/replication-agent-administration.md)  
  
  
