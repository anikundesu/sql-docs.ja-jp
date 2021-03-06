---
title: "NullKeyNotAllowed 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
apiname: NullKeyNotAllowed Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: NullKeyNotAllowed
helpviewer_keywords: NullKeyNotAllowed element
ms.assetid: 4ece99eb-954b-4da1-add4-dd9efd5fff0a
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e843c4b020c71fe502c32f557e5e1b88b95285b9
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="nullkeynotallowed-element-assl"></a>NullKeyNotAllowed 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]決定する方法、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]処理エンジンが処理中に発生した null キー エラーを処理します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ErrorConfiguration>  
   ...  
   <NullKeyNotAllowed>...</NullKeyNotAllowed>  
   ...  
</ErrorConfiguration>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*[Reportandcontinue]*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ErrorConfiguration](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 NULL キー エラーは、NULL 値が許可されていないキー列で NULL 値が検出され、処理中にレコードが破棄された場合に発生します。 場合にのみ、ただし、このエラーが発生、 [NullProcessing](../../../analysis-services/scripting/properties/nullprocessing-element-assl.md)要素を**DataItem**の先祖、 **ErrorConfiguration**に設定されている親要素*エラー*です。  
  
 この要素の値は、次の表のいずれかの文字列に制限されます。  
  
|値|Description|  
|-----------|-----------------|  
|*IgnoreError*|処理は、エラーを無視し、続行します。|  
|*[Reportandcontinue]*|処理は、エラーを報告し、続行します。|  
|*ReportAndStop*|処理は、停止、エラーを報告します。|  
  
 許可される値に対応する列挙**NullKeyNotAllowed**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ErrorOption>します。  
  
## <a name="see-also"></a>参照  
 [ErrorConfiguration 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)  
  
  
