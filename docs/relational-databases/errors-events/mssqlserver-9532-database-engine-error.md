---
title: MSSQLSERVER_9532 | Microsoft Docs
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
helpviewer_keywords: 9532 (Database Engine error)
ms.assetid: ab95cce8-4f97-4aea-a746-a73eea7c9aab
caps.latest.revision: "9"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 514c8efd47a7cb54397db495a268b1c9c415be58
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver9532"></a>MSSQLSERVER_9532
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|9532|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|XMLERR_COLUMNSET_CANNOT_CONVERT_FROM_TO|  
|メッセージ テキスト|列セット '%.*ls' に関係するクエリ/DML 操作で、列 '%.\*ls' のデータ型 '%ls' をデータ型 '%ls' に変換する際に変換に失敗しました。|  
  
## <a name="explanation"></a>説明  
列セットは、型指定されていない XML 表現であり、テーブルの複数の列を 1 つにまとめて構造化した出力です。 XML 列セットを使用してスパース列の値を挿入または更新する場合、基になるスパース列に挿入される値は、**xml** データ型から暗黙的に変換されます。 列のデータ型に変換できない値が指定されました。  
  
## <a name="user-action"></a>ユーザーの操作  
指定された値は暗黙的に変換することができなかったため、無効なエントリとなる可能性があります。 エラーを修正して再試行してください。 値が正しい場合は、列セットではなく個々の列を使用するようにステートメントを変更します。 これにより、値を適切なデータ型に明示的にキャストすることができます。  
  
