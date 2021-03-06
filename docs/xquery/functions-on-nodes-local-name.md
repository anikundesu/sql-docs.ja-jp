---
title: "local-name 関数 (XQuery) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
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
- fn:local-name function
- local-name function
ms.assetid: c901ef5d-89c5-482a-bf64-3eefbcf3098d
caps.latest.revision: "14"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 2412e0f5a350b2e8bb4fb507440bcbfba289e359
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="functions-on-nodes---local-name"></a>ノードのローカル名に使用する関数
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  名前のローカル部分を返します*$arg* xs:string されるか、長さゼロの文字列またはられます xs:NCName の構文形式になります。 引数を指定しない場合の既定値はコンテキスト ノードです。  
  
## <a name="syntax"></a>構文  
  
```  
fn:local-name() as xs:string  
fn:local-name($arg as node()?) as xs:string  
```  
  
## <a name="arguments"></a>引数  
 *$arg*  
 ローカル名部分を取得するノード名。  
  
## <a name="remarks"></a>解説  
  
-   SQL Server で**fn:local-name()**せず、引数は、コンテキストに依存する述語のコンテキストでのみ使用できます。 具体的には、この属性は角かっこ内にのみ使用できます (`[ ]`)。  
  
-   引数に空のシーケンスを指定すると、関数は長さゼロの文字列を返します。  
  
-   対象ノードに名前がない場合、そのノードはドキュメント ノード、コメント、またはテキスト ノードなので、関数は長さゼロの文字列を返します。  
  
## <a name="examples"></a>使用例  
 このトピックでは、さまざまなに格納されている XML インスタンスに対して XQuery の例は、 **xml** AdventureWorks データベース内の列を入力します。  
  
### <a name="a-retrieve-local-name-of-a-specific-node"></a>A. 特定のノードのローカル名を取得する  
 次のクエリは、型指定されていない XML インスタンスに対して指定されています。 クエリ式、 `local-name(/ROOT[1])`、指定したノードのローカル名部分を取得します。  
  
```  
declare @x xml  
set @x='<ROOT><a>111</a></ROOT>'  
SELECT @x.query('local-name(/ROOT[1])')  
-- result = ROOT  
```  
  
 次のクエリは、ProductModel テーブルの型指定された xml 型の列である Instructions 列に対して指定されています。 式、 `local-name(/AWMI:root[1]/AWMI:Location[1])`、ローカルの名前を返します`Location`、指定したノードのです。  
  
```  
SELECT Instructions.query('  
declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
     local-name(/AWMI:root[1]/AWMI:Location[1])') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
-- result = Location  
```  
  
### <a name="b-using-local-name-without-argument-in-a-predicate"></a>B. 述語で引数を指定せずに local-name を使用する  
 次のクエリは型指定された、Instructions 列に対して指定**xml** ProductModel テーブルの列です。 式は、QName のローカル名部分が "Location" である <`root`> 要素のすべての子要素を返します。 **Local-name()**関数は、述語で指定し、コンテキスト ノードが、関数で使用される引数がありません。  
  
```  
SELECT Instructions.query('  
declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
  /AWMI:root//*[local-name() = "Location"]') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 クエリでは、すべてを返します、<`Location`> の子要素、<`root`> 要素。  
  
## <a name="see-also"></a>参照  
 [ノードの関数](http://msdn.microsoft.com/library/09a8affa-3341-4f50-aebc-fdf529e00c08)   
 [名前空間 uri 関数 &#40;です。XQuery と #41 です。](../xquery/functions-on-nodes-namespace-uri.md)  
  
  
