---
title: "server trigger recursion サーバー構成オプション | Microsoft Docs"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- recursive triggers [SQL Server]
- triggers [SQL Server], recursive
- server trigger recursion option
ms.assetid: da4c25f5-d04c-4951-a3db-409e71a1b468
caps.latest.revision: "24"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e8f9412d311c5c12d0a77eb4ec0fb02fb9664d75
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="server-trigger-recursion-server-configuration-option"></a>server trigger recursion サーバー構成オプション
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  サーバーレベルのトリガーを再帰的に起動できるようにするかどうかを指定するには、 **server trigger recursion** オプションを使用します。 このオプションを 1 (ON) に設定すると、サーバーレベルのトリガーを再帰的に起動できます。 このオプションを 0 (OFF) に設定すると、サーバーレベルのトリガーは再帰的に起動できません。 server trigger recursion オプションが 0 (OFF) の場合は、直接再帰のみが回避されます  (間接再帰を無効にするには、**nested triggers** オプションを 0 に設定します)。このオプションの既定値は 1 (ON) です。 この設定はすぐに適用されます。サーバーを再起動する必要はありません。  
  
 詳しくは、「 [入れ子になったトリガーの作成](../../relational-databases/triggers/create-nested-triggers.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
