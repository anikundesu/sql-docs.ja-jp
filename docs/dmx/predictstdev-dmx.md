---
title: "PredictStdev (DMX) |Microsoft ドキュメント"
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
f1_keywords: PredictStdev
dev_langs: DMX
helpviewer_keywords: PredictStdev function
ms.assetid: 2614aad0-f3f2-4f56-9dad-9c436f11a35f
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 63a4d43c4c851f4bc03675fe06220e3a42827a85
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="predictstdev-dmx"></a>PredictStdev (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定された列に対して、予測された標準偏差を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
PredictStdev(<scalar column reference>)  
```  
  
## <a name="applies-to"></a>適用対象  
 スカラー列です。  
  
## <a name="return-type"></a>戻り値の型  
 指定された型のスカラー値*\<スカラー列参照 >*です。  
  
## <a name="remarks"></a>解説  
 列参照が不連続で場合**PredictStdev**不連続の値から標準偏差を計算できないために、0 を返します。  
  
## <a name="examples"></a>使用例  
 次の例は、自然予測結合を使用して、個人が TM Decision Tree マイニング モデルに基づいた自転車購入者である可能性を判断します。また、予測の標準偏差も判断します。  
  
```  
SELECT  
  [Bike Buyer],  
  PredictStdev([Bike Buyer]) AS [Standard Deviation]  
FROM  
  [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 &#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [関数 &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [一般的な予測関数 &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
