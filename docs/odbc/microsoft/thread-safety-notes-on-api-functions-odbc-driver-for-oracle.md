---
title: "API 関数 (ODBC Driver for Oracle) にスレッド セーフの注意事項 |Microsoft ドキュメント"
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
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], threading
- threading options [ODBC]
- multiple concurrent statements [ODBC]
ms.assetid: f0c9bdfd-f79d-4088-9ecb-afcd8ca7fb73
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6037a11f71d5fc6af4d9f173974fc91c80833fc0
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="thread-safety-notes-on-api-functions-odbc-driver-for-oracle"></a>API 関数 (ODBC Driver for Oracle) にスレッド セーフの注意事項
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 Microsoft ODBC Driver for Oracle はスレッド セーフです。ただし、Oracle では、単一の接続で複数の同時実行ステートメントは使用はできません。 ドライバーは、この制限を強制します。 つまり、マルチ スレッド アプリケーションで、任意のスレッドがいつでも for Oracle ODBC ドライバーに呼び出すことができますが、ドライバー ブロックが同じ接続で、ドライバーから他のスレッド、元のスレッドが、ドライバーを離れるまでします。  
  
 ドライバーは、次の 2 つの異なる接続で 2 つのステートメントがある場合にブロックされません。 ただし、2 つのステートメントで 1 つの接続がある場合はブロックが発生する可能性です。
