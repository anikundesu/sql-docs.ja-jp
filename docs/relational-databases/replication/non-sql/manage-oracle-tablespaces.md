---
title: "Oracle テーブルスペースの管理 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Oracle publishing [SQL Server replication], managing tablespaces
- tablespaces [SQL Server replication]
ms.assetid: b8ea6c3b-01d6-4efc-bbfb-03b264530bbd
caps.latest.revision: "33"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 65f476ef6f6a5ae9a97124e3a26a10e1a6354a63
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="manage-oracle-tablespaces"></a>Oracle テーブルスペースの管理
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] テーブルスペースは、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のファイル グループにほぼ等しいデータベース領域の単位です。 テーブルスペースでは、個々のグループ内でデータベース オブジェクトの格納および管理が可能です。 詳細については Oracle のマニュアルを参照してください。  
  
 Oracle パブリケーションの一部としてテーブルを構成する場合、必要に応じて、レプリケーション ログ情報を格納するときに既存の Oracle テーブルスペースを使用するように指定できます。 指定しない場合、レプリケーション オブジェクトのテーブルスペースは、パブリッシャーの構成時に構成したレプリケーション管理ユーザー スキーマに関連付けられた既定のテーブルスペースとなります。  
  
 **アーティクルのログ テーブルのテーブルスペースを指定するには**   
  
-   **[アーティクルのプロパティ]** ダイアログ ボックスでテーブルスペースを指定します。 このダイアログ ボックスへのアクセスの詳細については、「 [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)」を参照してください。  
  
-   [sp_changearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md) を使用します。 **sp_changearticle**を使用するには、以下を指定します。  
  
    -   パラメーター **@publisher**のファイル グループにほぼ等しいデータベース領域の単位です。  
  
    -   パラメーター **@publication**のファイル グループにほぼ等しいデータベース領域の単位です。  
  
    -   パラメーター **@article**のファイル グループにほぼ等しいデータベース領域の単位です。  
  
    -   パラメーター **@property**のファイル グループにほぼ等しいデータベース領域の単位です。  
  
    -   パラメーター **@value**のファイル グループにほぼ等しいデータベース領域の単位です。  
  
## <a name="see-also"></a>参照  
 [Oracle パブリッシャーの構成](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Objects Created on the Oracle Publisher](../../../relational-databases/replication/non-sql/objects-created-on-the-oracle-publisher.md)  
  
  
