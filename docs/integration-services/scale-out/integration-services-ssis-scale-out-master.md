---
title: SQL Server Integration Services (SSIS) Scale Out Master | Microsoft Docs
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 07cd19a5e7a53e824d2bed3a2e2943efd7ef867b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="integration-services-ssis-scale-out-master"></a>Integration Services (SSIS) Scale Out Master
Scale Out Master では、SSISDB カタログと Scale Out Master サービスを利用して Scale Out システムが管理されます。 

SSISDB カタログでは、Scale Out Worker、パッケージ、実行に関するすべての情報が保存されます。 Scale Out Worker を有効にして、Scale Out でパッケージを実行するインターフェイスを提供します。詳細については、「[チュートリアル: Integration Services Scale Out をセットアップする](walkthrough-set-up-integration-services-scale-out.md)」、「[Integration Services でパッケージを実行する](run-packages-in-integration-services-ssis-scale-out.md)」を参照してください。

Scale Out Master サービスは、Scale Out Worker との通信を担当する Windows サービスです。 HTTPS を利用して Scale Out Worker とパッケージ実行の状態を交換し、SSISDB のデータを操作します。 

## <a name="scale-out-related-sql-views-and-stored-procedures-in-ssisdb"></a>Scale Out 関連の SQL ビューと SSISDB のストアド プロシージャ

#### <a name="views"></a>Views:
[[catalog].[master_properties]](../../integration-services/system-views/catalog-master-properties-ssisdb-database.md), [[catalog].[worker_agents]](../../integration-services/system-views/catalog-worker-agents-ssisdb-database.md).

#### <a name="stored-procedures"></a>ストアド プロシージャ:

- Scale Out Worker 管理用:  
 [[catalog].[disable_worker_agent]](../../integration-services/system-stored-procedures/catalog-disable-worker-agent-ssisdb-database.md), [[catalog].[enable_worker_agent]](../../integration-services/system-stored-procedures/catalog-enable-worker-agent-ssisdb-database.md).
- Scale Out のパッケージ実行用:   
[[catalog].[create_execution]](../../integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database.md), [[catalog].[add_execution_worker]](../../integration-services/system-stored-procedures/catalog-add-execution-worker-ssisdb-database.md), [[catalog].[start_execution]](../../integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database.md).   

## <a name="configure-sql-server-integration-services-scale-out-master-service"></a>SQL Server Integration Services Scale Out Master サービスの構成
Scale Out Master サービスは、 \<ドライバー\>:\Program Files\Microsoft SQL Server\140\DTS\Binn\MasterSettings.config ファイルを使用して構成することができます。 構成ファイルの更新後に、サービスを再起動する必要があります。


構成  |Description  |[既定値]  
---------|---------|---------
PortNumber|Scale Out Worker との通信に利用されるネットワーク ポート番号。|8391         
SSLCertThumbprint|Scale Out Worker との通信の保護に利用される SSL 証明書のサムプリント。|Scale Out Master のインストール時に指定される SSL 証明書のサムプリント         
SqlServerName|SSISDB カタログが含まれている [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] の名前。 例: ServerName\\\\InstanceName|Scale Out Master と共にインストールされる SQL Server の名前。         
CleanupCompletedJobsIntervalInMs|完了した実行ジョブを消去する間隔 (ミリ秒単位)。|43200000         
DealWithExpiredTasksIntervalInMs|期限切れ実行ジョブを処理する間隔 (ミリ秒単位)。|300000
MasterHeartbeatIntervalInMs|Scale Out Master ハートビートの間隔 (ミリ秒単位)。 これにより、Scale Out Master が SSISDB カタログでのそのオンライン ステータスを更新する間隔が指定されます。|30000
SqlConnectionTimeoutInSecs|SSISDB に接続するときの SQL 接続のタイムアウト (秒)。|15        

## <a name="view-scale-out-master-service-log"></a>Scale Out Master サービス ログを表示する
Scale Out Master サービスのログ ファイルは、\<ドライバー\>:\Users\\*[アカウント]*\AppData\Local\SSIS\ScaleOut\Master フォルダー パスにあります。 

*[アカウント]* は、Scale Out Master サービスを実行するアカウントです。 既定のアカウントは SSISScaleOutMaster140 です。
