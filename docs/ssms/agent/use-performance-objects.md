---
title: "パフォーマンス オブジェクトの使用 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent, monitoring
- SQL Server Agent service, monitoring
- SQL Server Agent service, performance objects
- SQL Server Agent, performance objects
- performance objects [SQL Server Agent]
- monitoring [SQL Server], SQL Server Agent
- monitoring [SQL Server Agent]
- performance counters [SQL Server], SQL Server Agent
- counters [SQL Server], SQL Server Agent
ms.assetid: 830b843a-6b2a-4620-a51b-98358e9fc54b
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 34279a9ff92a6cda54ee76ebadad6bc9ed6ca5ef
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="use-performance-objects"></a>パフォーマンス オブジェクトの使用
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントには、サービスの動作を監視するためのパフォーマンス オブジェクトとパフォーマンス カウンターが含まれています。 パフォーマンス オブジェクトを使用すると、パフォーマンス モニターや Windows ツールを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスのバックグラウンド動作を特定できるようになります。 たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスで現在実行されているアクティブなジョブの数を特定して、ブロックされたジョブを特定できます。  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスのパフォーマンス オブジェクトとパフォーマンス カウンターは、コンピューターにインストールされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] のインスタンスごとに存在します。 パフォーマンス オブジェクトの名前は、各オブジェクトが表す [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] のインスタンスに従って付けられます。  
  
次の表は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスのパフォーマンス オブジェクトの命名形式を示しています。  
  
|インスタンスの種類|オブジェクト名です。|  
|-----------------|---------------|  
|既定|**SQLAgent:***オブジェクト*:*カウンター*|  
|名前付き|**SQLAgent$**<br /> **&#42;instance_name&#42; :***オブジェクト*:*カウンター*|  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントの次のパフォーマンス オブジェクトが含まれています。  
  
|オブジェクト名です。|Description|  
|---------------|---------------|  
|[SQLAgent:Jobs](http://msdn.microsoft.com/en-us/225b5e2d-4a78-4178-b2b6-b419df83c4aa)|開始されたジョブ、成功率、および現在の状態に関するパフォーマンス情報|  
|[SQLAgent:JobSteps](http://msdn.microsoft.com/en-us/44f9983c-1753-4fe0-8475-973aa2460b3a)|ジョブ ステップに関する状態情報|  
|[SQLAgent:Alerts](http://msdn.microsoft.com/en-us/e5e37f74-ee88-46d0-ad8f-71fd1b1fa64a)|警告と通知の数に関する情報|  
|[SQLAgent:Statistics](http://msdn.microsoft.com/en-us/ebe92bfa-0721-48aa-9ba6-e7904ad265a1)|パフォーマンスに関する一般的な情報|  
  
## <a name="see-also"></a>参照  
[パフォーマンスの監視とチューニング](http://msdn.microsoft.com/en-us/87f23f03-0f19-4b2e-bfae-efa378f7a0d4)  
[システム モニターを起動する方法 (Windows)](http://msdn.microsoft.com/en-us/5e51bb79-5737-470b-9c47-fac330c001c5)  
  
