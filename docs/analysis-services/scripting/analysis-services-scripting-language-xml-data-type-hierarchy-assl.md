---
title: "Analysis Services スクリプト言語の XML データ型階層 (ASSL) |Microsoft ドキュメント"
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
apiname: Analysis Services Scripting Language XML Data Type Hierarchy
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- ASSL, data types
- Analysis Services Scripting Language, data types
- data types [Analysis Services Scripting Language]
- inheritance [Analysis Services Scripting Language]
- hierarchies [Analysis Services Scripting Language]
ms.assetid: f143c9f8-225d-495d-ac8e-ac2d2a7b4c07
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0ce62ac4aad7532b53c66d34f9d55e2097217fdb
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="analysis-services-scripting-language-xml-data-type-hierarchy-assl"></a>Analysis Services スクリプト言語の XML データ型階層 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]次の表は、Analysis Services スクリプト言語 (ASSL) のデータ型の継承階層を表示します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
Action  
      DrillThroughAction  
      ReportAction  
      StandardAction  
AggregationAttribute  
AggregationDesignAttribute  
AggregationDesignDimension  
AggregationDimension  
Assembly  
      ClrAssembly  
      ComAssembly  
AttributeTranslation  
Binding  
      AttributeBinding  
      ColumnBinding  
      CubeAttributeBinding  
      CubeDimensionBinding  
      DataSourceViewBinding  
      DimensionBinding  
      InheritedBinding  
      MeasureBinding  
      MeasureGroupBinding  
      MeasureGroupDimensionBinding  
      PartitionBinding  
      ProactiveCachingBinding  
            ProactiveCachingIncrementalProcessingBinding  
            ProactiveCachingObjectNotificationBinding  
                  ProactiveCachingInheritedBinding  
                  ProactiveCachingTablesBinding  
            ProactiveCachingQueryBinding  
      RowBinding  
      TabularBinding  
            DSVTableBinding  
            QueryBinding  
            TableBinding  
      TimeAttributeBinding  
      TimeBinding  
      UserDefinedGroupBinding  
ClrAssemblyFile  
CubeAttribute  
CubeBinding (out-of-line)  
CubeDimension  
CubeDimensionPermission  
CubeHierarchy  
DataBlock  
DataItem  
DataMiningMeasureGroupDimension  
DegenerateMeasureGroupDimension  
DimensionAttribute  
EventColumn  
ManyToManyMeasureGroupDimension  
MeasureGroupAttribute  
MeasureGroupBinding (out-of-line)  
MeasureGroupDimension  
MeasureGroupHierarchy  
MiningModelColumn  
MiningModelingFlag  
MiningStructureColumn  
OlapDataSource  
Permission  
PerspectiveAction  
PerspectiveAttribute  
PerspectiveCalculation  
PerspectiveDimension  
PerspectiveHierarchy  
PerspectiveKpi  
PerspectiveMeasure  
PerspectiveMeasureGroup  
PushedDataSource  
ReferenceMeasureGroupDimension  
RegularMeasureGroupDimension  
RelationalDataSource  
ScalarMiningStructureColumn  
TableMiningStructureColumn  
```  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 &#40;です。ASSL &#41;](../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)   
 [Analysis Services スクリプト言語の XML 要素の階層 &#40;です。ASSL &#41;](../../analysis-services/scripting/analysis-services-scripting-language-xml-element-hierarchy-assl.md)   
 [Analysis Services スクリプト言語 &#40;です。ASSL を XMLA &#41;](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md)  
  
  
