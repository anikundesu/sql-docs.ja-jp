---
title: "getSendStringParametersAsUnicode メソッド (SQLServerDataSource) |Microsoft ドキュメント"
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
apiname: SQLServerDataSource.getSendStringParametersAsUnicode
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 3836d0ab-c3fb-41ff-bb89-10389594ae51
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d7eb3b6f95939250d2eccf7edaaa06aace8d743f
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="getsendstringparametersasunicode-method-sqlserverdatasource"></a>getSendStringParametersAsUnicode メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  返します、**ブール**文字列パラメーターを UNICODE 形式でサーバーに送信が有効かどうかを示す値。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean getSendStringParametersAsUnicode()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**文字列パラメーターが UNICODE 形式でサーバーに送信された場合。 それ以外の場合は、 **false**です。  
  
## <a name="remarks"></a>解説  
 SendStringParametersAsUnicode プロパティ設定されている場合**true**既定値は、文字列パラメーターが UNICODE 形式でサーバーに送信されます。 SendStringParametersAsUnicode に設定されている場合**false**、文字列パラメーターは、UNICODE ではなく ASCII/MBCS 形式でサーバーに送信されます。 SendStringParametersAsUnicode が設定されていない場合、getSendStringParametersAsUnicode の既定値を返します**true**です。  
  
 SendStringParametersAsUnicode 接続プロパティの詳細については、次を参照してください。[接続プロパティの設定](../../../connect/jdbc/setting-the-connection-properties.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
