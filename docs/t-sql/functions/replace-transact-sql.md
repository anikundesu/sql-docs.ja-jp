---
title: "置換 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/23/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- REPLACE_TSQL
- REPLACE
dev_langs: TSQL
helpviewer_keywords:
- first string expression [SQL Server]
- replacing string expression
- third string expressions [SQL Server]
- second string expressions [SQL Server]
- REPLACE function
ms.assetid: 8a7aaaf2-62e3-46c0-8e44-fa22290dd86b
caps.latest.revision: "39"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: a50c0b7220eba654df21349e2fd3cd57b9a0d7d3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="replace-transact-sql"></a>REPLACE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  指定した文字列値をすべて別の文字列値に置き換えます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
REPLACE ( string_expression , string_pattern , string_replacement )  
```  
  
## <a name="arguments"></a>引数  
 *string_expression*  
 文字列は、[式](../../t-sql/language-elements/expressions-transact-sql.md)検索します。 *string_expression*文字またはバイナリ データ型であることができます。  
  
 *string _*パターン  
 検索するサブストリングを指定します。 *string_pattern*文字またはバイナリ データ型であることができます。 *string_pattern*空の文字列 (") にすることはできませんし、ページに収まる最大バイト数を超えない必要があります。  
  
 *string _*置換  
 置き換え後の文字列を指定します。 *string_replacement*文字またはバイナリ データ型であることができます。  
  
## <a name="return-types"></a>戻り値の型  
 返します**nvarchar**が、入力引数のいずれかの場合、 **nvarchar**データ型以外の場合はそれ以外の場合、置換を返します**varchar**です。  
  
 いずれかの引数が NULL の場合は、NULL を返します。  
  
 場合*string_expression*型ではありません**varchar (max)**または**nvarchar (max)、置換**戻り値が 8,000 バイトで切り捨てられます。 8,000 バイトより大きい値を返す*string_expression*大きな値のデータ型に明示的にキャストする必要があります。  
  
## <a name="remarks"></a>解説  
 REPLACE は、入力の照合順序に基づいて比較を行います。 使用することを指定した照合順序で比較を実行する[COLLATE](~/t-sql/statements/collations.md)入力に明示的な照合順序を適用します。  
  
 0x0000 (**char (0)**) の Windows 照合順序で未定義の文字は、REPLACE に含めることはできません。  
  
## <a name="examples"></a>使用例  
 次の例は、文字列を置換`cde`で`abcdefghi`で`xxx`です。  
  
```sql  
SELECT REPLACE('abcdefghicde','cde','xxx');  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
------------  
abxxxfghixxx  
(1 row(s) affected)  
```  
  
 次の例では、`COLLATE`関数。  
  
```sql  
SELECT REPLACE('This is a Test'  COLLATE Latin1_General_BIN,  
'Test', 'desk' );  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
------------  
This is a desk  
(1 row(s) affected)  
```  

  
## <a name="see-also"></a>参照  
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [文字列関数 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/string-functions-transact-sql.md)  
  
