---
title: "パーセント文字 (ワイルドカード - 一致する文字列) (TRANSACT-SQL) |Microsoft ドキュメント"
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
- Azure SQL Data Warehouse
- Azure SQL Database
- SQL Server (starting with 2008)
f1_keywords:
- '%'
- '%_TSQL'
- wildcard
dev_langs: TSQL
helpviewer_keywords:
- conditions [SQL Server], wildcards
- '% (wildcard - character(s) to match)'
- matching conditions [SQL Server]
- wildcard characters [SQL Server]
- characters [SQL Server], wildcard
ms.assetid: d4cbc1a9-37e1-4101-97fb-e6ac30c1223e
caps.latest.revision: "23"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: c75d2707cb09a85de67c0b7f9b5d337e6468b4d3
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="percent-character-wildcard---characters-to-match-transact-sql"></a>パーセント文字 (ワイルドカード - 一致する文字列) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  0 個以上の文字で構成される文字列に一致します。 このワイルドカード文字は、プレフィックスとしてもサフィックスとしても使用できます。  
  
## <a name="examples"></a>使用例  
 次の例では、`Person` の `AdventureWorks2012` テーブルに登録されている人のうち、`Dan` で始まるすべての名前を返します。  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName  
FROM Person.Person  
WHERE FirstName LIKE 'Dan%';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ような &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/like-transact-sql.md)   
 [演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)   
 [式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
 [& #91。&#93;です。(ワイルドカード - 一致する文字列)](../../t-sql/language-elements/wildcard-character-s-to-match-transact-sql.md)   
  [& #91、^ (& a) #93 です。(ワイルドカード - 一致しない文字列)](../../t-sql/language-elements/wildcard-character-s-not-to-match-transact-sql.md)     
 [_ (ワイルドカード - 一致する 1 文字)](../../t-sql/language-elements/wildcard-match-one-character-transact-sql.md)  
    
  
