---
title: "SQLRemoveDefaultDataSource 関数 |Microsoft ドキュメント"
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
apiname: SQLRemoveDefaultDataSource
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLRemoveDefaultDataSource
helpviewer_keywords: SQLRemoveDefaultDataSource function [ODBC]
ms.assetid: db803266-57df-4864-a41b-901247549c1f
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d8b1e368c3ed09b0cc99de6b324a02546e04803e
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sqlremovedefaultdatasource-function"></a>SQLRemoveDefaultDataSource 関数
**準拠**  
 バージョンが導入されています。 ODBC 1.0 では、非推奨  
  
 **概要**  
 ODBC 3.0 では、 **SQLRemoveDefaultDataSource**関数が呼び出しによって置き換えられました[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)で、*起こり*ODBC_REMOVE_DEFAULT_DSN の引数。 場合、ODBC 2*.x*インストール プログラムは、この関数を呼び出し、ODBC のインストーラーを使用すると、次にマップする**SQLConfigDataSource**呼び出し。  
  
```  
SQLConfigDataSource (NULL, ODBC_REMOVE_DEFAULT_DSN, NULL, NULL)  
```
