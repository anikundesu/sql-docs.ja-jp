---
title: "対称キー アクセス許可の付与 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2017
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
- symmetric keys [SQL Server], permissions
- permissions [SQL Server], symmetric keys
- encryption [SQL Server], symmetric keys
- GRANT statement, symmetric keys
- cryptography [SQL Server], symmetric keys
- granting permissions [SQL Server], symmetric keys
ms.assetid: 5c61557f-67ae-4e55-b86d-713575b27cea
caps.latest.revision: "28"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a80cd14f583074fa4d4d605c9f38b3df671d436d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="grant-symmetric-key-permissions-transact-sql"></a>GRANT (対称キーの権限の許可) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  対称キーの権限を許可します。 
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
GRANT permission [ ,...n ]    
    ON SYMMETRIC KEY :: symmetric_key_name   
    TO <database_principal> [ ,...n ] [ WITH GRANT OPTION ]  
        [ AS <database_principal> ]   
  
<database_principal> ::=   
        Database_user   
    | Database_role   
    | Application_role   
    | Database_user_mapped_to_Windows_User   
    | Database_user_mapped_to_Windows_Group   
    | Database_user_mapped_to_certificate   
    | Database_user_mapped_to_asymmetric_key   
    | Database_user_with_no_login   
```  
  
## <a name="arguments"></a>引数  
 *アクセス許可*  
 対称キーで許可できる権限を指定します。 権限の一覧については、後の「解説」を参照してください。  
  
 対称キー::*asymmetric_key_name*  
 権限を許可する対称キーを指定します。 スコープ修飾子 (::) が必要です。  
  
 \< *Database_principal*>  
 権限を許可するプリンシパルを指定します。  
  
 WITH GRANT OPTION  
 権限が許可されたプリンシパルが、この権限を他のプリンシパルにも許可できることを示します。  
  
 AS \<database_principal > このクエリを実行するプリンシパルが権限を許可する権利の派生元のプリンシパルを指定します。  
  
 *Database_user*  
 データベース ユーザーを指定します。  
  
 *Database_role*  
 データベース ロールを指定します。  
  
 *Application_role*  
 アプリケーション ロールを指定します。  
  
 *Database_user_mapped_to_Windows_User*  
 Windows ユーザーにマップされているデータベース ユーザーを指定します。  
  
 *Database_user_mapped_to_Windows_Group*  
 Windows グループにマップされているデータベース ユーザーを指定します。  
  
 *Database_user_mapped_to_certificate*  
 証明書にマップされているデータベース ユーザーを指定します。  
  
 *Database_user_mapped_to_asymmetric_key*  
 非対称キーにマップされているデータベース ユーザーを指定します。  
  
 *Database_user_with_no_login*  
 対応するサーバー レベルのプリンシパルがないデータベース ユーザーを指定します。  
  
## <a name="remarks"></a>解説  
 対称キーに関する情報は、 [sys.symmetric_keys](../../relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql.md)カタログ ビューです。  
  
 対称キーは、データベース レベルのセキュリティ保護可能なリソースで、権限の階層で親となっているデータベースに含まれています。 次の表に、対称キーで許可できる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に示します。  
  
|対称キー権限|権限が含まれる対称キー権限|権限が含まれるデータベース権限|  
|------------------------------|-----------------------------------------|------------------------------------|  
|ALTER|CONTROL|ALTER ANY SYMMETRIC KEY|  
|CONTROL|CONTROL|CONTROL|  
|REFERENCES|CONTROL|REFERENCES|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 権限の許可者 (または AS オプションで指定されたプリンシパル) は、GRANT OPTION によって与えられた権限を保持しているか、権限が暗黙的に与えられる上位の権限を保持している必要があります。  
  
 AS オプションを使用している場合は、次の追加要件が適用されます。  
  
|AS *granting_principal*|必要な追加権限|  
|------------------------------|------------------------------------|  
|データベース ユーザー|ユーザーに対する IMPERSONATE 権限、db_securityadmin 固定データベース ロールのメンバーシップ、db_owner 固定データベース ロールのメンバーシップ、または sysadmin 固定サーバー ロールのメンバーシップ。|  
|Windows ログインにマップされているデータベース ユーザー|ユーザーに対する IMPERSONATE 権限、db_securityadmin 固定データベース ロールのメンバーシップ、db_owner 固定データベース ロールのメンバーシップ、または sysadmin 固定サーバー ロールのメンバーシップ。|  
|Windows グループにマップされているデータベース ユーザー|Windows グループのメンバーシップ、db_securityadmin 固定データベース ロールのメンバーシップ、db_owner 固定データベース ロールのメンバーシップ、または sysadmin 固定サーバー ロールのメンバーシップ。|  
|証明書にマップされているデータベース ユーザー|db_securityadmin 固定データベース ロールのメンバーシップ、db_owner 固定データベース ロールのメンバーシップ、または sysadmin 固定サーバー ロールのメンバーシップ。|  
|非対称キーにマップされるデータベース ユーザー|db_securityadmin 固定データベース ロールのメンバーシップ、db_owner 固定データベース ロールのメンバーシップ、または sysadmin 固定サーバー ロールのメンバーシップ。|  
|任意のサーバー プリンシパルにマップされていないデータベース ユーザー|ユーザーに対する IMPERSONATE 権限、db_securityadmin 固定データベース ロールのメンバーシップ、db_owner 固定データベース ロールのメンバーシップ、または sysadmin 固定サーバー ロールのメンバーシップ。|  
|データベース ロール|ロールに対する ALTER 権限、db_securityadmin 固定データベース ロールのメンバーシップ、db_owner 固定データベース ロールのメンバーシップ、または sysadmin 固定サーバー ロールのメンバーシップ。|  
|アプリケーション ロール|ロールに対する ALTER 権限、db_securityadmin 固定データベース ロールのメンバーシップ、db_owner 固定データベース ロールのメンバーシップ、または sysadmin 固定サーバー ロールのメンバーシップ。|  
  
 セキュリティ保護可能なリソースに対して CONTROL 権限があるプリンシパルは、そのリソースの権限を許可できます。  
  
 sysadmin 固定サーバー ロールのメンバーなど、CONTROL SERVER 権限が許可されているユーザーは、サーバー内のセキュリティ保護可能なリソースに対する権限を許可できます。 db_owner 固定データベース ロールのメンバーなど、データベースに対する CONTROL 権限が許可されているユーザーは、データベース内のセキュリティ保護可能なリソースに対する権限を許可できます。  
  
## <a name="examples"></a>使用例  
 次の例では付与`ALTER`対称キーに対する権限`SamInventory42`データベース ユーザーに`HamidS`です。  
  
```  
USE AdventureWorks2012;  
GRANT ALTER ON SYMMETRIC KEY::SamInventory42 TO HamidS;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sys.symmetric_keys &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql.md)   
 [対称キーの権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-symmetric-key-permissions-transact-sql.md)   
 [対称キーの権限を REVOKE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-symmetric-key-permissions-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [アクセス許可 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

