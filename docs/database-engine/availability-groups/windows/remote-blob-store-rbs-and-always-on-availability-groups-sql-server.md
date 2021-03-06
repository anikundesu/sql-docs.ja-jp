---
title: "リモート BLOB ストア (RBS) と AlwaysOn 可用性グループ (SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: availability-groups
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 01a70258-d4fd-40bc-bc44-c490b5d6c420
caps.latest.revision: "15"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 69bef6ce678e9808d1a09d3af6b4e480247501a8
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="remote-blob-store-rbs-and-always-on-availability-groups-sql-server"></a>リモート BLOB ストア (RBS) と AlwaysOn 可用性グループ (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] では、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][リモート BLOB ストア (RBS)](../../../relational-databases/blob/remote-blob-store-rbs-sql-server.md) の BLOB オブジェクトの高可用性およびディザスター リカバリー ソリューションを提供できます。 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] では、可用性データベースに格納されている RBS メタデータとスキーマをセカンダリ レプリカにレプリケートすることによってこれらを保護します。 これは SharePoint コンテンツ データベースです。 一般に、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] には、この RBS メタデータが BLOB とは別に格納されます。  
  
 次のように、RBS の BLOB データの保護は BLOB ストアの場所によって異なります。  
  
|BLOB ストアの場所|可用性グループによるこの BLOB データの保護|  
|-------------------------|-----------------------------------------------------|  
|RBS メタデータを含む同じデータベース (RBS リモート FILESTREAM プロバイダーを使用して格納)|可|  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の同じインスタンスにある別のデータベース (RBS リモート FILESTREAM プロバイダーを使用して格納)|可<br /><br /> このデータベースは、RBS メタデータを含むデータベースと同じ可用性グループに含めることをお勧めします。|  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の別のインスタンスにある別のデータベース (RBS リモート FILESTREAM プロバイダーを使用して格納)|可<br /><br /> このデータベースは、別の可用性グループに含まれている必要があります。|  
|サード パーティの BLOB ストア|いいえ<br /><br /> この BLOB データを保護するには、BLOB ストア プロバイダーの高可用性メカニズムを使用します。|  
  
##  <a name="Limitations"></a> 制限事項  
  
-   RBS Maintainer は、プライマリ レプリカで対象にする必要があります。  
  
##  <a name="Recommendations"></a> 推奨事項  
  
-   可用性グループ リスナーを使用します。 詳細については、「 [可用性グループ リスナー、クライアント接続、およびアプリケーションのフェールオーバー &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md)での 1 つ以上の可用性グループの構成と管理において重要です。  
  
##  <a name="RelatedContent"></a> 関連コンテンツ  
  
-   [リモート BLOB ストアのメンテナンス](http://msdn.microsoft.com/library/gg316773\(SQL.105\).aspx) ( [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] オンライン ブック)  
  
-   [RBS Maintainer の実行](http://blogs.msdn.com/b/sqlrbs/archive/2010/03/19/running-rbs-maintainer.aspx) (ブログ)  
  
-   [FILESTREAM プロバイダーでのリモート BLOB ストレージ (RBS) の構成 (SharePoint 2010)](http://blogs.msdn.com/b/mvpawardprogram/archive/2012/04/02/configure-remote-blob-storage-rbs-with-the-filestream-provider-sharepoint-2010.aspx) (ブログ)  
  
## <a name="see-also"></a>参照  
 [AlwaysOn クライアントの接続 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/always-on-client-connectivity-sql-server.md)   
 [リモート BLOB ストア &#40;RBS&#41; &#40;SQL Server&#41;](../../../relational-databases/blob/remote-blob-store-rbs-sql-server.md)  
  
  
