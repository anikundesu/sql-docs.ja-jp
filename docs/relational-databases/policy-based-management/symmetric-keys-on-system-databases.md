---
title: "システム データベースの対称キー | Microsoft Docs"
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
ms.assetid: 28e25ae3-d3dc-45ec-b316-f219512a1a47
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ff1c3870a2e10fcc7bca42aca4cf6a3c59b1239a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="symmetric-keys-on-system-databases"></a>システム データベースの対称キー
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] このルールでは、master、msdb、model、および tempdb の各データベースにあるユーザーが作成した対称キーについて確認します。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 システム データベースには対称キーを作成しないでください。  
  
## <a name="for-more-information"></a>詳細情報  
 [暗号化アルゴリズムの選択](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したベスト プラクティスの監視と実行](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
