---
title: "+ (追加)(DMX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: DMX
helpviewer_keywords:
- + (add)
- add operator (+)
ms.assetid: 35e7636f-814c-44c3-94a7-384a305d65ea
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: ef0709148ffb59ec95cb57b29bdcddf0e1acaf64
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="-add-dmx"></a>+ (加算) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  2 つの数字を加算する算術演算子を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Numeric_Expression + Numeric_Expression  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Numeric_Expression*  
 数値を返す有効なデータ マイニング拡張機能 (DMX) 式です。  
  
## <a name="return-value"></a>戻り値  
 優先順位の高いパラメーターのデータ型を持つ値です。  
  
## <a name="remarks"></a>解説  
 両方の式は、同じデータ型でなければなりません。または、一方の式をもう一方の式のデータ型に暗黙的に変換できる必要があります。 1 つの式が NULL 値に評価される場合、この演算子は、もう一方の式の結果を返します。  
  
## <a name="see-also"></a>参照  
 [算術演算子 &#40; DMX &#41;](../dmx/operators-arithmetic.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [演算子 &#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
