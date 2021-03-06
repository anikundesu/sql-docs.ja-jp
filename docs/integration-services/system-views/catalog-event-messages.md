---
title: catalog.event_messages | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: a31a654f-31e9-4da1-aabf-182b07848e36
caps.latest.revision: "7"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c1569b4bb562d9342792e4ff9cda58ffe3714eb2
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="catalogeventmessages"></a>catalog.event_messages
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  操作中にログに記録されたメッセージに関する情報を表示します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|Event_message_ID|bigint|イベント メッセージの一意の ID。|  
|Operation_id|bigint|操作の種類。<br /><br /> 操作の種類の一覧については、「[catalog.operations &#40;SSISDB Database&#41;](../../integration-services/system-views/catalog-operations-ssisdb-database.md)」を参照してください。|  
|Message_time|datetimeoffset(7)|メッセージが作成された時刻。|  
|Message_type|smallint|表示されるメッセージの種類。 メッセージの種類の詳細については、「[catalog.operation_messages &#40;SSISDB データベース&#41](../../integration-services/system-views/catalog-operation-messages-ssisdb-database.md)」を参照してください。|  
|Message_source_type|smallint|メッセージのソース。|  
|message|nvarchar(max)|メッセージのテキストです。|  
|Extended_info_id|bigint|操作メッセージに関連する追加情報の ID については、[catalog.extended_operation_info &#40;SSISDB データベース&#41;](../../integration-services/system-views/catalog-extended-operation-info-ssisdb-database.md) ビューを参照してください。|  
|Package_name|nvarchar (260)|パッケージ ファイルの名前。|  
|Event_name|nvarchar (1024)|メッセージに関連付けられた実行時イベント。|  
|Message_source_name|nvarchar (4000)|メッセージのソースであるパッケージ コンポーネント。|  
|Message_source_id|nvarchar(38)|メッセージのソースの一意の ID。|  
|Subcomponent_name|nvarchar (4000)|メッセージのソースであるデータ フロー コンポーネント。<br /><br /> メッセージが [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] エンジンによって返されると、SSIS.Pipeline がこの列に表示されます。|  
|Package_path|nvarchar(max)|パッケージ内のコンポーネントの一意のパス。|  
|Execution_path|nvarchar(max)|親パッケージからコンポーネントが実行されるポイントまでの完全パス。<br /><br /> このパスは、コンポーネントの繰り返しもキャプチャします。|  
|threadID|int|メッセージがログに記録されるときに実行しているスレッドの ID。|  
|Message_code|int|メッセージに関連付けられたコード。|  
  
## <a name="remarks"></a>解説  
 このビューに表示されるメッセージ ソースの種類は次のとおりです。  
  
|**message_source_type**|Description|  
|-------------------------------|-----------------|  
|10|T-SQL や CLR ストアド プロシージャのようなエントリの API|  
|20|パッケージ (ISServerExec.exe) を実行するために使用する外部プロセス|  
|30|パッケージ レベルのオブジェクト|  
|40|制御フロー タスク|  
|50|制御フロー コンテナー|  
|60|データ フロー タスク|  
  
## <a name="permissions"></a>Permissions  
 このビューには、次の権限のいずれかが必要です。  
  
-   この操作の READ 権限  
  
-   **ssis_admin** データベース ロールのメンバーシップ。  
  
-   **sysadmin** サーバー ロールのメンバーシップ。  
  
## <a name="see-also"></a>参照  
 [catalog.event_message_context](../../integration-services/system-views/catalog-event-message-context.md)  
  
  
