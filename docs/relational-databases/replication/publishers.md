---
title: "パブリッシャー | Microsoft Docs"
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
f1_keywords: sql13.rep.configuredistributionwizard.enablepublishers.f1
ms.assetid: 116cd6a5-32ac-4273-81a2-d184408e0f07
caps.latest.revision: "21"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2c277d809dc9ce385326520872cb5ccc10f98eef
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="publishers"></a>パブリッシャー
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] 他のパブリッシャーにこのディストリビューターの使用許可を与えることができます。 パブリッシャーがサーバーをパブリッシャーのリモート ディストリビューターとして使用しても、そのサーバーがパブリッシャーにならないことに注意してください。 パブリッシャーに接続し、パブリッシュするための構成を行って、このサーバーをディストリビューターとして選択する必要があります。 パブリケーションの新規作成ウィザードを使用して、パブリッシャーを構成し、ディストリビューターを選択できます。  
  
 パブリッシャーとして選択したサーバーでは、このウィザードの **[ディストリビューション データベース]** ページで指定したディストリビューション データベースが使用されます。 他のディストリビューション データベースを使用する場合には、この時点でパブリッシャーを有効にしないでください。 代わりに、ディストリビューションの構成ウィザードの終了後に、 **[ディストリビューターのプロパティ]** ダイアログ ボックスを使用してパブリッシャーを追加します。  
  
## <a name="options"></a>オプション  
 **パブリッシャー**  
 このディストリビューターの使用を許可するサーバーを選択します。 その他のプロパティを表示し、設定するには、[パブリッシャー] の横にあるプロパティ ボタン (**[...]**) をクリックします。  
  
 **[追加]**  
 許可するサーバーが一覧に表示されていない場合には、 **[追加]** をクリックして、使用できるパブリッシャーの一覧に [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリッシャーまたは Oracle パブリッシャーを追加します。  
  
## <a name="see-also"></a>参照  
 [ディストリビューションの構成](../../relational-databases/replication/configure-distribution.md)   
 [パブリッシングおよびディストリビューションの構成](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [ディストリビューターとパブリッシャーのプロパティの表示および変更](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Publisher で文書を作成するには](../../relational-databases/replication/publish/create-a-publication.md)  
  
  
