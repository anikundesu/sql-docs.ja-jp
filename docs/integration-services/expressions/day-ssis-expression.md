---
title: "DAY (SSIS 式) | Microsoft Docs"
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
- DAY function
- dates [Integration Services], DAY
ms.assetid: d8447187-49df-45b7-a98e-142ad44fd3e2
caps.latest.revision: "38"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d668b8fc2d869066791b84724219b7d2525d741c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="day-ssis-expression"></a>DAY (SSIS 式)
  ある日付の、日の日付要素を表す整数値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
DAY(date)  
```  
  
## <a name="arguments"></a>引数  
 *date*  
 有効な日付または日付形式の文字列を返す式です。  
  
## <a name="result-types"></a>戻り値の型  
 DT_I4  
  
## <a name="remarks"></a>解説  
 引数が NULL の場合、DAY は NULL を返します。  
  
 日付リテラルは、日付データ型のいずれかに明示的にキャストされる必要があります。 詳細については、「 [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md)」を参照してください。  
  
> [!NOTE]  
>  日付リテラルが DT_DBTIMESTAMPOFFSET と DT_DBTIMESTAMP2 のいずれかの日付データ型に明示的にキャストされると、式の検証は失敗します。  
  
 DAY 関数を使用すると、DATEPART("DAY", date) 関数を使用する場合と同じ結果を、より簡単に取得できます。  
  
## <a name="expression-examples"></a>式の例  
 この例は、日付リテラルの日数を返します。 データ形式が "mm/dd/yyyy" 形式の場合、この例は 23 を返します。  
  
```  
DAY((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 この例は、 **ModifiedDate** 列内の日を表す整数を返します。  
  
```  
DAY(ModifiedDate)  
```  
  
 この例は、現在の日付の日を表す整数を返します。  
  
```  
DAY(GETDATE())  
```  
  
## <a name="see-also"></a>参照  
 [DATEADD &#40;SSIS 式&#41;](../../integration-services/expressions/dateadd-ssis-expression.md)   
 [DATEDIFF &#40;SSIS 式&#41;](../../integration-services/expressions/datediff-ssis-expression.md)   
 [DATEPART &#40;SSIS 式&#41;](../../integration-services/expressions/datepart-ssis-expression.md)   
 [MONTH &#40;SSIS 式&#41;](../../integration-services/expressions/month-ssis-expression.md)   
 [YEAR &#40;SSIS 式&#41;](../../integration-services/expressions/year-ssis-expression.md)   
 [関数 (SSIS 式)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
