---
title: "メンバー、組、およびセット (MDX) での作業 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/13/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDX [Analysis Services], tuples
- member keys [MDX]
- MDX [Analysis Services], sets
- calculated members [MDX]
- members [MDX]
- Multidimensional Expressions [Analysis Services], members
- named sets [MDX]
- Multidimensional Expressions [Analysis Services], tuples
- member functions [MDX]
- sets [MDX]
- MDX [Analysis Services], members
- member names [MDX]
- Multidimensional Expressions [Analysis Services], sets
- tuple functions
- tuples
- set functions [MDX]
ms.assetid: b6ec2439-caef-46d3-9fd7-5f4526cee334
caps.latest.revision: "41"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 63b558fadebc2598da0969e13eac04d75aa4ef94
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="working-with-members-tuples-and-sets-mdx"></a>メンバー、組、およびセットの操作 (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]MDX には多数の関数を 1 つ以上のメンバー、組、またはセットを返すまたは、メンバー、組、に対して操作を実行する、または設定します。  
  
## <a name="member-functions"></a>メンバー関数  
 MDX には、ディメンション、レベル、セット、組などの他の MDX エンティティからメンバーを取得するための関数がいくつかあります。 たとえば、 [FirstChild](../../../mdx/firstchild-mdx.md) 関数はメンバーに対して操作を実行してメンバーを返す関数です。  
  
 時間ディメンションの最初の子メンバーを取得するには、次の例のように、明示的にメンバーを指定できます。  
  
```  
SELECT [Date].[Calendar Year].[CY 2001] on 0  
FROM [Adventure Works]  
  
```  
  
 または、次の例のように、 **FirstChild** 関数を使用して同じメンバーを返すこともできます。  
  
```  
SELECT [Date].[Calendar Year].FirstChild on 0  
FROM [Adventure Works]  
  
```  
  
 MDX メンバー関数の詳細については、「 [MDX 関数リファレンス &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md)」をご覧ください。  
  
## <a name="tuple-functions"></a>組関数  
 MDX には、組を返す関数がいくつかあります。これらの関数は、組を使用できる任意の箇所で使用できます。 たとえば、[Item &#40;組&#41; &#40;MDX&#41;](../../../mdx/item-tuple-mdx.md) 関数はセットから最初の組を抽出するために使用できます。これは、セットに含まれているのが単一の組であるとわかっており、組を 1 つ必要とする関数にその組を渡す場合に非常に便利です。  
  
 次の例では、列軸上の組のセット内から最初の組を返します。  
  
```  
SELECT {  
   ([Measures].[Reseller Sales Amount]  
      ,[Date].[Calendar Year].[CY 2003]  
   )  
, ([Measures].[Reseller Sales Amount]  
      ,[Date].[Calendar Year].[CY 2004]  
   )  
}.Item(0)  
ON COLUMNS   
FROM [Adventure Works]  
```  
  
 組関数の詳細については、「 [MDX 関数リファレンス &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md)」をご覧ください。  
  
## <a name="set-functions"></a>集合関数  
 MDX には、セットを返す関数がいくつかあります。 セットを取得する方法は、明示的に組を入力して中かっこで囲むだけではありません。 セットを返すメンバー関数の詳細については、「 [MDX の主な概念 &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)」をご覧ください。 他にも多くのセット関数があります。  
  
 コロン演算子を使用すれば、メンバーの順序を指定してセットを作成できます。 たとえば、次の例のセットには、2002 年度の第 1 四半期から第 4 四半期までの組が含まれます。  
  
```  
SELECT   
   {[Calendar Quarter].[Q1 CY 2002]:[Calendar Quarter].[Q4 CY 2002]}   
ON 0  
FROM [Adventure Works]  
```  
  
 コロン演算子を使用してセットを作成しない場合は、次の例のような組を指定することで、同じメンバー セットを作成できます。  
  
```  
SELECT {  
   [Calendar Quarter].[Q1 CY 2002],   
   [Calendar Quarter].[Q2 CY 2002],   
   [Calendar Quarter].[Q3 CY 2002],   
   [Calendar Quarter].[Q4 CY 2002]  
   } ON 0  
FROM [Adventure Works]  
  
```  
  
 コロン演算子は内包的な関数です。 コロン演算子の両側のメンバーはどちらも結果セットに含まれます。  
  
 セット関数の詳細については、「 [MDX 関数リファレンス &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md)」をご覧ください。  
  
## <a name="array-functions"></a>配列関数  
 配列関数は、セットに対して操作を実行して配列を返します。 配列関数の詳細については、「 [MDX 関数リファレンス &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md)」をご覧ください。  
  
## <a name="hierarchy-functions"></a>階層関数  
 階層関数は、メンバー、レベル、階層、または文字列に対して操作を実行して、階層を返します。 階層関数の詳細については、「 [MDX 関数リファレンス &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md)」をご覧ください。  
  
## <a name="level-functions"></a>レベル関数  
 レベル関数は、メンバー、レベル、または文字列に対して操作を実行して、レベルを返します。 レベル関数の詳細については、「 [MDX 関数リファレンス &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md)」をご覧ください。  
  
## <a name="logical-functions"></a>論理関数  
 論理関数は、MDX 式に対して操作を実行し、その式の組、メンバー、またはセットに関する情報を返します。 たとえば、[IsEmpty &#40;MDX&#41;](../../../mdx/isempty-mdx.md) 関数は、式から空のセル値が返されるかどうかを評価します。 論理関数の詳細については、「[MDX 関数リファレンス &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md)」をご覧ください。  
  
## <a name="numeric-functions"></a>数値関数  
 数値関数は、MDX 式に対して操作を実行してスカラー値を返します。 たとえば、[Aggregate &#40;MDX&#41;](../../../mdx/aggregate-mdx.md) 関数は、指定されたセットの組に対し、メジャーを集計することで計算されるスカラー値を返します。 数値関数の詳細については、「[MDX 関数リファレンス &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md)」をご覧ください。  
  
## <a name="string-functions"></a>文字列関数  
 文字列関数は、MDX 式に対して操作を実行して文字列を返します。 たとえば、[UniqueName &#40;MDX&#41;](../../../mdx/uniquename-mdx.md) 関数は、ディメンション、階層、レベル、メンバーの一意の名前を格納した文字列値を返します。 文字列関数の詳細については、「[MDX 関数リファレンス &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [MDX の主な概念 &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)   
 [MDX クエリの基礎と #40 です。Analysis Services &#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)   
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../../../mdx/mdx-function-reference-mdx.md)  
  
  
