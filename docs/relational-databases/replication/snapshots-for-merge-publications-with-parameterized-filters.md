---
title: "パラメーター化されたフィルターを使用したマージ パブリケーションのスナップショット | Microsoft Docs"
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
- parameterized filters [SQL Server replication], snapshots
- snapshots [SQL Server replication], parameterized filters and
- filters [SQL Server replication], parameterized
- merge replication [SQL Server replication], initializing subscriptions
- initializing subscriptions [SQL Server replication], snapshots
ms.assetid: 99d7ae15-5457-4ad4-886b-19c17371f72c
caps.latest.revision: "37"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 83e1c3bcb6cc4a435f3db4b3e96812a0c308c8b9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="snapshots-for-merge-publications-with-parameterized-filters"></a>パラメーター化されたフィルターを使用したマージ パブリケーションのスナップショット
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] パラメーター化された行フィルターがマージ パブリケーションで使用される場合、レプリケーションは 2 つの要素から成るスナップショットを持つ各サブスクリプションを初期化します。 まず、レプリケーションに必要なすべてのオブジェクトとパブリッシュされたオブジェクトのスキーマが含まれるスキーマ スナップショットが作成されます。ただしデータは含まれません。 次に、スキーマ スナップショットからのオブジェクトとスキーマが含まれるスナップショットと、サブスクリプションのパーティションに属するデータを使用して、各サブスクリプションが初期化されます。 複数のサブスクリプションが特定のパーティションを受信する場合 (つまり、同じスキーマとデータを受信する場合)、そのパーティションのスナップショットは 1 回しか作成されません。複数のサブスクリプションは、同じスナップショットから初期化されます。 パラメーター化された行フィルターの詳細については、「 [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)」を参照してください。  
  
 次の 3 つの方法のいずれかで、パラメーター化されたフィルターを使用して、パブリケーションのスナップショットを作成できます。  
  
-   各パーティションのスナップショットを事前に生成します。 このオプションを使用すると、スナップショットが生成されたときに制御できます。  
  
     スナップショットがスケジュールに従って更新されるように選択することもできます。 スナップショットの作成対象となったパーティションをサブスクライブする新しいサブスクライバーは、最新のスナップショットを受信します。  
  
-   サブスクライバーが初めて同期されたときに、スナップショットの生成と適用を要求できるようにします。 このオプションを使用すると、新しいサブスクライバーは管理者の介入を必要としないで同期できます (スナップショットを生成するには[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントがパブリッシャーで実行されている必要があります)。  
  
    > [!NOTE]  
    >  パブリケーション内の 1 つ以上のアーティクルにフィルターを適用して、各サブスクリプション固有の重複しないパーティションが得られる場合、マージ エージェントが実行されるたびにメタデータがクリーンアップされます。 これは、パーティション スナップショットの有効期間が短時間で切れてしまうことを意味します。 このオプションを使用する場合は、サブスクライバーに対してスナップショットの生成と配信を許可することを検討する必要があります。 フィルター オプションの詳細については、「 [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)」を参照してください。  
  
-   スナップショット エージェントを使用して、手動で各サブスクライバーのスナップショットを生成します。 サブスクライバーは、マージ エージェントが正しいスナップショットを取得および適用できるように、スナップショットの場所をマージ エージェントに提供する必要があります。  
  
    > [!NOTE]  
    >  このオプションは、旧バージョンとの互換性のためにサポートされており、FTP スナップショット共有を使用できません。  
  
 最も柔軟性の高い方法は、事前に生成され、サブスクライバーに要求されるスナップショット オプションの組み合わせを使用することです。スナップショットは、スケジュールに基づいて (通常はオフピーク時に) 事前生成および更新されますが、新しいパーティションを必要とするサブスクリプションが作成された場合は、サブスクライバーが独自のスナップショットを生成できます。  
  
 各店舗に在庫を配送する移動営業部署のある [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)]について考えてみましょう。 各営業担当者は、各自のログインに基づいてサブスクリプションを受信し、各自が担当する店舗についてのデータを取得します。 管理者は、スナップショットを事前に生成し、毎週日曜日に更新するように選択しています。 場合によっては、新しいユーザーがシステムに追加され、スナップショットを使用できないパーティションのデータが必要になります。 管理者の選択により、サブスクライバーが開始するスナップショットで、スナップショットがまだ使用できないためにサブスクライバーがパブリケーションをサブスクライブできない状況を回避することもできます。 新しいサブスクライバーが初めて接続すると、指定されたパーティションに対してスナップショットが生成され、サブスクライバーで適用されます (スナップショットを生成できるようにするには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントがパブリッシャーで実行されている必要があります)。  
  
 パラメーター化されたフィルターを使用してパブリケーションのスナップショットを作成するには、「 [Create a Snapshot for a Merge Publication with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)」を参照してください。  
  
## <a name="security-settings-for-the-snapshot-agent"></a>スナップショット エージェントに対するセキュリティの設定  
 スナップショット エージェントは各パーティションのスナップショットを作成します。 事前に生成されるスナップショットとサブスクライバーによって要求されるスナップショットの場合、エージェントが実行され、パブリケーションのスナップショット エージェント ジョブ作成時に指定された資格情報に基づいて接続が作成されます (このジョブは、パブリケーションの新規作成ウィザードまたは **sp_addpublication_snapshot**によって作成されます)。 資格情報を変更するには、 **sp_changedynamicsnapshot_job**を使用します。 詳しくは、「[sp_changedynamicsnapshot_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedynamicsnapshot-job-transact-sql.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [スナップショットを使用したサブスクリプションの初期化](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)   
 [スナップショット フォルダーのセキュリティ保護](../../relational-databases/replication/security/secure-the-snapshot-folder.md)  
  
  
