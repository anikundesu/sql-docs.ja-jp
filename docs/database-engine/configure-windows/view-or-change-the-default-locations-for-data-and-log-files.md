---
title: "データ ファイルとログ ファイルの既定の場所の表示または変更 | Microsoft Docs"
ms.custom: 
ms.date: 06/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- log files [SQL Server], changing default location
- data files [SQL Server], changing default location
ms.assetid: 70a57fda-fcfe-490f-9cf6-5df620e32b2a
caps.latest.revision: "16"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 27d43adce0dbcae948cd725d265e808495c22fcf
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="view-or-change-the-default-locations-for-data-and-log-files"></a>データ ファイルとログ ファイルの既定の場所の表示または変更
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
 データ ファイルとログ ファイルを保護するために、それらがアクセス制御リスト (ACL) によって保護されていることを確認します。 ACL は、ファイルを作成するディレクトリのルートに設定します。  
 
  
## <a name="view-or-change-the-default-locations-for-database-files"></a>データベース ファイルの既定の場所を表示または変更する  
  
1.  オブジェクト エクスプローラーで、サーバーを右クリックして **[プロパティ]**をクリックします。  
  
2.  その [プロパティ] ページの左側のパネルで、 **[データベースの設定]** タブをクリックします。  
  
3.  **[データベースの既定の場所]**パネルに、新しいデータ ファイルと新しいログ ファイルの現在の既定の場所が表示されます。 既定の場所を変更するには、 **[データ]** フィールドまたは **[ログ]** フィールドに新しい既定のパス名を入力するか、参照ボタンをクリックしてパス名を選択します。  
  
>**注:** 既定の場所を変更したら、SQLServer サービスをいったん停止してから再起動して変更を完了する必要があります。  
  
## <a name="see-also"></a>参照  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [データベースの作成](../../relational-databases/databases/create-a-database.md)  
  
  
