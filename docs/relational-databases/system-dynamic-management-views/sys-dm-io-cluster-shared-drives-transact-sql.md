---
title: "sys.dm_io_cluster_shared_drives (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_io_cluster_shared_drives_TSQL
- sys.dm_io_cluster_shared_drives
- dm_io_cluster_shared_drives_TSQL
- dm_io_cluster_shared_drives
dev_langs: TSQL
helpviewer_keywords: sys.dm_io_cluster_shared_drives dynamic management view
ms.assetid: c8fcced8-c780-49dc-99bd-6beb3ca532c4
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 66e4e1de40aee22313bd8950986079e176f5278d
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmioclustershareddrives-transact-sql"></a>sys.dm_io_cluster_shared_drives (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  このビューは、現在のサーバー インスタンスがクラスター化されたサーバーの場合、各共有ドライブのドライブ名を返します。 現在のサーバー インスタンスがクラスター化されたサーバーでない場合は、空の行セットを返します。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_io_cluster_shared_drives**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**DriveName**|**nchar(2)**|クラスターの共有ディスク アレイを構成する個別のディスクを表すドライブの名前 (ドライブ文字)。 列値が許容されません。|  
|**pdw_node_id**|**int**|**適用されます**: ssPDW<br /><br /> この分布はでは、ノードの識別子。|  
  
## <a name="remarks"></a>解説  
 クラスター化が有効な場合、フェールオーバー クラスター インスタンスには、共有ディスク上にデータ ファイルとログ ファイルが置かれ、別のノードにフェールオーバーした後アクセスできるようになっている必要があります。 このビューの各行は、クラスター化された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスで使用される 1 つの共有ディスクを表します。 データを保管するためのこのインスタンスのログ ファイルはこのビューで表示されているディスクのみを使用できます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 このビューで表示されるディスクは、SQL Server インスタンスに関連付けられているクラスター リソース グループに属するディスクです。  
  
> [!NOTE]  
>  このビューは、今後のリリースでは推奨されていません。 使用することをお勧め[sys.dm_io_cluster_valid_path_names &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-valid-path-names-transact-sql.md)代わりにします。  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、sys.dm_io_cluster_shared_drives を使用して、クラスター サーバー インスタンスの共有デバイスを特定します。  
  
```  
SELECT * FROM sys.dm_io_cluster_shared_drives;  
```  
  
 これは、結果セットを示します。  
  
 DriveName  
  
 --------\-  
  
 m  
  
 n  
  
## <a name="see-also"></a>参照  
 [sys.dm_io_cluster_valid_path_names &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-valid-path-names-transact-sql.md)   
 [sys.dm_os_cluster_nodes &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-cluster-nodes-transact-sql.md)   
 [sys.fn_servershareddrives &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/sys-fn-servershareddrives-transact-sql.md)   
 [動的管理ビューおよび関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  
