---
title: "valueOf (java.sql.Timestamp, java.util.Calendar) メソッド |Microsoft ドキュメント"
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
ms.assetid: 7320c383-0b06-446d-963b-7005e50324a2
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 138a53f22791390600ed21e535a7c26597f46321
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="valueof-method-javasqltimestamp-javautilcalendar"></a>valueOf (java.sql.Timestamp, java.util.Calendar) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  作成、 **DateTimeOffset**引数に java.sql.Timestamp 値とオフセットを示す java.util.Calendar 値 GMT からの特定のオフセットのポイントを表すオブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public static DateTimeOffset valueOf(java.sql.Timestamp timestamp, java.util.Calendar calendar)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *timestamp*  
  
 java.sql.Timestamp値です。  
  
 *予定表*  
  
 オフセットの値。  日付と時刻の要素*カレンダー*に従って設定されます、*タイムスタンプ*値。  
  
## <a name="return-value"></a>戻り値  
 特定 java.util.Calendar オブジェクトのタイム ゾーンでの java.sql.Timestamp オブジェクトで指定された特定の点を表す DateTimeOffset オブジェクトを返します。  
  
## <a name="remarks"></a>解説  
 このメソッドでは、ポイントに java.util.Calendar オブジェクトも java.sql.Timestamp オブジェクトによって指定された時間内に設定します。  
  
## <a name="see-also"></a>参照  
 [DateTimeOffset クラス](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset のメンバー](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
