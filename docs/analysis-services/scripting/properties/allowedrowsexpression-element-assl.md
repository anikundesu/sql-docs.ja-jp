---
title: "AllowedRowsExpression 要素 (ASSL) |Microsoft ドキュメント"
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
applies_to: SQL Server 2016 Preview
ms.assetid: ec24b11d-d11e-4369-a619-7e41a3c46159
caps.latest.revision: "6"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b4431e5c770f2948ae1c246cd05980737d39c005
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="allowedrowsexpression-element-assl"></a>AllowedRowsExpression 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]を親要素の内容を定義するブール型の Data Analysis expression (DAX) が含まれています。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CellPermission> <!-- or StandardAction -->  
   ...  
   <Expression>...</Expression>  
   ...  
</CellPermission>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CellPermission](../../../analysis-services/scripting/objects/cellpermission-element-assl.md)、 [StandardAction](../../../analysis-services/scripting/data-type/standardaction-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **CellPermission**要素、**式**要素にはによって示される権限に適用されるセルを識別する論理 MDX 式が含まれています、[アクセス](../../../analysis-services/scripting/properties/access-element-assl.md)要素、 **CellPermission**要素。 場合の値、**式**要素を**CellPermission**要素は空では、 **CellPermission**要素は無視されます。  
  
 **StandardAction**要素、**式**要素には、アクションの内容を表す MDX 式が含まれています。 場合の値、**式**要素を**StandardAction**要素は空では、 **StandardAction**要素は無視されます。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで親に対応する要素は、<xref:Microsoft.AnalysisServices.CellPermission> と <xref:Microsoft.AnalysisServices.StandardAction> です。  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
