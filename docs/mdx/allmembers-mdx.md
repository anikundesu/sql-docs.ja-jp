---
title: "AllMembers (MDX) |Microsoft ドキュメント"
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
f1_keywords: ALLMEMBERS
dev_langs: kbMDX
helpviewer_keywords: AllMembers function
ms.assetid: 202e81d4-d2ee-4ec1-a019-4835eb19f446
caps.latest.revision: "44"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: b4953bd5bff4ab578cc492991918ee5c90abb7a1
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="allmembers-mdx"></a>AllMembers (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  階層式またはレベル式を評価し、指定された階層またはレベルのすべてのメンバー (計算されるメンバーも含む) を格納したセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Hierarchy syntax  
Hierarchy_Expression.AllMembers  
  
Level syntax  
Level_Expression.AllMembers  
```  
  
## <a name="arguments"></a>引数  
 *Hierarchy_Expression*  
 階層を返す有効な多次元式 (MDX) 式です。  
  
 *Level_Expression*  
 レベルを返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 **AllMembers**関数を指定された階層またはレベルで、計算されるメンバーを含むすべてのメンバーを含むセットを返します。 **AllMembers**関数が、指定された階層またはレベルが表示できるメンバーに含まれない場合でも、計算されるメンバーを返します。  
  
> [!IMPORTANT]  
>  ディメンションに表示されている 1 つの階層のみが含まれている場合、階層を構成できますディメンション名、または階層名を参照ディメンションの名前がここでは、表示のみの階層に解決されるためです。 たとえば、`Measures.AllMembers`有効な MDX 式は、Measures ディメンション内の唯一の階層に解決されるためです。  
  
> [!NOTE]  
>  **AllMembers**関数に意味が似て、 [AddCalculatedMembers (MDX)](../mdx/addcalculatedmembers-mdx.md)関数。  
  
## <a name="examples"></a>使用例  
 次の例は、すべてのメンバーを返します、[`Date].[Calendar Year]`列軸で属性階層、これが含まれています計算されるメンバー、およびすべての子のセット、`[Product].[Model Name]`属性階層からの行軸、 **Adventure Works**キューブ。  
  
```  
SELECT  
   [Date].[Calendar Year].AllMembers ON COLUMNS,  
   [Product].[Model Name].Children ON ROWS  
FROM  
   [Adventure Works]  
```  
  
 次の例は、すべてのメンバーを返します、**メジャー**ディメンションで列の軸が含まれますすべての計算されるメンバー、およびすべての子のセット、`[Product].[Model Name]`属性階層からの行軸、 **Adventure Works**キューブ。  
  
```  
SELECT  
    Measures.AllMembers ON COLUMNS,  
    [Product].[Model Name].Children ON ROWS  
FROM  
    [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [AddCalculatedMembers &#40;です。MDX と #41 です。](../mdx/addcalculatedmembers-mdx.md)   
 [子と #40 です。MDX と #41 です。](../mdx/children-mdx.md)   
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
