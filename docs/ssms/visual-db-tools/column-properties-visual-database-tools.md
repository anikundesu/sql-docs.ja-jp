---
title: "[列のプロパティ] (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vdt.designers.properties.Column.ColumnIdentitySpec
- vdt.designers.properties.Column
- vdt.tablecolumn
- vdt.designers.properties.Column.ColumnComputedColumnSpec
- vdt.designers.properties.Column.ColumnFulltextSpec
ms.assetid: e549a2a8-4154-4ec8-b146-614564169b39
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: dfd26bcff6aa621967ab9295ac65a92718db9f8c
ms.lasthandoff: 04/11/2017

---
# <a name="column-properties-visual-database-tools"></a>[列のプロパティ] (Visual Database Tools)
列のプロパティのセットには、テーブル デザイナーの **[列のプロパティ]** タブに表示される完全なセット ([!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] データベースでのみ使用可能) と、サーバー エクスプローラーで [プロパティ] ウィンドウに表示されるサブセットの 2 種類があります。  
  
> [!NOTE]  
> このトピックでは、プロパティを五十音順ではなくカテゴリ別に示しています。  
  
> [!NOTE]  
> 使用中の設定やエディションに応じて、表示されるダイアログ ボックスとメニュー コマンドがヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** を選択してください。  
  
## <a name="properties-window"></a>[プロパティ] ウィンドウ  
サーバー エクスプローラーで列を選択したとき、次のプロパティが [プロパティ] ウィンドウに表示されます。  
  
> [!NOTE]  
> これらのプロパティは読み取り専用であり、サーバー エクスプローラーを使用してアクセスできます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] データベースの列プロパティを編集するには、テーブル デザイナーで列を選択します。 そのプロパティについては、後でこのトピックの中で説明します。  
  
**[IDENTITY] カテゴリ**  
展開すると、 **[オブジェクト名]** プロパティと **[データベース]** プロパティが表示されます。  
  
**[オブジェクト名]**  
列の名前が表示されます。  
  
**[データベース]**  
選択した列のデータ ソースの名前が表示されます (OLE DB にのみ適用)。  
  
**[その他] カテゴリ**  
展開すると、その他のプロパティが表示されます。  
  
**データ型**  
選択した列のデータ型が表示されます。 詳細については、「 [データ型 (Transact-SQL)](http://msdn.microsoft.com/en-us/a54f7373-b247-4d61-8fb8-7f2ec7a8d0a4)」を参照してください。  
  
**[IDENTITY インクリメント]**  
ID 列の以降の各行で **[IDENTITY シード]** に追加される増分値が表示されます ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]にのみ適用されます)。  
  
**[IDENTITY シード]**  
テーブル内で ID 列の最初の行に割り当てられるシード値が表示されます ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]にのみ適用されます)。  
  
**[[Is Identity]]**  
選択されている列がテーブルの ID 列であるかどうかを示します。 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]にのみ適用されます)。  
  
**長さ**  
文字ベースのデータ型で許容される文字数が表示されます。  
  
**[可]**  
列で NULL が許容されるかどうかが表示されます。  
  
**有効桁数**  
数値データ型で許容される最大桁数が表示されます。 数値データ型でないデータ型の場合、このプロパティには **0** と表示されます。  
  
**Scale**  
数値データ型の小数点の右側にある桁数の最大数が表示されます。 この値は、有効桁数以下である必要があります。 数値データ型でないデータ型の場合、このプロパティには **0** と表示されます。  
  
## <a name="column-properties-tab"></a>[列のプロパティ] タブ  
これらのプロパティにアクセスするには、サーバー エクスプローラーで列が属しているテーブルを右クリックした後、 **[テーブル定義を開く]**を選択し、テーブル デザイナーの [テーブル] グリッドで行を選択します。  
  
> [!NOTE]  
> これらのプロパティは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]のみに適用されます。  
  
