---
title: "sys.dm_cryptographic_provider_sessions (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sys.dm_cryptographic_provider_sessions
- dm_cryptographic_provider_sessions_TSQL
- sys.dm_cryptographic_provider_sessions_TSQL
- dm_cryptographic_provider_sessions
dev_langs: TSQL
helpviewer_keywords: sys.dm_cryptographic_provider_sessions dynamic management function
ms.assetid: 9a4de02b-1a07-4850-979a-0861fddb7f9d
caps.latest.revision: "13"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2f2f90b8dcca93b007b0dd7aa490fa468f010c98
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmcryptographicprovidersessions-transact-sql"></a>sys.dm_cryptographic_provider_sessions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  暗号プロバイダーの開いているセッションに関する情報を返します。  
 
## <a name="syntax"></a>構文  
  
```  
  
sys.dm_cryptographic_provider_sessions(session_identifier)  
```  
  
## <a name="arguments"></a>引数  
 *session_identifier*  
 返されるセッションを示す整数。  
  
 0 = 現在の接続のみ  
  
 1 = すべての暗号接続  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**provider_id**|**int**|暗号化サービス プロバイダーの ID 番号。|  
|**session_handle**|**varbytes(8)**|暗号セッション ハンドル。|  
|**id**|**nvarchar (128)**|暗号プロバイダーでの認証に使用する ID。|  
|**spid**|**短い**|接続のセッション ID SPID。 詳細については、次を参照してください。 [@@SPID &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/spid-transact-sql.md).|  
  
## <a name="remarks"></a>解説  
 **Sys.dm_cryptographic_provider_sessions**ビューは、現在の接続をパブリックに表示します。 表示するにはすべての暗号接続する必要があります、**コントロール**server 権限が許可されます。  
  
## <a name="see-also"></a>参照  
 [セキュリティ カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [拡張キー管理 &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/create-cryptographic-provider-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
