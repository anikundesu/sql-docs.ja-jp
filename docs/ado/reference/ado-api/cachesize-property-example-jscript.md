---
title: "CacheSize プロパティの例 (JScript) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: JScript
helpviewer_keywords: CacheSize property [ADO], JScript example
ms.assetid: 3675f641-b4b1-48ff-ba33-8d9ea064cd04
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7489d2bc20cea493f0314c6efb6d70f186541f38
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="cachesize-property-example-jscript"></a>CacheSize プロパティの例 (JScript)
この例では、 [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)と 30 レコード キャッシュなしに実行される操作のパフォーマンスの違いを表示するプロパティです。 切り取りをメモ帳または別のテキスト エディターでは、次のコードを貼り付けとして保存して**CacheSizeJS.asp**です。  
  
```  
<!-- BeginCacheSizeJS -->  
<%@ Language="JScript" %>  
<%// use this meta tag instead of adojavas.inc%>  
<!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" -->  
  
<HTML>  
<HEAD>  
<title>CacheSize Property Example (JScript)</title>  
<style>  
<!--  
body {  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;  
   BACKGROUND-COLOR:white;  
   COLOR:black;  
    }  
.thead2 {  
   background-color: #800000;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.tbody {   
   text-align: center;  
   background-color: #f7efde;  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
    }  
-->  
</style>  
</HEAD>  
<BODY>  
<h1>CacheSize Property Example (JScript)</h1>  
<%  
    // connection and recordset variables  
    var Cnxn = Server.CreateObject("ADODB.Connection")  
    var strCnxn = "Provider='sqloledb';Data Source=" + Request.ServerVariables("SERVER_NAME") + ";" +  
            "Initial Catalog='Northwind';Integrated Security='SSPI';";  
    var rsCustomer = Server.CreateObject("ADODB.Recordset");  
    // caching variables  
    var Now = new Date();  
    var Start = Now.getTime();  
    var End, Cache, NoCache  
  
    try  
    {  
        // open connection  
        Cnxn.Open(strCnxn)  
  
        // open a recordset on the Employee table using client-side cursor  
        rsCustomer.CursorLocation = adUseClient;  
        rsCustomer.Open("Customers", strCnxn);  
  
        // loop through the recordset 20 times  
        for (var i=1; i<=20; i++)  
        {  
            rsCustomer.MoveFirst();  
            while (!rsCustomer.EOF)  
            {  
                // do something with the record  
                var strTemp = new String(rsCustomer("CompanyName"));  
                rsCustomer.MoveNext();  
            }  
        }  
  
        Now = new Date();  
        End = Now.getTime();  
        NoCache = End - Start;  
  
        // cache records in groups of 30  
        rsCustomer.MoveFirst();  
        rsCustomer.CacheSize = 30;  
  
        Now = new Date();  
        Start = Now.getTime();  
  
        // loop through the recordset 20 times  
        for (var i=1; i<=20; i++)  
        {  
            rsCustomer.MoveFirst();  
            while (!rsCustomer.EOF)  
            {  
                // do something with the record  
                var strTemp = new String(rsCustomer("CompanyName"));  
                rsCustomer.MoveNext();  
            }  
        }  
  
        Now = new Date();  
        End = Now.getTime();  
        var Cache = End - Start;  
    }  
    catch (e)  
    {  
        Response.Write(e.message);  
    }  
    finally  
    {  
        // clean up  
        if (rsCustomer.State == adStateOpen)  
            rsCustomer.Close;  
        if (Cnxn.State == adStateOpen)  
            Cnxn.Close;  
        rsCustomer = null;  
        Cnxn = null;  
    }  
%>  
  
    <table border="2">  
        <tr class="thead2">  
            <th>No Cache</th>  
            <th>30 Record Cache</th>  
        </tr>  
        <tr class="tbody">  
            <td><%=NoCache%></td>  
            <td><%=Cache%></td>  
        </tr>  
    </table>  
  
</BODY>  
</HTML>  
<!-- EndCacheSizeJS -->  
```  
  
## <a name="see-also"></a>参照  
 [CacheSize プロパティ (ADO)](../../../ado/reference/ado-api/cachesize-property-ado.md)   
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
