---
title: "サーバー接続ファイル (MySQLToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-mysql
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Server connection file validation
- Server connection files
ms.assetid: df0e970c-da0b-4118-b359-c9dcbbad16d6
caps.latest.revision: "18"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 275a2c1a8a7f3f22926eddc0504c36e9b00ad930
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="creating-the-server-connection-files-mysqltosql"></a>サーバー接続ファイル (MySQLToSQL) を作成します。
スクリプト ファイルの [サーバー] セクションで、または別のサーバー接続ファイルには、サーバー情報を指定することができます。 サーバー接続ファイルのコマンド ライン パラメーターは、`-c <serverconnectionfile>`です。 サーバーと同じ id が、スクリプト ファイルとサーバー接続ファイルの両方に存在する場合は、スクリプト ファイル内のサーバー定義と見なされます。  
  
**例:**  
  
```xml  
<!--Sample of server connection file commands -->  
  
<mysql name ="<source-server-unique-name>">  
  
   <standard-mode>  
  
      <server value ="<server-name>"/>  
  
      <user-id value ="<user-name>"/>  
  
      <password value ="<password>"/>  
  
      <port value ="<port>"/>  
  
   </standard-mode>  
  
</mysql>  
```  
  
```xml  
<!--Connection to SQL Server-->  
  
<sql-server name="<target-server-unique-name>">  
  
   <sql-server-authentication>  
  
      <server value="<server-name>"/>  
  
      <database value="<database-name>"/>  
  
      <user-id value="<user-name>"/>  
  
      <password value="<password>"/>  
  
      <encrypt value="<true/false>"/>  
  
      <trust-server-certificate value="<true/false>"/>  
  
   </sql-server-authentication>  
  
</sql-server>  
```  
  
```xml  
<!--Connection to SQL Azure-->  
  
<sql-azure name="<target-server-unique-name>">  
  
   <server value="<server-name>"/>  
  
   <database value="<database-name>"/>  
  
   <user-id value="<user-name>"/>  
  
   <password value="<password>"/>  
  
</sql-azure>  
```  
  
## <a name="server-connection-file-validation"></a>サーバー接続ファイルの検証  
ユーザーが、スキーマ定義ファイルに対する自分のサーバー接続ファイルを簡単に検証**'M2SSConsoleScriptServersSchema.xsd'** 'スキーマ' フォルダー内にあります。  
  
## <a name="next-step"></a>次の手順  
コンソールの運用には、次の手順は[SSMA コンソール &#40; を実行します。MySQLToSQL &#41;](../../ssma/mysql/executing-the-ssma-console-mysqltosql.md)  
  
## <a name="see-also"></a>参照  
[SSMA コンソール (MySQL) を実行します。](http://msdn.microsoft.com/en-us/e3e9f7e4-0619-4861-a202-3d5d39953b26)  
  
