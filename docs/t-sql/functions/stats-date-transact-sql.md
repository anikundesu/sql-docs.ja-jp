---
title: "STATS_DATE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
- STATS_DATE_TSQL
- STATS_DATE
dev_langs: TSQL
helpviewer_keywords:
- statistical information [SQL Server], last time updated
- STATS_DATE function
- query optimization statistics [SQL Server], last time updated
- last time statistics updated
ms.assetid: f9ec3101-1e41-489d-b519-496a0d6089fb
caps.latest.revision: "43"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: e19ad2cc1a55f226e44197f5cc29d903952523e6
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="statsdate-transact-sql"></a>STATS_DATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  テーブルまたはインデックス付きビューの統計の最終更新日を返します。  
  
 統計の更新の詳細については、次を参照してください。[統計](../../relational-databases/statistics/statistics.md)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
STATS_DATE ( object_id , stats_id )  
```  
  
## <a name="arguments"></a>引数  
 *object_id*  
 統計を含むテーブルまたはインデックス付きビューの ID。  
  
 *stats_id*  
 統計オブジェクトの ID。  
  
## <a name="return-types"></a>戻り値の型  
 返します**datetime**成功するとします。 返します**NULL**エラーが発生します。  
  
## <a name="remarks"></a>解説  
 システム関数は、選択リストや WHERE 句のほか、式が許可される場所であればどこでも使用できます。  
  
## <a name="permissions"></a>Permissions  
 db_owner 固定データベース ロールのメンバーシップか、テーブルまたはインデックス付きビューのメタデータを表示する権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-return-the-dates-of-the-most-recent-statistics-for-a-table"></a>A. テーブルの統計の最終更新日を返す  
 次の例では、`Person.Address` テーブルの各統計オブジェクトの最終更新日を返します。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT name AS stats_name,   
    STATS_DATE(object_id, stats_id) AS statistics_update_date  
FROM sys.stats   
WHERE object_id = OBJECT_ID('Person.Address');  
GO  
```  
  
 統計、インデックスに対応する場合、 *stats_id*値で、 [sys.stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)カタログ ビューと同じ、 *index_id*値で、 [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)カタログ ビュー、および次のクエリは、上記のクエリと同じ結果を返します。 統計がインデックスに対応していない場合は sys.stats の結果には、sys.indexes の結果ではなくです。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT name AS index_name,   
    STATS_DATE(object_id, index_id) AS statistics_update_date  
FROM sys.indexes   
WHERE object_id = OBJECT_ID('Person.Address');  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-learn-when-a-named-statistics-was-last-updated"></a>B. 指定された統計の最終更新日時の説明します。  
 次の例では、DimCustomer テーブルの LastName 列に統計を作成します。 後の日付の統計情報を表示するクエリを実行します。 次に、統計の更新プログラムおよび更新された日付を表示するには、もう一度クエリを実行します。  
  
```  
  
--First, create a statistics object  
USE AdventureWorksPDW2012;  
GO  
CREATE STATISTICS Customer_LastName_Stats  
ON AdventureWorksPDW2012.dbo.DimCustomer (LastName)  
WITH SAMPLE 50 PERCENT;  
GO  
  
--Return the date when Customer_LastName_Stats was last updated  
USE AdventureWorksPDW2012;  
GO  
SELECT stats_id, name AS stats_name,   
    STATS_DATE(object_id, stats_id) AS statistics_date  
FROM sys.stats s  
WHERE s.object_id = OBJECT_ID('dbo.DimCustomer')  
    AND s.name = 'Customer_LastName_Stats';  
GO  
  
--Update Customer_LastName_Stats so it will have a different timestamp in the next query  
GO  
UPDATE STATISTICS dbo.dimCustomer (Customer_LastName_Stats);  
  
--Return the date when Customer_LastName_Stats was last updated.  
SELECT stats_id, name AS stats_name,   
    STATS_DATE(object_id, stats_id) AS statistics_date  
FROM sys.stats s  
WHERE s.object_id = OBJECT_ID('dbo.DimCustomer')  
    AND s.name = 'Customer_LastName_Stats';  
GO  
  
```  
  
### <a name="c-view-the-date-of-the-last-update-for-all-statistics-on-a-table"></a>C. テーブルのすべての統計情報の最後の更新の日付を表示します。  
 この例は、DimCustomer テーブル上の各統計オブジェクトが最後に更新されたときの日付を返します。  
  
```  
--Return the dates all statistics on the table were last updated.  
SELECT stats_id, name AS stats_name,   
    STATS_DATE(object_id, stats_id) AS statistics_date  
FROM sys.stats s  
WHERE s.object_id = OBJECT_ID('dbo.DimCustomer');  
GO  
```  
  
 統計、インデックスに対応する場合、 *stats_id*値で、 [sys.stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)カタログ ビューと同じ、 *index_id*値で、 [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)カタログ ビュー、および次のクエリは、上記のクエリと同じ結果を返します。 統計がインデックスに対応していない場合は sys.stats の結果には、sys.indexes の結果ではなくです。  
  
```  
USE AdventureWorksPDW2012;  
GO  
SELECT name AS index_name,   
    STATS_DATE(object_id, index_id) AS statistics_update_date  
FROM sys.indexes   
WHERE object_id = OBJECT_ID('dbo.DimCustomer');  
GO  
```  
  
## <a name="see-also"></a>参照  
 [システム関数 &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)   
 [sp_autostats &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-autostats-transact-sql.md)   
 [統計](../../relational-databases/statistics/statistics.md)  
  
  

