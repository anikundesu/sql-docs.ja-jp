---
title: "AllowNullsEnum |Microsoft ドキュメント"
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
f1_keywords: AllowNullsEnum
helpviewer_keywords: AllowNullsEnum enumeration [ADOX]
ms.assetid: 6acf3689-1a7f-4379-9d7f-df452ccbac27
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d8dd42fbac84831c2b31247ee5b5279c97ba2ba5
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="allownullsenum"></a>AllowNullsEnum
Null 値を持つレコードのインデックスが作成するかどうかを指定します。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adIndexNullsAllow**|0|インデックスは、キー列が null 値のエントリを許可します。 キー列に null 値を入力すると、エントリは、インデックスに挿入されます。|  
|**adIndexNullsDisallow**|@shouldalert|既定値です。 インデックスには、キー列が null 値のエントリはできません。 キー列に null 値を入力すると、エラーが発生します。|  
|**adIndexNullsIgnore**|2|インデックスは、null キーを含むエントリを挿入できません。 キー列に null 値を入力すると場合、エントリは無視され、エラーは発生しません。|  
|**adIndexNullsIgnoreAny**|4|インデックスは、いくつかのキー列が null 値を持つエントリを挿入できません。 複数の列を持つインデックス キーの列で null 値が入力した場合、エントリが無視され、エラーは発生しません。|  
  
## <a name="applies-to"></a>適用対象  
 [IndexNulls プロパティ (ADOX)](../../../ado/reference/adox-api/indexnulls-property-adox.md)
