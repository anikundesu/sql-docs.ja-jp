---
title: "managed_backup.sp_ backup_master_switch (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_ backup_master_switch
- smart_admin.sp_ backup_master_switch
- sp_ backup_master_switch_TSQL
- smart_admin.sp_ backup_master_switch_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sp_ backup_master_switch
- smart_admin.sp_ backup_master_switch
ms.assetid: 1ed2b2b2-c897-41cc-bed5-1c6bc47b9dd2
caps.latest.revision: "12"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0d7567235212388b477abcbfddca8049f2ada735
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="managedbackupsp-backupmasterswitch-transact-sql"></a>managed_backup.sp_ backup_master_switch (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  一時停止または再開、[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]です。  
  
 使用してこのストアド プロシージャを一時的に停止し、それらの再開[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]です。 これにより、すべての構成設定はそのまま保持され、サービスの再開時にもその設定は維持されています。 ときに[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]が一時停止して、保有期間は適用されません。 つまり、ファイルをストレージから削除する必要があるかどうか、またはバックアップ ファイルが壊れていたりログ チェーンが分断されたりしているかどうかがチェックされることはありません。  
  

  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```tsql  
EXEC managed_backup.sp_backup_master_switch   
                     [@state = ] { 0 | 1}  
```  
  
##  <a name="Arguments"></a> 引数  
 @state  
 状態を設定[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]です。 @stateパラメーターは**ビット**です。 値を 0 に設定した場合は操作が一時停止し、値を 1 に設定した場合は操作が再開されます。  
  
## <a name="return-code-value"></a>リターン コード値  
 0 (成功) または 1 (失敗)  
  
## <a name="security"></a>セキュリティ  
 このステートメントに関連したセキュリティの問題について説明します。サブセクション (H3 見出し) として「権限」を含めます。 必要に応じて、組み合わせ所有権や監査に関する他のサブセクションを含めることを検討してください。  
  
### <a name="permissions"></a>Permissions  
 メンバーシップが必要**db_backupoperator**データベース ロール、 **ALTER ANY CREDENTIAL**アクセス許可、および**EXECUTE**に対するアクセス許可**sp_deletebackuphistory**ストアド プロシージャです。  
  
## <a name="examples"></a>使用例  
 次の例を使用すると、[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]を、そのバックアップが実行されているインスタンス上で一時停止できます。  
  
```  
Use msdb;  
GO  
EXEC managed_backup.sp_master_switch @state=0;  
Go  
  
```  
  
 次の例を使用すると、[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]を再開できます。  
  
```  
Use msdb;  
GO  
EXEC managed_backup.sp_master_switch @state=1;  
Go  
  
```  
  
## <a name="see-also"></a>参照  
 [Microsoft Azure への SQL Server マネージ バックアップ](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)  
  
  
