---
title: "setSendStringParametersAsUnicode メソッド (SQLServerDataSource) |Microsoft ドキュメント"
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
apiname: SQLServerDataSource.setSendStringParametersAsUnicode
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 49198d63-76cb-4843-8d04-e49b1fbb6916
caps.latest.revision: "17"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3d987c3c3665fc20ce6439ae796e2d5d279622db
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="setsendstringparametersasunicode-method-sqlserverdatasource"></a>setSendStringParametersAsUnicode メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  セット、**ブール**文字列パラメーターを UNICODE 形式でサーバーに送信が有効かどうかを示す値。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setSendStringParametersAsUnicode(boolean sendStringParametersAsUnicode)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *sendStringParametersAsUnicode*  
  
 **true**文字列パラメーターが UNICODE 形式でサーバーに送信された場合。 それ以外の場合は、 **false**です。  
  
## <a name="remarks"></a>解説  
 SendStringParametersAsUnicode プロパティ設定されている場合**true**既定値は、文字列パラメーターが UNICODE 形式でサーバーに送信されます。 SendStringParametersAsUnicode に設定されている場合**false**文字列パラメーターは、UNICODE ではなく ASCII/MBCS 形式でサーバーに送信されます。 SendStringParametersAsUnicode が設定されていない場合[getSendStringParametersAsUnicode](../../../connect/jdbc/reference/getsendstringparametersasunicode-method-sqlserverdatasource.md)の既定値を返します**true**です。  
  
 SendStringParametersAsUnicode 接続プロパティの詳細については、次を参照してください。[接続プロパティの設定](../../../connect/jdbc/setting-the-connection-properties.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
