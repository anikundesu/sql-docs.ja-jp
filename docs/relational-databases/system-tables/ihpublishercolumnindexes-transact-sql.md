---
title: "IHpublishercolumnindexes (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- IHpublishercolumnindexes
- IHpublishercolumnindexes_TSQL
dev_langs: TSQL
helpviewer_keywords: IHpublishercolumnindexes system table
ms.assetid: 95b95a1d-b502-4838-825f-82a456487e25
caps.latest.revision: "23"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 21370e81d1be10aef58a5dda779f765417fc0a54
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihpublishercolumnindexes-transact-sql"></a>IHpublishercolumnindexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHpublishercolumnindexes**システム テーブル内の SQL Server 以外のパブリケーションの列をマップ、 [IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md)システム テーブル内のインデックスに、 [IHpublisherindexes](../../relational-databases/system-tables/ihpublisherindexes-transact-sql.md)システム テーブル。 このテーブルは、ディストリビューション データベースに保存されます。  
  
## <a name="definition"></a>定義  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**publishercolumn_id**|**int**|列を識別[IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md)関連付けられたインデックス。|  
|**publisherindex_id**|**int**|インデックスを識別、 [IHpublisherindexes](../../relational-databases/system-tables/ihpublisherindexes-transact-sql.md)列に関連付けられているテーブル。|  
|**indid**|**int**|パブリッシュされたテーブル内での列の位置|  
  
## <a name="see-also"></a>参照  
 [異種データベース レプリケーション](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
