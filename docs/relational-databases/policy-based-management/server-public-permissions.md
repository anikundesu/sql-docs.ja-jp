---
title: "サーバーのパブリック権限 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Best Practices [Database Engine]
ms.assetid: 9a276caa-ea38-473d-92bc-26302bfcf660
caps.latest.revision: "11"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 616eb78e01c635e6c70df4c9be9bda662b74959d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="server-public-permissions"></a>サーバーのパブリック権限
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] このルールでは、public サーバー ロールにサーバー権限があるかどうかを調べます。 サーバー上で作成されたログインは、すべて public サーバー ロールのメンバーです。 この条件が満たされる場合、サーバー上のログインにはすべてサーバー権限が付与されます。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 public サーバー ロールにサーバー権限を付与しないでください。  
  
> [!IMPORTANT]  
>  セットアップの完了後、 **PUBLIC** ロールには、 **専用管理者接続** 以外のすべてのエンドポイントに対する **CONNECT**権限が付与されます。 これは正常な動作です。通常は変更しないでください (アクセスの制御には、新しいログインの作成時に自動的に付与される **CONNECT SQL** 権限が使用されます)。  
  
### <a name="for-more-information"></a>詳細情報  
 [SQL Server の保護](../../relational-databases/security/securing-sql-server.md)  
  
  
