---
title: "Server State イベント カテゴリの検出 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- Discover Server State event category
- server state events [Analysis Services]
- discover server state events
- event classes [Analysis Services], discover server state
ms.assetid: b62ebf66-d090-4f74-8c83-11ed518b2018
caps.latest.revision: "25"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 744cf73bdbdf1389ce7f9a67d10f2a90232606b6
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="discover-server-state-event-category"></a>サーバー状態検出イベント カテゴリ
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Discover Server State イベント カテゴリには、次の表に示したイベント クラスがあります。  
  
|Event Class|イベント ID|Description|  
|-----------------|--------------|-----------------|  
|Server State Discover Begin|33|トレースが開始されてからのすべての Server-State XMLA Discover Begin イベントを収集します。|  
|Server State Discover Data|34|トレースが開始されてからのすべての Server-State XMLA Discover Data イベントを収集します。 これらのイベントは、検出要求に対する応答の内容がキャプチャされます。|  
|Server State Discover End|35|トレースが開始されてからのすべての Server-State XMLA Discover End イベントを収集します。|  
  
 Query イベントの各イベント クラスに関連する列の詳細については、「 [Discover Server State イベントのデータ列](../../analysis-services/trace-events/discover-server-state-events-data-columns.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Analysis Services トレース イベント](../../analysis-services/trace-events/analysis-services-trace-events.md)  
  
  
