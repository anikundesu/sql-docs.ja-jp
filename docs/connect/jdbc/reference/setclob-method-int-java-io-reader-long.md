---
title: "setClob (int, java.io.Reader, long) メソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 157882dd-1a96-4501-a895-46e88a49266e
caps.latest.revision: "26"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7ed6649bc445fb01f4eb68d5d3bc5afbc261778c
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="setclob-method-int-javaioreader-long"></a>setClob (int, java.io.Reader, long) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された文字数は、指定したリーダー オブジェクトを指定されたパラメーターを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setClob(int parameterIndex,  
                          java.io.Reader reader,  
                          long length)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *parameterIndex*  
  
 **Int**パラメーター インデックスを示すです。  
  
 *リーダー*  
  
 リーダー オブジェクト。  
  
 *length*  
  
 A**長い**パラメーター値の文字数を示すです。  
  
## <a name="remarks"></a>解説  
 この setClob メソッドは、java.sql.PreparedStatement インターフェイスの setClob メソッドによって指定されます。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="see-also"></a>参照  
 [setClob メソッド &#40;です。SQLServerPreparedStatement &#41;](../../../connect/jdbc/reference/setclob-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement のメンバー](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
