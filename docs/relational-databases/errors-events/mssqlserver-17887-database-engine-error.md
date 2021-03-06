---
title: MSSQLSERVER_17887 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 17887 (Database Engine error)
ms.assetid: ad0806e6-3296-4c32-b103-fccf0f8a8d3d
caps.latest.revision: "17"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bb10e2970cf8612486bb515e8e8d88ba483ef4a0
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver17887"></a>MSSQLSERVER_17887
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|17887|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SRV_IO_COMP_LISTENER_NONYIELDING|  
|メッセージ テキスト|IO 完了リスナー (0x%lx) のワーカー 0x%p が、ノード %ld で応答を停止している可能性があります。 CPU の概算使用量: カーネル %I64d ミリ秒、ユーザー %I64d ミリ秒、間隔: %I64d。|  
  
## <a name="explanation"></a>説明  
ネットワークの読み取りまたは書き込みのイベント用に I/O 完了ルーチンを実行しているときに、指定されたノード上の I/O 完了ポート リスナーに問題が発生している可能性があることを示します。 I/O 完了ポート リスナーが I/O 完了ルーチンの実行から戻ると、このエラーは解決します。  
  
## <a name="user-action"></a>ユーザーの操作  
マイクロソフト カスタマー サポート サービス (CSS) に連絡してください。  
  
