---
title: "&amp;&amp; (論理 AND) (SSIS 式) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: expressions
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '&& (logical AND)'
- AND, logical AND
- logical AND (&&)
ms.assetid: a8cb3517-d5d1-4861-9f04-905c719185ff
caps.latest.revision: "33"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: be65e95a28cedfcd697ef79b87adfe0096ac84ef
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="ampamp-logical-and-ssis-expression"></a>&amp;&amp; (論理 AND) (SSIS 式)
  論理 AND 演算を実行します。 両方の条件が TRUE の場合、式は TRUE に評価されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
boolean_expression1 && boolean_expression2  
```  
  
## <a name="arguments"></a>引数  
 *boolean _expression1, boolean_expression2*  
 TRUE、FALSE、または NULL に評価される、任意の有効な式です。  
  
## <a name="result-types"></a>戻り値の型  
 DT_BOOL  
  
## <a name="remarks"></a>解説  
 次の表は、&& 演算子の結果を示します。  
  
|結果|式|式|  
|------------|----------------|----------------|  
|TRUE|TRUE|TRUE|  
|FALSE|TRUE|FALSE|  
|FALSE|FALSE|FALSE|  
|NULL|NULL|NULL|  
|NULL|NULL|TRUE|  
|FALSE|NULL|FALSE|  
  
## <a name="expression-examples"></a>式の例  
 この例では、 **StandardCost** 列と **ListPrice** 列を使用しています。 **StandardCost** 列の値が 300 より小さく、かつ **ListPrice** 列の値が 500 より大きい場合、式は TRUE に評価されます。  
  
```  
StandardCost < 300 && ListPrice > 500  
```  
  
 この例では、リテラルの代わりに変数 **SPrice** と **LPrice** を使用しています。  
  
```  
StandardCost < @SPrice && ListPrice > @LPrice  
```  
  
## <a name="see-also"></a>参照  
 [& (ビット演算子 AND) (SSIS 式)](../../integration-services/expressions/bitwise-and-ssis-expression.md)   
 [演算子の優先順位と結合規則](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [演算子 (SSIS 式)](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
