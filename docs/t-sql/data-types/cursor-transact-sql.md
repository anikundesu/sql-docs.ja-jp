---
title: "カーソル (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords: cursor data type
ms.assetid: fbea16ef-f2cc-4734-9149-ec2598fd3cca
caps.latest.revision: "22"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b9fa1c8e8fea6aabf8fe8a0e6e84f82f7220facf
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="cursor-transact-sql"></a>cursor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

カーソルへの参照を格納している変数やストアド プロシージャの OUTPUT パラメーターを表すデータ型です。
  
## <a name="remarks"></a>解説  
変数とパラメーターを参照できる操作、**カーソル**データ型は。
-   DECLARE  *@local_variable* 設定と *@local_variable* ステートメントです。  
-   OPEN、FETCH、CLOSE、および DEALLOCATE の各カーソル ステートメント  
-   ストアド プロシージャ出力パラメーター  
-   CURSOR_STATUS 関数  
-   **Sp_cursor_list**、 **sp_describe_cursor**、 **sp_describe_cursor_tables**、および**sp_describe_cursor_columns**格納されているシステムプロシージャです。  
  
**Cursor_name**の出力列**sp_cursor_list**と**sp_describe_cursor**カーソル変数の名前を返します。
  
作成された任意の変数、**カーソル**データ型は null を許容します。
  
**カーソル**CREATE TABLE ステートメント内の列のデータ型を使用することはできません。
  
## <a name="see-also"></a>参照
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CURSOR_STATUS &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/cursor-status-transact-sql.md)  
[データ型の変換 &#40;データベース エンジン&#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE CURSOR および #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/declare-cursor-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)
  
  
