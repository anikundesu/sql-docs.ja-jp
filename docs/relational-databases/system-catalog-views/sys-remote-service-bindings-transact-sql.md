---
title: "sys.remote_service_bindings (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sys.remote_service_bindings_TSQL
- remote_service_bindings_TSQL
- remote_service_bindings
- sys.remote_service_bindings
dev_langs: TSQL
helpviewer_keywords: sys.remote_service_bindings catalog view
ms.assetid: 4e1a885d-eed1-4993-9c87-e6fd781f437d
caps.latest.revision: "20"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ccfb729fd864449b0df9468167a76d591b7e6520
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysremoteservicebindings-transact-sql"></a>sys.remote_service_bindings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  リモート サービス バインドごとに 1 行のデータを格納するカタログ ビューです。 
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|リモート サービス バインドの名前。 Null を許容しません。|  
|**remote_service_binding_id**|**int**|リモート サービス バインドの ID。 Null を許容しません。|  
|**principal_id**|**int**|リモート サービス バインドを所有しているデータベース プリンシパルの ID。 NULL 値は許可されます。|  
|**remote_service_name**|**nvarchar (256)**|バインドが適用されるリモート サービスの名前。 NULL 値は許可されます。|  
|**service_contract_id**|**int**|バインドが適用されるコントラクトの ID。 値 0 は、このバインドがサービスのすべてのコントラクトに適用されることを表すワイルドカードです。 Null を許容しません。|  
|**remote_principal_id**|**int**|リモート サービス バインドに指定されているユーザーの ID。 Service Broker では、このユーザーが所有する証明書を使用して、指定したコントラクトに基づき、指定したサービスと通信します。 NULL 値は許可されます。|  
|**is_anonymous_on**|**bit**|リモート サービス バインドで ANONYMOUS セキュリティを使用します。 メッセージ交換を開始するユーザーの識別情報は、対象サービスに提供されません。 Null を許容しません。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
  
