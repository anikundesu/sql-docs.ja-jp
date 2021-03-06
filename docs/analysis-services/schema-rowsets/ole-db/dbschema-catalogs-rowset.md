---
title: "DBSCHEMA_CATALOGS 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
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
apiname: DBSCHEMA_CATALOGS
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DBSCHEMA_CATALOGS rowset
ms.assetid: f02dc75d-5442-4eea-b33a-567dc816be7a
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ed421bd5b4ad15d79e1e54afb4b629d1eff02d91
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="dbschemacatalogs-rowset"></a>DBSCHEMA_CATALOGS 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]データベース管理システム (DBMS) からアクセス可能なカタログに関連付けられている物理属性を識別します。  
  
## <a name="rowset-columns"></a>行セットの列  
 **DBSCHEMA_CATALOGS**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|255|カタログ名。 null にすることはできません。|  
|**DESCRIPTION**|**DBTYPE_WSTR**||テーブルに関して人が認識できる説明。|  
|**ロール**|**DBTYPE_WSTR**||現在のユーザーが所属するロールのコンマ区切りの一覧。<br /><br /> アスタリスク (\*)、現在のユーザーがサーバーまたはデータベース管理者の場合は、ロールとして含まれます。<br /><br /> **ユーザー名**に付加されます**ロール**動的なセキュリティを使用して、ロールのいずれかの場合。|  
|**DATE_MODIFIED**|**DBTYPE_DBTIMESTAMP**||カタログの最後変更日。|  
  
 行セットが並べ替えられて**CATALOG_NAME**です。  
  
## <a name="restriction-columns"></a>制限の列  
 **DBSCHEMA_CATALOGS**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|省略可|  
  
## <a name="see-also"></a>参照  
 [OLE DB Schema 行セット](../../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)  
  
  
