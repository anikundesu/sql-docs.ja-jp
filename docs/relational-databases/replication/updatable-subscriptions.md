---
title: "[更新可能なサブスクリプション] | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.newsubwizard.updatablesubscriptions.f1
ms.assetid: 8e9a13a0-6b24-47c6-9d83-3cbaf08f673d
caps.latest.revision: "22"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 139c6e956eb8f54df670f9c913988d80b05d14b4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="updatable-subscriptions"></a>[更新可能なサブスクリプション]
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] トランザクション レプリケーションの場合、レプリケートされたデータは読み取り専用として扱う必要がありますが、更新可能なサブスクリプションを使用することにより、レプリケートされたデータを [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーで変更できます。 サブスクライバーでデータを変更する必要がある場合は、要件に応じて次のいずれかのオプションを選択してください。  
  
|更新可能なサブスクリプション タイプ|必要条件|  
|---------------------------------|------------------|  
|即時更新|サブスクライバーのデータを更新するために、パブリッシャーとサブスクライバーを接続します。|  
|キュー更新|サブスクライバーのデータを更新するために、パブリッシャーとサブスクライバーを接続する必要はありません。 更新をオフラインで実行し、後からパブリッシャーとサブスクライバーの間で同期させることができます。|  
  
## <a name="options"></a>オプション  
 **[以下のサブスクライバーの変更内容をレプリケートします]**  
 更新可能にする必要のある各サブスクライバーの **[レプリケート]** 列のチェック ボックスをオンにします。 これらの更新可能なサブスクライバーに対して、 **[パブリッシャーでのコミット]** 列のドロップダウン リスト ボックスから適切なオプションを選択します。  
  
-   即時更新サブスクリプションに対して **[変更を同時にコミットする]** を選択します。  
  
-   キュー更新サブスクリプションに対して **[変更をキューに登録し、可能な場合はコミット]** を選択します。  
  
## <a name="see-also"></a>参照  
 [プル サブスクリプションの作成](../../relational-databases/replication/create-a-pull-subscription.md)   
 [ssSDSFull](../../relational-databases/replication/create-a-push-subscription.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)   
 [トランザクション レプリケーションの更新可能なサブスクリプション](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
