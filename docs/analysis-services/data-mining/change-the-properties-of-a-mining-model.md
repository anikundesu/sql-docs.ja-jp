---
title: "マイニング モデルのプロパティの変更 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
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
- mining models [Analysis Services], properties
- properties [data mining]
ms.assetid: aefaeb7f-d174-48d1-a188-0987a3b1196b
caps.latest.revision: "38"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ccfd17eb10b11052f24cf18f9b0e94649b5030af
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="change-the-properties-of-a-mining-model"></a>マイニング モデルのプロパティの変更
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]いくつかのマイニング モデルのプロパティが、モデル全体に適用し、その他のモデルのプロパティが個々 の列に適用します。 モデル全体に適用されるプロパティの例は、ケース データをクエリで使用可能にする必要があるかどうかを指定する **Drillthrough** プロパティと、 **Description** プロパティです。 列に適用されるプロパティには、モデル内で列のデータが使用される方法を制御する **Usage** および **ModelingFlags**があります。  
  
 次のモデル プロパティには、式の作成または複雑なモデル プロパティの構成に使用できる高度なエディターがあります。 プロパティには次の機能があります。  
  
-   **Filter** プロパティ: [[データセット フィルター] または [モデル フィルター] ダイアログ ボックス](http://msdn.microsoft.com/library/a9602174-b7e2-4e16-8ded-dfd8eb9264d7)を開きます。  
  
-   **AlgorithmParameters** プロパティ: [[アルゴリズム パラメーター] ダイアログ ボックス &#40;[マイニング モデル] ビュー&#41;](http://msdn.microsoft.com/library/57f9f6f8-8ca4-4a6e-8f18-85f0571b7060) を開きます。  
  
 マイニング モデルのプロパティを設定する方法については、「[マイニング モデル列](../../analysis-services/data-mining/mining-model-columns.md)」を参照してください。  
  
### <a name="to-change-the-properties-of-a-mining-model"></a>マイニング モデルのプロパティを変更するには  
  
1.  データ マイニング デザイナーの **[マイニング モデル]** タブで、マイニング モデル名を含む列ヘッダーか、マイニング アルゴリズム名を含むグリッドの行のいずれかを右クリックし、 **[プロパティ]**を選択します。  
  
2.  画面の右側の **[プロパティ]** ウィンドウで、変更するプロパティに対応する値を強調表示し、新しい値を入力します。  
  
     新しい値は、デザイナーで別の要素を選択したときに有効になります。  
  
### <a name="to-change-the-properties-of-a-mining-model-column"></a>マイニング モデル列のプロパティを変更するには  
  
1.  データ マイニング デザイナーの **[マイニング モデル]** タブで、マイニング構造列とマイニング モデルが交差するグリッド内のセルを右クリックし、 **[プロパティ]**を選択します。  
  
2.  画面の右側の **[プロパティ]** ウィンドウで、変更するプロパティに対応する値を強調表示し、新しい値を入力します。  
  
    > [!NOTE]  
    >  列の使用法が **Ignore**に設定されている場合、その列の **[プロパティ]** ウィンドウは空白になります。  
  
     新しい値は、デザイナーで別の要素を選択したときに有効になります。  
  
## <a name="see-also"></a>参照  
 [マイニング モデル タスクと操作方法](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  
