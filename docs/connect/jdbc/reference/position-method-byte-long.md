---
title: "position メソッド (バイト、long) |Microsoft ドキュメント"
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
apiname: SQLServerBlob.position (byte[], long)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 787412c2-4342-49c8-9ca2-7a9ddcd3277c
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c1abb3e2df956be93b8aee42b1b1b6b14e62d0fe
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="position-method-byte-long"></a>position メソッド (バイト、long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  に基づいて、BLOB の指定されたパターンの位置を返します、指定された**バイト**パターンと開始インデックスの配列。  
  
## <a name="syntax"></a>構文  
  
```  
  
public long position(byte[] bPattern,  
                     long start)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *bPattern*  
  
 検索するパターンです。  
  
 *開始*  
  
 検索の開始インデックスです。  
  
## <a name="return-value"></a>戻り値  
 A**長い**パターンが見つかった位置の値か、見つからなかった場合は-1。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この位置メソッドは、位置、java.sql.Blob インターフェイスのメソッドでによって指定されます。  
  
## <a name="see-also"></a>参照  
 [方法 &#40; を配置します。SQLServerBlob &#41;](../../../connect/jdbc/reference/position-method-sqlserverblob.md)   
 [SQLServerBlob のメソッド](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [SQLServerBlob のメンバー](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob クラス](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
