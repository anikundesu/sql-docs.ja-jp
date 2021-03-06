---
title: "Analysis Services のサーバー プロパティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SSAS, configuration properties
- Analysis Services, configuration properties
- SQL Server Analysis Services, configuration properties
- configuration options [Analysis Services]
- server properties [Analysis Services]
- properties [Analysis Services], configuration
- properties [Analysis Services]
ms.assetid: 274b89cd-14ed-4666-bc13-eedf1de51e18
caps.latest.revision: "21"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 6da7af04e852c5fff10a6d33e1ab69723d79e014
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="server-properties-in-analysis-services"></a>Analysis Services のサーバー プロパティ
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]管理者がの既定のサーバー構成プロパティを変更できる、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンス。 各インスタンスには、同じサーバーの他のインスタンスとは別に設定される固有の構成プロパティがあります。  
  
 サーバーを構成するには、SQL Server Management Studio を使用するか、特定のインスタンスの msmdsrv.ini ファイルを編集します。  
 
SQL Server Management Studio のプロパティ ページには、最も頻繁に変更されるプロパティのサブセットが表示されます。 プロパティの完全な一覧は msmdsrv.ini ファイルにあります。   
  
> [!NOTE]  
>  既定のインストールでは、msmdsrv.ini は \Program Files\Microsoft SQL Server\MSAS13.MSSQLSERVER\OLAP\Config フォルダーに格納されます。
> 
> サーバー構成に影響を与える他のプロパティには、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]の配置構成プロパティが含まれます。 これらのプロパティに関する詳細については、「 [ソリューションの配置に関する構成設定の指定](../../analysis-services/multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)」を参照してください。
 
##  <a name="bkmk_config"></a> Management Studio のプロパティを構成する 
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスに接続します。  
  
2. オブジェクト エクスプローラーで、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスを右クリックし、 **[プロパティ]**をクリックします。 [全般] ページが表示され、より使用頻度の高いプロパティが表示されます。  

3.  その他のプロパティを表示するには、ページ下部にある **[すべての詳細プロパティを表示する]** チェック ボックスをオンにします。  
  
     サーバー プロパティの変更は、テーブル モードおよび多次元モードのサーバーについてのみサポートされます。 マイクロソフトのサポートから別途指示された場合を除き、 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]をインストールした場合は、必ず既定値を使用してください。  
  
     運用上またはパフォーマンス上の問題をサーバーのプロパティを通じて解消する方法については、「 [SQL Server 2008 R2 Analysis Services 操作ガイド](http://go.microsoft.com/fwlink/?LinkID=225539)」を参照してください。  
  
     サーバーのプロパティについては、Microsoft ホワイト ペーパー「 [SQL Server 2005 Analysis Services (SSAS) サーバー プロパティ](http://go.microsoft.com/fwlink/?LinkID=199102)」も参照してください。サーバーのプロパティの多くは、過去数回のリリースにわたり変更されていません。    
  
##  <a name="bkmk_msmdsrvini"></a> msmdsrv.ini のプロパティを構成する
  一部のプロパティの設定は、msmdrsrv.ini ファイルでのみ行うことができます。 詳細プロパティを表示しても設定する対象のプロパティが含まれていない場合は、msmdsrv.ini ファイルを直接編集する必要があります。
  
1.  Management Studio の [全般プロパティ] ページの **DataDir** プロパティをチェックして、Analysis Services プログラム ファイル (msmdsrv.ini を含む) の場所を確認します。

     サーバーに複数のインスタンスがある場合、変更するファイルを間違えないためにプログラム ファイルの場所を確認します。  
  
2.  プログラム ファイル フォルダーの場所にある **config** フォルダーに移動します。

3. 元のファイルに戻す必要がある場合は、ファイルのバックアップを作成します。  
  
4.  テキスト エディターを使用して、msmdsrv.ini ファイルを表示または編集します。  
  
5.  ファイルを保存し、サービスを再起動します。  
  
##  <a name="bkmk_ref"></a> サーバー プロパティ リファレンス  
  
 次のトピックでは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のさまざまな構成プロパティについて説明します。  
  
|トピック|Description|  
|-----------|-----------------|  
|[全般プロパティ](../../analysis-services/server-properties/general-properties.md)|全般プロパティには、基本プロパティと詳細プロパティの両方があり、データ ディレクトリ、バックアップ ディレクトリ、およびサーバーの他の動作を定義するプロパティが含まれます。|  
|[データ マイニング プロパティ](../../analysis-services/server-properties/data-mining-properties.md)|データ マイニング プロパティでは、どのデータ マイニング アルゴリズムを有効または無効にするかを制御します。 既定では、すべてのアルゴリズムが有効になっています。| 
|[DAX のプロパティ](../../analysis-services/server-properties/dax-properties.md)|DAX クエリに関連するプロパティを定義します。|
|DSO|DSO は現在サポートされません。 DSO のプロパティは無視されます。|  
|[機能プロパティ](../../analysis-services/server-properties/feature-properties.md)|機能プロパティは、製品の機能に関連しており、そのほとんどが詳細プロパティです。サーバー インスタンス間のリンクを制御するプロパティが含まれます。|  
|[Filestore プロパティ](../../analysis-services/server-properties/filestore-properties.md)|ファイル ストア プロパティは、高度な用途のみを対象としています。 高度なメモリ管理設定が含まれます。|  
|[ロック マネージャーのプロパティ](../../analysis-services/server-properties/lock-manager-properties.md)|ロック マネージャー プロパティでは、ロックおよびタイムアウトに関連するサーバーの動作を定義します。 これらのほとんどのプロパティは、高度な用途のみを対象としています。|  
|[ログのプロパティ](../../analysis-services/server-properties/log-properties.md)|ログ プロパティでは、サーバー上でイベントがログ記録される条件、場所、および方法を制御します。 これには、エラー ログ、例外ログ、フライト レコーダー、クエリ ログ、およびトレースが含まれます。|  
|[メモリのプロパティ](../../analysis-services/server-properties/memory-properties.md)|メモリ プロパティでは、サーバーでメモリが使用される方法を制御します。 主に高度な用途を対象としています。|  
|[ネットワーク プロパティ](../../analysis-services/server-properties/network-properties.md)|ネットワーク プロパティでは、ネットワークに関連するサーバーの動作を制御します。圧縮およびバイナリ XML を制御するプロパティが含まれます。 これらのほとんどのプロパティは、高度な用途のみを対象としています。|  
|[OLAP のプロパティ](../../analysis-services/server-properties/olap-properties.md)|OLAP プロパティでは、キューブおよびディメンションの処理、レイジー処理、データのキャッシュ、およびクエリの動作を制御します。 基本プロパティと詳細プロパティの両方が含まれます。|  
|[セキュリティのプロパティ](../../analysis-services/server-properties/security-properties.md)|セキュリティ セクションには、アクセス権を定義する基本プロパティと詳細プロパティの両方が含まれています。 管理者およびユーザーに関連する設定が含まれます。|  
|[スレッド プール プロパティ](../../analysis-services/server-properties/thread-pool-properties.md)|スレッド プール プロパティでは、サーバーによって作成されるスレッドの数を制御します。 これらは主に詳細プロパティです。|  
  
## <a name="see-also"></a>参照  
 [Analysis Services インスタンス管理](../../analysis-services/instances/analysis-services-instance-management.md)   
 [ソリューションの配置に関する構成設定の指定](../../analysis-services/multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)  
  
  
