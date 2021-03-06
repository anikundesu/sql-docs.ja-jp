---
title: "sys.internal_tables (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.internal_tables
- internal_tables
- sys.internal_tables_TSQL
- internal_tables_TSQL
dev_langs: TSQL
helpviewer_keywords:
- internal tables
- sys.internal_tables catalog view
ms.assetid: a5821c70-f150-4676-8476-3a31f7403dca
caps.latest.revision: "52"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cc5ab8560914be149128c55f563bc9e5b422d4d5
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysinternaltables-transact-sql"></a>sys.internal_tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  内部テーブルであるオブジェクトごとに 1 行のデータを返します。 内部テーブルはによって自動的に生成[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]さまざまな機能をサポートするためにします。 たとえば、プライマリ XML インデックスを作成する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を細分化の XML ドキュメントのデータを保持する内部テーブルが自動的に作成します。 内部テーブルに表示される、 **sys**すべてのデータベースのスキーマなど、その機能を示す、システムによって生成された一意の名前を持つ**xml_index_nodes_2021582240_32001**または**queue_messages_1977058079**  
  
 内部テーブルには、ユーザーがアクセスできるデータは含まれていません。また、そのスキーマは固定され変更できません。 内部テーブルの名前を [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで参照することはできません。 たとえば、SELECT などのステートメントを実行することはできません\*FROM  *\<sys.internal_table_name >*です。 ただし、カタログ ビューにクエリを実行して、内部テーブルのメタデータを表示することはできます。  
  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**\<Sys.objects から継承された列 >**||このビューが継承する列の一覧は、次を参照してください。 [sys.objects &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).|  
|**internal_type**|**tinyint**|内部テーブルの種類。<br /><br /> 201 = **queue_messages**<br /><br /> 202 = **xml_index_nodes**<br /><br /> 203 = **fulltext_catalog_freelist**<br /><br /> 205 = **query_notification**<br /><br /> 206 = **service_broker_map**<br /><br /> 207 = **extended_indexes** (空間インデックスなど)<br /><br /> 208 = **filestream_tombstone**<br /><br /> 209 = **change_tracking**<br /><br /> 210 = **tracked_committed_transactions**|  
|**internal_type_desc**|**nvarchar (60)**|内部テーブルの種類の説明。<br /><br /> QUEUE_MESSAGES<br /><br /> XML_INDEX_NODES<br /><br /> FULLTEXT_CATALOG_FREELIST<br /><br /> FULLTEXT_CATALOG_MAP<br /><br /> QUERY_NOTIFICATION<br /><br /> SERVICE_BROKER_MAP<br /><br /> EXTENDED_INDEXES<br /><br /> FILESTREAM_TOMBSTONE<br /><br /> CHANGE_TRACKING<br /><br /> TRACKED_COMMITTED_TRANSACTIONS|  
|**parent_id**|**int**|親の ID。スキーマのスコープが設定されているかどうかは関係ありません。 親が存在しない場合は 0 です。<br /><br /> **queue_messages** = **object_id**キューの<br /><br /> **xml_index_nodes** = **object_id** xml インデックスの<br /><br /> **fulltext_catalog_freelist** = **fulltext_catalog_id**フルテキスト カタログの<br /><br /> **fulltext_index_map** = **object_id**フルテキスト インデックスの<br /><br /> **query_notification**、または**service_broker_map** = 0<br /><br /> **extended_indexes** = **object_id**の空間インデックスなど拡張インデックスは、<br /><br /> **object_id**追跡が有効にするテーブルのテーブルの = **change_tracking**|  
|**parent_minor_id**|**int**|親のマイナー ID。<br /><br /> **xml_index_nodes** = **index_id** XML インデックスの<br /><br /> **extended_indexes** = **index_id**の空間インデックスなど拡張インデックスは、<br /><br /> 0 = **queue_messages**、 **fulltext_catalog_freelist**、 **fulltext_index_map**、 **query_notification**、 **service_broker_map**、または**change_tracking**|  
|**lob_data_space_id**|**int**|0 以外の値の場合、このテーブルのラージ オブジェクト (LOB) データを格納するデータ領域 (ファイル グループまたはパーティション構成) の ID。|  
|**filestream_data_space_id**|**int**|将来の使用のために予約されています。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="remarks"></a>解説  
 内部テーブルは、親エンティティと同じファイル グループに配置されます。 後半の例 F で示すカタログ クエリを使用して、内部テーブルが行内データ、行外データ、およびラージ オブジェクト (LOB) データに使用するページ数を返すことができます。  
  
 使用することができます、 [sp_spaceused](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)システム プロシージャを内部テーブルの領域使用状況データを返します。 **sp_spaceused**次の方法で内部テーブルの領域をレポートします。  
  
-   キュー名を指定すると、キューに関連付けられた基になる内部テーブルが参照され、そのストレージ使用量がレポートされます。  
  
-   XML インデックス、空間インデックス、フルテキスト インデックスの内部テーブルによって使用されているページに含まれる、 **index_size**列です。 列に XML インデックス、空間インデックス、およびそのオブジェクトのフルテキスト インデックスのページが含まれるテーブルまたはインデックス付きビューの名前を指定すると、**予約**と**index_size**です。  
  
## <a name="examples"></a>使用例  
 次の例では、カタログ ビューを使用して内部テーブルのメタデータにクエリを実行する方法について説明します。  
  
### <a name="a-show-internal-tables-that-inherit-columns-from-the-sysobjects-catalog-view"></a>A. sys.objects カタログ ビューから列を継承する内部テーブルを表示する  
  
```  
SELECT * FROM sys.objects WHERE type = 'IT';  
```  
  
### <a name="b-return-all-internal-table-metadata-including-that-which-is-inherited-from-sysobjects"></a>B. すべての内部テーブルのメタデータ (sys.objects から継承される内容を含む) を返す  
  
```  
SELECT * FROM sys.internal_tables;  
```  
  
### <a name="c-return-internal-table-columns-and-column-data-types"></a>C. 内部テーブルの列と列のデータ型を返す  
  
```  
SELECT SCHEMA_NAME(itab.schema_id) AS schema_name  
    ,itab.name AS internal_table_name  
    ,typ.name AS column_data_type   
    ,col.*  
FROM sys.internal_tables AS itab  
JOIN sys.columns AS col ON itab.object_id = col.object_id  
JOIN sys.types AS typ ON typ.user_type_id = col.user_type_id  
ORDER BY itab.name, col.column_id;  
```  
  
### <a name="d-return-internal-table-indexes"></a>D. 内部テーブルのインデックスを返す  
  
```  
SELECT SCHEMA_NAME(itab.schema_id) AS schema_name  
    , itab.name AS internal_table_name  
    , idx.*  
FROM sys.internal_tables AS itab  
JOIN sys.indexes AS idx ON itab.object_id = idx.object_id  
ORDER BY itab.name, idx.index_id;  
```  
  
### <a name="e-return-internal-table-statistics"></a>E. 内部テーブルの統計情報を返す  
  
```  
SELECT SCHEMA_NAME(itab.schema_id) AS schema_name  
    ,itab.name AS internal_table_name  
    , s.*  
FROM sys.internal_tables AS itab  
JOIN sys.stats AS s ON itab.object_id = s.object_id  
ORDER BY itab.name, s.stats_id;  
```  
  
### <a name="f-return-internal-table-partition-and-allocation-unit-information"></a>F. 内部テーブルのパーティションとアロケーション ユニットの情報を返す  
  
```  
SELECT SCHEMA_NAME(itab.schema_id) AS schema_name  
    ,itab.name AS internal_table_name  
    ,idx.name AS heap_or_index_name  
    ,p.*  
    ,au.*  
FROM sys.internal_tables AS itab  
JOIN sys.indexes AS idx  
--     JOIN to the heap or the clustered index  
    ON itab.object_id = idx.object_id AND idx.index_id IN (0,1)  
JOIN   sys.partitions AS p   
    ON p.object_id = idx.object_id AND p.index_id = idx.index_id  
JOIN   sys.allocation_units AS au  
--     IN_ROW_DATA (type 1) and ROW_OVERFLOW_DATA (type 3) => JOIN to partition's Hobt  
--     else LOB_DATA (type 2) => JOIN to the partition ID itself.  
ON au.container_id =    
    CASE au.type   
        WHEN 2 THEN p.partition_id   
        ELSE p.hobt_id   
    END  
ORDER BY itab.name, idx.index_id;  
```  
  
### <a name="g-return-internal-table-metadata-for-xml-indexes"></a>G. XML インデックスに関する内部テーブルのメタデータを返す  
  
```  
SELECT t.name AS parent_table  
    ,t.object_id AS parent_table_id  
    ,it.name AS internal_table_name  
    ,it.object_id AS internal_table_id  
    ,xi.name AS primary_XML_index_name  
    ,xi.index_id as primary_XML_index_id  
FROM sys.internal_tables AS it  
JOIN sys.tables AS t   
    ON it.parent_id = t.object_id  
JOIN sys.xml_indexes AS xi   
    ON it.parent_id = xi.object_id  
    AND it.parent_minor_id  = xi.index_id  
WHERE it.internal_type_desc = 'XML_INDEX_NODES';  
GO  
```  
  
### <a name="h-return-internal-table-metadata-for-service-broker-queues"></a>H. Service Broker キューに関する内部テーブルのメタデータを返す  
  
```  
SELECT q.name AS queue_name  
    ,q.object_id AS queue_id  
    ,it.name AS internal_table_name  
    ,it.object_id AS internal_table_id  
FROM sys.internal_tables AS it  
JOIN sys.service_queues  AS  q ON it.parent_id = q.object_id  
WHERE it.internal_type_desc = 'QUEUE_MESSAGES';  
GO  
```  
  
## <a name="i-return-internal-table-metadata-for-all-service-broker-services"></a>I. すべての Service Broker サービスに関する内部テーブルのメタデータを返す  
  
```  
SELECT *   
FROM tempdb.sys.internal_tables   
WHERE internal_type_desc = 'SERVICE_BROKER_MAP';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  
  
  
