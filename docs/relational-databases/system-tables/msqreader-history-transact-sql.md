---
title: "MSqreader_history (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- MSqreader_history
- MSqreader_history_TSQL
dev_langs: TSQL
helpviewer_keywords: MSqreader_history system table
ms.assetid: c5c91d39-513c-4a77-870b-c8ef74a1cd6b
caps.latest.revision: "15"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7c9615bb702c89d8b2a5be0087671df9d8a6a910
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="msqreaderhistory-transact-sql"></a>MSqreader_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSqreader_history**ローカル ディストリビューターに関連付けられているキュー リーダー エージェントの履歴行を保持します。 このテーブルは、ディストリビューション データベースに保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|キュー リーダー エージェントの ID|  
|**publication_id**|**int**|パブリケーションの ID。|  
|**runstatus**|**int**|エージェントの実行状態。<br /><br /> **1** = 開始します。<br /><br /> **2** = 成功します。<br /><br /> **3** = 実行中です。<br /><br /> **4** = アイドル状態です。<br /><br /> **5** = 再試行します。<br /><br /> **6** = 失敗します。|  
|**start_time**|**datetime**|エージェント セッションの開始日時。|  
|**time**|**datetime**|最後にメッセージがログに記録された日時。|  
|**duration**|**int**|セッションの利用状況をログに記録してからの経過時間 (秒単位)。|  
|**コメント**|**nvarchar (255)**|説明のテキスト。|  
|**transaction_id**|**nvarchar (40)**|メッセージと共に格納されるトランザクション ID です (適用できる場合)。|  
|**transaction_status**|**int**|トランザクションの状態です。|  
|**transactions_processed**|**int**|セッション中に処理されたトランザクション数の累計。|  
|**commands_processed**|**int**|セッション中に処理されたコマンド数の累計。|  
|**delivery_rate**|**float(53)**|1 秒あたりに配信される平均コマンド数。|  
|**transaction_rate**|**float(53)**|処理されたトランザクションの割合。|  
|**サブスクライバー**|**sysname**|サブスクライバーの名前。|  
|**subscriberdb**|**sysname**|サブスクリプション データベースの名前。|  
|**error_id**|**int**|場合は 0、その番号を表す、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラー メッセージ。|  
|**timestamp**|**timestamp**|テーブルのタイムスタンプ列。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
