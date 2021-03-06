---
title: "setNull (int、int, java.lang.String) メソッド |Microsoft ドキュメント"
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
apiname: SQLServerPreparedStatement.setNull (int, int, java.lang.String)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 43c74e06-2858-49ba-bae7-b88808e5fff4
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dbf616a9d4ea79f3a8413c143d3430ac199fef68
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="setnull-method-int-int-javalangstring"></a>setNull (int, int, java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡されたパラメーターの型と名前を使用して、指定されたパラメーターを null 値に設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setNull(int paramIndex,  
                          int sqlType,  
                          java.lang.String typeName)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *paramIndex*  
  
 **Int**パラメーター数を示すです。  
  
 *sqlType*  
  
 Java.sql.Types で定義されている JDBC 型コード。  
  
 *型名*  
  
 A**文字列**が設定されているパラメーターの完全修飾名を示すです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setNull メソッドは、java.sql.PreparedStatement インターフェイスの setNull メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [setNull メソッド &#40;です。SQLServerPreparedStatement &#41;](../../../connect/jdbc/reference/setnull-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement のメンバー](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement クラス](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
