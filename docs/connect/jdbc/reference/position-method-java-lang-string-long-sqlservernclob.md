---
title: "配置 (java.lang.String, long) メソッド (SQLServerNClob) |Microsoft ドキュメント"
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
ms.assetid: 46d4beec-831a-449f-98b6-322a80cc499a
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 733e4e3588c38303a6a84c794593a5e5111074fe
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="position-method-javalangstring-long-sqlservernclob"></a>position (java.lang.String, long) メソッド (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  文字の位置を取得、指定した部分文字列*searchstr*に表示されます、 **NCLOB**これによって表される値**NClob**オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public long position(java.lang.String searchstr,  
              long start)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *searchstr*  
  
 検索対象の部分文字列です。  
  
 *開始*  
  
 検索を開始する位置です。最初の位置は 1 です。  
  
## <a name="return-value"></a>戻り値  
 部分文字列が現れる位置です。部分文字列がない場合は -1 が返されます。 最初の位置は 1 です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この位置メソッドは、位置、java.sql.NClob インターフェイスのメソッドでによって指定されます。  
  
## <a name="see-also"></a>参照  
 [方法 &#40; を配置します。SQLServerNClob &#41;](../../../connect/jdbc/reference/position-method-sqlservernclob.md)   
 [SQLServerNClob のメソッド](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob のメンバー](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob クラス](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
