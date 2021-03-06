---
title: "多次元モデルのデータ アクセス (Analysis Services - 多次元データ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
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
- SSAS, data access interfaces
- objects [Analysis Services], data access interfaces
- Analysis Services data access interfaces
- data retrieval [Analysis Services]
- retrieving data
- metadata [Analysis Services]
- data access interfaces [Analysis Services]
- manipulating objects [Analysis Services]
- Analysis Services data access interfaces, about data access interfaces
ms.assetid: 46388efb-3c78-47a2-b5c9-5a69ff394d03
caps.latest.revision: "46"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 678912f45f94b99ce9abf96e864b60dd794f7b1c
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="multidimensional-model-data-access-analysis-services---multidimensional-data"></a>多次元モデルのデータ アクセス (Analysis Services - 多次元データ)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]このトピックの情報を使用してアクセスする方法について[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]プログラム方法、スクリプト、またはに接続するための組み込みサポートが含まれているクライアント アプリケーションを使用してデータを多次元、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]ネットワーク上のサーバー。  
  
 このトピックには、次のセクションが含まれます。  
  
 [クライアント アプリケーション](#bkmk_clientapps)  
  
 [クエリ言語](#bkmk_querylang)  
  
 [プログラミング インターフェイス](#bkmk_api)  
  
##  <a name="bkmk_clientapps"></a> クライアント アプリケーション  
 Analysis Services は、多次元データベースをプログラムから構築または統合できるインターフェイスを備えていますが、実際には、Analysis Services のデータにアクセスするための機能が組み込まれた既存のクライアント アプリケーションが Microsoft やその他のソフトウェア ベンダーから提供されているため、そちらを利用する方が一般的です。  
  
 次の Microsoft アプリケーションでは、多次元データへのネイティブ接続がサポートされます。  
  
### <a name="excel"></a>Excel  
 通常、Analysis Services の多次元データの表示には、Excel ブックのピボット テーブルとピボット グラフ コントロールが使用されます。 モデル内の階層と集計、ナビゲーション構造は、ピボットテーブルのデータ サマリー機能と相性がよいことから、ピボットテーブルは多次元データに適しています。 データ接続を簡単にセットアップできるように、Analysis Services OLE DB データ プロバイダーは Excel のインストールに含まれています。 詳細については、「 [SQL Server Analysis Services のデータに接続する、または SQL Server Analysis Services のデータをインポートする](http://go.microsoft.com/fwlink/?linkID=215150)」を参照してください。  
  
### <a name="reporting-services-reports"></a>Reporting Services レポート  
 レポート ビルダーまたはレポート デザイナーを使用すると、分析データを格納する Analysis Services データベースを利用したレポートを作成できます。 レポート ビルダーとレポート デザイナーにはどちらも MDX クエリ デザイナーが備わっており、利用可能なデータ ソースからデータを取得する MDX ステートメントを、このクエリ デザイナーを使用して入力、設計することができます。 詳細については、「[Reporting Services でサポートされるデータ ソース (SSRS)](../../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md)」と「[MDX のための Analysis Services の接続の種類 (SSRS)](../../../reporting-services/report-data/analysis-services-connection-type-for-mdx-ssrs.md)」を参照してください。  
  
### <a name="performancepoint-dashboards"></a>PerformancePoint ダッシュボード  
 PerformancePoint ダッシュボードは、あらかじめ定義された指標に対しての業績を表すスコアカードを SharePoint で作成するときに使用します。 PerformancePoint は、Analysis Services 多次元データへのデータ接続をサポートします。 詳細については、「 [Analysis Services のデータ接続を作成する (PerformancePoint Services)](http://go.microsoft.com/fwlink/?linkid=232471)」を参照してください。  
  
### <a name="sql-server-data-tools"></a>SQL Server Data Tools  
 モデル デザイナーとレポート デザイナーでは、SQL Server データ ツールを使用して、多次元モデルを含んだソリューションを構築します。 Analysis Services インスタンスにソリューションを配置するということは、後でビジネス インテリジェンス クライアント アプリケーション (Excel や Reporting Services など) から接続するためのデータベースを作成するということです。  
  
 SQL Server データ ツールは Visual Studio のシェルをベースに構築されており、モデルの編成と格納にはプロジェクトが使用されます。 詳細については、「[SQL Server データ ツール (SSDT) を使用した多次元モデルの作成](../../../analysis-services/multidimensional-models/creating-multidimensional-models-using-sql-server-data-tools-ssdt.md)」を参照してください。  
  
### <a name="sql-server-management-studio"></a>SQL Server Management Studio  
 データベース管理者にとって SQL Server Management Studio は、多次元データベースや Analysis Services のインスタンスを含む、SQL Server のインスタンスを管理するための統合環境です。 詳細については、「 [SQL Server Management Studio](http://msdn.microsoft.com/library/66a6b7b1-de6a-4161-82bd-98ded486947b) 」と「 [Analysis Services への接続](../../../analysis-services/instances/connect-to-analysis-services.md)」を参照してください。  
  
##  <a name="bkmk_querylang"></a> クエリ言語  
 MDX は、OLAP データベースからデータを取得するための業界標準のクエリ/計算言語です。 Analysis Services において、MDX は、データを取得するためのクエリ言語であると共に、データの定義とデータの操作にも対応しています。 SQL Server Management Studio、Reporting Services、および SQL Server データ ツールには MDX エディターが組み込まれています。 使用頻度の高いデータ操作については、MDX エディターを使用して、アドホック クエリや再利用可能なスクリプトを作成することができます。  
  
 Excel をはじめとする一部のツールやアプリケーションでは、Analysis Services データ ソースをクエリする際に MDX の構文が内部的に使用されています。 XMLA の Execute 要求に MDX ステートメントを含めることによって、プログラムから MDX を使用することもできます。  
  
 MDX の詳細については、次のリンクを参照してください。  
  
 [MDX による多次元データのクエリ](../../../analysis-services/multidimensional-models/mdx/querying-multidimensional-data-with-mdx.md)  
  
 [MDX の主な概念 (Analysis Services)](../../../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)  
  
 [MDX クエリの基礎 (Analysis Services)](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
 [MDX スクリプティングの基礎 (Analysis Services)](../../../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)  
  
##  <a name="bkmk_api"></a> プログラミング インターフェイス  
 多次元データを使用したカスタム アプリケーションを構築する場合のデータへのアクセス手段は、そのほとんどが、次のいずれかのカテゴリに該当します。  
  
-   **XMLA**。 広範なオペレーティング システムおよびプロトコルとの互換性を確保する必要がある場合は XMLA を使用します。 柔軟性の点では XMLA に勝る手段はありませんが、その分、パフォーマンスの高さとプログラミングのしやすさが損なわれる場合があります。  
  
-   **クライアント ライブラリ**。 Microsoft Windows オペレーティング システム上のクライアント アプリケーションからプログラムによってデータにアクセスするには、ADOMD.NET、AMO、OLE DB など、Analysis Services のクライアント ライブラリを使用します。 クライアント ライブラリでは、XMLA がオブジェクト モデルによってラップされ、より高いパフォーマンスを実現するために最適化されています。  
  
     ADOMD.NET と AMO クライアント ライブラリは、マネージ コードで作成されたアプリケーション用です。 アプリケーションがネイティブ コードで作成されている場合は、OLE DB for Analysis Services を使用してください。  
  
 Analysis Services をカスタム アプリケーションに接続するためのクライアント ライブラリについて、より詳しい情報とリンクを次の表に示します。  
  
|インターフェイス|Description|  
|---------------|-----------------|  
|Analysis Services 管理オブジェクト (AMO)|AMO は、Analysis Services のインスタンスと多次元データベースをコードで管理するための主要なオブジェクト モデルです。 たとえば、SQL Server Management Studio では、サーバーとデータベースの管理をサポートするために AMO が使用されています。 詳細については、「[分析管理オブジェクト (AMO) による開発](../../../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)」を参照してください。|  
|ADOMD.NET|ADOMD.NET は、カスタム アプリケーションから多次元データを作成し、利用するための主要なオブジェクト モデルです。 マネージ クライアント アプリケーションでは ADOMD.NET を使用して、共通の Microsoft .NET Framework データ アクセス インターフェイスを経由して [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 情報を取得できます。 詳細については、「 [ADOMD.NET での開発](../../../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md) 」と「 [ADOMD.NET クライアント プログラミング](../../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)」を参照してください。|  
|Analysis Services OLE DB Provider (MSOLAP.dll)|ネイティブ OLE DB プロバイダーを使用すると、プログラムで非マネージ API から [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] にアクセスすることができます。 詳細については、「[Analysis Services OLE DB Provider (Analysis Services - 多次元データ)](http://msdn.microsoft.com/library/cdeecd50-1d91-4162-a4a2-01c7799b02a8)」を参照してください。|  
|スキーマ行セット|スキーマ行セットのテーブルは、サーバーに配置された多次元モデルについての説明情報と、サーバー上の現在のアクティビティに関する情報を格納するデータ構造です。 プログラマは、クライアント アプリケーションからスキーマ行セットのテーブルをクエリすることによって、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスに格納されているメタデータを調べたり、サポート情報や監視情報を取得したりすることができます。 スキーマ行セットは、OLE DB、OLE DB for Analysis Services、OLE DB for Data Mining、XMLA のいずれかのプログラム インターフェイスで利用できます。 詳細については、「 [Analysis Services のスキーマ行セット](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)」をご覧ください。<br /><br /> 次の一覧では、スキーマ行セットを使用するためのいくつかの方法について説明します。<br /><br /> - SQL Server Management Studio またはカスタム レポートから、SQL 構文を使用して DMV クエリを実行し、スキーマ行セットにアクセスする。 詳細については、「[動的管理ビュー (DMV) を使用した Analysis Services の監視](../../../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)」を参照してください。<br /><br /> - スキーマ行セットを呼び出す ADOMD.NET コードを作成する。<br /><br /> - XMLA **Discover** メソッドを [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスに対して直接実行し、スキーマ行セット情報を取得する。 詳細については、「[Discover メソッド (XMLA)](../../../analysis-services/xmla/xml-elements-methods-discover.md)」を参照してください。|  
|XMLA|XMLA は、Analysis Services のプログラマが利用できる最下層の API であり、Analysis Services データに対するあらゆるアクセス手法の下に横たわる共通の基盤です。 XMLA は、SOAP ベースの業界標準の XML プロトコルで、HTTP 接続で利用できるあらゆる標準的な多次元データ ソースへの汎用データ アクセスをサポートします。 多次元データの要求と応答は SOAP を使用して作成されます。 アプリケーションが Windows 以外のプラットフォームで実行されている場合は、ネットワーク上の Windows サーバーで運用されている多次元データベースに、XMLA を使用してアクセスできます。 詳細については、「 [Analysis Services での XMLA による開発](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)」を参照してください。|  
|Analysis Services スクリプト言語 (ASSL)|ASSL は、XMLA プロトコルの Analysis Services 拡張機能を指す概念的な用語です。 XMLA プロトコルには Execute メソッドと Discover メソッドが定義されていますが、ASSL によって、次の機能が加わります。<br /><br /> - XMLA スクリプト<br /><br /> - XMLA オブジェクト定義<br /><br /> - XMLA コマンド<br /><br /> ASSL 拡張機能によってデータ定義、データ操作、データ制御への対応が可能となり、Analysis Services は、XMLA プロトコルに備わっている基本機能の枠を超えて XMLA の構成要素を使用することができます。 詳細については、「 [Analysis Services スクリプト言語 (ASSL) での開発](../../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)」を参照してください。|  
  
## <a name="see-also"></a>参照  
 [Analysis Services への接続](../../../analysis-services/instances/connect-to-analysis-services.md)   
 [Analysis Services スクリプト言語 &#40; を使用した開発ASSL &#41;](../../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Analysis Services の XMLA による開発](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)   
 [テーブル モデル データ アクセス](../../../analysis-services/tabular-models/tabular-model-data-access.md)  
  
  
