---
title: "sp_delete_notification (TRANSACT-SQL) |Microsoft ドキュメント"
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
f1_keywords:
- sp_delete_notification_TSQL
- sp_delete_notification
dev_langs: TSQL
helpviewer_keywords: sp_delete_notification
ms.assetid: b55d3898-596d-47a5-a4f0-d65dc736223b
caps.latest.revision: "21"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1e346749b4aa7cdcb44763302bc9f8315773c72d
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="spdeletenotification-transact-sql"></a>sp_delete_notification (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  特定の警告およびオペレーターに対する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント通知定義を削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_delete_notification  
     [ @alert_name = ] 'alert' ,   
     [ @operator_name = ] 'operator'   
```  
  
## <a name="arguments"></a>引数  
 [  **@alert_name=** ] **'***アラート***'**  
 警告の名前を指定します。 *アラート*は**sysname**、既定値はありません。  
  
 [  **@operator_name=** ] **'***演算子***'**  
 オペレーターの名前です。 *演算子*は**sysname**、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 通知を削除する場合は、通知だけが削除されます。警告やオペレーターには影響しません。  
  
## <a name="permissions"></a>Permissions  
 このストアド プロシージャを実行するユーザーに付与する必要があります、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 次の例では、オペレーターに通知を送信`François Ajenstat`とき警告`Test Alert`に発生します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_notification  
    @alert_name = 'Test Alert',  
    @operator_name = 'François Ajenstat' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_add_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-alert-transact-sql.md)   
 [sp_add_notification &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-add-notification-transact-sql.md)   
 [sp_add_operator &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-add-operator-transact-sql.md)   
 [sp_delete_alert &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-delete-alert-transact-sql.md)   
 [sp_help_alert &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-help-alert-transact-sql.md)   
 [sp_help_notification &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-help-notification-transact-sql.md)   
 [sp_help_operator &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-help-operator-transact-sql.md)   
 [sp_update_notification &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-update-notification-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
