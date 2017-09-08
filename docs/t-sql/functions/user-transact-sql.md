---
title: "ユーザー (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- USER
- USER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- usernames [SQL Server]
- system-supplied usernames [SQL Server]
- USER function
- users [SQL Server], database names
- names [SQL Server], database users
- database usernames [SQL Server]
ms.assetid: 82bbbd94-870c-4c43-9ed9-d9abc767a6be
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5230769c1e41d5831d77c3711c9b5c4a215414cb
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="user-transact-sql"></a>USER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  既定値が指定されていない場合に、現在のユーザーのデータベース ユーザー名に対するシステム定義の値を、テーブルに挿入します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
USER  
```  
  
## <a name="return-types"></a>戻り値の型  
 **char**  
  
## <a name="remarks"></a>解説  
 USER では、USER_NAME システム関数と同じ機能が提供されます。  
  
 USER は、CREATE TABLE または ALTER TABLE ステートメントで DEFAULT 制約を指定して実行するか、標準的な関数として使用します。  
  
 USER では、常に現在のコンテキストの名前が返されます。 EXECUTE AS ステートメントの後に呼び出した場合は、権限を借用したコンテキストの名前が返されます。  
  
 Windows プリンシパルがグループのメンバーシップを使ってデータベースにアクセスした場合、グループの名前ではなく Windows プリンシパルの名前が返されます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-user-to-return-the-database-user-name"></a>A. USER を使用してデータベース ユーザー名を返す  
 次の例として、変数を宣言する`char`をユーザーの現在の値を代入し、テキストの説明の変数を出力します。  
  
```  
DECLARE @usr char(30)  
SET @usr = user  
SELECT 'The current user''s database username is: '+ @usr  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `-----------------------------------------------------------------------`  
  
 `The current user's database username is: dbo`  
  
 `(1 row(s) affected)`  
  
### <a name="b-using-user-with-default-constraints"></a>B. USER を DEFAULT 制約と共に使用する  
 次の例では、sales 行の販売員に対する `USER` 制約として `DEFAULT` を使用し、テーブルを作成します。  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE inventory22  
(  
 part_id int IDENTITY(100, 1) NOT NULL,  
 description varchar(30) NOT NULL,  
 entry_person varchar(30) NOT NULL DEFAULT USER   
)  
GO  
INSERT inventory22 (description)  
VALUES ('Red pencil')  
INSERT inventory22 (description)  
VALUES ('Blue pencil')  
INSERT inventory22 (description)  
VALUES ('Green pencil')  
INSERT inventory22 (description)  
VALUES ('Black pencil')  
INSERT inventory22 (description)  
VALUES ('Yellow pencil')  
GO  
```  
  
 次は、`inventory22` テーブルからすべての情報を選択するクエリです。  
  
```  
SELECT * FROM inventory22 ORDER BY part_id;  
GO  
```  
  
 次に結果セットを示します。`entry-person` の値に注意してください。  
  
 `part_id     description                    entry_person`  
  
 `----------- ------------------------------ -------------------------`  
  
 `100         Red pencil                     dbo`  
  
 `101         Blue pencil                    dbo`  
  
 `102         Green pencil                   dbo`  
  
 `103         Black pencil                   dbo`  
  
 `104         Yellow pencil                  dbo`  
  
 `(5 row(s) affected)`  
  
### <a name="c-using-user-in-combination-with-execute-as"></a>C. USER を EXECUTE AS と組み合わせて使用する  
 次の例では、権限を借用したセッションを内部で呼び出すときの、`USER` の動作を示します。  
  
```  
SELECT USER;  
GO  
EXECUTE AS USER = 'Mario';  
GO  
SELECT USER;  
GO  
REVERT;  
GO  
SELECT USER;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `DBO`  
  
 `Mario`  
  
 `DBO`  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-using-user-to-return-the-database-user-name"></a>D. USER を使用してデータベース ユーザー名を返す  
 次の例として、変数を宣言する`char`をユーザーの現在の値を代入し、テキストの説明の変数を出力します。  
  
```  
DECLARE @usr char(30)  
SET @usr = user  
SELECT 'The current user''s database username is: '+ @usr  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `-----------------------------------------------------------------------`  
  
 `The current user's database username is: dbo`  
  
 `(1 row(s) affected)`  
  
## <a name="see-also"></a>参照  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [CURRENT_TIMESTAMP & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/current-timestamp-transact-sql.md)   
 [CURRENT_USER と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/current-user-transact-sql.md)   
 [セキュリティ関数 &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)   
 [SESSION_USER と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/session-user-transact-sql.md)   
 [SYSTEM_USER & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/system-user-transact-sql.md)   
 [USER_NAME & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/user-name-transact-sql.md)  
  
  

