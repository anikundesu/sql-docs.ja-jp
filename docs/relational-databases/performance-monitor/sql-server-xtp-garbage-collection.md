---
title: SQL Server XTP Garbage Collection | Microsoft Docs
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
ms.assetid: 64ae91e5-b420-44b4-af1a-f8bca83d7f41
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1a14b7101f0aaab288f205d1de11df8fd6f5d042
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sql-server-xtp-garbage-collection"></a>SQL Server XTP Garbage Collection
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  SQL Server XTP Garbage Collection パフォーマンス オブジェクトには、インメモリ OLTP エンジンのガベージ コレクターに関連するカウンターが含まれています。  
  
 次の表では、 **SQL Server XTP Garbage Collection** カウンターについて説明します。  
  
|カウンター|説明|  
|-------------|-----------------|  
|**Dusty corner scan retries/sec (GC-issued)**|ガベージ コレクターによって発行されたダスティ コーナー スウィープ (詳細なクリーンアップ) の実行中に、書き込みの競合が原因で発生したスキャン再試行回数に関する 1 秒あたりの平均です。 これは非常に低レベルのカウンターであり、お客様による使用は想定されていません。|  
|**Main GC work items/sec**|メイン GC スレッドで処理された作業項目の数です。|  
|**Parallel GC work item/sec**|並列スレッドが GC 作業項目を実行した回数です。|  
|**Rows processed/sec**|ガベージ コレクターにより 1 秒間に処理された (平均) 行数です。|  
|**Rows processed/sec (first in bucket and removed)**|ガベージ コレクターによって処理され、最初は対応するハッシュ バケット内に存在し、直ちに削除することができた行の数に関する 1 秒あたりの平均です。|  
|**Rows processed/sec (first in bucket)**|ガベージ コレクターによって処理され、最初は対応するハッシュ バケット内に存在していた行の数に関する 1 秒あたりの平均です。|  
|**Rows processed/sec (marked for unlink)**|ガベージ コレクターによって処理され、既にリンク解除のマークが付いていた行の数に関する 1 秒あたりの平均です。|  
|**Rows processed/sec (no sweep needed)**|ガベージ コレクターによって処理され、ダスティ コーナー スウィープ (詳細なクリーンアップ) を必要としない行の数に関する 1 秒あたりの平均です。|  
|**Sweep expired rows removed/sec**|ダスティ コーナー スウィープの実行中に削除された、有効期限切れの行の数に関する 1 秒あたりの平均です。|  
|**Sweep expired rows touched/sec**|ダスティ コーナー スウィープの実行中に操作された、有効期限切れの行の数に関する 1 秒あたりの平均です。|  
|**Sweep expiring rows touched/sec**|ダスティ コーナー スウィープの実行中に操作された、間もなく期限切れになる行の数に関する 1 秒あたりの平均です。|  
|**Sweep rows touched/sec**|ダスティ コーナー スウィープの実行中に操作された行の数に関する 1 秒あたりの平均です。|  
|**Sweep scans started/sec**|ダスティ コーナー スウィープ スキャンが開始された回数に関する 1 秒あたりの平均。|  
  
## <a name="see-also"></a>参照  
 [SQL Server XTP &#40;インメモリ OLTP&#41; パフォーマンス カウンター](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)  
  
  
