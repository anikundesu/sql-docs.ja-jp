---
title: MSSQLSERVER_3181 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 3181 (Database Engine error)
ms.assetid: e6d2e716-5263-477c-ad0e-7bcbfef4c1f3
caps.latest.revision: "13"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 928fe1db4bf164e80b765c9b77dc3fefe3517b5d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver3181"></a>MSSQLSERVER_3181
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|イベント ID|3181|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|LDDB_STORAGE_VERIFY|  
|メッセージ テキスト|このバックアップの復元を試みるとストレージ領域に問題が発生する可能性があります。 詳細については、この後のメッセージを参照してください。|  
  
## <a name="explanation"></a>説明  
RESTORE VERIFYONLY ステートメントでは、データベースの復元先ディスクの利用可能なストレージ領域がチェックされます。  
  
### <a name="possible-causes"></a>考えられる原因  
使用可能なディスク領域が不十分なため、確認中のバックアップを復元できない可能性があります。  
  
## <a name="user-action"></a>ユーザーの操作  
十分なディスク領域があるドライブにバックアップを復元するか、ディスク領域を増やします。  
  
## <a name="see-also"></a>参照  
[データベースを新しい場所に復元する &#40;SQL Server&#41;](~/relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)  
[新しい場所へのファイルの復元 &#40;SQL Server&#41;](~/relational-databases/backup-restore/restore-files-to-a-new-location-sql-server.md)  
[RESTORE &#40;Transact-SQL&#41;](~/t-sql/statements/restore-statements-transact-sql.md)  
[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](~/t-sql/statements/restore-statements-verifyonly-transact-sql.md)  
  
