---
title: "getConnection (java.lang.String, java.lang.String) メソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDataSource.getConnection (java.lang.String, java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 78db89d6-a8a0-4116-8885-548e627220ed
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 39b7a3bb2896ff308fc58510443bd54c487c77f8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getconnection-method-javalangstring-javalangstring"></a>getConnection (java.lang.String, java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  このソースのデータとの接続を確立するために試行[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)特定のユーザー名とパスワードを使用してオブジェクトを表します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.Connection getConnection(java.lang.String username,  
                                         java.lang.String password)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ユーザー名*  
  
 A**文字列**ユーザー名を格納しています。  
  
 *パスワード*  
  
 A**文字列**パスワードを格納しています。  
  
## <a name="return-value"></a>戻り値  
 A [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクト。  
  
## <a name="exceptions"></a>例外  
 java.sql.SQLException  
  
## <a name="remarks"></a>解説  
 この getConnection メソッドは、javax.sql.DataSource インターフェイスの getConnection メソッドによって指定されます。  
  
 呼び出し、getConnection、null 以外のユーザー名またはパスワードを持つメソッドは、SQLServerConnection オブジェクトを初期化するときに、SQLServerDataSource クラスに設定されているユーザー名とパスワードのプロパティに置き換えられます。 たとえば、呼び出し元が呼び出された場合[setUser](../../../connect/jdbc/reference/setuser-method-sqlserverdatasource.md)と[setPassword](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md)でデータ ソースとし、呼び出し getConnection 装置が null 以外のユーザー名または null 以外のパスワード、ユーザー名とパスワードを設定setUser と setPassword はユーザー名と getConnection に渡されるパスワードによって置き換えられます。  
  
> [!NOTE]  
>  ユーザー名とパスワードへの呼び出しを使用して、URL 内に設定した、 [setURL](../../../connect/jdbc/reference/seturl-method-sqlserverdatasource.md)メソッドはここでは変更されません。  
  
## <a name="see-also"></a>参照  
 [getConnection メソッド & #40 です。SQLServerDataSource &#41;](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)   
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  