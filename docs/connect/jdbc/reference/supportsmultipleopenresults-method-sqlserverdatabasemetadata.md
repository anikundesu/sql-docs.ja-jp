---
title: "supportsMultipleOpenResults メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント"
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
apiname: SQLServerDatabaseMetaData.supportsMultipleOpenResults
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 9480d280-5e3d-46ae-80e6-1bba3ac5a641
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8fa4b149e4c2f2d899d6d355692559237fe8c2de
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="supportsmultipleopenresults-method-sqlserverdatabasemetadata"></a>supportsMultipleOpenResults メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  複数を設定することがあるかどうかを取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)から返されるオブジェクト、 [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)オブジェクトを同時にします。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean supportsMultipleOpenResults()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**サポートされている場合。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この supportsMultipleOpenResults メソッドは、java.sql.DatabaseMetaData インターフェイスの supportsMultipleOpenResults メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
