---
title: "テーブル サイズの見積もり | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: databases
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pages [SQL Server], space
- space [SQL Server], tables
- row size [SQL Server]
- size [SQL Server], tables
- column size [SQL Server]
- predicting table size [SQL Server]
- table size [SQL Server]
- estimating table size
- clustered indexes, table size
- disk space [SQL Server], tables
- space allocation [SQL Server], table size
- designing databases [SQL Server], estimating size
- reserved free rows per page [SQL Server]
- calculating table size
ms.assetid: 15c17c92-616f-402e-894b-907a296efe5f
caps.latest.revision: "30"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 91d77c9df5d9f3de6428928ae6b9cca09f47a983
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="estimate-the-size-of-a-table"></a>テーブル サイズの見積もり
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] 次の手順を実行して、テーブルにデータを格納するために必要な領域を見積もることができます。  
  
1.  「 [ヒープ サイズの見積もり](../../relational-databases/databases/estimate-the-size-of-a-heap.md) 」または「 [クラスター化インデックスのサイズの見積もり](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md)」の説明に従って、ヒープまたはクラスター化インデックスに必要な領域を計算します。  
  
2.  「 [非クラスター化インデックスのサイズの算出](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md)」に記載されている手順に従って、非クラスター化インデックスごとに必要な領域を計算します。  
  
3.  手順 1. と手順 2. で計算した値を加算します。  
  
## <a name="see-also"></a>参照  
 [データベース サイズの見積もり](../../relational-databases/databases/estimate-the-size-of-a-database.md)   
 [ヒープ サイズの見積もり](../../relational-databases/databases/estimate-the-size-of-a-heap.md)   
 [クラスター化インデックスのサイズの見積もり](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md)   
 [非クラスター化インデックスのサイズの算出](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md)  
  
  
