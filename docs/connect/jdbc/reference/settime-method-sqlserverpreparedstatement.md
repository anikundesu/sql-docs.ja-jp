---
title: "setTime メソッド (SQLServerPreparedStatement) |Microsoft ドキュメント"
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
apiname: SQLServerPreparedStatement.setTime
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: b3a83ea3-6636-4096-842b-71b37340fa07
caps.latest.revision: "17"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 76d540b51a281f4de1e6f337939c520cf0c64c8a
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="settime-method-sqlserverpreparedstatement"></a>setTime メソッド (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたパラメーターを、渡された時刻の値に設定します。  
  
 以降で[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]JDBC Driver 3.0 では、このメソッドの動作は、によって変更が、 **sendTimeAsDatetime**接続プロパティ ([接続プロパティの設定](../../../connect/jdbc/setting-the-connection-properties.md)) および[SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md)です。  
  
 詳細については、次を参照してください。[を構成する方法の java.sql.Time 値は、サーバーに送信される](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md)です。  
  
## <a name="overload-list"></a>オーバーロードの一覧  
  
|名前|Description|  
|----------|-----------------|  
|[setTime (int, java.sql.Time)](../../../connect/jdbc/reference/settime-method-int-java-sql-time.md)|指定されたパラメーターを、渡された時刻の値に設定します。|  
|[setTime (int、java.sql.Time, java.util.Calendar)](../../../connect/jdbc/reference/settime-method-int-java-sql-time-java-util-calendar.md)|渡された Calendar オブジェクトを使用して、指定されたパラメーターを、渡された時刻の値に設定します。|  
  
## <a name="see-also"></a>参照  
 [SQLServerPreparedStatement のメンバー](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement クラス](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
