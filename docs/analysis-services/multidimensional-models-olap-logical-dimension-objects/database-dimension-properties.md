---
title: "データベース ディメンション プロパティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
helpviewer_keywords:
- metadata [Analysis Services]
- dimensions [Analysis Services], characteristics
- properties [Analysis Services], dimensions
ms.assetid: 075548ef-08a3-413c-8ee0-4a074c276fcc
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f22fa80ab461872b097ecd62eb54de1a22416c3c
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="database-dimension-properties"></a>データベース ディメンション プロパティ
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)][!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]ディメンションの特性は、さまざまなディメンション プロパティの設定と、属性またはディメンションに含まれる階層に基づいて、ディメンションのメタデータによって定義されます。 次の表では、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のディメンション プロパティについて説明します。  
  
|プロパティ|Description|  
|--------------|-----------------|  
|**AttributeAllMemberName**|ディメンションの属性の All メンバーの名前を指定します。|  
|**照合順序**|ディメンションで使用する照合順序を指定します。|  
|**CurrentStorageMode**|ディメンションの現在のストレージ モードを格納します。|  
|**DependsOnDimension**|ディメンションが別のディメンションに依存している場合は、その ID を格納します。|  
|**Description**|ディメンションの説明を格納します。|  
|**ErrorConfiguration**|重複するキー、不明なキー、エラーの制限、エラー検出時のアクション、エラー ログ ファイル、および NULL キーを処理するための、構成可能なエラー処理設定です。|  
|**ID**|ディメンションの一意識別子 (ID) を示します。|  
|**言語**|ディメンションの既定の言語を指定します。|  
|**MdxMissingMemberMode**|欠落しているメンバーを多次元式 (MDX) ステートメントでどのように処理するかを指定します。|  
|**MiningModelID**|データ マイニング ディメンションが関連付けられているマイニング モデルの ID を保持します。 このプロパティは、ディメンションがマイニング モデル ディメンションの場合にのみ適用できます。|  
|**名前**|ディメンションの名前を指定します。|  
|**プロアクティブ キャッシュ**|ディメンションのプロアクティブ キャッシュの設定を定義します。|  
|**ProcessingGroup**|処理グループを指定します。 有効値は ByAttribute または ByTable です。 既定値は**ByAttribute**です。|  
|**ProcessingMode**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によるインデックス化および集計を処理中または処理後のどちらに行うかを示します。|  
|**ProcessingPriority**|レイジー集計、インデックス作成、クラスター化など、バックグラウンド操作中のディメンション処理の優先度を指定します。|  
|**ソース**|ディメンションのバインド先のデータ ソース ビューを指定します。|  
|**StorageMode**|ディメンションのストレージ モードを指定します。|  
|**型**|ディメンションの種類を指定します。|  
|**UnknownMember**|不明なメンバーが表示されるかどうかを示します。|  
|**UnknownMemberName**|ディメンションの不明なメンバーのキャプションをディメンションの既定の言語で指定します。|  
|**WriteEnabled**|ディメンションの書き戻しを使用できるかどうかを示します (セキュリティ権限に依存)。|  
  
> [!NOTE]  
>  Null 値やその他のデータ整合性の問題に取り組む際の ErrorConfiguration および UnknownMember プロパティの値を設定の詳細については、次を参照してください。 [Analysis Services 2005 でのデータの整合性問題の処理](http://go.microsoft.com/fwlink/?LinkId=81891)です。  
  
## <a name="see-also"></a>参照  
 [属性と属性階層](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [ユーザー階層](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)   
 [ディメンション リレーションシップ](../../analysis-services/multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)   
 [ディメンション &#40;Analysis Services - 多次元データ&#41;](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  
