---
title: "手順 6 : 参照変換の追加と構成 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: tutorial
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: 5c59f723-9707-4407-80ae-f05f483cf65f
caps.latest.revision: "38"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: aa364a063138708cfa48bea87abe7f0833d07575
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="lesson-1-6---adding-and-configuring-the-lookup-transformations"></a>レッスン 1-6 - 参照変換の追加と構成
ソース ファイルからデータを取り出すフラット ファイルを構成したら、次は、 **CurrencyKey** および **DateKey**の値を取得する際に必要な参照変換を定義します。 参照変換は、指定の入力列のデータを参照データセットの列に結合することにより、参照を実行します。 参照データセットは、既存のテーブル、既存のビュー、新しいテーブル、または SQL ステートメントの結果のいずれかになります。 このチュートリアルでは、参照変換は、OLE DB 接続マネージャーを使用して、参照データセットのソースとなるデータを含むデータベースに接続します。  
  
> [!NOTE]  
> 参照データセットを含むキャッシュに接続するように参照変換を構成することもできます。 詳細については、「 [Lookup Transformation](../integration-services/data-flow/transformations/lookup-transformation.md)」を参照してください。  
  
このチュートリアルでは、次の 2 つの参照変換コンポーネントをパッケージに追加し、構成します。  
  
-   **DimCurrency** ディメンションの **CurrencyKey** 列から取得される値を参照する変換コンポーネント。 **CurrencyID** 列の値と一致する値をフラット ファイルから探します。  
  
-   **DimDate** ディメンションの **DateKey** 列から取得される値を参照する変換コンポーネント。 **CurrencyDate** 列の値と一致する値をフラット ファイルから探します。  
  
どちらの場合も、以前に作成した OLE DB 接続マネージャーを使用します。  
  
### <a name="to-add-and-configure-the-lookup-currency-key-transformation"></a>Lookup Currency Key 変換を追加および構成するには  
  
1.  **[SSIS ツールボックス]**で **[共通]**を展開し、 **[参照]** を **[データ フロー]** タブのデザイン画面にドラッグします。[参照] を **[Extract Sample Currency Data]** ソースのすぐ下に置きます。  
  
2.  **[Extract Sample Currency Data]** フラット ファイル ソースをクリックします。次に、緑色の矢印を、新しく追加した **[参照]** 変換までドラッグして、これら 2 つのコンポーネントを接続します。  
  
3.  **[データ フロー]** デザイン画面で、 **[参照]** 変換の **[参照]** をクリックし、名前を「 **Lookup Currency Key**」に変更します。  
  
4.  **Lookup Currency Key** 変換をダブルクリックし、参照変換エディターを表示します。  
  
5.  **[全般]** ページで、以下の選択を行います。  
  
    1.  **[フル キャッシュ]**を選択します。  
  
    2.  **[接続の種類]** 領域で、 **[OLE DB 接続マネージャー]**を選択します。  
  
6.  **[接続]** ページで、以下の選択を行います。  
  
    1.  **[OLE DB 接続マネージャー]** ダイアログ ボックスに、 **localhost.AdventureWorksDW2012** が表示されていることを確認します。  
  
    2.  **[SQL クエリの結果を使用する]**をクリックし、次の SQL ステートメントを入力するかコピーします。  
  
        ```sql
        select * from (select * from [dbo].[DimCurrency]) as refTable  
        where [refTable].[CurrencyAlternateKey] = 'ARS'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'AUD'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'BRL'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'CAD'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'CNY'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'DEM'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'EUR'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'FRF'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'GBP'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'JPY'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'MXN'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'SAR'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'USD'  
        OR  
        [refTable].[CurrencyAlternateKey] = 'VEB'  
        ```  
  
7.  **[列]** ページで、以下の選択を行います。  
  
    1.  **[使用できる入力列]** パネルの **[CurrencyID]** を **[使用できる参照列]** パネルにドラッグし、 **[CurrencyAlternateKey]**の上にドロップします。  
  
    2.  **[使用できる参照列]** ボックスの一覧で、 **[CurrencyKey]**の左側のチェック ボックスをオンにします。  
  
8.  **[OK]** をクリックして、 **[データ フロー]** デザイン画面に戻ります。  
  
9. [Lookup Currency Key] 変換を右クリックし、 **[プロパティ]**をクリックします。  
  
10. [プロパティ] ウィンドウで、 **LocaleID** プロパティが **[英語 (米国)]** に、 **[DefaultCodePage]** プロパティが **[1252]**に設定されていることを確認します。  
  
### <a name="to-add-and-configure-the--lookup-datekey-transformation"></a>Lookup Date Key 変換を追加および構成するには  
  
1.  **[SSIS ツールボックス]**で **[参照]** をクリックし、 **[データ フロー]** デザイン画面上にドラッグします。 [参照] を **[Lookup Currency Key]** のすぐ下に配置します。  
  
2.  **[Lookup Currency Key]** 変換をクリックします。緑色の矢印を、新しく追加した **[参照]** 変換までドラッグして、これら 2 つのコンポーネントを接続します。  
  
3.  **[入出力の選択]** ダイアログ ボックスの **[出力]** ボックスの一覧で **[参照の一致出力]** をクリックし、 **[OK]**をクリックします。  
  
4.  **[データ フロー]** デザイン画面で、新しく追加した **[参照]** 変換の **[参照]** をクリックし、名前を「 **Lookup Date Key**」に変更します。  
  
5.  **[Lookup Date Key]** 変換をダブルクリックします。  
  
6.  **[全般]** ページで、 **[部分キャッシュ]**を選択します。  
  
7.  **[接続]** ページで、以下の選択を行います。  
  
    1.  **[OLEDB 接続マネージャー]** ダイアログ ボックスに、 **localhost.AdventureWorksDW2012** が表示されていることを確認します。  
  
    2.  **[テーブルまたはビューを使用]** ボックスで、 **[dbo].[DimDate]**を選択するか、または入力します。  
  
8.  **[列]** ページで、以下の選択を行います。  
  
    1.  **[使用できる入力列]** パネルの **[CurrencyDate]** を **[使用できる参照列]** パネルにドラッグし、 **[FullDateAlternateKey]**の上にドロップします。  
  
    2.  **[使用できる参照列]** ボックスの一覧で、 **[DateKey]**の左側のチェック ボックスをオンにします。  
  
9. **[詳細設定]** ページで、キャッシュ オプションを確認します。  
  
10. **[OK]** をクリックして、**[データ フロー]** デザイン画面に戻ります。  
  
11. [Lookup Date Key] 変換を右クリックし、 **[プロパティ]**をクリックします。  
  
12. [プロパティ] ウィンドウで、 **LocaleID** プロパティが **[英語 (米国)]** に、 **[DefaultCodePage]** プロパティが **[1252]**に設定されていることを確認します。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[手順 7 : OLE DB 変換先の追加と構成](../integration-services/lesson-1-7-adding-and-configuring-the-ole-db-destination.md)  
  
## <a name="see-also"></a>参照  
[Lookup Transformation](../integration-services/data-flow/transformations/lookup-transformation.md)  
  
  
  
