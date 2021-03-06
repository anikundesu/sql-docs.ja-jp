---
title: "[エージェント プロファイル](単独のエージェント) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.profiles.perfprofileagentname.f1
helpviewer_keywords: Agent Profile dialog box
ms.assetid: 22713555-c496-4ce1-8ec7-4ae75cfadca8
caps.latest.revision: "18"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 39849c5a7cd991e45b16520744d4022d8c7b6dfa
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="agent-profiles-single-agent"></a>[エージェント プロファイル] (単独のエージェント)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] **[エージェント プロファイル]** ダイアログ ボックスを使用すると、エージェントのプロファイルを管理できます。 エージェント プロファイルを利用すると、各エージェントの実行時パラメーターを容易に管理できます。 それぞれのエージェントは既定のプロファイルを持ちます。一部のエージェントには、追加の定義済みプロファイルが用意されています。 たとえば、マージ エージェントには、低帯域幅接続の "低速リンク" プロファイルが用意されています。 ほとんどのアプリケーションでは定義済みのプロファイルで十分ですが、ユーザー定義プロファイルを作成して、エージェントの動作をカスタマイズすることもできます。  
  
## <a name="options"></a>オプション  
 **[新規の既定]**  
 特定の種類のエージェントに対してジョブを作成するときに使用するプロファイルを選択します。 たとえば、マージ パブリケーションに対していくつかのサブスクリプションを作成する場合、選択されたプロファイルが各サブスクリプションのマージ エージェント ジョブで使用されます。 既存のジョブのプロファイルを変更するには、プロファイルを選択し、 **[既存のエージェントの変更]**をクリックします。  
  
 **名前**  
 プロファイルの名前。  
  
 **型**  
 プロファイルの種類です。 **[ユーザー]** (ユーザー定義) または **[システム]** (定義済み) を選択します。  
  
 **[プロパティ] (...)**  
 クリックすると、エージェント プロファイルの各パラメーターに使用されている値が表示されます。  
  
 **新規**  
 クリックすると、新しいプロファイルを作成できます。  
  
 **Del**  
 ユーザー定義プロファイルを削除するには、プロファイルを選択し、 **[削除]** をクリックします。 定義済みのプロファイルは削除できません。  
  
 **[既存のエージェントの変更]**  
 特定の種類のエージェントのすべての既存のジョブで、選択したプロファイルを使用する場合は、プロファイルを選択して **[既存のエージェントの変更]** をクリックします。 たとえば、マージ パブリケーションに対して作成したサブスクリプションがいくつかあり、これらの各サブスクリプションのマージ エージェント ジョブで **低速リンク エージェント プロファイル**を使用するようにプロファイルを変更するには、目的のプロファイルを選択し、 **[既存のエージェントの変更]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [レプリケーション エージェント プロファイルの操作](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)   
 [レプリケーション エージェントの概要](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [レプリケーション エージェント プロファイル](../../relational-databases/replication/agents/replication-agent-profiles.md)  
  
  
