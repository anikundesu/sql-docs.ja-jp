---
title: "sys.database_event_session_targets (Azure SQL データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.reviewer: 
ms.service: 
ms.component: system-catalog-views
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: Azure SQL Database
ms.assetid: 38d775ee-1fe1-4820-88c6-02b2f875a66b
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0e06bf788cb8d5b2b66a1470fff431015d2df0ec
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdatabaseeventsessiontargets-azure-sql-database"></a>sys.database_event_session_targets (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  イベント セッションのイベント ターゲットごとに 1 行のデータを返します。  
  
||  
|-|  
|**適用されます**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 およびそれ以降のバージョン。|  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|イベント セッションの ID。 NULL 値は許可されません。|  
|target_id|**int**|ターゲットの ID。 ID は、イベント セッション オブジェクト内で一意です。 NULL 値は許可されません。|  
|name|**sysname**|イベント ターゲットの名前。 NULL 値は許可されません。|  
|パッケージ (package)|**sysname**|イベント ターゲットを含むイベント パッケージの名前。 NULL 値は許可されません。|  
|モジュール (module)|**sysname**|イベント ターゲットを含むモジュールの名前。 NULL 値は許可されません。|  
  
## <a name="permissions"></a>Permissions  
 サーバーに対する VIEW DATABASE STATE 権限が必要です。  
  
## <a name="remarks"></a>解説  
 このビューは、次に示すリレーションシップの基数を持ちます。  
  
||||  
|-|-|-|  
|From|変換先|リレーションシップ|  
|sys.database_event_session_targets.event_session_id|sys.database_event_sessions.event_session_id|多対一|  
  
## <a name="see-also"></a>参照  
 [拡張イベント](../../relational-databases/extended-events/extended-events.md)  
  
  
