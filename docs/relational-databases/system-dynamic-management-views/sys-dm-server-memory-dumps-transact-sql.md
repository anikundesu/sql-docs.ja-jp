---
title: "sys.dm_server_memory_dumps (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sys.dm_server_memory_dumps_TSQL
- dm_server_memory_dumps_TSQL
- dm_server_memory_dumps
- sys.dm_server_memory_dumps
dev_langs: TSQL
helpviewer_keywords: sys.dm_server_memory_dumps dynamic management view
ms.assetid: 41782719-f54d-4e11-941a-c050c7576e23
caps.latest.revision: "6"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cd4af6e42415814c6fc0771346f94a5283a41730
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmservermemorydumps-transact-sql"></a>sys.dm_server_memory_dumps (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  によって生成されたメモリ ダンプ ファイルごとに 1 つの行を返します、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]です。 この動的管理ビューを使用して、潜在的な問題のトラブルシューティングを行います。  
 
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**ファイル名**|**nvarchar (256)**|メモリ ダンプ ファイルのパスおよび名前。 null にすることはできません。|  
|**creation_time**|**datetimeoffset (7)**|日付と時刻、ファイルが作成されました。 null にすることはできません。|  
|**size_in_bytes**|**bigint**|ファイルのサイズ (バイト単位)。 NULL 値が許可されます。|  
  
## <a name="general-remarks"></a>全般的な解説  
 ダンプの種類として、ミニダンプ、すべてのスレッドのダンプ、または完全なダンプを使用できます。 ファイルの拡張子は .mdmp です。  
  
## <a name="security"></a>セキュリティ  
 ダンプ ファイルには機密情報が含まれている場合があります。 機密情報を保護するには、アクセス制御リスト (ACL) を使用してこのファイルへのアクセスを制限するか、アクセスが制限されたフォルダーにファイルをコピーすることができます。 たとえば、デバッグ ファイルを Microsoft サポート サービスを送信する前に、機密情報や機密情報を削除することを勧めします。  
  
### <a name="permissions"></a>Permissions  
 VIEW SERVER STATE 権限が必要です。  
  
  
