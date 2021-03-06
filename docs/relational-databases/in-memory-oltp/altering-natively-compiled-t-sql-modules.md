---
title: "ネイティブ コンパイル T-SQL モジュールの変更 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: in-memory-oltp
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 010318a0-6807-47c3-8ecc-bb7cb60513f0
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9aff56e96ff1161c6366b459444f5210b052c36b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="altering-natively-compiled-t-sql-modules"></a>ネイティブ コンパイル T-SQL モジュールの変更
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] (およびそれ以降) および [!INCLUDE[ssSDS](../../includes/sssds-md.md)] では、ALTER ステートメントを使用して、ネイティブ コンパイル ストアド プロシージャおよびスカラー UDF やトリガーなどの他のネイティブ コンパイル T-SQL モジュールに対して、ALTER 操作を実行できます。  
  
 ネイティブ コンパイル T-SQL モジュールに対して ALTER を実行すると、モジュールは新しい定義を使用して再コンパイルされます。 再コンパイルの進行中、古いバージョンのモジュールは引き続き実行に使用できます。 コンパイルが完了すると、モジュールの実行は削除され、新しいバージョンのモジュールがインストールされます。 ネイティブ コンパイル T-SQL モジュールを変更する場合、次のオプションを変更できます。  
  
-   パラメーター  
  
-   EXECUTE AS  
  
-   TRANSACTION ISOLATION LEVEL  
  
-   LANGUAGE  
  
-   DATEFIRST  
  
-   DATEFORMAT  
  
-   DELAYED_DURABILITY  
  
> [!NOTE]  
>  ネイティブ コンパイル T-SQL モジュールは、非ネイティブ コンパイル モジュールに変換できません。 非ネイティブ コンパイル T-SQL モジュールは、ネイティブ コンパイル モジュールに変換できません。  
  
 ALTER PROCEDURE の機能と構文の詳細については、「[ALTER PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-procedure-transact-sql.md)」を参照してください。  
  
 ネイティブ コンパイル T-SQL モジュールに対して sp_recompile を実行できます。これにより、モジュールは次の実行時に再コンパイルされます。  
  
## <a name="example"></a>例  
 次の例では、メモリ最適化テーブル (T1) と、T1 のすべての列を選択するネイティブ コンパイル ストアド プロシージャ (SP1) が作成されます。 その後、SP1 は、EXECUTE AS 句を削除し、LANGUAGE を変更して、T1 からただ 1 つの列 (C1) を選択するように変更されます。  
  
```  
CREATE TABLE [dbo].[T1]  
(  
[c1] [int] NOT NULL,  
[c2] [float] NOT NULL,  
CONSTRAINT [PK_T1] PRIMARY KEY NONCLUSTERED ([c1])  
)WITH ( MEMORY_OPTIMIZED = ON , DURABILITY = SCHEMA_AND_DATA )  
GO  
  
CREATE PROCEDURE [dbo].[usp_1]  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH  
(  
 TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english'  
)  
 SELECT c1, c2 from dbo.T1  
END  
GO  
  
ALTER PROCEDURE [dbo].[usp_1]  
WITH NATIVE_COMPILATION, SCHEMABINDING  
AS BEGIN ATOMIC WITH  
(  
 TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'Dutch'  
)  
 SELECT c1 from dbo.T1  
END  
GO  
  
```  
  
  
