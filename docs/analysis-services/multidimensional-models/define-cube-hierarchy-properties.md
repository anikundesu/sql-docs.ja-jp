---
title: "キューブ階層のプロパティの定義 |Microsoft ドキュメント"
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
helpviewer_keywords:
- hierarchies [Analysis Services], multilevel
- hierarchies [Analysis Services], cubes
ms.assetid: 819d0a4e-7815-4332-a605-b07ca2ade6ac
caps.latest.revision: "18"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 858e5f95c4c382b46d85a9f0abcae728bae102c1
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="define-cube-hierarchy-properties"></a>キューブ階層のプロパティの定義
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]キューブ階層のプロパティを有効にすると、同じデータベース ディメンションに基づいたキューブ ディメンションでユーザー定義階層に固有の設定を指定します。 次の表では、キューブ階層のプロパティについて説明します。  
  
|プロパティ|Description|  
|--------------|-----------------|  
|**有効**|キューブ ディメンションの階層が有効かどうかを決定します。|  
|**HierarchyID**|階層の一意の識別子 (ID) を格納します。|  
|**OptimizedState**|階層に適用される最適化のレベルを決定します。 このプロパティは、以下の値をとります。<br /><br /> **FullyOptimized**:<br />                    インスタンスは、階層のインデックスを構築し、クエリ パフォーマンスを改善します。 これが既定値です。<br /><br /> **NotOptimized**:<br />                    インスタンスは追加のインデックスを構築しません。|  
|**[表示]**|キューブ階層の表示を決定します。 既定値は **True**です。|  
  
## <a name="see-also"></a>参照  
 [ユーザー階層](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)  
  
  
