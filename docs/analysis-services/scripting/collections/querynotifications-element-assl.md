---
title: "QueryNotifications 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: QueryNotifications Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
helpviewer_keywords: QueryNotifications element
ms.assetid: 0e7e951f-c8b9-4492-bb01-e4b5d16edde6
caps.latest.revision: "15"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8eaf78e9ea72fa5727fdb167f2f3bc0d6684fe2a
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="querynotifications-element-assl"></a>QueryNotifications 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]コレクションを格納[QueryNotification](../../../analysis-services/scripting/objects/querynotification-element-assl.md)要素に情報を提供する、 [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)データ ソースが変更されているかどうかを判断するために実行するクエリについて要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ProactiveCachingQueryBinding>  
   ...  
   <QueryNotifications>  
      <QueryNotification>...</QueryNotification>  
...</QueryNotifications>  
   ...  
</ProactiveCachingQueryBinding>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ProactiveCachingQueryBinding](../../../analysis-services/scripting/data-type/proactivecachingquerybinding-data-type-assl.md)|  
|子要素|[QueryNotification](../../../analysis-services/scripting/objects/querynotification-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.QueryNotificationCollection>します。  
  
## <a name="see-also"></a>参照  
 [コレクション &#40;です。ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
