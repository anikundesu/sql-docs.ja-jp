---
title: "共有メモリ プロトコルを使用して有効な接続文字列を作成する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connection strings [Database Engine], shared memory
- aliases [SQL Server], shared memory
ms.assetid: 5fff42e8-377f-4b40-b0c8-b02393f8a1af
caps.latest.revision: "25"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 05853deae21ee27d582f3263d6b9427ddae88a1b
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="creating-a-valid-connection-string-using-shared-memory-protocol"></a>共有メモリ プロトコルを使用した有効な接続文字列の作成
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]接続[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアントから同じコンピューターで実行されている共有メモリ プロトコルを使用します。 共有メモリには、構成可能なプロパティはありません。 共有メモリは常に最初に試行されるプロトコルであり、 **[クライアント プロトコルのプロパティ]** 一覧にある **[有効なプロトコル]** 一覧の最上位から移動することはできません。 共有プロトコルを無効にすることは可能です。これは、他のプロトコルのトラブルシューティングを行うときに便利です。  
  
 共有メモリ プロトコルを使用して別名を作成することはできませんが、共有メモリが有効になっている状態で [!INCLUDE[ssDE](../../includes/ssde-md.md)] に名前で接続すると、共有メモリ接続が作成されます。 共有メモリ接続文字列の形式は、 `lpc:<servername>[\instancename]`です。  
  
## <a name="connecting-to-the-local-server"></a>ローカル サーバーへの接続  
 クライアントと同じコンピューター上で実行されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続する場合は、サーバー名として " **(local)** " を使用することもできます。 このような指定はあいまいさを残すのでお勧めできませんが、対象のコンピューター上でクライアントを実行していることがわかっている場合には便利な機能です。 たとえば、営業スタッフは、ノート PC 上で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行し、プロジェクト データもそのノート PC に保存しておきます。このように、ネットワークに接続しないモバイル ユーザー用のアプリケーションの場合、 **(local)** に接続するクライアントは、常にそのノート PC で実行している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続することになります。 " **(local)** " の代わりに "**localhost**" またはピリオド ( **.**) を使用することもできます。  
  
## <a name="verifying-your-connection-protocol"></a>接続プロトコルの確認  
 以下のクエリは、現在の接続に使用しているプロトコルを返します。  
  
```  
SELECT net_transport   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
  
```  
  
## <a name="examples"></a>例 :  
 共有メモリ プロトコルが有効になっている場合に、以下の名前を使用すると、共有メモリを使用してローカル コンピューターに接続します。  
  
 `<servername>`  
  
 `<servername>\<instancename>`  
  
 `(local)`  
  
 `localhost`  
  
 共有メモリ接続のための別名を作成することはできません。  
  
> [!NOTE]  
>  **[サーバー]** ボックスで IP アドレスを指定すると、TCP/IP 接続になります。  
  
## <a name="see-also"></a>参照  
 [TCP/IP を使用した有効な接続文字列の作成](../../tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)   
 [名前付きパイプを使用して有効な接続文字列を作成します。](http://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f)   
 [ネットワーク プロトコルの選択](http://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)  
  
  
