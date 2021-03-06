---
title: "sys.dm_hadr_availability_replica_states (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_hadr_availability_replica_states
- sys.dm_hadr_availability_replica_states_TSQL
- sys.dm_hadr_availability_replica_states
- dm_hadr_availability_replica_states_TSQL
dev_langs: TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.dm_hadr_availability_replica_states dynamic management view
ms.assetid: d2e678bb-51e8-4a61-b223-5c0b8d08b8b1
caps.latest.revision: "65"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: bf08e1c4aa40e78f9a6e3cb345aff501804d5736
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmhadravailabilityreplicastates-transact-sql"></a>sys.dm_hadr_availability_replica_states (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  同じ Always On 可用性グループ、ローカルのレプリカとしてのローカル レプリカごとに行と、各リモート レプリカの行を返します。 各行には、特定のレプリカの状態に関する情報が含まれています。  
  
> [!IMPORTANT]  
>  特定の可用性グループのすべてのレプリカに関する情報を取得するクエリ**sys.dm_hadr_availability_replica_states**がプライマリ レプリカをホストするサーバー インスタンスでします。 可用性グループのセカンダリ レプリカをホストしているサーバー インスタンスに対してクエリを実行した場合、この動的管理ビューはその可用性グループのローカル情報のみを返します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**replica_id**|**uniqueidentifier**|レプリカの一意の識別子。|  
|**group_id**|**uniqueidentifier**|可用性グループの一意識別子。|  
|**is_local**|**bit**|レプリカがローカルかどうかのいずれか。<br /><br /> 0 = プライマリ レプリカがローカル サーバー インスタンスでホストされている可用性グループ内のリモート セカンダリ レプリカを示します。 この値が表示されるのは、プライマリ レプリカの場所だけです。<br /><br /> 1 = ローカル レプリカを示します。 セカンダリ レプリカの場合、これはそのレプリカが属する可用性グループに対して使用できる唯一の値です。|  
|**ロール**|**tinyint**|現在[!INCLUDE[ssHADR](../../includes/sshadr-md.md)]ローカル レプリカまたは接続のリモート レプリカの 1 つのロール。<br /><br /> 0 = 解決中<br /><br /> 1 = プライマリ<br /><br /> 2 = セカンダリ<br /><br /> [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] のロールについては、「[Always On 可用性グループの概要 &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)」を参照してください。|  
|**role_desc**|**nvarchar (60)**|説明**ロール**,、1 つの。<br /><br /> RESOLVING<br /><br /> PRIMARY<br /><br /> SECONDARY|  
|**operational_state**|**tinyint**|いずれかのレプリカの現在の操作状態:<br /><br /> 0 = フェールオーバー保留<br /><br /> 1 = 保留中<br /><br /> 2 = オンライン<br /><br /> 3 = オフライン<br /><br /> 4 = 失敗<br /><br /> 5 = 失敗、クォーラムなし<br /><br /> NULL = レプリカがローカルでない<br /><br /> 詳細については、次を参照してください。[ロールと操作状態](#RolesAndOperationalStates)、このトピックで後述します。|  
|**運用\_状態\_desc**|**nvarchar (60)**|説明**運用\_状態**,、1 つの。<br /><br /> PENDING_FAILOVER<br /><br /> PENDING<br /><br /> ONLINE<br /><br /> OFFLINE<br /><br /> FAILED<br /><br /> FAILED_NO_QUORUM<br /><br /> NULL|  
|**回復\_ヘルス**|**tinyint**|ロールアップ、**データベース\_状態**の列、 [sys.dm_hadr_database_replica_states](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md)動的管理ビュー。 使用可能な値とその説明を次に示します。<br /><br /> 0: 進行中です。  少なくとも 1 つの参加データベースがオンライン以外のデータベースの状態 (**データベース\_状態**が 0 ではありません)。<br /><br /> 1: オンラインです。 すべての参加データベースがオンラインのデータベースの状態にある (**database_state**は 0) です。<br /><br /> Null を返します**is_local** = 0。|  
|**recovery_health_desc**|**nvarchar (60)**|説明**recovery_health**,、1 つの。<br /><br /> ONLINE_IN_PROGRESS<br /><br /> ONLINE<br /><br /> NULL|  
|**同期\_ヘルス**|**tinyint**|データベースの同期状態のロールアップが反映されます (**synchronization_state**) すべての可用性データベースを参加 (とも呼ばれる*レプリカ*) とレプリカ (可用性モード同期コミット モードまたは非同期コミット モード)。 ロールアップ状態が反映されます少なくとも正常累積、データベース レプリカでします。 使用可能な値とその説明のとおりです。<br /><br /> 0: 正常ではありません。   少なくとも 1 つの参加データベースが NOT SYNCHRONIZING 状態です。<br /><br /> 1: 部分的に正常な状態です。 一部のレプリカが目標の同期状態ではありません: 同期コミット レプリカは SYNCHRONIZED である必要があり、非同期コミット レプリカは SYNCHRONIZING である必要があります。<br /><br /> 2: 正常な状態です。 すべてのレプリカが目標の同期状態です: 同期コミット レプリカは SYNCHRONIZED であり、非同期コミット レプリカは SYNCHRONIZING です。|  
|**synchronization_health_desc**|**nvarchar (60)**|説明**synchronization_health**,、1 つの。<br /><br /> NOT_HEALTHY<br /><br /> PARTIALLY_HEALTHY<br /><br /> HEALTHY|  
|**connected_state**|**tinyint**|セカンダリ レプリカが現在接続しているか、プライマリ レプリカにします。 使用可能な値は、その説明を以下に示します。<br /><br /> 0: 切断します。 切断された状態への可用性レプリカの応答は、そのロールによって異なりますプライマリ レプリカでセカンダリ レプリカが切断されている場合、セカンダリ データベースはマーク セカンダリを待って、プライマリ レプリカに同期されていない。再接続します。切断されていることを検出すると、セカンダリ レプリカでセカンダリ レプリカはプライマリ レプリカに再接続しようとします。<br /><br /> 1: 接続されています。<br /><br /> 各プライマリ レプリカでは、同じ可用性グループに含まれるすべてのセカンダリ レプリカの接続状態を追跡します。 セカンダリ レプリカでは、プライマリ レプリカの接続状態のみを追跡します。|  
|**connected_state_desc**|**nvarchar (60)**|説明**connection_state**,、1 つの。<br /><br /> DISCONNECTED<br /><br /> CONNECTED|  
|**last_connect_error_number**|**int**|最後の接続エラーの番号。|  
|**last_connect_error_description**|**nvarchar (1024)**|テキスト、 **last_connect_error_number**メッセージ。|  
|**last_connect_error_timestamp**|**datetime**|いつかを示す日付と時刻のタイムスタンプ、 **last_connect_error_number**エラーが発生しました。|  
  
##  <a name="RolesAndOperationalStates"></a>ロールと操作状態  
 役割、**ロール**、特定の可用性レプリカの状態と動作の状態を反映**operational_state**レプリカはすべてのクライアント要求を処理する準備ができているかどうかについて説明します、可用性レプリカのデータベースです。 各ロールの可能なオペレーション状態の概要を次に示します: 解決して、プライマリ、およびセカンダリ。  
  
 **RESOLVING:**運用状態には、次の表に示すように可用性レプリカが RESOLVING ロールの場合は、します。  
  
|動作状態|Description|  
|-----------------------|-----------------|  
|PENDING_FAILOVER|可用性グループに対するフェールオーバー コマンドを処理しています。|  
|OFFLINE|WSFC クラスターおよびローカル メタデータ内の可用性レプリカのすべての構成データが更新されたが、可用性グループには現在プライマリ レプリカがありません。|  
|FAILED|WSFC クラスターから情報を取得しようとして、読み取りエラーが発生しました。|  
|FAILED_NO_QUORUM|ローカルの WSFC ノードに、クォーラムがありません。 これは、推論された状態です。|  
  
 **PRIMARY:**可用性レプリカがプライマリ ロールを実行してが現在プライマリ レプリカであります。 運用状態には、次の表に示すようにします。  
  
|動作状態|Description|  
|-----------------------|-----------------|  
|PENDING|これは一時的な状態ですが、ワーカーを使用して要求を処理できない場合、プライマリ レプリカがこの状態になることがあります。|  
|ONLINE|可用性グループ リソースがオンラインになっており、すべてのデータベース ワーカー スレッドが選択されました。|  
|FAILED|可用性レプリカは、WSFC クラスターに対して読み取りまたは書き込みを行うことができません。|  
  
 **SECONDARY:**セカンダリ レプリカが現在可用性レプリカがセカンダリ ロールを実行する、ときにします。 運用状態には次の表に示すようにします。  
  
|動作状態|Description|  
|-----------------------|-----------------|  
|ONLINE|ローカル セカンダリ レプリカがプライマリ レプリカに接続されています。|  
|FAILED|ローカル セカンダリ レプリカが WSFC クラスターに対して読み取りまたは書き込みを行うことができません。|  
|NULL|プライマリ レプリカでは、行がセカンダリ レプリカに関係する場合に、この値が返されます。|  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>Permissions  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [可用性グループの監視 &#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)  
  
  
