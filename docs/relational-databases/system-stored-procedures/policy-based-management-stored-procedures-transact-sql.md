---
title: "ポリシー ベースの管理ストアド プロシージャ (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- Policy-Based Management, stored procedures
- stored procedures [Policy-Based Management]
ms.assetid: df64ab19-4e66-4702-96bd-32ad587d00f0
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f47b4e74a47659b8428ed8b5f856a3974da27cd3
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="policy-based-management-stored-procedures-transact-sql"></a>ポリシー ベースの管理ストアド プロシージャ (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、次のシステムでは、ポリシー ベースの管理に使用されるプロシージャが格納されます。  
  
> [!IMPORTANT]  
>  サポートされているのは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックに記載されているポリシー ベースの管理ストアド プロシージャのみです。 記載されていないストアド プロシージャは、内部ポリシー ベースの管理コンポーネント専用です。ポリシー ベースの管理には使用しないでください。  
  
|||  
|-|-|  
|[sp_syspolicy_add_policy_category](../../relational-databases/system-stored-procedures/sp-syspolicy-add-policy-category-transact-sql.md)|[sp_syspolicy_rename_policy_category](../../relational-databases/system-stored-procedures/sp-syspolicy-rename-policy-category-transact-sql.md)|  
|[sp_syspolicy_add_policy_category_subscription](../../relational-databases/system-stored-procedures/sp-syspolicy-add-policy-category-subscription-transact-sql.md)|[sp_syspolicy_repair_policy_automation](../../relational-databases/system-stored-procedures/sp-syspolicy-repair-policy-automation-transact-sql.md)|  
|[sp_syspolicy_configure](../../relational-databases/system-stored-procedures/sp-syspolicy-configure-transact-sql.md)|[sp_syspolicy_set_config_enabled](../../relational-databases/system-stored-procedures/sp-syspolicy-set-config-enabled-transact-sql.md)|  
|[sp_syspolicy_delete_policy_category](../../relational-databases/system-stored-procedures/sp-syspolicy-delete-policy-category-transact-sql.md)|[sp_syspolicy_set_config_history_retention](../../relational-databases/system-stored-procedures/sp-syspolicy-set-config-history-retention-transact-sql.md)|  
|[sp_syspolicy_delete_policy_category_subscription](../../relational-databases/system-stored-procedures/sp-syspolicy-delete-policy-category-subscription-transact-sql.md)|[sp_syspolicy_set_log_on_success](../../relational-databases/system-stored-procedures/sp-syspolicy-set-log-on-success-transact-sql.md)|  
|[sp_syspolicy_delete_policy_execution_history](../../relational-databases/system-stored-procedures/sp-syspolicy-delete-policy-execution-history-transact-sql.md)|[sp_syspolicy_subscribe_to_policy_category](../../relational-databases/system-stored-procedures/sp-syspolicy-subscribe-to-policy-category-transact-sql.md)|  
|[sp_syspolicy_purge_health_state](../../relational-databases/system-stored-procedures/sp-syspolicy-purge-health-state-transact-sql.md)|[sp_syspolicy_unsubscribe_from_policy_category](../../relational-databases/system-stored-procedures/sp-syspolicy-unsubscribe-from-policy-category-transact-sql.md)|  
|[sp_syspolicy_purge_history](../../relational-databases/system-stored-procedures/sp-syspolicy-purge-history-transact-sql.md)|[sp_syspolicy_update_policy_category](../../relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-transact-sql.md)|  
|[sp_syspolicy_rename_condition](../../relational-databases/system-stored-procedures/sp-syspolicy-rename-condition-transact-sql.md)|[sp_syspolicy_update_policy_category_subscription](../../relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-subscription-transact-sql.md)|  
|[sp_syspolicy_rename_policy](../../relational-databases/system-stored-procedures/sp-syspolicy-rename-policy-transact-sql.md)||  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したサーバーの管理](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  