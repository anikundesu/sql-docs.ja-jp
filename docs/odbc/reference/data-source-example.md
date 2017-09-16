---
title: "データ ソースの使用例 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data sources [ODBC], examples
ms.assetid: cbf15f32-0550-4c74-8088-8f7ac3855469
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 85eae404d4fa0ab739c699c8f120c76122c8ba67
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="data-source-example"></a>データ ソースの例
Microsoft® Windows NT® Server または Windows 2000 Server、Microsoft Windows NT ワークステーション/Windows 2000 Professional、または Microsoft Windows® 95/98、マシンのデータを実行するコンピューターでは、ソース情報がレジストリに格納されます。 によっては、レジストリ キーの情報に格納されている、データ ソースと呼ばれます、*ユーザー データ ソース*または*システム データ ソース*です。 ユーザー データ ソースは、HKEY_CURRENT_USER キーには保存され、現在のユーザーにのみ提供されます。 システム データ ソースは、HKEY_LOCAL_MACHINE キーに格納され、1 台のコンピューターの 1 つ以上のユーザーによって使用されることができます。 また、システム全体のサービスは、アクセスできるように、データ ソースに、マシンにログオンしているユーザーがいない場合でもによっても使用できます。 ユーザーおよびシステム データ ソースの詳細については、次を参照してください。 [SQLManageDataSources](../../odbc/reference/syntax/sqlmanagedatasources.md)です。  
  
 ユーザーが次の 3 つのユーザー データ ソース: 担当者とインベントリを使用して Oracle データベース管理システムです。および給与支払いは、Microsoft SQL Server データベース管理システムを使用します。 データ ソースのレジストリ値があります。  
  
```  
HKEY_CURRENT_USER  
SOFTWARE  
          ODBC  
               Odbc.ini  
                    ODBC Data Sources  
                    Personnel : REG_SZ : Oracle  
                    Inventory : REG_SZ : Oracle  
                    Payroll : REG_SZ : SQL Server  
```  
  
 および給与データ ソースのレジストリ値があります。  
  
```  
HKEY_CURRENT_USER  
     SOFTWARE  
          ODBC  
               Odbc.ini  
                    Payroll  
                         Driver : REG_SZ : C:\WINDOWS\SYSTEM\Sqlsrvr.dll  
                         Description : REG_SZ : Payroll database  
                         Server : REG_SZ : PYRLL1  
                         FastConnectOption : REG_SZ : No                          UseProcForPrepare : REG_SZ : Yes  
                         OEMTOANSI : REG_SZ : No  
                         LastUser : REG_SZ : smithjo  
                         Database : REG_SZ : Payroll  
                         Language : REG_SZ :  
```