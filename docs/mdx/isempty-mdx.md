---
title: "IsEmpty (MDX) |Microsoft ドキュメント"
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
f1_keywords: ISEMPTY
dev_langs: kbMDX
helpviewer_keywords: IsEmpty function
ms.assetid: b4a50996-61d1-4e23-8003-7d530195ea72
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: c012af7c0df0ccc2507fb41097b9bcf58b97739c
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="isempty-mdx"></a>IsEmpty (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  評価した式が空のセル値かどうかを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
IsEmpty(Value_Expression)   
```  
  
## <a name="arguments"></a>引数  
 *Value_Expression*  
 有効な多次元式 (MDX) 式です。通常は、メンバーまたは組のセル座標を返します。  
  
## <a name="remarks"></a>解説  
 **IsEmpty**関数が返される**true**式の評価結果が空のセル値の場合。 この関数を返しますそれ以外の場合、 **false**です。  
  
> [!NOTE]  
>  メンバーの既定のプロパティは、そのメンバーの値です。  
  
 **IsEmpty**関数は、空のセル値に特別な意味があるため、空のセルを確実にテストする唯一の方法[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]です。  
  
> [!IMPORTANT]  
>  値式の評価エラーが返されます、この関数を返します**false**です。 値式がエラーを返すのは、たとえば、プロパティ参照によって、無効なプロパティまたは存在しないプロパティが参照されているような場合です。  
  
 空のセルの詳細については、OLE DB のドキュメントを参照してください。  
  
## <a name="example"></a>例  
 次の例では、Date ディメンションの Fiscal 階層にある現在のメンバーの Internet Sales Amount が空のセルを返す場合、TRUE を返します。  
  
 `WITH MEMBER MEASURES.ISEMPTYDEMO AS`  
  
 `IsEmpty([Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount],MEASURES.ISEMPTYDEMO} ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [空の値の扱い](../mdx/working-with-empty-values.md)   
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
