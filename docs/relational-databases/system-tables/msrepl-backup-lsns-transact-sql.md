---
title: "MSrepl_backup_lsns (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- MSrepl_backup_lsns_TSQL
- MSrepl_backup_lsns
dev_langs: TSQL
helpviewer_keywords: MSrepl_backup_Isns system table
ms.assetid: de06c349-82a8-48c6-b602-b5d6938514f6
caps.latest.revision: "18"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e7d73641645963ed6a136cc2fe5028abc63642a2
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="msreplbackuplsns-transact-sql"></a>MSrepl_backup_lsns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSrepl_backup_lsns**テーブルには、ディストリビューション データベースの"sync with backup"オプションをサポートするためのトランザクション ログ シーケンス番号 (LSN) が含まれています。 このテーブルは、ディストリビューション データベースに保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**化コ**|**int**|パブリッシャー データベースの ID。|  
|**valid_xact_id**|**varbinary (16)**|ログの切り捨て位置にマークを付けるため、パブリッシャーに送られるトランザクションの ID。 ディストリビューション データベースが "sync with backup" モードの場合のみ使用されます。 バックアップされたディストリビューション データベース内の、最新のレプリケートされたトランザクションの ID に相当します。 ログの切り捨て位置にマークを付けるために、ログ リーダーによってパブリッシャーに送られます。|  
|**valid_xact_seqno**|**varbinary (16)**|ログの切り捨て位置にマークを付けるために、パブリッシャーに送られるトランザクションのシーケンス番号。 ディストリビューション データベースが "sync with backup" モードの場合にのみ使用されます。 バックアップされたディストリビューション データベース内の、最新のレプリケートされたトランザクションのログ シーケンス番号に相当します。 ログの切り捨て位置にマークを付けるために、ログ リーダーによってパブリッシャーに送られます。|  
|**next_xact_id**|**varbinary (16)**|バックアップ操作で使用する一時的なログ シーケンス番号。|  
|**nextx_xact_seqno**|**varbinary (16)**|バックアップ操作で使用する一時的なログ シーケンス番号。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
