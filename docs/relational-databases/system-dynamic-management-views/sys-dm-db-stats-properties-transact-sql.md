---
title: "sys.dm_db_stats_properties (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/05/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_db_stats_properties_TSQL
- sys.dm_db_stats_properties
- dm_db_stats_properties_TSQL
- dm_db_stats_properties
dev_langs: TSQL
helpviewer_keywords: sys.dm_db_stats_properties
ms.assetid: 8a54889d-e263-4881-9fcb-b1db410a9453
caps.latest.revision: "13"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: e2a1ebc3301372b490de9ec631c3cdb0743f264b
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmdbstatsproperties-transact-sql"></a>sys.dm_db_stats_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在の指定されたデータベース オブジェクト (テーブルまたはインデックス付きビュー) の統計情報のプロパティを返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース。 パーティション分割されたテーブルの場合と同様を参照してください[sys.dm_db_incremental_stats_properties](../../relational-databases/system-dynamic-management-views/sys-dm-db-incremental-stats-properties-transact-sql.md)です。 
 
## <a name="syntax"></a>構文  
  
```  
sys.dm_db_stats_properties (object_id, stats_id)  
```  
  
## <a name="arguments"></a>引数  
 *object_id*  
 統計のプロパティが要求された、現在のデータベース内にあるオブジェクトの ID です。 *object_ID* は **int**です。  
  
 *stats_id*  
 指定された *object_id*の統計情報の ID です。 統計 ID は、 [sys.stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md) 動的管理ビューから取得できます。 *stats_id* は **int**です。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|object_id|**int**|統計オブジェクトのプロパティを返す対象であるオブジェクト (テーブルまたはインデックス付きビュー) の ID。|  
|stats_id|**int**|統計オブジェクトの ID。 テーブルまたはインデックス付きビューで一意です。 詳細については、「[sys.stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)」を参照してください。|  
|last_updated|**datetime2**|オブジェクトが最後に更新された日付と時刻。|  
|rows|**bigint**|テーブルまたはインデックス付きビューの統計が最後に更新されたときの行の合計数。 統計がフィルター選択されている場合、またはフィルター選択されたインデックスに対応している場合は、行数がテーブルの行数よりも少なくなることがあります。|  
|rows_sampled|**bigint**|統計の計算時にサンプリングされた行の合計数。|  
|steps|**int**|ヒストグラムの区間の数。 詳細については、「 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)には含まれていません。|  
|unfiltered_rows|**bigint**|フィルター式を適用する前のテーブル内の行の合計数 (フィルター選択された統計情報の場合)。 統計がフィルター選択されていない場合は unfiltered_rows は行の列に返される値と同じです。|  
|modification_counter|**bigint**|統計情報が前回更新されてから先頭の統計列 (構築するヒストグラムの基になる列) に対して行われた変更の総数。<br /><br /> メモリ最適化テーブル: 開始[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]し、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]この列が含まれています: テーブル、前回の統計が更新されたか、または、データベースの再起動からの変更の合計数。|  
|persisted_sample_percent|**float**|サンプリングの割合が明示的に指定されていない統計の更新プログラムの使用されるサンプルのパーセンテージを永続化されます。 値がゼロの場合、永続化されたサンプルのパーセンテージが設定されていないこの統計のです。<br /><br /> **適用されます:** [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 CU4|  
  
## <a name="remarks"></a>解説  
 **sys.dm_db_stats_properties**次の条件のいずれかで空の行セットを返します。  
  
-   **object_id**または**stats_id**は NULL です。  
  
-   指定したオブジェクトが見つからないか、テーブルまたはインデックス付きビューに対応しない。  
  
-   指定した統計 ID が、指定したオブジェクト ID の既存の統計情報に対応しない。  
  
-   現在のユーザーに統計オブジェクトを表示する権限がない。  
  
 この動作により、安全な使用量の**sys.dm_db_stats_properties**クロス適用時にビューの行になど**sys.objects**と**sys.stats**です。  
  
## <a name="permissions"></a>Permissions  
 ユーザーは、統計情報列に対する select 権限を持つテーブルを所有するユーザーまたはユーザーのメンバーである必要があります、`sysadmin`固定サーバー ロール、`db_owner`固定データベース ロール、または`db_ddladmin`固定データベース ロール。  
  
## <a name="examples"></a>使用例  

### <a name="a-simple-example"></a>A. 簡単な例
次の例は、の統計を返します、 `Person.Person` AdventureWorks データベース内のテーブルです。

```
SELECT * FROM sys.dm_db_stats_properties (object_id('Person.Person'), 1);
``` 
  
### <a name="b-returning-all-statistics-properties-for-a-table"></a>B. テーブルのすべての統計プロパティを返す  
 次の例では、テーブル TEST に関して存在するすべての統計のプロパティを返します。  
  
```  
SELECT sp.stats_id, name, filter_definition, last_updated, rows, rows_sampled, steps, unfiltered_rows, modification_counter   
FROM sys.stats AS stat   
CROSS APPLY sys.dm_db_stats_properties(stat.object_id, stat.stats_id) AS sp  
WHERE stat.object_id = object_id('TEST');  
```  
  
### <a name="c-returning-statistics-properties-for-frequently-modified-objects"></a>C. 頻繁に変更されるオブジェクトの統計プロパティを返す  
 次の例では、統計が前回更新されてからの先頭列の変更が 1,000 回を超える、現在のデータベース内にあるすべてのテーブル、インデックス付きビュー、および統計を返します。  
  
```  
SELECT obj.name, obj.object_id, stat.name, stat.stats_id, last_updated, modification_counter  
FROM sys.objects AS obj   
INNER JOIN sys.stats AS stat ON stat.object_id = obj.object_id  
CROSS APPLY sys.dm_db_stats_properties(stat.object_id, stat.stats_id) AS sp  
WHERE modification_counter > 1000;  
```  
  
## <a name="see-also"></a>参照  
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [sys.stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)   
 [オブジェクト関連の動的管理ビューおよび関数 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/object-related-dynamic-management-views-and-functions-transact-sql.md)   
 [動的管理ビューおよび関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
 [sys.dm_db_incremental_stats_properties (TRANSACT-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-incremental-stats-properties-transact-sql.md)  
 [sys.dm_db_stats_histogram (TRANSACT-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md) 
  

