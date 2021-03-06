---
title: "sys.database_usage (Azure SQL データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: 
ms.prod_service: sql-database
ms.reviewer: 
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- database_usage
- database_usage_TSQL
- sys.database_usage_TSQL
- sys.database_usage
dev_langs: TSQL
helpviewer_keywords:
- database_usage
- sys.database_usage
ms.assetid: be6820de-60bf-4ddd-ace7-4077893d630f
caps.latest.revision: "13"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 670c1a9c7028d495141247b5f2b8b35f85142d6f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysdatabaseusage-azure-sql-database"></a>sys.database_usage (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  **注意: Azure SQL データベース V11 にのみ適用します。**  
  
 上の数、型、およびデータベースの期間を一覧表示、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]サーバー。  
  
 **Sys.database_usage**ビューには、次の列が含まれています。  
  
|列名|Description|  
|-----------------|-----------------|  
|time|使用状況イベントが発生した日付。|  
|sku|データベース用のサービス層の型: **Web**、**ビジネス**、**基本**、**標準**、 **Premium**|  
|quantity|その日に存在していた SKU の種類のデータベースの最大数。|  
  
## <a name="permissions"></a>Permissions  
 このビューに読み取り専用のアクセスに接続するアクセス許可を持つすべてのユーザーには、**マスター**データベース。  
  
## <a name="remarks"></a>解説  
 **Sys.database_usage**ビューは、サブスクリプションの日付ごとに 1 行を返します。  
  
## <a name="see-also"></a>参照  
 [SQL データベースの料金詳細](http://go.microsoft.com/fwlink/?LinkID=394978)   
 [Windows Azure SQL データベースのアカウントと課金](http://msdn.microsoft.com/library/windowsazure/ee621788.aspx)  
  
  
