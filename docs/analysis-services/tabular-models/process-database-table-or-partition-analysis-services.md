---
title: "データベースの処理、テーブル、またはパーティション (Analysis Services) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
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
f1_keywords: sql13.ASVS.SSMS.PARTITIONS.PROCESSINGOPTIONS.IMBI.F1
ms.assetid: 307d69c3-cabb-4dfa-b90c-9852492c1213
caps.latest.revision: "8"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: bd4457fefbd0afa6caaf1402e961a4604a58d855
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="process-database-table-or-partition-analysis-services"></a>データベース、テーブル、またはパーティションの処理 (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]このトピックのタスクを使用してテーブル モデル データベース、テーブル、またはパーティションを手動で処理する方法について説明、**プロセス\<オブジェクト >**  ダイアログ ボックスで[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]です。  
  
 テーブル モデルの処理の詳細については、[「データの処理 (SSAS テーブル)」](../../analysis-services/tabular-models/process-data-ssas-tabular.md) を参照してください。  
  
##  <a name="bkmk_process_tasks"></a> 処理手順  
  
###  <a name="bkmk_process_db"></a> データベースを処理するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で処理対象のデータベースを右クリックし、 **[データベースの処理]**をクリックします。  
  
2.  **[データベースの処理]** ダイアログ ボックスの **[モード]** ボックスの一覧で、次のプロセス モードのいずれかを選択します。  
  
    |[モード]|Description|  
    |----------|-----------------|  
    |**既定の処理**|データベース オブジェクトの処理状態を検出し、処理されていないオブジェクトや部分的に処理されたオブジェクトを完全処理状態にするために必要な処理を行います。 空のテーブルとパーティションのデータが読み込まれ、階層、計算列、およびリレーションシップが構築または再構築 (再計算) されます。|  
    |**完全処理**|データベースとそのデータベースに含まれるすべてのオブジェクトを処理します。 既に処理されたオブジェクトに対して完全処理を実行すると、そのオブジェクト内のすべてのデータが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって削除されてから、オブジェクトが処理されます。 この種の処理は、構造上の変更をオブジェクトに加えた場合に必要となります。 このオプションは最も多くのリソースを必要とします。|  
    |**消去の処理**|データベース オブジェクトからすべてのデータを削除します。|  
    |**再計算の処理**|階層、リレーションシップ、および計算列を更新して再計算します。|  
  
3.  **[処理]** チェックボックス列で、選択したモードで処理するパーティションを選択し、 **[OK]**をクリックします。  
  
###  <a name="bkmk_process_table"></a> テーブルを処理するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、処理対象のテーブルを含むテーブル モデル データベースの **[テーブル]** ノードを展開し、処理対象のテーブルを右クリックしてから **[テーブルの処理]**をクリックします。  
  
2.  **[テーブルの処理]** ダイアログ ボックスの **[モード]** ボックスの一覧で、次のプロセス モードのいずれかを選択します。  
  
    |[モード]|Description|  
    |----------|-----------------|  
    |**既定の処理**|テーブル オブジェクトの処理状態を検出し、処理されていないオブジェクトや部分的に処理されたオブジェクトを完全処理状態にするために必要な処理を行います。 空のテーブルとパーティションのデータが読み込まれ、階層、計算列、およびリレーションシップが構築または再構築 (再計算) されます。|  
    |**完全処理**|テーブル オブジェクトとそこに含まれているすべてのオブジェクトを処理します。 既に処理されたオブジェクトに対して完全処理を実行すると、そのオブジェクト内のすべてのデータが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって削除されてから、オブジェクトが処理されます。 この種の処理は、構造上の変更をオブジェクトに加えた場合に必要となります。 このオプションは最も多くのリソースを必要とします。|  
    |**データの処理**|階層またはリレーションシップを再構築したり、計算列とメジャーを再計算したりせずに、テーブルにデータを読み込みます。|  
    |**消去の処理**|テーブルおよびテーブル パーティションからすべてのデータを削除します。|  
    |**デフラグの処理**|補助テーブルのインデックスをデフラグします。|  
  
3.  テーブルのチェックボックス列でテーブルを確認し、必要に応じて処理対象の追加のテーブルを選択し、 **[OK]**をクリックします。  
  
###  <a name="bkmk_process_partition"></a> 1 つ以上のパーティションを処理するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、処理対象のパーティションが存在するテーブルを右クリックして **[パーティション]**をクリックします。  
  
2.  **[パーティション]** ダイアログ ボックスの **[パーティション]**で、[処理] ボタンをクリックします。  
  
3.  **[パーティションの処理]** ダイアログ ボックスの **[モード]** ボックスの一覧で、次のプロセス モードのいずれかを選択します。  
  
    |[モード]|Description|  
    |----------|-----------------|  
    |**既定の処理**|パーティション オブジェクトの処理状態を検出して、未処理または部分的に処理されたパーティション オブジェクトを完全に処理された状態にするために必要な処理を実行します。 空のテーブルとパーティションのデータが読み込まれ、階層、計算列、およびリレーションシップが構築または再構築 (再計算) されます。|  
    |**完全処理**|パーティション オブジェクトとそこに含まれているすべてのオブジェクトを処理します。 既に処理されたオブジェクトに対して完全処理を実行すると、そのオブジェクト内のすべてのデータが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって削除されてから、オブジェクトが処理されます。 この種の処理は、構造上の変更をオブジェクトに加えた場合に必要となります。|  
    |**データの処理**|階層またはリレーションシップを再構築したり、計算列とメジャーを再計算したりせずに、パーティションまたはテーブルにデータを読み込みます。|  
    |**消去の処理**|パーティションからすべてのデータを削除します。|  
    |**追加の処理**|パーティションを新しいデータで増分更新します。|  
  
4.  **[処理]** チェックボックス列で、選択したモードで処理するパーティションを選択し、 **[OK]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [テーブル モデル パーティション (SSAS テーブル)](../../analysis-services/tabular-models/tabular-model-partitions-ssas-tabular.md)   
 [テーブル モデル パーティションの作成および管理 (SSAS テーブル)](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md)  
  
  
