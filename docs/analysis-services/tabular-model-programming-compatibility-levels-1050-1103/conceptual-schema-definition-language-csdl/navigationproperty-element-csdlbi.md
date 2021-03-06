---
title: "NavigationProperty 要素 (CSDLBI) |Microsoft ドキュメント"
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
ms.assetid: a36b4d3b-6a6c-489b-8a46-2e6b925b568f
caps.latest.revision: "10"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: af807f0c68cf255903ff2d25cd14fa8a032d3264
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="navigationproperty-element-csdlbi"></a>NavigationProperty 要素 (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]NavigationProperty 要素は、ビジネス インテリジェンス データ モデルでのナビゲーションをサポートするために、CSDL Member の種類を拡張する複合型です。  
  
> [!WARNING]  
>  この要素は報告用であり、変更または操作することはできません。  
  
## <a name="elements-and-attributes"></a>要素と属性  
 次の表に、NavigationProperty 要素を定義する要素と属性を示します。  
  
|名前|必須かどうか|Description|  
|----------|-----------------|-----------------|  
|CollectionCaption|いいえ|ナビゲーション プロパティのインスタンスのセットを参照するための複数形の名前。<br /><br /> この属性が省略されると、ベース メンバーの Caption 属性が使用されます。|  
  
## <a name="example"></a>例  
 **テーブル**  
  
 次の例では、テーブル モデルの Product SubCategory テーブルと Product テーブルの間のリンクを記述するナビゲーション プロパティを CSDLBI Version 1.1 で示します。  
  
```  
  
<NavigationProperty   
    Name="Product_Sub_Category_ProductSubcategoryKey"      
    Relationship="Sandbox.Product_Product_Sub_Category_Product_Sub_Category_ProductSubcategoryKey"  
     FromRole="Product_ProductSubcategoryKey"   
    ToRole="Product_Sub_Category_ProductSubcategoryKey">  
<bi:NavigationProperty   
     ReferenceName="Product Sub-Category_ProductSubcategoryKey" />  
</NavigationProperty>  
```  
  
## <a name="example"></a>例  
 **多次元**  
  
 次の例では、Contoso Operations キューブで 2 つのテーブル間のリレーションシップを記述するナビゲーション プロパティを CSDLBI Version 1.1 で示します。 このリレーションシップが、Bike Category テーブルと Product Subcategory テーブルを接続しています。  
  
```  
  
<NavigationProperty   
     Name="BikeSubcategory_ProductSubcategoryKey"   
     Relationship="Sandbox.Bike_BikeSubcategory_BikeSubcategory_ProductSubcategoryKey"   
     FromRole="Bike_ProductSubcategoryKey"   
     ToRole="BikeSubcategory_ProductSubcategoryKey">  
   <bi:NavigationProperty />  
</NavigationProperty>  
```  
  
## <a name="see-also"></a>参照  
 [レベルを 1050 から 1103 表形式オブジェクト モデルの互換性を理解します。](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  
