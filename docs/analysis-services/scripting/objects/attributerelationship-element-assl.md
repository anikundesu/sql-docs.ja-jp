---
title: "AttributeRelationship 要素 (ASSL) |Microsoft ドキュメント"
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
apiname: AttributeRelationship Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: MemberProperty
helpviewer_keywords: AttributeRelationship element
ms.assetid: 2e786109-b8bf-4295-b0fe-9c1997349993
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ad7c3b8aa0e61cf0ac9e73010784df7b7505e00b
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="attributerelationship-element-assl"></a>AttributeRelationship 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]2 つの属性間のリレーションシップに関する詳細情報を提供します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AttributeRelationships>  
      <AttributeRelationship>  
      <AttributeID>...</AttributeID>  
            <RelationshipType>...</RelationshipType>  
      <Cardinality>...</Cardinality>  
      <Optionality >...</Optionality>  
      <OverrideBehavior >...</OverrideBehavior>  
            <Annotations>...</Annotations>  
      <Name>...</Name>  
      <Visible>...</Visible>  
      <Translations>...</Translations>  
   </AttributeRelationship>  
</AttributeRelationships>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AttributeRelationships](../../../analysis-services/scripting/collections/attributerelationships-element-assl.md)|  
|子要素|[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、 [AttributeID](../../../analysis-services/scripting/properties/attributeid-element-assl.md)、[基数](../../../analysis-services/scripting/properties/cardinality-element-assl.md)、[名前](../../../analysis-services/scripting/properties/name-element-assl.md)、 [Optionality](../../../analysis-services/scripting/properties/optionality-element-assl.md)、 [OverrideBehavior](../../../analysis-services/scripting/properties/overridebehavior-element-assl.md)、 [RelationshipType](../../../analysis-services/scripting/properties/relationshiptype-element-assl.md)、[翻訳](../../../analysis-services/scripting/collections/translations-element-assl.md)、[表示](../../../analysis-services/scripting/properties/visible-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.AttributeRelationship>します。  
  
## <a name="see-also"></a>参照  
 [オブジェクト &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
