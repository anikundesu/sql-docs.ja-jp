---
title: "DBCC show_statistics で (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SHOW_STATISTICS_TSQL
- DBCC SHOW_STATISTICS
- SHOW_STATISTICS
- DBCC_SHOW_STATISTICS_TSQL
dev_langs: TSQL
helpviewer_keywords:
- query optimization statistics [SQL Server], densities
- histograms [SQL Server]
- statistical information [SQL Server], viewing statistics objects
- current distribution statistics
- query optimization statistics [SQL Server], histograms
- DBCC SHOW_STATISTICS statement
- distribution statistics
- statistical information [SQL Server], densities
- statistics objects
- statistical information [SQL Server], histograms
- query optimization statistics [SQL Server], viewing statistics objects
- statistical information [SQL Server], distribution
- densities [SQL Server]
- displaying distribution statistics
ms.assetid: 12be2923-7289-4150-b497-f17e76a50b2e
caps.latest.revision: "75"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 777deb8a6e479b388d0dc980b58f7b757eed1b73
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="dbcc-showstatistics-transact-sql"></a>DBCC SHOW_STATISTICS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

DBCC SHOW_STATISTICS では、テーブルまたはインデックス付きビューについての、現在のクエリの最適化に関する統計を表示します。 クエリ オプティマイザーでは、統計を使用してクエリ結果の基数や行数を推定することで、高品質のクエリ プランを作成できます。 たとえば、クエリ オプティマイザーでは、基数の推定に基づいて、クエリ プランで Index Scan 操作ではなく Index Seek 操作が使用される場合があります。この場合、リソースを大量に消費する Index Scan 操作を使用しないようにすることでパフォーマンスが向上します。
  
クエリ オプティマイザーでは、テーブルまたはインデックス付きビューの統計を統計オブジェクトに格納します。 テーブルの場合、インデックスまたはテーブル列のリストに関する統計オブジェクトが作成されます。 統計オブジェクトには、統計オブジェクト、および列間の相関関係を測定する密度ベクトルの最初のキー列のヘッダー、統計に関するメタデータを値の分布のヒストグラムが含まれます。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]統計オブジェクトのデータのいずれかと基数の推定値を計算できます。
  
DBCC SHOW_STATISTICS では、統計オブジェクトに格納されたデータに基づくヘッダー、ヒストグラム、および密度ベクトルを表示します。 この構文では、テーブルまたはインデックス付きビューを指定するときに、対象のインデックス名、統計名、または列名も指定することができます。 このトピックでは、統計の表示方法と表示される結果の意味について説明します。
  
詳細については、「 [Statistics](../../relational-databases/statistics/statistics.md)」を参照してください。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```
-- Syntax for SQL Server and Azure SQL Database  
  
DBCC SHOW_STATISTICS ( table_or_indexed_view_name , target )   
[ WITH [ NO_INFOMSGS ] < option > [ , n ] ]  
< option > :: =  
    STAT_HEADER | DENSITY_VECTOR | HISTOGRAM | STATS_STREAM  
```  
  
```
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  

DBCC SHOW_STATISTICS ( table_name , target )   
    [ WITH {STAT_HEADER | DENSITY_VECTOR | HISTOGRAM } [ ,...n ] ]  
[;]  
```  
  
