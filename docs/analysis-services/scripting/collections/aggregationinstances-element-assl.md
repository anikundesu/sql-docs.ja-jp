---
title: "AggregationInstances 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
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
apiname: AggregationInstances Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
helpviewer_keywords: AggregationInstances element
ms.assetid: e8321aa8-361b-4d8a-bd89-a596eeb814b1
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 67428069e63a4d33e3742134f9d5b4953661605c
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="aggregationinstances-element-assl"></a>AggregationInstances 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]定義されている集計インスタンスのコレクションを格納、[パーティション](../../../analysis-services/scripting/objects/partition-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Partition>  
   ...  
   <AggregationInstances>  
      <AggregationInstance>...</AggregationInstance>  
   </AggregationInstances>  
   ...  
</Partition>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし (コレクション型)|  
|既定値|なし (コレクション型)|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[パーティション](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|子要素|[AggregationInstance](../../../analysis-services/scripting/objects/aggregationinstance-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.AggregationInstanceCollection>します。  
  
## <a name="see-also"></a>参照  
 [コレクション &#40;です。ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
