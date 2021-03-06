---
title: "1103 を通じてレベル 1050 に表形式オブジェクト モデルを理解する |Microsoft ドキュメント"
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
ms.assetid: 6077b7e8-cb3e-4480-a5de-bb602cf9d69a
caps.latest.revision: "10"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 48091c81446898964d504f1a174f68f1ee90af92
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="understanding-tabular-object-model-at-levels-1050-through-1103"></a>1103 を通じてレベル 1050 に表形式オブジェクト モデルを理解します。
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
[!INCLUDE[ssas-appliesto-sqlas-all](../../../includes/ssas-appliesto-sqlas-all.md)]

  テーブル モデルは、テーブル、リレーションシップ、階層、パースペクティブ、メジャー、および主要業績に関する論理的表現です。 ここでは、AMO を使用した内部実装について説明します。 参照してください[分析管理オブジェクト &#40; を使用した開発AMO &#41;](../../../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)までに AMO を使用していない場合。  
  
 ここで使用するアプローチはトップダウンであり、テーブル モデルに関連するすべてのオブジェクトを論理的に AMO オブジェクトにマップし、必須の対話型操作やワークフローについて説明します。 AMO、AMO to Tabular サンプルを使用して表形式モデルを作成するソース コード サンプルは、Codeplex から入手できます。 サンプル内のコードに関する重要な注意: コードはここで説明する論理的概念をサポートする目的でのみ提供されるものであり、運用環境では使用しないでください。 サンプルは、サポートや保証なしで提供されます。  
  
## <a name="database-representation"></a>データベース表現  
 データベースは、テーブル モデルに対応するコンテナー オブジェクトを提供します。 テーブル モデル内のすべてのオブジェクトは、データベースに格納されます。 AMO オブジェクトの場合、データベース表現は <xref:Microsoft.AnalysisServices.Database> と一対一マッピングのリレーションシップにあり、その他の主要 AMO オブジェクトを必要としません。 これは AMO データベース オブジェクトに含まれるすべてのオブジェクトが、モデリングの際に使用できるという意味ではないことに注意する必要があります。  
  
 参照してください[表現 &#40; データベース表形式 &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/database-representation-tabular.md)を作成してデータベース表現を操作する方法の詳細についてはします。  
  
## <a name="connection-representation"></a>接続表現  
 接続によって、テーブル モデル ソリューションに含めるデータとモデル自体の間のリレーションシップが確立されます。 AMO オブジェクトの場合、接続は <xref:Microsoft.AnalysisServices.DataSource> と一対一マッピングのリレーションシップにあり、その他の主要 AMO オブジェクトを必要としません。 これは AMO データソース オブジェクトに含まれるすべてのオブジェクトが、モデリングの際に使用できるという意味ではないことに注意する必要があります。  
  
 参照してください[接続表現 &#40;です。表形式 &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/connection-representation-tabular.md)作成し、データ ソースの表現を操作する方法の詳細についてはします。  
  
## <a name="table-representation"></a>テーブル表現  
 テーブルは、データベースのデータを格納するデータベース オブジェクトです。 AMO オブジェクトでは、テーブルは一対多マッピングのリレーションシップを持ちます。 テーブルは必要な主要オブジェクトである次の AMO オブジェクトを使用して表現されます。<xref:Microsoft.AnalysisServices.DataSourceView>、<xref:Microsoft.AnalysisServices.Dimension>、<xref:Microsoft.AnalysisServices.Cube>、<xref:Microsoft.AnalysisServices.CubeDimension>、<xref:Microsoft.AnalysisServices.MeasureGroup>、および <xref:Microsoft.AnalysisServices.Partition>。ただし、これは上記の AMO オブジェクトに含まれるすべてのオブジェクトが、モデリングの際に使用できるという意味ではないことに注意する必要があります。  
  
 参照してください[テーブルの表示 &#40;です。表形式 &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/tables-representation-tabular.md)作成し、テーブルの表現を操作する方法の詳細についてはします。  
  
### <a name="calculated-column-representation"></a>計算列表現  
 計算列はテーブル内の列を生成する評価式であり、新しい値が計算されてテーブル内の各行に格納されます。 AMO オブジェクトでは、計算列は一対多マッピングのリレーションシップを持ちます。 計算列は、必要な主要オブジェクトである次の AMO オブジェクトを使用して表現されます。<xref:Microsoft.AnalysisServices.Dimension> および <xref:Microsoft.AnalysisServices.MeasureGroup>。 これは上記の AMO オブジェクトに含まれるすべてのオブジェクトが、モデリングの際に使用できるという意味ではないことに注意する必要があります。  
  
 参照してください[計算列表現 &#40;です。表形式 &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/tables-calculated-column-representation.md)作成し、計算列表現を操作する方法の詳細についてはします。  
  
### <a name="calculated-measure-representation"></a>計算されるメジャー表現  
 計算されるメジャーは、モデルが展開された後で要求によって評価されるストアドの式です。 AMO オブジェクトでは、計算されるメジャーは一対多マッピングのリレーションシップを持ちます。 計算列は、必要な主要オブジェクトである次の AMO オブジェクトを使用して表現されます。<xref:Microsoft.AnalysisServices.MdxScript.Commands%2A> および <xref:Microsoft.AnalysisServices.MdxScript.CalculationProperties%2A>。 これは上記の AMO オブジェクトに含まれるすべてのオブジェクトが、モデリングの際に使用できるという意味ではないことに注意する必要があります。  
  
> [!NOTE]  
>  <xref:Microsoft.AnalysisServices.Measure> オブジェクトはテーブル モデル内の計算されるメジャーとのリレーションシップを持たず、テーブル モデルでサポートされません。  
  
 参照してください[計算されるメジャー表現 &#40;です。表形式 &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/tables-calculated-measure-representation.md)作成し、計算されるメジャー表現を操作する方法の詳細についてはします。  
  
### <a name="hierarchy-representation"></a>階層表現  
 階層は、高度なドリル アップおよびドリル ダウン操作をエンド ユーザーに提供するメカニズムです。 AMO オブジェクトの場合、階層表現は <xref:Microsoft.AnalysisServices.Hierarchy> と一対一マッピングのリレーションシップにあり、その他の主要 AMO オブジェクトを必要としません。 これは AMO データベース オブジェクトに含まれるすべてのオブジェクトが、テーブル モデリングを実行する際に使用できるという意味ではないことに注意する必要があります。  
  
 参照してください[階層表現 &#40;です。表形式 &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/tables-hierarchy-representation.md)を作成して階層表現を操作する方法の詳細についてはします。  
  
### <a name="key-performance-indicator-kpi--representation"></a>主要業績評価指標 (KPI) 表現  
 KPI は、対象の値に対するベース メジャーによって定義される値のパフォーマンスの測定に使用されます。 AMO オブジェクトでは、KPI 表現は一対多マッピングのリレーションシップを持ちます。 KPI は、必要な主要オブジェクトである次の AMO オブジェクトを使用して表現されます。<xref:Microsoft.AnalysisServices.MdxScript.Commands%2A> および <xref:Microsoft.AnalysisServices.MdxScript.CalculationProperties%2A>。  これは上記の AMO オブジェクトに含まれるすべてのオブジェクトが、モデリングの際に使用できるという意味ではないことに注意する必要があります。  
  
> [!NOTE]  
>  また、<xref:Microsoft.AnalysisServices.Kpi> オブジェクトはテーブル モデル内の KPI とリレーションシップを持たないことにも注意してください。 さらに、このオブジェクトはテーブル モデルではサポートされません。  
  
 参照してください[主要業績評価指標表現 &#40;です。表形式 &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/tables-key-performance-indicator-representation.md)を作成して、KPI 表現を操作する方法の詳細についてはします。  
  
### <a name="partition-representation"></a>パーティション表現  
 運用上の目的のために、結合させるとテーブルを形成する異なる行のサブセットにテーブルを分割することができます。 それぞれのサブセットがテーブルのパーティションです。 AMO オブジェクトでは、パーティション表現は一対一のマッピングのリレーションシップに<xref:Microsoft.AnalysisServices.Partition>とその他の主要 AMO オブジェクトは必要ありません。 これは AMO データベース オブジェクトに含まれるすべてのオブジェクトが、モデリングの際に使用できるという意味ではないことに注意する必要があります。  
  
 参照してください[表現 &#40; をパーティション分割表形式 &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/tables-partition-representation.md)作成し、パーティション表現を操作する方法の詳細についてはします。  
  
## <a name="relationship-representation"></a>リレーションシップ表現  
 リレーションシップとは、2 つのデータ テーブルの間の接続です。 これにより、2 つのテーブルのデータの関連付けの方法が決まります。  
  
 テーブル モデルでは、2 つのテーブル間に複数のリレーションシップを定義できます。 2 つのテーブル間に複数のリレーションシップを定義する場合、既定のアクティブなリレーションシップとして定義できるのは 1 つのみです。 その他のリレーションシップはすべて、非アクティブです。  
  
 AMO オブジェクトの場合、すべての非アクティブなリレーションシップが <xref:Microsoft.AnalysisServices.Relationship> と一対一マッピングのリレーションシップの表現を持ち、その他の主要 AMO オブジェクトを必要としません。 アクティブなリレーションシップの場合、それ以外の要件が存在し、<xref:Microsoft.AnalysisServices.ReferenceMeasureGroupDimension> へのマッピングも必須です。 これは AMO リレーションシップや referenceMeasureGroupDimension オブジェクトに含まれるすべてのオブジェクトがモデリングの際に使用できるという意味ではないことに注意する必要があります。  
  
 参照してください[リレーションシップ表現 &#40;です。表形式 &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/relationship-representation-tabular.md)作成し、リレーションシップ表現を操作する方法の詳細についてはします。  
  
## <a name="perspective-representation"></a>パースペクティブ表現  
 パースペクティブは、モデルを簡素化したり絞りこんだりするメカニズムです。 AMO オブジェクトの場合、リレーションシップ表現は <xref:Microsoft.AnalysisServices.Perspective> と一対一マッピングのリレーションシップにあり、その他の主要 AMO オブジェクトを必要としません。 これは AMO パースペクティブ オブジェクトに含まれるすべてのオブジェクトが、テーブル モデリングを実行する際に使用できるという意味ではないことに注意する必要があります。  
  
 参照してください[パースペクティブ表現 &#40;です。表形式 &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/perspective-representation-tabular.md)を作成して、パースペクティブ表現を操作する方法の詳細についてはします。  
  
> [!WARNING]  
>  パースペクティブはセキュリティ メカニズムではありません。パースペクティブの外にあるオブジェクトも、ユーザーは他のインターフェイスを利用してアクセスできます。  
  
  
