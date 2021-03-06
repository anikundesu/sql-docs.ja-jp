---
title: "SQLServerConnectionPoolDataSource のメンバー |Microsoft ドキュメント"
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
ms.assetid: dac0337e-8088-488c-a25a-801a2190f6ca
caps.latest.revision: "25"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c30d17335d610e6c04dcdc1a7e136b6470eee875
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="sqlserverconnectionpooldatasource-members"></a>SQLServerConnectionPoolDataSource のメンバー
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  次の表に、によって公開されるメンバー、 [SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)クラスです。  
  
## <a name="constructors"></a>コンス トラクター  
  
|名前|Description|  
|----------|-----------------|  
|[SQLServerConnectionPoolDataSource)](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-constructor.md)|新しいインスタンスを初期化、 [SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)クラスです。|  
  
## <a name="fields"></a>フィールド  
 [なし] :  
  
## <a name="inherited-fields"></a>継承されたフィールド  
 [なし] :  
  
## <a name="methods"></a>メソッド  
  
|名前|Description|  
|----------|-----------------|  
|[getApplicationIntent](../../../connect/jdbc/reference/getapplicationintent-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) の値を返します、 **applicationIntent**接続プロパティです。|  
|[getApplicationName](../../../connect/jdbc/reference/getapplicationname-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) アプリケーション名を返します。|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) データ ソース オブジェクトが表すデータ ソースとの接続の確立を試みます。|  
|[getDatabaseName](../../../connect/jdbc/reference/getdatabasename-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) データベース名を返します。|  
|[getDescription](../../../connect/jdbc/reference/getdescription-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) データ ソースの説明を返します。|  
|[getFailoverPartner](../../../connect/jdbc/reference/getfailoverpartner-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) データベース ミラーリング構成で使用されるフェールオーバー サーバーの名前を返します。|  
|[getInstanceName](../../../connect/jdbc/reference/getinstancename-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) を返します、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]インスタンス名。|  
|[getLastUpdateCount](../../../connect/jdbc/reference/getlastupdatecount-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) を返します、**ブール**lastUpdateCount プロパティが有効かどうかを示す値。|  
|[getLockTimeout](../../../connect/jdbc/reference/getlocktimeout-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) を返します、 **int**データベースがロック タイムアウトを報告する前に待機するミリ秒数を示す値。|  
|[getLoginTimeout](../../../connect/jdbc/reference/getlogintimeout-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 接続を確立中にこのデータ ソース オブジェクトが待機する秒数を返します。|  
|[getLogWriter](../../../connect/jdbc/reference/getlogwriter-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) のすべてのログ記録とトレース メッセージで使用される文字出力ストリームを返します。|  
|[getMultiSubnetFailover](../../../connect/jdbc/reference/getmultisubnetfailover-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) の値を返します、 **multiSubnetFailover**接続プロパティです。|  
|[getPooledConnection](../../../connect/jdbc/reference/getpooledconnection-method-sqlserverconnectionpooldatasource.md)|プールされた接続として使用できる物理データベース接続の確立を試みます。|  
|[getPortNumber](../../../connect/jdbc/reference/getportnumber-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) との通信に使用される現在のポート番号を返します[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。|  
|[getReference](../../../connect/jdbc/reference/getreference-method-sqlserverconnectionpooldatasource.md)|このデータ ソース オブジェクトへの参照を返します。|  
|[getSelectMethod](../../../connect/jdbc/reference/getselectmethod-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) このデータ ソース オブジェクトを使用して作成されるすべての結果セットに使用される既定のカーソルの種類を返します。|  
|[getSendStringParametersAsUnicode](../../../connect/jdbc/reference/getsendstringparametersasunicode-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) を返します、**ブール**文字列パラメーターを UNICODE 形式でサーバーに送信が有効かどうかを示す値。|  
|[getServerName](../../../connect/jdbc/reference/getservername-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) を実行しているコンピューターの名前を返します[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。|  
|[getURL](../../../connect/jdbc/reference/geturl-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) データ ソースへの接続に使用される URL を返します。|  
|[getUser](../../../connect/jdbc/reference/getuser-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) データ ソースに接続に使用されるユーザー名を返します。|  
|[getWorkstationID](../../../connect/jdbc/reference/getworkstationid-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) データ ソースへの接続に使用されるコンピューター名、クライアントの名前を返します。|  
|[getXopenStates](../../../connect/jdbc/reference/getxopenstates-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) を返します、**ブール**XOPEN 互換の状態を SQL 状態の変換が有効かどうかを示す値。|  
|[isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverconnectionpooldatasource.md)|このオブジェクトが指定されたインターフェイスのラッパーであるかどうかを示します。|  
|[setApplicationIntent](../../../connect/jdbc/reference/setapplicationintent-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) の値を設定、 **applicationIntent**接続プロパティです。|  
|[setApplicationName](../../../connect/jdbc/reference/setapplicationname-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) アプリケーション名を設定します。|  
|[setAuthenticationSceme](../../../connect/jdbc/reference/setauthenticationscheme-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md))、アプリケーションを使用する統合セキュリティの種類を示します。|  
|[setDatabaseName](../../../connect/jdbc/reference/setdatabasename-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) に接続するデータベースの名前を設定します。|  
|[setDescription](../../../connect/jdbc/reference/setdescription-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md))、データ ソースの説明を設定します。|  
|[setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) データベース ミラーリング構成で使用されるフェールオーバー サーバーの名前を設定します。|  
|[setInstanceName](../../../connect/jdbc/reference/setinstancename-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) セット、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]インスタンス名。|  
|[setIntegratedSecurity](../../../connect/jdbc/reference/setintegratedsecurity-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) セット、**ブール**integratedSecurity プロパティが有効かどうかを示す値。|  
|[setLastUpdateCount](../../../connect/jdbc/reference/setlastupdatecount-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) セット、**ブール**lastUpdateCount プロパティが有効かどうかを示す値。|  
|[setLockTimeout](../../../connect/jdbc/reference/setlocktimeout-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) セット、 **int**データベースがロック タイムアウトを報告する前に待機するミリ秒数を示す値。|  
|[setLoginTimeout](../../../connect/jdbc/reference/setlogintimeout-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 接続を確立中にこのデータ ソース オブジェクトが待機する秒数を設定します。|  
|[setLogWriter](../../../connect/jdbc/reference/setlogwriter-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) のすべてのログ記録とトレース メッセージで使用される文字出力ストリームを設定します。|  
|[setMultiSubnetFailover](../../../connect/jdbc/reference/setmultisubnetfailover-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) の値を設定、 **multiSubnetFailover**接続プロパティです。|  
|[setPassword](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) への接続に使用されるパスワードを設定[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。|  
|[setPortNumber](../../../connect/jdbc/reference/setportnumber-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) との通信に使用するポート番号を設定[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。|  
|[setSelectMethod](../../../connect/jdbc/reference/setselectmethod-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) このデータ ソース オブジェクトを使用して作成されるすべての結果セットに使用される既定のカーソルの種類を設定します。|  
|[setSendStringParametersAsUnicode](../../../connect/jdbc/reference/setsendstringparametersasunicode-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) セット、**ブール**文字列パラメーターを UNICODE 形式でサーバーに送信が有効かどうかを示す値。|  
|[setServerName](../../../connect/jdbc/reference/setservername-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) を実行しているコンピューターの名前を設定[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。|  
|[setURL](../../../connect/jdbc/reference/seturl-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md))、データ ソースへの接続に使用される URL を設定します。|  
|[setUser](../../../connect/jdbc/reference/setuser-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md))、データ ソースの接続に使用されるユーザー名を設定します。|  
|[setWorkstationID](../../../connect/jdbc/reference/setworkstationid-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md))、クライアントにデータ ソースへの接続に使用されるコンピューター名を設定します。|  
|[setXopenStates](../../../connect/jdbc/reference/setxopenstates-method-sqlserverdatasource.md)|(から継承された[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) セット、**ブール**XOPEN 互換の状態を SQL 状態の変換が有効かどうかを示す値。|  
|[unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverconnectionpooldatasource.md)|アクセス許可を指定したインターフェイスを実装するオブジェクトを返します、 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-特定のメソッドです。|  
  
## <a name="inherited-methods"></a>継承されたメソッド  
  
|継承元のクラス|メソッド|  
|---------------------------|-------------|  
|com.microsoft.sqlserver.jdbc.SQLServerDataSource|getApplicationName、getConnection、getDatabaseName、getDescription、getFailoverPartner、getInstanceName、getLastUpdateCount、getLockTimeout、getLoginTimeout、getLogWriter、getPortNumber、getSelectMethod、getSendStringParametersAsUnicode、getServerName、getURL、getUser、getWorkstationID、getXopenStates、setApplicationName、setDatabaseName、setDescription、setFailoverPartner、setInstanceName、setIntegratedSecurity、setLastUpdateCount、setLockTimeout、setLoginTimeout、setLogWriter、setPassword、setPortNumber、setSelectMethod、setSendStringParametersAsUnicode、setServerName、setURL、setUser、setWorkstationID、setXopenStates|  
|java.lang.Object|clone、equals、finalize、getClass、hashCode、notify、notifyAll、toString、wait|  
|java.sql.Wrapper|isWrapperFor、unwrap|  
|javax.sql.ConnectionPoolDataSource|getLoginTimeout、getLogWriter、setLoginTimeout、setLogWriter、getPooledConnection|  
  
## <a name="see-also"></a>参照  
 [SQLServerConnectionPoolDataSource クラス](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)  
  
  
