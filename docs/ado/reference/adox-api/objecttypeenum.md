---
title: "ObjectTypeEnum |Microsoft ドキュメント"
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
f1_keywords: ObjectTypeEnum
helpviewer_keywords: ObjectTypeEnum enumeration [ADOX]
ms.assetid: 3fdecfca-aa91-4596-ad98-610f1b7f840b
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b4907a7ea076a38c4f0832cf5e33b1cbcae57f15
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="objecttypeenum"></a>ObjectTypeEnum
Ownership のいずれかのアクセス許可を設定する対象のデータベース オブジェクトの種類を指定します。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adPermObjColumn**|2|オブジェクトは、列です。|  
|**adPermObjDatabase**|3|オブジェクトは、データベースです。|  
|**adPermObjProcedure**|4|オブジェクトは、プロシージャです。|  
|**adPermObjProviderSpecific**|-1|オブジェクトは、プロバイダーによって定義された型です。 場合、エラーが発生、 *ObjectType*パラメーターは**adPermObjProviderSpecific**と*ObjectTypeId*が指定されていません。|  
|**adPermObjTable**|@shouldalert|オブジェクトは、テーブルです。|  
|**adPermObjView**|5|オブジェクトは、ビューです。|  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[GetObjectOwner メソッド (ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)|[GetPermissions メソッド (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)|  
|[SetObjectOwner メソッド](../../../ado/reference/adox-api/setobjectowner-method.md)|[SetPermissions メソッド (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)|
