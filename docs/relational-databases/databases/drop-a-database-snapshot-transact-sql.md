---
title: "データベース スナップショットの削除 (Transact-SQL) | Microsoft Docs"
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
helpviewer_keywords:
- removing database snapshots
- deleting database snapshots
- database snapshots [SQL Server], deleting
ms.assetid: ad70ec97-d5fb-41aa-b72a-915e74b61b76
caps.latest.revision: "36"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 2a86dbd8133febc11c103a97515fe486a79726de
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="drop-a-database-snapshot-transact-sql"></a>データベース スナップショットの削除 (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] データベース スナップショットを削除すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からデータベース スナップショットが削除され、そのスナップショットで使用されていたスパース ファイルが削除されます。 データベース スナップショットを削除すると、そのデータベース スナップショットに対するすべてのユーザー接続が終了します。  
  
## <a name="security"></a>セキュリティ  
  
###  <a name="Permissions"></a> アクセス許可  
 DROP DATABASE 権限を持つすべてのユーザーが、データベース スナップショットを削除できます。  
  
##  <a name="TsqlProcedure"></a> データベース スナップショットを削除する方法 (Transact-SQL の使用)  
 **データベース スナップショットを削除するには**  
  
1.  削除するデータベース スナップショットを特定します。 データベース内のスナップショットは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で参照できます。 詳細については、「 [データベース スナップショットの表示 &#40;SQL Server&#41;](../../relational-databases/databases/view-a-database-snapshot-sql-server.md)で参照できます。  
  
2.  削除するデータベース スナップショットの名前を指定して [DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md) ステートメントを実行します。 構文は次のとおりです。  
  
     DROP DATABASE *database_snapshot_name* [ **,**...*n* ]  
  
     ここで、 *database_snapshot_name* は、削除するデータベース スナップショットの名前です。  
  
####  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 この例では、データベース スナップショット SalesSnapshot0600 を削除します。これは元のデータベースには影響しません。  
  
```  
DROP DATABASE SalesSnapshot0600 ;  
```  
  
 SalesSnapshot0600 へのユーザー接続がすべて終了し、スナップショットで使用される NTFS ファイル システムのスパース ファイルがすべて削除されます。  
  
> [!NOTE]  
>  データベース スナップショットによるスパース ファイルの使用の詳細については、「 [データベース スナップショット &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md)で参照できます。  
  
##  <a name="RelatedTasks"></a> 関連タスク  
  
-   [データベース スナップショットの作成 &#40;Transact-SQL&#41;](../../relational-databases/databases/create-a-database-snapshot-transact-sql.md)  
  
-   [データベース スナップショットの表示 &#40;SQL Server&#41;](../../relational-databases/databases/view-a-database-snapshot-sql-server.md)  
  
-   [データベースをデータベース スナップショットに戻す](../../relational-databases/databases/revert-a-database-to-a-database-snapshot.md)  
  
  
## <a name="see-also"></a>参照  
 [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md)   
 [データベース スナップショット &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md)  
  
  
