---
title: "サブスクリプションの種類 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.newsubwizard.subscriptiontype.f1
ms.assetid: 9a50f588-ee45-4a87-826f-372ff0798587
caps.latest.revision: "20"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 62cc8604ef818768c612fc144ec3510330292bcf
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="subscription-type"></a>サブスクリプションの種類
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)] マージ レプリケーションには、サーバーとクライアントという 2 つのサブスクリプションの種類があります。[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の以前のバージョンでは、これらはグローバルとローカルと呼ばれていました。 サブスクライバーはサーバー サブスクリプションによって次の操作を実行できます。  
  
-   他のサブスクライバーにデータを再パブリッシュする。  
  
-   代わりの同期パートナーを提供する。  
  
-   設定された優先度に応じて競合を解決する。  
  
 ほとんどのサブスクライバーは、この機能を必要とせず、クライアント サブスクリプションを使用できます。 クライアント サブスクリプションは競合の検出と解決ができますが、サブスクライバーには優先度が割り当てられていません。変更によって競合が発生した場合は、変更をパブリッシャーに最初に送信したサブスクライバーが優先されます。  
  
> [!NOTE]  
>  サブスクリプションの種類は、作成後に変更することはできません。  
  
## <a name="options"></a>オプション  
 **[サブスクリプションのプロパティ]**  
 **[サブスクリプションの種類]** 列のドロップダウン リスト ボックスで、各サブスクライバーに対して、 **[クライアント]** または **[サーバー]** を選択します。 サブスクライバーでサーバー サブスクリプションを使用する場合は、 **[競合解決の優先度]** 列に 0 ～ 99.99 の範囲の数値を入力します。数字が大きいほどサブスクライバーに対する優先度が高くなります。  
  
## <a name="see-also"></a>参照  
 [プル サブスクリプションの作成](../../relational-databases/replication/create-a-pull-subscription.md)   
 [ssSDSFull](../../relational-databases/replication/create-a-push-subscription.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
