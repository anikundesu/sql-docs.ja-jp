---
title: "DrilldownMember (MDX) |Microsoft ドキュメント"
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
f1_keywords: DRILLDOWNMEMBER
dev_langs: kbMDX
helpviewer_keywords: DrilldownMember function
ms.assetid: 765f2fc7-0baa-428b-864a-22c9f3113083
caps.latest.revision: "40"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 35fb3fec36ffc3aacd68bab3baf4612942c5afd8
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="drilldownmember-mdx"></a>DrilldownMember (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  2 番目に指定されたセット内に存在する、指定されたセットのメンバーをドリル ダウンします。  
  
 または、最初の組階層または必要に応じて指定した階層を使用して、関数が組のセットをドリル ダウンします。  
  
## <a name="syntax"></a>構文  
  
```  
  
DrillDownMember(<Set_Expression1>, <Set_Expression2> [,[<Target_Hierarchy>]] [,[RECURSIVE][,INCLUDE_CALC_MEMBERS]])  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression1*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Set_Expression2*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Target_Hierarchy*  
 階層を返す有効な多次元式 (MDX) 式です。  
  
 *再帰*  
 セットの再帰的な比較を示すキーワードです。  
  
 *Include_Calc_Members*  
 計算されるメンバーがドリルダウン結果に含まれるようにするキーワードです。  
  
## <a name="remarks"></a>解説  
 この関数は、階層によって順序付けられた子メンバーのセットを返します。また、2 番目のセットにも存在する 1 番目のセットで指定されたメンバーが含まれています。 最初のセットに親メンバーと 1 つ以上の子が含まれている場合、親メンバーはドリル ダウンされません。 1 番目のセットの次元は任意ですが、2 番目には 1 次元のセットを指定する必要があります。 1 番目のセット内の元のメンバーの間で順序を維持、それぞれの親メンバーの結果に含まれるすべての子メンバーが設定されること以外、関数がすぐに含まれています。 この関数は、最初のセットのメンバーのうち、2 番目のセット内にも存在する各メンバーの子メンバーを取得することによって結果セットを作成します。 場合**再帰**を指定すると、関数は、再帰的に比較し、結果セットに対して、結果内の各メンバーの子を取得する 2 番目のセットのメンバーを 2 番目のセットで、結果セットから他のメンバーが見つかるまで、2 番目のセット内にも存在します。  
  
 XMLA プロパティのクエリを実行する**MdpropMdxDrillFunctions**サーバーがドリル関数が提供するサポートのレベルを確認することができます。 参照してください[サポートされる XMLA プロパティ &#40;です。XMLA &#41;](../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md)詳細についてはします。  
  
 1 番目のセットには、メンバーではなく組を含めることもできます。 組のドリル ダウンは OLE DB の拡張機能であり、メンバーではなく組のセットを返します。  
  
> [!IMPORTANT]  
>  メンバーのすぐ後に、そのメンバーの子のいずれかが続いていると、そのメンバーはドリルダウンされません。 セット内のメンバーの順序は重要です。 ドリル ダウン * と Drillup\*系関数。  
  
## <a name="examples"></a>使用例  
 次の例では、最初のセットのメンバーであり 2 番目のセットにも存在する、Australia へのドリル ダウンを行っています。  
  
```  
SELECT DrilldownMember   
   ( [Geography].[Geography].Children,  
      {[Geography].[Geography].[Country].[Australia],  
        [Geography].[Geography].[State-Province].[New South Wales]}  
   )  
   ON 0  
   FROM [Adventure Works]  
```  
  
 次の例では、最初のセットのメンバーであり 2 番目のセットにも存在する、Australia へのドリル ダウンを行っています。 RECURSIVE 引数があるので、結果セットのメンバー (State-Province レベルのメンバー) を 2 番目のセットと再帰的に比較し、結果セット内にあり 2 番目のセット内にも存在する各メンバーの子 (City レベルのメンバー) を取得するという操作が、結果セットのメンバーが 2 番目のセット内で検出されなくなるまで続けて行われます。  
  
```  
SELECT DrilldownMember   
   ( [Geography].[Geography].Children,  
      {[Geography].[Geography].[Country].[Australia],  
        [Geography].[Geography].[State-Province].[New South Wales]}  
   ,RECURSIVE)  
   ON 0  
   FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
