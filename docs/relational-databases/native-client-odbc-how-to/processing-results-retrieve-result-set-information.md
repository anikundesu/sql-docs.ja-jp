---
title: "結果セットの情報 (ODBC) の取得 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-how-to
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC]
- result sets [ODBC], fetching
ms.assetid: 34f235e4-f80b-4123-8764-9deb18506f14
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bd99d4fe84bf7ceb09b90d19dd5ec12b26c272c9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="processing-results---retrieve-result-set-information"></a>結果の処理結果セットの情報の取得
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

    
### <a name="to-get-information-about-a-result-set"></a>結果セットに関する情報を取得するには  
  
1.  呼び出す[SQLNumResultCols](../../relational-databases/native-client-odbc-api/sqlnumresultcols.md)を結果セットの列の数を取得します。  
  
2.  結果セット内の各列に対して次の操作を行います。  
  
    -   呼び出す[SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md)結果列に関する情報を取得します。  
  
     または  
  
    -   呼び出す[SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md)結果列に関する具体的な記述子情報を取得します。  
  
## <a name="see-also"></a>参照  
[プロセスの結果 &#40; ODBC &#41;](../../relational-databases/native-client-odbc-how-to/processing-results-process-results.md)

[特性の結果セット &#40; ODBC &#41; を決定します。](../../relational-databases/native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
  
