---
title: "StrToSet (MDX) |Microsoft ドキュメント"
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
f1_keywords: STRTOSET
dev_langs: kbMDX
helpviewer_keywords: StrToSet function
ms.assetid: 1700a563-6527-450a-8d3b-975c65bb6e51
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 8b6b456c53dd0daf34d81240fcb1efa48749d24e
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="strtoset-mdx"></a>StrToSet (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  多次元式 (MDX) 形式の文字列によって指定されているセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
StrToSet(Set_Specification [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>引数  
 *Set_Specification*  
 直接的または間接的にセットを指定する有効な文字列式です。  
  
## <a name="remarks"></a>解説  
 **StrToSet**関数、文字列式で指定されたセットを返します。 **StrToSet**関数は、通常使用ユーザー定義関数またはを返すセットの指定を外部関数から MDX ステートメントでは、MDX クエリがパラメーター化されたときにします。  
  
-   CONSTRAINED フラグを使用する場合、セットの指定には、修飾されているメンバー名か修飾されていないメンバー名を使用するか、修飾されているメンバー名か修飾されていないメンバー名を含む組のセットを中かっこ {} で囲んで使用する必要があります。 このフラグは、指定された文字列によるインジェクション攻撃の危険性を軽減するために使用します。 修飾されているメンバー名または修飾されていないメンバー名に直接解決できない文字列が指定されると、"STRTOSET 関数の CONSTRAINED フラグによって設定された制限に違反しました。" というエラーが表示されます。  
  
-   CONSTRAINED フラグを使用しない場合、セットを返す有効な多次元式 (MDX) 式に解決されるセットの指定を指定できます。  
  
-   セットとメンバーの違いを理解するには、「セット式の使用」および「メンバー式の使用」を参照してください。  
  
## <a name="examples"></a>使用例  
 次の例を使用して、State-province 属性階層のメンバーのセットを返します、 **StrToSet**関数。 セットの指定には、有効な MDX セット式が指定されています。  
  
```  
SELECT StrToSet ('[Geography].[State-Province].Members')  
ON 0  
FROM [Adventure Works]  
  
```  
  
 次の例では、CONSTRAINED フラグが原因でエラーが返されます。 セットの指定には有効な MDX セット式が指定されていますが、CONSTRAINED フラグを使用する場合は、セットの指定に修飾されたメンバー名または修飾されていないメンバー名を含める必要があります。  
  
```  
SELECT StrToSet ('[Geography].[State-Province].Members', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
  
```  
  
 次の例では、ドイツとカナダの Reseller Sales Amount メジャーを返しています。 セットの指定には、CONSTRAINED フラグによって必要とされる、修飾されたメンバー名が含まれています。  
  
```  
SELECT StrToSet ('{[Geography].[Geography].[Country].[Germany],[Geography].[Geography].[Country].[Canada]}', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
