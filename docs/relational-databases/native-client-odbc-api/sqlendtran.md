---
title: "SQLEndTran |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords: SQLEndTran function
ms.assetid: 95cff841-c2d5-4e1e-a18d-f3d4696a5b85
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0ae667a2fa572a12a8b00fc68a87faa676027c5b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sqlendtran"></a>SQLEndTran
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーはステートメントの関連付けられたカーソルを閉じるときに**SQLEndTran**がコミットまたはロールバック操作します。 サーバー カーソルは、静的カーソルでない限り、閉じられます。 ときに**SQLEndTran**がコミットまたはロールバック操作、ステートメントの関連付けられたカーソルの動作はによって設定ドライバー固有のODBC接続属性SQL_COPT_SS_PRESERVE_CURSORSの値によって決まります[SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)です。  
  
## <a name="see-also"></a>参照  
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [SQLEndTran 関数](http://go.microsoft.com/fwlink/?LinkId=59342)  
  
  
