---
title: "WITHOUT_ARRAY_WRAPPER オプションを使用して JSON から角かっこを削除する | Microsoft Docs"
ms.custom: 
ms.date: 06/02/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: json
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WITHOUT_ARRAY_WRAPPER
ms.assetid: aa86c2d1-458e-465f-abfa-75470137d054
caps.latest.revision: "11"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 8cf8eb9559743275d1a742b62fc9b399fb811483
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="remove-square-brackets-from-json---withoutarraywrapper-option"></a>WITHOUT_ARRAY_WRAPPER オプションを使用して JSON から角かっこを削除する
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

既定で **FOR JSON** 句の JSON 出力を囲んでいる角かっこを削除するには、 **WITHOUT_ARRAY_WRAPPER** オプションを指定します。 単一要素の配列の代わりに、単一の JSON オブジェクトを出力として生成するには、このオプションと単一行の結果を使います。

このオプションと複数行の結果を使うと、複数の要素が生成されて角かっこがないため、結果の出力は有効な JSON ではなくなります。  
  
## <a name="example-single-row-result"></a>例 (単一行の結果)  
**WITHOUT_ARRAY_WRAPPER** オプションを指定した場合と指定しなかった場合の **FOR JSON** 句の出力例を以下に示します。  
  
 **Query**  
  
```sql  
SELECT 2015 as year, 12 as month, 15 as day  
FOR JSON PATH, WITHOUT_ARRAY_WRAPPER 
```  

 **WITHOUT_ARRAY_WRAPPER** オプションを使用した**結果**  
  
```json  
{
    "year": 2015,
    "month": 12,
    "day": 15
} 
```  
  
 **WITHOUT_ARRAY_WRAPPER** オプションを使わない**結果** (既定)  
  
```json  
[{
    "year": 2015,
    "month": 12,
    "day": 15
}]
```  

## <a name="example-multiple-row-result"></a>例 (複数行の結果)
次に、 **FOR JSON** オプションを指定した場合と指定しなかった場合の **WITHOUT_ARRAY_WRAPPER** オプションを指定します。 この例では、複数行の結果が生成されます。 複数の要素があり、角かっこがないため、出力は有効な JSON ではありません。
  
 **Query**  
  
```sql  
SELECT TOP 3 SalesOrderNumber, OrderDate, Status  
FROM Sales.SalesOrderHeader  
ORDER BY ModifiedDate  
FOR JSON PATH, WITHOUT_ARRAY_WRAPPER 
```  
  
 **WITHOUT_ARRAY_WRAPPER** オプションを使用した**結果**  
  
```json  
{
    "SalesOrderNumber": "SO43662",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
}, {
    "SalesOrderNumber": "SO43661",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
}, {
    "SalesOrderNumber": "SO43660",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
} 
```  
  
 **WITHOUT_ARRAY_WRAPPER** オプションを使わない**結果** (既定)  
  
```json  
[{
    "SalesOrderNumber": "SO43662",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
}, {
    "SalesOrderNumber": "SO43661",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
}, {
    "SalesOrderNumber": "SO43660",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
}]
```  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>SQL Server に組み込まれている JSON サポートの詳細情報  
多くの具体的なソリューション、ユース ケース、推奨事項については、Microsoft のプログラム マネージャー Jovan Popovic による SQL Server および Azure SQL Database に[組み込まれている JSON のサポートに関するブログ投稿](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)をご覧ください。
  
## <a name="see-also"></a>参照  
 [FOR 句 &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)  
  
  
