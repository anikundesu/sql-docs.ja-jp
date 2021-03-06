---
title: "[^](ワイルドカード - 一致しない文字列)(TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/06/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server (starting with 2008)
f1_keywords:
- wildcard
- '[^]_TSQL'
- '[^]'
- Not Match
dev_langs: TSQL
helpviewer_keywords:
- wildcard characters [SQL Server]
- '[^] (wildcard - character(s) not to match)'
ms.assetid: b970038f-f4e7-4a5d-96f6-51e3248c6aef
caps.latest.revision: "36"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: d80ac01fe5fbfcfce5da1a60acc15ab1b76bda70
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="-wildcard---characters-not-to-match-transact-sql"></a>\[^\](ワイルドカード - 一致しない文字列)(TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  角かっこで指定した範囲または集合に該当しない、任意の 1 文字を判別します。  
  
## <a name="examples"></a>使用例  
 次の例では [^] 演算子を使用して、`Contact` テーブルを対象に、名前の先頭が `Al` で始まり 3 文字目が `a` ではないすべての人を検索します。  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName  
FROM Person.Person  
WHERE FirstName LIKE 'Al[^a]%'  
ORDER BY FirstName;  
```  
  
## <a name="see-also"></a>参照  
 [ような &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/like-transact-sql.md)   
 [PATINDEX &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/patindex-transact-sql.md)   
 [% &#40;です。ワイルドカード - 文字 &#40; s &#41;一致と #41 です。&#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/percent-character-wildcard-character-s-to-match-transact-sql.md)   
  [& #91。&#93;です。&#40;です。ワイルドカード - 文字 &#40; s &#41;一致と #41 です。&#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/wildcard-character-s-to-match-transact-sql.md)   
 [\_&#40;です。ワイルドカード - 一致する 1 文字 &#41;&#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/wildcard-match-one-character-transact-sql.md)  
  
  
