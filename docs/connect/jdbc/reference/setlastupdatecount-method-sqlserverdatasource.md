---
title: "setLastUpdateCount メソッド (SQLServerDataSource) |Microsoft ドキュメント"
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
apiname: SQLServerDataSource.setLastUpdateCount
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 5487631a-1107-4169-84ca-b77fd09bea66
caps.latest.revision: "18"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dea575ca8c0baf6f4bb017dc50cebc26448f0397
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="setlastupdatecount-method-sqlserverdatasource"></a>setLastUpdateCount メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  セット、**ブール**lastUpdateCount プロパティが有効かどうかを示す値。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setLastUpdateCount(boolean lastUpdateCount)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *lastUpdateCount*  
  
 **true** lastUpdateCount が有効になっている場合。 それ以外の場合は、 **false**です。  
  
## <a name="remarks"></a>解説  
 LastUpdateCount プロパティ設定されている場合**true**、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]最後だけを返すから SQL ステートメントからの更新数が、サーバーに渡されます。 LastUpdateCount プロパティ設定されている場合**false**ドライバーはすべての更新数が発生した可能性があるすべてのトリガーによって返されるものなどを返します。 LastUpdateCount プロパティが設定されていない場合、 [getLastUpdateCount](../../../connect/jdbc/reference/getlastupdatecount-method-sqlserverdatasource.md)メソッドの既定値を返します**true**です。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
