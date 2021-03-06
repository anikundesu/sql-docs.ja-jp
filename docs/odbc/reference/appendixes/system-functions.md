---
title: "システム関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- system functions [ODBC]
- functions [ODBC], system functions
ms.assetid: 36614b4c-e037-43ef-8692-67f4861b144d
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 79cbe8677ba4401fb779dc9765d639b1d86a0f5f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="system-functions"></a>システム関数
次の表は、ODBC スカラー関数のセットに含まれているシステム関数を一覧表示します。 呼び出して**SQLGetInfo**で、*情報の種類*するシステム関数は、ドライバーでサポートされる SQL_SYSTEM_FUNCTIONS のアプリケーションを決定できます。  
  
 として表される引数*exp* SQL_NUMERIC SQL_DECIMAL、SQL_TINYINT、SQL_SMALLINT、SQL_INTEGER SQL として基になるデータ型を表すことができます、列、他のスカラー関数、または、リテラルの結果の名前を指定できます_BIGINT、使用できます、SQL_REAL、SQL_DOUBLE、SQL_TYPE_DATE、SQL_TYPE_TIME、および sql_type_timestamp 型。  
  
 として表される引数*値*SQL_NUMERIC、SQL_DECIMAL、SQL_TINYINT、SQL_SMALLINT、SQL_INTEGER、SQL_BIGINT、使用できます、SQL_REAL、SQL_DOUBLE、sql _ 基になるデータ型を表すことがリテラルの定数であることができますTYPE_DATE、SQL_TYPE_TIME、および sql_type_timestamp 型。  
  
 返される値は、ODBC データ型として表されます。  
  
|機能|Description|  
|--------------|-----------------|  
|**データベースに関するページ ()** (ODBC 1.0)|接続ハンドルに対応するデータベースの名前を返します。 (を呼び出して、データベースの名前が使用可能なも**SQLGetConnectOption** SQL_CURRENT_QUALIFIER 接続オプションを使用します)。|  
|**見つかれば (** *exp*、*値***)** (ODBC 1.0)|場合*exp*が null、*値*が返されます。 場合*exp*が null でない*exp*が返されます。 考えられるデータ型または型の*値*のデータ型と互換性のある必要があります*exp*です。|  
|**ユーザー ()** (ODBC 1.0)|DBMS のユーザー名を返します。 (ユーザー名がによって使用可能なも**SQLGetInfo**情報の種類を指定することによって: SQL_USER_NAME)。これは、ログイン名とは異なることができます。|
