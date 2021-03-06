---
title: "システム オブジェクトの権限 (TRANSACT-SQL) の拒否 |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- DENY statement, system objects
- encryption [SQL Server], system objects
- system objects [SQL Server]
- cryptography [SQL Server], system objects
ms.assetid: 4e43f954-0982-470b-a239-08a13c61563a
caps.latest.revision: "21"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8d584aa3c7329b8f81e445f612e7041cd14e0747
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="deny-system-object-permissions-transact-sql"></a>DENY (システム オブジェクトの権限の拒否) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  ストアド プロシージャ、拡張ストアド プロシージャ、関数、ビューなどのシステム オブジェクトに対する権限を拒否します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DENY { SELECT | EXECUTE } ON [ sys.]system_object TO principal   
```  
  
## <a name="arguments"></a>引数  
 **[ sys です。]**  
 **Sys**カタログ ビューおよび動的管理ビューを参照している場合にのみ、修飾子が必要です。  
  
 *system_object*  
 権限を拒否するオブジェクトを指定します。  
  
 *プリンシパル*  
 権限を取り消すプリンシパルを指定します。  
  
## <a name="remarks"></a>解説  
 このステートメントを使用すると、特定のストアド プロシージャ、拡張ストアド プロシージャ、テーブル値関数、スカラー関数、ビュー、カタログ ビュー、互換ビュー、INFORMATION_SCHEMA ビュー、動的管理ビュー、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によってインストールされたシステム テーブルに対する権限を拒否できます。 Resource データベースに一意なレコードとして存在するこれらのシステム オブジェクトの各 (**mssqlsystemresource**)。 リソース データベースは読み取り専用です。 オブジェクトへのリンクが内のレコードとして公開されている、 **sys**すべてのデータベースのスキーマです。  
  
 既定の名前解決では、修飾子のないプロシージャ名はリソース データベースとして解釈されます。 そのため、 **sys**修飾子は、のみのカタログ ビューと動的管理ビューを指定する場合に必要です。  
  
> [!CAUTION]  
>  システム オブジェクトに対する権限を拒否すると、そのシステム オブジェクトに依存するアプリケーションは失敗します。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]使用してでは、カタログ ビューおよびカタログ ビューの既定のアクセス許可を変更するかどうかは、正常に機能しない可能性があります。  
  
 システム オブジェクトのトリガーおよび列に対する権限の拒否はサポートされていません。  
  
 アップグレード中にシステム オブジェクトに対する権限は保持されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 システム オブジェクトは、 [sys.system_objects](../../relational-databases/system-catalog-views/sys-system-objects-transact-sql.md) カタログ ビューで確認できます。 システム オブジェクトの権限は、 [master](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md) データベースの **sys.database_permissions** カタログ ビューで確認できます。  
  
 次のクエリでは、システム オブジェクトの権限に関する情報が返されます。  
  
```  
SELECT * FROM master.sys.database_permissions AS dp   
    JOIN sys.system_objects AS so  
    ON dp.major_id = so.object_id  
    WHERE dp.class = 1 AND so.parent_object_id = 0 ;  
GO  
```  
  
## <a name="permissions"></a>Permissions  
 CONTROL SERVER 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例を拒否`EXECUTE`に対する権限`xp_cmdshell`に`public`です。  
  
```  
DENY EXECUTE ON sys.xp_cmdshell TO public;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [TRANSACT-SQL 構文表記規則 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)   
 [sys.database_permissions および #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)   
 [システム オブジェクトの権限 &#40; を許可します。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-system-object-permissions-transact-sql.md)   
 [システム オブジェクトの権限 &#40; を取り消すTRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-system-object-permissions-transact-sql.md)  
  
  
