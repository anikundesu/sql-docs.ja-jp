---
title: "ActiveCommand プロパティ (ADO) |Microsoft ドキュメント"
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
f1_keywords: Recordset20::ActiveCommand
helpviewer_keywords: ActiveCommand property [ADO]
ms.assetid: fb4088d5-5968-42d6-aeaa-3955046bb4da
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8e5384aff9ee8646493d26272cdeaae33ab49157
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="activecommand-property-ado"></a>ActiveCommand プロパティ (ADO)
示します、[コマンド](../../../ado/reference/ado-api/command-object-ado.md)を作成した、関連付けられているオブジェクト[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 返します、**バリアント**を格納している、**コマンド**オブジェクト。 既定値は、null オブジェクト参照です。  
  
## <a name="remarks"></a>解説  
 **ActiveCommand**プロパティは読み取り専用です。  
  
 場合、**コマンド**オブジェクトが、現在の作成に使用されなかった**Recordset**、 **Null**オブジェクト参照が返されます。  
  
 このプロパティを使用して、関連付けられている検索**コマンド**オブジェクトの結果のみが指定されると**Recordset**オブジェクト。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [ActiveCommand プロパティの例 (VB)](../../../ado/reference/ado-api/activecommand-property-example-vb.md)   
 [ActiveCommand プロパティの例 (JScript)](../../../ado/reference/ado-api/activecommand-property-example-jscript.md)   
 [ActiveCommand プロパティの例 (vc++)](../../../ado/reference/ado-api/activecommand-property-example-vc.md)   
 [Command オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)
