---
title: "catalog.extended_operation_info (SSISDB データベース) | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: db299b45-557d-4c62-8e14-355cdb051f63
caps.latest.revision: "13"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6eaae27a96c79901693899b2e8730efd87e20864
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="catalogextendedoperationinfo-ssisdb-database"></a>catalog.extended_operation_info (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログのすべての操作に対する拡張された情報を表示します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|info_id|**bigint**|拡張された情報の一意識別子 (ID)。|  
|operation_id|**bigint**|拡張された情報に対応する操作の一意の ID。|  
|object_name|**nvarchar(260)**|オブジェクトの名前。|  
|object_type|**smallint**|操作の影響を受けるオブジェクトの種類。 オブジェクトは、フォルダー (`10`)、プロジェクト (`20`)、パッケージ (`30`)、環境 (`40`)、または実行のインスタンス (`50`) です。|  
|reference_id|**bigint**|操作で使用される参照の一意の ID。|  
|ステータス|**int**|操作の状態。 使用される可能性がある値は、作成済み (`1`)、実行中 (`2`)、取り消し済み (`3`)、失敗 (`4`)、保留中 (`5`)、予期しない終了 (`6`)、成功 (`7`)、停止 (`8`)、および完了 (`9`) です。|  
|start_time|**datetimeoffset(7)**|操作が開始された日時。|  
|end_time|**datetimeoffset(7)**|操作が終了した日時。|  
  
## <a name="remarks"></a>解説  
 1 回の操作で、複数の拡張された情報行を指定できます。  
  
## <a name="permissions"></a>Permissions  
 このビューには、次の権限のいずれかが必要です。  
  
-   この操作の READ 権限  
  
-   **ssis_admin** データベース ロールのメンバーシップ  
  
-   **sysadmin** サーバー ロールのメンバーシップ  
  
> [!NOTE]  
>  サーバー上で操作を実行する権限がある場合は、操作に関する情報を表示する権限もあります。 行レベルのセキュリティが適用されるため、表示する権限がある行のみが表示されます。  
  
  
