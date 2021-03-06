---
title: "記述子の解放 |Microsoft ドキュメント"
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
- SQLFreeHandle function [ODBC]
- descriptors [ODBC], allocating and freeing
- freeing descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 317213f4-0ebb-4bf8-a37a-4d6b1313823f
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f951b69af4ecc18dc1dcdc23d0cbd1ce115caf0b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="freeing-descriptors"></a>記述子の解放
明示的に割り当てられた記述子は、いずれかを呼び出すことによって、明示的に解放**SQLFreeHandle**で*HandleType* SQL_HANDLE_DESC、または暗黙的にすると、接続ハンドルが解放されます。 明示的に割り当てられた記述子が解放されるときに、それらを暗黙的に割り当てられた記述子を元に戻す、解放された記述子を自動的に適用されるすべてのステートメント ハンドルです。  
  
 暗黙的に割り当てられた記述子を呼び出すことによってのみ解放できる**SQLDisconnect**、すべてのステートメントを破棄する記述子を接続またはまたは呼び出すことによって**SQLFreeHandle**で、 *HandleType* SQL_HANDLE_STMT ステートメント ハンドルと、ステートメントに関連付けられているすべての暗黙的に割り当てられた記述子を解放するのです。 暗黙的に割り当てられた記述子を呼び出すことによって解放できない**SQLFreeHandle**で、 *HandleType* SQL_HANDLE_DESC のです。  
  
 暗黙的に割り当てられた記述子は有効、解放されると場合でも、 **SQLGetDescField**そのフィールドで呼び出すことができます。
