---
title: "パフォーマンスのベースラインの設定 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: performance
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- database performance [SQL Server], baselines
- monitoring performance [SQL Server], baselines
- tuning databases [SQL Server], baselines
- server performance [SQL Server], baselines
- performance [SQL Server], baselines
- baseline performance [SQL Server]
- measurements for baseline statistics [SQL Server]
- monitoring server performance [SQL Server], establishing baseline
- database monitoring [SQL Server], baselines
ms.assetid: dc5aa8d6-2507-448f-ad86-4196443915fc
caps.latest.revision: "22"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ef8bc2586219538cedc61e7623e09ff16b3f0066
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="establish-a-performance-baseline"></a>パフォーマンスのベースラインの設定
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システムが最適に実行されているかどうかを判断するには、たとえ問題が発生しなくても、長期にわたって定期的にパフォーマンスを測定し、サーバーのパフォーマンス ベースラインを設定します。 各新規測定値セットを以前の測定値と比較します。  
  
 次の要素が、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のパフォーマンスに影響します。  
  
-   システム リソース (ハードウェア)  
  
-   ネットワーク アーキテクチャ  
  
-   オペレーティング システム  
  
-   データベース アプリケーション  
  
-   クライアント アプリケーション  
  
 少なくとも、ベースライン測定値を使用して次のことを判断します。  
  
-   操作のピーク時間とオフピーク時間  
  
-   実稼働クエリまたはバッチ コマンドの応答時間。  
  
-   データベースのバックアップと復元の終了までにかかる時間  
  
 サーバーのパフォーマンス ベースラインを設定したら、ベースライン統計と現在のサーバーのパフォーマンスを比較します。 ベースラインと比べて極端に大きいまたは小さい数値は、詳細な調査の対象となります。 これらはチューニングや再構成が必要な要素を示しています。 たとえば、クエリ セットの実行時間が増える場合、クエリを調べて、クエリの再作成が可能かどうか、列統計または新しいインデックスを追加する必要があるかどうかを判断します。  
  
## <a name="see-also"></a>参照  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
