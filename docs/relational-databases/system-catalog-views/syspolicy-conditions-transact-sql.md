---
title: "syspolicy_conditions (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- syspolicy_conditions
- syspolicy_conditions_TSQL
dev_langs: TSQL
helpviewer_keywords: syspolicy_conditions view
ms.assetid: af97d26c-4bd5-4b08-be51-8419e3b2832c
caps.latest.revision: "22"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a0628b0913358fd5fb80f3c36fbcf8e5a5c05170
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="syspolicyconditions-transact-sql"></a>syspolicy_conditions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  インスタンスのポリシー ベースの管理条件ごとに 1 行を表示[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 syspolicy_conditions は、msdb データベースの dbo スキーマに属します。 次の表では、syspolicy_conditions ビュー内の列について説明します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|condition_id|**int**|この条件の識別子。 各条件は、1 つ以上の条件式のコレクションを表します。|  
|name|**sysname**|条件の名前。|  
|date_created|**datetime**|条件が作成された日時。|  
|description|**nvarchar(max)**|条件の説明。 この説明の列は省略可能であり、NULL の場合もあります。|  
|created_by|**sysname**|条件を作成したログイン。|  
|modified_by|**sysname**|条件を最近変更したログイン。 変更されていない場合は NULL です。|  
|date_modified|**datetime**|条件が作成された日時。 変更されていない場合は NULL です。|  
|is_name_condition|**smallint**|条件が名前付け条件かどうかを指定します。<br /><br /> 0 = 条件式には @Name 変数が含まれません。<br /><br /> 1 = 条件式が含まれています、@Name変数。|  
|ファセット (facet)|**nvarchar(max)**|条件の基になっているファセットの名前。|  
|式|**nvarchar(max)**|ファセットの状態の式。|  
|obj_name|**sysname**|割り当てられたオブジェクト名@Name条件式には、この変数が含まれている場合。|  
  
## <a name="remarks"></a>解説  
 ポリシー ベースの管理のトラブルシューティングを行う場合に、条件を作成または最後に変更したユーザーを特定するには、syspolicy_conditions ビューを照会します。  
  
## <a name="permissions"></a>Permissions  
 msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したサーバーの管理](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [ポリシーベースの管理ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
