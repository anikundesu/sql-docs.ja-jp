---
title: "SELECT FROM&lt;モデル&gt;です。SAMPLE_CASES (DMX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SAMPLE_CASES
- SELECT
- FROM
dev_langs: DMX
helpviewer_keywords:
- SELECT FROM <model>.SAMPLE_CASES statement
- mining models [Analysis Services], sample cases
- sample cases [DMX]
- training mining models
ms.assetid: e7a34b9b-3562-4503-bfa7-dd9b12db480a
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 3b66bc09dcf501d73fdb8dd66516b738a4483e22
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="select-from-ltmodelgtsamplecases-dmx"></a>SELECT FROM&lt;モデル&gt;です。SAMPLE_CASES (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  データ マイニング モデルの学習に使用されるケースを表すサンプル ケースを返します。  
  
 このステートメントを使用するには、マイニング モデルの作成時にドリルスルーを使用可能にする必要があります。 ドリルスルーを有効にする方法の詳細については、次を参照してください。[マイニング モデルの作成 &#40;DMX&#41;](../dmx/create-mining-model-dmx.md)、 [SELECT INTO &#40;DMX&#41;](../dmx/select-into-dmx.md)、および[ALTER MINING STRUCTURE &#40;DMX&#41;](../dmx/alter-mining-structure-dmx.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <expression list> FROM <model>.SAMPLE_CASES  
[WHERE <condition list>] ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>引数  
 *n*  
 省略可。 返す行数を指定する整数値です。  
  
 *式の一覧*  
 関連付けられた列識別子のコンマ区切りのリストです。  
  
 *model*  
 モデル識別子です。  
  
 *条件の一覧*  
 省略可。 列の一覧から返される値を制限する条件です。  
  
 *式 (expression)*  
 省略可。 スカラー値を返す式。  
  
## <a name="remarks"></a>解説  
 サンプル ケースは生成されたものである場合や実際には学習データに存在しない場合があります。 返されたケースは、指定されたコンテンツ ノードを表します。  
  
 ただし、[!INCLUDE[msCoName](../includes/msconame-md.md)]シーケンス クラスター アルゴリズムでは、唯一[!INCLUDE[msCoName](../includes/msconame-md.md)]選択から使用をサポートするアルゴリズム\<モデル >。SAMPLE_CASES、サード パーティのアルゴリズムもこれをサポートします。  
  
## <a name="examples"></a>使用例  
 次の例では、Target Mail マイニング モデルの学習に使用されるサンプル ケースを返しています。 使用して、 [IsInNode & # #40; DMX &#41;](../dmx/isinnode-dmx.md)で機能、**場所**句 000000003」ノードに関連付けられたケースのみが返されます。 ノード文字列は、スキーマ行セットの NODE_UNIQUE_NAME 列にあります。  
  
```  
Select * from [Sequence Clustering].SAMPLE_Cases  
WHERE IsInNode('000000003')  
```  
  
## <a name="see-also"></a>参照  
 [選択 &#40;DMX&#41;](../dmx/select-dmx.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;データ定義ステートメント](../dmx/dmx-statements-data-definition.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;データ操作ステートメント](../dmx/dmx-statements-data-manipulation.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
