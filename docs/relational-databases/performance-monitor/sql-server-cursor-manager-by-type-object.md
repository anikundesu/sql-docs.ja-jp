---
title: "SQL Server: Cursor Manager by Type オブジェクト | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Cursor Manager by Type object
- SQLServer:Cursor Manager by Type
ms.assetid: d67fbd8a-7554-4a16-96f1-d9ee857a95e3
caps.latest.revision: "15"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4b896d5a57046912fec183be926120dc98398bbd
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sql-server-cursor-manager-by-type-object"></a>SQL Server: Cursor Manager by Type オブジェクト
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] **SQLServer:Cursor Manager by Type** オブジェクトには、種類別にグループ化されたカーソルを監視するカウンターが用意されています。  
  
 次の表で、SQL Server **Cursor Manager by Type** カウンターについて説明します。  
  
|Cursor Manager by Type カウンター|説明|  
|-------------------------------------|-----------------|  
|**Active cursors**|アクティブなカーソルの数。|  
|**Cache Hit Ratio**|キャッシュ ヒットとキャッシュ参照の比率。|  
|**Cache Hit Ratio Base**|内部使用のみです。| 
|**Cached Cursor Counts**|キャッシュ内の特定種類のカーソルの数。|  
|**Cursor Cache Use Count/sec**|キャッシュされている各種のカーソルが使用された時間。|  
|**Cursor memory usage**|カーソルによって消費されたメモリ量 (KB)。|  
|**Cursor Requests/sec**|サーバーが受け取った SQL カーソル要求の数。|  
|**Cursor worktable usage**|カーソルによって使用された作業テーブルの数。|  
|**Number of active cursor plans**|カーソル プランの数。|  
  
 オブジェクトの各カウンターには、次のインスタンスが含まれています。  
  
|Cursor Manager のインスタンス|説明|  
|-----------------------------|-----------------|  
|**_Total**|すべてのカーソルに関する情報。|  
|**API Cursor**|API カーソルのみに関する情報。|  
|**TSQL Global Cursor**|[!INCLUDE[tsql](../../includes/tsql-md.md)] グローバル カーソルのみに関する情報。|  
|**TSQL Local Cursor**|[!INCLUDE[tsql](../../includes/tsql-md.md)] ローカル カーソルのみに関する情報。|  
  
## <a name="see-also"></a>参照  
 [リソースの利用状況の監視 &#40;システム モニター&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
