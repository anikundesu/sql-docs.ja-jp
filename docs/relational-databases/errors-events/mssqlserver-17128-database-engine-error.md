---
title: MSSQLSERVER_17128 | Microsoft Docs
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
helpviewer_keywords: 17128 (Database Engine error)
ms.assetid: 7b15a5e6-fd41-47ce-ba87-54f72acea4bb
caps.latest.revision: "14"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 10284d4192b05ff7fac278e5a02e33384982517f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver17128"></a>MSSQLSERVER_17128
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|17128|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|INIT_NOBUFSPACE|  
|メッセージ テキスト|initdata: カーネル バッファー用のメモリがありません。|  
  
## <a name="explanation"></a>説明  
バッファー プールの初回メモリ割り当てまたは予約に失敗しており、SQL Server が終了します。  
  
## <a name="user-action"></a>ユーザーの操作  
通常、最小システム要件を大きく下回るような非常に小規模なコンピューターで SQL Server を起動した場合に発生します。  
  
