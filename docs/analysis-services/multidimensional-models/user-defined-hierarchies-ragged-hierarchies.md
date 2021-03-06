---
title: "不規則階層 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
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
helpviewer_keywords: ragged hierarchies [Analysis Services]
ms.assetid: e40a5788-7ede-4b0f-93ab-46ca33d0cace
caps.latest.revision: "16"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 4b3ffa23cdd185c57a86bc34921c3e489870cd2d
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="user-defined-hierarchies---ragged-hierarchies"></a>ユーザー定義階層の不規則階層
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]不規則階層を持つ、不均一な数のレベルのユーザー定義階層です。 一般的な例として、部門の管理者と管理者以外のメンバーの両方が直属の部下として上級管理者に属している組織図や、国 - 地域 - 市から構成される地理的な階層 (ワシントン D.C.、バチカン、ニューデリーなど、親となる州や省などを持たない市がいくつかあります) などを挙げることができます。  
  
 ディメンション内のほとんどの階層では、各レベルの上にあるメンバーの数は、同じレベルにある他のメンバーでも同じ数になります。 このような場合と異なり、不規則階層では、少なくとも 1 つのメンバーの論理上の親メンバーが、そのメンバーのすぐ上のレベルにありません。 この場合、階層は異なるドリル ダウン パスのさまざまなレベルに至ります。 クライアント アプリケーションでは、これによりドリルダウン パスが不必要に複雑になる可能性があります。  
  
 クライアント アプリケーションによって、不規則階層の処理方法は異なります。 モデル内に不規則階層がある場合は、必要な表示動作が実現されるように、追加の作業を行う準備をしてください。  
  
 まず、クライアント アプリケーションを調べて、ドリル ダウン パスの処理方法を確認します。 たとえば、Excel では、不足値のプレースホルダーとして親の名前が繰り返されます。 この動作を確認するには、Adventure Works 多次元モデルの Sales Territory ディメンションを使用してピボットテーブルを構築します。 ピボットテーブルでは、Sales Territory 属性として "グループ"、"国"、"地域" を設定します。地域の値が欠落している場合、国がプレースホルダーとして使用されることを確認します。この場合は、地域の上の親 (国名) が繰り返し使用されます。 この動作は、Excel 内で固定されている MDX Compatibility=1 接続文字列プロパティから派生します。 必要としているドリル ダウンの動作をクライアントが実現しない場合は、それらの動作のいくつかを変更するように、モデルのプロパティを設定することができます。  
  
 このトピックには、次のセクションが含まれます。  
  
