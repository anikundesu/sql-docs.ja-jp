---
title: "-(コメント) (MDX) |Microsoft ドキュメント"
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
f1_keywords: --
dev_langs: kbMDX
helpviewer_keywords:
- commenting characters
- -- (comment character)
ms.assetid: 02aec133-6809-4829-b9a2-102c376e21da
caps.latest.revision: "40"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 964195bc8af57de5855beaf695a554019a7c0d32
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="comment---mdx-operator-reference"></a>コメントの MDX 演算子リファレンス
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  ユーザーが指定したコメントのテキストを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
-- Comment_Text      
```  
  
#### <a name="parameters"></a>パラメーター  
 *Comment_Text*  
 コメントのテキストを含む文字列です。  
  
## <a name="remarks"></a>解説  
 コメントは、別個の行として挿入することも、多次元式 (MDX) スクリプトの行の末尾で入れ子にすることも、MDX ステートメント内で入れ子にすることも可能です。 サーバーはコメントを評価しません。  
  
 1 行のコメントまたは入れ子にしたコメントには、この演算子を使用します。 -- によって挿入するコメントは、改行文字で区切ります。  
  
 コメントの長さには制限がありません。  
  
## <a name="examples"></a>使用例  
 この演算子の使用例を以下に示します。  
  
```  
-- This member returns the gross profit margin for product types  
-- and reseller types crossjoined by year.  
SELECT   
    [Date].[Calendar].[Calendar Year].Members *  
      [Reseller].[Reseller Type].Children ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM -- Select from the Adventure Works cube.  
    [Adventure Works]  
WHERE  
    [Measures].[Gross Profit Margin]  
```  
  
## <a name="see-also"></a>参照  
 [コメント &#40;MDX&#41;](../mdx/comment-mdx.md)   
 [&#40;です。コメント &#41;&#40;です。MDX と #41 です。](../mdx/comment-mdx-double-slash.md)   
 [MDX 演算子リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-operator-reference-mdx.md)  
  
  
