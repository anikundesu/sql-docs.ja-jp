---
title: "メンバー リビジョン履歴のロールバック (マスター データ サービス) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d39d3474-20e7-429f-9c8d-fcc4eb0854fc
caps.latest.revision: "5"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 123c2e3be7c8ce472c4499f4ac12bc38ea13edbc
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="rollback-member-revision-history-master-data-services"></a>メンバー リビジョン履歴のロールバック (マスター データ サービス)
  メンバー リビジョン履歴は、メンバーが変更されるたびに記録されます。 メンバー リビジョン履歴は前のバージョンにロールバックすることができます。  
  
## <a name="prerequisites"></a>Prerequisites  
  
-   選択したメンバーの少なくとも 1 つの属性を更新できるアクセス許可が必要です。 リビジョン履歴をロールバックすると、更新できるすべての属性値が前のバージョンの値にロールバックされます。  
  
-   リビジョン履歴は、エンティティのトランザクション ログの種類がメンバーである場合にのみ使用できます。  
  
 **メンバー リビジョン履歴をロールバックするには**  
  
1.  マスター データ マネージャーで、[エクスプローラー] をクリックします。  
  
2.  ロールバックするエンティティとメンバーを選択します。  
  
3.  **[履歴の表示]**をクリックします。  
  
4.  ロールバックするリビジョンを選択し、 **[ロールバック]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [メンバー リビジョン履歴 (マスター データ サービス)](../master-data-services/member-revision-history-master-data-services.md)   
 [エンティティのトランザクション ログの種類の変更 (マスター データ サービス)](../master-data-services/change-the-entity-transaction-log-type-master-data-services.md)  
  
  
