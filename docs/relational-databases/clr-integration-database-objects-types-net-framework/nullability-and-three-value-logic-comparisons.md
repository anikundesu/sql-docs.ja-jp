---
title: "Null 値許容と 3 値論理比較 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- precision [CLR integration]
- overflow detections [CLR integration]
- null values [CLR integration]
- three-value logic comparisons [CLR integration]
- data types [CLR integration]
- SqlBoolean data type
ms.assetid: 13da4c7f-1010-4b2d-a63c-c69b6bfd96f1
caps.latest.revision: "38"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 274f9342f3d0f69aec6a1a5083cc84ccf061f102
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="nullability-and-three-value-logic-comparisons"></a>NULL 値の許容と 3 値論理比較
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]慣れている場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型のようなセマンティクスや有効桁数を検索は、 **System.Data.SqlTypes**で名前空間、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]です。 ただし、いくつか違いもあります。このトピックでは、これらの違いの中から最も重要な点について説明します。  
  
## <a name="null-values"></a>NULL 値  
 CLR (共通言語ランタイム) のネイティブ データ型と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型の主な違いは、CLR データ型では NULL 値が許容されないのに対して、SQL Server データ型では完全な NULL セマンティクスが用意されているという点です。  
  
 比較は NULL 値の影響を受けます。 つまり、2 つの値 x と y を比較するときに、x または y が NULL の場合、一部の論理比較では true または false ではなく UNKNOWN 値に評価されます。  
  
## <a name="sqlboolean-data-type"></a>SqlBoolean データ型  
 **System.Data.SqlTypes**名前空間が導入されています、 **SqlBoolean**この 3 値ロジックを表す型。 いずれかの間の比較**SqlTypes**を返す、 **SqlBoolean**値の型。 不明な値が null の値によって表される、 **SqlBoolean**型です。 プロパティ**IsTrue**、 **IsFalse**、および**IsNull**の値をチェックする指定された、 **SqlBoolean**型です。  
  
## <a name="operations-functions-and-null-values"></a>演算、関数、および NULL 値  
 すべての算術演算子 (+、-、 \*、/、%)、ビットごとの演算子 (~、&、および |)、ほとんどの関数は、オペランドのいずれかの型または引数に NULL を返すと**SqlTypes**は NULL です。 **IsNull**プロパティは常に true または false 値を返します。  
  
## <a name="precision"></a>有効桁数  
 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR の decimal データ型の最大値は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の numeric データ型や decimal データ型の最大値とは異なります。 また、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR の decimal データ型では、最大有効桁数が想定されます。 CLR で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、ただし、 **SqlDecimal**同じ最大有効桁数および小数点以下桁数とでの decimal データ型と同じセマンティクスを提供[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
## <a name="overflow-detection"></a>オーバーフローの検出  
 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR では、非常に大きな 2 つの数を加算しても例外がスローされないことがあります。 チェック演算子を使用しないと、負の整数に "回り込んだ" 結果が返されます。 **System.Data.SqlTypes**、すべてのオーバーフローおよびアンダー フロー エラー、および 0 除算エラーに対して例外がスローされます。  
  
## <a name="see-also"></a>参照  
 [.NET Framework での SQL Server データ型](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
