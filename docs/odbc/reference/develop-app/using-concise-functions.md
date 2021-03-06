---
title: "簡潔な関数の使用 |Microsoft ドキュメント"
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
- concise functions [ODBC]
- functions [ODBC], concise functions
- descriptors [ODBC], concise functions
ms.assetid: 31ac070f-8c59-4fd5-bd5a-466bb27dbca0
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f58efc6ca7f6587ce7d7070bc02ad935efe06bff
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="using-concise-functions"></a>簡潔な関数の使用
一部の ODBC 関数へのアクセス暗黙の型記述子。 アプリケーション ライターがありますに呼び出し元より便利**SQLSetDescField**または**SQLGetDescField**です。 これらの関数を呼び出す*簡潔な*のさまざまな機能、設定、記述子フィールドの取得などを実行するために機能します。 いくつかの簡潔な関数は、1 つの関数の呼び出しで複数の関連する記述子フィールドを取得または設定アプリケーションを使用できます。  
  
 簡潔な関数は、最初の引数として使用する記述子ハンドルを取得することがなく呼び出すことができます。 これらの関数で呼び出されたステートメント ハンドルに関連付けられている記述子フィールドを使用します。  
  
 簡潔な関数**SQLBindCol**と**SQLBindParameter**その引数に対応する記述子フィールドを設定して、列またはパラメーターをバインドします。 これらの各関数は、単に記述子を設定するよりも多くのタスクを実行します。 **SQLBindCol**と**SQLBindParameter**データ列または動的パラメーターのバインドの完全な仕様を提供します。 変えることができます、ただし、バインディングの個別の詳細を呼び出して**SQLSetDescField**または**SQLSetDescRec**し、一連に適切な呼び出しをすることで列またはパラメーターをバインドできる完全にこれらの関数。  
  
 簡潔な関数**SQLColAttribute**、 **SQLDescribeCol**、 **SQLDescribeParam**、 **SQLNumParams**、および**SQLNumResultCols**の記述子フィールドの値を取得します。  
  
 **Sqlsetdescrec による**と**SQLGetDescRec**簡潔な関数は、1 回の呼び出しとデータ型および列またはパラメーターのデータの記憶域に影響する複数の記述子フィールドを取得または設定します。 **SQLSetDescRec**を 1 つのステップ内の列またはパラメーターのデータのバインドを変更する効果的な方法です。  
  
 **SQLSetStmtAttr**と**SQLGetStmtAttr**場合によっては簡潔な関数として機能します。 (を参照してください[記述子フィールド](../../../odbc/reference/develop-app/descriptor-fields.md))。
