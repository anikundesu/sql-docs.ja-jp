---
title: "サーバー側の XML 書式設定 (SQLXML 4.0) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- FOR XML clause, formatting
- server-side XML formatting
ms.assetid: ae9ea068-0857-4505-a3b2-f53d256b644c
caps.latest.revision: "12"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4ef0040fba0df07a7be9a1142b3e676c840ac739
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="server-side-xml-formatting-sqlxml-40"></a>サーバー側の XML 書式設定 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]このトピックは、Microsoft では、データベースに対して実行されるクエリによって生成される行セットから、サーバー側で XML ドキュメントの書式設定に関する情報を提供[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]です。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、データベース テーブルに XML ドキュメントを格納したり、データベース テーブルから XML ドキュメントを取得することができます。 XML ドキュメントを取得するには、SELECT クエリで FOR XML クエリ拡張を使用します。  
  
 たとえば、クライアント アプリケーションに対してコマンドを実行する[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]次で構成される[!INCLUDE[tsql](../../../includes/tsql-md.md)]クエリ。  
  
```  
SELECT FirstName, LastName  
FROM   Person.Contact  
FOR XML AUTO  
```  
  
 サーバーでは、クエリが 2 段階で実行されます。 最初に、サーバーでは次の SELECT ステートメントが実行されます。  
  
```  
SELECT FirstName, LastName  
FROM   Person.Contact  
```  
  
 次に、サーバーでは生成された行セットに対して FOR XML 変換が適用され、 結果の XML が 1 列の行セットとしてクライアントに送られます。 このドキュメントでは、この処理をサーバー側の XML 書式設定と呼びます。  
  
 サーバー側では、FOR XML 句で次のモードを指定できます。  
  
-   RAW  
  
-   AUTO  
  
-   EXPLICIT  
  
 FOR XML 句の詳細については、次を参照してください。 [For を使用して XML](../../../relational-databases/xml/for-xml-sql-server.md)です。  
  
## <a name="see-also"></a>参照  
 [クライアント側およびサーバー側の XML 書式設定 (&) #40 です。 のアーキテクチャSQLXML 4.0 &#41;](../../../relational-databases/sqlxml/formatting/architecture-of-client-side-and-server-side-xml-formatting-sqlxml-4-0.md)   
 [クライアント側の XML 書式設定 (&) #40 です。SQLXML 4.0 &#41;](../../../relational-databases/sqlxml/formatting/client-side-xml-formatting-sqlxml-4-0.md)   
 [FOR XML &#40;SQL Server&#41;](../../../relational-databases/xml/for-xml-sql-server.md)  
  
  
