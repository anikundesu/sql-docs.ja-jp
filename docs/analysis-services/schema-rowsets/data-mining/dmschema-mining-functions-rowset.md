---
title: "DMSCHEMA_MINING_FUNCTIONS 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DMSCHEMA_MINING_FUNCTIONS
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DMSCHEMA_MINING_FUNCTIONS rowset
ms.assetid: 9ace7493-a7b1-45ca-93de-3cb2f3597017
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 37ca291ee59e345e9d62424fcb2f37e537d6c07d
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="dmschemaminingfunctions-rowset"></a>DMSCHEMA_MINING_FUNCTIONS 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]実行しているサーバーで使用できるデータ マイニング アルゴリズムでサポートされているデータ マイニング関数について説明します[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
## <a name="rowset-columns"></a>行セットの列  
 **DMSCHEMA_MINING_FUNCTIONS**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**SERVICE_NAME**|**DBTYPE_WSTR**||アルゴリズムの名前。|  
|**FUNCTION_NAME**|**DBTYPE_WSTR**||関数の名前です。|  
|**FUNCTION_SIGNATURE**|**DBTYPE_WSTR**||関数の署名。|  
|**RETURNS_TABLE**|**DBTYPE_BOOL**||**FALSE**関数がスカラー コンテンツ (など、文字の引数の長さ); を返す場合**TRUE**場合は、ヒストグラム テーブルなどのテーブルを返します。|  
|**DESCRIPTION**|**DBTYPE_WSTR**||関数についてのわかりやすい説明。|  
|**HELP_FILE**|**DBTYPE_WSTR**||この関数のマニュアルを含んでいるファイルの名前。|  
|**HELP_CONTEXT**|**DBTYPE_I4**||この関数のヘルプ コンテキスト ID。|  
  
## <a name="restriction-columns"></a>制限の列  
 **DMSCHEMA_MINING_FUNCTIONS**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**SERVICE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**FUNCTION_NAME**|**DBTYPE_WSTR**|省略可。|  
  
## <a name="see-also"></a>参照  
 [データ マイニング スキーマ行セット](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
