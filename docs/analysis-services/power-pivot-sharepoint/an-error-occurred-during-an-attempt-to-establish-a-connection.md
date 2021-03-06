---
title: "接続の確立を試行中にエラーが発生しました |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 1b951da1-f62d-43d2-b40b-270a4a9ab92c
caps.latest.revision: "7"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0f5cf8de15fdbb9eed6fae4cf4ccd17c3d99e56d
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="an-error-occurred-during-an-attempt-to-establish-a-connection"></a>接続の確立を試行中にエラーが発生しました
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]クエリを実行する場合、このエラーが発生した[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]がないサーバー上のデータ[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]for SharePoint をインストールします。 また、SQL Server Analysis Services ([!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]) サービスが停止した場合や、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データを以前のバージョンで表示しようとした場合にも発生します。  
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|適用対象|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint|  
|製品バージョン|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|原因|データ接続に失敗しました。|  
|メッセージ テキスト|外部データ ソースへの接続を確立しようとしましたが、エラーが発生しました。 以下の接続を更新できませんでした: [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ|  
  
## <a name="explanation"></a>説明  
 SharePoint にパブリッシュされた Excel ブック内の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データのクエリを実行するときに SharePoint 環境に [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint サーバーがないか、SQL Server Analysis Services ([!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]) サービスが停止している場合は、Excel Services からこのエラーが返されます。  
  
 このエラーは、クエリ エンジンを使用できないときに [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データのスライスまたはフィルター処理を行うと発生します。  
  
## <a name="user-action"></a>ユーザーの操作  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint をインストールするか、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint がインストールされた SharePoint 環境に [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックを移動します。 詳細については、「 [PowerPivot for SharePoint 2010 のインストール](http://msdn.microsoft.com/en-us/8d47dde7-c941-4280-a934-e2fe3f9a938f)」を参照してください。  
  
 このソフトウェアがインストールされている場合は、SQL Server Analysis Services ([!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]) のインスタンスが実行されていることを確認します。 サーバーの全体管理で、 **[サーバーのサービスの管理]** を確認します。 また、管理ツールの [サービス] コンソール アプリケーションも確認します。  
  
 SQL Server 2008 R2 バージョンの [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for Excel で作成された [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックの場合、SQL Server 2008 R2 バージョンの Analysis Services OLE DB プロバイダーをインストールする必要があります。 プロバイダーをインストールし、Microsoft.AnalysisServices.ChannelTransport.dll ファイルを登録しなかった場合、このエラーが発生します。 ファイルの登録の詳細については、「 [SharePoint サーバーへの Analysis Services OLE DB プロバイダーのインストール](http://msdn.microsoft.com/en-us/2c62daf9-1f2d-4508-a497-af62360ee859)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [データ接続では Windows 認証を使用しており、ユーザーの資格情報を借用できませんでした。以下の接続を更新できませんでした: Power Pivot データ](../../analysis-services/power-pivot-sharepoint/the-data-connection-user-could-not-be-delegated.md)  
  
  
