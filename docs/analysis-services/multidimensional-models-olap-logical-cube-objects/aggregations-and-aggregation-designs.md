---
title: "集計と集計デザイン |Microsoft ドキュメント"
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
- aggregations [Analysis Services], about aggregations
- storage [Analysis Services], aggregations
- Storage Design Wizard
- data summary [Analysis Services]
- data storage [Analysis Services]
- storing data [Analysis Services], aggregations
- aggregations [Analysis Services]
ms.assetid: 35bd8589-39fa-4e0b-b28f-5a07d70da0a2
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b51ee2cb78ff5309e6f2fe3ffc515a15a1649619
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="aggregations-and-aggregation-designs"></a>集計と集計デザイン
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]<xref:Microsoft.AnalysisServices.AggregationDesign>オブジェクトが複数のパーティションで共有できる集計定義のセットを定義します。  
  
 <xref:Microsoft.AnalysisServices.Aggregation> オブジェクトは、メジャー グループ データの概要を、ディメンションの特定の粒度で表します。  
  
 簡単な <xref:Microsoft.AnalysisServices.Aggregation> オブジェクトは、基本情報およびディメンションで構成されます。 基本情報には、集計の名前、ID、注釈、および説明が含まれます。 ディメンションは、ディメンションの粒度属性の一覧を含む <xref:Microsoft.AnalysisServices.AggregationDimension> オブジェクトのコレクションです。  
  
 集計とは、事前に計算されたリーフ セル データを要約したものです。 集計により、質問の回答があらかじめ用意されているので、クエリの応答時間を短縮できます。 たとえば、何千行も蓄積されているデータ ウェアハウスのファクト テーブルから特定の製品ラインの週間売上合計を要求するクエリがあるとします。これを計算するために、問い合わせ時にファクト テーブルのすべての行をスキャンして合計していると、応答時間が長くなる場合があります。 ただし、このクエリの回答となる集計データがあらかじめ計算されていれば、即座に応答ができます。 処理中に要約データを事前計算しておくことは、高速な応答時間を実現するための、基本的な OLAP 技術です。  
  
 キューブとは、要約データを多次元構造で編成するための OLAP 技術です。 ディメンションとその属性階層構造には、キューブに照会できる内容が反映されています。 集計は、各ディメンションによって指定された座標位置にあるセルに、多次元構造で格納されます。 たとえば、"北西地域 (Northwest) における 1998 年の製品 X の売上は?" という質問には、 3 つのディメンション (製品、時間、および地理) と 1 つのメジャー (Sales) が関係します。 この質問では、キューブ内の指定された座標 (製品 X, 1998, Northwest) にあるセルの値が回答 (1 つの数値) になります。  
  
 回答が複数の値になる質問もあります。 たとえば、"1998 年のハードウェア製品の四半期別の地域別売上は?" のような質問です。 この場合、指定された条件を満たす座標位置にある各セルが返されます。 返されるセルの数は、製品ディメンションの Hardware レベルに含まれる項目数、1998 年の 4 つの四半期、および地理ディメンションの地域数によって決まります。 ここで、すべての要約データが事前計算され集計として格納されていれば、このクエリの応答時間は、指定されたセルの抽出に必要な時間だけになります。 つまり、データの計算やファクト テーブルからのデータの読み取りは必要ありません。  
  
 キューブに含まれるすべての集計を事前計算しておくと、すべてのクエリの応答時間が最も高速になりますが、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では特定の集計値を他の事前計算された集計から簡単に計算することができます。 これに加えて、可能な集計をすべて計算するには、大量の処理時間とストレージが必要になります。 そのため、必要なストレージと事前計算される集計の割合の間にトレードオフが発生します。 集計を事前計算しない (0%) 場合、キューブに必要な処理時間とストレージ領域は最小限に抑えられます。ただし、各クエリへの応答に必要なデータをリーフ セルから取得してから、各クエリに応答するためにクエリ時に集計しなければならないので、クエリ応答時間は遅くなる可能性があります。 たとえば、前述の質問 ("北西地域における 1998 年の製品 X の売上は?") の場合、回答となる 1 つの数値を返すために、場合によっては何千行ものデータ行を読み取り、それぞれの行から Sales メジャーを求めるための列の値を抽出し、合計を算出しなければなりません。 これだけでなく、そのデータに使用されているストレージ モード (MOLAP、HOLAP、または ROLAP) によっても、データの取得に必要な時間が異なります。  
  
## <a name="designing-aggregations"></a>集計のデザイン  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]ならなかったの集計を選択して、他の集計は事前計算された値に基づいてすばやく計算するようにする高度なアルゴリズムが組み込まれています。 たとえば、時間階層の Month レベルの集計が事前計算されている場合、Quarter レベルの算出に必要なのは 3 つの数値を集計することだけで、これは要求時に即座に計算できます。 この方法では、クエリ応答時間への影響を最小限に抑えながら、処理時間を節約し、必要なストレージを削減できます。  
  
 集計のデザイン ウィザードには、このアルゴリズムに対するストレージと集計の割合の制約を指定するためのオプションが用意されています。これらのオプションを使用して、クエリ応答時間と必要なストレージの間のトレードオフを最適化することができます。 ただし、集計のデザイン ウィザードのアルゴリズムでは、すべてのクエリが等しく発生することが前提となっています。 また、使用法に基づく最適化ウィザードでは、クライアント アプリケーションによって送信されたクエリを分析して、メジャー グループの集計デザインを調整できます。 このウィザードを使用することで、キューブに必要なストレージにはほとんど影響を与えずに、使用頻度の低いクエリよりも使用頻度の高いクエリへの応答の方が高速になるように、キューブの集計をチューニングできます。  
  
 このウィザードを使用することで集計はデザインされますが、集計デザインの対象であるパーティションが処理されるまで、実際の計算は行われません。 キューブの構造が変更された場合、集計が作成された後、またはデータの追加またはキューブのソース テーブルで変更された場合は、通常、キューブの集計を確認し、キューブを再処理する必要があります。  
  
## <a name="see-also"></a>参照  
 [パーティションのストレージ モードと処理](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)  
  
  
