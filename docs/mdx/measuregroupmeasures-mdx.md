---
title: "MeasureGroupMeasures (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: kbMDX
helpviewer_keywords: MeasureGroupMeasures function
ms.assetid: 69d9b205-1ca7-4741-9ca9-c7926bc87ead
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 41e6b89b661dbf500f4b9908574244a616af6372
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="measuregroupmeasures-mdx"></a>MeasureGroupMeasures (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定されたメジャー グループに属するメジャーのセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
MEASUREGROUPMEASURES(MeasureGroupName)  
```  
  
## <a name="arguments"></a>引数  
 *MeasureGroupName*  
 メジャーのセットの取得元となるメジャー グループの名前が格納されている有効な文字列式です。  
  
## <a name="remarks"></a>解説  
 指定する文字列は、メジャー グループの名前と正確に一致する必要があります。 スペースを含むメジャー グループ名を角かっこで囲む必要はありません。  
  
## <a name="example"></a>例  
 次の例では、Adventure Works キューブの Internet Sales メジャー グループ内のメジャーがすべて返されます。  
  
```  
SELECT MeasureGroupMeasures('Internet Sales') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
