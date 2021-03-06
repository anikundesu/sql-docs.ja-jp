---
title: MSSQLSERVER_41030 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 41030 (Database Engine error)
ms.assetid: c85341ae-0fbf-42ae-9275-4cfe678238f0
caps.latest.revision: "6"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bb6128fc5009532100df1b35b4414a014a9f09f4
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver41030"></a>MSSQLSERVER_41030
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|イベント ID|41030|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|OPEN_CLUSTER_SUB_KEY|  
|メッセージ テキスト|Windows Server フェールオーバー クラスタリング レジストリ サブキー '%.*ls' を開くことができませんでした (エラー コード %d)。  親キーはクラスター ルート キーです。  WSFC サービスは実行されていないか、現在の状態でアクセスできない可能性があります。または、指定された引数が無効です。 対応する可用性グループが削除されている場合、このエラーが発生します。 このエラー コードの詳細については、Windows 開発ドキュメントの「システム エラー コード」を参照してください。|  
  
## <a name="explanation"></a>説明  
WSFC クラスターが破棄されると、[!INCLUDE[ssHADR](../../includes/sshadr-md.md)] に関連するすべてのレジストリ キーが削除されます。  
  
## <a name="user-action"></a>ユーザーの操作  
WSFC クラスターを再作成した後、AlwaysOn が有効になっている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの各クラスター ノードで AlwaysOn を無効にし、再度有効にします。 この作業には、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用できます。  
  
## <a name="see-also"></a>参照  
[AlwaysOn 可用性グループの有効化と無効化 &#40;SQL Server&#41;](~/database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)  
[Windows Server フェールオーバー クラスタリン &#40;WSFC&#41; と SQL Server](~/sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)  
  
