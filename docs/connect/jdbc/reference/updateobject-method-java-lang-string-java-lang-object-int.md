---
title: "updateObject (java.lang.String、java.lang.Object, int) メソッド |Microsoft ドキュメント"
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
apiname: SQLServerResultSet.updateObject (java.lang.String, java.lang.Object, int)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 27283ce1-637e-4e2c-91ee-8ad379114ac5
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f40caa5bf5c72f24e3b175af5fb607b17f85d76a
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="updateobject-method-javalangstring-javalangobject-int"></a>updateObject (java.lang.String, java.lang.Object, int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された列の更新、**オブジェクト**列の名前と小数点以下桁数を指定された値。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateObject(java.lang.String columnName,  
                         java.lang.Object x,  
                         int scale)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnName*  
  
 A**文字列**列の名前を格納しています。  
  
 *obj*  
  
 **オブジェクト**値。  
  
 *scale*  
  
 java.sql.Types.DECIMAL 型または java.sql.Types.NUMERIC 型の場合、この値は小数点以下の桁数になります。 その他のすべての種類はこの値は無視されます。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この updateObject メソッドは、java.sql.ResultSet インターフェイスの updateObject メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [updateObject メソッド &#40;です。SQLServerResultSet &#41;](../../../connect/jdbc/reference/updateobject-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
