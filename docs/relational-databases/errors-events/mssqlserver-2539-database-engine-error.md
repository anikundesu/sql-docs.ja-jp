---
title: MSSQLSERVER_2539 | Microsoft Docs
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
helpviewer_keywords: 2539 (Database Engine error)
ms.assetid: e638efcc-56f4-40f9-9740-17ef67b47d79
caps.latest.revision: "16"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6ccacd3d44477f156882474cbfb37111135f4ef4
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver2539"></a>MSSQLSERVER_2539
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|2539|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC_ALLOCATION_SUMMARY_FOR_DATABASE|  
|メッセージ テキスト|このデータベース内のエクステントの合計数 = EXTENTS、使用ページ数 = USED_PAGES、および予約ページ数 = RESERVED_PAGES。|  
  
## <a name="explanation"></a>説明  
この情報は、DBCC CHECKALLOC コマンドからの出力の一部です。 この情報は、指定されたデータベースについて、割り当てられたエクステント数、使用ページ数、および予約ページ数を示す要約です。  
  
## <a name="user-action"></a>ユーザーの操作  
なし  
  
