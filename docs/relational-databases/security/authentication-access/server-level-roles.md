---
title: "サーバー レベルのロール | Microsoft Docs"
ms.custom: 
ms.date: 05/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, pdw
ms.service: 
ms.component: security
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.Security.NT_AUTHORITY.SYSTEM
- sql13.Security.BUILTIN.administrators
helpviewer_keywords:
- roles [SQL Server], server-level
- principals [SQL Server], server-level
- CONTROL SERVER permission
- fixed server roles [SQL Server]
- credentials [SQL Server], roles
- sysadmin fixed server role
- server-level roles [SQL Server]
- authentication [SQL Server], roles
ms.assetid: 7adf2ad7-015d-4cbe-9e29-abaefd779008
caps.latest.revision: "52"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: a095d9f3e7839a2f3cfa14a2bf49790776f0cd1b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="server-level-roles"></a>サーバー レベルのロール
[!INCLUDE[appliesto-ss-xxxx-xxxx-pdw-md](../../../includes/appliesto-ss-xxxx-xxxx-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、サーバー上の権限を管理するためのサーバー レベルのロールを提供します。 これらのロールは、他のプリンシパルをグループ化するセキュリティ プリンシパルです。 サーバー レベルのロールは、その権限のスコープがサーバー全体に及びます (*ロール* は、Windows オペレーティング システムの *グループ* に似ています)。  
  
 固定サーバー ロールは、旧バージョンとの互換性を維持するために便宜的に提供されています。 可能な限り、より詳細な権限を割り当ててください。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、9 つの固定サーバー ロールを提供します。 固定サーバー ロール (**public** を除く) に許可される権限は変更できません。 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]以降では、ユーザー定義のサーバー ロールを作成し、そのユーザー定義のサーバー ロールにサーバー レベルの権限を追加できます。  
  
 サーバー レベルのロールには、サーバー レベルのプリンシパル ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログイン、Windows アカウント、および Windows グループ) を追加できます。 固定サーバー ロールの各メンバーは、そのロールに他のログインを追加することができます。 ユーザー定義のサーバー ロールのメンバーは、そのロールに他のサーバー プリンシパルを追加できません。  
>  [!NOTE]
>  サーバー レベルの権限は、SQL Database や SQL Data Warehouse では使用できません。 SQL Database の詳細については、「[データベース アクセスの制御と許可](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins)」を参照してください。
  
## <a name="fixed-server-level-roles"></a>固定サーバー レベル ロール  
 次の表に、固定サーバー レベル ロールとその機能を示します。  
  
