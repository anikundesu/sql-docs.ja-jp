---
title: "STIsValid (geography データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords: STIsValid method (geography)
ms.assetid: 1bfe787f-ddf0-4fc7-af6a-570a58faab23
caps.latest.revision: "11"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 035a7edb3f17ac40a19e427d1e80844fbf9e221c
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="stisvalid-geography-data-type"></a>STIsValid (geography データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  場合は true を返します、 **geography**インスタンスが整形式であり、Open Geospatial Consortium (OGC) 型に基づいて有効な geography オブジェクトとして認識されています。 場合は false を返します、 **geography**インスタンスが整形式ではありません。 このメソッドは正確です。  
  
 この geography データ型メソッドでサポート**FullGlobe**インスタンスまたは空間インスタンスは、半球より大きいをします。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STIsValid ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す:**ビット**  
  
 CLR の戻り値の型: **SqlBoolean**  
  
## <a name="remarks"></a>解説  
 OGC の型の**geography**インスタンスを呼び出すことによって判別できます[STGeometryType()](../../t-sql/spatial-geography/stgeometrytype-geography-data-type.md)です。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のみの有効な生成**geography**インスタンスしますが、無効なインスタンスの取得と記憶域が可能です。 使用して、無効なインスタンスの同じ地点のセットを表す有効なインスタンスを取得することができます、`MakeValid()`メソッドです。  
  
## <a name="examples"></a>使用例  
 `geography` インスタンスを作成し、`STIsValid()` を使用してこのインスタンスが有効かどうかをテストする例を次に示します。  
  
```  
DECLARE @g geography = geography::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 4326);  
SELECT @g.STIsValid();  
DECLARE @g geography  
```  
  
## <a name="see-also"></a>参照  
 [STGeometryType &#40;geography データ型&#41;](../../t-sql/spatial-geography/stgeometrytype-geography-data-type.md)   
 [MakeValid &#40;geography データ型&#41;](../../t-sql/spatial-geography/makevalid-geography-data-type.md)   
 [Geography インスタンスの OGC メソッド](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
