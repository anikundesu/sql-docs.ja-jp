---
title: "SQLState プロパティ |Microsoft ドキュメント"
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
- Error::GetSQLState
- Error::SQLState
- Error::get_SQLState
helpviewer_keywords: SQLState property
ms.assetid: f9e25967-54b0-444d-af2a-0d2c75365d3e
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9acd68c473f43fcbc4763dc2e76d80015fdca93c
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sqlstate-property"></a>SQLState プロパティ
SQL 状態を示す、指定された[エラー](../../../ado/reference/ado-api/error-object.md)オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 5 文字を返します**文字列**ANSI SQL 標準に準拠し、エラー コードを示す値。  
  
## <a name="remarks"></a>解説  
 使用して、 **SQLState**プロバイダーを返す SQL ステートメントの処理中にエラーが発生したときに 5 文字のエラー コードを読み取るためです。 たとえば、ODBC 用の Microsoft OLE DB プロバイダーを使用して、Microsoft SQL Server データベースと、ときに SQL 状態のエラー コードを起点 ODBC では、ODBC に固有のエラーまたは Microsoft SQL Server から送信され、ODBC にマップし、エラーに基づいてエラー。 これらのエラー コードは、ANSI SQL 標準に記載されていますが、さまざまなデータ ソースによって異なる方法で実装される場合があります。  
  
## <a name="applies-to"></a>適用対象  
 [Error オブジェクト](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>参照  
 [説明、HelpContext、HelpFile、以下、数、ソース、および SQLState のプロパティの例 (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [説明、HelpContext、HelpFile、以下、数、ソース、および SQLState のプロパティの例 (vc++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
