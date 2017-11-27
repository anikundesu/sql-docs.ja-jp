---
title: "Service Broker の管理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: Service Broker [SMO]
ms.assetid: b29d7432-d1e5-4bb6-b544-57b3a9430f95
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c95f140f023d59e07161ac0f8841d306425b77c7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="managing-service-broker"></a>Service Broker の管理
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]SMO では、[!INCLUDE[ssSB](../../../includes/sssb-md.md)]内のオブジェクトにある、 **Microsoft.SqlServer.Management.Smo.Broker**名前空間は Microsoft.SqlServer.Smo.dll への参照が必要です。 クラス情報のサポートには、Microsoft.SqlServer.ServiceBrokerEnum.dll への参照も必要です。  
  
 SMO によって、[!INCLUDE[ssSB](../../../includes/sssb-md.md)] 実装のプログラムによる管理 (DDL) を許可する [!INCLUDE[ssSB](../../../includes/sssb-md.md)] オブジェクトのセットが提供されます。 これには、メッセージ型、コントラクト、キュー、およびサービスの定義が含まれます。 SMO はデータ操作を目的としていない管理ツールであるため、[!INCLUDE[ssSB](../../../includes/sssb-md.md)] メッセージの送受信は SMO ではサポートされていません。  
  
 SMO では、<xref:Microsoft.SqlServer.Management.Smo.Database.ServiceBroker%2A> オブジェクトが最上位レベルのクラスであり、この下に [!INCLUDE[ssSB](../../../includes/sssb-md.md)] のすべての機能が配置されます。 分散メッセージ アプリケーションに参加している各データベースに対して、[!INCLUDE[ssSB](../../../includes/sssb-md.md)] 実装が必要です。 したがって、<xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceBroker> オブジェクトは、<xref:Microsoft.SqlServer.Management.Smo.Database> オブジェクトの子となります。  
  
 <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceBroker> オブジェクトには、[!INCLUDE[ssSB](../../../includes/sssb-md.md)] 実装を定義するために使用される、次のオブジェクトのコレクションが含まれています。  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Broker.MessageType> オブジェクトは、メッセージの内容を定義するメッセージ型を表します。  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Broker.MessageTypeMapping> オブジェクトは、指定されたメッセージ交換でのメッセージの方向と型を指定するコントラクトを表します。  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceQueue> オブジェクトは、送信前および受信後にメッセージを格納します。 その他の利点に加え、同じメッセージ交換グループ内のメッセージの自動ロックなど、サービス間での非同期通信がこれらのオブジェクトによって提供されます。  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Broker.BrokerService> オブジェクトは、アドレス指定が可能なメッセージ交換エンドポイントである [!INCLUDE[ssSB](../../../includes/sssb-md.md)] サービスを表します。 [!INCLUDE[ssSB](../../../includes/sssb-md.md)] メッセージは、あるサービスから別のサービスに送信されます。 サービスによってメッセージを保持するキューが指定され、このサービスの対象とするコントラクトを指定します。  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Broker.RemoteServiceBinding>設定を表すオブジェクトを[!INCLUDE[ssSB](../../../includes/sssb-md.md)]リモート サービスと通信するときに、セキュリティと認証を使用します。  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceRoute> オブジェクトは、サービスおよびサービスが定義されているデータベースの位置情報を格納した [!INCLUDE[ssSB](../../../includes/sssb-md.md)] ルートを表します。 メッセージの配信にはルートが必要です。 既定では、各データベースに [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の現在のインスタンスとして場所を示すルートが含まれます。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.SqlServer.Management.Smo.Broker>   
 [SQL Server Service Broker (SQL Server Service Broker)](../../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  