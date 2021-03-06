---
title: "データ ソース ビュー (Analysis Services) でプロパティを変更 |Microsoft ドキュメント"
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
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- friendly names [Analysis Services]
- names [Analysis Services], data source views
- viewing tables
- displaying tables
- data source views [Analysis Services], tables
- tables [Analysis Services], data source views
ms.assetid: 4ccdabea-9c4d-460d-ba78-d23068143696
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b8d8d731552fe099d161d6b87bca87ceecd709a9
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="change-properties-in-a-data-source-view-analysis-services"></a>データ ソース ビューのプロパティの変更 (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]データ ソース ビュー ウィザードを使用して、テーブル、ビューを追加するデータ ソース ビューを定義する名前付き計算、および名前付きクエリ、データ ソースを表示後に、関連するプロパティを変更することがあります。  
  
-   データ ソース ビューの一致条件  
  
-   データ ソース ビューの詳細オプション  
  
-   オブジェクト名  
  
-   オブジェクト メタデータ  
  
 変更できないデータ ソースから取得したオブジェクト メタデータを表示することもできます。  
  
## <a name="viewing-or-changing-data-source-view-properties"></a>データ ソース ビューのプロパティの表示または変更  
 データ ソース ビューの説明以外のデータ ソース ビューのプロパティは、データ ソース ビューを最初に定義したときにデータ ソース ビュー ウィザードで設定されます。 次の表は、データ ソース ビューのプロパティの一覧およびその説明を示します。  
  
> [!NOTE]  
>  [プロパティ] ペインは、.dsv ファイルおよび DSV オブジェクトのプロパティを示しています。 オブジェクトのプロパティを表示するには、ソリューション エクスプ ローラーでプロパティをダブルクリックします。 次のテーブルに表示されるプロパティを反映してプロパティが更新されます。  
  
|プロパティ|Description|  
|--------------|-----------------|  
|[データ ソース]|表示中のプロパティを持つデータ ソース ビュー内のデータ ソースを指定します。|  
|Description|データ ソース ビューの説明を指定します。|  
|名前|ソリューション エクスプローラーまたは Analysis Services データベースに表示されるデータ ソース ビューの名前を指定します。 データ ソース ビュー名は、ここで変更するか、ソリューション エクスプローラーで変更できます。|  
|NameMatchingCriteria|データ ソースの名前一致条件。 主キーと外部キーのリレーションシップがデータ ソース ビュー ウィザードで検出された場合の既定値は (なし) です。 このプロパティがデータ ソース ビュー ウィザードで設定されているかどうかにかかわらず、ここでは値を指定できます。 データベース リレーションシップが存在している場合に名前一致条件を指定すると、これら両方が既存のテーブルと新たに追加されたテーブル間のリレーションシップの推測に使用されます。|  
|RetrieveRelationships|リレーションシップをデータベースから取得するかどうかを指定します。 既定値は True です。|  
|SchemaRestriction|データ ソースから取得されるスキーマに制限がある場合は、その制限を指定します。 既定では、スキーマの制限は存在しません。|  
  
## <a name="viewing-or-changing-datatable-properties"></a>DataTable プロパティの表示または変更  
 **DataTable** プロパティは、データ ソース ビュー内のテーブル、ビュー、および名前付きクエリのプロパティです。 これらのプロパティは、これらのオブジェクトのいずれかがデータ ソース ビューに追加されたときに設定されます。 次の表は、データ ソース ビューの **DataTable** オブジェクトのプロパティの一覧およびその説明を示します。  
  
