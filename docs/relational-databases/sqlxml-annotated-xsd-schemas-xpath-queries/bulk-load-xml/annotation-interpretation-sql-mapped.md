---
title: "sql: マップ (SQLXML 4.0) |Microsoft ドキュメント"
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
- mapped annotation
- element mapping [SQLXML], XML Bulk Load
- attribute mapping [SQLXML], XML Bulk Load
- overflow data [SQLXML]
- sql:mapped
- column mapping [SQLXML]
ms.assetid: 7042741e-ce4d-4912-9c4a-d77194a028fc
caps.latest.revision: "22"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ff3fc4b275e60bd2a209589ddb9601e668cf3345
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="annotation-interpretation---sqlmapped"></a>注釈の解釈 - sql: マップ
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]XML 一括読み込み処理、 **sql: マップ**期待どおりに、XSD スキーマで注釈-つまり、マッピング スキーマを指定する場合**sql: マップ ="false"**任意の要素または属性を使用して、XML 一括読み込みはできません対応する列に関連付けられているデータを格納しようとしてください。  
  
 XML 一括読み込みは、要素とマップされていない属性は無視されます (スキーマで記述されていないか、XSD スキーマで注釈が付いているため**sql: マップ ="false"**)。 使用してこのような列が指定されている場合に、オーバーフロー列にマップされていないすべてのデータが**sql:overflow-フィールド**です。  
  
 たとえば、次の XSD スキーマを考えてみます。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:element name="ROOT" sql:is-constant="1">  
<xsd:complexType>  
<xsd:sequence>  
  <xsd:element name="Customers" sql:relation="Cust"  
                                sql:overflow-field="OverflowColumn" >  
   <xsd:complexType>  
       <xsd:attribute name="CustomerID"  type="xsd:integer" />  
       <xsd:attribute name="CompanyName" type="xsd:string" />  
       <xsd:attribute name="City"        type="xsd:string" />  
       <xsd:attribute name="HomePhone"   type="xsd:string"   
                                       sql:mapped="false" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:sequence>  
</xsd:complexType>  
</xsd:element>  
</xsd:schema>  
```  
  
 **HomePhone**属性を指定**sql: マップ ="false"**、XML 一括読み込みでは、この属性の対応する列にマップされません。 XSD スキーマを識別、オーバーフロー列 (**OverflowColumn**) XML 一括読み込みでこの未使用データを格納します。  
  
### <a name="to-test-a-working-sample"></a>実際のサンプルをテストするには  
  
1.  次の表を作成、 **tempdb**データベース。  
  
    ```  
    USE tempdb  
    CREATE TABLE Cust  
              (CustomerID     int         PRIMARY KEY,  
               CompanyName    varchar(20) NOT NULL,  
               City           varchar(20) DEFAULT 'Seattle',  
               OverflowColumn nvarchar(200))  
    GO  
    ```  
  
2.  この例のスキーマを SampleSchema.xml として保存します。  
  
3.  次のサンプル XML データを SampleXMLData.xml として保存します。  
  
    ```  
    <ROOT>  
      <Customers CustomerID="1111" CompanyName="Sean Chai"   
                 City="NY" HomePhone="111-1111" />  
      <Customers CustomerID="1112" CompanyName="Dont Know"   
                 City="LA" HomePhone="222-2222" />  
    </ROOT>  
    ```  
  
4.  XML 一括読み込みを実行するには、この [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) の例を Sample.vbs として保存し実行します。  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints=True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
 これは、同等の XDR スキーマです。  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >   
   <ElementType name="ROOT" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
   <ElementType name="Customers" sql:relation="Cust"  
                             sql:overflow-field="OverflowColumn" >  
      <AttributeType name="CustomerID" />  
      <AttributeType name="CompanyName"  />  
      <AttributeType name="City"  />  
      <AttributeType name="HomePhone" />  
      <attribute type="CustomerID"  />  
      <attribute type="CompanyName"  />  
      <attribute type="City" />  
      <attribute type="HomePhone" sql:map-field="0" />  
   </ElementType>  
</Schema>  
```  
  
  
