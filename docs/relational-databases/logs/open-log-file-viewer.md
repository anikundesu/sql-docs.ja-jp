---
title: "[ログ ファイルの表示] を開く | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: logs
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Log File Viewer, opening
ms.assetid: a86b89cb-0432-4648-895a-05ecc5450e45
caps.latest.revision: "29"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 58798cfeb515819c081be5fe24261209d96f18fb
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="open-log-file-viewer"></a>[ログ ファイルの表示] を開く
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の [ログ ファイルの表示] を使用すると、次のログに記録されたエラーおよびイベントに関する情報にアクセスできます。  
  
-   監査コレクション  
  
-   データ コレクション  
  
-   データベース メール  
  
-   ジョブ履歴  
  
-   SQL Server  
  
-   SQL Server エージェント  
  
-   Windows イベント (イベント ビューアーからもアクセス可能)  
  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]以降では、登録済みサーバーを使用して、ローカルまたはリモートの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログ ファイルを表示できます。 登録済みサーバーを使用すると、インスタンスがオンラインでもオフラインでも、ログ ファイルを表示できます。 オンライン アクセスの詳細については、このトピックで後述する「登録済みサーバーからオンラインのログ ファイルを参照するには」の手順を参照してください。 オフラインの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログ ファイルへのアクセス方法の詳細については、「 [オフライン ログ ファイルの表示](../../relational-databases/logs/view-offline-log-files.md)」を参照してください。  
  
 [ログ ファイルの表示] は、表示する情報に応じていくつかの方法で開くことができます。  
  
##  <a name="BeforeYouBegin"></a> 権限  
 オンラインの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスのログ ファイルにアクセスするには、securityadmin 固定サーバー ロールのメンバーシップが必要です。  
  
 オフラインの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスのログ ファイルにアクセスするには、 **Root\Microsoft\SqlServer\ComputerManagement10** WMI 名前空間、およびログ ファイルの保存されているフォルダーの両方に対する読み取りアクセス権が必要です。 詳細については、「 [オフライン ログ ファイルの表示](../../relational-databases/logs/view-offline-log-files.md)」トピックの「セキュリティ」セクションを参照してください。  
  
### <a name="security"></a>セキュリティ  
 securityadmin 固定サーバー ロールのメンバーシップが必要です。  
  
### <a name="view-log-files"></a>ログ ファイルの表示  
  
##### <a name="to-view-logs-that-are-related-to-general-sql-server-activity"></a>SQL Server の一般的な動作に関連するログを表示するには  
  
1.  オブジェクト エクスプローラーで、 **[管理]**を展開します。  
  
2.  以下のいずれかを実行します。  
  
    -   **[SQL Server ログ]**を右クリックし、 **[表示]**をポイントして、 **[SQL Server ログ]** または **[SQL Server および Windows ログ]**をクリックします。  
  
    -   **[SQL Server ログ]**を展開し、任意のログ ファイルを右クリックして **[SQL Server ログの表示]**をクリックします。 任意のログ ファイルをダブルクリックすることもできます。  
  
     ログには、 **データベース メール**、 **SQL Server**、 **SQL Server エージェント**、および **Windows NT**が含まれます。  
  
##### <a name="to-view-logs-that-are-related-to-jobs"></a>ジョブに関連するログを表示するには  
  
-   オブジェクト エクスプローラーで **[SQL Server エージェント]**を展開し、 **[ジョブ]**を右クリックして **[履歴の表示]**をクリックします。  
  
     ログには、 **データベース メール**、 **ジョブ履歴**、および **SQL Server エージェント**が含まれます。  
  
##### <a name="to-view-logs-that-are-related-to-maintenance-plans"></a>メンテナンス プランに関連するログを表示するには  
  
-   オブジェクト エクスプローラーで **[管理]**を展開し、 **[メンテナンス プラン]**を右クリックして **[履歴の表示]**をクリックします。  
  
     ログには、 **データベース メール**、 **ジョブ履歴**、 **メンテナンス プラン**、 **リモート メンテナンス プラン**、および **SQL Server エージェント**が含まれます。  
  
##### <a name="to-view-logs-that-are-related-to-data-collection"></a>データ コレクションに関連するログを表示するには  
  
-   オブジェクト エクスプローラーで **[管理]**を展開し、 **[データ コレクション]**を右クリックして **[ログの表示]**をクリックします。  
  
     ログには、 **データ コレクション**、 **ジョブ履歴**、および **SQL Server エージェント**が含まれます。  
  
##### <a name="to-view-logs-that-are-related-to-database-mail"></a>データベース メールに関連するログを表示するには  
  
-   オブジェクト エクスプローラーで、 **[管理]**を展開し、 **[データベース メール]**を右クリックし、 **[データベース メール ログの表示]**をクリックします。  
  
     ログには、 **データベース メール、ジョブ履歴**、 **メンテナンス プラン**、 **リモート メンテナンス プラン**、 **SQL Server**、 **SQL Server エージェント**、および **Windows NT**が含まれます。  
  
##### <a name="to-view-logs-that-are-related-to-audits-collections"></a>監査コレクションに関連するログを表示するには  
  
-   オブジェクト エクスプローラーで、 **[セキュリティ]**、 **[監査]**の順に展開し、監査を右クリックして **[監査ログの表示]**をクリックします。  
  
     ログには、 **監査コレクション** と **Windows NT**が含まれます。  
  
##### <a name="to-view-logs-that-are-related-to-audits-collections"></a>監査コレクションに関連するログを表示するには  
  
-   オブジェクト エクスプローラーで、 **[セキュリティ]**、 **[監査]**の順に展開し、監査を右クリックして **[監査ログの表示]**をクリックします。  
  
     ログには、 **監査コレクション** と **Windows NT**が含まれます。  
  
## <a name="see-also"></a>参照  
 [ログ ファイルの表示](../../relational-databases/logs/log-file-viewer.md)   
 [SQL Server Audit &#40;データベース エンジン&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)   
 [オフライン ログ ファイルの表示](../../relational-databases/logs/view-offline-log-files.md)  
  
  
