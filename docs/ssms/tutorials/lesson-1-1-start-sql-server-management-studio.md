---
title: "SQL Server Management Studio の起動 | Microsoft Docs"
ms.custom: 
ms.date: 07/11/2017
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
ms.assetid: 25ffaea6-0eee-4169-8dd0-1da417c28fc6
caps.latest.revision: "45"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 100026baf315404c6b50da48a358e3bfd7200abf
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="lesson-1-1---start-sql-server-management-studio"></a>レッスン 1-1 - SQL Server Management Studio の起動
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] このチュートリアルを開始する前に、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を開いてみましょう。  
  
## <a name="opening-sql-server-management-studio"></a>SQL Server Management Studio を開く  
  
#### <a name="to-open-sql-server-management-studio"></a>SQL Server Management Studio を開くには  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] (SSMS) の起動方法は、使用するオペレーティング システムによって異なります。  
  * **スタート ページ**のある新しいバージョンの Windows の場合、**スタート ページ**で「**[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**」と入力すると、プログラムが表示されます。 プログラムをクリックして、SSMS を開きます。 プログラムを右クリックして、 **スタート ページ**へのピン留めを行うことができます。   
  * 以前のバージョンの Windows では、 **[スタート]** ボタンをクリックし、 **[すべてのプログラム]**、[ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]] の順にポイントして、 **[SQL Server Management Studio]**をクリックします。 あるいは、 **[実行]** ダイアログ ボックスで、「 **SSMS.exe** 」と入力し、 **[OK]**をクリックします。  
  
    > [!NOTE]  
    >  SSMS が表示されない場合は、SSMS が正常にインストールされていない可能性があります。 [ダウンロード センター](../download-sql-server-management-studio-ssms.md)から SSMS をインストールしてください。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 の場合、SSMS は自動的にインストールされません。 すべての機能にアクセスするには、最新バージョンを使用します。  
  
2.  次の手順では、SSMS の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [オブジェクト エクスプローラー] **コンポーネントを使用して、** に接続します。 オブジェクト エクスプローラー ペインが表示されない場合は、 **[表示]** メニューの **[オブジェクト エクスプローラー]**をクリックします。 オブジェクト エクスプローラー メニューで **[接続]** ボタンをクリックし、 **[データベース エンジン]**をクリックします。 **[サーバーへの接続]** ダイアログ ボックスが表示されます (SSMS が事前にインストールされている場合、ユーザー設定によっては **[サーバーへの接続]** ダイアログ ボックスが自動的に表示されることがあります)。  
  
3.  **[サーバーへの接続]** ダイアログ ボックスで、 **[サーバー名]** ボックスに名前を指定します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の 3 つの種類のいずれかに接続できます。 種類ごとに、 **[サーバー名]** ボックスの形式が少し異なります。 次のいずれかの形式を使用します。  
  -  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定のインスタンス:** コンピューターに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をインストールするときは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが既定のインスタンス (名前のないインスタンス) または名前付きインスタンスになるように指定することができます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定のインスタンスに接続する場合は、コンピューターの名前を挿入します。 たとえば、Accounting という名前のコンピューターで SSMS を実行している場合に、そのコンピューターにインストールされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  の既定のインスタンスに接続するには、 **[サーバー名]** ボックスに「 **Accounting** 」と入力します。  
  -  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の名前付きインスタンス:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップ時に、インスタンスの名前を指定できます。たとえば、Accounting という名前のコンピューター上で、**Receivables** という名前の名前付きインスタンスを指定することが可能です。 名前付きインスタンスに接続するには、 **[サーバー名]** ボックスに、コンピューター名、円記号 (\)、インスタンス名の順に入力します。たとえば「 **Accounting\Receivables**」と入力します。  
  -  **Azure SQL Database:** SQL Database のサーバー名の形式は SQL_Server_name.database.windows.net となります。たとえば、 **mydb2.database.windows.net**とすることができます。 サーバー名を決定する際に問題が発生した場合は、Azure ポータルにアクセスして、接続文字列の作成方法を確認してください。  
  
4. **[認証]** 領域で、認証方法を選択します。  
  - コンピューターの管理者であり、SQL Server をインストールしたばかりの場合は、**Windows 認証** を試してください。  SQL Server へのアクセス権を持つドメイン ユーザーとして構成した場合は、この方法も有効です。 このログインの試行では Windows のログインに使用した資格情報を使用するため、**ユーザー名**と**パスワード**の両方のボックスが灰色表示されています。 
  -  ユーザー アカウントの名前とパスワードがわかっている場合は、**SQL Server 認証**を選択し、**ユーザー名**と**パスワード**を指定します。
  - SSMS の最新バージョンをお持ちの場合はさらに、**Active Directory 認証**を始めとする 3 つのオプションがあります。 これらの高度なオプションについては、「[SQL Database と SQL Data Warehouse でのユニバーサル認証 (MFA 対応の SSMS サポート)](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-ssms-mfa-authentication)」をご覧ください。  
  
## <a name="management-studio-components"></a>Management Studio のコンポーネント  
[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] では、情報は種類ごとに専用のウィンドウに表示されます。 データベース情報はオブジェクト エクスプローラーとドキュメント ウィンドウに表示されます。  
  
-   オブジェクト エクスプローラーには、サーバー上のすべてのデータベース オブジェクトがツリー形式で表示されます。 たとえば、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]、および [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]のデータベースが表示されます。 オブジェクト エクスプローラーには、接続しているすべてのサーバーの情報が登録されています。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]を開くと、前回使用した設定にオブジェクト エクスプローラーを接続するかどうかをたずねられます。 [登録済みサーバー] の一覧でサーバーをダブルクリックすると、そのサーバーに接続できますが、接続するサーバーを登録する必要はありません。  
  
-   ドキュメント ウィンドウは、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]の中で最も大きな部分を占めています。 ドキュメント ウィンドウにはクエリ エディターとブラウザー ウィンドウを表示できます。 既定では [概要] ページが表示され、現在のコンピューター上にある [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続されます。  
  
## <a name="showing-additional-windows"></a>その他のウィンドウの表示  
  
#### <a name="to-show-the-registered-servers-window"></a>登録済みサーバー ウィンドウを表示するには  
  
1.  **[表示]** メニューの **[登録済みサーバー]**をクリックします。  
  
    [登録済みサーバー] ウィンドウがオブジェクト エクスプローラーの上または隣に表示されます。 これをドラッグし、さまざまな場所にドッキングすることができます。 登録済みサーバーには、管理頻度の高いサーバーの一覧が表示されます。 この一覧にサーバーを追加したり、一覧からサーバーを削除することができます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているコンピューター上の [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]インスタンスのみが一覧に表示されます。  
  
2.  [登録済みサーバー] にサーバーが表示されない場合は、 **[データベース エンジン]**を右クリックし、 **[タスク]**をクリックし、 **[ローカル サーバーの登録情報を更新]**をクリックします。 その他の SQL Server または SQL Database を追加するには、登録済みサーバーの場所を右クリックし、 **[新規サーバーの登録]**をクリックします。 **[サーバーへの接続]** ダイアログ ボックスの場合と同様に、 **[ログイン]** 領域に必要な情報を入力します。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[登録済みサーバーおよびオブジェクト エクスプローラーを使用した接続](../../tools/sql-server-management-studio/lesson-1-2-connect-with-registered-servers-and-object-explorer.md)  

  
