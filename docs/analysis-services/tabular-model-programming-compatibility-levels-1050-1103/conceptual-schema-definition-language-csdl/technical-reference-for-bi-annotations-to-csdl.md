---
title: "CSDL への BI 注釈のテクニカル リファレンス |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
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
applies_to: SQL Server 2016 Preview
ms.assetid: 63b3e069-6ba5-474e-b769-47b7cc87b7dd
caps.latest.revision: "16"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: be086d8e2a61ffbf5871c12b73cb628f656414ac
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="technical-reference-for-bi-annotations-to-csdl"></a>CSDL への BI 注釈のテクニカル リファレンス
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]このセクションで示します要素、属性、および CSDL で使用されるプロパティを表す[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]表形式モデル。 一部の新規要素以外は、ビジネス インテリジェンス モデリングをサポートするために注釈が付加されたか、拡張されたものです。  
  
 表形式モデルとエンティティ、リレーションシップ、および数式が CSDL で表現する方法の概要については、次を参照してください[Business Intelligence &#40; 向けの CSDL 注釈。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/csdl-annotations-for-business-intelligence-csdlbi.md).  
  
## <a name="extended-csdl-elements-complex-types"></a>拡張 CSDL 要素: 複合型  
 CSDL の次の要素が、テーブルと多次元の両方のビジネス インテリジェンス データ モデルをサポートするために追加または拡張されました。  
  
-   [AssociationSet 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/associationset-element-csdlbi.md)  
  
-   [BaseProperty 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/baseproperty-element-csdlbi.md)  
  
-   [DefaultDetails 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/defaultdetails-element-csdlbi.md)  
  
-   [DisplayKey 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/displaykey-element-csdlbi.md)  
  
-   [EntityContainer 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/entitycontainer-element-csdlbi.md)  
  
-   [EntitySet 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/entityset-element-csdlbi.md)  
  
-   [EntityType 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/entitytype-element-csdlbi.md)  
  
-   [Hierarchy 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/hierarchy-element-csdlbi.md)  
  
-   [KPI 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/kpi-element-csdlbi.md)  
  
-   [KpiGoal 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/kpigoal-element-csdlbi.md)  
  
-   [KpiStatus 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/kpistatus-element-csdlbi.md)  
  
-   [Level 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/level-element-csdlbi.md)  
  
-   [Measure 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/measure-element-csdlbi.md)  
  
-   [Member 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/member-element-csdlbi.md)  
  
-   [MemberRef 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/memberref-element-csdlbi.md)  
  
-   [NavigationProperty 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/navigationproperty-element-csdlbi.md)  
  
-   [プロパティ要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/property-element-csdlbi.md)  
  
-   [PropertyRef 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/propertyref-element-csdlbi.md)  
  
## <a name="simple-type-and-subtypes"></a>単純型とサブタイプ  
 次の表に、前の一覧の複合型の定義に含まれる単純型と副次的な複合型の一部を示します。 左列の単純型とサブタイプについてのドキュメントは、右列の親要素で用意されています。  
  
|単純型|」を参照します。|  
|-----------------|--------------------|  
|Alignment|[BaseProperty 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/baseproperty-element-csdlbi.md)|  
|CompareOptions|[EntityContainer 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/entitycontainer-element-csdlbi.md)|  
|目次|[EntityType 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/entitytype-element-csdlbi.md)|  
|ContextualNameRule|[Member 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/member-element-csdlbi.md)|  
|DefaultAggregationFunction|[プロパティ要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/property-element-csdlbi.md)|  
|DirectQueryMode|[EntityContainer 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/entitycontainer-element-csdlbi.md)|  
|GroupingBehavior|[プロパティ要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/property-element-csdlbi.md)|  
|MemberRefs|[MemberRef 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/memberref-element-csdlbi.md)|  
|PropertyRefs|[PropertyRef 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/propertyref-element-csdlbi.md)|  
|SortDirection|[BaseProperty 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/baseproperty-element-csdlbi.md)|  
|状態|[AssociationSet 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/associationset-element-csdlbi.md)|  
|Stability|[プロパティ要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/property-element-csdlbi.md)|  
|SortDirection|[BaseProperty 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/baseproperty-element-csdlbi.md)|  
  
## <a name="see-also"></a>参照  
 [CSDLBI の概念](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/csdlbi-concepts.md)  
  
  
