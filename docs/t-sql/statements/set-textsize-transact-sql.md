---
title: "[SET textsize] (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/12/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TEXTSIZE_TSQL
- TEXTSIZE
- SET_TEXTSIZE_TSQL
- SET TEXTSIZE
dev_langs: TSQL
helpviewer_keywords:
- SET TEXTSIZE statement
- SELECT statement [SQL Server], text size returned
- size [SQL Server], text and image data
- TEXTSIZE option
- text size returned [SQL Server]
ms.assetid: 787154a6-39a6-4dd6-a6d0-67b4364f95d5
caps.latest.revision: "38"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 5ecffd26c600d3a224824aa9a64ce347cd2f9fbc
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="set-textsize-transact-sql"></a>SET TEXTSIZE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  サイズを指定**varchar (max)**、 **nvarchar (max)**、 **varbinary (max)**、**テキスト**、 **ntext**、および**イメージ**、SELECT ステートメントによって返されるデータ。  
  
> [!IMPORTANT]  
>  **ntext**、**テキスト**、および**イメージ**データ型は、将来のバージョンで削除される予定[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 新しい開発作業では、これらのデータ型の使用は避け、現在これらのデータ型を使用しているアプリケーションは修正するようにしてください。 代わりに、 **nvarchar(max)**、 **varchar(max)**、 **varbinary(max)** を使用してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
SET TEXTSIZE { number }   
```  
  
## <a name="arguments"></a>引数  
 *number*  
 長さは、 **varchar (max)**、 **nvarchar (max)**、 **varbinary (max)**、**テキスト**、 **ntext**、または**イメージ**(バイト単位) のデータ。 *数*2,147, 483,647 (2 GB) の最大値を持つ整数です。  値-1 は無制限のサイズを示します。 値 0 は、4 KB の既定値をサイズをリセットします。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client (10.0 以降) および ODBC Driver for[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]自動的に指定される`-1`(無制限) の場合に接続します。  
  
 **ドライバーよりも古い[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2008:** 、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーと[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダー (バージョン 9) の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続するときに、2,147, 483,647 に TEXTSIZE を自動的に設定します。  
  
## <a name="remarks"></a>解説  
 SET TEXTSIZE に影響を設定、@@TEXTSIZE関数。  
  
 TEXTSIZE は、解析時ではなく実行時に設定されます。  
  
## <a name="permissions"></a>Permissions  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [@@TEXTSIZE &#40;Transact-SQL&#41;](../../t-sql/functions/textsize-transact-sql.md)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  
