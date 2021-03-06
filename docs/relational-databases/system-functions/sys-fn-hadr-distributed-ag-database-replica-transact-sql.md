---
title: "sys.fn_hadr_distributed_ag_database_replica (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/14/2016
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
- sys.fn_hadr_distributed_ag_database_replica
- sys.fn_hadr_distributed_ag_database_replica_TSQL
- fn_hadr_distributed_ag_database_replica
- fn_hadr_distributed_ag_database_replica_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.fn_hadr_distributed_ag_database_replica
ms.assetid: 0e6202a1-e872-4f53-99d7-c16b6f712efc
caps.latest.revision: "9"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 415600ca830f5ba1b4b1930b486e423057ec9c62
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysfnhadrdistributedagdatabasereplica-transact-sql"></a>sys.fn_hadr_distributed_ag_database_replica (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  分散型可用性グループ内のデータベースをローカルの可用性グループ内のデータベースにマップするために使用します。  
   
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.fn_hadr_distributed_ag_database_replica( lag_Id, database_id )  
```  
  
## <a name="arguments"></a>引数  
 '*lag_Id*'  
 分散型可用性グループの識別子です。 *lag_Id*は型です。 **uniqueidentifier**です。  
  
 '*database_id*'  
 分散型可用性グループ内のデータベースの識別子です。 *database_id*は型です。 **uniqueidentifier**です。  
  
## <a name="tables-returned"></a>返されたテーブル  
 次の情報を返します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**group_database_id**|**uniqueidentifier**|ローカルの可用性グループ内のデータベースの ID です。|  
  
## <a name="examples"></a>使用例  
  
### <a name="using-sysfnhadrdistributedagdatabasereplica"></a>Sys.fn_hadr_distributed_ag_database_replica を使用します。  
 次の例は、分散型可用性グループのデータベース ID を渡します。 ローカルの可用性グループに関連付けられているデータベースの ID を持つテーブルを返します。  
  
```  
DECLARE @lagId uniqueidentifier = '4A03D1A8-4AE6-B153-E7E9-ED22A546008D'  
DECLARE @databaseId uniqueidentifier = '3FFA882A-C4C3-5B9E-A203-8F44BD9659F7'  
  
SELECT * FROM sys.fn_hadr_distributed_ag_database_replica(@lagId, @databaseId)  
GO  
```  
  
## <a name="see-also"></a>参照  
 [Always On 可用性グループの関数と #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/always-on-availability-groups-functions-transact-sql.md)   
 [AlwaysOn 可用性グループ &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [分散型可用性グループ &#40;です。Always On 可用性グループ &#41;](../../database-engine/availability-groups/windows/distributed-availability-groups-always-on-availability-groups.md)   
 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-availability-group-transact-sql.md)  
  
  
