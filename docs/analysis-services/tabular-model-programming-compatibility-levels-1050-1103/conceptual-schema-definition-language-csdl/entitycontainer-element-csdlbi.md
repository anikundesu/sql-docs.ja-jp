---
title: "EntityContainer 要素 (CSDLBI) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
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
ms.assetid: e328558e-16b0-4d4a-a79a-fdd3c9493595
caps.latest.revision: "17"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 21ad4c6d328c8c299a2ae34c4ac5aab27feec794
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="entitycontainer-element-csdlbi"></a>EntityContainer 要素 (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]EntityContainer 要素は、CSDL の種類を 1 つのデータ モデル内のエンティティのコレクションを定義に基づく、複合型です。 ビジネス インテリジェンス アプリケーションでは、EntityContainer で表されるデータ モデルは、リレーションシップによってリンクされた列のある複数のテーブルと、計算、メジャー、および KPI を含む可能性があります。 概念的には、データベースやデータ ソースに似ています。  
  
 EntityContainer では、テーブルやリレーションシップを含む、データ モデルに含まれる各エンティティ タイプを指定する必要があります。 これらのモデル エンティティに関する情報は、Entity 要素型の子エンティティをリストすることで指定します。 詳細については、「[EntityType 要素 &#40;CSDLBI&#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/entitytype-element-csdlbi.md)」を参照してください。  
  
 照合順序や言語などのプロパティは、個別のオブジェクトではなく、EntityContainer のレベルで定義されます。 ただし、モデル内の列およびテキスト属性は、キャプションまたは他の言語での翻訳を持つことができます。  
  
## <a name="elements-and-attributes"></a>要素と属性  
 次の表に、EntityContainer 要素を定義する要素と属性を示します。  
  
|名前|必須かどうか|Description|  
|----------|-----------------|-----------------|  
|名前|可|データ モデルの名前。|  
|Caption|いいえ|データベースまたはデータ モデルの説明。|  
|カルチャ|可|要求の LCID を含む文字列。|  
|CompareOptions|可|モデルの言語固有の並べ替えおよび文字列比較のオプション|  
|DirectQueryMode|いいえ|モデルが DirectQuery モードを使用するときのクエリ モードを示す列挙体。|  
|EntitySet 要素|可|[EntitySet 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/entityset-element-csdlbi.md)|  
|AssociationSet 要素|不可|[AssociationSet 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/associationset-element-csdlbi.md)|  
  
## <a name="compareoptions-element"></a>CompareOptions 要素  
 CompareOptions 属性では、データ モデルに適用される照合順序のプロパティが定義されます。 CompareOptions で定義されているプロパティは、モデルのデザイン時に Analysis Services データベースで設定される並べ替え順序、かなの区別、大文字小文字の区別に対する設定から派生されます。 次の表では、CompareOptions 属性の一部として含まれる値について説明します。  
  
|値|Description|  
|-----------|-----------------|  
|IgnoreCase|文字列の比較で大文字と小文字を区別するかどうかを示すブール値。|  
|IgnoreNonSpace|文字列の比較で、分音文字などの非空白結合文字を無視するかどうかを示すブール値。|  
|IgnoreKanaType|文字列の比較でカタカナを区別するかどうかを示すブール値。|  
|IgnoreWidth|文字列の比較で文字幅を区別するかどうかを示すブール値。|  
  
## <a name="directquerymode"></a>DirectQueryMode  
 **DirectQueryMode**  
  
 単純型である DirectQueryMode は、リレーショナル データ ソースからの直接的なデータの取得がモデルで有効である場合に、既定で使用されるクエリの種類を定義します。 このプロパティは、DirectQuery モードで実行されるテーブル モデルのみに適用されます。 次の表は、DirectQuery モード列挙体で使用可能な値の一覧です。  
  
|値|Description|  
|-----------|-----------------|  
|InMemory|モデルに対するクエリがキャッシュ内のデータを使用することを示します。|  
|InMemoryWithDirectQuery|既定では、モデルに対するクエリがリレーショナル データ ソースからのデータを使用することを示します。|  
|DirectQueryWithInMemory|既定ではモデルに対するクエリがキャッシュ内のデータを使用することを示します。|  
|DirectQuery|モデルに対するクエリがリレーショナル データ ソース内のみのデータを使用することを示します。|  
  
## <a name="example"></a>例  
 **テーブル**  
  
 CSDLBI Version 1.1 における次の例は、AdventureWorks テーブル データ モデルの一部です。  
  
```  
  
<EntityContainer   
     Name="Sandbox">  
   <EntitySet   
       Name="DimEmployee"   
       EntityType="Sandbox.DimEmployee">  
   <bi:EntitySet />  
   </EntitySet>  
  
   <EntitySet   
     Name="DimProduct"   
       EntityType="Sandbox.DimProduct">  
    <bi:EntitySet />  
    </EntitySet>  
  
<bi:EntityContainer Caption="AWSimple" Culture="en-US">  
  
```  
  
## <a name="example"></a>例  
 **多次元**  
  
 CSDLBI Version 1.1 における次の例は、Contoso Operations キューブからの抜粋です。  
  
```  
  
<EntityContainer   
     Name="Sandbox">  
   <EntitySet   
      Name="Bike"   
      EntityType="Sandbox.Bike">  
    <bi:EntitySet Hidden="true" />  
   </EntitySet>  
…  
<bi:EntityContainer   
   Caption="CSDLTest"   
   Culture="en-US">  
<bi:CompareOptions   
   IgnoreCase="true" />  
</bi:EntityContainer>  
</EntityContainer>  
  
```  
  
## <a name="see-also"></a>参照  
 [EntitySet 要素 &#40;です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/entityset-element-csdlbi.md)  
  
  
