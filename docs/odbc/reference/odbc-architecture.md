---
title: "ODBC アーキテクチャ |Microsoft ドキュメント"
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
- ODBC architecture [ODBC], components
- ODBC architecture [ODBC]
ms.assetid: 2604f492-587b-4a51-9876-59a7870b3ef2
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 495a8c03361e7a7bf94ef7c0a403a1894d24836e
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="odbc-architecture"></a>ODBC アーキテクチャ
ODBC アーキテクチャには、4 つのコンポーネントがあります。  
  
-   **アプリケーション**SQL ステートメントを送信し、結果を取得する処理と呼び出しの ODBC 関数を実行します。  
  
-   **ドライバー マネージャー**負荷とアプリケーションに代わってドライバーをアンロードします。 プロセスの ODBC 関数やドライバーに渡します。  
  
-   **ドライバー**プロセス ODBC 関数呼び出し、特定のデータ ソースに対する SQL 要求の送信およびアプリケーションに結果が返されます。 必要に応じて、要求が関連付けられている DBMS によってサポートされている構文に準拠しているように、ドライバー、アプリケーションの要求を変更します。  
  
-   **データ ソース**データから構成されています。 ユーザーがアクセスし、次のように関連付けられているオペレーティング システム、DBMS すると、ネットワーク プラットフォーム (存在する場合)、DBMS にアクセスするために使用します。  
  
 ODBC アーキテクチャには、次の点に注意してください。 これにより、同時に 1 つ以上のデータ ソースからデータにアクセスするアプリケーション最初、複数のドライバー、およびデータ ソースが存在できます。 2 つの場所で ODBC API を使用する第 2 に、: アプリケーションと、ドライバー マネージャー間およびドライバー マネージャーと各ドライバー。 ドライバー マネージャーとドライバーの間のインターフェイスと呼ばれることがあります、*サービス プロバイダー インターフェイス*または*SPI*です。 ODBC では、アプリケーション プログラミング インターフェイス (API) と、サービス プロバイダー インターフェイス (SPI) は同じです。ドライバー マネージャーと各ドライバーは、同じ機能を同じインターフェイスを持っています。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [アプリケーション](../../odbc/reference/applications.md)  
  
-   [ドライバー マネージャー](../../odbc/reference/the-driver-manager.md)  
  
-   [ドライバー](../../odbc/reference/drivers.md)  
  
-   [データ ソース](../../odbc/reference/data-sources.md)
