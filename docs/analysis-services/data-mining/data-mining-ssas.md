---
title: "データ マイニング (SSAS) |Microsoft ドキュメント"
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
ms.topic: article
helpviewer_keywords: data mining [Analysis Services], about data mining
ms.assetid: b1c912da-72f6-4d96-89c8-55a2c4f19e88
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: ac8390ebf0ffd45388d4fcea1dfbf846146b3b0d
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="data-mining-ssas"></a>データ マイニング (SSAS)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2000年リリース以降のデータ マイニングを提供することによって予測分析でリーダーが行われた[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]です。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ マイニングの組み合わせにより、データ クレンジングと準備、機械学習、およびレポート作成機能を備えた、予測分析の統合プラットフォームを提供しています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ マイニングには、EM および K-Means クラスタリング モデル、ニューラル ネットワーク、ロジスティック回帰と線形回帰、デシジョン ツリー、Naive Bayes 分類子など、複数の標準的なアルゴリズムが含まれています。 すべてのモデルに視覚エフェクトが統合されており、モデルの開発、調整、および評価が簡単に行えます。  データ マイニングをビジネス インテリジェンス ソリューションに統合することで、複雑な問題に関して合理的な意思決定を行う場合に、この情報を役立てることができます。  
  
## <a name="benefits-of-data-mining"></a>データ マイニングの利点  
 データ マイニング (予測分析と機械学習とも呼ばれます) では、詳細な研究に基づいた統計原則を使用してデータ内のパターンを検出します。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のデータ マイニング アルゴリズムをデータに適用することにより、傾向の予測、パターンの識別、およびルールや提案の作成を行い、複雑なデータ セット内でイベントの順序を分析し、新しい見識を得ることができます。  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のデータ マイニングは、強力でありながら使いやすく、分析用やレポート作成用として多くの人に使用されているツールに統合されています。  
  
## <a name="key-data-mining-features"></a>データ マイニングの主要機能  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ マイニングでは、統合データ マイニング ソリューションをサポートするために次の機能が提供されています。  
  
-   複数のデータ ソース: スプレッドシートやテキスト ファイルなど、任意の表形式のデータ ソースをデータ マイニングに使用することができます。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]で作成した OLAP キューブを簡単にマイニングすることもできます。 ただし、インメモリ データベースからのデータは使用できません。  
  
-   統合されたデータ クレンジング、データ管理、およびレポート: [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] では、データのプロファイリングとクレンジングのための高度なツールが提供されます。 モデル作成の準備段階でデータ クリーニング用の ETL プロセスを構築できます。また、ssISnoversion により、モデルの再トレーニングと更新が容易になります。  
  
-   複数のカスタマイズ可能なアルゴリズム: クラスタリング、ニューラル ネットワーク、デシジョン ツリーなどのアルゴリズムの提供に加え、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ マイニングは、独自のカスタム プラグイン アルゴリズムの開発をサポートします。  
  
-   モデル テスト用インフラストラクチャ: 相互検証、分類マトリックス、リフト チャート、散布図などの重要な統計ツールを使用して、モデルおよびデータ セットをテストできます。 テストおよびトレーニングのセットを容易に作成および管理できます。  
  
-   クエリおよびドリルスルー: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ マイニングでは、予測クエリをアプリケーションに統合するための DMX 言語が提供されます。 モデルから詳細な統計とパターンを取得し、ケース データにドリルスルーすることもできます。  
  
-   クライアント ツール: SQL Server で提供される開発および設計スタジオに加え、Excel 用データ マイニング アドインを使用して、モデルの作成、照会、および参照を行うことができます。 Web サービスなど、カスタムのクライアントを作成することもできます。  
  
-   スクリプト言語サポートとマネージ API: データ マイニング オブジェクトはすべて、プログラム可能です。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]用の MDX 拡張機能、XMLA 拡張機能、または、PowerShell 拡張機能により、スクリプトの作成が可能です。 データ マイニング拡張機能 (DMX) 言語を使用すると、クエリとスクリプト作成を迅速に行うことができます。  
  
-   セキュリティおよび配置: [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]により、ロール ベースのセキュリティが提供されます (モデルと構造データへのドリルスルーに、別々の権限を使用できるなど)。 他のサーバーへのモデルの配置が容易であるため、ユーザーがパターンにアクセスし、予測を実行することが可能になります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 このセクションのトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ マイニングの主要機能および関連タスクについて説明します。  
  
-   [データ マイニングの概念](../../analysis-services/data-mining/data-mining-concepts.md)  
  
-   [データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)  
  
-   [マイニング構造 &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)  
  
-   [マイニング モデル &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/mining-models-analysis-services-data-mining.md)  
  
-   [テストおよび検証 &#40;データ マイニング&#41;](../../analysis-services/data-mining/testing-and-validation-data-mining.md)  
  
-   [データ マイニング クエリ](../../analysis-services/data-mining/data-mining-queries.md)  
  
-   [データ マイニング ソリューション](../../analysis-services/data-mining/data-mining-solutions.md)  
  
-   [データ マイニング ツール](../../analysis-services/data-mining/data-mining-tools.md)  
  
-   [データ マイニングのアーキテクチャ](../../analysis-services/data-mining/data-mining-architecture.md)  
  
-   [セキュリティの概要 &#40;データ マイニング&#41;](../../analysis-services/data-mining/security-overview-data-mining.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server R サービス](../../advanced-analytics/r-services/sql-server-r-services.md)  
  
  
