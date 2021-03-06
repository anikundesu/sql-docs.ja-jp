---
title: "managed_backup.fn_get_current_xevent_settings (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
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
- fn_get_current_xevent_settings
- smart_admin.fn_get_current_xevent_settings_TSQL
- fn_get_current_xevent_settings_TSQL
- smart_admin.fn_get_current_xevent_settings
dev_langs: TSQL
helpviewer_keywords:
- smart_admin.fn_get_current_xevent_settings
- fn_get_current_xevent_settings
ms.assetid: 95d3adaa-bb9d-4833-b8b4-3d9fd4f9c82a
caps.latest.revision: "11"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 80ac067f956383e7df57d072431b17f90ae3d293
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="managedbackupfngetcurrentxeventsettings-transact-sql"></a>managed_backup.fn_get_current_xevent_settings (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Smart Admin によってサポートされる拡張イベントの種類ごとに 1 行を返します。  
  
 この関数を使用すると、現在の拡張イベントの設定を返したり確認したりして、構成可能なイベントの種類や現在の構成を識別できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```tsql  
smart_admin.fn_get_current_xevent_settings ()   
```  
  
##  <a name="Arguments"></a> 引数  
 この関数には引数がありません。  
  
## <a name="table-returned"></a>返されるテーブル  
 拡張イベントの管理、分析、運用のチャネルは必須であり、既定で有効になっていますが、構成することはできません。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|Event_name|NVARCHAR(128)|拡張イベントの種類。|  
|is_configurable|NVARCHAR(128)|これは、設定は**True**イベントが構成可能な場合は、それ以外の場合、設定**False**です。|  
|is_enabled|NVARCHAR(128)|イベントが有効な場合は True に設定されます。有効でない場合は False に設定されます。 デバッグ イベントを有効にするには、smart_admin.sp_set_parameter を使用します。|  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>Permissions  
 必要があります**選択**関数に対する権限。  
  
## <a name="examples"></a>使用例  
 次の例では、すべての拡張イベントが現在の状態と共に返されます。  
  
```  
SELECT *   
FROM smart_admin.fn_get_current_xevent_settings ()  
  
```  
  
  
