---
title: "STLineFromText (geometry データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STLineFromText (geometry Data Type)
- STLineFromText_TSQL
dev_langs: TSQL
helpviewer_keywords: STLineFromText (geometry Data Type)
ms.assetid: 430508ad-207b-4dee-a4d1-4ddf25e6b4a9
caps.latest.revision: "20"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 40fbc8cc01601c3c7a3893be7aa61eb50f8952ab
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="stlinefromtext-geometry-data-type"></a>STLineFromText (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

返します、 **geometry**いる Z (標高) 値および M (メジャー) 値で補完された、Open Geospatial Consortium (OGC) Well-Known Text (WKT) 表現からのインスタンスがインスタンスで実行します。
  
## <a name="syntax"></a>構文  
  
```  
  
STLineFromText ( 'linestring_tagged_text' , SRID )  
```  
  
## <a name="arguments"></a>引数  
 *linestring_tagged_text*  
 WKT 表現です、 **geometryLineString**インスタンスを取得します。 *linestring_tagged_text*は、 **nvarchar (max)**式。  
  
 *SRID*  
 **Int** 、空間を表す式の ID (SRID) を参照、 **geometryLineString**インスタンスを取得します。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す:**ジオメトリ**  
  
 CLR の戻り値の型: **SqlGeometry**  
  
 OGC の型: **LineString**  
  
## <a name="remarks"></a>解説  
 このメソッドはスロー、 **FormatException**入力が適切な形式でない場合。  
  
## <a name="examples"></a>使用例  
 次の例で`STLineFromText()`を作成する、`geometry`インスタンス。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STLineFromText('LINESTRING (100 100, 200 200)', 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>参照  
 [OGC の静的なジオメトリ メソッド](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  

