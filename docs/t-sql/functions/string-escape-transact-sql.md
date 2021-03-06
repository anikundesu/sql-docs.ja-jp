---
title: "STRING_ESCAPE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/25/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STRING_ESCAPE
- STRING_ESCAPE_TSQL
dev_langs: TSQL
helpviewer_keywords: STRING_ESCAPE function
ms.assetid: 2163bc7a-3816-4304-9c40-8954804f5465
caps.latest.revision: "11"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: add41d4ac936190316f432f810f40fec286e4647
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="stringescape-transact-sql"></a>STRING_ESCAPE (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  テキストに特殊文字をエスケープし、エスケープ文字でテキストを返します。 **STRING_ESCAPE**決定的関数です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
STRING_ESCAPE( text , type )  
```  
  
## <a name="arguments"></a>引数  
 *text*  
 **Nvarchar**[式](../../t-sql/language-elements/expressions-transact-sql.md)エスケープする必要があるオブジェクトを表す式。  
  
 *型*  
 適用される規則をエスケープします。 現在サポートされている値は`'json'`します。  
  
## <a name="return-types"></a>戻り値の型  
 **nvarchar (max)**特殊のエスケープと制御文字を含むテキスト。 現在**STRING_ESCAPE**次の表に示すように JSON の特殊文字をエスケープのみです。  
  
|特殊文字|エンコードされたシーケンス|  
|-----------------------|----------------------|  
|引用符 (")|\\"|  
|逆斜線 (\\)|\\\|  
|斜線 (/)|\\/|  
|バックスペース|\b|  
|改ページ|\f|  
|改行|\n|  
|キャリッジ リターン|\r|  
|水平タブ|\t|  
  
|制御文字|エンコードされたシーケンス|  
|-----------------------|----------------------|  
|CHAR(0)|\u0000|  
|CHAR(1)|\u0001|  
|[...]|[...]|  
|CHAR(31)|\u001f|  
  
## <a name="remarks"></a>解説  
  
## <a name="examples"></a>使用例  
  
### <a name="a--escape-text-according-to-the-json-formatting-rules"></a>A.  JSON 形式の規則に従って文字列をエスケープします。  
 次のクエリでは、JSON の規則を使用して、特殊文字をエスケープし、エスケープされたテキストを返します。  
  
```  
SELECT STRING_ESCAPE('\   /  
\\    "     ', 'json') AS escapedText;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
escapedText  
-------------------------------------------------------------  
\\\t\/\n\\\\\t\"\t
```  
  
### <a name="b-format-json-object"></a>B. JSON オブジェクトの書式設定  
 次のクエリでは、数値と文字列の変数から JSON テキストを作成し、変数内の任意の特殊な JSON 文字をエスケープします。  
  
```  
SET @json = FORMATMESSAGE('{ "id": %d,"name": "%s", "surname": "%s" }',   
    17, STRING_ESCAPE(@name,'json'), STRING_ESCAPE(@surname,'json') );  
```  
  
## <a name="see-also"></a>参照  
 [文字列関数 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/string-functions-transact-sql.md)   
 [部分文字列と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/substring-transact-sql.md)  
  
  
