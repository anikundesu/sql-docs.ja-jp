---
title: "FOR JSON が SQL Server データ型を JSON データ型に変換する方法 (SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 07/07/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: json
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FOR JSON, data type conversion
ms.assetid: da356f06-efd0-4ea3-8157-77395bf790d7
caps.latest.revision: "11"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9d934c3ddaee2d87a0a4afa5f9df900f759a1ed7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="how-for-json-converts-sql-server-data-types-to-json-data-types-sql-server"></a>FOR JSON が SQL Server データ型を JSON データ型に変換する方法 (SQL Server)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  **FOR JSON** 句は、次の規則に従って、JSON 出力で SQL Server データ型を JSON 型に変換します。  
  
|カテゴリ|SQL Server データ型|JSON データ型|  
|--------------|--------------|---------------|  
|文字型と文字列型|char、nchar、varchar、nvarchar|string|  
|数値型|int、bigint、float、decimal、numeric|number|  
|ビット型|bit|Boolean (true または false)|  
|日付型と時刻型|date、datetime、datetime2、time、datetimeoffset|string|  
|バイナリ型|varbinary、binary、image、timestamp、rowversion|BASE64 エンコード文字列|  
|CLR 型|geometry、geography、他の CLR 型|サポートされていません。 これらの型はエラーを返します。<br /><br /> SELECT ステートメントで CAST または CONVERT を使用するか、CLR プロパティまたはメソッドを使用して、JSON 型に正常に変換できる SQL Server データ型にソース データを変換します。 たとえば、geometry 型には **STAsText()** を使い、CLR 型には **ToString()** を使います。 次に、JSON 出力値の型が、SELECT ステートメントで適用している変換の戻り値の型から導き出されます。|  
|その他の種類|uniqueidentifier、money|string|  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>SQL Server に組み込まれている JSON サポートの詳細情報  
多くの具体的なソリューション、ユース ケース、推奨事項については、Microsoft のプログラム マネージャー Jovan Popovic による SQL Server および Azure SQL Database に[組み込まれている JSON のサポートに関するブログ投稿](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)をご覧ください。
  
## <a name="see-also"></a>参照  
 [FOR JSON を使用してクエリ結果を JSON として書式設定する &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
  
  
