---
title: "データ ソースの定義 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: 5a3e83c9-8788-431e-85b0-a68c79377ff3
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: c6d92c514cb38f1277efeedaa4172968f8e150ec
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="lesson-1-2---defining-a-data-source"></a>レッスン 1、2、データ ソースを定義します。
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]作成した後、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]プロジェクト、一般に作業を開始するプロジェクトとプロジェクトで使用する 1 つまたは複数のデータ ソースを定義しています。 データ ソースを定義するときは、データ ソースへの接続に使用する接続文字列情報を定義します。 詳細については、「 [データ ソースの作成 &#40;SSAS 多次元&#41;](../analysis-services/multidimensional-models/create-a-data-source-ssas-multidimensional.md)」を参照してください。  
  
次の実習では、AdventureWorksDWSQLServer2012 サンプル データベースを [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial プロジェクトのデータ ソースとして定義します。 チュートリアル用にサンプル データベースはローカル コンピューターに保存されていますが、ソース データベースから 1 つ以上のリモート コンピューターをホストすることもしばしばあります。  
  
### <a name="to-define-a-new-data-source"></a>新しいデータ ソースを定義するには  
  
1.  ソリューション エクスプローラー (Microsoft Visual Studio ウィンドウの右側) で、 **[データ ソース]**を右クリックし、 **[新しいデータ ソース]**をクリックします。  
  
2.  **データ ソース ウィザード** の **[データ ソース ウィザードへようこそ]**ページで、 **[次へ]** をクリックして **[接続の定義方法を選択します]** ページを開きます。  
  
3.  **[接続の定義方法を選択します]** ページでは、新しい接続、既存の接続、または以前に定義したデータ ソース オブジェクトに基づいて、データ ソースを定義できます。 ここでは、新しい接続に基づいてデータ ソースを定義します。 **[既存の接続または新しい接続に基づいてデータ ソースを作成する]** が選択されていることを確認し、 **[新規作成]**をクリックします。  
  
4.  **[接続マネージャー]** ダイアログ ボックスで、データ ソースの接続のプロパティを定義します。 **[プロバイダー]** ボックスの一覧で、 **[ネイティブ OLE DB\SQL Server Native Client 11.0]** が選択されていることを確認します。  
  
    [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] では、 **[プロバイダー]** ボックスの一覧に表示されるその他のプロバイダーもサポートしています。  
  
5.  **[サーバー名]** ボックスに「 **localhost**」と入力します。  
  
    ローカル コンピューター上の名前付きインスタンスに接続する場合は、「 **localhost\\<instance name>**」を参照してください。 ローカル コンピューターではなく指定のコンピューターに接続するには、コンピューター名または IP アドレスを入力します。  
  
6.  **[Windows 認証を使用]** が選択されていることを確認します。 **[データベースの選択または入力]** ボックスの一覧で、 **[AdventureWorksDW2012]**を選択します。  
  
7.  **[接続テスト]** をクリックして、データベースへの接続をテストします。  
  
8.  **[OK]**をクリックし、 **[次へ]**をクリックします。  
  
9. ウィザードの **[権限借用情報]** ページでは、データ ソースへの接続時に使用する [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のセキュリティ資格情報を定義します。 権限借用は、Windows 認証が選択されている場合に、データ ソースへの接続に使用される Windows アカウントに関連する機能です。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] では、OLAP オブジェクトを処理するための権限借用はサポートされていません。 **[サービス アカウントを使用する]**をクリックし、 **[次へ]**をクリックします。  
  
10. **[ウィザードの完了]** ページで、既定の名前である **Adventure Works DW 2012**をそのまま使用して、 **[完了]** をクリックします。新しいデータ ソースが作成されます。  
  
> [!NOTE]  
> 作成後にデータ ソースのプロパティを変更するには、 **[データ ソース]** フォルダー内のデータ ソースをダブルクリックします。 **[データ ソース デザイナー]**にデータ ソースのプロパティが表示されます。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[データ ソース ビューの定義](../analysis-services/lesson-1-3-defining-a-data-source-view.md)  
  
## <a name="see-also"></a>参照  
[データ ソースの作成 &#40;SSAS 多次元&#41;](../analysis-services/multidimensional-models/create-a-data-source-ssas-multidimensional.md)  
  
