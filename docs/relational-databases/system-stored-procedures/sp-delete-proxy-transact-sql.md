---
title: "sp_delete_proxy (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_delete_proxy
- sp_delete_proxy_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sp_delete_proxy
- DROP PROXY statement
ms.assetid: 44a1db13-b7f2-4dab-a1b5-b8dafb41737c
caps.latest.revision: "21"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8c9f647232ee2265effe782d3373a08738202d33
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spdeleteproxy-transact-sql"></a>sp_delete_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定したプロキシを削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_delete_proxy [ @proxy_id = ] id , [ @proxy_name = ] 'proxy_name'  
```  
  
## <a name="arguments"></a>引数  
 [  **@proxy_id** =] *id*  
 削除するプロキシのプロキシ識別番号を指定します。 *Proxy_id*は**int**、既定値は NULL です。  
  
 [  **@proxy_name** =] **'***proxy_name***'**  
 削除するプロキシの名前を指定します。 *Proxy_name*は**sysname**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 いずれか **@proxy_name** または **@proxy_id** 指定する必要があります。 両方の引数を指定する場合は、両方とも同じプロキシを参照する必要があります。異なるプロキシを参照する場合、ストアド プロシージャは失敗します。  
  
 指定したプロキシがジョブ ステップによって参照されている場合は、プロキシを削除できないため、ストアド プロシージャは失敗します。  
  
## <a name="permissions"></a>Permissions  
 既定では、メンバーにのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_delete_proxy**です。  
  
## <a name="examples"></a>使用例  
 次の例は、プロキシを削除`Catalog application proxy`です。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_proxy  
    @proxy_name = N'Catalog application proxy' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_add_proxy &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)  
  
  
