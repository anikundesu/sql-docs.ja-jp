---
title: "サーバーのアクセス許可 (TRANSACT-SQL) を取り消す |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- permissions [SQL Server], servers
- REVOKE statement, server permissions
- servers [SQL Server], permissions
ms.assetid: 7b9a56b3-face-452e-a655-147dac306ba1
caps.latest.revision: "34"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 682afe6c9da8c675231c1cf7b505cb2c28813c26
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="revoke-server-permissions-transact-sql"></a>REVOKE (サーバーの権限の取り消し) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サーバー レベルの GRANT および DENY の権限を取り消します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
REVOKE [ GRANT OPTION FOR ] permission  [ ,...n ]   
    { TO | FROM } <grantee_principal> [ ,...n ]  
        [ CASCADE ]  
    [ AS <grantor_principal> ]   
  
<grantee_principal> ::= SQL_Server_login   
        | SQL_Server_login_mapped_to_Windows_login  
    | SQL_Server_login_mapped_to_Windows_group  
    | SQL_Server_login_mapped_to_certificate  
    | SQL_Server_login_mapped_to_asymmetric_key  
    | server_role  
  
<grantor_principal> ::= SQL_Server_login   
    | SQL_Server_login_mapped_to_Windows_login  
    | SQL_Server_login_mapped_to_Windows_group  
    | SQL_Server_login_mapped_to_certificate  
    | SQL_Server_login_mapped_to_asymmetric_key  
    | server_role  
