---
title: "GRANT データベース スコープ資格情報 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/19/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GRANT DATABASE SCOPED CREDENTIAL
- GRANT_DATABASE_SCOPED_CREDENTIAL_TSQL
dev_langs: TSQL
helpviewer_keywords:
- granting permissions [SQL Server], database scoped credential
- permissions [SQL Server], database scoped credential
- database scoped credential [SQL Server], permissions
- GRANT statement, database scoped credentials
ms.assetid: 501f2c8a-6aeb-41af-bf0b-974d17af33c0
caps.latest.revision: "3"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6dbd261334e580904e9c6ad3b12ff761d8c909ab
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="grant-database-scoped-credential-permissions-transact-sql"></a>GRANT データベース スコープの資格情報のアクセス許可 (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  スコープの資格情報をデータベースに対する権限を許可します。 
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
GRANT permission  [ ,...n ]    
    ON DATABASE SCOPED CREDENTIAL :: credential_name   
    TO principal [ ,...n ] [ WITH GRANT OPTION ]   
    [ AS granting_principal ]   
```  
  
## <a name="arguments"></a>引数  
 *アクセス許可*  
 できる権限付与されたデータベースのスコープの資格情報を指定します。 下の表をご覧ください。  
  
 データベース スコープ資格情報で**::***credential_name*  
 権限が許可されているデータベース スコープ資格情報を指定します。 スコープ修飾子 "::" が必要です。  
  
 *database_principal*  
 権限を許可するプリンシパルを指定します。 次のいずれかです。  
  
-   データベース ユーザー  
-   データベース ロール (database role)  
-   アプリケーション ロール (application role)  
-   Windows ログインにマップされるデータベース ユーザー  
-   Windows グループにマップされるデータベース ユーザー  
-   証明書にマップされるデータベース ユーザー  
-   非対称キーにマップされているデータベース ユーザー  
-   データベース ユーザーが、サーバー プリンシパルにマップされていません。  
  
GRANT OPTION  
 権限が許可されたプリンシパルが、この権限を他のプリンシパルにも許可できることを示します。  
  
AS *granting_principal*  
 このクエリを実行するプリンシパルが権限を許可する権利を取得した、元のプリンシパルを指定します。 次のいずれかです。  
  
-   データベース ユーザー  
-   データベース ロール (database role)  
-   アプリケーション ロール (application role)  
-   Windows ログインにマップされるデータベース ユーザー  
-   Windows グループにマップされるデータベース ユーザー  
-   証明書にマップされるデータベース ユーザー  
-   非対称キーにマップされているデータベース ユーザー  
-   データベース ユーザーが、サーバー プリンシパルにマップされていません。  
  
## <a name="remarks"></a>解説  
 データベース スコープ資格情報は、データベース レベルのセキュリティ保護可能な権限の階層で親となっているデータベースに含まれる、します。 できる最も限定的アクセス権付与データベース スコープ資格情報の次のとおり、暗黙的に含む一般的な権限と共に示します。  
  
|データベース スコープの資格情報のアクセス許可|含まれるデータベース スコープ資格情報の権限|権限が含まれるデータベース権限|  
|----------------------------|---------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|CONTROL|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 権限の許可者 (または AS オプションで指定されたプリンシパル) は、GRANT OPTION によって与えられた権限を保持しているか、権限が暗黙的に与えられる上位の権限を保持している必要があります。  
  
 AS オプションを使用する場合は、次の追加要件があります。  
  
|AS *granting_principal*|必要な追加権限|  
|------------------------------|------------------------------------|  
|データベース ユーザー|メンバーシップ ユーザーに対する IMPERSONATE 権限、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
|Windows ログインにマップされているデータベース ユーザー|メンバーシップ ユーザーに対する IMPERSONATE 権限、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
|Windows グループにマップされているデータベース ユーザー|メンバーシップである Windows グループのメンバーシップ、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
|証明書にマップされているデータベース ユーザー|メンバーシップ、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
|非対称キーにマップされるデータベース ユーザー|メンバーシップ、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
|任意のサーバー プリンシパルにマップされていないデータベース ユーザー|メンバーシップ ユーザーに対する IMPERSONATE 権限、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
|データベース ロール|メンバーシップ、ロールに対する ALTER 権限、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
|アプリケーション ロール|メンバーシップ、ロールに対する ALTER 権限、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
  
 オブジェクトの所有者は、所有するオブジェクトの権限を許可できます。 セキュリティ保護可能なリソースに対して CONTROL 権限があるプリンシパルは、そのリソースの権限を許可できます。  
  
 メンバーなど、CONTROL SERVER 権限の付与、 **sysadmin**固定サーバー ロールは、いずれかに対する権限を許可できるサーバーのセキュリティ保護可能な。 メンバーなど、データベースに対する CONTROL 権限の付与、 **db_owner**固定データベース ロールがいずれかに対する権限を許可できるデータベースのセキュリティ保護可能な。 スキーマに対する CONTROL 権限が許可されているユーザーは、スキーマ内のオブジェクトに対する権限を許可できます。  
  
## <a name="see-also"></a>参照  
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [REVOKE データベース スコープ資格情報 (TRANSACT-SQL)](../../t-sql/statements/revoke-database-scoped-credential-transact-sql.md)   
 [データベース スコープ資格情報 (TRANSACT-SQL) を拒否します。](../../t-sql/statements/deny-database-scoped-credential-transact-sql.md)   
 [アクセス許可 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
