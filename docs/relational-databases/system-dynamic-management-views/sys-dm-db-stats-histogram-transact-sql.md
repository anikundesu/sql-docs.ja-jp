---
title: "sys.dm_db_stats_histogram (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sys.dm_db_stats_histogram
- sys.dm_db_stats_histogram_TSQL
- dm_db_stats_histogram
- dm_db_stats_histogram_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_db_stats_histogram dynamic management function
ms.assetid: 1897fd4a-8d51-461e-8ef2-c60be9e563f2
caps.latest.revision: "11"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 93aec7a71f3522114bc9ef6c2d19edaccaac2e57
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysdmdbstatshistogram-transact-sql"></a>sys.dm_db_stats_histogram (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

現在の指定されたデータベース オブジェクト (テーブルまたはインデックス付きビュー) の統計ヒストグラムを返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース。 ような`DBCC SHOW_STATISTICS WITH HISTOGRAM`します。

> [!NOTE] 
> この DMF は以降で利用可能な[!INCLUDE[ssSQL15](../../includes/ssSQL15-md.md)]SP1 CU2

## <a name="syntax"></a>構文  
  
```  
sys.dm_db_stats_histogram (object_id, stats_id)  
```  
  
## <a name="arguments"></a>引数  
 *object_id*  
 統計のプロパティが要求された、現在のデータベース内にあるオブジェクトの ID です。 *object_ID* は **int**です。  
  
 *stats_id*  
 指定された *object_id*の統計情報の ID です。 統計 ID は、 [sys.stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md) 動的管理ビューから取得できます。 *stats_id* は **int**です。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|object_id |**int**|統計オブジェクトのプロパティを返す対象であるオブジェクト (テーブルまたはインデックス付きビュー) の ID。|  
|stats_id |**int**|統計オブジェクトの ID。 テーブルまたはインデックス付きビューで一意です。 詳細については、「[sys.stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)」を参照してください。|  
|step_number |**int** |ヒストグラムのステップの数。 |
|range_high_key |**sql_variant** |ヒストグラム区間の上限の列値。 この列値はキー値とも呼ばれます。|
|range_rows |**real** |ヒストグラム区間内 (上限は除く) に列値がある行の予測数。 |
|equal_rows |**real** |ヒストグラム区間の上限と列値が等しい行の予測数。 |
|distinct_range_rows |**bigint** |ヒストグラム区間内 (上限は除く) にある個別の列値を持つ行の予測数。 |
|average_range_rows |**real** |上限を除く、ヒストグラムのステップ内の重複する列の値を持つ行の数の平均値 (`RANGE_ROWS / DISTINCT_RANGE_ROWS`の`DISTINCT_RANGE_ROWS > 0`)。 |
  
 ## <a name="remarks"></a>解説  
 
 結果セット`sys.dm_db_stats_histogram`のような情報を返します`DBCC SHOW_STATISTICS WITH HISTOGRAM`も含まれていますと`object_id`、 `stats_id`、および`step_number`です。

 列`range_high_key`sql_variant データ型を使用する必要があります`CAST`または`CONVERT`場合は、述語が非文字列定数と比較します。

### <a name="histogram"></a>ヒストグラム
  
 ヒストグラムでは、データセットの個別の値ごとに出現頻度を測定します。 クエリ オプティマイザーでは、統計オブジェクトの最初のキー列の列値に基づいてヒストグラムを計算し、行を統計的にサンプリングするかテーブルまたはビュー内のすべての行でフル スキャンを実行することによって列値を選択します。 サンプリングされた行のセットからヒストグラムを作成する場合、格納される行の総数および個別の値の数は推定値であり、必ずしも整数にはなりません。  
  
 ヒストグラムを作成するには、クエリ オプティマイザーで列値を並べ替え、個別の列値ごとに一致する値の数を計算し、列値を最大 200 の連続したヒストグラム区間に集計します。 各区間には、上限の列値までの列値の範囲が含まれます。 この範囲には、境界値の間 (境界値自体は除く) のすべての有効な列値が含まれます。 格納される最小の列値は、最初のヒストグラム区間の上限境界値になります。  
  
 次の図は、6 つの区間があるヒストグラムを示しています。 最初の上限境界値の左側にある領域が最初の区間です。  
  
 ![](../../relational-databases/system-dynamic-management-views/media/a0ce6714-01f4-4943-a083-8cbd2d6f617a.gif "a0ce6714-01f4-4943-a083-8cbd2d6f617a")  
  
 ヒストグラムの各区間は、以下のように表されます。  
  
