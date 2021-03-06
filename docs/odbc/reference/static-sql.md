---
title: "静的 SQL |Microsoft ドキュメント"
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
- static SQL [ODBC]
- SQL [ODBC], embedded SQL
- SQL statements [ODBC], embedded SQL
- SQL statements [ODBC], static SQL
- embedded SQL [ODBC]
- SQL [ODBC], static SQL
ms.assetid: 667d92ec-fed9-4028-81d4-bb9ba867356a
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6175fc0e363d336e9baf2eed2faa82b5954828a1
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="static-sql"></a>静的 SQL
表示される埋め込み SQL [Embedded SQL 例](../../odbc/reference/embedded-sql-example.md)静的 SQL と呼ばれます。 プログラムでの SQL ステートメントは静的にするために、静的 SQL を呼び出されますつまり、プログラムを実行するたびに、変更しないでください。 前のセクションで説明した、プログラムの残りの部分はコンパイル時にこれらのステートメントがコンパイルされます。  
  
 静的な SQL はさまざまな状況に適しています、プログラムのデザイン時に、データ アクセスを決定できる任意のアプリケーションで使用できます。 たとえば、受注プログラムが常に同じステートメントを使用して、新しい注文を挿入し、航空券予約システムが常に同じステートメントを使ってから予約に使用可能な接続クライアント ライセンスの状態を変更します。 ホストの変数を使用して一般化するとこれらの各ステートメント別の販売注文の値を挿入することができ、異なる座席を予約することができます。 このようなステートメントは、プログラムにハードコーディングすることができますため、このようなプログラムのステートメントが解析、検証し、コンパイル時に 1 回だけは、最適化する必要があるという利点もあります。 これは、比較的高速のコードになります。
