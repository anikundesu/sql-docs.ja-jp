---
title: "sys.filetable_system_defined_objects (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
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
- sys.filetable_system_defined_objects_TSQL
- filetable_system_defined_objects
- filetable_system_defined_objects_TSQL
- sys.filetable_system_defined_objects
dev_langs: TSQL
helpviewer_keywords: sys.filetable_system_defined_objects catalog view
ms.assetid: 62022e6b-46f6-495f-b14b-53f41e040361
caps.latest.revision: "9"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c3bd6bd8368525c94ce0d999af921c76c2cade96
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysfiletablesystemdefinedobjects-transact-sql"></a>sys.filetable_system_defined_objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  FileTable に関連するシステム定義のオブジェクトの一覧が表示されます。 システム定義のオブジェクトごとに 1 行のデータを格納します。  
  
 FileTable を作成すると、関連するオブジェクト (制約、インデックスなど) が同時に作成されます。 これらのオブジェクトを変更または削除することはできません。これらは、FileTable 自体が削除されると一緒に削除されます。  
  
 Filetable の詳細については、次を参照してください。 [Filetable &#40;です。SQL Server &#41;](../../relational-databases/blob/filetables-sql-server.md).  
  
|列|データ型|Description|  
|------------|---------------|-----------------|  
|**object_id**|**int**|FileTable に関連するシステム定義オブジェクトのオブジェクト ID。<br /><br /> 内のオブジェクトを参照して**sys.objects**です。|  
|**parent_object_id**|**int**|親 FileTable のオブジェクト ID。<br /><br /> 内のオブジェクトを参照して**sys.objects**です。|  
  
## <a name="see-also"></a>参照  
 [FileTable の作成、変更、および削除](../../relational-databases/blob/create-alter-and-drop-filetables.md)   
 [FileTable の管理](../../relational-databases/blob/manage-filetables.md)  
  
  
