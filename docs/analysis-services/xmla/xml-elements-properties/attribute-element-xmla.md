---
title: "属性の要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Attribute Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Attribute
- microsoft.xml.analysis.attribute
- urn:schemas-microsoft-com:xml-analysis#Attribute
helpviewer_keywords: Attribute element
ms.assetid: 0df9cf44-dc5f-4234-8a5a-daac8aabc0d6
caps.latest.revision: "17"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b2100479529d5d7ca15bd8b6dcf0600088617c02
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="attribute-element-xmla"></a>Attribute 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]定義またはフィルターの対象である属性内のメンバー、親[挿入](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)、[更新](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)、または[ドロップ](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)コマンドを実行します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Attributes>  
   ...  
   <Attribute>  
      <AttributeName>...</AttributeName>  
      <Keys>...</Keys>  
      <!-- The following elements are included only for attributes contained in the Attributes element of a parent Insert or Update command -->  
      <Name>...</Name>  
      <Translations>...</Translations>  
      <CustomRollup>...</CustomRollup>  
      <CustomRollupProperties>...</CustomRollupProperties>  
      <UnaryOperator>...</UnaryOperator>  
      <SkippedLevels>...</SkippedLevels>  
   </Attribute>  
   ...  
</Attributes>  
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
|親要素|[属性](../../../analysis-services/xmla/xml-elements-properties/attributes-element-xmla.md)|  
|子要素|次の表を参照してください。|  
  
|先祖または親|子要素|  
|------------------------|-------------------|  
|[Drop](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)、[場所](../../../analysis-services/xmla/xml-elements-properties/where-element-xmla.md)|[AttributeName](../../../analysis-services/xmla/xml-elements-properties/attributename-element-xmla.md)、[キー](../../../analysis-services/xmla/xml-elements-properties/keys-element-xmla.md)|  
|[挿入](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)、[更新](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)|[AttributeName](../../../analysis-services/xmla/xml-elements-properties/attributename-element-xmla.md)、 [[customrollup]](../../../analysis-services/xmla/xml-elements-properties/customrollup-element-xmla.md)、 [[customrollupproperties]](../../../analysis-services/xmla/xml-elements-properties/customrollupproperties-element-xmla.md)、[キー](../../../analysis-services/xmla/xml-elements-properties/keys-element-xmla.md)、[名前](../../../analysis-services/xmla/xml-elements-properties/name-element-xmla.md)、 [SkippedLevels](../../../analysis-services/xmla/xml-elements-properties/skippedlevels-element-xmla.md)、[翻訳](../../../analysis-services/xmla/xml-elements-properties/translations-element-xmla.md)、 [[unaryoperator]](../../../analysis-services/xmla/xml-elements-properties/unaryoperator-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
 **Attribute** 要素は、 **Insert**、 **Update**、または **Drop** コマンドによって、挿入、更新、または削除される属性メンバーを定義します。 1 つの属性メンバーだけで、一度に処理できるためにこれらのコマンド、[属性](../../../analysis-services/xmla/xml-elements-properties/attributes-element-xmla.md)のコレクション、**挿入**、**更新**、および**をドロップ**コマンドには、1 つだけ含めることができます**属性**要素。 ただし、 **Attributes** および **Where** コマンドの **Drop** 要素の **Update** コレクションには複数の **Attribute** 要素を含めることができ、書き込み許可ディメンション内の削除または更新対象の属性をフィルター処理できます。  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)   
 [書き込み許可ディメンション](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
