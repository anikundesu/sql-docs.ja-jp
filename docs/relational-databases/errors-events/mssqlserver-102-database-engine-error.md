---
title: MSSQLSERVER_102 | Microsoft Docs
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
helpviewer_keywords: 102 (Database Engine error)
ms.assetid: 264dc1a2-c8a0-4c89-b5f6-951baf950299
caps.latest.revision: "8"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8dea747ecad3640040dce817aaf706f90e4f63d6
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver102"></a>MSSQLSERVER_102
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|102|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|P_SYNTAXERR2|  
|メッセージ テキスト|'%.*ls' 付近に不適切な構文があります。|  
  
## <a name="explanation"></a>説明  
構文エラーを示します。 エラーにより[!INCLUDE[ssDE](../../includes/ssde-md.md)]でステートメントを処理できないため、追加情報は入手できません。  
  
このエラーは、互換性モードが 90 でも 100 でもない場合に、非推奨の RC4 暗号化または RC4_128 暗号化を使用して対称キーを作成しようとして発生した可能性があります。  
  
## <a name="user-action"></a>ユーザーの操作  
[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントに構文エラーがないか調べてください。  
  
RC4 または RC4_128 を使用して対称キーを作成する場合、AES アルゴリズムのいずれかなど、新しい暗号化を選択します  (推奨)。RC4 を使用する必要がある場合、ALTER DATABASE SET COMPATIBILITY_LEVEL を使用して、データベースの互換性レベルを 90 または 100 に設定します  (非推奨)。  
  
