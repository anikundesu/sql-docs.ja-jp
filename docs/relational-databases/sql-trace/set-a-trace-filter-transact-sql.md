---
title: "トレース フィルターの設定 (Transact-SQL) | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-trace
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- filters [SQL Server], traces
- traces [SQL Server], filters
ms.assetid: 7b976a84-7381-43a6-a828-ba83ada71cbe
caps.latest.revision: "20"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e2c3d67f34b0863731f76a647e43949e7a7a71ff
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="set-a-trace-filter-transact-sql"></a>トレース フィルターの設定 (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] このトピックでは、ストアド プロシージャを使用して、トレース中のイベントに関して必要な情報のみを取得するフィルターを作成する方法について説明します。  
  
### <a name="to-set-a-trace-filter"></a>トレース フィルターを設定するには  
  
1.  トレースが既に実行中の場合は、**@status = 0** を指定して **sp_trace_setstatus** を実行し、トレースを停止します。  
  
2.  **sp_trace_setfilter** を実行して、トレース中のイベントに関して取得する情報の種類を構成します。  
  
> [!IMPORTANT]  
>  通常のストアド プロシージャとは異なり、すべての [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ストアド プロシージャ (**sp_trace_*xx***) で、パラメーターのデータ型が厳密に定義されており、データ型の自動変換はサポートしていません。 これらのパラメーターを、引数の説明で指定されている正しいデータ型で指定しないと、このストアド プロシージャではエラーが返されます。  
  
## <a name="see-also"></a>参照  
 [トレースへのフィルターの適用](../../relational-databases/sql-trace/filter-a-trace.md)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [SQL Server Profiler のストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql.md)  
  
  
