---
title: "マイニング構造から列を削除 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/13/2017
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
ms.topic: article
helpviewer_keywords:
- mining structures [Analysis Services], columns
- removing columns
- deleting columns
- columns [data mining], mining structure columns
ms.assetid: 41073ffe-9351-416b-9f0c-62634bc213f9
caps.latest.revision: "27"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5592cefdc8e4e77ec5b6e92ee0d4d671b5df3408
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="remove-columns-from-a-mining-structure"></a>マイニング構造からの列の削除
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]データ マイニング デザイナーを使用して、構造が既に作成した後、マイニング構造から列を削除することができます。 マイニング構造列を削除する理由には、次のようなものがあります。  
  
-   マイニング構造に列の複数のコピーが格納されており、モデルで重複データを使用しないようにする。  
  
-   データを保護する必要があるが、ドリルスルーが有効になっている。  
  
-   データがモデリングで使用されておらず、処理する必要がない。  
  
 マイニング構造から列を削除しても、データ ソース ビュー内の列または外部データ内の列は変更されません。メタデータのみ削除されます。 ただし、マイニング構造で使用される列を変更する場合は、構造およびその構造に基づくモデルを再処理する必要があります。  
  
### <a name="to-remove-a-column-from-the-mining-structure"></a>マイニング構造から列を削除するには  
  
1.  データ マイニング デザイナーで **[マイニング構造]** タブを選択します。  
  
2.  マイニング構造のツリーを展開し、すべての列を表示します。  
  
3.  削除する列を右クリックして、 **[削除]**をクリックします。  
  
4.  **[オブジェクトの削除]** ダイアログ ボックスで **[OK]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [マイニング構造のタスクと操作方法](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  