-   太字の行が、上限境界値を表します (*range_high_key*) とそれが発生した回数 (*equal_rows*)  
  
-   領域が左*range_high_key*列の値と各列の値が発生した時間の平均数の範囲を表します (*average_range_rows*)。 *Average_range_rows*最初のヒストグラムのステップは常に 0 です。  
  
-   点線は、範囲内の個別の値の合計数を推定するために使用するサンプルの値を表す (*distinct_range_rows*) と、範囲の値の合計数 (*range_rows*)。 クエリ オプティマイザーで使用*range_rows*と*distinct_range_rows*を計算する*average_range_rows*サンプリングされた値は格納されません。  
  
 クエリ オプティマイザーでは、統計的有意性に応じてヒストグラム区間を定義します。 区間幅を最大にするアルゴリズムを使用して境界値の差を最大にし、ヒストグラムの区間の数を最小限に抑えます。 区間の最大数は 200 です。 ヒストグラムの区間の数は、境界点が 200 より少ない列でも、個別の値の数より少なくなることがあります。 たとえば、個別の値が 100 個ある列のヒストグラムの境界点が 100 より少なくなる場合もあります。  
  
## <a name="permissions"></a>Permissions  

ユーザーは、統計情報列に対する select 権限を持つテーブルを所有するユーザーまたはユーザーのメンバーである必要があります、`sysadmin`固定サーバー ロール、`db_owner`固定データベース ロール、または`db_ddladmin`固定データベース ロール。

## <a name="examples"></a>使用例  

### <a name="a-simple-example"></a>A. 簡単な例    
次の例では、作成し、単純なテーブルを追加します。 統計を作成し、`Country_Name`列です。

```tsql
CREATE TABLE Country
(Country_ID int IDENTITY PRIMARY KEY,
Country_Name varchar(120) NOT NULL);
INSERT Country (Country_Name) VALUES ('Canada'), ('Denmark'), ('Iceland'), ('Peru');

CREATE STATISTICS Country_Stats  
    ON Country (Country_Name) ;  
```   
主キーが占める`stat_id`番号は 1、ためコール`sys.dm_db_stats_histogram`の`stat_id`番号を返すための統計ヒストグラム、2、`Country`テーブル。    
```tsql     
SELECT * FROM sys.dm_db_stats_histogram(OBJECT_ID('Country'), 2);
```


### <a name="b-useful-query"></a>B. 便利なクエリは:   
```tsql  
SELECT hist.step_number, hist.range_high_key, hist.range_rows, 
    hist.equal_rows, hist.distinct_range_rows, hist.average_range_rows
FROM sys.stats AS s
CROSS APPLY sys.dm_db_stats_histogram(s.[object_id], s.stats_id) AS hist
WHERE s.[name] = N'<statistic_name>';
```

### <a name="c-useful-query"></a>C. 便利なクエリは:
次の例は、テーブルから選択`Country`列の述語で`Country_Name`です。

```tsql  
SELECT * FROM Country 
WHERE Country_Name = 'Canada';
```

次の例は、以前に作成された統計テーブルに`Country`と列`Country_Name`上記のクエリで述語に一致するヒストグラムのステップにします。

```tsql  
SELECT ss.name, ss.stats_id, shr.steps, shr.rows, shr.rows_sampled, 
    shr.modification_counter, shr.last_updated, sh.range_rows, sh.equal_rows
FROM sys.stats ss
INNER JOIN sys.stats_columns sc 
    ON ss.stats_id = sc.stats_id AND ss.object_id = sc.object_id
INNER JOIN sys.all_columns ac 
    ON ac.column_id = sc.column_id AND ac.object_id = sc.object_id
CROSS APPLY sys.dm_db_stats_properties(ss.object_id, ss.stats_id) shr
CROSS APPLY sys.dm_db_stats_histogram(ss.object_id, ss.stats_id) sh
WHERE ss.[object_id] = OBJECT_ID('Country') 
    AND ac.name = 'Country_Name'
    AND sh.range_high_key = CAST('Canada' AS CHAR(8));
```
  
## <a name="see-also"></a>参照  

[DBCC show_statistics で (TRANSACT-SQL)](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
[オブジェクト関連の動的管理ビューおよび関数 (TRANSACT-SQL)](../../relational-databases/system-dynamic-management-views/object-related-dynamic-management-views-and-functions-transact-sql.md)  
[sys.dm_db_stats_properties (TRANSACT-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-properties-transact-sql.md)  
