---
title: "sp_change_users_login (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/13/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_change_users_login
- sp_change_users_login_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_change_users_login
ms.assetid: 1554b39f-274b-4ef8-898e-9e246b474333
caps.latest.revision: "43"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 207272f7644ab39055b7c6bb330faf6053353601
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spchangeuserslogin-transact-sql"></a>sp_change_users_login (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  マップする既存のデータベース ユーザー、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインします。 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]使用して[ALTER USER](../../t-sql/statements/alter-user-transact-sql.md)代わりにします。  
  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_change_users_login [ @Action = ] 'action'   
    [ , [ @UserNamePattern = ] 'user' ]   
    [ , [ @LoginName = ] 'login' ]   
    [ , [ @Password = ] 'password' ]  
[;]  
```  
  
## <a name="arguments"></a>引数  
 [ @Action=] '*アクション*'  
 プロシージャにより実行されるアクションの説明です。 *アクション*は**varchar (10)**です。 *アクション*値は次のいずれかを持つことができます。  
  
|値|Description|  
|-----------|-----------------|  
|**Auto_Fix**|現在のデータベース内の sys.database_principals システム カタログ ビューにあるユーザー エントリを、同じ名前の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインにリンクします。 同じ名前のログインが存在しない場合は、新しく作成されます。 結果を**Auto_Fix**の適切なリンクが実際に作成されたことを確認するステートメント。 使用しないでください**Auto_Fix**セキュリティ上重要な状況でします。<br /><br /> 使用すると**Auto_Fix**を指定する必要があります*ユーザー*と*パスワード*ログインが既に存在しない場合は、それ以外の場合を指定してください*ユーザー*が*パスワード*は無視されます。 *ログイン*NULL にする必要があります。 *ユーザー*現在のデータベースで有効なユーザーである必要があります。 別のユーザーがマップされているログインは使用できません。|  
|**レポート**|現在のデータベース内で、どのログインにもリンクされていないユーザーと、対応するセキュリティ識別子 (SID) を一覧表示します。 *ユーザー*、*ログイン*、および*パスワード*NULL であるか、指定されていません。<br /><br /> 置き換えるにはレポート オプションは、システム テーブルを使用してクエリを使用して、比較のエントリ**sys.server_prinicpals**のエントリを**sys.database_principals**です。|  
|**Update_One**|指定したリンク*ユーザー* 、現在のデータベースを既存の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]*ログイン*です。 *ユーザー*と*ログイン*指定する必要があります。 *パスワード*NULL であるか、指定されていません。|  
  
 [ @UserNamePattern=] '*ユーザー*'  
 現在のデータベースに存在するユーザーの名前を指定します。 *ユーザー*は**sysname**、既定値は NULL です。  
  
 [ @LoginName=] '*ログイン*'  
 名前を指定、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインします。 *ログイン*は**sysname**、既定値は NULL です。  
  
 [ @Password=] '*パスワード*'  
 新しいに割り当てられているパスワードは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を指定して作成されたログイン**Auto_Fix**です。 一致するログインが既に存在する場合、ユーザーとログインがマップと*パスワード*は無視されます。 Sp_change_users_login が新たに作成一致するログインが存在しない場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインと割り当てます*パスワード*新しいログインのパスワードとして。 *パスワード*は**sysname**NULL にする必要がありません。  
  
> **重要!!** 常に使用する、[強力なパスワードです。](../../relational-databases/security/strong-passwords.md)
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|UserName|**sysname**|データベース ユーザー名。|  
|UserSID|**varbinary (85)**|ユーザーのセキュリティ識別子。|  
  
## <a name="remarks"></a>解説  
 sp_change_users_login は、現在のデータベースのデータベース ユーザーを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインとリンクする場合に使用します。 ユーザーのログインが既に変更されている場合は、sp_change_users_login を使用してユーザーを新しいログインにリンクすれば、ユーザーの権限が失われることはありません。 新しい*ログイン*sa にすることはできません、*ユーザー*dbo、guest、または INFORMATION_SCHEMA ユーザーにすることはできません。  
  
 sp_change_users_login は、データベース ユーザーを Windows レベルのプリンシパル、証明書、または非対称キーにマップする場合は使用できません。  
  
 sp_change_users_login は、Windows プリンシパルから作成された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインや、CREATE USER WITHOUT LOGIN を使用して作成されたユーザーでは使用できません。  
  
 ユーザー定義のトランザクション内では、sp_change_users_login は実行できません。  
  
## <a name="permissions"></a>Permissions  
 db_owner 固定データベース ロールのメンバーシップが必要です。 Sysadmin 固定サーバー ロールのメンバーのみを指定できます、 **Auto_Fix**オプション。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-showing-a-report-of-the-current-user-to-login-mappings"></a>A. 現在のユーザーとログインの対応関係を示すレポートを表示する  
 次の例では、現在のデータベース内のユーザーと各ユーザーのセキュリティ識別子 (SID) を示すレポートを作成します。  
  
```  
EXEC sp_change_users_login 'Report';  
```  
  
### <a name="b-mapping-a-database-user-to-a-new-sql-server-login"></a>B. データベース ユーザーを新しい SQL Server ログインにマップする  
 次の例では、データベース ユーザーは、新しい関連付け[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインします。 データベース ユーザー `MB-Sales`、最初は、別のログインにマップが再マップのログインに`MaryB`です。  
  
```  
--Create the new login.  
CREATE LOGIN MaryB WITH PASSWORD = '982734snfdHHkjj3';  
GO  
--Map database user MB-Sales to login MaryB.  
USE AdventureWorks2012;  
GO  
EXEC sp_change_users_login 'Update_One', 'MB-Sales', 'MaryB';  
GO  
```  
  
### <a name="c-automatically-mapping-a-user-to-a-login-creating-a-new-login-if-it-is-required"></a>C. ユーザーをログインに自動的にマップし、必要に応じて新しいログインを作成する  
 次の例は、使用する方法を示しています。 `Auto_Fix` 、同じ名前のログインにマップされて、既存のユーザーを作成したり、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン`Mary`パスワードを持つ`B3r12-3x$098f6`場合、ログイン`Mary`存在しません。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_change_users_login 'Auto_Fix', 'Mary', NULL, 'B3r12-3x$098f6';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [sp_adduser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adduser-transact-sql.md)   
 [sp_helplogins &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helplogins-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)  
  
  
