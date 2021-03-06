---
title: "図形 (DMX) |Microsoft ドキュメント"
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
f1_keywords: SHAPE
dev_langs: DMX
helpviewer_keywords:
- SHAPE statement
- multiple data sources
ms.assetid: b9526ec2-40bc-4bf5-b4e5-774f71075065
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: b337483b23ef2f4bee4f82a7be05f3ea521b03a1
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="ltsource-data-querygt---shape"></a>&lt;ソース データ クエリ&gt;-図形
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  マイニング モデルのケース テーブルとなる、複数のデータ ソースから単一の階層テーブル (入れ子になったテーブルを使用するテーブル) にクエリを結合します。  
  
 完全な構文、**図形**コマンドについては、 [!INCLUDE[msCoName](../includes/msconame-md.md)] Data Access Components (MDAC) ソフトウェア開発キット (SDK)。  
  
## <a name="syntax"></a>構文  
  
```  
  
SHAPE {<master query>}  
APPEND ({ <child table query> }   
     RELATE <master column> TO <child column>)   
          AS <column table name>  
[  
     ({ <child table query> }   
     RELATE <master column> TO <child column>)   
          AS < column table name>  
...  
]       
```  
  
## <a name="arguments"></a>引数  
 *マスター クエリ*  
 クエリは親テーブルを返します。  
  
 *子テーブルのクエリ*  
 クエリは入れ子になったテーブルを返します。  
  
 *マスターの列*  
 child table query の結果から子の行を識別する親テーブル内の列です。  
  
 *子の列*  
 master query の結果から親の行を識別する子テーブル内の列です。  
  
 *テーブルの列名*  
 入れ子になったテーブルの親テーブルに、列名を新たに追加します。  
  
## <a name="remarks"></a>解説  
 親テーブルと子テーブルを関連付ける列ごとにクエリを発行する必要があります。  
  
## <a name="examples"></a>使用例  
 内で次の例を使用することができます、 [INSERT INTO &#40;DMX&#41;](../dmx/insert-into-dmx.md)ステートメントを入れ子になったテーブルが含まれるモデルをトレーニングします。 2 つのテーブル内で、**図形**によってステートメントが関連付けられて、 **OrderNumber**列です。  
  
```  
SHAPE {  
    OPENQUERY([Adventure Works DW Multidimensional 2012],'SELECT OrderNumber  
    FROM vAssocSeqOrders ORDER BY OrderNumber')  
} APPEND (  
    {OPENQUERY([Adventure Works DW Multidimensional 2012],'SELECT OrderNumber, model FROM   
    dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')}  
  RELATE OrderNumber to OrderNumber)   
```  
  
## <a name="see-also"></a>参照  
 [&#60;以外の場合はソース データ クエリ &#62;。](../dmx/source-data-query.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;データ定義ステートメント](../dmx/dmx-statements-data-definition.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;データ操作ステートメント](../dmx/dmx-statements-data-manipulation.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