```  
  
## <a name="arguments"></a>引数  
 *アクセス許可*  
 サーバーで許可できる権限を指定します。 権限の一覧については、後の「解説」を参照してください。  
  
 {に |FROM} \<grantee_principal > 元となる、権限を取り消すプリンシパルを指定します。  
  
 AS \<grantor_principal > このクエリを実行するプリンシパルの権限を取り消す権利の派生元のプリンシパルを指定します。  
  
 GRANT OPTION FOR  
 指定した権限を他のプリンシパルに許可するための権利が、取り消されます。 その権限自体は失効しません。  
  
> [!IMPORTANT]  
>  指定した権限が GRANT オプションなしでプリンシパルに許可されている場合は、その権限自体が取り消されます。  
  
 CASCADE  
 このプリンシパルによって権限が許可または拒否されている他のプリンシパルからも、同じ権限が取り消されることを示します。  
  
> [!CAUTION]  
>  WITH GRANT OPTION で許可されている権限を CASCADE で取り消すと、その権限の GRANT および DENY の両方が取り消されます。  
  
 *SQL_Server_login*  
 指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインします。  
  
 *SQL_Server_login_mapped_to_Windows_login*  
 指定します、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows ログインにマップされるログインです。  
  
 *SQL_Server_login_mapped_to_Windows_group*  
 指定します、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows グループにマップされるログインです。  
  
 *SQL_Server_login_mapped_to_certificate*  
 証明書にマップされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを指定します。  
  
 *SQL_Server_login_mapped_to_asymmetric_key*  
 指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]非対称キーにマップされるログインです。  
  
 *server_role*  
 ユーザー定義サーバー ロールを指定します。  
  
## <a name="remarks"></a>解説  
 サーバー スコープの権限を取り消すことができるのは、現在のデータベースが master のときだけです。  
  
 REVOKE では、GRANT と DENY の両方の権限が取り消されます。  
  
 指定した権限を許可するための権利を取り消すには、REVOKE GRANT OPTION FOR を使用します。 プリンシパルに、権限とその権限を許可する権利がある場合は、権限を許可する権利だけが取り消され、権限自体は取り消されません。 ただし、指定した権限が GRANT オプションなしでプリンシパルに許可されている場合は、その権限自体が取り消されます。  
  
 サーバー権限に関する情報を表示することができます、 [sys.server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md)でカタログ ビュー、およびサーバー プリンシパルに関する情報を表示できます、 [sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)カタログ ビューです。 サーバー ロールのメンバーシップに関する情報を表示できます、 [sys.server_role_members](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)カタログ ビューです。  
  
 サーバーは権限の階層の最上位となります。 次の表に、サーバーで取り消すことができる最も限定的な権限を示します。  
  
|サーバーのアクセス許可|権限が含まれるサーバー権限|  
|-----------------------|----------------------------------|  
|ADMINISTER BULK OPERATIONS|CONTROL SERVER|  
|ALTER ANY AVAILABILITY GROUP<br /><br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|CONTROL SERVER|  
|ALTER ANY CONNECTION|CONTROL SERVER|  
|ALTER ANY CREDENTIAL|CONTROL SERVER|  
|ALTER ANY DATABASE|CONTROL SERVER|  
|ALTER ANY ENDPOINT|CONTROL SERVER|  
|ALTER ANY EVENT NOTIFICATION|CONTROL SERVER|  
|ALTER ANY EVENT SESSION|CONTROL SERVER|  
|ALTER ANY LINKED SERVER|CONTROL SERVER|  
|ALTER ANY LOGIN|CONTROL SERVER|  
|ALTER ANY SERVER AUDIT|CONTROL SERVER|  
|ALTER ANY SERVER ROLE<br /><br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|CONTROL SERVER|  
|ALTER RESOURCES|CONTROL SERVER|  
|ALTER SERVER STATE|CONTROL SERVER|  
|ALTER SETTINGS|CONTROL SERVER|  
|ALTER TRACE|CONTROL SERVER|  
|AUTHENTICATE SERVER|CONTROL SERVER|  
|CONNECT ANY DATABASE<br /><br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|CONTROL SERVER|  
|CONNECT SQL|CONTROL SERVER|  
|CONTROL SERVER|CONTROL SERVER|  
|CREATE ANY DATABASE|ALTER ANY DATABASE|  
|CREATE AVAILABILITY GROUP<br /><br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|ALTER ANY AVAILABILITY GROUP|  
|CREATE DDL EVENT NOTIFICATION|ALTER ANY EVENT NOTIFICATION|  
|CREATE ENDPOINT|ALTER ANY ENDPOINT|  
|CREATE SERVER ROLE<br /><br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|ALTER ANY SERVER ROLE|  
|CREATE TRACE EVENT NOTIFICATION|ALTER ANY EVENT NOTIFICATION|  
|EXTERNAL ACCESS ASSEMBLY|CONTROL SERVER|  
|IMPERSONATE ANY LOGIN<br /><br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|CONTROL SERVER|  
|SELECT ALL USER SECURABLES<br /><br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|CONTROL SERVER|  
|SHUTDOWN|CONTROL SERVER|  
|UNSAFE ASSEMBLY|CONTROL SERVER|  
|VIEW ANY DATABASE|VIEW ANY DEFINITION|  
|VIEW ANY DEFINITION|CONTROL SERVER|  
|VIEW SERVER STATE|ALTER SERVER STATE|  
  
## <a name="permissions"></a>Permissions  
 CONTROL SERVER 権限、または sysadmin 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-revoking-a-permission-from-a-login"></a>A. ログインから権限を取り消す  
 次の例では失効`VIEW SERVER STATE`からのアクセス許可、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン`WanidaBenshoof`です。  
  
```  
USE master;  
REVOKE VIEW SERVER STATE FROM WanidaBenshoof;  
GO  
```  
  
### <a name="b-revoking-the-with-grant-option"></a>B. WITH GRANT オプションを取り消す  
 次の例では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン `CONNECT SQL` から、`JanethEsteves` を許可する権利を取り消します。  
  
```  
USE master;  
REVOKE GRANT OPTION FOR CONNECT SQL FROM JanethEsteves;  
GO  
```  
  
 ログインは引き続き CONNECT SQL 権限を保持しますが、他のプリンシパルに権限を許可することはできなくなります。  
  
## <a name="see-also"></a>参照  
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)   
 [サーバーのアクセス許可 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-server-permissions-transact-sql.md)   
 [サーバーのアクセス許可 (TRANSACT-SQL) の取り消し](../../t-sql/statements/revoke-server-permissions-transact-sql.md)   
 [権限の階層 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)   
 [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [sys.fn_my_permissions &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)   
 [HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/has-perms-by-name-transact-sql.md)  
  
  