|固定サーバー レベル ロール|説明|  
|------------------------------|-----------------|  
|**sysadmin**|**sysadmin** 固定サーバー ロールのメンバーは、サーバーに対するすべての操作を実行できます。|  
|**serveradmin**|**serveradmin** 固定サーバー ロールのメンバーは、サーバー全体の構成オプションを変更したり、サーバーをシャットダウンしたりできます。|  
|**securityadmin**|**securityadmin** 固定サーバー ロールのメンバーは、ログインとログインのプロパティを管理します。 サーバー レベルの権限を `GRANT`、`DENY`、`REVOKE` することができます。 また、データベースにアクセスできる場合は、データベース レベルの権限も `GRANT`、`DENY`、`REVOKE` できます。 また、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインのパスワードをリセットできます。<br /><br /> **重要:** セキュリティ管理者は、[!INCLUDE[ssDE](../../../includes/ssde-md.md)]へのアクセスを許可する権限およびユーザー権限を構成する権限を使用して、ほとんどのサーバー権限を割り当てることができます。 **securityadmin** ロールは、 **sysadmin** ロールと同等のものとして扱う必要があります。|  
|**processadmin**|**processadmin** 固定サーバー ロールのメンバーは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンス内で実行中のプロセスを終了できます。|  
|**setupadmin**|**setupadmin** 固定サーバー ロールのメンバーは、[!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを使用して、リンク サーバーを追加および削除できます  (**sysadmin** メンバーシップは、[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] を使用するときに必要になります)。|  
|**bulkadmin**|**bulkadmin** 固定サーバー ロールのメンバーは、`BULK INSERT` ステートメントを実行できます。|  
|**diskadmin**|**diskadmin** 固定サーバー ロールは、ディスク ファイルを管理するために使用します。|  
|**dbcreator**|**dbcreator** 固定サーバー ロールのメンバーは、任意のデータベースを作成、変更、削除、および復元できます。|  
|**public**|すべての [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインは、**public** サーバー ロールに属しています。 サーバー プリンシパルにセキュリティ保護可能なオブジェクトに対する特定の権限が与えられていないか権限が拒否されている場合、そのユーザーは、そのオブジェクトに対して public に付与されている権限を継承します。 すべてのユーザーがオブジェクトを使用できるようにする場合は、対象のオブジェクトに public 権限のみを割り当てます。 public のメンバーシップを変更することはできません。<br /><br /> **注:** **public** 他のロールと実装方法が異なり、public 固定サーバー ロールからは権限を許可、拒否、または取り消しすることができます。|  
  
## <a name="permissions-of-fixed-server-roles"></a>固定サーバー ロールの権限  
 各固定サーバー ロールには、特定の権限が割り当てられます。 次の図は、サーバー ロールに割り当てられている権限を示しています。   
![fixed_server_role_permissions](../../../relational-databases/security/authentication-access/media/permissions-of-server-roles.png)   
  
> [!IMPORTANT]  
>  **CONTROL SERVER** 権限は **sysadmin** 固定サーバー ロールと似ていますが、同じではありません。 権限があることはロールのメンバーシップを意味せず、ロールのメンバーシップによって権限は付与されません。 (例: **CONTROL SERVER** は **sysadmin** 固定サーバー ロールのメンバーシップを意味しません)。ただし、ロールと同等の権限の間で借用が可能な場合があります。 ほとんどの **DBCC** コマンドと多くのシステム プロシージャには、**sysadmin** 固定サーバー ロールのメンバーシップが必要です。 **sysadmin** メンバーシップを必要とする 171 のシステム ストアド プロシージャの一覧については、Andreas Wolter によるブログ投稿「 [CONTROL SERVER と sysadmin/sa: 権限、システム プロシージャ、DBCC、自動スキーマ作成、および特権のエスカレーション - 注意](http://www.insidesql.org/blogs/andreaswolter/2013/08/control-server-vs-sysadmin-sa-permissions-privilege-escalation-caveats)」を参照してください。  
  
## <a name="server-level-permissions"></a>サーバーレベルの権限  
 ユーザー定義のサーバー ロールに追加できるのは、サーバー レベルの権限のみです。 サーバー レベルの権限の一覧を表示するには、次のステートメントを実行します。 サーバー レベルの権限は、次のとおりです。  
  
```  
SELECT * FROM sys.fn_builtin_permissions('SERVER') ORDER BY permission_name;  
```  
  
 権限の詳細については、「[アクセス許可 (データベース エンジン)](../../../relational-databases/security/permissions-database-engine.md)」および「[sys.fn_builtin_permissions &#40;Transact-SQL&#41;](../../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)」を参照してください。  
  
## <a name="working-with-server-level-roles"></a>サーバー レベルのロールの操作  
 次の表では、サーバー レベルのロールを操作するためのコマンド、ビュー、および関数について説明します。  
  
|機能|型|説明|  
|-------------|----------|-----------------|  
|[sp_helpsrvrole &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-helpsrvrole-transact-sql.md)|メタデータ|サーバー レベルのロールの一覧を返します。|  
|[sp_helpsrvrolemember &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-helpsrvrolemember-transact-sql.md)|メタデータ|サーバー レベルのロールのメンバーに関する情報を返します。|  
|[sp_srvrolepermission &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-srvrolepermission-transact-sql.md)|メタデータ|サーバー レベルのロールの権限を表示します。|  
|[IS_SRVROLEMEMBER &#40;Transact-SQL&#41;](../../../t-sql/functions/is-srvrolemember-transact-sql.md)|メタデータ|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインが、指定されたサーバー レベルのロールのメンバーであるかどうかを示します。|  
|[sys.server_role_members &#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)|メタデータ|各サーバー レベルのロールのメンバーごとに 1 行のデータを返します。|  
|[sp_addsrvrolemember &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md)|Command|ログインをサーバー レベルのロールのメンバーとして追加します。 非推奨。 代わりに [ALTER SERVER ROLE](../../../t-sql/statements/alter-server-role-transact-sql.md) を使用してください。|  
|[sp_dropsrvrolemember &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql.md)|Command|サーバー レベルのロールから、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインや、Windows ユーザーまたはグループを削除します。 非推奨。 代わりに [ALTER SERVER ROLE](../../../t-sql/statements/alter-server-role-transact-sql.md) を使用してください。|  
|[CREATE SERVER ROLE &#40;Transact-SQL&#41;](../../../t-sql/statements/create-server-role-transact-sql.md)|Command|ユーザー定義サーバー ロールを作成します。|  
|[ALTER SERVER ROLE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-server-role-transact-sql.md)|Command|サーバー ロールのメンバーシップを変更、またはユーザー定義のサーバー ロールの名前を変更します。|  
|[DROP SERVER ROLE &#40;Transact-SQL&#41;](../../../t-sql/statements/drop-server-role-transact-sql.md)|Command|ユーザー定義サーバー ロールを削除します。|  
|[IS_SRVROLEMEMBER &#40;Transact-SQL&#41;](../../../t-sql/functions/is-srvrolemember-transact-sql.md)|関数|サーバー ロールのメンバーシップを決定します。|  
  
## <a name="see-also"></a>参照  
 [データベース レベルのロール](../../../relational-databases/security/authentication-access/database-level-roles.md)   
 [セキュリティ カタログ ビュー &#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [セキュリティ関数 &#40;Transact-SQL&#41;](../../../t-sql/functions/security-functions-transact-sql.md)   
 [SQL Server の保護](../../../relational-databases/security/securing-sql-server.md)   
 [GRANT (サーバー プリンシパルの権限の許可) &#40;Transact-SQL&#41;](../../../t-sql/statements/grant-server-principal-permissions-transact-sql.md)   
 [REVOKE (サーバー プリンシパルの権限の取り消し) &#40;Transact-SQL&#41;](../../../t-sql/statements/revoke-server-principal-permissions-transact-sql.md)   
 [DENY (サーバー プリンシパルの権限の拒否) &#40;Transact-SQL&#41;](../../../t-sql/statements/deny-server-principal-permissions-transact-sql.md)   
 [サーバー ロールの作成](../../../relational-databases/security/authentication-access/create-a-server-role.md)  
  
  
