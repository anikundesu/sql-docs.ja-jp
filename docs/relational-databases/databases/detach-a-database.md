---
title: "データベースのデタッチ | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: databases
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.detachdatabase.f1
helpviewer_keywords:
- database detaching [SQL Server]
- detaching databases [SQL Server]
ms.assetid: f63d4107-13e4-4bfe-922d-5e4f712e472d
caps.latest.revision: "36"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: c31efc7e44be9eec0e50300911eaf5590d5f8199
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="detach-a-database"></a>データベースのデタッチ
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] このトピックでは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のデータベースをデタッチする方法について説明します。 デタッチされたファイルはそのまま残り、FOR ATTACH または FOR ATTACH_REBUILD_LOG オプションを指定した CREATE DATABASE によって再アタッチできます。 ファイルを別のサーバーに移動し、そこにアタッチすることもできます。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [セキュリティ](#Security)  
  
-   **データベースをデタッチする方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
 制限事項と制約事項の一覧については、「 [データベースのデタッチとアタッチ &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)のデータベースをデタッチする方法について説明します。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> アクセス許可  
 db_owner 固定データベース ロールのメンバーシップが必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-detach-a-database"></a>データベースをデタッチするには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] オブジェクト エクスプローラーで、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続して、そのインスタンスを展開します。  
  
2.  **[データベース]**を展開し、デタッチするユーザー データベースの名前を選択します。  
  
3.  データベース名を右クリックして **[タスク]**をポイントし、 **[デタッチ]**をクリックします。 **[データベースのデタッチ]** ダイアログ ボックスが表示されます。  
  
     **[デタッチするデータベース]**  
     デタッチするデータベースを一覧表示します。  
  
     **Database Name**  
     デタッチするデータベースの名前を表示します。  
  
     **[接続の削除]**  
     指定したデータベースへの接続を切断します。  
  
    > [!NOTE]  
    >  アクティブな接続があるデータベースをデタッチすることはできません。  
  
     **統計の更新**  
     既定では、データベースをデタッチしても、古い最適化統計情報が保持されます。既存の最適化統計情報を更新するには、このチェック ボックスをオンにします。  
  
     **[フルテキスト カタログの保持]**  
     既定では、デタッチ操作を行っても、データベースに関連付けられたフルテキスト カタログが保持されます。 これらのカタログを削除するには、 **[フルテキスト カタログの保持]** チェック ボックスをオフにします。 このオプションは、データベースを [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]からアップグレードする場合にのみ表示されます。  
  
     **[状態]**  
     **[準備完了]** または **[準備ができていません]**のどちらかの状態を表示します。  
  
     **メッセージ**  
     **[メッセージ]** 列に、次のようにデータベースに関する情報が表示される場合があります。  
  
    -   データベースがレプリケーションに含まれている場合、 **[状態]** は **[準備ができていません]** になり、 **[メッセージ]** 列に **[データベースがレプリケートされました]**と表示されます。  
  
    -   データベースにアクティブな接続が 1 つ以上ある場合、**[状態]** は **[準備ができていません]** になり、**[メッセージ]** 列に [*<number_of_active_connections>* **のアクティブな接続]** (例: **[1 のアクティブな接続]**) と表示されます。 データベースをデタッチするには、 **[接続の削除]**を選択してアクティブな接続を切断する必要があります。  
  
     メッセージについてより詳しい情報を得るには、ハイパーリンクのテキストをクリックして利用状況モニターを開きます。  
  
4.  データベースをデタッチする準備ができたら、 **[OK]**をクリックします。  
  
> [!NOTE]  
>  新たにデタッチしたデータベースは、表示を最新の情報に更新するまで、オブジェクト エクスプローラーの **[データベース]** ノード内に表示されたままです。 表示の更新はいつでも実行できます。表示を更新するには、[オブジェクト エクスプローラー] ペインをクリックし、 **[表示]** メニューの **[最新の情報に更新]**をクリックします。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-detach-a-database"></a>データベースをデタッチするには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。 この例では、skipchecks を true に設定して、AdventureWorks2012 データベースをデタッチします。  
  
```  
EXEC sp_detach_db 'AdventureWorks2012', 'true';  
```  
  
## <a name="see-also"></a>参照  
 [データベースのデタッチとアタッチ &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [sp_detach_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)  
  
  
