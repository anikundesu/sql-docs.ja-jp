---
title: "SQLInstallTranslator 関数 |Microsoft ドキュメント"
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
apiname: SQLInstallTranslator
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLInstallTranslator
helpviewer_keywords: SQLInstallTranslator function [ODBC]
ms.assetid: 453b21ff-3c2b-4069-8ff7-5c727f062d89
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ef9452b9ff442ec5ed40b7eb38957936d31d16b5
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sqlinstalltranslator-function"></a>SQLInstallTranslator 関数
**準拠**  
 バージョンが導入されています。 ODBC 2.5、非推奨  
  
 **概要**  
 ODBC 3.0 **SQLInstallTranslator**代わりました[SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)です。 呼び出す**SQLInstallTranslator**にマップされます**SQLInstallTranslatorEx**です。 詳細については、次を参照してください。 **SQLInstallTranslatorEx**です。  
  
 **SQLInstallTranslator**アプリケーションでは、それを呼び出す ODBC 3 の場合は FALSE を返します*.x*ドライバー マネージャーで、 *lpszInfFile*引数が NULL 以外の値に設定します。 ODBC 2 で使用される Odbc.inf ファイルです。*x* ODBC 3 ではサポートされなく*.x*旧バージョンとの互換性のためにあっても、します。
