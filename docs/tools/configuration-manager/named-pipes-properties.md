---
title: "名前付きパイプ プロパティ |Microsoft ドキュメント"
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
- pipes [SQL Server]
- listening [SQL Server], pipes
- pipes [SQL Server], listening on pipes
- Named Pipes [SQL Server], listening on pipes
ms.assetid: a5fd5b8e-f889-485b-89e3-d4010ec4c6ec
caps.latest.revision: "32"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5397519a722e753509161e9fc6cfcf108fc5c73a
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="named-pipes-properties"></a>[名前付きパイプのプロパティ] ダイアログ ボックス
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]使用して、**プロトコル**ページで、**名前付きパイプのプロパティ** ダイアログ ボックスを表示または変更、名前付きパイプです[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]がリッスンする、名前付きパイプ プロトコルを使用する場合。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を再起動する必要があるのは、プロトコルを有効または無効にする場合、または名前付きパイプを変更する場合です。  
  
## <a name="options"></a>オプション  
 **有効**  
 可能な値は **Yes** と **No**です。  
  
 **[パイプ名]**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がリッスンする名前付きパイプを指定します。 既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が既定のインスタンスの場合は `\\.\pipe\sql\query` と、名前付きインスタンスの場合は `\\.\pipe\MSSQL$<instancename>\sql\query` でリッスンします。 このフィールドには最大 2,047 文字まで入力できます。  
  
## <a name="creating-an-alternate-named-pipe"></a>代替名前付きパイプの作成  
 名前付きパイプを変更するには、新しいパイプ名を **[パイプ名]** ボックスに入力し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を再起動します。 **sql\query** は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が使用する名前付きパイプとしてよく知られているため、パイプを変更することによって、悪意のあるプログラムによる攻撃の危険性を減らすことができます。  
  
### <a name="example"></a>例  
 **\\\\unit\app** パイプでリッスンするには、 **.\pipe\unit\app** と入力します。  
  
 **\\\\acct** パイプでリッスンするには、 **.\pipe\acct** と入力します。  
  
## <a name="see-also"></a>参照  
 [サーバー ネットワーク プロトコルの有効化または無効化](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)   
 [ネットワーク プロトコルの選択](http://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)   
 [名前付きパイプを使用した有効な接続文字列の作成](http://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f)  
  
  
