---
title: "sys.assembly_types (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- assembly_types
- sys.assembly_types
- sys.assembly_types_TSQL
- assembly_types_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.assembly_types catalog view
ms.assetid: 35f0384f-7a6d-41b1-9461-f1406d68f317
caps.latest.revision: "22"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 211cb9f89fe2e84b6a8a21dd8268551df6a2e97c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysassemblytypes-transact-sql"></a>sys.assembly_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  CLR アセンブリによって定義されるユーザー定義型ごとに 1 行のデータを保持します。 次**sys.assembly_types**継承された列の一覧に表示されます (を参照してください[sys.types &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)) 後**rule_object_id**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**assembly_id**|**int**|この型の作成元であるアセンブリの ID です。|  
|**assembly_class**|**sysname**|この型を定義しているアセンブリ内のクラスの名前です。|  
|**is_binary_ordered**|**bit**|この型のバイトの並べ替えは、この型での比較演算子を使用した並べ替えと同じです。|  
|**is_fixed_length**|**bit**|この型の長さは、常に max_length と同じです。|  
|**prog_id**|**nvarchar (40)**|COM に公開される型の ProgID です。|  
|**assembly_qualified_name**|**nvarchar (4000)**|アセンブリの修飾された型名です。 この名前は、Type.GetType() に渡すのに適した形式になっています。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [スカラー型カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/scalar-types-catalog-views-transact-sql.md)  
  
  
