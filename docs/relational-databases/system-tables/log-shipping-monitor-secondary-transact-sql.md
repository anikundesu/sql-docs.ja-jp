---
title: "log_shipping_monitor_secondary (TRANSACT-SQL) |Microsoft ドキュメント"
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
- log_shipping_monitor_secondary_TSQL
- log_shipping_monitor_secondary
dev_langs: TSQL
helpviewer_keywords: log_shipping_monitor_secondary system table
ms.assetid: afbe1bb7-89a7-4020-9408-0af64a043c2e
caps.latest.revision: "22"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 913796ba13f2440b511ee036a9d9b8e8e67c1bfb
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="logshippingmonitorsecondary-transact-sql"></a>log_shipping_monitor_secondary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  各ログ配布構成内のセカンダリ データベースごとに、1 つの監視レコードを格納します。 次の表は、 **msdb**データベース。  
  
 履歴や監視に関するテーブルは、プライマリ サーバーとセカンダリ サーバーでも使用されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**secondary_server**|**sysname**|セカンダリ インスタンスの名前、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]ログ配布構成にします。|  
|**secondary_database**|**sysname**|ログ配布構成におけるセカンダリ データベースの名前。|  
|**secondary_id**|**uniqueidentifier**|ログ配布構成におけるセカンダリ サーバーの ID。|  
|**primary_server**|**sysname**|ログ配布構成における [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のプライマリ インスタンスの名前。|  
|**primary_database**|**sysname**|ログ配布構成におけるプライマリ データベースの名前。|  
|**restore_threshold**|**int**|復元操作が始まってから警告が生成されるまでの許容経過時間 (分単位)。|  
|**threshold_alert**|**int**|復元のしきい値を超えたときに発生する警告。|  
|**threshold_alert_enabled**|**bit**|復元のしきい値の警告を有効にするかどうか。 1 = 有効にします。<br /><br /> 0 = 無効。|  
|**last_copied_file**|**nvarchar (500)**|セカンダリ サーバーにコピーされた最後のバックアップ ファイルの名前。|  
|**last_copied_date**|**datetime**|セカンダリ サーバーに対して最後にコピー操作を行った日時。|  
|**last_copied_date_utc**|**datetime**|セカンダリ サーバーに対して最後にコピー操作を行った日時。協定世界時 (UTC) で表されます。|  
|**last_restored_file**|**nvarchar (500)**|セカンダリ データベースに復元された最後のバックアップ ファイルの名前。|  
|**last_restored_date**|**datetime**|セカンダリ データベースに対して最後に復元操作を行った日時。|  
|**last_restored_date_utc**|**datetime**|セカンダリ データベースに対して最後に復元操作を行った日時。協定世界時 (UTC) で表されます。|  
|**last_restored_latency**|**int**|ログ バックアップがプライマリで作成されてからセカンダリで復元されるまでの経過時間 (分単位)。<br /><br /> 初期値は NULL です。|  
|**ヒストリは削除**|**int**|指定したセカンダリ データベースでログ配布履歴レコードが保持される時間 (分単位)。この時間を過ぎるとレコードは削除されます。|  
  
## <a name="remarks"></a>解説  
 リモート監視サーバーに格納されているだけでなくなるとセカンダリ サーバーでセカンダリ サーバーに関連する情報が格納されているもの**log_shipping_monitor_secondary**テーブル。  
  
## <a name="see-also"></a>参照  
 [ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_refresh_log_shipping_monitor &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql.md)   
 [sp_add_log_shipping_secondary_database &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql.md)   
 [sp_change_log_shipping_secondary_database &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-change-log-shipping-secondary-database-transact-sql.md)   
 [sp_delete_log_shipping_secondary_database &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql.md)   
 [sp_help_log_shipping_secondary_database &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-database-transact-sql.md)   
 [sp_help_log_shipping_monitor_secondary &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-secondary-transact-sql.md)   
 [sp_refresh_log_shipping_monitor &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql.md)   
 [システム テーブルと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
