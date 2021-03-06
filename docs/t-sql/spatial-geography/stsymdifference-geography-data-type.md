---
title: "STSymDifference (geography データ型) |Microsoft ドキュメント"
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
f1_keywords:
- STSymDifference (geography Data Type)
- STSymDifference_TSQL
dev_langs: TSQL
helpviewer_keywords: STSymDifference (geography Data Type)
ms.assetid: 82bbfa2c-a61b-4f41-9bf8-6f720f363bae
caps.latest.revision: "20"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2c591f665b6f441face6a83aa9421fc47c5b0982
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="stsymdifference-geography-data-type"></a>STSymDifference (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  いずれかであるすべてのポイントを表すオブジェクトを返します**geography**インスタンスと別**geography**インスタンスが両方のインスタンスに存在する地点されません。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STSymDifference ( other_geography )  
```  
  
## <a name="arguments"></a>引数  
 *other_geography*  
 もう 1 つ**geography**インスタンス STSymDistance() が呼び出されて、インスタンス。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **geography**  
  
 CLR の戻り値の型: **SqlGeography**  
  
## <a name="remarks"></a>解説  
 このメソッドは、場合常に null を返しますの spatial reference identifier (Srid)、 **geography**インスタンスが一致しません。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]半球より大きい空間インスタンスをサポートしています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、サーバーで結果セットが拡張されて**FullGlobe**インスタンス。  
  
 結果に円弧が含まれるのは、入力インスタンスに円弧が含まれる場合のみです。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-computing-the-symmetric-difference-of-two-polygons"></a>A. 2 つの多角形の対称差を計算する  
 次の例で`STSymDifference()`2 つの対称差を計算する`Polygon`インスタンス。  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SET @h = geography::STGeomFromText('POLYGON((-122.351 47.656, -122.341 47.656, -122.341 47.661, -122.351 47.661, -122.351 47.656))', 4326);  
SELECT @g.STSymDifference(@h).ToString();  
```  
  
### <a name="b-computing-the-symmetric-difference-with-fullglobe"></a>B. FullGlobe を使用して、対称差を計算する  
 次の例の対称差を比較し、`Polygon`で`FullGlobe`です。  
  
```
 DECLARE @g geography = 'POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 SELECT @g.STSymDifference('FULLGLOBE').ToString();
 ```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの OGC メソッド](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