-   [不規則階層でのドリル ダウン ナビゲーションを変更する方法](#bkmk_approach)  
  
-   [HideMemberIf を設定して標準階層のメンバーを非表示にする](#bkmk_Hide)  
  
-   [MDX の互換性を設定してクライアント アプリケーションでのプレースホルダーの表示方法を指定する](#bkmk_Mdx)  
  
##  <a name="bkmk_approach"></a> 不規則階層でのドリル ダウン ナビゲーションを変更する方法  
 ドリル ダウン ナビゲーションが予期した値を返さない場合や使いにくい場合、不規則階層の存在が問題になります。 不規則階層が原因となるナビゲーションの問題を解決するには、次の点を検討してください。  
  
-   標準階層を使用します。ただし、各レベルの **HideMemberIf** プロパティを設定し、ユーザーに対して欠落しているレベルを表示するかどうかを指定します。 **HideMemberIf**を設定するとき、接続文字列で **MDXCompatibility** も設定し、既定のナビゲーション動作をオーバーライドします。 これらのプロパティの設定手順をこのトピックで説明します。  
  
-   レベル メンバーを明示的に管理する親子階層を作成します。 この技法の図解については、「 [Ragged Hierarchy in SSAS (blog post)](http://dwbi1.wordpress.com/2011/03/30/ragged-hierarchy-in-ssas/)」(SSAS での不規則階層 (ブログ投稿)) をご覧ください。 詳しくは、オンライン ブックの「 [親子ディメンション](../../analysis-services/multidimensional-models/parent-child-dimension.md)」をご覧ください。 親子階層を作成する際の問題点は、ディメンションごとに 1 つの階層があるので、中間レベルのメンバーを集計する場合のパフォーマンスが一般的に低下することです。  
  
 ディメンションに複数の不規則階層が含まれている場合は、第 1 の方法である、 **HideMemberIf**の設定を使用してください。 不規則階層の操作について実践的な経験がある BI 開発者であれば、さらに、物理データ テーブルへの追加の変更を提案したり、レベルごとの個別のテーブルを作成したりすることができます。 この方法の詳細については、「 [SSAS Financial Cube–Part 1a–Ragged Hierarchies](http://martinmason.wordpress.com/2012/03/03/the-ssas-financial-cubepart-1aragged-hierarchies-cont/) 」(SSAS 財務キューブ – パート 1a – 不規則階層 (Martin Mason のブログ)) をご覧ください。  
  
##  <a name="bkmk_Hide"></a> HideMemberIf を設定して標準階層のメンバーを非表示にする  
 不規則なディメンションのテーブルでは、論理的に欠落しているメンバーはさまざまな方法で表されます。 テーブルのセルに NULL または空の文字列を含めたり、親と同じ値を含めてプレースホルダーとして使用できます。 プレースホルダーの表示は、子メンバーのプレースホルダーのステータス、 **HideMemberIf** プロパティ、クライアント アプリケーションの **MDX Compatibility** 接続文字列プロパティによって決まります。  
  
 不規則階層の表示をサポートしているクライアント アプリケーションの場合、これらのプロパティを使用して、論理的に欠落しているメンバーを非表示にできます。  
  
1.  SSDT で、ディメンションをダブルクリックし、ディメンション デザイナーでそのディメンションを開きます。 最初のタブである [ディメンション構造] の [階層] ペインには、属性階層が表示されます。  
  
2.  階層内のメンバーを右クリックし、 **[プロパティ]**をクリックします。 **HideMemberIf** を、次に説明する値のいずれかに設定します。  
  
    |HideMemberIf の設定値|Description|  
    |--------------------------|-----------------|  
    |**Never**|レベル メンバーがすべて表示されます。 これが既定値です。|  
    |**OnlyChildWithNoName**|レベル メンバーは、その親の唯一の子で、その名前が null または空の文字列である場合、表示されません。|  
    |**OnlyChildWithParentName**|レベル メンバーは、その親の唯一の子で、その名前がその親の名前と同じである場合、表示されません。|  
    |**NoName**|レベル メンバーは、その名前が空の場合、表示されません。|  
    |**ParentName**|レベル メンバーは、名前がその親の名前と同じである場合、表示されません。|  
  
##  <a name="bkmk_Mdx"></a> MDX の互換性を設定してクライアント アプリケーションでのプレースホルダーの表示方法を指定する  
 階層レベルで **HideMemberIf** を設定したら、クライアント アプリケーションから送信される接続文字列の **MDX Compatibility** プロパティも設定する必要があります。 **MDX Compatibility** の設定によって、 **HideMemberIf** が使用されるかどうかが決まります。  
  
|MDX Compatibility の設定|Description|使用方法|  
|-------------------------------|-----------------|-----------|  
|**1**|プレースホルダーの値を表示します。|この値は、Excel、SSDT、SSMS で既定で使用される値です。 この値は、サーバーに対して、不規則階層で空のレベルがドリル ダウンされた場合にプレースホルダーの値を返すように指示します。 プレースホルダーの値をクリックすると、ドリル ダウンを継続して、子 (リーフ) ノードを取得できます。<br /><br /> Excel には Analysis Services に接続する際に使用される接続文字列があり、この接続文字列では、新しく接続を行うたびに **MDX Compatibility** が必ず 1 に設定されます。 この動作は、旧バージョンとの互換性のために保持されています。|  
|**2**|プレースホルダーの値 (null 値または親レベルの複製) を非表示にします。ただし、関連する値を持つ他のレベルとノードは表示します。|不規則階層では、通常、**MDX Compatibility**=2 が優先される設定として示されます。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポートと一部のサードパーティのクライアント アプリケーションでは、この設定を保存できます。|  
  
## <a name="see-also"></a>参照  
 [ユーザー定義階層の作成](../../analysis-services/multidimensional-models/user-defined-hierarchies-create.md)   
 [ユーザー階層](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)   
 [親子ディメンション](../../analysis-services/multidimensional-models/parent-child-dimension.md)   
 [接続文字列プロパティ (Analysis Services)](../../analysis-services/instances/connection-string-properties-analysis-services.md)  
  
  
