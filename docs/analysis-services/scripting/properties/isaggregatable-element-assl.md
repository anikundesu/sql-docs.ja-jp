---
title: "IsAggregatable 要素 (ASSL) |Microsoft ドキュメント"
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
apiname: IsAggregatable Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: IsAggregatable
helpviewer_keywords: IsAggregatable element
ms.assetid: ed7dbe89-259c-4c5c-9660-b965c3af1573
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2a40d33451ac36edc848f1d66eecd2ea21c3b2dc
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="isaggregatable-element-assl"></a>IsAggregatable 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]指定するかどうかの値、 [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)要素を集計することができます。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DimensionAttribute>  
      ...  
   <IsAggregatable>...</IsAggregatable>  
  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|ブール値|  
|既定値|True|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**IsAggregatable**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.DimensionAttribute>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
