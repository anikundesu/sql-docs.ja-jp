---
title: "ストアド プロシージャのプロパティの例 (JScript) |Microsoft ドキュメント"
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
helpviewer_keywords:
- ActiveConnection property [ADO], JScript example
- CommandText property [ADO], JScript example
- Size property [ADO], JScript example
- Direction property [ADO], JScript example
- CommandTimeout property [ADO], JScript example
ms.assetid: ea74e2a3-c965-43aa-9076-26a084b48ad8
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f6e9a8ba4fd6996a5c75b219025df0b2e9a17b40
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="activeconnection-commandtext-commandtimeout-commandtype-size-and-direction-properties-example-jscript"></a>ActiveConnection、CommandText、CommandTimeout、CommandType、サイズ、および方向プロパティの例 (JScript)
この例では、 [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)、 [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)、 [CommandTimeout](../../../ado/reference/ado-api/commandtimeout-property-ado.md)、 [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md)、[サイズ](../../../ado/reference/ado-api/size-property-ado-parameter.md)、および[方向](../../../ado/reference/ado-api/direction-property.md)ストアド プロシージャを実行するプロパティです。 切り取りをメモ帳または別のテキスト エディターでは、次のコードを貼り付けとして保存して**ActiveConnectionJS.asp**です。  
  
```  
<!-- BeginActiveConnectionJS -->  
<%@LANGUAGE="JScript"%>  
<%// use this meta tag instead of adojavas.inc%>  
<!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" -->  
  
<html>  
<head>  
    <title>ActiveConnection, CommandText, CommandTimeout, CommandType, Size, and Direction Properties</title>  
<style>  
<!--  
BODY {  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;  
   BACKGROUND-COLOR:white;  
   COLOR:black;  
    }  
.thead {  
   background-color: #008080;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
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
</head>  
  
<body bgcolor="White">  
  
<%  
    var iRoyalty = parseInt(Request.Form("RoyaltyValue"));  
    // check user input  
  
    if (iRoyalty > -1)  
    {  
            // connection and recordset variables  
        var Cnxn = Server.CreateObject("ADODB.Connection")  
        var strCnxn = "Provider='sqloledb';Data Source=" + Request.ServerVariables("SERVER_NAME") + ";" +  
            "Initial Catalog='pubs';Integrated Security='SSPI';";  
        var cmdByRoyalty = Server.CreateObject("ADODB.Command");  
        var rsByRoyalty = Server.CreateObject("ADODB.Recordset");  
        var rsAuthor = Server.CreateObject("ADODB.Recordset");  
        // display variables  
        var filter, strMessage;          
  
        try  
        {  
            // open connection  
            Cnxn.Open(strCnxn);  
  
            cmdByRoyalty.CommandText = "byroyalty";  
            cmdByRoyalty.CommandType = adCmdStoredProc;  
            cmdByRoyalty.CommandTimeOut = 15;  
  
            // The stored procedure called above is as follows:  
                //    CREATE PROCEDURE byroyalty  
                //  @percentage int  
                //    AS  
                //  SELECT au_id from titleauthor  
                //  WHERE titleauthor.royaltyper = @percentage  
                //  GO  
  
            prmByRoyalty = Server.CreateObject("ADODB.Parameter");  
            prmByRoyalty.Type = adInteger;  
            prmByRoyalty.Size = 3;  
            prmByRoyalty.Direction = adParamInput;  
            prmByRoyalty.Value = iRoyalty;  
            cmdByRoyalty.Parameters.Append(prmByRoyalty);  
  
            cmdByRoyalty.ActiveConnection = Cnxn;  
  
            // recordset by Command - Execute  
            rsByRoyalty = cmdByRoyalty.Execute();  
  
            // recordset by Recordset - Open  
            rsAuthor.Open("Authors", Cnxn);  
  
            while (!rsByRoyalty.EOF)  
            {  
                // set filter  
                filter = "au_id='" + rsByRoyalty("au_id")  
                rsAuthor.Filter = filter + "'";  
  
                // start new line  
                strMessage = "<P>";  
  
                // get data  
                strMessage += rsAuthor("au_fname") + " ";   
                strMessage += rsAuthor("au_lname") + " ";  
  
                // end line  
                strMessage += "</P>";  
  
                // show data  
                Response.Write(strMessage);  
  
                // get next record  
                rsByRoyalty.MoveNext;  
            }  
        }  
        catch (e)  
        {  
            Response.Write(e.message);  
        }  
        finally  
        {  
            // clean up  
            if (rsByRoyalty.State == adStateOpen)  
                rsByRoyalty.Close;  
            if (rsAuthor.State == adStateOpen)  
                rsAuthor.Close;  
            if (Cnxn.State == adStateOpen)  
                Cnxn.Close;  
            rsByRoyalty = null;  
            rsAuthor = null;  
            Cnxn = null;  
        }  
    }  
%>  
  
<hr>  
  
<form method="POST" action="ActiveConnectionJS.asp">  
  <p align="left">Enter royalty percentage to find (e.g., 40): <input type="text" name="RoyaltyValue" size="5"></p>  
  <p align="left"><input type="submit" value="Submit" name="B1"><input type="reset" value="Reset" name="B2"></p>  
</form>  
  
</body>  
  
</html>  
<!-- EndActiveConnectionJS -->  
```  
  
## <a name="see-also"></a>参照  
 [ActiveCommand プロパティ (ADO)](../../../ado/reference/ado-api/activecommand-property-ado.md)   
 [コマンド オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [CommandText プロパティ (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [CommandTimeout プロパティ (ADO)](../../../ado/reference/ado-api/commandtimeout-property-ado.md)   
 [CommandType プロパティ (ADO)](../../../ado/reference/ado-api/commandtype-property-ado.md)   
 [接続オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [方向プロパティ](../../../ado/reference/ado-api/direction-property.md)   
 [パラメーター オブジェクト](../../../ado/reference/ado-api/parameter-object.md)   
 [Record オブジェクト (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Size プロパティ (ADO Parameter)](../../../ado/reference/ado-api/size-property-ado-parameter.md)
