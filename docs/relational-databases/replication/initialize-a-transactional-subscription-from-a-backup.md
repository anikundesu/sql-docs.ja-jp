---
title: "バックアップからのトランザクション サブスクリプションの初期化 | Microsoft Docs"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: TSQL
helpviewer_keywords:
- manual subscription initialization [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], without snapshots
- transactional replication, backup and restore
- backups [SQL Server replication], transactional replication
ms.assetid: d0637fc4-27cc-4046-98ea-dc86b7a3bd75
caps.latest.revision: "36"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 28db06d71319802392246416ec6b6ce21c3974b6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="initialize-a-transactional-subscription-from-a-backup"></a>バックアップからのトランザクション サブスクリプションの初期化
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] トランザクション パブリケーションのサブスクリプションは通常、スナップショットを使用して初期化されますが、レプリケーション ストアド プロシージャを使用して、バックアップからサブスクリプションを初期化することもできます。 詳細については、「 [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)を使用して、サブスクリプションを手動で初期化する方法について説明します。  
  
### <a name="to-initialize-a-transactional-subscriber-from-a-backup"></a>トランザクション サブスクライバーをバックアップから初期化するには  
  
1.  既存のパブリケーションの場合は、パブリッシャーのパブリケーション データベースで [sp_helppublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) を実行して、バックアップから初期化する機能をパブリケーションがサポートしているかどうかを確認します。 結果セットの **allow_initialize_from_backup** の値を確認します。  
  
    -   この値が **1**の場合、パブリケーションはこの機能をサポートしています。  
  
    -   この値が **0** の場合、パブリッシャー側のパブリケーション データベースに対して [sp_changepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md) を実行します。 **@property** に **allow_initialize_from_backup** を、**@value** に **true** を指定します。  
  
2.  新しいパブリケーションの場合、パブリッシャー側のパブリケーション データベースに対して [sp_addpublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md) を実行します。 **allow_initialize_from_backup** には、 **true**を指定します。 詳細については、「 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)」をご覧ください。  
  
    > [!WARNING]  
    >  サブスクライバー データの欠落を回避するために、 **sp_addpublication** で `@allow_initialize_from_backup = N'true'`を使用する場合は、常に `@immediate_sync = N'true'`を使用します。  
  
3.  [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md) ステートメントを使用して、パブリケーション データベースのバックアップを作成します。  
  
4.  [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md) ステートメントを使用し、サブスクライバー上でバックアップを復元します。  
  
5.  パブリッシャー側のパブリケーション データベースに対して、ストアド プロシージャ [sp_addsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) を実行します。 次のパラメーターを指定します。  
  
    -   **@sync_type** - **initialize with backup**」をご覧ください。  
  
    -   **@backupdevicetype** - バックアップ デバイスの種類として、 **logical** (既定値)、 **disk**、 **tape**」をご覧ください。  
  
    -   **@backupdevicename** - 復元に使用する論理バックアップ デバイスまたは物理バックアップ デバイスを指定します。  
  
         論理デバイスの場合は、 **sp_addumpdevice** を使ってデバイスを作成する際に指定したバックアップ デバイスの名前を指定します。  
  
         物理デバイスの場合は、「 `DISK = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\BACKUP\Mybackup.dat'` 」または「 `TAPE = '\\.\TAPE0'`」のように、完全なパスとファイル名を指定します。  
  
    -   (省略可) **@password** - バックアップ セットの作成時に指定したパスワードを指定します。  
  
    -   (省略可) **@mediapassword** - メディア セットのフォーマット時に指定したパスワードを指定します。  
  
    -   (省略可) **@fileidhint** - 復元するバックアップ セットの識別子を指定します。 たとえば、 **1** はバックアップ メディアの 1 番目のバックアップ セットを示し、 **2** は 2 番目のバックアップ セットを示します。  
  
    -   (テープ デバイスの場合は省略可) **@unload** - 復元が完了した後にテープをドライブからアンロードする場合は **1** (既定値) を、テープをアンロードしない場合は **0** を指定します。  
  
6.  (省略可能) プル サブスクリプションの場合は、サブスクライバーのサブスクリプション データベースで [sp_addpullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md) と [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md) を実行します。 詳細については、「 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)」をご覧ください。  
  
7.  (省略可) ディストリビューション エージェントを起動します。 詳細については、「 [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) 」または「 [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [バックアップと復元によるデータベースのコピー](../../relational-databases/databases/copy-databases-with-backup-and-restore.md)   
 [SQL Server データベースのバックアップと復元](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
  
