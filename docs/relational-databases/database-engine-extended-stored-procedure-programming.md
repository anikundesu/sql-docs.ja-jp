---
title: "データベース エンジン拡張ストアド プロシージャ プログラミング | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: relational-databases-misc
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], programming
- stored procedures [SQL Server], extended
- Database Engine [SQL Server], stored procedures
- macros [SQL Server]
- Extended Stored Procedure API [SQL Server]
ms.assetid: 158a6765-0542-4e84-b5ab-f173d946ef5e
caps.latest.revision: "37"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2fbf4a216b71b68f6ac8101e2a3ab404f62cf86c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="database-engine-extended-stored-procedure-programming"></a>データベース エンジン拡張ストアド プロシージャ プログラミング
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../includes/ssnotedepfuturedontuse-md.md)] 代わりに CLR Integration を使用してください。 詳細については、「[共通言語ランタイム &#40;CLR&#41; 統合のプログラミング概念](../relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts.md)」をご覧ください。  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] 拡張ストアド プロシージャ API は、[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の機能を拡張するためのサーバー ベースのアプリケーション プログラミング インターフェイスです。 この API は、拡張ストアド プロシージャおよびゲートウェイ アプリケーションのカテゴリでアプリケーションの構築に使用する C および C++ の関数とマクロで構成されています。  
  
 拡張ストアド プロシージャを使用すると、C などのプログラミング言語を使用してユーザー独自の外部ルーチンを作成できます。拡張ストアド プロシージャは、ユーザーには通常のストアド プロシージャのように見え、同じように実行されます。 拡張ストアド プロシージャにはパラメーターを渡すことができ、拡張ストアド プロシージャは結果や状態を返すことができます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [拡張ストアド プロシージャのプログラミング](../relational-databases/extended-stored-procedures-programming/database-engine-extended-stored-procedures-programming.md)  
 拡張ストアド プロシージャを作成、管理、および使用する方法について説明します。  
  
 [拡張ストアド プロシージャのプログラマーズ リファレンス](../relational-databases/extended-stored-procedures-reference/database-engine-extended-stored-procedures-reference.md)  
 拡張ストアド プロシージャ API に関する参照トピックが記載されています。  
  
  
