---
title: "Delete メソッド (ADO パラメーターのコレクション) |Microsoft ドキュメント"
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
f1_keywords:
- _DynaCollection::Delete
- _DynaCollection::raw_Delete
helpviewer_keywords: Delete method [ADO]
ms.assetid: 160c575e-df63-4ade-a2d3-5fd8f72e70cc
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 588b7c28a306cdf99baf549da3241882e9de2eb2
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="delete-method-ado-parameters-collection"></a>Delete メソッド (ADO パラメーターのコレクション)
オブジェクトを削除、[パラメーター](../../../ado/reference/ado-api/parameters-collection-ado.md)コレクション。  
  
## <a name="syntax"></a>構文  
  
```  
  
Parameters.Delete Index  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Index*  
 A**文字列**コレクション内で、削除するオブジェクトまたはオブジェクトの位置 (インデックス) の名前を含む値です。  
  
## <a name="remarks"></a>解説  
 使用して、**削除**コレクションでメソッドを使用して、コレクション内のオブジェクトの 1 つを削除できます。 このメソッドは、上でのみ使用可能な**パラメーター**のコレクション、[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクト。 使用する必要があります、[パラメーター](../../../ado/reference/ado-api/parameter-object.md)オブジェクトの[名前](../../../ado/reference/ado-api/name-property-ado.md)プロパティまたはそのコレクションのインデックスを呼び出すときに、**削除**メソッド: オブジェクト変数は有効な引数ではありません。  
  
## <a name="applies-to"></a>適用対象  
 [Parameters コレクション (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)  
  
## <a name="see-also"></a>参照  
 [Delete メソッド (ADO フィールドのコレクション)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Delete メソッド (ADO レコード セット)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [DeleteRecord メソッド (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)
