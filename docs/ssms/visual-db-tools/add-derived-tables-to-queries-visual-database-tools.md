---
title: "クエリへの派生テーブルの追加 (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queries [Visual Database Tools]
- joins [SQL Server], derived tables
- table joins [SQL Server]
- derived tables
ms.assetid: 05f1ba1d-465f-4e36-84bb-21b963c9b8f9
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a6a04a3e2beadefdd94596e215eb972c0af4a7ad
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="add-derived-tables-to-queries-visual-database-tools"></a>クエリへの派生テーブルの追加 (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] 派生テーブルは、クエリのソース テーブルとして使用される結果セットです。 **ダイアグラム ペイン**でクエリに派生テーブルを追加できます。  
  
### <a name="to-add-a-derived-table-to-a-query"></a>クエリに派生テーブルを追加するには  
  
1.  既存のクエリを開くか、新しいクエリを作成します。  
  
2.  **ダイアグラム ペイン** を右クリックし、 **[派生した新しいテーブルの追加]**を選択します。  
  
    derivedtbl_*N* という名前で新しいテーブルが追加され、派生テーブルの SELECT ステートメントがクエリの FROM 句に追加されます。  
  
## <a name="see-also"></a>参照  
[クエリに関する基本操作の実行 (Visual Database Tools)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
[クエリの作成 (Visual Database Tools)](../../ssms/visual-db-tools/create-queries-visual-database-tools.md)  
[クエリを開く (Visual Database Tools)](../../ssms/visual-db-tools/open-queries-visual-database-tools.md)  
[SELECT (Transact-SQL)](http://msdn.microsoft.com/en-us/dc85caea-54d1-49af-b166-f3aa2f3a93d0)  
  
