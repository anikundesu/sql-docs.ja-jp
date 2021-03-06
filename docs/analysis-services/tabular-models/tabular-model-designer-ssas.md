---
title: "テーブル モデル デザイナー |Microsoft ドキュメント"
ms.date: 10/19/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.custom: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.ASVS.BIDTOOLSET.TOPLEVSEMMODUIENTRY.F1
ms.assetid: 45735c57-2a95-4e45-8994-7242df6c9c5f
caps.latest.revision: "22"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 14a6ca056a079b4a51813783883cc09c5f53e8ad
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="tabular-model-designer-ssas"></a>テーブル モデル デザイナー (SSAS)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]テーブル モデル デザイナーの一部である[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]に統合された Microsoft [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]、プロフェッショナルなテーブル モデル ソリューションを開発するには、具体的には追加のプロジェクトの種類のテンプレートにします。  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] は無料で Web からダウンロードしてインストールできます。 詳細については、「[SQL Server Data Tools (SSDT) のダウンロード](../../ssdt/download-sql-server-data-tools-ssdt.md)」を参照してください。    
  
##  <a name="bkmk_benefits"></a> 利点  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]をインストールすると、テーブル モデルを作成するための新しいプロジェクト テンプレートが、使用可能なプロジェクトの種類に追加されます。 いずれかのテンプレートを使用して新しいテーブル モデル プロジェクトを作成した後は、テーブル モデル デザイナー ツール、およびウィザードを使用して、モデル作成を開始できます。  
  
 プロフェッショナルな多次元のテーブル モデル ソリューション作成のための新しいテンプレートとツールのほかに、 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 環境には、組織のために最も強力な BI ソリューションを作成するための、デバッグ、およびプロジェクトのライフ サイクルに関する機能が用意されています。 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]の詳細については、「 [Visual Studio の概要](http://go.microsoft.com/fwlink/?LinkId=206389)」を参照してください。  
  
##  <a name="bkmk_proj_temp"></a>プロジェクト テンプレート  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]をインストールすると、以下のテーブル モデル プロジェクト テンプレートがビジネス インテリジェンス プロジェクトの種類に追加されます。  
  
 **Analysis Services のテーブル プロジェクト**  
 このテンプレートを使用すると、新しい、空白のテーブル モデル プロジェクトを作成できます。 互換性レベルは、プロジェクトを作成するときに指定します。
  
 **サーバー (表形式) からのインポート**  
 このテンプレートを使用すると、Analysis Services 内の既存のテーブル モデルからメタデータを抽出して、新しいテーブル モデル プロジェクトを作成できます。  
  
 既存のモデルには、以前の互換性レベルが設定されています。 モデル定義をインポートした後は、互換性レベルのプロパティを変更することでアップグレードすることができます。  
  
 **インポート: [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]**  
 このテンプレートを使用すると、 [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] ファイルからメタデータとデータを抽出して、新しいテーブル モデル プロジェクトを作成できます。  
  
##  <a name="bkmk_wind_men"></a> ウィンドウおよびメニュー  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] のテーブル モデルの作成環境には、次が含まれています。  
  
### <a name="designer-window"></a>デザイナー ウィンドウ  
 デザイナー ウィンドウは、モデルを視覚的に表現し、テーブル モデルの作成に使用されます。 Model.bim ファイルを開くと、デザイナー ウィンドウにそのモデルが表示されます。 デザイナー ウィンドウでは、2 つの異なる表示モードを使用してモデルを作成することができます。  
  
 **データ ビュー**  
 データ ビューではテーブルが表形式のグリッド形式で表示されます。 また、メジャー グリッドを使用してメジャーを定義することもできます。メジャー グリッドはテーブルごとにデータ ビューのみで表示することができます。  
  
 **ダイアグラム ビュー**  
 ダイアグラム ビューでは、テーブル間のリレーションシップと共にグラフィカルな形式でテーブルが表示されます。 列、メジャー、階層、および KPI はフィルター選択することも、定義済みのパースペクティブを使用してモデルを表示することを選択することもできます。  
  
 どちらのビューでもほとんどのモデル作成タスクを実行できます。  
  
### <a name="view-code-window"></a>コード ウィンドウを表示します。  
 ソリューション エクスプローラーでファイルを右クリックして **[コードの表示]** を選択すると、Model.bim ファイルのコードを表示できます。 互換性レベル 1200 以降の表形式モデル、モデル定義は JSON で表されます。  
  
 JSON エディターを含む、通常版の Visual Studio が必要です。 商用エディションに含まれる追加機能が不要な場合は、 [無料の Visual Studio Community エディション](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx) をダウンロードしてインストールできます。  
  
### <a name="solution-explorer"></a>ソリューション エクスプローラー  
 ソリューション エクスプローラー ウィンドウには、テーブル モデル プロジェクトの論理的コンテナーとしての作業対象のソリューションと、その関連付けられたアイテムが表示されます。 モデル プロジェクト (.smproj) には、References オブジェクト (空) と Model.bim ファイルのみが含まれます。 このビューからプロジェクト アイテムを開いて、変更やその他の管理作業を直接実行することができます。  
  
 テーブル モデル ソリューションには、通常、1 つのプロジェクトしか含まれませんが、ソリューションには、Integration Services プロジェクトや Reporting Services プロジェクトなど、その他のプロジェクトも含まれる場合があります。 テーブル モデル プロジェクト ファイルと異なる種類で、ビルド アクション プロパティが [なし] に設定されているか、出力ディレクトリにコピー プロパティが [コピーしない] に設定されている場合は、任意数のファイルを追加することができます。  
  
 ソリューション エクスプローラーを表示するには、 **[表示]** メニューの **[ソリューション エクスプローラー]**をクリックします。  

### <a name="tabular-model-explorer"></a>テーブル モデル エクスプローラー
  最初の 2016 年 8 月リリース (14.0.60812.0) で利用できる[SQL Server Data Tools](https://msdn.microsoft.com/mt186501)、表形式モデル エクスプ ローラーでは表形式モデルのメタデータ オブジェクトを移動できます。

 テーブル モデル エクスプローラーを表示するには、 **[表示]** > **[その他のウィンドウ]**の順にクリックして、 **[Tabular Model Explorer (テーブル モデル エクスプローラー)]**をクリックします。
   
  ![テーブル モデル エクスプローラー](../../analysis-services/tabular-models/media/tabular-model-explorer.png) 
  
 表形式モデル エクスプ ローラーでは、メタデータ オブジェクトを表形式モデルのスキーマとよく似たツリー構造に整理します。 [データ ソース]、[パースペクティブ]、[リレーションシップ]、[ロール]、[テーブル]、および [翻訳] は、最上位のスキーマ オブジェクトに対応します。 KPI とメジャーだけに当てはまる例外がいくつかあります。KPI とメジャーは技術的には最上位オブジェクトではなく、モデルのさまざまなテーブルの子オブジェクトです。 ただし、すべての KPI とメジャー用に統合された最上位コンテナーがあるため、これらのオブジェクトを (特に、非常に多数のテーブルが含まれている場合に) 簡単に操作できます。 メジャーは対応する親テーブルの下にも表示されるので、実際の親子関係がよくわかります。 最上位のメジャー コンテナーでメジャーを選択すると、テーブルの下にある子コレクションでも同じメジャーが選択され、逆の場合も同様です。  
 
 テーブル モデル エクスプローラーのオブジェクト ノードは、これまでは Visual Studio の [モデル]、[テーブル]、[列] メニューの下に隠れていた適切なメニュー オプションにリンクしています。 オブジェクトを右クリックして、オブジェクトの種類のオプションを確認できます。 コンテキスト メニューがまだないオブジェクト ノードの種類もありますが、今後のリリースでオプションが追加されて機能が強化されます。 

 テーブル モデル エクスプローラーでは、便利な検索機能も提供されます。 検索ボックスの名前の部分に入力するだけで、テーブル モデル エクスプローラーのツリー ビューがそれに合わせて絞り込まれます。 
  
### <a name="properties-window"></a>[プロパティ] ウィンドウ  
 プロパティ ウィンドウには、選択したオブジェクトのプロパティが一覧表示されます。 次のオブジェクトには、プロパティ ウィンドウで表示および編集できるプロパティがあります。  
  
-   Model.bim  
  
-   Table  
  
-   列  
  
-   [メジャー]  
  
 プロジェクト ウィンドウには、プロジェクト プロパティによりプロジェクト名とプロジェクト フォルダーのみが表示されます。 プロジェクトには、モーダル プロパティ ダイアログ ボックスを使用して設定できる配置オプションと配置サーバーの追加の設定もあります。 これらのプロパティを表示するには、 **ソリューション エクスプローラー**で、プロジェクトを右クリックして、 **[プロパティ]**をクリックします。  
  
 プロパティ ウィンドウのフィールドには、クリックすると開くコントロールが埋め込まれています。 編集コントロールの種類は、プロパティごとに異なります。 コントロールには、エディット ボックス、ドロップダウン リスト、およびカスタム ダイアログ ボックスへのリンクが含まれています。 淡色表示のプロパティは読み取り専用です。  
  
 **プロパティ** ウィンドウを開くには、 **[表示]** メニューをクリックしてから **[プロパティ ウィンドウ]**をクリックします。  
  
### <a name="error-list"></a>エラー一覧  
 エラー一覧ウィンドウには、次のようなモデルの状態に関するメッセージが含まれています。  
  
-   セキュリティのベスト プラクティスについての通知。  
  
-   データ処理の要件。  
  
-   計算列、メジャー、およびロールの行フィルターのセマンティック エラー情報。 計算列では、エラー メッセージをダブルクリックすると、エラーのソースに移動できます。  
  
-   DirectQuery 検証エラー。  
  
 既定では、 **エラー一覧** は、エラーが返されない限り表示されません。 ただし、 **エラー一覧** ウィンドウはいつでも表示できます。 **エラー一覧** ウィンドウを表示するには、 **[表示]** メニューをクリックしてから **[エラー一覧]**をクリックします。  
  
### <a name="output"></a>出力  
 ビルドと配置の情報が、(進捗状況のモーダル ダイアログに加えて) **出力** ウィンドウに表示されます。 **出力** ウィンドウを表示するには、 **[表示]** をクリックしてから [出力] をクリックします。  
  
### <a name="menu-items"></a>メニュー項目  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]をインストールすると、テーブル モデルの作成のために特化したメニュー項目が Visual Studio のメニュー バーに追加されます。 **[モデル]** メニューを使用して、データ インポート ウィザードを起動したり、既存の接続を表示したり、ワークスペース データを処理したりできるほか、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel でモデル ワークスペースを参照することもできます。 **[テーブル]** メニューは、テーブル間のリレーションシップの作成と管理、メジャーの作成と管理のほか、データ テーブルの設定や計算オプションなど、各種のテーブル プロパティを指定する際に使用します。 **[列]** メニューでは、テーブル内の列の追加と削除、列の表示と非表示のほか、列のプロパティ (データ型、フィルターなど) を指定することができます。 テーブル モデル ソリューションは、 **[ビルド]** メニューからビルドおよび配置できます。 コピーと貼り付けの機能は、 **[編集]** メニューに含まれています。  
  
 これらのメニュー項目に加えて、Analysis Services のオプションに別途設定が追加されます。追加された設定には、[ツール] のメニュー項目からアクセスすることができます。  
  
### <a name="toolbar"></a>[ツール バー]  
 Analysis Services ツール バーを使用すると、最もよく使用されるモデル作成コマンドにすばやく簡単にアクセスできます。  
  
##  <a name="bkmk_vsint"></a>Visual Studio の統合  
 **ソース管理**  
 Analysis Services プロジェクトは、選択したソース管理プラグインと統合されます。 ソース コントロールを使用するように Visual Studio を構成した場合は、ソリューション エクスプローラーからチェックインとチェックアウトを使用できます。 Team Foundation Server を使用するように構成するには、「 [Team Foundation バージョン管理を使用する Visual Studio の構成](http://msdn.microsoft.com/library/ms253064.aspx)」を参照してください。 多くのサード パーティ製ソース管理プラグインもサポートされます。  
  
 **フォント**  
 テーブル モデルでは [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 環境フォントを使用して表示フォントを制御します。 既定の [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] フォントに、対象の言語で必要なすべての Unicode 文字がない場合は、このフォントの変更が必要になることがあります。 フォントを変更するには、 **[ツール]** メニューをクリックし、 **[オプション]**、 **[フォントおよび色]**の順にクリックします。  
  
 **キーボード ショートカット**  
 Analysis Services のキーボード ショートカットは、[ツール]  > [オプション] > [キーボード] ダイアログで構成/再マップできます。 テーブル モデル デザイナーのコンテキストでは、ビルド、保存、デバッグ、新しいプロジェクトなど、一部のグローバル [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ショートカットがサポートされています。 その他のテーブル モデル デザイナーに固有のショートカットは Analysis Services コンテキストです。  
  
## <a name="see-also"></a>参照  
 [テーブル モデル プロジェクト (SSAS テーブル)](../../analysis-services/tabular-models/tabular-model-projects-ssas-tabular.md)   
 [プロパティ (SSAS テーブル)](../../analysis-services/tabular-models/properties-ssas-tabular.md)  
  
  
