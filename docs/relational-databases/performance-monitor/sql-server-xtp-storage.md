---
title: "SQL Server の XTP ストレージ | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4070580b-880d-4f4c-abcc-626a4fe0c9a2
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a9cb620530972d0b8f1999f70d2a5a3996794cd8
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sql-server-xtp-storage"></a>SQL Server の XTP ストレージ
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  SQL Server XTP ストレージのパフォーマンス オブジェクトには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインメモリ OLTP のためのオンディスク ストレージに関連するカウンターが含まれています。  
  
 次の表では、 **SQL Server XTP ストレージ** カウンターについて説明します。  
  
|カウンター|説明|  
|-------------|-----------------|  
|**終了したチェックポイント**|オンライン エージェントによって終了されたチェックポイントの数。|  
|**完了したチェックポイント**|オフライン チェックポイント スレッドによって処理されたチェックポイントの数。|  
|**完了したコア マージ**|マージ ワーカー スレッドによって実行されたコア マージの数。 これらのマージは、引き続きインストールされている必要があります。|  
|**マージ ポリシーの評価**|サーバーが開始してから行われたマージ ポリシーの評価の数。|  
|**未処理のマージ要求**|サーバーが開始してから未処理になっているのマージ要求の数。|  
|**放棄されたマージ**|エラーにより放棄されたマージの数。|  
|**インストールされているマージ**|適切にインストールされたマージの数。|  
|**マージされているファイルの総数**|マージされているソース ファイルの総数。 この数を使用すると、マージ内のソース ファイル数の平均がわかります。|  
  
## <a name="see-also"></a>参照  
 [SQL Server XTP &#40;インメモリ OLTP&#41; パフォーマンス カウンター](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)  
  
  
