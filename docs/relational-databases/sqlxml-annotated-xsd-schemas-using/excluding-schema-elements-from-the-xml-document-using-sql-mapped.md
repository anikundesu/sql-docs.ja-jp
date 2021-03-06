---
title: "Sql を使用して XML ドキュメントからスキーマ要素の除外: マップ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
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
- element does not map [SQLXML]
- annotated XSD schemas, excluding schema elements
- mapped annotation
- table mapping [SQLXML], excluding schema elements
- sql:mapped
- excluding schema elements
- element mapping [SQLXML], excluding schema elements
- column mapping [SQLXML]
- XSD schemas [SQLXML], excluding schema elements
- attribute mapping [SQLXML], excluding schema elements
- table/view mapping [SQLXML], excluding schema elements
ms.assetid: 7d2649dd-0038-4a2c-b16d-f80f7c306966
caps.latest.revision: "26"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 660fe866db09675916d90cdf8130b2b99980b2ec
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="excluding-schema-elements-from-the-xml-document-using-sqlmapped"></a>Sql を使用して XML ドキュメントからスキーマ要素の除外: マップ
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]すべての要素と、XSD スキーマで属性は、既定のマッピングにより、データベース テーブルまたはビューと列にマップされます。 ですが、データベースのテーブル (ビュー) または列にマップされないと、XML で表示しない、XSD スキーマで要素を作成するかどうかを指定できます、 **sql: マップ**注釈。  
  
 **Sql: マップ**注釈は、スキーマを変更することはできませんまたは他のソースし、まだデータベースに保存されていないデータを格納してから XML を検証するスキーマを使用する場合に特に便利です。 **Sql: マップ**注釈とは異なります**sql: 定数**点で、XML ドキュメントにマップされない要素と属性は表示されません。  
  
 **Sql: マップ**注釈はブール値 (0 = false、1 = true)。 指定できる値は 0、1、true、false です。  
  
## <a name="examples"></a>使用例  
 次の例を使用した実際のサンプルを作成するには、特定の条件を満たす必要があります。 詳細については、次を参照してください。 [SQLXML の例を実行するための要件](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md)です。  
  
### <a name="a-specifying-the-sqlmapped-annotation"></a>A. sql:mapped 注釈を指定する  
 他のソースからの XSD スキーマがあるとします。 この XSD スキーマから成る、  **\<Person.Contact >**を持つ要素**ContactID**、 **FirstName**、 **LastName**、および**HomeAddress**属性。  
  
 この XSD スキーマを AdventureWorks データベースの Person.Contact テーブルにマップする**sql: マップ**で指定された、 **HomeAddress** Employees テーブルで、ホームが格納されていないので属性従業員の住所。 この結果、マッピング スキーマに対して Xpath クエリを指定すると、属性はデータベースにマップされず、結果の XML ドキュメント内に返されません。  
  
 スキーマの残りの部分に対しては、既定のマッピングが適用されます。 **\<Person.Contact >**要素は Person.Contact テーブルにマップされ、すべての属性が Person.Contact テーブル内の同じ名前の列にマップします。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact">  
    <xsd:complexType>  
      <xsd:attribute name="ContactID"   type="xsd:string"/>  
      <xsd:attribute name="FirstName"    type="xsd:string" />  
      <xsd:attribute name="LastName"     type="xsd:string" />  
      <xsd:attribute name="HomeAddress" type="xsd:string"   
                     sql:mapped="false" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>スキーマに対してサンプル XPath クエリをテストするには  
  
1.  上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、 sql-mapped.xml として保存します。  
  
2.  次のテンプレートをコピーして、テキスト ファイルに貼り付け、 sql-mapped.xml を保存したディレクトリに sql-mappedT.xml として保存します。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="sql-mapped.xml">  
            /Person.Contact[@ContactID < 10]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     マッピング スキーマ (MySchema.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。 次のように、絶対パスを指定することもできます。  
  
    ```  
    mapping-schema="C:\MyDir\sql-mapped.xml"  
    ```  
  
3.  SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。  
  
     詳細については、次を参照してください。 [SQLXML クエリの実行に使用する ADO](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)です。  
  
 これは、結果セットを示します。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact ContactID="1" FirstName="Gustavo" LastName="Achong" />   
  <Person.Contact ContactID="2" FirstName="Catherine" LastName="Abel" />   
  <Person.Contact ContactID="3" FirstName="Kim" LastName="Abercrombie" />   
  <Person.Contact ContactID="4" FirstName="Humberto" LastName="Acevedo" />   
  <Person.Contact ContactID="5" FirstName="Pilar" LastName="Ackerman" />   
  <Person.Contact ContactID="6" FirstName="Frances" LastName="Adams" />   
  <Person.Contact ContactID="7" FirstName="Margaret" LastName="Smith" />   
  <Person.Contact ContactID="8" FirstName="Carla" LastName="Adams" />   
  <Person.Contact ContactID="9" FirstName="Jay" LastName="Adams" />   
</ROOT>  
```  
  
 ContactID、FirstName、および LastName 表示されているが、HomeAddress はマッピング スキーマの場合は 0 を指定するためにないことに注意してください、 **sql: マップ**属性。  
  
## <a name="see-also"></a>参照  
 [テーブルと列 &#40; に XSD 要素および属性の既定のマッピングSQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
  
  
