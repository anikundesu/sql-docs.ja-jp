---
title: "TRIM (SSIS 式) | Microsoft Docs"
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
- leading blanks
- TRIM function
- trailing blanks
ms.assetid: 7dd9081d-a3d4-483a-bf7e-bf2bd7692d39
caps.latest.revision: "34"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 48ed42d0e12ed6b3d80c61a392b50a529813899e
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="trim-ssis-expression"></a>TRIM (SSIS 式)
  先頭および末尾のスペースを削除した後の文字式を返します。  
  
> [!NOTE]  
>  TRIM では、タブや改行文字などの空白文字は削除されません。 Unicode には各種スペースを表すコード ポイントが用意されていますが、この関数では Unicode コード ポイント 0x0020 のみが認識されます。 Unicode に変換される 2 バイト文字セット (DBCS) の文字列には、0x0020 以外のスペース文字が含まれる場合があり、このようなスペースはこの関数で削除できません。 すべての種類のスペースを削除するには、スクリプト コンポーネントから実行するスクリプト内で、Microsoft Visual Basic .NET の Trim メソッドを使用できます。  
  
## <a name="syntax"></a>構文  
  
```  
  
TRIM(character_expression)  
```  
  
## <a name="arguments"></a>引数  
 *character_expression*  
 スペースを削除する対象となる文字式です。  
  
## <a name="result-types"></a>戻り値の型  
 DT_WSTR  
  
## <a name="remarks"></a>解説  
 引数が NULL の場合、TRIM は NULL を返します。  
  
 TRIM は、DT_WSTR データ型でのみ機能します。 *character_expression* 引数が DT_STR データ型の文字列リテラルまたはデータ列である場合は、TRIM による演算の実行前に、暗黙的に DT_WSTR データ型にキャストされます。 その他のデータ型は、明示的に DT_WSTR データ型にキャストされる必要があります。 詳細については、「[Integration Services のデータ型](../../integration-services/data-flow/integration-services-data-types.md)」 および「[Cast (SSIS 式)](../../integration-services/expressions/cast-ssis-expression.md)」 を参照してください。  
  
## <a name="expression-examples"></a>式の例  
 この例では、文字列リテラルから先頭および末尾のスペースが削除されます。 返される結果は、"New York" です。  
  
```  
TRIM("   New York   ")  
```  
  
 この例では、 **FirstName** 列と **LastName** 列を連結した結果から、先頭および末尾のスペースが削除されます。 **FirstName** と **LastName** の間の空の文字列は、削除されません。  
  
```  
TRIM(FirstName + " "+ LastName)  
```  
  
## <a name="see-also"></a>参照  
 [LTRIM (SSIS 式)](../../integration-services/expressions/ltrim-ssis-expression.md)   
 [RTRIM &#40;SSIS 式&#41;](../../integration-services/expressions/rtrim-ssis-expression.md)   
 [関数 (SSIS 式)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
