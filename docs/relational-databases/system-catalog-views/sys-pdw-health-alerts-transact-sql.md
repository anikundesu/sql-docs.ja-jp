---
title: "sys.pdw_health_alerts (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49c01e5f-ee47-41a0-871d-35a759f50851
caps.latest.revision: "7"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0f7e05ccc9cc264faf5d4d7f563d1df028969309
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="syspdwhealthalerts-transact-sql"></a>sys.pdw_health_alerts (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  システムで発生する可能性が別のアラートのプロパティを格納します。これは、アラートのカタログ テーブルです。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|alert_id|**int**|アラートの一意の識別子。<br /><br /> このビューのキーです。|NOT NULL|  
|component_id|**int**|このアラートの対象コンポーネントの ID。 コンポーネントは、「電源装置、」などのコンポーネントの一般的な識別子は、され、インストールに固有ではありません。 参照してください[sys.pdw_health_components &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).|NOT NULL|  
|alert_name|**nvarchar (255)**|アラートの名前です。|NOT NULL|  
|state|**nvarchar (32)**|アラートの状態です。|NOT NULL<br /><br /> 有効値は次のとおりです。<br /><br /> ' Operational'<br /><br /> ' 操作不可状態 '<br /><br /> ' 低下 '<br /><br /> ' 失敗 '|  
|severity|**nvarchar (32)**|アラートの重大度。|NOT NULL<br /><br /> 有効値は次のとおりです。<br /><br /> ' 情報 '<br /><br /> 「警告」<br /><br /> ' Error'|  
|型|**nvarchar (32)**|アラートの種類。|NOT NULL<br /><br /> 有効値は次のとおりです。<br /><br /> 状況 - デバイスの状態が変更されました。<br /><br /> しきい値の値は、しきい値を超えました。|  
|description|**nvarchar (4000)**|アラートの説明です。|NOT NULL|  
|condition|**nvarchar (255)**|ときに使用される入力のしきい値を = です。 警告のしきい値の計算方法を定義します。|NULL|  
|ステータス|**nvarchar (32)**|アラートの状態|NULL|  
|condition_value|**bit**|システムの操作中に発生するアラートを許可するかどうかを示します。|NULL<br /><br /> 使用可能な値<br /><br /> 0 - アラートは生成されません。<br /><br /> 1-アラートが生成されます。|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と並列データ ウェアハウスのカタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
