---
title: "暗号化されたバックアップの作成 | Microsoft Docs"
ms.custom: 
ms.date: 08/04/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: backup-restore
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e29061d3-c2ab-4d98-b9be-8e90a11d17fe
caps.latest.revision: "17"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: c9dc51c3288ceae6e91cd014b1220ea890d3114f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="create-an-encrypted-backup"></a>暗号化されたバックアップの作成
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] このトピックでは、暗号化されたバックアップを Transact-SQL で作成するために必要な手順について説明します。  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]の使用例については、「 [データベースの完全バックアップの作成 (SQL Server)](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)」を参照してください。 
  
## <a name="backup-to-disk-with-encryption"></a>暗号化の使用によるディスクへのバックアップ  
 **前提条件:**  
  
-   データベースのバックアップを作成するための空き領域が十分にあるローカル ディスクまたはストレージへのアクセス。  
  
-   master データベースのデータベース マスター キー、SQL Server インスタンスで使用可能な証明書または非対称キー。 暗号化の要件と権限については、「 [バックアップの暗号化](../../relational-databases/backup-restore/backup-encryption.md)」を参照してください。  
  
 データベースの暗号化されたバックアップをローカル ディスクに作成するには、次の手順を実行します。 この例では、MyTestDB というユーザー データベースを使用します。  
  
1.  **master データベースのデータベース マスター キーの作成:** データベースに格納されるマスター キーのコピーを暗号化するためのパスワードを選択します。 データベース エンジンに接続して新しいクエリ ウィンドウを開き、次の例をコピーして貼り付け、 **[実行]**をクリックします。  
  
    ```  
    -- Creates a database master key.   
    -- The key is encrypted using the password "<master key password>"  
    USE master;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<master key password>';  
    GO  
  
    ```  
  
2.  **バックアップ証明書の作成:** master データベースに、バックアップ証明書を作成します。 次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。  
  
    ```  
    Use Master  
    GO  
    CREATE CERTIFICATE MyTestDBBackupEncryptCert  
       WITH SUBJECT = 'MyTestDB Backup Encryption Certificate';  
    GO  
  
    ```  
  
3.  **データベースのバックアップ:** 使用する暗号化アルゴリズムと証明書を指定します。 次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。  
  
    ```  
    BACKUP DATABASE [MyTestDB]  
    TO DISK = N'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\MyTestDB.bak'  
    WITH  
      COMPRESSION,  
      ENCRYPTION   
       (  
       ALGORITHM = AES_256,  
       SERVER CERTIFICATE = MyTestDBBackupEncryptCert  
       ),  
      STATS = 10  
    GO  
  
    ```  
  
 EKM で保護されているバックアップの暗号化の例については、「[Azure Key Vault を使用する拡張キー管理 &#40;SQL Server&#41;](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)」を参照してください。  
  
### <a name="backup-to-windows-azure-storage-with-encryption"></a>暗号化の使用による Windows Azure ストレージへのバックアップ  
 **[SQL Server Backup to URL]** オプションを使用して Windows Azure ストレージへのバックアップを作成する場合、暗号化の手順は同じですが、バックアップ先として URL を使用し、Windows Azure ストレージへの認証用に SQL 資格情報を指定する必要があります。 暗号化のオプションを使用して [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] を構成する場合は、「 [Microsoft Azure への SQL Server マネージ バックアップを有効にする](../../relational-databases/backup-restore/enable-sql-server-managed-backup-to-microsoft-azure.md)」を参照してください。  
  
 **前提条件:**  
  
-   Windows ストレージ アカウントとコンテナー。 詳細については、以下を参照してください。 [レッスン 1: Windows Azure ストレージ オブジェクトの作成](http://msdn.microsoft.com/library/74edd1fd-ab00-46f7-9e29-7ba3f1a446c5)。  
  
-   master データベースのデータベース マスター キー、SQL Server インスタンス上の証明書または非対称キー。 暗号化の要件と権限については、「 [バックアップの暗号化](../../relational-databases/backup-restore/backup-encryption.md)」を参照してください。  
  
1.  **SQL Server 資格情報の作成:** SQL Server 資格情報を作成するには、データベース エンジンに接続して新しいクエリ ウィンドウを開き、次の例をコピーして貼り付け、 **[実行]**をクリックします。  
  
    ```  
    CREATE CREDENTIAL mycredential   
    WITH IDENTITY= 'mystorageaccount' – this is the name of the storage account you specified when creating a storage account    
    , SECRET = '<storage account access key>' – this should be either the Primary or Secondary Access Key for the storage account  
    ```  
  
2.  **データベース マスター キーの作成:** データベースに格納されるマスター キーのコピーを暗号化するためのパスワードを選択します。 データベース エンジンに接続して新しいクエリ ウィンドウを開き、次の例をコピーして貼り付け、 **[実行]**をクリックします。  
  
    ```  
    -- Creates a database master key.  
    -- The key is encrypted using the password "<master key password>"  
    USE Master;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<master key password>';  
    GO  
  
    ```  
  
3.  **バックアップ証明書の作成:** master データベースに、バックアップ証明書を作成します。 次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。  
  
    ```  
    USE Master;  
    GO  
    CREATE CERTIFICATE MyTestDBBackupEncryptCert  
       WITH SUBJECT = 'MyTestDBBackupEncryptCert ';  
    GO  
  
    ```  
  
4.  **データベースのバックアップ:** 使用する暗号化アルゴリズムと証明書を指定します。 次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。  
  
    ```  
    BACKUP DATABASE [MyTestDB]  
    TO URL = N'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\MyTestDB.bak'  
    WITH  
      CREDENTIAL 'mycredential' – this is the name of the credential created in the first step.  
      ,COMPRESSION  
      ,ENCRYPTION   
       (  
       ALGORITHM = AES_256,  
       SERVER CERTIFICATE = MyTestDBBackupEncryptCert  
       ),  
      STATS = 10  
    GO  
  
    ```  
  
  
