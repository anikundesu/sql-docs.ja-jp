---
title: "ReportAction データ型 (ASSL) |Microsoft ドキュメント"
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
apiname: ReportAction Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: ReportAction
helpviewer_keywords: ReportAction data type
ms.assetid: b22f0d52-ed3a-4239-840e-0eaf172d7276
caps.latest.revision: "40"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7eb9764d898ac72407ea6fb6940a3875fc6e96af
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="reportaction-data-type-assl"></a>ReportAction データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]生成するアクションを表す派生データ型を定義、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]レポートします。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ReportAction>  
   <!-- The following elements extend Action -->  
   <ReportServer>...</ReportServer>  
   <Path>...</Path>  
   <ReportParameters>...</ReportParameters>  
   <ReportFormatParameters>...</ReportFormatParameters>  
</ReportAction>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|[操作](../../../analysis-services/scripting/data-type/action-data-type-assl.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[パス](../../../analysis-services/scripting/properties/path-element-assl.md)、 [ReportFormatParameters](../../../analysis-services/scripting/collections/reportformatparameters-element-assl.md)、 [ReportParameters](../../../analysis-services/scripting/collections/reportparameters-element-assl.md)、 [ReportServer](../../../analysis-services/scripting/properties/reportserver-element-assl.md)|  
|派生要素|[アクション](../../../analysis-services/scripting/objects/action-element-assl.md)([アクション](../../../analysis-services/scripting/collections/actions-element-assl.md)のコレクション[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)または[パースペクティブ](../../../analysis-services/scripting/objects/perspective-element-assl.md))|  
  
## <a name="remarks"></a>解説  
 レポート サーバーは、レポートに関する URL ベースの要求に応答します。 型を持つレポート アクションが定義されている*レポート*です。 リソースおよびパラメーターは、アクションの作成時にサーバーに送信されます。 サーバーは、rowset 型のアクションとしてアクションを公開します。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.ReportAction>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
