---
title: "SQL ステートメントが、ユーザーが入力した |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user-entered SQL statements [ODBC]
- SQL statements [ODBC], constructing
- SQL statements [ODBC], entered by user
ms.assetid: 109af162-93ba-425a-8fe5-49c7dc7cc784
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 91ae086fd7be4222c55a8fad9b8383846cc59949
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sql-statements-entered-by-the-user"></a>ユーザーが入力した SQL ステートメント
また、一般アド ホック分析を実行するアプリケーションでは、SQL ステートメントを直接入力するユーザーを許可します。 例:  
  
```  
SQLCHAR *     Statement, SqlState[6], Msg[SQL_MAX_MESSAGE_LENGTH];  
SQLSMALLINT   i, MsgLen;  
SQLINTEGER    NativeError;  
SQLRETURN     rc1, rc2;  
  
// Prompt user for SQL statement.  
GetSQLStatement(Statement);  
  
// Execute the statement directly. Because it will be executed only once,  
// do not prepare it.  
rc1 = SQLExecDirect(hstmt, Statement, SQL_NTS);  
  
// Process any errors or returned information.  
if ((rc1 == SQL_ERROR) || rc1 == SQL_SUCCESS_WITH_INFO) {  
   i = 1;  
   while ((rc2 = SQLGetDiagRec(SQL_HANDLE_STMT, hstmt, i, SqlState, &NativeError,  
         Msg, sizeof(Msg), &MsgLen)) != SQL_NO_DATA) {  
      DisplayError(SqlState, NativeError, Msg, MsgLen);  
      i++;  
   }  
}  
```  
  
 この手法では、アプリケーションのコーディング; 簡略化します。アプリケーションには、SQL ステートメントを作成して、ステートメントの有効性を確認するデータ ソースが依存しています。 十分に複雑な SQL を公開するグラフィカル ユーザー インターフェイスの作成が困難になっているため、SQL ステートメントのテキストを入力するユーザーに依頼するだけと、望ましい代替可能性があります。 ただし、SQL だけでなく、クエリ対象データ ソースのスキーマを知っているユーザーが必要です。 一部のアプリケーションでは、ユーザー基本的な SQL ステートメントを作成し、また使用する、ユーザーが変更できるテキスト インターフェイスを提供するのグラフィカル ユーザー インターフェイスを提供します。
