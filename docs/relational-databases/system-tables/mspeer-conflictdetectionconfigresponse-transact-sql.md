---
title: "MSpeer_conflictdetectionconfigresponse (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
- MSpeer_conflictdetectionconfigresponse
- MSpeer_conflictdetectionconfigresponse_TSQL
dev_langs: TSQL
helpviewer_keywords: MSpeer_conflictdetectionconfigureresponse
ms.assetid: 2685fb66-731d-40f7-af4b-596b9222c5d4
caps.latest.revision: "11"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cb96eb44f44e3a7a0d1e1e4bcd0b1ce8dc00cf5e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mspeerconflictdetectionconfigresponse-transact-sql"></a>MSpeer_conflictdetectionconfigresponse (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  トポロジ全体の構成要求に対する各ノードの応答を保存するために、ピア ツー ピア レプリケーションで使用されます。 このテーブルは、パブリケーション データベース内に保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|request_id|**int**|競合構成要求エントリを識別、 [MSpeer_conflictdetectionconfigrequest](../../relational-databases/system-tables/mspeer-conflictdetectionconfigrequest-transact-sql.md)テーブル。|  
|peer_node|**sysname**|応答を生成したサーバー インスタンスの名前です。|  
|peer_db|**sysname**|応答を生成したピア側のサブスクリプション データベースです。|  
|peer_version|**sysname**|パブリッシャーのバージョン番号を識別します。|  
|peer_db_version|**sysname**|ピア データベースのバージョン番号を識別します。|  
|is_peer|**bit**|ノードが読み取り専用サブスクライバーかどうかを示します。 値**0**読み取り専用サブスクライバーが示されます。|  
|conflict_detection_enabled|**bit**|トポロジで競合検出を有効にするかどうかを指定します。|  
|originator_id|**varbinary (16)**|競合検出のためにトポロジの各ノードを識別します。 詳細については、「 [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)」を参照してください。|  
|peer_conflict_retention|**int**|メタデータが競合テーブルに保存される期間 (日数) です。|  
|peer_subscriptions|**XML**|要求に応答したノードに関する情報です。|  
|progress_phase|**nvarchar (32)**|処理の現在のフェーズを識別します。有効値は次のとおりです。<br /><br /> Started<br /><br /> 収集されたピア バージョン<br /><br /> 収集された状態|  
|modified_date|**datetime**|フェーズが完了した日時です。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
