---
title: "SQL Server のリソース正常性のトラブルシューティング (SQL Server ユーティリティ) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: maintenance-plans
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 614f07b5-f221-4013-9f8d-22964cf42270
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: eb7cb98417cf8eaf78647f4a52fd984be6c338d3
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="troubleshoot-sql-server-resource-health-sql-server-utility"></a>SQL Server のリソース正常性のトラブルシューティング (SQL Server ユーティリティ)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UCP によって特定されるリソース正常性の問題のトラブルシューティングでは、コンピューターや [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスでの CPU の過大使用を緩和したり、データ層アプリケーションの CPU の過大使用を緩和したりします。 この他にも、データベース ファイルのファイル領域の過大使用や記憶域ボリュームに割り当てられたディスク領域の過大使用の解決も行われます。  
  
 データベースが "緊急" 状態になっている場合、正常性状態は過大使用になっているログ ファイル領域を示します。  
  
 データ収集の失敗 (UCP のマネージ インスタンスのリスト ビューに灰色の状態アイコンで示されます) の詳細については、「 [SQL Server ユーティリティのトラブルシューティング](http://msdn.microsoft.com/library/f5f47c2a-38ea-40f8-9767-9bc138d14453)」を参照してください。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティの概要の詳細については、「 [SQL Server ユーティリティの機能とタスク](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)」を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UCP で検出された特定のリソースの正常性に関する問題を緩和する方法の詳細については、以下のトピックを参照してください。  
  
-   [SQL Server のバージョンとエディションを識別する方法](http://go.microsoft.com/fwlink/?LinkID=178504)  
  
-   [SQL Server 2008 のパフォーマンスに関する問題のトラブルシューティング](http://go.microsoft.com/fwlink/?LinkId=151354)  
  
  
