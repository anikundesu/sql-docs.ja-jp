---
title: "NamedParameters プロパティ (ADO) |Microsoft ドキュメント"
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
f1_keywords: _Command::NamedParameters
helpviewer_keywords: NamedParameters property [ADO]
ms.assetid: 42409387-026c-435f-a9b1-bf4167095875
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 357cfc37c90822ca97ae5ca1349f0bc6743d4859
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="namedparameters-property-ado"></a>NamedParameters プロパティ (ADO)
パラメーター名をプロバイダーに渡す必要があるかどうかを示します。  
  
## <a name="remarks"></a>解説  
 ADO がの値を渡しますこのプロパティが true の場合、**名前**内の各パラメーターのプロパティ、**パラメーター**のコレクション、[コマンド オブジェクト](../../../ado/reference/ado-api/command-object-ado.md)です。 プロバイダーでパラメーターに一致するパラメーター名を使用して、 **CommandText**または**CommandStream**プロパティです。 このプロパティが false の場合 (既定値) は、パラメーター名は無視され、プロバイダーでは、パラメーターの順序を使用して、パラメーターに値を照合する、 **CommandText**または**CommandStream**プロパティです。  
  
## <a name="applies-to"></a>適用対象  
 [Command オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [CommandText プロパティ (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [CommandStream プロパティ (ADO)](../../../ado/reference/ado-api/commandstream-property-ado.md)   
 [Parameters コレクション (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)
