---
title: "locatorsUpdateCopy メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント"
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
apiname: SQLServerDatabaseMetaData.locatorsUpdateCopy
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: f6ec8c1d-7ff8-4bc5-8bd3-0199a9294a6e
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7097d5586b233547574fc3fbe3c982586e90962c
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="locatorsupdatecopy-method-sqlserverdatabasemetadata"></a>locatorsUpdateCopy メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  LOB に対する更新が、コピーに対して行われたか、LOB に直接行われたかを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean locatorsUpdateCopy()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**コピーに更新される場合。 **false**更新プログラムが直接行われた場合。  
  
## <a name="exceptions"></a>例外  
 java.sql.SQLException  
  
## <a name="remarks"></a>解説  
 この locatorsUpdateCopy メソッドは、java.sql.DatabaseMetaData インターフェイスの locatorsUpdateCopy メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
