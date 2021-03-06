---
title: "(TRANSACT-SQL) を圧縮解除 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/30/2015
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
- DECOMPRESS
- DECOMPRESS_TSQL
helpviewer_keywords: DECOMPRESS function
ms.assetid: 738d56be-3870-4774-b112-3dce27becc11
caps.latest.revision: "8"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2988959b7ec3f9eccad74b752e7643f1e6675590
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="decompress-transact-sql"></a>圧縮解除 (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  GZIP アルゴリズムを使用して、入力式を圧縮解除できません。 圧縮の結果は、バイト配列 (varbinary (max) 型) です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
DECOMPRESS ( expression )  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 **Varbinary (***n***)**、 **varbinary (max)**、または**バイナリ (** *n***)**. 詳細については、「[式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)」を参照してください。  
  
## <a name="return-types"></a>戻り値の型  
 データ型を返す**varbinary (max)**型です。 入力引数は、ZIP アルゴリズムを使用して圧縮が解除されます。 ユーザーは、必要な場合は、対象の種類に結果を明示的にキャストする必要があります。  
  
## <a name="remarks"></a>解説  
  
## <a name="examples"></a>使用例  
  
### <a name="a-decompress-data-at-query-time"></a>A. クエリ時にデータを圧縮解除します。  
 次の例では、圧縮するテーブルからデータを表示する方法を示します。  
  
```  
SELECT _id, name, surname, datemodified,  
             CAST(DECOMPRESS(info) AS NVARCHAR(MAX)) AS info  
FROM player;  
```  
  
### <a name="b-display-compressed-data-using-computed-column"></a>B. 計算列を使用して圧縮されたデータを表示します。  
 次の例では、圧縮解除されたデータを格納するテーブルを作成する方法を示します。  
  
```  
CREATE TABLE (  
    _id int primary key identity,  
    name nvarchar(max),  
    surname nvarchar(max),  
    info varbinary(max),  
    info_json as CAST(decompress(info) as nvarchar(max))  
);  
```  
  
## <a name="see-also"></a>参照  
 [文字列関数 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/string-functions-transact-sql.md)   
 [COMPRESS &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/compress-transact-sql.md)  
  
  
