---
title: "SQL Server Profiler の実行 |Microsoft ドキュメント"
ms.custom: 
ms.date: 7/7/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: sql-server-profiler
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Profiler [SQL Server Profiler], starting
- SQL Server Profiler, starting
- starting SQL Server Profiler
- Profiler [SQL Server Profiler], running
- SQL Server Profiler, running
- running SQL Server Profiler
ms.assetid: 22e57ffa-63b0-4de3-b92e-df297dda1226
caps.latest.revision: "25"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: f9327a1cdb70be829701fa0710f5833545f8a0d2
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="run-sql-server-profiler"></a>SQL Server Profiler の実行
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]実行することができます[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]、さまざまな方法でのトレースの収集をサポートするために出力をさまざまなシナリオでします。 開始することができます[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]、Windows 10 から**開始**] メニューの [から、**ツール**メニューの[!INCLUDE[ssDE](../../includes/ssde-md.md)]チューニング アドバイザーと複数の場所から[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]です。  
  
初めて起動すると[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]選択**新しいトレース**から、**ファイル**メニューで、アプリケーションが表示されます、**サーバーへの接続**を指定する ダイアログ ボックス、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスに接続します。  
## <a name="to-start-sql-server-profiler-from-the-windows-10-start-menu"></a>Windows 10 の [スタート] メニューから SQL Server Profiler を起動するには  
-  [Windows] をクリックして**開始**アイコンまたはキーを押して、Windows キーおよび"SQL Server Profiler 17"の入力を開始します。 ときに、 **SQL Server Profiler 17**にタイルが表示されたら、 をクリックします。   

## <a name="to-start-sql-server-profiler-in-database-engine-tuning-advisor"></a>データベース エンジン チューニング アドバイザーで SQL Server Profiler を起動するには  
-  [!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーで、 **[ツール]** メニューの **[SQL Server Profiler]**をクリックします。  

## <a name="to-start-sql-server-profiler-in-sql-server-management-studio"></a>SQL Server Management Studio での SQL Server Profiler を起動するには  
 開始する[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]で複数の場所から[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]です。 ときに[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]開始されると、接続コンテキスト、トレース テンプレート、およびその起動ポイントのフィルター コンテキストが読み込まれます。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]独自のインスタンスで各 SQL Server Profiler セッションを開始し、プロファイラーをシャット ダウンする場合に実行する[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]です。  
### <a name="to-start-sql-server-profiler-from-the-tools-menu"></a>[ツール] メニューから SQL Server Profiler を起動するには  
-  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **チューニング アドバイザーの** メニューの **[SQL Server Profiler]**から起動することもできます。  

### <a name="to-start-sql-server-profiler-from-the-query-editor"></a>クエリ エディターから SQL Server Profiler を起動するには  
- クエリ エディター内で右クリックし、 **[SQL Server Profiler でクエリをトレース]**を選択します。  

  > [!NOTE]  
  >  接続コンテキストはエディター接続、トレース テンプレートは TSQL_SPs、適用されているフィルターは SPID = query window SPID です。  
    
### <a name="to-start-sql-server-profiler-from-activity-monitor"></a>利用状況モニターから SQL Server Profiler を起動するには  
- 利用状況モニターをクリックして、**プロセス** ウィンドウで、をクリックし、プロファイルするプロセスを右クリックして**SQL Server Profiler のトレース プロセス**です。  

    > [!NOTE]  
    >  プロセスを選択したときに、利用状況モニターが開いていた場合、接続コンテキストはオブジェクト エクスプローラー接続になります。 トレース テンプレートはサーバーの種類に応じた既定値になります。SPID は、選択されたプロセスの SPID と等しくなります。  
    
## <a name="net-framework-security"></a>.NET Framework のセキュリティ  
- Windows 認証モードで、実行するユーザー アカウント[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]のインスタンスに接続する権限が必要[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
- [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] でトレースを実行するには、ユーザーが ALTER TRACE 権限も持っている必要があります。  

## <a name="next-steps"></a>次の手順  
 [SQL Server Profiler の概要](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [SQL Server Management Studio の使用 [SQL Server]](http://msdn.microsoft.com/library/f289e978-14ca-46ef-9e61-e1fe5fd593be)  
