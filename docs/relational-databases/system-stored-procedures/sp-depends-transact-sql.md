---
title: "sp_depends (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
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
- sp_depends
- sp_depends_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_depends
ms.assetid: d9934590-c6ae-4936-91c3-146055ef2c57
caps.latest.revision: "41"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: f10445e28fd8f0a23d5dcf3f11208cbb733bcc49
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spdepends-transact-sql"></a>sp_depends (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  テーブルまたはビューに従属するビューおよびプロシージャ、ビューまたはプロシージャが従属するテーブルおよびビューなど、データベース オブジェクトの従属性に関する情報を表示します。 現在のデータベース内に存在しないオブジェクトへの参照はレポートされません。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]使用して[sys.dm_sql_referencing_entities](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md)と[sys.dm_sql_referenced_entities](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md)代わりにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_depends [ @objname = ] '<object>'   
  
<object> ::=  
{  
    [ database_name. [ schema_name ] . | schema_name.  
    object_name  
}  
```  
  
## <a name="arguments"></a>引数  
 *database_name*  
 データベースの名前です。  
  
 *schema_name*  
 オブジェクトが所属するスキーマの名前を指定します。  
  
 *object_name*  
 従属性を調べるデータベース オブジェクトを指定します。 オブジェクトにはテーブル、ビュー、ストアド プロシージャ、ユーザー定義関数、またはトリガーを指定できます。 o*bject_name*は**nvarchar (776)**、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 **sp_depends** 2 つの結果セットが表示されます。  
  
 次の結果セットでオブジェクトを表示*\<オブジェクト >*によって異なります。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar (257** **)**|従属性が存在するアイテムの名前。|  
|**型**|**nvarchar (16)**|アイテムの種類。|  
|**更新**|**nvarchar (7)**|アイテムが更新されているかどうかを示します。|  
|**選択されています。**|**nvarchar (8)**|アイテムが SELECT ステートメントで使用されているかどうかを示します。|  
|**列**|**sysname**|従属性が存在する列またはパラメーター。|  
  
 次の結果セットに依存するオブジェクトを表示する*\<オブジェクト >*です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar (257** **)**|従属性が存在するアイテムの名前。|  
|**型**|**nvarchar (16)**|アイテムの種類。|  
  
## <a name="permissions"></a>Permissions  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-listing-dependencies-on-a-table"></a>A. テーブルの従属性を一覧表示する  
 次の例に依存するデータベース オブジェクトの一覧、`Sales.Customer`テーブルに、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース。 ここではスキーマ名とテーブル名の両方を指定します。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_depends @objname = N'Sales.Customer' ;  
```  
  
### <a name="b-listing-dependencies-on-a-trigger"></a>B. トリガーの従属性を一覧表示する  
 次の例では、対象のデータベース オブジェクトを表示するトリガー`iWorkOrder`によって異なります。  
  
```  
EXEC sp_depends @objname = N'AdventureWorks2012.Production.iWorkOrder' ;  
```  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.sql_dependencies &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-sql-dependencies-transact-sql.md)  
  
  
