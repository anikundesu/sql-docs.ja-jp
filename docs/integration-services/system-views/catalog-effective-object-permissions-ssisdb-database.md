---
title: "catalog.effective_object_permissions (SSISDB データベース) | Microsoft Docs"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- catalog.effective_object_permissions views [Integration Services]
- effective_object_permissions view [Integration Services]
ms.assetid: e70c4ce9-79f5-44df-ac75-6c29b6e38776
caps.latest.revision: "26"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 42d6b9da71776adfa65272499da496881f6857e2
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="catalogeffectiveobjectpermissions-ssisdb-database"></a>catalog.effective_object_permissions (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログのすべてのオブジェクトの現在のプリンシパルに対する有効な権限を表示します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|object_type|**smallint**|セキュリティ保護可能なオブジェクトの種類。 セキュリティ保護可能なオブジェクトの種類には、フォルダー (`1`)、プロジェクト (`2`)、環境 (`3`)、および操作 (`4`) があります。|  
|object_id|**bigint**|一意の識別子 (ID) またはオブジェクトの主キー。|  
|permission_type|**smallint**|権限の種類。|  
  
## <a name="remarks"></a>解説  
 このビューは、次の表に示す権限の種類を表示します。  
  
|permission_type 値|権限名|権限の説明|該当するオブジェクトの種類|  
|----------------------------|---------------------|----------------------------|-----------------------------|  
|`1`|READ|プロパティなど、オブジェクトの一部と見なされる情報をプリンシパルが読み取ることができるようにします。 プリンシパルがオブジェクト内に含まれるその他のオブジェクトのコンテンツを列挙したり、読み取ったりすることはできません。|フォルダー、プロジェクト、環境、操作|  
|`2`|MODIFY|プロパティなど、オブジェクトの一部と見なされる情報をプリンシパルが変更できるようにします。 プリンシパルがオブジェクト内に含まれるその他のオブジェクトを修正することはできません。|フォルダー、プロジェクト、環境、操作|  
|`3`|CREATE ステートメントを実行する前に、|プリンシパルがプロジェクトのすべてのパッケージを実行できるようにします。|プロジェクト|  
|`4`|MANAGE_PERMISSIONS|プリンシパルがオブジェクトに権限を割り当てることができるようにします。|フォルダー、プロジェクト、環境、操作|  
|`100`|CREATE_OBJECTS|プリンシパルがフォルダーでオブジェクトを作成できるようにします。|フォルダー|  
|`101`|READ_OBJECTS|プリンシパルがフォルダーのすべてのオブジェクトを読み取ることができるようにします。|フォルダー|  
|`102`|MODIFY_OBJECTS|プリンシパルがフォルダーのすべてのオブジェクトを変更できるようにします。|フォルダー|  
|`103`|EXECUTE_OBJECTS|プリンシパルがフォルダーのすべてのプロジェクトからすべてのパッケージを実行できるようにします。|フォルダー|  
|`104`|MANAGE_OBJECT_PERMISSIONS|プリンシパルがフォルダー内のすべてのオブジェクトに対する権限を管理できるようにします。|フォルダー|  
  
 呼び出し元が権限を持つオブジェクトだけが評価されます。 権限は、以下に基づいて計算されます。  
  
-   明示的権限  
  
-   継承された権限  
  
-   ロールのプリンシパルのメンバーシップ  
  
-   グループのプリンシパルのメンバーシップ  
  
## <a name="permissions"></a>Permissions  
 ユーザーは、ユーザー自身およびユーザーがメンバーであるロールに対してのみ有効な権限を確認できます。  
  
  
