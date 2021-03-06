---
title: "[トレース ファイル] |Microsoft ドキュメント"
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
- trace files [ODBC]
- tracing options [ODBC], trace files
ms.assetid: ec97f949-126f-40a2-b67e-e74520a524cb
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 17820a03e062feb24e3b10e58cbcf29b3feb8ba3
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="trace-file"></a>トレース ファイル
アプリケーション ファイルを指定します、トレース設定するか、 **TraceFile**キーワード Odbc.ini レジストリ エントリで、または呼び出すことによって**SQLSetConnectAttr** SQL_ATTR_TRACEFILE 接続属性を持つ。 トレースが有効にすると、ファイルが存在しない場合、ドライバー マネージャーは、ファイルを作成します。 各アプリケーションは、競合を避けるため、独自の専用のトレース ファイルが必要です。 アプリケーションは、複数のトレース ファイルを使用できます。アプリケーションのセットアップ プログラムは、トレース ファイルの選択したユーザーに提供できます。 トレースが動的に有効な場合、アプリケーションも表示できますログではなく、トレース結果トレース ファイルに。  
  
 トレース ファイルは、データ型を持つ各 ODBC 関数呼び出しのログとのすべての引数の値を提供します。 すべての入力関数をログに記録し、リターン コードとエラーの状態を使用して返されるすべての機能を記録します。  
  
 ODBC 3*.x*DLL は、トレース接続関数にパラメーターが指定されていません。
