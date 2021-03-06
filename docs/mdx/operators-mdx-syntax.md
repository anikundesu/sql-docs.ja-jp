---
title: "演算子 (MDX 構文) |Microsoft ドキュメント"
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
dev_langs: kbMDX
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], operators
- operators [MDX]
- precedence [MDX]
- MDX [Analysis Services], operators
ms.assetid: 1ff5a529-88fd-4619-86e1-19fa214650d6
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: f7d13bdd9c8d5abd19e6b64d92e45bcd688feeef
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="operators-mdx-syntax"></a>演算子 (MDX 構文)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  多次元式 (MDX) では、演算子を使用して以下の操作を実行できます。  
  
-   永続的または一時的なデータ変更  
  
-   指定した条件を満たしている値またはオブジェクトの検索  
  
-   値の間または式の間での判断  
  
-   トランザクションの開始やコミット、または特定のステートメントの実行の前に行う特定の条件に対する試験  
  
 MDX では、以下の表に示す演算子がサポートされます。  
  
|演算の種類|新しく使用する機能|  
|---------------------------------------|---------|  
|変数に値を代入するかまたは結果セット列を別名に関連付けます。|[代入演算子](../mdx/assignment-operators.md)|  
|加算、減算、乗算、除算。|[算術演算子](../mdx/arithmetic-operators.md)|  
|AND、OR、NOT、XOR などの条件が真かどうか調べます。|[ビット処理演算子](../mdx/bitwise-operators.md)|  
|値を他の値または式と比較します。|[比較演算子](../mdx/comparison-operators.md)|  
|2 つの文字列を永続的または一時的に 1 つの文字列に結合します。|[連結演算子](../mdx/concatenation-operators.md)|  
|2 つのセット式を永続的または一時的に 1 つのセットに結合します。|[セット演算子](../mdx/set-operators.md)|  
|1 つのオペランドに対して 1 つの演算を行います。|[単項演算子](../mdx/unary-operators.md)|  
  
> [!NOTE]  
>  クエリ内では、特定の種類の演算子と共に使用するキューブのデータを読み取ることができるユーザーは演算を実行できます。 ただし、データを変更するには適切な権限が必要です。  
  
 複数の演算子を使用する場合、MDX によって演算子が評価される順序は重要です。 同様に重要な点として、演算子を評価する前に、あるデータ型を別のデータ型に変換しておかなければならない場合もあります。  
  
## <a name="evaluating-complex-expressions"></a>複雑な式の評価  
 演算子を使用すると、複数の小さい式を結合して 1 つの式を作成できます。 これらの複雑な式に MDX 演算子によって使用される演算子の優先順位の定義に基づく順序で[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]です。 MDX は、優先順位の高い演算子を、優先順位の低い演算子より先に実行します。  
  
### <a name="understanding-operator-precedence"></a>演算子の優先順位について  
 以下の一覧に、演算子を優先順位の高いものから順に示します。 同じ行に示されている演算子は優先順位が同じです。かっこによる強制的な優先がない限り、左から右の順に評価されます。  
  
-   IS  
  
-   AS  
  
-   DISTINCT  
  
-   [ ] :  
  
-   ^  
  
-   /, *  
  
-   +, -  
  
-   EXISTING  
  
-   <>, >=, =, \<=, >, <  
  
-   [NOT]  
  
-   [AND]  
  
-   XOR  
  
-   または  
  
 MDX の演算子の詳細については、次を参照してください。 [MDX 演算子リファレンス &#40;です。MDX と #41 です;](../mdx/mdx-operator-reference-mdx.md)。  
  
### <a name="determining-results"></a>結果の決定  
 単純な式を結合して複雑な式を作成する場合、演算子に関する規則とデータ型の優先順位に関する規則の組み合わせによって、結果の値のデータ型が決まります。  
  
 結果が文字値または Unicode 値の場合、演算子に関する規則と照合順序の優先順位に関する規則の組み合わせによって、結果の照合順序が決まります。 照合順序の詳細については、次を参照してください。[言語および照合順序と #40 です。Analysis Services &#41;](../analysis-services/languages-and-collations-analysis-services.md).  
  
 単純式の有効桁数、小数点以下桁数、長さに基づいて結果の有効桁数、小数点以下桁数、長さを指定するルールもあります。  
  
## <a name="converting-data-types"></a>データ型の変換  
 MDX では、あるオブジェクトが別のデータ型を必要とする式の中で使用されている場合、そのオブジェクトを別のデータ型へ暗黙的に変換します。 各オブジェクトは、次の表に示す規則に従って変換されます。  
  
|元の型|必要な型|変換|  
|-------------------|-----------------|----------------|  
|レベル|オン|\<レベル > ですメンバー。|  
|階層|メンバー|\<階層 > .defaultmember|  
|メンバー|組|(\<メンバー >)|  
|組|メンバー|\<タプル > .item(0)|  
|組|スカラー|\<タプル > .value|  
  
## <a name="see-also"></a>参照  
 [MDX 演算子リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-operator-reference-mdx.md)   
 [MDX 構文の要素 &#40;です。MDX と #41 です。](../mdx/mdx-syntax-elements-mdx.md)  
  
  