|プロパティ|Description|  
|--------------|-----------------|  
|AllowChangesDuringGeneration|スキーマ生成ウィザードに、再生成中のデータ ソース ビューの上書き権限があるかどうかを指定します。 このプロパティは、スキーマ生成ウィザードによって最初に生成されたテーブルのみに存在します。 詳細については、「 [増分生成の理解](../../analysis-services/multidimensional-models/understanding-incremental-generation.md)」を参照してください。|  
|DataSource|オブジェクトのデータ ソースを指定します。 このプロパティを編集することはできません。|  
|Description|テーブル、ビュー、または名前付きクエリの説明を指定します。 基になるデータベース テーブルまたはビューに、拡張プロパティとして格納されている説明がある場合に、この値が表示されます。 このプロパティは編集できます。|  
|FriendlyName|ユーザーが理解しやすいか、サブジェクト領域との関連性が高いテーブル名またはビュー名を指定します。 既定では、テーブルまたはビューの **FriendlyName** プロパティは、テーブルまたはビューの **Name** プロパティと同じです。 **FriendlyName** プロパティは、テーブルまたはビューを基にしてオブジェクト名を定義するときに、OLAP およびデータ マイニング オブジェクトによって使用されます。 このプロパティは編集できます。|  
|名前|基になるテーブルまたはビューの名前、または名前付きクエリの名前を指定します。 **Name** プロパティは、名前付きクエリを基にしてオブジェクト名を定義するときに、OLAP およびデータ マイニング オブジェクトによって使用されます。 このプロパティは、名前付きクエリに対してのみ編集できます。|  
|QueryDefinition|名前付きクエリの定義を指定します。 このプロパティは名前付きクエリのみに適用され、直接編集することはできません。 このプロパティを編集するには、名前付きクエリ自体を編集します。|  
|スキーマ|テーブル、ビュー、または名前付きクエリに適用されるデータベース スキーマを指定します。 このプロパティは編集できません。|  
|TableType|テーブル、ビュー、または名前付きクエリのテーブルの種類を指定します。 このプロパティは編集できません。|  
  
## <a name="viewing-or-changing-datacolumn-properties"></a>DataColumn プロパティの表示または変更  
 **DataColumn** プロパティは、データ ソース ビュー内のテーブル、ビュー、および名前付きクエリ内の列のプロパティです。 これらのプロパティは、これらのオブジェクトのいずれかが、基になるテーブルかビューまたは名前付きクエリからデータ ソース ビューに追加されるか、名前付き計算で定義されてデータ ソース ビューに追加されるときに設定されます。 次の表は、データ ソース ビューの **DataColumn** オブジェクトのプロパティの一覧およびその説明を示します。  
  
|プロパティ|Description|  
|--------------|-----------------|  
|AllowNull|基になるテーブル内の列、値、または名前付きクエリに基づいて、列の NULL 値許容プロパティを指定します。 このプロパティは編集できません。|  
|DataType|基になるテーブル内の列、値、または名前付きクエリに基づいて列のデータ型を指定します。 このプロパティは直接編集できません。 ただし、テーブルまたはビューの列のデータ型を変更する必要がある場合は、列を目的のデータ型に変換する名前付きクエリにテーブルを置換します。|  
|DateTimeMode|**DateTime** 列の日付シリアル化形式を指定します。 既定値は **UnspecifiedLocal**です。 このプロパティは編集できます。|  
|Description|列の説明を指定します。 基になるデータベース列に、拡張プロパティとして格納されている説明がある場合に、この値が表示されます。 このプロパティは編集できます。|  
|FriendlyName|ユーザーが理解しやすいか、サブジェクト領域との関連性が高い、テーブルまたはビューの列の名前を指定します。 既定では、テーブルまたはビューの列の **FriendlyName** プロパティは、列の **Name** プロパティと同じです。 **FriendlyName** プロパティは、テーブルまたはビューの列を基にして属性を定義するときに、OLAP およびデータ マイニング オブジェクトによって使用されます。 このプロパティは編集できます。|  
|長さ|基になるテーブルまたはビュー内の列のデータに基づいて、列の最大長を指定します。|  
|名前|基になる列の名前、または名前付き計算の名前を指定します。 **Name** プロパティは、名前付き計算を基にして属性を定義するときに、OLAP およびデータ マイニング オブジェクトによって使用されます。 このプロパティは、名前付き計算に対してのみ編集できます。|  
  
## <a name="see-also"></a>参照  
 [多次元モデル内のデータ ソース ビュー](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)   
 [データ ソース ビュー デザイナーでのダイアグラムの操作 (Analysis Services)](../../analysis-services/multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md)  
  
  
