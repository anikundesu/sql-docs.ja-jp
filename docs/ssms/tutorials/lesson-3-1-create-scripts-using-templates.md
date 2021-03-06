---
title: "テンプレートを使用したスクリプトの作成 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-tutorial
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
ms.assetid: ed48014c-3fc9-48ff-8c0f-8d1822195f14
caps.latest.revision: "28"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 41b8e42e5af6b1fbdd5a094ba4df63938e2dea21
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="lesson-3-1---create-scripts-using-templates"></a>レッスン 3-1 - テンプレートを使用したスクリプトの作成
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] には、一般のさまざまな作業に適した [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントがスクリプト テンプレートとして多数用意されています。 これらのテンプレートには、テーブル名などのようなユーザーの入力した値に対応するパラメーターが含まれています。 これらのパラメーターを使用して名前を一度入力すると、その名前は、スクリプト内の必要なすべての場所に自動的にコピーされます。 独自のカスタム テンプレートを作成し、頻繁に記述するスクリプトに役立てることができます。 さらに、テンプレートの移動、またはテンプレートを保存する新規フォルダーの作成を行い、テンプレート ツリーを整理できます。 次の実習では、照合テンプレートを指定しつつ、テンプレートを使用してデータベースを作成します。  
  
## <a name="using-templates"></a>テンプレートの使用  
  
#### <a name="to-create-a-script-using-a-template"></a>テンプレートを使用してスクリプトを作成するには  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]で、 **[表示]** メニューの **[テンプレート エクスプローラー]**をクリックします。  
  
2.  テンプレート エクスプローラーではテンプレートがグループ別に表示されます。 **[Database]**を展開し、 **[Create Database]**をダブルクリックします。  
  
3.  **[データベース エンジンへの接続]** ダイアログ ボックスで接続情報を指定し、 **[接続]**をクリックします。 新しいクエリ エディター ウィンドウが開き、 **Create Database** テンプレートの内容が表示されます。  
  
4.  **[クエリ]** メニューの **[テンプレート パラメーターの値の指定]**をクリックします。  
  
5.  **[テンプレート パラメーターの値の指定]** ダイアログ ボックスの **[値]** 列には、 **Database_Name** パラメーターの推奨値が表示されます。 **Database Name** パラメーターの [値] 列のボックスに「 **Marketing**」と入力し、**[OK]** をクリックします。 スクリプトの複数の場所に "Marketing" が挿入されていることを確認します。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[カスタム テンプレートの作成](../../tools/sql-server-management-studio/lesson-3-2-create-custom-templates.md)  
  
  
  
