---
title: "レッスン 3: URL へのデータベースのバックアップ | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: tutorial
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
ms.assetid: a9ae1501-b614-49d3-b975-6569da8350b2
caps.latest.revision: "16"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: f63e84d8c22b5c88214cc4d85a6bebf572c41430
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="lesson-3-database-backup-to-url"></a>レッスン 3: URL へのデータベースのバックアップ
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] このレッスンでは、「[レッスン 1: Azure コンテナーに格納済みアクセス ポリシーと Shared Access Signature を作成する](../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md)」で作成した Azure コンテナーに、オンプレミスの SQL Server 2016 インスタンス内の AdventureWorks2014 データベースをバックアップします。  
  
> [!NOTE]  
> この Azure コンテナーに SQL Server 2012 SP1 CU2 以降のデータベースまたは SQL Server 2014 データベースをバックアップする場合、 [こちら](https://technet.microsoft.com/en-US/library/dn435916(v=sql.120).aspx) に記載されている非推奨構文を使用すれば、WITH CREDENTIAL 構文で URL へのバックアップを行うことができます。  
  
BLOB ストレージにデータベースをバックアップするには、次の手順に従います。  
  
1.  SQL Server Management Studio に接続します。  
  
2.  新しいクエリ ウィンドウを開き、Azure 仮想マシン内にあるデータベース エンジンの SQL Server 2016 インスタンスに接続します。  
  
3.  次の Transact-SQL スクリプトをコピーしてクエリ ウィンドウに貼り付けます。 レッスン 1 で指定したコンテナーとストレージ アカウント名に合わせて適宜 URL を変更し、次のスクリプトを実行します。  
  
    ```  
  
    -- To permit log backups, before the full database backup, modify the database to use the full recovery model.  
    USE master;  
    ALTER DATABASE AdventureWorks2014  
       SET RECOVERY FULL;  
  
    -- Back up the full AdventureWorks2014 database to the container that you created in Lesson 1  
    BACKUP DATABASE AdventureWorks2014   
       TO URL = 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/AdventureWorks2014_onprem.bak'  
  
    ```  
  
4.  オブジェクト エクスプローラーを開き、ストレージ アカウントとアカウント キーを使用して Azure ストレージに接続します。  
  
5.  コンテナーの展開。レッスン 1 で作成されたコンテナーを展開し、前述の手順 3 で作成されたバックアップがこのコンテナー内に表示されているかどうかを確認します。  
  
    ![オンプレミスのバックアップ ファイルが Azure コンテナーに blob として表示される](../relational-databases/media/0d060e51-012f-4c61-ab8d-16d461d0ffad.JPG "オンプレミスのバックアップ ファイルが Azure コンテナーに blob として表示される")  
  
**次のレッスン:**  
  
[レッスン 4: URL から仮想マシンにデータベースを復元する](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)  
  
