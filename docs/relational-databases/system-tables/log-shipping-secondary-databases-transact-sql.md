---
title: "log_shipping_secondary_databases (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- log_shipping_secondary_databases_TSQL
- log_shipping_secondary_databases
dev_langs: TSQL
helpviewer_keywords: log_shipping_secondary_databases system table
ms.assetid: ba2374af-86b8-480c-a10c-51e7c4e3ae23
caps.latest.revision: "19"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 60237602284820c646513b0ff6d8c1fcc8002cce
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="logshippingsecondarydatabases-transact-sql"></a>log_shipping_secondary_databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  各ログ配布構成内のセカンダリ データベースごとに、1 つのレコードを格納します。 次の表は、 **msdb**データベース。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**secondary_database**|**sysname**|ログ配布構成におけるセカンダリ データベースの名前。|  
|**secondary_id**|**uniqueidentifier**|ログ配布構成におけるセカンダリ サーバーの ID。|  
|**restore_delay**|**int**|指定されたバックアップ ファイルを復元するまでセカンダリ サーバーが待機する時間 (分単位)。 既定値は、0 分です。|  
|**restore_all**|**bit**|場合は、復元ジョブを実行すると、1、セカンダリ サーバーに設定はすべてのトランザクション ログ バックアップを復元します。 1 以外に設定すると、セカンダリ サーバーは 1 つのファイルが復元された後で停止します。|  
|**restore_mode**|**bit**|セカンダリ データベースの復元モードを指定します。<br /><br /> 0 = NORECOVERY でログを復元します。<br /><br /> 1 = STANDBY でログを復元します。|  
|**disconnect_users**|**bit**|1 に設定、ユーザー接続が切断されます、セカンダリ データベースから復元操作を実行するとします。 既定値 0 を = です。|  
|**block_size**|**int**|バックアップ デバイスのブロック サイズに使用されるサイズ (バイト単位)。|  
|**buffer_count**|**int**|バックアップまたは復元操作で使用されるバッファーの総数。|  
|**max_transfer_size**|**int**|サイズをバイト単位の最大入力または出力要求によって発行されたで[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]バックアップ デバイスにします。|  
|**last_restored_file**|**nvarchar (500)**|セカンダリ データベースに復元された最後のバックアップ ファイルの名前。|  
|**last_restored_date**|**datetime**|セカンダリ データベースに対して最後に復元操作を行った日時。|  
  
## <a name="see-also"></a>参照  
 [ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_add_log_shipping_secondary_database &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql.md)   
 [sp_delete_log_shipping_secondary_database &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql.md)   
 [sp_help_log_shipping_secondary_database &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-database-transact-sql.md)   
 [log_shipping_secondary &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/log-shipping-secondary-transact-sql.md)   
 [システム テーブルと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
