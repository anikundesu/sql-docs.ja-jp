---
title: "DisplayKey 要素 (CSDLBI) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: 7d881278-1e77-42e1-8cfc-f1bbd9ec2340
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ea38abe670eb7585a8f0b6286f8ffa059d6a4457
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="displaykey-element-csdlbi"></a>DisplayKey 要素 (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]DisplayKey 要素には、一緒に強い識別子を構成する次の要素の一覧が含まれています。 DisplayKey は EntityType 要素の子としてのみ存在します。 列またはロール エンドを参照できます。  
  
## <a name="elements-and-attributes"></a>要素と属性  
 次の表に DisplayKey 要素の属性を示します。  
  
|名前|必須かどうか|Description|  
|----------|-----------------|-----------------|  
|IsDisplayKey|いいえ|True または False |  
  
## <a name="remarks"></a>解説  
 この要素はレポート用です。 この属性を適用する要素は、実際のテーブル キーである必要はなく、キーとして提示する要素でかまいません。 ただし、DisplayKey に対して使用する列は一意の値を含む必要があります。  
  
## <a name="example"></a>例  
 **テーブル**  
  
 CSDLBI Version 1.1 における次の例では、テーブルに対して DisplayKey と指定された AdventureWorks サンプル データ モデルの列を示します。  
  
```  
<sample in progress>  
```  
  
## <a name="example"></a>例  
 **多次元**  
  
 CSDLBI Version 1.1 における次の例は、Contoso Operations キューブの表現から抜粋したものです。 このモデルでは、Color 列が Bikes テーブルの表示キーとしてマークされています。  
  
```  
  
<EntityType   
    Name="Bike">  
.. .. ..  
<Property   
    Name="Color"   
    Type="String"   
    MaxLength="Max"   
    Unicode="true"   
    FixedLength="false">  
<bi:Property   
    ContextualNameRule="Context"   
    Alignment="Left" Units="counts"   
    SortDirection="Descending"   
    IsRightToLeft="true"   
    DefaultAggregateFunction="Max" />  
</Property>  
.. .. ..  
<bi:EntityType>  
   <bi:DisplayKey>  
      <bi:MemberRef Name="Color" />  
   </bi:DisplayKey>>  
.. .. ..  
</bi:EntityType>  
</EntityType>  
```  
  
## <a name="see-also"></a>参照  
 [レベルを 1050 から 1103 表形式オブジェクト モデルの互換性を理解します。](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [CSDLBI の概念](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/csdlbi-concepts.md)  
  
  
