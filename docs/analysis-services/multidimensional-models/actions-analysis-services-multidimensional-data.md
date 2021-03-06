---
title: "操作 (Analysis Services - 多次元データ) |Microsoft ドキュメント"
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
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- actions [Analysis Services]
- actions [Analysis Services], about actions
- MDX [Analysis Services], actions
- cubes [Analysis Services], actions
- OLAP objects [Analysis Services], actions
ms.assetid: 07229bb2-805c-427e-8455-69c9ca5d01e0
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 23021f365a349e226194326ed2d4d43acb2e7af8
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="actions-analysis-services---multidimensional-data"></a>アクション (Analysis Services - 多次元データ)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]アクションがさまざまな種類のありが適切に作成する必要があることができます。 アクションの種類は次のとおりです。  
  
-   ドリルスルー アクション。このアクションが発生したキューブで選択されているセル内のデータを表す行セットを返します。  
  
-   レポート アクション。このアクションは、実行されたキューブで選択されているセクションに関連付けられた [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] からレポートを返します。  
  
-   標準アクション。このアクションは、実行されたキューブで選択されているセクションに関連付けられたアクション要素 (URL、HTML、DataSet、RowSet などの要素) を返します。  
  
 アクションを取得してエンド ユーザーに公開する際、クライアント アプリケーションでは ADOMD.NET などのクエリ インターフェイスが使用されます。 詳細については、「 [ADOMD.NET での開発](../../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md)」を参照してください。  
  
 簡単な <xref:Microsoft.AnalysisServices.Action> オブジェクトは、基本情報、アクションが実行される対象、アクション スコープの限定条件、およびアクションの種類で構成されます。 基本情報には、アクションの名前、アクションの説明、アクションに推奨されるキャプションなどが含まれます。  
  
 対象は、アクションが実行されるキューブ内の実際の場所です。 対象は、対象の種類および対象オブジェクトで構成されます。 対象の種類は、アクションが有効化されるキューブ内のオブジェクトの種類を表します。 対象の種類には、レベル メンバー、セル、階層、階層メンバーなどがあります。 対象オブジェクトは、その対象の種類に属する特定のオブジェクトです。対象の種類が階層の場合、対象オブジェクトは、キューブ内で定義された階層のうちの 1 つです。  
  
 条件は、アクション イベント時に評価される、 **ブール値** の MDX 式です。 条件が **true**と評価された場合に、アクションが実行されます。 それ以外の場合、アクションは実行されません。  
  
 種類は、実行されるアクションの種類です。 <xref:Microsoft.AnalysisServices.Action> は抽象クラスであるため、これを使用するにはその派生クラスのいずれかを使用する必要があります。 2 種類のアクションが事前定義されています。ドリルスルーおよびレポートです。 これらのアクションには次の対応する派生クラスがあります: <xref:Microsoft.AnalysisServices.DrillThroughAction> と <xref:Microsoft.AnalysisServices.ReportAction>」を参照してください。 その他のアクションは、 <xref:Microsoft.AnalysisServices.StandardAction> クラスに含まれます。  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]でのアクションとは、クライアント アプリケーションによって表示および使用されるストアド MDX ステートメントです。 つまり、アクションとは、サーバーで定義され格納されたクライアント コマンドです。 また、クライアント アプリケーションによって MDX ステートメントを表示および処理するタイミングと方法を指定する情報も含まれています。 アクションで指定される操作では、アクションに含まれる情報をパラメーターとして使用してアプリケーションを起動したり、アクションで指定される条件に基づいて情報を取得することができます。  
  
 アクションを使用すると、ビジネス ユーザーは分析結果に従った操作を実行できます。 従来の分析は、データの表示で終わることが普通でしたが、アクションを保存および再利用することで、エンド ユーザーはそれ以上の効果を得ることができます。問題と欠陥を検出するソリューションを開始できるので、キューブの範囲を超えてビジネス インテリジェンス アプリケーションを拡張できます。 アクションの利用により、クライアント アプリケーションを高度なデータ表示ツールから企業の運用システムの不可欠部分へと変えることができます。 エンド ユーザーは、運用アプリケーションへの入力としてのデータ送信に終始せず、むしろ意思決定プロセスの "環を閉じる (Closing the Loop)" ことができるのです。 分析データを意思決定に変えることのできる能力は、成功をもたらすビジネス インテリジェンス アプリケーションにとって不可欠です。  
  
 たとえば、キューブを参照するビジネス ユーザーが、ある製品の現在の在庫が不足していることに気付いたとします。 クライアント アプリケーションは、Analysis Services データベースから取得したアクションの一覧をビジネス ユーザーに提供します。この一覧に含まれるすべてのアクションは、製品在庫の値が不足していることに関係しています。ここでビジネス ユーザーが、製品を表すキューブのメンバーの Order アクションを選択するとします。 Order アクションにより、運用データベースのストアド プロシージャが呼び出されて、新しい注文が開始されます。 このストアド プロシージャでは、適切な情報が生成されて注文入力システムに送信されます。  
  
 アクションは、柔軟に作成できます。たとえば、アクションでアプリケーションを起動したり、データベースから情報を取得することができます。 ディメンション、レベル、メンバー、セルなど、キューブのほとんどすべての部分からアクションがトリガーされるように構成したり、キューブの同じ部分に対して複数のアクションを作成することができます。 また、起動したアプリケーションに文字列パラメーターを渡して、アクションの実行時にエンド ユーザーに表示されるキャプションを指定することもできます。  
  
> [!IMPORTANT]  
>  ビジネス ユーザーがアクションを使用するには、ビジネス ユーザーが実行するクライアント アプリケーションでアクションがサポートされている必要があります。  
  
## <a name="types-of-actions"></a>アクションの種類  
 次の表に、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]に含まれているアクションの種類を示します。  
  
|アクションの種類|Description|  
|-----------------|-----------------|  
|CommandLine|コマンド プロンプトでコマンドを実行します。|  
|データセット|データセットをクライアント アプリケーションに返します。|  
|ドリルスルー|ドリルスルー ステートメントを式として返します。この式は、行セットを返すときにクライアントによって実行されます。|  
|Html|インターネット ブラウザーで HTML スクリプトを実行します。|  
|[専用]|この一覧に表示されていないインターフェイスを使用して操作を実行します。|  
|レポート|パラメーター化された URL ベースの要求をレポート サーバーに送信して、レポートをクライアント アプリケーションに返します。|  
|[行セット]|行セットをクライアント アプリケーションに返します。|  
|ステートメントから削除してください。|OLE DB コマンドを実行します。|  
|[URL]|インターネット ブラウザーで動的 Web ページを表示します。|  
  
## <a name="resolving-and-executing-actions"></a>アクションの競合回避と実行  
 コマンド オブジェクトが定義されているオブジェクトにビジネス ユーザーがアクセスすると、アクションに関連付けられているステートメントが自動的に解決されます。このため、クライアント アプリケーションでそのステートメントを利用できるようになりますが、アクションが自動的に実行されるわけではありません。 アクションは、ビジネス ユーザーがそのアクションを開始するクライアント固有の操作をしたときにのみ実行されます。 たとえば、クライアント アプリケーションでは、ビジネス ユーザーが特定のメンバーまたはセルを右クリックしたときに、ポップアップ メニューとしてアクションの一覧を表示できます。  
  
## <a name="see-also"></a>参照  
 [多次元モデルのアクション](../../analysis-services/multidimensional-models/actions-in-multidimensional-models.md)  
  
  
