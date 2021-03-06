---
title: "sys.dm_cryptographic_provider_properties (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_cryptographic_provider_properties_TSQL
- sys.dm_cryptographic_provider_properties
- sys.dm_cryptographic_provider_properties_TSQL
- dm_cryptographic_provider_properties
dev_langs: TSQL
helpviewer_keywords: sys.dm_cryptographic_provider_properties dynamic management view
ms.assetid: 024b0095-6766-4189-a39a-d316c5ec2874
caps.latest.revision: "15"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ded9cecb8f5fca6c876e0971e80b0a3964b8aa24
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmcryptographicproviderproperties-transact-sql"></a>sys.dm_cryptographic_provider_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  登録された暗号化サービス プロバイダーの情報を返します。  
  
 
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|provider_id|**int**|暗号化サービス プロバイダーの ID 番号。|  
|guid|**uniqueidentifier**|一意のプロバイダー GUID。|  
|provider_version|**nvarchar (256)**|バージョンの形式でプロバイダー '*aa.bb.cccc.dd*' です。|  
|sqlcrypt_version|**nvarchar (256)**|メジャー バージョン、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]形式で Cryptographic API '*aa.bb.cccc.dd*' です。|  
|friendly_name|**nvarchar (2048)**|プロバイダーによって指定された名前。|  
|authentication_type|**nvarchar (256)**|WINDOWS、BASIC、または OTHER。|  
|symmetric_key_support|**tinyint**|0 (サポートされていません)<br /><br /> 1 (サポートされています)|  
|symmetric_key_export|**tinyint**|0 (サポートされていません)<br /><br /> 1 (サポートされています)|  
|symmetric_key_import|**tinyint**|0 (サポートされていません)<br /><br /> 1 (サポートされています)|  
|symmetric_key_persistance|**tinyint**|0 (サポートされていません)<br /><br /> 1 (サポートされています)|  
|asymmetric_key_support|**tinyint**|0 (サポートされていません)<br /><br /> 1 (サポートされています)|  
|asymmetric_key_export|**tinyint**|0 (サポートされていません)<br /><br /> 1 (サポートされています)|  
|symmetric_key_import|**tinyint**|0 (サポートされていません)<br /><br /> 1 (サポートされています)|  
|symmetric_key_persistance|**tinyint**|0 (サポートされていません)<br /><br /> 1 (サポートされています)|  
  
## <a name="remarks"></a>解説  
 sys.dm_cryptographic_provider_properties ビューはパブリックに表示できます。  
  
## <a name="see-also"></a>参照  
 [セキュリティ カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [拡張キー管理 &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/create-cryptographic-provider-transact-sql.md)   
 [セキュリティ関連の動的管理ビューおよび関数 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  
