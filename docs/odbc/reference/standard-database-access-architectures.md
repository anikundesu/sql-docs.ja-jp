---
title: "標準のデータベース アクセス アーキテクチャ |Microsoft ドキュメント"
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
ms.assetid: a9d41800-9068-4b76-895a-32b2853692dd
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2cb4ddb3b51763772b00b7d17691e60109d1d6aa
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="standard-database-access-architectures"></a>標準のデータベース アクセスのアーキテクチャ
前のセクションで説明されているデータベース アクセスのコンポーネントを調べて、結局のところ、2 つの — プログラミング インターフェイスと、データ ストリーム プロトコル — 適した候補となる標準化します。 その他の 2 つのコンポーネント: IPC メカニズムとネットワーク プロトコル-低すぎるレベルで存在するだけでなく、どちらも、ネットワークとオペレーティング システムに大きく依存します。 3 番目のアプローチもがある-ゲートウェイ — 標準化の可能性を提供します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [標準のプログラミング インターフェイス](../../odbc/reference/standard-programming-interface.md)  
  
-   [標準のデータ ストリーム プロトコル](../../odbc/reference/standard-data-stream-protocol.md)  
  
-   [標準のゲートウェイ](../../odbc/reference/standard-gateway.md)
