---
title: "true 関数 (XQuery) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2016
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: xquery
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
dev_langs: XML
helpviewer_keywords:
- fn:true function
- true function
ms.assetid: 318e370d-0444-4812-afe4-307df7ef9f3b
caps.latest.revision: "17"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f38cd50748b59b2a0cf32e5a7e9ab0a28f7e396b
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="boolean-constructor-functions---true-xquery"></a>ブール値コンス トラクター関数の true (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  xs:boolean 値 True を返します。 これに相当`xs:boolean("1")`です。  
  
## <a name="syntax"></a>構文  
  
```  
fn:true() as xs:boolean  
```  
  
## <a name="examples"></a>使用例  
 このトピックでは、さまざまなに格納されている XML インスタンスに対して XQuery の例は、 **xml** AdventureWorks データベース内の列を入力します。  
  
### <a name="a-using-the-true-xquery-boolean-function"></a>A. XQuery 論理関数 true() の使用  
 次の例は、型指定されていないクエリ**xml**変数。 内の式、 **value()**メソッドは、ブール値を返します**true()** "aaa"属性値である場合。 **Value()**のメソッド、 **xml**データ型がブール値、ビットに変換し、それを取得します。  
  
```  
DECLARE @x XML  
SET @x= '<ROOT><elem attr="aaa">bbb</elem></ROOT>'  
select @x.value(' if ( (/ROOT/elem/@attr)[1] eq "aaa" ) then fn:true() else fn:false() ', 'bit')  
go  
-- result = 1  
```  
  
 次の例では、クエリが指定の型指定されたに対して**xml**列です。 `if`式の型指定されたブール値をチェックする、<`ROOT`> 要素と、それに応じて、構築された XML が返されます。 この例では、次の操作が実行されます。  
  
-   定義する XML スキーマ コレクションを作成、<`ROOT`> xs:boolean 型の要素。  
  
-   型指定されたテーブルを作成**xml** XML スキーマ コレクションを使用して列です。  
  
-   XML インスタンスを列に保存し、クエリを実行します。  
  
```  
-- Drop table if exist  
--DROP TABLE T  
--go  
DROP XML SCHEMA COLLECTION SC  
go  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema"  
targetNamespace="QNameXSD" >  
      <element name="ROOT" type="boolean" nillable="true"/>  
</schema>'  
go  
CREATE TABLE T (xmlCol XML(SC))  
go  
-- following OK  
insert into T values ('<ROOT xmlns="QNameXSD">true</ROOT>')  
 go  
-- Retrieve the local name.   
SELECT xmlCol.query('declare namespace a="QNameXSD";   
   if (/a:ROOT[1] eq true()) then  
       <result>Found boolean true</result>  
   else  
       <result>Found boolean false</result>')  
  
FROM T  
-- result = <result>Found boolean true</result>  
-- Clean up  
DROP TABLE T  
go  
DROP XML SCHEMA COLLECTION SC  
go  
```  
  
## <a name="see-also"></a>参照  
 [ブール値コンス トラクター関数 &#40;です。XQuery と #41 です。](http://msdn.microsoft.com/library/fa907f39-d4b7-4495-b829-c788928e0f64)  
  
  
