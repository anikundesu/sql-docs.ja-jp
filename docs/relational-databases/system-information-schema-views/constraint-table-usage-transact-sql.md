---
title: "CONSTRAINT_TABLE_USAGE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-information-schema-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CONSTRAINT_TABLE_USAGE_TSQL
- CONSTRAINT_TABLE_USAGE
dev_langs: TSQL
helpviewer_keywords:
- CONSTRAINT_TABLE_USAGE view
- INFORMATION_SCHEMA.CONSTRAINT_TABLE_USAGE view
ms.assetid: 5770b696-6c04-4d5c-a8db-9eb92022fa42
caps.latest.revision: "37"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 74b4c55aafb5830eee79a2ec0498750a0f07b5dd
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="constrainttableusage-transact-sql"></a>CONSTRAINT_TABLE_USAGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在のデータベース内にある、制約が定義されているテーブルごとに 1 行を返します。 この情報スキーマ ビューは、現在のユーザーが権限を所有しているオブジェクトについての情報を返します。  
  
 これらのビューから情報を取得するには、完全修飾の名前を指定**INFORMATION_SCHEMA** 。*view_name*です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_CATALOG**|**nvarchar (**128**)**|テーブル修飾子|  
|**TABLE_SCHEMA、**|**nvarchar (**128**)**|テーブルを含むスキーマの名前<br /><br /> **\*\*重要な\* \*** オブジェクトのスキーマを決定 INFORMATION_SCHEMA ビューを使用しないでください。 オブジェクトのスキーマを調べる唯一の信頼性のある方法は、sys.objects カタログ ビューに対するクエリを実行する方法です。|  
|**TABLE_NAME**|**sysname**|テーブル名です。|  
|**CONSTRAINT_CATALOG**|**nvarchar (**128**)**|制約修飾子|  
|**CONSTRAINT_SCHEMA**|**nvarchar (**128**)**|制約を含むスキーマの名前です。<br /><br /> **\*\*重要な\* \*** オブジェクトのスキーマを決定 INFORMATION_SCHEMA ビューを使用しないでください。 オブジェクトのスキーマを調べる唯一の信頼性のある方法は、sys.objects カタログ ビューに対するクエリを実行する方法です。|  
|**CONSTRAINT_NAME**|**sysname**|制約名。|  
  
## <a name="see-also"></a>参照  
 [システム ビュー &#40;です。TRANSACT-SQL と #41 です。](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [情報スキーマ ビュー &#40;です。TRANSACT-SQL と #41 です。](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.objects &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.check_constraints &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-check-constraints-transact-sql.md)   
 [sys.key_constraints &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-key-constraints-transact-sql.md)   
 [sys.foreign_keys &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-foreign-keys-transact-sql.md)  
  
  
