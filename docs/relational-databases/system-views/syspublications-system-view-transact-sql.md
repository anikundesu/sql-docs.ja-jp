---
title: "syspublications (システム ビュー) (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- syspublications
- syspublications_TSQL
dev_langs: TSQL
helpviewer_keywords: syspublications view
ms.assetid: e5f57c32-efc0-4455-a74f-684dc2ae51f8
caps.latest.revision: "20"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: afd6e57ed8c17dc74b24320808e8502a679bf152
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="syspublications-system-view-transact-sql"></a>syspublications (システム ビュー) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Syspublications**ビューはパブリケーション情報を公開します。 このビューは、ディストリビューション データベースに保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**説明**|**nvarchar (255)**|パブリケーションの説明エントリします。|  
|**name**|**sysname**|パブリケーションに関連付けられた一意な名前。|  
|**pubid**|**int**|パブリケーションの一意な ID を示す ID 列。|  
|**repl_freq**|**tinyint**|レプリケーションの頻度。<br /><br /> **0** = トランザクション ベース (トランザクション)。<br /><br /> **1**テーブルの定期更新 (スナップショット) を = です。|  
|**ステータス**|**tinyint**|パブリケーションの状態。<br /><br /> **0** = 非アクティブです。<br /><br /> **1**アクティブを = です。|  
|**sync_method**|**tinyint**|同期方法。<br /><br /> **0** = ネイティブな一括コピー プログラム ユーティリティ (BCP)。<br /><br /> **1** = キャラクター BCP。<br /><br /> **3** = 同時実行は、ネイティブ BCP が使用されますが、スナップショット時に、テーブルはロックされていないことを意味します。<br /><br /> **4** = Concurrent_c 文字 BCP が使用されますが、テーブルが、スナップショット時にロックされていないことを意味します。|  
|**snapshot_jobid**|**binary (16)**|初期スナップショットの生成が予定されているエージェント ジョブの識別子。|  
|**independent_agent**|**bit**|このパブリケーションに対して、スタンドアロンのディストリビューション エージェントがあるかどうかを示します。<br /><br /> **0** = パブリケーションでは共有ディストリビューション エージェントを使用して、パブリッシャー データベース/サブスクライバー データベースの各ペアが 1 つの共有エージェントです。<br /><br /> **1** = このパブリケーション用のスタンドアロン ディストリビューション エージェントが存在します。|  
|**immediate_sync**|**bit**|同期ファイルが作成またはスナップショット エージェントを実行するたびに再作成するかどうかを示す、 **1**が作成されるたびにエージェントが実行されることを意味します。|  
|**enabled_for_internet**|**bit**|パブリケーションの同期ファイルがファイル転送プロトコル (FTP) やその他のサービスを介してインターネットに公開されるかどうかを示します、 **1**インターネットからアクセスできることを意味します。|  
|**allow_push**|**bit**|パブリケーションに対してプッシュ サブスクリプションを許可するかどうかを示す、 **1**が許可されていることを意味します。|  
|**allow_pull**|**bit**|パブリケーションに対してプル サブスクリプションを許可するかどうかを示す、 **1**が許可されていることを意味します。|  
|**allow_anonymous**|**bit**|パブリケーションに対して匿名サブスクリプションを許可するかどうかを示す、 **1**が許可されていることを意味します。|  
|**immediate_sync_ready**|**bit**|スナップショットがスナップショット エージェントによって生成されたかどうか、および新しいサブスクリプションで使用できるかどうかを示します。 即時更新パブリケーションでのみ意味を持ちます。 **1**スナップショット準備ができていることを示します。|  
|**allow_sync_tran**|**bit**|パブリケーションでサブスクリプションの即時更新を許可するかどうかを示します。 **1**即時更新サブスクリプションが許可されることを意味します。|  
|**autogen_sync_procs**|**bit**|即時更新サブスクリプションの同期ストアド プロシージャがパブリッシャーで生成されるかどうかを示します。 **1**パブリッシャー側で生成されることを意味します。|  
|**保有期間**|**int**|パブリケーションへの変更をディストリビューション データベースに保存する期間 (時間単位)。|  
|**allow_queued_tran**|**bit**|変更をパブリッシャーで適用できるようになるまで、サブスクライバーで変更をキューに保持するかどうかを示します。 場合**1**、サブスクライバーの変更はキューに格納します。|  
|**snapshot_in_defaultfolder**|**bit**|スナップショット ファイルは既定のフォルダーに格納されているかどうかを指定します。 場合**0**、スナップショット ファイルで指定された代替位置に格納されている*alternate_snapshot_folder*です。 1 の場合、スナップショット ファイルは既定のフォルダーに格納されます。|  
|**alt_snapshot_folder**|**nvarchar(510)**|スナップショットの代替フォルダーの場所を指定します。|  
|**pre_snapshot_script**|**nvarchar(510)**|ポインターを指定します、 **.sql**ファイルの場所。 ディストリビューション エージェントは、サブスクライバー側でスナップショットを適用するとき、レプリケートされたオブジェクト スクリプトより前に、プリスナップショット スクリプトを実行します。|  
|**post_snapshot_script**|**nvarchar(510)**|ポインターを指定します、 **.sql**ファイルの場所。 ディストリビューション エージェントは、最初の同期中、他のすべてのレプリケートされたオブジェクト スクリプトとデータが適用された後に、ポストスナップショット スクリプトを実行します。|  
|**compress_snapshot**|**bit**|指定に書き込まれたスナップショット、 *alt_snapshot_folder*の場所を圧縮するには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] CAB 形式です。 **1**スナップショットが圧縮されることを意味します。|  
|**ftp_address**|**sysname**|ディストリビューター用 FTP サービスのネットワーク アドレス。 ディストリビューション エージェントが受け取るパブリケーション スナップショット ファイルの場所を示します。|  
|**ftp_port**|**int**|ディストリビューター用 FTP サービスのポート番号。 ディストリビューション エージェントが受け取るパブリケーション スナップショット ファイルの場所を指定します。|  
|**ftp_subdirectory**|**nvarchar(510)**|スナップショット ファイルは、パブリケーションが FTP を使用してスナップショットの配布をサポートしている場合に、ディストリビューション エージェントの使用可能な場所を指定します。|  
|**ftp_login**|**nvarchar (256)**|FTP サービスへの接続に使用されるユーザー名。|  
|**ftp_password**|**nvarchar(1048)**|FTP サービスへの接続に使用されるユーザー パスワード。|  
|**allow_dts を含む**|**bit**|パブリケーションで、[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] データ変換サービス (DTS) による変換を許可するかどうか。 **1** DTS 変換が許可されていることを指定します。|  
|**allow_subscription_copy**|**bit**|パブリケーションにサブスクライブするサブスクリプション データベースをコピーする機能が有効かどうかを示します。 **1**コピーが許可されていることを意味します。|  
|**centralized_conflicts**|**bit**|競合レコードがパブリッシャーに格納されるかどうかを示します。<br /><br /> **0** = 競合レコードは、パブリッシャーの両方と、競合の原因となったサブスクライバーで格納します。<br /><br /> **1** = 競合レコードはパブリッシャーに保存します。|  
|**conflict_retention**|**int**|競合レコードの保有期間の日数。|  
|**conflict_policy**|**int**|キュー更新サブスクライバー オプションを使用するときの競合の解決方法。 これらの値のいずれかを指定できます。<br /><br /> **1** = パブリッシャー優先します。<br /><br /> **2** = サブスクライバー優先します。<br /><br /> **3** = サブスクリプションを再初期化します。|  
|**queue_type**|**int**|使用されるキューの種類。 これらの値のいずれかを指定できます。<br /><br /> **1** = を使用して msmq。[!INCLUDE[msCoName](../../includes/msconame-md.md)]メッセージ キューがトランザクションを格納します。<br /><br /> **2** = を使用して .sql[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]トランザクションを格納します。<br /><br /> 注: を使用して[!INCLUDE[msCoName](../../includes/msconame-md.md)]メッセージ キューは廃止されており、現在サポートされていません。|  
|**ad_guidname**|**sysname**|パブリケーションがパブリッシュされるかどうかを指定します、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory です。 有効なグローバル一意識別子 (GUID) の場合、パブリケーションが Active Directory でパブリッシュされることを示します。また GUID が、対応する Active Directory パブリケーション オブジェクトの objectGUID であることを示します。 NULL の場合、パブリケーションは Active Directory にパブリッシュされません。<br /><br /> 注: Active Directory への発行がサポートされていません。|  
|**backward_comp_level**|**int**|データベースの互換性レベル。次のいずれかの値になります。<br /><br /> **90** = [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].<br /><br /> **100** = [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].|  
|**allow_initialize_from_backup**|**bit**|サブスクライバーが初期スナップショットではなく、バックアップから、このパブリケーションに対するサブスクリプションを初期化できるかどうかを示します。 **1**をバックアップからサブスクリプションを初期化できることを意味し、 **0**できないことを意味します。 詳細については、「 [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)を使用して、サブスクリプションを手動で初期化する方法について説明します。|  
|**min_autonosync_lsn**|**binary(1)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**replicate_ddl**|**int**|パブリケーションに対してスキーマ レプリケーションがサポートされているかどうかを示します。<br /><br /> **1** = DDL ステートメントがパブリッシャーで実行がレプリケートされます。<br /><br /> **0** = DDL ステートメントがレプリケートされないことを示します。 詳細については、「[パブリケーション データベースでのスキーマの変更](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)」を参照してください。|  
|**オプション**|**int**|追加のパブリッシング オプションを指定するビットマップ。ビットごとのオプション値は次のようになります。<br /><br /> **0x1** - ピア ツー ピア レプリケーションに対して有効です。<br /><br /> **0x2** -ピア ツー ピア レプリケーションに対してローカル変更のみをパブリッシュします。<br /><br /> **0x4** - に対して有効ではない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクライバーです。<br /><br /> **0x8** - ピア ツー ピア競合検出に対して有効です。|  
|**originator_id**|**smallint**|競合検出のためにピア ツー ピア レプリケーション トポロジの各ノードを識別します。 詳細については、「 [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)」を参照してください。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_addpublication &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)   
 [sp_changepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)   
 [sp_helppublication &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md)  
  
  
