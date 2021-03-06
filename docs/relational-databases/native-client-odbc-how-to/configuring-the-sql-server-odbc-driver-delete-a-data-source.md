---
title: "データ ソース (ODBC) の削除 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/01/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-how-to
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: data sources [ODBC]
ms.assetid: 910e3e16-7b91-49d8-80bb-b4243926afaa
caps.latest.revision: "19"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 1d6d68bf462c06213c8f09fab4d30110848bf790
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="configuring-the-sql-server-odbc-driver---delete-a-data-source"></a>SQL Server ODBC ドライバーの削除、データ ソースを構成します。
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降で ODBC アプリケーションを使用する前に、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でカタログ ストアド プロシージャのバージョンをアップグレードする方法や、データ ソースを追加、削除、およびテストする方法を理解しておく必要があります。  
  
  ODBC アドミニストレーターをプログラムでを使用してデータ ソースを削除することができます (を使用して[SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md))、または削除するファイル (ファイル データ ソース名)。  
  
### <a name="to-delete-a-data-source-by-using-odbc-administrator"></a>ODBC アドミニストレーターを使用してデータ ソースを削除するには  
  
1.  **コントロール パネルの **、開かれている**管理ツール**、し、ダブルクリックするか**ODBC データ ソース (64 ビット)**または**ODBC データ ソース (32 ビット)**. コマンド プロンプトから odbcad32.exe を実行することもできます。  
  
2.  クリックして、**ユーザー DSN**、**システム DSN**、または**ファイル DSN**タブです。  
  
3.  削除するデータ ソースを選択します。  
  
4.  をクリックして**削除**、削除を確定します。  
  
## <a name="example"></a>例  
 データ ソースをプログラムで削除するには、呼び出す[SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md) 2 番目のパラメーターとして ODBC_REMOVE_DSN または ODBC_REMOVE_SYS_DSN を使用します。  
  
 次のサンプルでは、データ ソースをプログラムで削除する方法を示しています。  
  
```  
// remove_odbc_data_source.cpp  
// compile with: ODBCCP32.lib user32.lib  
#include <iostream>  
#include \<windows.h>  
#include \<odbcinst.h>  
  
int main() {   
   LPCSTR provider = "SQL Server";   // Windows SQL Server Driver  
   LPCSTR provider = "SQL Server";   // Windows SQL Server driver  
   LPCSTR provider2 = "SQL Server Native Client 11.0";   // SQL Server 2012 Native Client driver  
   LPCSTR dsnname = "DSN=data2";  
   BOOL retval = SQLConfigDataSource(NULL, ODBC_REMOVE_DSN, provider, dsnname);  
   std::cout << retval;   // 1 if successful  
}  
```  
  
## <a name="see-also"></a>参照  
 [追加のデータ ソース &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/configuring-the-sql-server-odbc-driver-add-a-data-source.md)  
  
  
