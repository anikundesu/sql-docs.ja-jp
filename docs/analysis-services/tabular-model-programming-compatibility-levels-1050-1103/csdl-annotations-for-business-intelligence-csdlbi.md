---
title: "Business Intelligence (CSDLBI) 向けの CSDL 注釈 |Microsoft ドキュメント"
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
applies_to: SQL Server 2016 Preview
ms.assetid: bf6f372a-bc67-45ea-a771-b2dc5b0527e5
caps.latest.revision: "21"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 4f41d6d697299ad964912fe1df86db9b0581cdda
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="csdl-annotations-for-business-intelligence-csdlbi"></a>ビジネス インテリジェンス向けの CSDL 注釈 (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]概念スキーマ定義言語をビジネス インテリジェンス注釈 (CSDLBI) と呼ばれる XML 形式で表形式モデルの定義の表示をサポートします。 このトピックでは、CSDLBI の概要および [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ モデルでの使用方法について説明します。  
  
## <a name="understanding-the-role-of-csdl"></a>CSDL の役割について  
 概念スキーマ定義言語 (CSDL) は、エンティティ、リレーションシップ、および関数を記述する XML ベースの言語です。 CSDL は Entity Data Framework の一部として定義されます。 BI 注釈は、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を使用してデータ モデリングをサポートするための拡張機能です。  
  
 CSDL は Entity Data Framework に準拠していますが、エンティティとリレーションシップのモデルについての理解や、テーブル モデルまたはモデルに基づくレポートを構築するための専用ツールは必要ありません。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] などのクライアント ツールや AMO などの API を使用してモデルを作成し、それをサーバーに配置します。 クライアントからモデルへの接続にはモデル定義ファイルを使用し、通常、モデル定義ファイルは SharePoint ライブラリにパブリッシュされます。レポート デザイナーとレポート コンシューマーは、このライブラリでモデルの定義ファイルを使用できます。 詳細については、次のリンクを参照してください。  
  
-   [テーブル モデル ソリューション (SSAS テーブル)](../../analysis-services/tabular-models/tabular-model-solutions-ssas-tabular.md)  
  
-   [テーブル モデル ソリューションの配置 &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md)  
  
-   [Power Pivot BI セマンティック モデル接続 &#40;.bism&#41;](../../analysis-services/power-pivot-sharepoint/power-pivot-bi-semantic-model-connection-bism.md)  
  
 CSDLBI スキーマは、[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] などのクライアントからのモデル定義の要求に対して、Analysis Services サーバーで生成されます。 クライアント アプリケーションは、モデル データをホストする Analysis Services サーバーに XML クエリを送信します。 その応答として、サーバーはモデル内のエンティティの定義を含む XML メッセージを CSDLBI 注釈を使用して送信します。 レポート クライアントは、この情報を使用して、フィールド、集計、およびモデルで使用可能なメジャーを表示します。 CSDLBI 注釈は、データのグループ化、並べ替え、および書式設定の方法に関する情報も提供します。  
  
 CSDLBI の全般については、次を参照してください。 [CSDLBI の概念](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/csdlbi-concepts.md)です。  
  
### <a name="working-with-csdl"></a>CSDL の操作  
 特定のテーブル モデルを表す CSDLBI 注釈のセットは、単純型と複合型の両方のエンティティのコレクションを含む XML ドキュメントです。 エンティティは、計算列、メジャーまたは KPI に含まれるテーブル (またはディメンション)、列 (属性)、関連付け (リレーションシップ) および式を定義します。  
  
 これらのオブジェクトを直接変更することはできません。テーブル モデルを操作するには、クライアント ツールおよびアプリケーション プログラミング インターフェイス (API) を使用してください。  
  
 モデルの CSDL を取得するには、モデルをホストするサーバーに DISCOVER 要求を送信します。 この要求は、サーバーとモデルのほか、必要に応じてビューまたはパースペクティブを指定して修飾する必要があります。 返されるメッセージは、XML 文字列です。 一部の要素は言語に依存しているため、現在の接続の言語に応じて異なる値が返される可能性があります。 詳細については、次を参照してください。 [DISCOVER_CSDL_METADATA 行セット](../../analysis-services/schema-rowsets/xml/discover-csdl-metadata-rowset.md)です。  
  
### <a name="csdlbi-versions"></a>CSDLBI のバージョン  
 元の CSDL 仕様 (Entity Data Framework に基づく) では、モデリングのサポートに必要なエンティティとプロパティの大半が規定されています。 BI 注釈は、テーブル モデルの特殊な要件、[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] などのクライアントに必要なレポート プロパティ、および多次元モデルに必要な追加のメタデータをサポートします。 このセクションでは、各バージョンでの更新内容を説明します。  
  
 **CSDLBI 1.0**  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] テーブル モデルをサポートするために CSDL スキーマに追加された最初のセットです。データ モデリング、カスタム計算、および拡張表現をサポートする注釈を含みました。  
  
-   テーブル モデルをサポートする新しい要素とプロパティ。 たとえば、モデルの作成に使用されるデータベース クエリの種類を指定するためのプロパティが追加されました。  
  
-   既存のエンティティの新しいプロパティと拡張。  たとえば、リレーションシップをサポートするように Association 要素が拡張されました。  
  
-   視覚化プロパティとナビゲーション プロパティ。 たとえば、カスタムの並べ替えフィールド、既定の画像をサポートするためのプロパティが追加されました。  
  
 **CSDLBI 1.1**  
  
 このバージョンの CSDLBI スキーマは、多次元データベース (OLAP キューブなど) をサポートします。 新しい要素とプロパティは次のとおりです。  
  
-   エンティティとしてディメンションのサポート。  
  
-   階層のサポート。  
  
-   ROLAP パーティションの公開。  
  
-   翻訳のサポート  
  
-   パースペクティブのサポート。  
  
 CSDLBI 注釈の個々 の要素の詳細については、次を参照してください。 [csdl の BI 注釈のテクニカル リファレンス](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)です。 CSDL のコア仕様については、次を参照してください。、 [CSDL 仕様](http://go.microsoft.com/fwlink/?LinkId=205855)msdn です。  
  
## <a name="see-also"></a>参照  
 [レベルを 1050 から 1103 表形式オブジェクト モデルの互換性を理解します。](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [CSDLBI の概念](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/csdlbi-concepts.md)   
 [レベルを 1050 から 1103 表形式オブジェクト モデルの互換性を理解します。](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  
