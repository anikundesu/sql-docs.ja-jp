---
title: "sp_datatype_info (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_datatype_info_TSQL
- sp_datatype_info
dev_langs: TSQL
helpviewer_keywords: sp_datatype_info
ms.assetid: 045f3b5d-6bb7-4748-8b4c-8deb4bc44147
caps.latest.revision: "32"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 32edf386d51ab28ae453db75c4adc8067c747cff
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spdatatypeinfo-transact-sql"></a>sp_datatype_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在の環境でサポートされるデータ型に関する情報を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_datatype_info [ [ @data_type = ] data_type ]   
     [ , [ @ODBCVer = ] odbc_version ]   
```  
  
## <a name="arguments"></a>引数  
 [  **@data_type=** ] *data_type*  
 対象となるデータ型のコード番号を指定します。 すべてのデータ型の一覧を表示するには、このパラメーターを省略します。 *data_type*は**int**、既定値は 0 です。  
  
 [  **@ODBCVer=** ] *odbc_version*  
 使用している ODBC のバージョンを指定します。 *odbc_version*は**tinyint**、既定値は 2 です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 なし  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|TYPE_NAME|**sysname**|DBMS に依存するデータ型です。|  
|DATA_TYPE|**smallint**|このデータ型のすべての列がマップされる ODBC 型のコードです。|  
|PRECISION|**int**|データ ソースでのデータ型の最大有効桁数です。 有効桁数を適用できないデータ型については、NULL が返されます。 PRECISION 列の戻り値は 10 進表記です。|  
|LITERAL_PREFIX|**varchar (**32**)**|定数の先頭に記述する文字です。 単一引用符など、(**'**) 文字の種類とバイナリの 0x をします。|  
|LITERAL_SUFFIX|**varchar (**32**)**|定数の末尾に記述する文字です。 単一引用符など、(**'**) 文字の種類とバイナリの引用符のです。|  
|CREATE_PARAMS|**varchar (**32**)**|データ型の作成パラメーターの説明です。 たとえば、 **10 進**は"precision, scale"、 **float**が NULL の場合、および**varchar** "max_length"は、します。|  
|NULLABLE|**smallint**|NULL 値を許容するかどうかを示します。<br /><br /> 1 = null 値を許可します。<br /><br /> 0 = は null 値を許容します。|  
|CASE_SENSITIVE|**smallint**|大文字と小文字を区別するかどうかを示します。<br /><br /> 1 = この型のすべての列では、大文字と小文字を区別します (照合の場合)。<br /><br /> 0 = この型のすべての列では、大文字と小文字を区別しません。|  
|SEARCHABLE|**smallint**|列の型の検索機能を示します。<br /><br /> 1 = 検索できません。<br /><br /> 2 = LIKE で検索できます。<br /><br /> 3 = WHERE で検索できます。<br /><br /> 4 = WHERE または LIKE で検索できます。|  
|UNSIGNED_ATTRIBUTE|**smallint**|データ型の符号を示します。<br /><br /> 1 = 符号なしのデータ型です。<br /><br /> 0 = 符号付きのデータ型です。|  
|MONEY|**smallint**|指定します、 **money**データ型。<br /><br /> 1 = **money**データ型。<br /><br /> 0 = 非、 **money**データ型。|  
|AUTO_INCREMENT|**smallint**|自動インクリメントを示します。<br /><br /> 1 = 自動インクリメントを行います。<br /><br /> 0 = 自動インクリメントを行いません。<br /><br /> NULL = この属性は適用できません。<br /><br /> アプリケーションは、この属性を持つ列に値を挿入することはできますが、その列の値を更新することはできません。 例外を除いて、**ビット**データ型 AUTO_INCREMENT は、真数型または概数のデータ型カテゴリに属しているデータ型に対してのみ有効です。|  
|LOCAL_TYPE_NAME|**sysname**|データ ソースに依存するデータ型のローカライズされた名前です。 たとえば、DECIMAL はフランス語で DECIMALE になります。 ローカライズされた名前がそのデータ ソースによってサポートされない場合は NULL が返されます。|  
|MINIMUM_SCALE|**smallint**|データ ソースでのデータ型の最小小数点以下桁数です。 データ型の小数点以下桁数が固定されている場合は、MINIMUM_SCALE 列および MAXIMUM_SCALE 列の両方にこの値が入ります。 小数点以下桁数が適用されない場合は NULL が返されます。|  
|MAXIMUM_SCALE|**smallint**|データ ソースでのデータ型の最大小数点以下桁数です。 この最大小数点以下桁数がデータ ソース上で別に定義されず、最大有効桁数と同じと定義されている場合は、この列には PRECISION 列と同じ値が入ります。|  
|SQL_DATA_TYPE|**smallint**|記述子の TYPE フィールドでの SQL データ型の値です。 この列は、DATA_TYPE 列と同じを除く、 **datetime**と ANSI**間隔**データ型。 このフィールドは常に値を返します。|  
|SQL_DATETIME_SUB|**smallint**|**datetime**または ANSI**間隔**SQL_DATA_TYPE の値が SQL_DATETIME または SQL_INTERVAL の場合のサブコードします。 型のデータ型以外の**datetime**と ANSI**間隔**、このフィールドは NULL です。|  
|NUM_PREC_RADIX|**int**|Bits または列が保持できる最大数を計算するための数字の数。 データ型が概数型である場合、この列に含まれる値は 2 で、複数のビットを示します。 真数型である場合、この列に含まれる値は 10 で、複数の小数点以下桁数を示します。 それ以外は、この列は NULL です。 アプリケーションは、基数と精度を組み合わせて、その列が保持できる最大数を計算できます。|  
|INTERVAL_PRECISION|**smallint**|間隔の場合は、有効桁数を先頭の値*data_type*は**間隔**以外の場合は NULL それ以外の場合。|  
|USERTYPE|**smallint**|**usertype** systypes テーブルからの値。|  
  
## <a name="remarks"></a>解説  
 sp_datatype_info は、ODBC で SQLGetTypeInfo と同じです。 結果は、まず DATA_TYPE の順序で、次にデータ型が対応する ODBC SQL データ型にどれだけ正確にマップされているのかに基づいて返されます。  
  
## <a name="permissions"></a>Permissions  
 public ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例の情報を取得する、 **sysname**と**nvarchar**データ型を指定して、 *data_type*の値`-9`です。  
  
```  
USE master;  
GO  
EXEC sp_datatype_info -9;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
