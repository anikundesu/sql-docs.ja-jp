---
title: "SQLNativeSql (カーソル ライブラリ) |Microsoft ドキュメント"
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
helpviewer_keywords: SQLNativeSql function [ODBC], Cursor Library
ms.assetid: c4459092-1177-4b2a-b7f5-e0083d3bf2b2
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b1541b22f68dabdc5f5425346fe83da7adf2ee83
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sqlnativesql-cursor-library"></a>SQLNativeSql (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックの使用、 **SQLNativeSql**カーソル ライブラリ内の関数。 に関する一般的な情報**SQLNativeSql**を参照してください[SQLNativeSql 関数](../../../odbc/reference/syntax/sqlnativesql-function.md)です。  
  
 ドライバーは、この関数をサポートする場合、カーソル ライブラリを呼び出す**SQLNativeSql**ドライバーで SQL ステートメントを渡します。 位置指定更新は、削除、配置と**更新用に選択**ステートメント、カーソル ライブラリがドライバーに渡す前にステートメントを変更します。  
  
> [!NOTE]  
>  カーソル ライブラリを誤って返します SQLSTATE 34000 (無効なカーソル名) 場合は、カーソル名は、位置指定更新または delete ステートメントに渡されるでは有効ではなく、 *InStatementText*の引数**SQLNativeSql**. **SQLNativeSql**はステートメントの準備または実行時にのみ、返される構文エラーを返すものではありません。
