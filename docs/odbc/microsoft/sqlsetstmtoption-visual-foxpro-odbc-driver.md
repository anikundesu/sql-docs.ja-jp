---
title: "SQLSetStmtOption (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQLSetStmtOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 76b813e3-c7dc-4bb2-a710-d2aa9dcfdc36
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 77cd6f6f8ddd09a011dba2cbbe39c962d78b4574
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sqlsetstmtoption-visual-foxpro-odbc-driver"></a>SQLSetStmtOption (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 サポート: 完全  
  
 レベル 1 の ODBC API への準拠:  
  
 ステートメント ハンドルに関連するオプションを設定*hstmt*です。  
  
|*fOption*|指定できる値|コメント|  
|---------------|--------------------|--------------|  
|SQL_ASYNC_ENABLE|SQL_ASYNC_ENABLE_OFF|これを設定しようとする場合*fOption*ドライバーは、エラーを返します:"非対応 Driver"です。 Visual FoxPro は、非同期実行をサポートしていません。|  
|SQL_BIND_TYPE|SQL_BIND_BY_COLUMN または構造体、または列のバインドされているためにバッファーのインスタンスの長さを示す 32 ビット値。||  
|SQL_CONCURRENCY|SQL_CONCUR_READ_ONLY<br /><br /> SQL_CONCUR_LOCK<br /><br /> SQL_CONCUR_VALUES|Visual FoxPro には、タイムスタンプに基づく行バージョン管理ができないために、ドライバーは、SQL_CONCUR_ROWVER を許可されていません。|  
|SQL_CURSOR_TYPE|SQL_CURSOR_FORWARD_ONLY<br /><br /> SQL_CURSOR_STATIC|ドライバーは許可されません SQL_CURSOR_KEYSET_DRIVEN SQL_CURSOR_DYNAMIC です。参照してください[SQLSetScrollOptions](../../odbc/microsoft/sqlsetscrolloptions-visual-foxpro-odbc-driver.md)詳細についてはします。|  
|SQL_KEYSET_SIZE|エラー:「ドライバー対応していない」|Visual FoxPro は keyset カーソル モデルをサポートしていません。|  
|SQL_MAX_LENGTH|0|これを設定しようとすると*fOption*値、ドライバー エラーが返されます、"非対応 Driver"です。|  
|SQL_MAX_ROWS|0|これを設定しようとすると*fOption*値、ドライバー エラーが返されます、"非対応 Driver"です。|  
|SQL_NOSCAN|SQL_NOSCAN_OFF||  
|SQL_QUERY_TIMEOUT|0|これを設定しようとすると*fOption*値、ドライバー エラーが返されます、"非対応 Driver"です。|  
|SQL_RETRIEVE_DATA|SQL_RD_ON、SQL_RD_OFF||  
|SQL_ROWSET_SIZE|1 に 4,294,967,296||  
|SQL_SIMULATE_CURSOR|エラー:「ドライバー対応していない」||  
|SQL_USE_BOOKMARKS|SQL_UB_OFF<br /><br /> SQL_UB_ON||  
  
 詳細については、次を参照してください。 [SQLSetStmtOption](../../odbc/reference/syntax/sqlsetstmtoption-function.md)で、 *ODBC プログラマ リファレンス*です。
