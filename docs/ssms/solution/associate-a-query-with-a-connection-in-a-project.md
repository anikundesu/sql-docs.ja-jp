---
title: "クエリとプロジェクト内の接続との関連付け | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-solutions
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connections [SQL Server Management Studio], query associations
- projects [SQL Server Management Studio], connections
- projects [SQL Server Management Studio], query connections
- query associations [SQL Server Management Studio]
ms.assetid: c9625ae0-29c1-4179-a709-51b7e2f9e23d
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c790e099f0fc9558b452879866c8dbbaa25d7f2d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="associate-a-query-with-a-connection-in-a-project"></a>クエリとプロジェクト内の接続との関連付け
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] クエリを接続の指定なしで作成した場合、またはクエリを別のプロジェクトに移動する場合は、そのクエリは現在のプロジェクト内の接続に関連付けられません。  
  
### <a name="to-associate-a-query-with-a-connection-in-a-project"></a>クエリをプロジェクト内の接続に関連付けるには  
  
1.  クエリをクエリ エディターで開いている場合は、クエリ エディターの空白部分を右クリックして **[接続]**をポイントし、 **[接続]**をクリックします。 クエリが開いていない場合は、ソリューション エクスプローラーでクエリをダブルクリックし、クエリを接続します。  
  
2.  **[データベース エンジンへの接続]** ダイアログ ボックスで、接続情報を入力します。 接続情報が既存の接続に一致すると、クエリはその接続に関連付けられます。  
  
## <a name="see-also"></a>参照  
[ソリューション エクスプローラー](../../ssms/solution/solution-explorer.md)  
[クエリに関連付けられた接続の変更](../../ssms/solution/change-the-connection-associated-with-a-query.md)  
[プロジェクト内の接続のプロパティを表示または変更する方法](../../ssms/solution/view-or-change-the-properties-of-a-connection-in-a-project.md)  
  
