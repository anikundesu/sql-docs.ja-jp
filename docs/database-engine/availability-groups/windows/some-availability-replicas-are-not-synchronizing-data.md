---
title: "一部の可用性レプリカでデータが同期されない | Microsoft Docs"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: availability-groups
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.agdashboard.agp4synchronizing.issues.f1
helpviewer_keywords: Availability Groups [SQL Server], policies
ms.assetid: 3db6a569-e942-4321-a0dd-c4ab002087c8
caps.latest.revision: "12"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 2188014ebcdfae69a1c6792c03f104e950b6baea
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="some-availability-replicas-are-not-synchronizing-data"></a>一部の可用性レプリカでデータが同期されない
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="introduction"></a>概要  
  
|||  
|-|-|  
|**ポリシー名**|可用性レプリカのデータ同期状態|  
|**問題点**|一部の可用性レプリカでデータが同期されません。|  
|**カテゴリ**|**警告**|  
|**ファセット**|可用性グループ|  
  
## <a name="description"></a>説明  
 このポリシーは、可用性グループのすべての可用性レプリカのデータ同期状態をロール アップし、可用性レプリカの同期が稼働しているかどうかを確認します。 可用性レプリカのデータ同期状態が NOT SYNCHRONIZING の場合、ポリシーは通常とは異なる状態です。  
  
 可用性レプリカのデータ同期状態が NOT SYNCHRONIZING でない場合、ポリシーは正常な状態です。  
  
> [!NOTE]  
>  [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]のこのリリース向けに、TechNet Wiki の「 [一部の可用性レプリカでデータが同期されない](http://go.microsoft.com/fwlink/p/?LinkId=220852) 」に、考えられるエラーの原因および解決方法に関する情報が紹介されています。  
  
## <a name="possible-causes"></a>考えられる原因  
 この可用性グループで、少なくとも 1 つのセカンダリ レプリカが NOT SYNCHRONIZING 同期状態であり、プライマリ レプリカからデータを受け取っていません。  
  
## <a name="possible-solution"></a>考えられる解決方法  
 可用性レプリカのポリシーの状態を検索条件として、NOT SYNCHRONIZING 状態の可用性レプリカを探し、問題を解決してください。  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
