---
title: "catalog.packages (SSISDB データベース) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
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
- packages view [Integration Services]
- catalog.packages view [Integration Services]
ms.assetid: a634e94d-f492-4dfd-9611-a35f545106a1
caps.latest.revision: "32"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e544436126d299182760f94ef46304c334d448b6
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="catalogpackages-ssisdb-database"></a>catalog.packages (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  **SSISDB** カタログに表示されるすべてのパッケージの詳細を表示します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|package_id|**bigint**|パッケージの一意識別子 (ID) です。|  
|name|**nvarchar (256)**|パッケージの一意の名前。|  
|package_guid|**uniqueidentifier**|パッケージを識別するグローバル一意識別子 (GUID)。|  
|description|**nvarchar(1024)**|パッケージの説明 (省略可)。|  
|package_format_version|**int**|パッケージの開発に使用された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョン。|  
|version_major|**int**|パッケージのメジャー バージョン。|  
|version_minor|**int**|パッケージのマイナー バージョン。|  
|version_build|**int**|パッケージのビルド バージョンです。|  
|version_comments|**nvarchar(1024)**|パッケージのバージョンに関するコメント (省略可)。|  
|version_guid|**uniqueidentifier**|パッケージのバージョンを個別に識別する GUID。|  
|project_id|**bigint**|プロジェクトの一意な ID。|  
|entry_point|**bit**|値 `1` は、パッケージが直接起動されることを示します。 値 `0` は、パッケージが、パッケージ実行タスクと共に実行される別のパッケージによって起動されたことを示します。 既定値は `1` です。|  
|validation_status|**char(1)**|検証の状態。|  
|last_validation_time|**datetimeoffset(7)**|前回の検証操作の時刻。|  
  
## <a name="remarks"></a>解説  
 このビューは、カタログの各パッケージの行を表示します。  
  
## <a name="permissions"></a>Permissions  
 このビューには、次の権限のいずれかが必要です。  
  
-   対応するプロジェクトに対する READ 権限  
  
-   **ssis_admin** データベース ロールのメンバーシップ  
  
-   **sysadmin** サーバー ロールのメンバーシップ。  
  
> [!NOTE]  
>  プロジェクトの READ 権限がある場合は、そのプロジェクトに関連付けられたすべてのパッケージおよび環境の READ 権限もあります。 行レベルのセキュリティが適用されるため、表示する権限がある行のみが表示されます。  
  
  
