---
title: "DISCOVER_DB_CONNECTIONS 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DISCOVER_DB_CONNECTIONS rowset
ms.assetid: 12a51a4e-5f3d-4449-9d94-7836fea1bc8b
caps.latest.revision: "17"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: dba000772382088eccc9c4e4e3771d7918ee305d
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="discoverdbconnections-rowset"></a>DISCOVER_DB_CONNECTIONS 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]サーバーからデータベースへの現在開いている接続に関するリソース使用状況とアクティビティ情報を提供します。  
  
## <a name="rowset-columns"></a>行セットの列  
 **DISCOVER_DB_CONNECTIONS**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CONNECTION_CATALOG_NAME**|**DBTYPE_WSTR**||現在接続されているデータベースの名前。|  
|**CONNECTION_ID**|**DBTYPE_I4**||接続を識別する一意の番号。|  
|**CONNECTION_IDLE_TIME_MS**|**DBTYPE_I8**||接続が開始されてからのアイドル時間 (ミリ秒単位)。|  
|**CONNECTION_IN_USE**|**DBTYPE_I4**||接続がアクティブ (1) かアイドル (0) かを示します。|  
|**CONNECTION_LAST_COMMAND_END_TIME**|**DBTYPE_DBTIMESTAMP**||最後のコマンドが実行を完了したときのサーバーの UTC 日時。|  
|**CONNECTION_LAST_COMMAND_START_TIME**|**DBTYPE_DBTIMESTAMP**||最後のコマンドが実行を開始したときのサーバーの UTC 日時。|  
|**CONNECTION_SERVER_NAME**|**DBTYPE_WSTR**||現在接続されているサーバーの名前。|  
|**CONNECTION_SPID**|**DBTYPE_I4**||セッション ID。|  
|**CONNECTION_START_TIME**|**DBTYPE_DBTIMESTAMP**||接続が開始されたときのサーバーの UTC 日時。|  
|**CONNECTION_USAGE_TIME_MS**|**DBTYPE_I8**||接続の開始以降に接続がアクティブであった時間 (ミリ秒単位)。|  
  
 このスキーマ行セットは並べ替えられません。  
  
> [!IMPORTANT]  
>  **DISCOVER_DB_CONNECTIONS**行セットのみ情報が表示されます、サービスがリレーショナル データ ソースに接続している場合。  
  
## <a name="restriction-columns"></a>制限の列  
 **DISCOVER_DB_CONNECTIONS**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|CONNECTION_ID|DBTYPE_I4|省略可。|  
|CONNECTION_IN_USE|DBTYPE_I4|省略可。|  
|CONNECTION_SERVER_NAME|DBTYPE_WSTR|省略可。|  
|CONNECTION_CATALOG_NAME|DBTYPE_WSTR|必須。|  
|CONNECTION_SPID|DBTYPE_I4|省略可。|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis Schema 行セット](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
