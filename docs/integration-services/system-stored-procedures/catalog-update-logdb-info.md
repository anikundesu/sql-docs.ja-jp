---
title: "catalog.update_logdb_info (SSISDB データベース) | Microsoft Docs"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
caps.latest.revision: "1"
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b1389bde14814bd1d295a7abb49461029925eb10
ms.sourcegitcommit: b603dcac7326bba387befe68544619e026e6a15e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="catalogupdatelogdbinfo-ssisdb-database"></a>catalog.update_logdb_info (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out Logging 情報を更新します。

## <a name="syntax"></a>構文

```sql
catalog.update_logdb_info [@server_name = ] server_name, [@connection_string = ] connection_string
```

## <a name="arguments"></a>引数
[ @server_name = ] *server_name*  
 Scale Out ログで使用する SQL Server。 *server_name* は **nvarchar** です。  

 [ @connection_string = ] *connection_string*  
 Scale Out ログで使用する接続文字列。 *connection_string* は **nvarchar** です。

 ## <a name="return-code-value"></a>リターン コード値  
 成功した場合は 0 を返します。  
  
## <a name="result-sets"></a>結果セット  
 なし  

## <a name="permissions"></a>アクセス許可  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
   
-   **ssis_admin** データベース ロールのメンバーシップ  
  
-   **sysadmin** サーバー ロールのメンバーシップ  
 
