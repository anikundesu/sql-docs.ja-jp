---
title: "Long (geography データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/02/2016
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
- Long_TSQL
- Long
dev_langs: TSQL
helpviewer_keywords: Long method
ms.assetid: bedbeced-70b8-4569-84f3-f86bfb04ce50
caps.latest.revision: "14"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 883ae205fde68963a588765b1617ea98dbf600ac
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="long-geography-data-type"></a>Long (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  経度プロパティ、 **geography**インスタンス。  
  
## <a name="syntax"></a>構文  
  
```  
  
.Long  
```  
  
## <a name="return-value"></a>戻り値  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型: **float**  
  
 CLR 型: **SqlDouble**  
  
## <a name="remarks"></a>解説  
 OpenGIS モデルで長いで定義されているのみ**geography**インスタンスは、単一のポイントで構成されます。 場合、このプロパティは NULL を返しますが**geography**インスタンスには、複数の単一のポイントが含まれています。 このプロパティは正確で、読み取り専用です。  
  
## <a name="examples"></a>使用例  
 この例で作成、**ポイント**インスタンスし、その地点の経度を取得します。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.Long;  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの拡張メソッド](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
