---
title: "DBCC SQLPERF (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SQLPERF
- DBCC_SQLPERF_TSQL
- SQLPERF_TSQL
- DBCC SQLPERF
dev_langs: TSQL
helpviewer_keywords:
- statistical information [SQL Server], transaction logs
- transaction logs [SQL Server], space usage
- space [SQL Server], transaction logs
- DBCC SQLPERF statement
ms.assetid: ec9225ce-e20f-4b03-8b3a-7bcad8a649df
caps.latest.revision: "43"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 2588cd67ae6412837914a1eb41490797b944679d
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="dbcc-sqlperf-transact-sql"></a>DBCC SQLPERF (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

すべてのデータベースを対象として、トランザクション ログ領域の使用状況に関する統計情報を提供します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]待機およびラッチ統計情報のリセットを使用することもできます。
  
**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658))、 [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] ([一部の地域でプレビュー](http://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag))
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql
DBCC SQLPERF   
(  
     [ LOGSPACE ]  
     |  
          [ "sys.dm_os_latch_stats" , CLEAR ]  
     |  
     [ "sys.dm_os_wait_stats" , CLEAR ]  
)   
     [WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>引数  
LOGSPACE  
データベースごとに、トランザクション ログの現在のサイズと使用されているログ領域の割合を返します。 この情報を利用して、トランザクション ログで使用されている領域の量を監視できます。  
  
**"** **sys.dm_os_latch_stats"、**クリア  
ラッチ統計をリセットします。 詳細については、次を参照してください。 [sys.dm_os_latch_stats &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-latch-stats-transact-sql.md). [!INCLUDE[ssSDS](../../includes/sssds-md.md)]では、このオプションは使用できません。  
  
**"sys.dm_os_wait_stats"、**クリア  
待機統計をリセットします。 詳細については、「[sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)」を参照してください。 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]では、このオプションは使用できません。  
  
WITH NO_INFOMSGS  
重大度レベル 0 から 10 のすべての情報メッセージを表示しないようにします。  
  
## <a name="result-sets"></a>結果セット  
 次の表では、結果セットの列について説明します。  
  
|列名|定義|  
|---|---|
|**データベース名**|ログ統計情報を表示するデータベースの名前。|  
|**ログのサイズ (MB)**|ログに割り当てられている現在のサイズ。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]では内部ヘッダー情報の格納用に少量のディスク容量が確保されるので、この値は最初にログ領域に割り当てられた容量よりも常に小さくなります。|  
|**ログの領域使用率 (%)**|トランザクション ログ情報の格納に使用されているログ ファイルの割合。|  
|**[状態]**|ログ ファイルの状態。 常に 0 です。|  
  
## <a name="remarks"></a>解説  
トランザクション ログには、データベースで実行された各トランザクションが記録されます。 詳細については、次を参照してください。[トランザクション ログ &#40;です。SQL Server &#41;](../../relational-databases/logs/the-transaction-log-sql-server.md).
  
## <a name="permissions"></a>Permissions  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DBCC sqlperf (logspace) を実行するには、サーバーに対する VIEW SERVER STATE 権限が必要です。 待機統計情報およびラッチ統計情報をリセットするには、サーバーに対する ALTER SERVER STATE 権限が必要です。
  
[!INCLUDE[ssSDS](../../includes/sssds-md.md)] Premium 階層には、データベースの VIEW DATABASE STATE 権限が必要です。 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Standard および Basic 階層が必要です、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]管理者アカウントです。 待機およびラッチ統計をリセットすることはできません。
  
## <a name="examples"></a>使用例  
  
### <a name="a-displaying-log-space-information-for-all-databases"></a>A. すべてのデータベースのログ領域情報を表示する  
次の例を表示`LOGSPACE`のインスタンスに含まれるすべてのデータベースの情報を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。
  
```sql  
DBCC SQLPERF(LOGSPACE);  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Database Name Log Size (MB) Log Space Used (%) Status        
------------- ------------- ------------------ -----------   
master         3.99219      14.3469            0   
tempdb         1.99219      1.64216            0   
model          1.0          12.7953            0   
msdb           3.99219      17.0132            0   
AdventureWorks 19.554688    17.748701          0  
```  
  
### <a name="b-resetting-wait-statistics"></a>B. 待機統計をリセットする  
次の例のインスタンスの待機の統計をリセットする[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。
  
```sql  
DBCC SQLPERF("sys.dm_os_wait_stats",CLEAR);  
```  
  
## <a name="see-also"></a>参照  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[sp_spaceused &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)
  
  

