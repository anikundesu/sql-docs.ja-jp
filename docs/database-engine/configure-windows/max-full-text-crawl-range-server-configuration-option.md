---
title: "max full-text crawl range サーバー構成オプション | Microsoft Docs"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: TSQL
helpviewer_keywords:
- crawls [full-text search]
- max full-text crawl range option
ms.assetid: a49de86b-0891-4dcd-89c0-ead30aab00e0
caps.latest.revision: "24"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8df5fb6d10be502ae07cd43f4103e3fcd5091bbd
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="max-full-text-crawl-range-server-configuration-option"></a>max full-text crawl range サーバー構成オプション
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  **max full-text crawl range** オプションは、CPU の使用率を最適化して、フル クロール中のクロールのパフォーマンスを向上させる場合に使用します。 このオプションを使用して、フル インデックス クロール中に [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって使用されるパーティションの数を指定できます。 たとえば、CPU が多数あり、CPU の使用率が最適でない場合は、このオプションの最大値を大きくすることができます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、このオプションだけでなく、テーブルの行数や CPU 数などの他の多くの要素によって、使用する実際のパーティション数を決定します。  
  
 このオプションの既定値は 4 です。また、最小値は 1 で、最大値は 256 です。 このオプションを変更すると、変更後のクロールにのみ影響します。 このオプションの設定を変更しても、処理中のクロールは影響を受けません。  
  
 **max full-text crawl range** オプションは拡張オプションです。 **sp_configure** システム ストアド プロシージャを使用して **max full-text crawl range** の設定を変更するには、 **show advanced options** を 1 に設定する必要があります。 新しい設定は、サーバーを再起動しなくてもすぐに有効になります。  
  
## <a name="see-also"></a>参照  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
