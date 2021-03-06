---
title: "@@TOTAL_READ (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/17/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@TOTAL_READ_TSQL'
- '@@TOTAL_READ'
dev_langs: TSQL
helpviewer_keywords:
- number of disk reads
- disks [SQL Server], number of disk reads
- '@@TOTAL_READ function'
- total read [SQL Server]
- read activity since last started
ms.assetid: b505fbe9-9569-4f3d-80b9-b64b5109ac98
caps.latest.revision: "22"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a062d6e9fab425ead0db82542baeca2c54861aae
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="x40x40totalread-transact-sql"></a>&#x40;&#x40;です。TOTAL_READ (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  返します、ディスク読み取りの数、していないキャッシュの読み取り、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ため[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が最後に起動します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
@@TOTAL_READ  
```  
  
## <a name="return-types"></a>戻り値の型  
 **整数 (integer)**  
  
## <a name="remarks"></a>解説  
 いくつか含むレポートを表示する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]実行の統計を読み取りおよび書き込み動作、含む**sp_monitor**です。  
  
## <a name="examples"></a>使用例  
 次の例では、現在のシステム上の日付と時刻におけるディスクの読み取りおよび書き込みの合計数が返されます。  
  
```  
SELECT @@TOTAL_READ AS 'Reads', @@TOTAL_WRITE AS 'Writes', GETDATE() AS 'As of';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Reads       Writes      As of                   
----------- ----------- ----------------------  
7760        97263       12/5/2006 10:23:00 PM   
```  
  
## <a name="see-also"></a>参照  
 [sp_monitor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)   
 [システム統計関数 &#40;です。TRANSACT-SQL と&#41;です。](../../t-sql/functions/system-statistical-functions-transact-sql.md)   
 [@@TOTAL_WRITE &#40;Transact-SQL&#41;](../../t-sql/functions/total-write-transact-sql.md)  
  
  
