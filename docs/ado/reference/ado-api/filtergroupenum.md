---
title: "FilterGroupEnum |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: FilterGroupEnum
helpviewer_keywords: FilterGroupEnum enumeration [ADO]
ms.assetid: b22e725e-84bd-4286-a070-290c278c3783
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d3b80757a0836fd11757c9e80c2b1650b0cb983f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="filtergroupenum"></a>FilterGroupEnum
フィルター処理するレコードのグループを指定します、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)です。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adFilterAffectedRecords**|2|最後に影響を受けるレコードのみを表示するためのフィルター[削除](../../../ado/reference/ado-api/delete-method-ado-recordset.md)、[再同期](../../../ado/reference/ado-api/resync-method.md)、 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)、または[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)呼び出します。|  
|**競合**|5|最後のバッチ更新が失敗したレコードを表示するためのフィルター。|  
|**adFilterFetchedRecords**|3|現在のキャッシュ内のレコードを表示するためのフィルター-つまり、データベースからレコードを取得するには、最後の呼び出しの結果。|  
|**adFilterNone**|0|現在のフィルターを削除し、表示するためのすべてのレコードを復元します。|  
|**行と列**|@shouldalert|変更されましたが、サーバーにまだ送信されていないレコードだけを表示するためのフィルター。 バッチ更新モードにのみ適用できます。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.FilterGroup.AFFECTEDRECORDS|  
|AdoEnums.FilterGroup.CONFLICTINGRECORDS|  
|AdoEnums.FilterGroup.FETCHEDRECORDS|  
|AdoEnums.FilterGroup.NONE|  
|AdoEnums.FilterGroup.PENDINGRECORDS|  
  
## <a name="applies-to"></a>適用対象  
 [Filter プロパティ](../../../ado/reference/ado-api/filter-property.md)