**[全般] カテゴリ**  
展開すると、 **[オブジェクト名]**、 **[Null を許容]**、 **[データ型]**、 **[既定値またはバインド]**、 **[長さ]**、 **[有効桁数]**、 **[小数点以下桁数]**が表示されます。  
  
**[オブジェクト名]**  
列の名前が表示されます。 名前を編集するには、テキスト ボックスに入力します。  
  
> [!CAUTION]  
> 既存のクエリ、ビュー、ユーザー定義関数、ストアド プロシージャ、またはプログラムからこの列を参照している場合、列の名前を変更すると、そのオブジェクトが無効になります。  
  
**[Null を許容]**  
列のデータ型で NULL が許容されるかどうかが表示されます。  
  
**データ型**  
選択した列のデータ型が表示されます。 このプロパティを編集するには、値をクリックしてドロップダウン リストを展開し、別の値を選択します。 詳細については、「 [データ型 (Transact-SQL)](http://msdn.microsoft.com/en-us/a54f7373-b247-4d61-8fb8-7f2ec7a8d0a4)」を参照してください。  
  
**[既定値またはバインド]**  
列に値が指定されていない場合の、列の既定値が表示されます。 このドロップダウン リストに、データ ソースで定義されているグローバル既定値がすべて表示されます。 列にグローバル既定値をバインドする場合は、ドロップダウン リストから選択します。 列に既定の制約を作成する場合は、既定値をテキストとして直接入力します。  
  
**[長さ]**  
文字ベースのデータ型で許容される文字数が表示されます。 このプロパティは、文字に基づくデータ型にのみ使用できます。  
  
**有効桁数**  
数値データ型で許容される最大桁数が表示されます。 数値データ型でないデータ型の場合、このプロパティには **0** と表示されます。 このプロパティは、数値のデータ型にのみ使用できます。  
  
**Scale**  
数値データ型の小数点の右側にある桁数の最大数が表示されます。 この値は、有効桁数以下である必要があります。 数値データ型でないデータ型の場合、このプロパティには **0** と表示されます。 このプロパティは、数値のデータ型にのみ使用できます。  
  
**[テーブル デザイナー] カテゴリ**  
展開すると、その他のプロパティが表示されます。  
  
**[照合順序]**  
選択した列における照合順序の設定が表示されます。 この設定を変更するには、 **[照合順序]** をクリックした後、値の右側にある **[...]** をクリックします  
  
**[計算列の指定] カテゴリ**  
展開すると、 **[式]** と **[永続化されている]**のプロパティが表示されます。 列が計算列である場合、式も表示されます。 式を編集するには、このカテゴリを展開して、 **[式]** プロパティで式を編集します。  
  
**[式]**  
選択した列が計算列の場合に、列で使用される式が表示されます。 このフィールドで式を入力したり、変更したりできます。  
  
**[永続化されている]**  
データ ソースを使用して計算列を保存できます。 保存された計算列にインデックスを作成できます。  
  
**[圧縮データ型]**  
フィールドのデータ型に関する情報が表示されます。SQL の CREATE TABLE ステートメントと同じ形式で表示されます。 たとえば、最大 20 文字の可変長文字列を含むフィールドは "varchar(20)" と表示されます。 このプロパティを変更するには、値を直接入力します。  
  
**Description**  
列の説明が表示されます。 完全な説明を表示したり、説明を表示したりするには、[説明] をクリックして、プロパティの右側にある **[...]** をクリックします。  
  
**[フルテキストの指定] カテゴリ**  
展開すると、フルテキスト列に関するプロパティが表示されます。  
  
**[[Is Full-text Indexed]]**  
この列にフルテキスト インデックスが作成されているかどうかが示されます。 この列のデータ型がフルテキスト検索に対応している場合、およびこの列が属するテーブルにフルテキスト インデックスが指定されている場合にのみ、このプロパティを **[はい]** に設定できます。 この値を編集するには、値をクリックしてドロップダウン リストを展開し、新しい値を選択します。  
  
**[フルテキスト型列]**  
image 型の列のドキュメントの種類を定義するために使用される列が表示されます。 image データ型を使用して、.doc ファイルや XML ファイルなどのさまざまなドキュメントを保存できます  
  
**言語**  
列のインデックス作成に使用される言語を指定します  
  
**[統計的セマンティクス]**  
選択されている列に対する統計的セマンティック インデックスを有効にするかどうかを選択します。 詳細については、 [セマンティック検索のプレースホルダー](http://msdn.microsoft.com/en-us/cd8faa9d-07db-420d-93f4-a2ea7c974b97)に関する記述を参照してください。  
  
**[統計的セマンティクス]** を選択する前に **[言語]**を選択した場合、選択した言語にセマンティック言語モデルが関連付けられていなければ、 **[統計的セマンティクス]** オプションは **[いいえ]** に設定され、変更できません。 **[言語]** を選択する前に **[統計的セマンティクス]** オプションで **[はい]**を選択した場合、 **[言語]** 列で使用できる言語は、セマンティック言語モデルでサポートされているものだけに制限されます。  
  
**[SQL Server 以外のサブスクライバーがある]**  
列に Microsoft SQL Server 以外のサブスクライバーが含まれているかどうかが表示されます  
  
**[IDENTITY の指定] カテゴリ**  
展開すると、 **[ID]**、 **[ID の増分値]**、 **[IDENTITY シード]**のプロパティが表示されます。  
  
**[[Is Identity]]**  
選択されている列がテーブルの ID 列であるかどうかを示します。 プロパティを変更するには、テーブル デザイナーでテーブルを開き、 **[プロパティ]** ウィンドウでプロパティを編集します。 この設定は、 *int*などの数値に基づくデータ型の列にのみ適用されます。  
  
**[IDENTITY インクリメント]**  
以降の各行で **[IDENTITY シード]** に追加される増分値が表示されます。 このセルを空白にすると、既定により値が 1 に設定されます。 このプロパティを編集するには、値を直接入力します。  
  
**[IDENTITY シード]**  
テーブルの最初の行に割り当てられる値が表示されます。 このセルを空白にすると、既定により値が 1 に設定されます。 このプロパティを編集するには、値を直接入力します。  
  
**[Deterministic]**  
選択した列のデータ型を明確に決定できるかどうかが表示されます  
  
**[DTS-published]**  
列が SSIS によりパブリッシュされているかどうかが表示されます  
  
**[Indexable]**  
選択した列にインデックスを作成できるかどうかが表示されます。 たとえば、不明確な計算列にはインデックスを作成できません。  
  
**[Merge-published]**  
列がマージによりパブリッシュされているかどうかが表示されます。  
  
**[Not For Replication]**  
レプリケーション時に元の ID 値を保持するかどうかを示します。 このプロパティを編集するには、値をクリックしてドロップダウン リストを展開し、別の値を選択します。  
  
**[Replicated]**  
この列を別の場所にレプリケートされるかどうかを示します。  
  
**[RowGuid]**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] でこの列が ROWGUID として使用されるかどうかが示されます。 データ型が **uniqueidentifier** の列でのみ、この値を **[はい]**に設定できます。 このプロパティを編集するには、値をクリックしてドロップダウン リストを展開し、別の値を選択します。  
  
**サイズ**  
列のデータ型で許容されるサイズがバイト単位で表示されます。 たとえば、 **nchar** データ型の長さが 10 (文字数) でも、Unicode 文字セットの場合のサイズは 20 になります。  
  
> [!NOTE]  
> **varchar(max)** データ型の長さは行ごとに異なります。 sp_help を実行すると、 **varchar(max)** 列の長さとして (-1) が返されます。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio_md.md)] では、列のサイズとして -1 が表示されます。  
  
