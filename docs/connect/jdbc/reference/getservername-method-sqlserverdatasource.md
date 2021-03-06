---
title: "getServerName メソッド (SQLServerDataSource) |Microsoft ドキュメント"
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
apiname: SQLServerDataSource.getServerName
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 3004ed22-5d69-4dd0-8761-d39f0b7dde13
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2302fded14543647060ce8ddcff4b59e0911c942
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="getservername-method-sqlserverdatasource"></a>getServerName メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  名前を返します、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]インスタンス。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getServerName()  
```  
  
## <a name="return-value"></a>戻り値  
 A**文字列**を格納しているサーバー名または null 値が設定されていない場合。  
  
## <a name="remarks"></a>解説  
 サーバー名を実行しているターゲット コンピューターのホスト名[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。 GetServerName プロパティが設定されていない場合、getServerName は既定値は null を返します。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
