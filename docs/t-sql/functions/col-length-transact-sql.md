---
title: "COL_LENGTH (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/24/2017
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
- COL_LENGTH
- COL_LENGTH_TSQL
dev_langs: TSQL
helpviewer_keywords:
- lengths [SQL Server], columns
- COL_LENGTH function
- column properties [SQL Server]
- column length [SQL Server]
ms.assetid: cf891206-c49f-40eb-858e-eefd2b638a33
caps.latest.revision: "20"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: a5fe2a9da9df8de05f5e4e7f492179445edcf62f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="collength-transact-sql"></a>COL_LENGTH (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

定義されている列の長さをバイト単位で返します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
COL_LENGTH ( 'table' , 'column' )   
```  
  
## <a name="arguments"></a>引数  
**'** *テーブル* **'**  
列の長さに関する情報を取得するテーブルの名前を指定します。 *テーブル*型の式は、 **nvarchar**です。
  
**'** *列* **'**  
長さを取得する列の名前を指定します。 *列*型の式は、 **nvarchar**です。
  
## <a name="return-type"></a>戻り値の型
**smallint**
  
## <a name="exceptions"></a>例外  
エラーが発生した場合、または呼び出し元にオブジェクトの表示権限がない場合は、NULL が返されます。
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ユーザーは、ユーザーが所有するまたはをユーザーが許可されているアクセス許可のセキュリティ保護可能なメタデータのみを表示できます。 つまり、オブジェクトに対する権限がユーザーに与えられていない場合、メタデータを生成する組み込み関数 (COL_LENGTH  など) が NULL を返す可能性があります。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。
  
## <a name="remarks"></a>解説  
型の列の**varchar**で宣言された、 **max**指定子 (**varchar (max)**)、COL_LENGTH では値-1 が返されます。
  
## <a name="examples"></a>使用例  
次の例では、`varchar(40)` 型と `nvarchar(40)` 型の列の値を返します。
  
```sql
USE AdventureWorks2012;  
GO  
CREATE TABLE t1(c1 varchar(40), c2 nvarchar(40) );  
GO  
SELECT COL_LENGTH('t1','c1')AS 'VarChar',  
      COL_LENGTH('t1','c2')AS 'NVarChar';  
GO  
DROP TABLE t1;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
VarChar     NVarChar  
40          80  
```  
  
## <a name="see-also"></a>参照
[式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
[メタデータ関数 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/metadata-functions-transact-sql.md)  
[COL_NAME &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/col-name-transact-sql.md)  
[COLUMNPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/columnproperty-transact-sql.md)
  
  
