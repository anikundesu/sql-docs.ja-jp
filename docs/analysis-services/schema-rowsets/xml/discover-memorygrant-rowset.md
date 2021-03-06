---
title: "DISCOVER_MEMORYGRANT 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
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
ms.assetid: d254e42d-9918-47ce-b6df-47f1f0b432dd
caps.latest.revision: "6"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 38eb6dae47c01758b3ca3b5c04794014b247b495
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="discovermemorygrant-rowset"></a>DISCOVER_MEMORYGRANT 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]サーバーで現在実行中のジョブによって実行されたクォータ付与内部メモリの一覧を返します。 サーバーでジョブが実行されているかどうかを調べるには、`Select * from $System.Discover_Jobs` を使用します。  
  
 **適用されます:**表形式モデル、多次元モデル  
  
## <a name="rowset-columns"></a>行セットの列  
 **DISCOVER_MEMORYGRANT**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|制限|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**MEMORY_ID**|**DBTYPE_I8**||メモリ クォータ付与を識別する番号。 1 つの DISCOVER_MEMORYGRANT 要求のコンテキスト内で一意です。|  
|**SPID**|**DBTYPE_I4**|必須|SPID は、`Select * from $System.Discover_Sessions` を実行することにより取得できます。|  
|**CreationTime**|**DBTYPE_I8 DBTYPE_DBTIMESTAMP**||クォータが付与された時刻。|  
|**LastRequestTime**|**DBTYPE_DBTIMESTAMP**||クォータ要求を前回変更した時刻。|  
|**MemoryUsed**|**DBTYPE_I4**||クォータに関連して使用されたメモリの量。|  
|**MemoryGranted**|**DBTYPE_I4**||メモリ クォータを取得するジョブで使用するために付与されたメモリの量。|  
|**ブロックされています。**|**DBTYPE_BOOL**||ジョブのブロック状態を示すブール値。 True は、そのジョブがブロックされており、そのクォータ要求を許可するのに十分なクォータが別のジョブから解放されるまで待機していることを示します。 False は、ジョブがそのクォータを受け取り、実行できることを示します。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>ADOMD.NET を使用した行セットのリターン  
 ADOMD.NET とスキーマ行セットを使用してメタデータを取得する場合、GetSchemaDataSet メソッドで GUID または文字列を使用してスキーマ行セット オブジェクトを参照できます。 詳細については、「 [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md)」を参照してください。  
  
 次の表に、この行セットを識別する GUID と文字列の値を示します。  
  
|引数|値|  
|--------------|-----------|  
|GUID|a07ccd23-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|MemoryGrant|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis Schema 行セット](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
