---
title: "getSQLXML (java.lang.String) メソッド (SQLServerResultSet) |Microsoft ドキュメント"
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
ms.assetid: ab9c7b10-026f-4a51-8d60-e6871d1abd02
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bce99af4596d12e800a68bcff43090431fa47765
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="getsqlxml-method-javalangstring-sqlserverresultset"></a>getSQLXML (java.lang.String) メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  現在の行に指定された列の値を取得、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) SQLXML オブジェクトとしてオブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final java.sql.SQLXML getSQLXML(java.lang.String columnLabel)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnName*  
  
 A**文字列**列ラベルを示すです。  
  
## <a name="return-value"></a>戻り値  
 ASQLXMLobject です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getSQLXML メソッドは、java.sql.ResultSet インターフェイスの getSQLXML メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [getSQLXML メソッド &#40;です。SQLServerResultSet &#41;](../../../connect/jdbc/reference/getsqlxml-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)  
  
  
