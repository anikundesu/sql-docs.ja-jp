---
title: "手順 1: レッスン 3 のパッケージのコピー | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
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
ms.assetid: 0d053786-5203-43f3-a613-27a8dd2bc44a
caps.latest.revision: "25"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1e0d051aa94420c8c3aba844f746c88ed9784f4f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="lesson-4-1---copying-the-lesson-3-package"></a>レッスン 4-1 - レッスン 3 のパッケージのコピー
ここでは、レッスン 3 で作成した Lesson 3.dtsx パッケージのコピーを作成します。 レッスン 3 を終了していない場合は、チュートリアルに含まれている、レッスン 3 を完了した状態のパッケージをプロジェクトに追加し、作業用のコピーを作成することもできます。 レッスン 4 の実習では、このパッケージの新しいコピーを使用します。  
  
### <a name="to-create-the-lesson-4-package"></a>レッスン 4 のパッケージを作成するには  
  
1.  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools がまだ開いていない場合は、 **[スタート]**ボタンをクリックし、 **[すべてのプログラム]**、 **[Microsoft SQL Server]**の順にポイントして、 **[SQL Server Data Tools]**をクリックします。  
  
2.  **[ファイル]** メニューの **[開く]**をクリックし、 **[プロジェクト/ソリューション]**をクリックします。次に、 **[SSIS Tutorial]** フォルダーをクリックして **[開く]**をクリックした後、 **SSIS Tutorial.sln**をダブルクリックします。  
  
3.  ソリューション エクスプローラーで、 **Lesson 3.dtsx**を右クリックし、 **[コピー]**をクリックします。  
  
4.  ソリューション エクスプローラーで **[SSIS パッケージ]**を右クリックし、 **[貼り付け]**をクリックします。  
  
    コピーしたパッケージの既定の名前は、Lesson 4.dtsx です。  
  
5.  ソリューション エクスプローラーで **Lesson 4.dtsx** をダブルクリックし、パッケージを開きます。  
  
6.  **[制御フロー]** タブの背景上で任意の場所を右クリックし、 **[プロパティ]**をクリックします。  
  
7.  [プロパティ] ウィンドウで、**[Name]** プロパティを「**Lesson 4**」に変更します。  
  
8.  **[ID]** プロパティのボックスをクリックし、一覧で **[<Generate New ID>]** をクリックします。  
  
### <a name="to-add-the-completed-lesson-3-package"></a>レッスン 3 を完了した状態のパッケージを追加するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] を開いて、SSIS Tutorial プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーで **[SSIS パッケージ]**を右クリックし、 **[既存のパッケージを追加]**をクリックします。  
  
3.  **[既存のパッケージのコピーを追加]** ダイアログ ボックスの **[パッケージの場所]** で、**[ファイル システム]** をクリックします。  
  
4.  参照ボタン ( **[...]** ) をクリックし、コンピューター上の Lesson 3.dtsx に移動して、 **[開く]**をクリックします。  
  
    このチュートリアルのレッスン パッケージをすべてダウンロードするには、次の手順を実行します。  
  
    1.  「[Integration Services 製品サンプル](http://go.microsoft.com/fwlink/?LinkId=275027)」に移動します。  
  
    2.  **[ダウンロード]** タブをクリックします。  
  
    3.  SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip ファイルをクリックします。  
  
5.  前の手順の手順 3 ～ 8 の説明に従って、レッスン 3 のパッケージをコピーして貼り付けます。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[手順 2: 破損ファイルの作成](../integration-services/lesson-4-2-creating-a-corrupted-file.md)  
  
