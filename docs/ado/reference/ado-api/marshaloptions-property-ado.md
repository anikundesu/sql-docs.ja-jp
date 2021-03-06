---
title: "スレッドのプロパティ (ADO) |Microsoft ドキュメント"
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
f1_keywords: Recordset15::MarshalOptions
helpviewer_keywords: MarshalOptions property [ADO]
ms.assetid: 390c8abf-133e-40da-8b99-8f748a983e4f
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f2510c196b455e348c7b131ea9113d23df237e5c
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="marshaloptions-property-ado"></a>スレッドのプロパティ (ADO)
レコードを示す、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)サーバーにマーシャ リングされます。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、 [MarshalOptionsEnum](../../../ado/reference/ado-api/marshaloptionsenum.md)値。 既定値は**adMarshalAll**です。  
  
## <a name="remarks"></a>解説  
 クライアント側の使用時に[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)クライアントで変更されたレコードに書き戻される中間層またはマーシャ リングでパッケージ化し、インターフェイス メソッドを送信するプロセスと呼ばれる手法を使用して Web サーバースレッドまたはプロセス境界を越えてパラメーターです。 設定、**スレッド**プロパティが変更されたリモート データが、中間層または Web サーバーに再び更新するためにマーシャ リングする際にパフォーマンスを向上できます。  
  
> [!NOTE]
>  **リモートのデータ サービスの使用法**クライアント側でのみこのプロパティは使用**Recordset**です。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [スレッドのプロパティの例 (VB)](../../../ado/reference/ado-api/marshaloptions-property-example-vb.md)   
 [MarshalOptions プロパティの例 (VC++)](../../../ado/reference/ado-api/marshaloptions-property-example-vc.md)   
