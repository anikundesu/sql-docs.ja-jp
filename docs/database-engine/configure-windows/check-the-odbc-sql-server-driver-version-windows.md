---
title: "ODBC SQL Server のドライバーのバージョンを確認する方法 (Windows) | Microsoft Docs"
ms.custom: 
ms.date: 11/07/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- driver version number [ODBC]
- ODBC drivers, version number
ms.assetid: 43451080-a562-4231-b1d4-1ba35ca0ea79
caps.latest.revision: "23"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: afe647fd866e396cdf418824281b9f6cfbc49de1
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="check-the-odbc-sql-server-driver-version-windows"></a>ODBC SQL Server のドライバーのバージョンを確認する方法 (Windows)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  コンピューターによっては、[!INCLUDE[msCoName](../../includes/msconame-md.md)] や他社製のさまざまな ODBC ドライバーが組み込まれています。 このトピックでは、Windows の **ODBC データ ソース アドミニストレーター** を使用して、インストールされている ODBC ドライバーのバージョンを確認する方法について説明します。  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-check-the-odbc-sql-server-driver-version-32-bit-odbc"></a>ODBC SQL Server のドライバーのバージョンを確認するには (32 ビット ODBC)  
  
-   **ODBC データ ソース アドミニストレーター**で **[ドライバー]** タブをクリックします。  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [バージョン] **列に、Microsoft** エントリの情報が表示されます。  


> [!NOTE]  
>  SQL Database の Azure Active Directory 認証への接続には、 [ODBC Driver 13.1 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53339)などの最新ドライバーをインストールします。   

  
## <a name="see-also"></a>参照  
 [ODBC データ ソース アドミニストレーターの起動](../../database-engine/configure-windows/open-the-odbc-data-source-administrator.md)  
  
  
