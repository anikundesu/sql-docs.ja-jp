---
title: "sys.fn_trace_getinfo (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- fn_trace_getinfo
- fn_trace_getinfo_TSQL
dev_langs: TSQL
helpviewer_keywords:
- traces [SQL Server], status information
- status information [SQL Server], traces
- sys.fn_trace_getinfo function
- fn_trace_getinfo function
ms.assetid: 04b140fe-110a-47b8-98b5-e4c161beb6c9
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 0f7816b4115982fb01f9b456864bb11fc5194ba1
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysfntracegetinfo-transact-sql"></a>sys.fn_trace_getinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定したトレースまたはすべての既存のトレースに関する情報を返します。  
  
> **重要:** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 代わりに拡張イベントを使用します。    
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.fn_trace_getinfo ( { trace_id | NULL | 0 | DEFAULT } )  
```  
  
## <a name="arguments"></a>引数  
 *trace_id*  
 トレースの ID を指定します。 *trace_id*は**int**です。有効な入力値は、トレースの ID 番号、NULL、0、または DEFAULT です。 このコンテキストでは、NULL、0、および DEFAULT は同じ値になります。 NULL、0 を指定するか、既定のインスタンスのすべてのトレースに関する情報を返す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
## <a name="tables-returned"></a>返されたテーブル  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|traceid|**int**|トレースの ID。|  
|property|**int**|トレースのプロパティ。<br /><br /> 1 = トレース オプション。 詳細については、次を参照してください。@optionsで[sp_trace_create &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md).<br /><br /> 2 = ファイル名。<br /><br /> 3 = 最大サイズ。<br /><br /> 4 = 停止時刻。<br /><br /> 5 = 現在のトレースの状態。 0 = 停止。 1 = 実行中。|  
|value|**sql_variant**|指定したトレースのプロパティに関する情報。|  
  
## <a name="remarks"></a>解説  
 特定のトレースの ID が渡された場合、fn_trace_getinfo ではそのトレースに関する情報が返されます。 無効な ID が渡された場合、空の行セットが返されます。  
  
 fn_trace_getinfo を実行すると、結果セットに含まれるトレース ファイルの名前には .trc 拡張子が付けられます。 トレースを定義する方法については、次を参照してください。 [sp_trace_create &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md). トレース フィルターは、同様の情報を参照してください。 [sys.fn_trace_getfilterinfo &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md).  
  
 トレース ストアド プロシージャを使用しての完全な例を参照してください[トレース &#40; を作成する。TRANSACT-SQL と #41 です。](../../relational-databases/sql-trace/create-a-trace-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 サーバーの ALTER TRACE 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、すべてのアクティブなトレースに関する情報を返します。  
  
```  
SELECT * FROM sys.fn_trace_getinfo(0) ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [トレースの作成 &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/create-a-trace-transact-sql.md)   
 [sp_trace_create &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)   
 [sp_trace_generateevent &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md)   
 [sys.fn_trace_geteventinfo &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql.md)   
 [sys.fn_trace_gettable &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/sys-fn-trace-gettable-transact-sql.md)  
  
  
