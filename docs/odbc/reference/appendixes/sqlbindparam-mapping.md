---
title: "SQLBindParam マッピング |Microsoft ドキュメント"
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
- SQLBindparam function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLBindParam
ms.assetid: 375f8f24-36de-4946-916e-c75abc6f070d
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 14af02864d6e0810ffa6ffa49a35bf676c000aea
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sqlbindparam-mapping"></a>SQLBindParam マッピング
**SQLBindParam**は本当に呼び出せません推奨されなくなったために存在していたしない odbc; ただし、まだは重複している機能-ドライバー マネージャーは、ISO 準拠しているオープン グループ – アプリケーションが使用されていることをエクスポートする必要があります。 **SQLBindParameter**のすべての機能を含む**SQLBindParam**、 **SQLBindParam**の上にマップされます**SQLBindParameter**(ときに、基になるドライバーは、ODBC 3*.x*ドライバー)。 ODBC 3*.x*ドライバーを実装する必要はありません**SQLBindParam**です。  
  
## <a name="remarks"></a>解説  
 次の呼び出しと**SQLBindParam**が行われます。  
  
```  
SQLBindParam(   StatementHandle,    ParameterNumber,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    StrLen_or_IndPtr)  
```  
  
 ドライバー マネージャー呼び出し**SQLBindParameter**次のように、ドライバーで。  
  
```  
SQLBindParameter(   StatementHandle,    ParameterNumber,    SQL_PARAM_INPUT,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    BufferLength,    StrLen_or_IndPtr)  
```  
  
 参照してください[ODBC 64 ビット情報](../../../odbc/reference/odbc-64-bit-information.md)、64 ビット オペレーティング システム、アプリケーションが実行される場合。  
  
## <a name="see-also"></a>参照  
 [非推奨の関数のマッピング](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)
