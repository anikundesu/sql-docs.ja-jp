---
title: "getHoldability メソッド (SQLServerResultSet) |Microsoft ドキュメント"
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
ms.assetid: 4508d90f-c3c4-4eac-8001-fb0b93b66734
caps.latest.revision: "16"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1d413613719a5ea0adc8e323cfd8aaea205219d2
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="getholdability-method-sqlserverresultset"></a>getHoldability メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  これの保持機能を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getHoldability()  
```  
  
## <a name="return-value"></a>戻り値  
 **Int**保持機能レベルは次のいずれかを含む値です。  
  
 HOLD_CURSORS_OVER_COMMIT  
  
 CLOSE_CURSORS_AT_COMMIT  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getHoldability メソッドは、java.sql.ResultSet インターフェイスの getHoldability メソッドによって指定されます。  
  
 結果セットの保持機能を設定するアプリケーションを使用して、 [setHoldability](../../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md)のメソッド、 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)クラスです。 後に、 [setHoldability](../../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md)メソッドが呼び出されると、ステートメント オブジェクトとその結果セット オブジェクトを作成および、ステートメントが実行、アプリケーションが、保持機能を再度変更する必要があります。  
  
 サーバー カーソルの場合は、SQL Server 2005 以降に接続しているときがまだその接続で作成される新しい結果セットの保持機能のみに影響の保持機能を設定します。 ただし、SQL Server 2000 の場合は、保持機能の設定が、既存の結果セットとその接続でこれから作成される新しい結果セットの両方の保持機能に影響を与えます。  
  
 保持機能はリセットされ、getHoldability メソッドが呼び出されると、以前に作成された結果セット オブジェクト、このメソッドによって返される値は、次のメソッドによって返される保持機能値と異なる可能性があります: Statement.getResultSetHoldability、Connection.getHoldability、または DatabaseMetaData.getResultSetHoldability です。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
