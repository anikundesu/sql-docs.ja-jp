---
title: "ReadWriteMode 要素 |Microsoft ドキュメント"
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
applies_to: SQL Server 2016 Preview
helpviewer_keywords: ReadWriteMode command
ms.assetid: 379bcaca-bb7e-4934-a9e7-21f8ede2fdc7
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8ed345b4e0562fd61b7995d91bd2db12cad4cd57
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="readwritemode-element"></a>ReadWriteMode 要素
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]**ReadWriteMode**データベース プロパティを指定するかどうか、データベースで**ReadWrite**モードまたは**ReadOnly**モード。 このプロパティの使用可能な値は 2 つだけです。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Database>  
...  
   <ddlns_100_0:ReadWriteMode>...</ddlns_100_0:ReadWriteMode>  
...  
</Database>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|ReadWrite|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[データベース](../../../analysis-services/xmla/xml-elements-properties/database-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 データベースを作成**ReadWrite**モードのみです。 データベースを作成することはできません**ReadOnly**モード。  
  
 値、 **ReadWriteMode**要素は次の表に示す文字列の 1 つに制限されます。  
  
|値|Description|  
|-----------|-----------------|  
|*読み取り専用*|変更または更新をデータベースに適用できません。|  
|*読み取り/書き込み*|変更または更新をデータベースに適用できます。|  
  
## <a name="see-also"></a>参照  
 [Attach 要素](../../../analysis-services/xmla/xml-elements-commands/attach-element.md)   
 [アタッチし、Analysis Services データベースのデタッチ](../../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [Analysis Services データベースを移動します。](../../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)   
 [データベースの Readwritemode](../../../analysis-services/multidimensional-models/database-readwritemodes.md)   
 [Analysis Services データベースの ReadOnly モードと ReadWrite モードの切り替え](../../../analysis-services/multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
  
