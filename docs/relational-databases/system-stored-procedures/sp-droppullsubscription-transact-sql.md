---
title: "sp_droppullsubscription (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_droppullsubscription
- sp_droppullsubscription_TSQL
helpviewer_keywords: sp_droppullsubscription
ms.assetid: 7352d94a-f8f2-42ea-aaf1-d08c3b5a0e76
caps.latest.revision: "21"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 13245c763bea2a34b6c7a95b13c046e43c3d4a31
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spdroppullsubscription-transact-sql"></a>sp_droppullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サブスクライバーの現在のデータベースでサブスクリプションを削除します。 このストアド プロシージャは、サブスクライバー側でプル サブスクリプション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_droppullsubscription [ @publisher= ] 'publisher'  
        , [ @publisher_db= ] 'publisher_db'  
        , [ @publication= ] 'publication'  
    [ , [ @reserved= ] reserved ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@publisher=** ] **'***パブリッシャー***'**  
 リモート サーバー名を指定します。 *パブリッシャー*は**sysname**、既定値はありません。 場合**すべて**サブスクリプションが削除されるすべてのパブリッシャーです。  
  
 [  **@publisher_db=** ] **'***publisher_db***'**  
 パブリッシャー データベースの名前です。 *publisher_db*は**sysname**、既定値はありません。 **すべて**はすべてのパブリッシャー データベースを意味します。  
  
 [  **@publication=** ] **'***パブリケーション***'**  
 パブリケーション名を指定します。 *パブリケーション*は**sysname**、既定値はありません。 場合**すべて**、すべてのパブリケーションにサブスクリプションを削除します。  
  
 [  **@reserved=** ]*予約済み*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_droppullsubscription**はスナップショット レプリケーションおよびトランザクション レプリケーションで使用します。  
  
 **sp_droppullsubscription**に対応する行を削除、 [MSreplication_subscriptions (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/msreplication-subscriptions-transact-sql.md)テーブルと、サブスクライバーで対応するディストリビューター エージェントです。 内の行が残っていない場合[MSreplication_subscriptions (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/msreplication-subscriptions-transact-sql.md)テーブルを削除します。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_droptranpullsubscription](../../relational-databases/replication/codesnippet/tsql/sp-droppullsubscription-_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたはプル サブスクリプションを作成したユーザーが実行できる**sp_droppullsubscription**です。 **Db_owner**固定データベース ロールが実行できる**sp_droppullsubscription**プル サブスクリプションを作成したユーザーがこのロールに属している場合。  
  
## <a name="see-also"></a>参照  
 [プル サブスクリプションを削除します。](../../relational-databases/replication/delete-a-pull-subscription.md)   
 [sp_addpullsubscription &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)   
 [sp_change_subscription_properties &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md)   
 [sp_helppullsubscription &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)   
 [sp_dropsubscription &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)  
  
  
