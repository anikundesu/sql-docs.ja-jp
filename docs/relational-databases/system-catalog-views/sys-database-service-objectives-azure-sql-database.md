---
title: "sys.database_service_objectives (Azure SQL データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/30/2016
ms.prod: 
ms.prod_service: sql-database, sql-data-warehouse
ms.reviewer: 
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- "弾力性プール"
- "弾力性プールの管理"
f1_keywords: DATABASE_SERVICE_OBJECTIVES_TSQL
ms.assetid: cecd8c31-06c0-4aa7-85d3-ac590e6874fa
caps.latest.revision: "16"
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4d1ccfea9f9c24312d29be192e5b6497c89e7972
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdatabaseserviceobjectives-azure-sql-database"></a>sys.database_service_objectives (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

存在する場合、Azure SQL データベースまたは Azure SQL Data Warehouse edition (サービス層)、(価格レベル) のサービス目標、および弾力性プール名を返します。 Azure SQL Database サーバーの master データベースにログオンした場合は、すべてのデータベースに関する情報を返します。 Azure SQL データ ウェアハウスには、master データベースに接続する必要があります。  
  
  
 料金については、次を参照してください。 [SQL データベースのオプションとパフォーマンス: SQL Database の価格](https://azure.microsoft.com/en-us/pricing/details/sql-database/)と[SQL データ ウェアハウスの価格](https://azure.microsoft.com/pricing/details/sql-data-warehouse/)です。  
  
 サービスの設定を変更するを参照してください。 [ALTER DATABASE (Azure SQL データベース)](../../t-sql/statements/alter-database-azure-sql-database.md)と[ALTER DATABASE (Azure SQL Data Warehouse)](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md)です。  
  
 Sys.database_service_objectives ビューには、次の列が含まれています。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|database_id|int|Azure SQL Database サーバーのインスタンス内で一意で、データベースの ID。 結合可能[sys.databases &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).|  
|のエディション|sysname|データベースまたはデータ ウェアハウス用のサービス層:**基本**、**標準**、 **Premium**または**データ ウェアハウス**です。|  
|service_objective|sysname|データベースの価格レベル。 データベースが弾力性プール内にある場合を返します**ElasticPool**です。<br /><br /> **基本**階層を返します**基本**です。<br /><br /> **Standard サービス階層内の単一データベース**次のいずれかを返します。 S0、S1、S2 または S3 です。<br /><br /> **Premium 階層内の単一データベース**次を返します: P1、P2、P4、P6/P3 または P11 です。<br /><br /> **SQL Data Warehouse** DW2000 を通じて DW100 を返します。|  
|elastic_pool_name|sysname|名前、[弾力性プール](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/)にデータベースが属しています。 返します**NULL**データベースが 1 つのデータベースまたはデータ warehoue 場合。|  
  
## <a name="permissions"></a>Permissions  
 必要があります**dbManager**マスター データベースに対する権限。  データベース レベルでは、ユーザーは、作成者または所有者をする必要があります。  
  
## <a name="examples"></a>使用例  
 この例は、master データベースまたはユーザー データベースで実行できます。 クエリは、名前、サービス、およびデータベースのパフォーマンス レベルの情報を返します。  
  
```tsql  
SELECT  d.name,   
     slo.*    
FROM sys.databases d   
JOIN sys.database_service_objectives slo    
ON d.database_id = slo.database_id;  
  
```  
  
  