## <a name="arguments"></a>引数  
 *table_or_indexed_view_name*  
 統計情報を表示するテーブルまたはインデックス付きビューの名前。  
  
 *table_name*  
 表示する統計情報を含むテーブルの名前。 テーブルには、外部テーブルをすることはできません。  
  
 *移行先*  
 統計情報を表示するインデックス、統計、または列の名前。 *ターゲット*角かっこで囲まれた 1 つの引用符、二重引用符、または引用符を使用しません。 場合*ターゲット*既存のインデックスの名前か、テーブルまたはインデックス付きビュー、target に関する統計情報に関する統計情報が返されます。 場合*ターゲット*既存の列の名前を指定し、この列に、自動的に作成された統計が存在する場合、その自動作成された統計に関する情報が返されます。 target 列に自動的に作成された統計が存在しない場合は、エラー メッセージ 2767 が返されます。  
 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、*ターゲット*列名にすることはできません。  
  
 NO_INFOMSGS  
 重大度レベル 0 から 10 のすべての情報メッセージを表示しないようにします。  
  
 STAT_HEADER |DENSITY_VECTOR |ヒストグラム |STATS_STREAM [ **、**  *n*  ]  
 これらのオプションを 1 つ以上指定すると、ステートメントによって返される結果セットが、指定のオプションに合わせて制限されます。 オプションを指定しないと、すべての統計情報が返されます。  
  
 STATS_STREAM は[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="result-sets"></a>結果セット  
次の表は、STAT_HEADER を指定した場合に結果セットに返される列を示しています。
  
|列名|Description|  
|-----------------|-----------------|  
|名前|統計オブジェクトの名前。|  
|[更新]|統計情報が最後に更新された日付と時刻。 [STATS_DATE](../../t-sql/functions/stats-date-transact-sql.md)関数は、この情報を取得することです。|  
|行数|統計情報が最後に更新された時点のテーブルまたはインデックス付きビューの行の総数。 統計がフィルター選択されている場合、またはフィルター選択されたインデックスに対応している場合は、行数がテーブルの行数よりも少なくなることがあります。 詳細については、次を参照してください。[統計](../../relational-databases/statistics/statistics.md)です。|  
|[サンプリングされた行数]|統計の計算時にサンプリングされた行の合計数。 Rows Sampled < Rows の場合、表示されるヒストグラムおよび密度の結果は、サンプリングされた行に基づいて推定されます。|  
|手順|ヒストグラムの区間の数。 各区間の範囲には、上限の列値までの列値の範囲が含まれます。 ヒストグラムの区間は、統計の最初のキー列に基づいて定義されます。 区間の最大数は 200 です。|  
|[密度]|ヒストグラムの境界値を除く、統計オブジェクトの最初のキー列のすべての値について、"1 / *distinct values* " として計算されます。 この Density の値はクエリ オプティマイザーでは使用されません。[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] より前のバージョンとの互換性を維持するために表示されます。|  
|[キーの平均の長さ]|統計オブジェクトのすべてのキー列の、値ごとの平均バイト数。|  
|String Index|Yes の場合は、統計オブジェクトに文字列の統計概要が含まれています。これにより、LIKE 演算子を使用するクエリ述語 ( `WHERE ProductName LIKE '%Bike'`など) に対する基数の推定が向上します。 文字列の概要統計情報は、ヒストグラムから個別に格納されているし、型であるときに、統計オブジェクトの最初のキー列に基づいて作成されます**char**、 **varchar**、 **nchar**、 **nvarchar**、 **varchar (max)**、 **nvarchar (max)**、**テキスト**、または**ntext。**です。|  
|[フィルター式]|統計オブジェクトに含まれるテーブル行のサブセットの述語。 NULL = フィルター選択されていない統計情報です。 フィルター選択された述語の詳細については、次を参照してください。 [Create Filtered Indexes](../../relational-databases/indexes/create-filtered-indexes.md)です。 フィルター選択された統計に関する詳細については、次を参照してください。[統計](../../relational-databases/statistics/statistics.md)です。|  
|[フィルター処理なしの行数]|フィルター式を適用する前のテーブル内の行の合計数。 [フィルター式] が NULL の場合、[フィルター処理なしの行数] は [行数] と同じになります。|  
|サンプル % を永続化|サンプリングの割合が明示的に指定されていない統計の更新プログラムの使用されるサンプルのパーセンテージを永続化されます。 値がゼロの場合、永続化されたサンプルのパーセンテージが設定されていないこの統計のです。<br /><br /> **適用されます:** [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 CU4| 
  
次の表は、DENSITY_VECTOR を指定した場合に結果セットに返される列を示しています。
  
|列名|Description|  
|-----------------|-----------------|  
|[すべての密度]|密度は "1 / *distinct values*" です。 結果には、統計オブジェクトの列の各プレフィックスに対する密度が、密度ごとに 1 行表示されます。 個別の値は、行および列プレフィックスごとの列値の個別のリストです。 たとえば、統計オブジェクトにキー列 (A, B, C) が含まれる場合、結果では列プレフィックス (A)、(A, B)、および (A, B, C) ごとに個別の値リストの密度が報告されます。 プレフィックス (A, B, C) を使用すると、これらの各リストは個別の値リスト (3, 5, 6)、(4, 4, 6)、(4, 5, 6)、(4, 5, 7) のようになります。 プレフィックス (A、B) を使用して、同じ列値がある個別の値リスト: (3, 5)、(4, 4) と (4, 5)|  
|[平均の長さ]|列プレフィックスの列値のリストを格納する平均の長さ (バイト単位)。 たとえば、リスト (3, 5, 6) の値ごとに 4 バイト必要な場合は、長さは 12 バイトになります。|  
|列|[すべての密度] および [平均の長さ] を表示するプレフィックスの列の名前。|  
  
次の表は、HISTOGRAM オプションを指定した場合に結果セットに返される列を示しています。
  
|列名|Description|  
|---|---|
|[RANGE_HI_KEY]|ヒストグラム区間の上限の列値。 この列値はキー値とも呼ばれます。|  
|RANGE_ROWS|ヒストグラム区間内 (上限は除く) に列値がある行の予測数。|  
|EQ_ROWS|ヒストグラム区間の上限と列値が等しい行の予測数。|  
|DISTINCT_RANGE_ROWS|ヒストグラム区間内 (上限は除く) にある個別の列値を持つ行の予測数。|  
|AVG_RANGE_ROWS|ヒストグラム区間内 (上限は除く) にある重複する列値を持つ行の平均数 (DISTINCT_RANGE_ROWS > 0 の場合 RANGE_ROWS / DISTINCT_RANGE_ROWS)| 
  
## <a name="remarks"></a>解説  
  
## <a name="histogram"></a>ヒストグラム  
ヒストグラムでは、データセットの個別の値ごとに出現頻度を測定します。 クエリ オプティマイザーでは、統計オブジェクトの最初のキー列の列値に基づいてヒストグラムを計算し、行を統計的にサンプリングするかテーブルまたはビュー内のすべての行でフル スキャンを実行することによって列値を選択します。 サンプリングされた行のセットからヒストグラムを作成する場合、格納される行の総数および個別の値の数は推定値であり、必ずしも整数にはなりません。
  
ヒストグラムを作成するには、クエリ オプティマイザーで列値を並べ替え、個別の列値ごとに一致する値の数を計算し、列値を最大 200 の連続したヒストグラム区間に集計します。 各区間には、上限の列値までの列値の範囲が含まれます。 この範囲には、境界値の間 (境界値自体は除く) のすべての有効な列値が含まれます。 格納される最小の列値は、最初のヒストグラム区間の上限境界値になります。
  
次の図は、6 つの区間があるヒストグラムを示しています。 最初の上限境界値の左側にある領域が最初の区間です。
  
![](../../relational-databases/system-dynamic-management-views/media/a0ce6714-01f4-4943-a083-8cbd2d6f617a.gif "a0ce6714-01f4-4943-a083-8cbd2d6f617a")
  
ヒストグラムの各区間は、以下のように表されます。
-   太線は、上限境界値 (RANGE_HI_KEY) およびその出現回数 (EQ_ROWS) を表します。  
-   RANGE_HI_KEY の左にある領域は、列値の範囲、およびそれぞれの列値の平均出現回数 (AVG_RANGE_ROWS) を表します。 最初のヒストグラム区間の AVG_RANGE_ROWS は常に 0 です。  
-   点線は、範囲内にある個別の値の総数 (DISTINCT_RANGE_ROWS) および範囲内の値の総数 (RANGE_ROWS) を推定するために使用されるサンプリングされた値を表します。 クエリ オプティマイザーでは、RANGE_ROWS および DISTINCT_RANGE_ROWS を使用して AVG_RANGE_ROWS を計算します。サンプリングされた値は格納されません。  
  
クエリ オプティマイザーでは、統計的有意性に応じてヒストグラム区間を定義します。 区間幅を最大にするアルゴリズムを使用して境界値の差を最大にし、ヒストグラムの区間の数を最小限に抑えます。 区間の最大数は 200 です。 ヒストグラムの区間の数は、境界点が 200 より少ない列でも、個別の値の数より少なくなることがあります。 たとえば、個別の値が 100 個ある列のヒストグラムの境界点が 100 より少なくなる場合もあります。
  
## <a name="density-vector"></a>密度ベクトル  
クエリ オプティマイザーでは、同一のテーブルまたはインデックス付きビューから複数の列を返すクエリに対する基数の推定を向上させるために密度を使用します。 密度ベクトルには、統計オブジェクトの列のプレフィックスごとに 1 つの密度が格納されます。 たとえば、統計オブジェクトにキー列`CustomerId`、`ItemId`と`Price`の次の列プレフィックスごとに密度が計算されます。
  
|列プレフィックス|密度の計算対象|  
|---|---|
|(CustomerId)|CustomerId の値が一致する行|  
|(CustomerId, ItemId)|CustomerId および ItemId の値が一致する行|  
|(CustomerId, ItemId, Price)|CustomerId、ItemId、および Price の値が一致する行|  
  
## <a name="restrictions"></a>制限  
 DBCC SHOW_STATISTICS では、空間インデックスおよび xVelocity メモリ最適化列ストア インデックスの統計情報は提供されません。  
  
## <a name="permissions-for-includessnoversionincludesssnoversion-mdmd-and-includesssdsincludessssds-mdmd"></a>アクセス許可[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と[!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
統計オブジェクトを表示するために、ユーザー、テーブルを所有または、ユーザーのメンバーである必要があります、`sysadmin`固定サーバー ロール、`db_owner`固定データベース ロール、または`db_ddladmin`固定データベース ロール。
  
[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]SP1 では、権限に関する制限が変更され、このコマンドを使用する SELECT 権限を持つことができます。 SELECT 権限でコマンドを実行するときは、次の要件に注意してください。
-   統計オブジェクトのすべての列に対する権限が必要です。  
-   フィルター条件がある場合は、そのすべての列に対する権限が必要です。  
-   テーブルには、行レベルのセキュリティ ポリシーを持つことはできません。  
  
この動作を無効にするには、トレース フラグ 9485 を使用します。
  
## <a name="permissions-for-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>アクセス許可[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
DBCC SHOW_STATISTICS では、次のいずれかのメンバーシップまたはテーブルに対する SELECT 権限が必要です。
-   sysadmin 固定サーバー ロール  
-   db_owner 固定データベース ロール  
-   db_ddladmin 固定データベース ロール  
  
## <a name="limitations-and-restrictions-for-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>制限事項と制約の[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
DBCC SHOW_STATISTICS では、コントロールのノード レベルでのシェル データベースに格納されている統計情報を表示します。 によって自動作成される統計が表示されない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]計算ノード上。
  
DBCC show_statistics では、テーブルの外部ではサポートされていません。
  
## <a name="examples-includessnoversionincludesssnoversion-mdmd-and-includesssdsincludessssds-mdmd"></a>例:[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と[!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
### <a name="a-returning-all-statistics-information"></a>A. すべての統計情報を返す  
次の例のすべての統計情報の表示、`AK_Address_rowguid`のインデックス、`Person.Address`テーブルに、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。
  
```t-sql
DBCC SHOW_STATISTICS ("Person.Address", AK_Address_rowguid);  
GO  
```  
  
### <a name="b-specifying-the-histogram-option"></a>B. HISTOGRAM オプションを指定する  
これによりを HISTOGRAM データ Customer_LastName を表示する統計情報が制限されます。
  
```t-sql
DBCC SHOW_STATISTICS ("dbo.DimCustomer",Customer_LastName) WITH HISTOGRAM;  
GO  
```  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="c-display-the-contents-of-one-statistics-object"></a>C. 1 つの統計オブジェクトの内容を表示します。  
 次の例では、DimCustomer テーブル Customer_LastName 統計の内容を表示します。  
  
```t-sql
-- Uses AdventureWorks  
--First, create a statistics object  
CREATE STATISTICS Customer_LastName   
ON AdventureWorksPDW2012.dbo.DimCustomer (LastName);  
GO  
DBCC SHOW_STATISTICS ("dbo.DimCustomer",Customer_LastName);  
GO  
```  
  
結果は、ヘッダー、密度ベクトル、およびヒストグラムの一部を示します。
  
![DBCC SHOW_STATISTICS の結果](../../t-sql/database-console-commands/media/aps-sql-dbccshow-statistics.JPG "DBCC SHOW_STATISTICS の結果")
  
## <a name="see-also"></a>参照  
[統計](../../relational-databases/statistics/statistics.md)  
[CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)  
[CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md)  
[DROP STATISTICS &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-statistics-transact-sql.md)  
[sp_autostats &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-autostats-transact-sql.md)  
[sp_createstats &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-createstats-transact-sql.md)  
[STATS_DATE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/stats-date-transact-sql.md)  
[UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)  
[sys.dm_db_stats_properties (TRANSACT-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-properties-transact-sql.md)  
[sys.dm_db_stats_histogram (TRANSACT-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md)   
