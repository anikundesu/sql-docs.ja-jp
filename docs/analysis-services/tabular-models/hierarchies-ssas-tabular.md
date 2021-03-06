---
title: "階層 |Microsoft ドキュメント"
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
ms.assetid: e3e50e89-f85d-485b-a271-1e0550520212
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 11112104f624c3594a99e867d03bfaaab28ac37c
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="hierarchies"></a>階層
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]テーブル モデルでの階層とは、テーブル内の 2 つ以上の列間のリレーションシップを定義するメタデータです。 階層は、あるレポート クライアント フィールドの一覧の他の列とは分けて表示できるため、クライアントのユーザーは簡単に移動し、レポートに含めることができます。  
  
##  <a name="bkmk_benefits"></a> 利点  
 テーブルには明確な規則性のない特殊な列名を持つ数十または数百の列が含まれる場合があります。 そのため、レポート クライアント フィールドの一覧での表示が無秩序になり、ユーザーがレポート内のデータを見つけたりレポートにデータを含めたりするのが難しくなることがあります。 階層では、複雑なデータ構造を単純で直感的な形式で表示できます。  
  
 たとえば、日付テーブルにカレンダー階層を作成できます。 カレンダーの年が最上位の親レベルとして使用され、子レベルとして月、週、日が含まれます (カレンダーの年 -> 月 -> 週 -> 日)。 この階層により、カレンダーの年から日までの論理関係が示されます。 クライアント ユーザーはフィールドの一覧からカレンダー年度を選択して、ピボットテーブルにレベルをすべて含めたり、階層を展開してピボットテーブルに含める特定のレベルだけを選択したりできます。  
  
 ある階層の各レベルは、あるテーブルの 1 列の表現なので、そのレベルの名前を変更できます。 階層に限定されてはいません (テーブル モデルではどの列でも名前を変更できます) が、階層レベル名を変更すると、ユーザーがレポート内のレベルを見つけたり含めたりするのが容易になります。 レベル名を変更しても、参照先の列名は変更されません。レベルが識別しやすくなるだけです。 カレンダー年度階層の例に示す、データ ビューの日付テーブルでは、CalendarYear、CalendarMonth、CalendarWeek、および CalendarDay の各列の名前が Calendar Year、Month、Week、および Day に変更され、識別が容易になりました。 レベル名を変更することには、複数レポート間での一貫性という利点もあります。これは、ピボットテーブルやチャートなどでの読み取りやすさを高めるためにユーザーが列名を変更する必要がほとんどなくなるからです。  
  
 パースペクティブに階層を含めることができます。 パースペクティブを使用すると、ビジネス固有またはアプリケーション固有のビューポイントをモデルに対して的を絞って作成するための、表示可能なサブセットを定義できます。 たとえば、パースペクティブによって、ユーザー固有のレポート要件に必要なデータ アイテムのみが含まれる表示可能な一覧 (階層) を作成できます。 詳細については、次を参照してください。[パースペクティブ](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)です。  
  
 階層は、セキュリティ メカニズムとして使用するためのものではなく、ユーザーの使用体験をより良いものにするためのツールとして使用するものです。 特定の階層のセキュリティはすべて、基になるモデルから継承されます。 階層では、ユーザーがアクセス権をまだ持っていないモデル オブジェクトにアクセスできません。 モデルのオブジェクトへのアクセスが階層を通じて提供されるようにするには、そのモデル データベースのセキュリティを解決しておく必要があります。 セキュリティ ロールを使用して、モデルのメタデータとデータをセキュリティ保護することができます。 詳細については、次を参照してください。[ロール](../../analysis-services/tabular-models/roles-ssas-tabular.md)です。  
  
##  <a name="bkmk_define"></a> Defining hierarchies  
 階層の作成と管理は、ダイアグラム ビューのモデル デザイナーを使用して行います。 階層の作成と管理は、データ ビューのモデル デザイナーではサポートされていません。 ダイアグラム ビューにモデル デザイナーを表示するには、 **[モデル]** メニューをクリックし、 **[モデル ビュー]**をポイントし、 **[ダイアグラム ビュー]**をクリックします。  
  
 階層を作成するには、親レベルとして指定する列を右クリックし、 **[階層の作成]**をクリックします。 (1 つのテーブル内で) 含める列の数に制限はなく、列をクリックして親レベルにドラッグすることで、子レベルとして後から追加することもできます。 複数の列を選択すると、基数に基づく順序で自動的に配置されます。 順序を変更するには、列 (レベル) をクリックして別の順序までドラッグするか、コンテキスト メニューにある上下の移動コントロールを使用します。 ある列を子レベルとして追加するとき、その列を親レベルにドラッグ アンド ドロップすることで、自動検出機能を使用できます。  
  
 1 つの列を複数の階層に表示することができます。 階層にメジャーや KPI などの非列オブジェクトを含めることはできません。 階層は単一のテーブルの列のみを基にして作成することができます。 1 つ以上の列と共に 1 つのメジャーを複数選択するか、または複数のテーブルから複数の列を選択した場合、コンテキスト メニューの **[階層の作成]** は無効になります。 異なるテーブルの列を追加するには、RELATED DAX 関数を使用して、関連するテーブル内の列を参照する計算列を追加します。 この関数では、 `=RELATED(TableName[ColumnName])`という構文を使用します。 関数の詳細については、「RELATED 関数」を参照してください。  
  
 既定では、新しい階層は hierarchy1、hierarchy 2、... のように名前が付けられます。親子関係の特性を反映するような階層名に変更して、ユーザーにとって識別しやすい名前にする必要があります。  
  
 階層の作成が完了したら、Excel で分析機能を使用して、階層の有効性をテストできます。 詳細については、次を参照してください。 [Excel で分析](../../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md)です。  
  
##  <a name="bkmk_related_tasks"></a> Related tasks  
  
|タスク|Description|  
|----------|-----------------|  
|[階層の作成および管理](../../analysis-services/tabular-models/create-and-manage-hierarchies-ssas-tabular.md)|ダイアグラム ビューのモデル デザイナーを使用して階層の作成と管理を行う方法について説明します。|  
  
## <a name="see-also"></a>参照  
 [テーブル モデル デザイナー](../../analysis-services/tabular-models/tabular-model-designer-ssas.md)   
 [パースペクティブ](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [Roles](../../analysis-services/tabular-models/roles-ssas-tabular.md)  
  
  
