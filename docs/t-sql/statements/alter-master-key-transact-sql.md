---
title: "ALTER MASTER KEY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, database-engine, pdw, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER MASTER KEY
- ALTER_MASTER_KEY_TSQL
dev_langs: TSQL
helpviewer_keywords:
- REGENERATE phrase
- ALTER MASTER KEY statement
- decryption [SQL Server], Database Master Key
- FORCE option
- encryption [SQL Server], Database Master Key
- database master key [SQL Server], modifying
- cryptography [SQL Server], Database Master Key
- modifying Database Master Key
- service master key [SQL Server], modifying
- DROP ENCRYPTION BY SERVICE MASTER KEY phrase
ms.assetid: 8ac501c3-4280-4d5b-b58a-1524fa715b50
caps.latest.revision: "49"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 0e664b594017b7131553869d1696708eae3b52b0
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="alter-master-key-transact-sql"></a>ALTER MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  データベース マスター キーのプロパティを変更します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server  
  
ALTER MASTER KEY <alter_option>  
  
<alter_option> ::=  
    <regenerate_option> | <encryption_option>  
  
<regenerate_option> ::=  
    [ FORCE ] REGENERATE WITH ENCRYPTION BY PASSWORD = 'password'  
  
<encryption_option> ::=  
    ADD ENCRYPTION BY { SERVICE MASTER KEY | PASSWORD = 'password' }  
    |   
    DROP ENCRYPTION BY { SERVICE MASTER KEY | PASSWORD = 'password' }  
```  
```  
-- Syntax for Azure SQL Database
-- Note: DROP ENCRYPTION BY SERVICE MASTER KEY is not supported on Azure SQL Database.
  
ALTER MASTER KEY <alter_option>  
  
<alter_option> ::=  
    <regenerate_option> | <encryption_option>  
  
<regenerate_option> ::=  
    [ FORCE ] REGENERATE WITH ENCRYPTION BY PASSWORD = 'password'  
  
<encryption_option> ::=  
    ADD ENCRYPTION BY { SERVICE MASTER KEY | PASSWORD = 'password' }  
    |   
    DROP ENCRYPTION BY { PASSWORD = 'password' }  
```  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
ALTER MASTER KEY <alter_option>  
  
<alter_option> ::=  
    <regenerate_option> | <encryption_option>  
  
<regenerate_option> ::=  
    [ FORCE ] REGENERATE WITH ENCRYPTION BY PASSWORD ='password'<encryption_option> ::=  
    ADD ENCRYPTION BY SERVICE MASTER KEY   
    |   
    DROP ENCRYPTION BY SERVICE MASTER KEY  
```  
  
## <a name="arguments"></a>引数  
 パスワード ='*パスワード*'  
 データベース マスター キーを暗号化または暗号化解除するパスワードを指定します。 *パスワード*のインスタンスを実行しているコンピューターの Windows パスワード ポリシーの要件を満たす必要がある[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
## <a name="remarks"></a>解説  
 REGENERATE オプションを指定すると、データベース マスター キーと、それによって保護されるすべてのキーが再作成されます。 これらのキーは、最初に元のマスター キーで暗号化解除され、次に新しいマスター キーで暗号化されます。 この操作はリソースを大量に消費するため、マスター キーのセキュリティに問題がある場合を除き、リソース要求が少ないときに実行するように考慮してください。  
  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] AES 暗号化アルゴリズムを使用してサービス マスター キー (SMK) とデータベース マスター キー (DMK) を保護します。 AES は、以前のバージョンで使用されていた 3DES よりも新しい暗号化アルゴリズムです。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスを [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] にアップグレードした後で、マスター キーを AES にアップグレードするために SMK と DMK を再度生成する必要があります。 SMK の再作成の詳細については、次を参照してください。 [ALTER SERVICE MASTER KEY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-service-master-key-transact-sql.md).  
  
 FORCE オプションを指定すると、マスター キーを使用できなかった場合や、暗号化されているすべての秘密キーをサーバーで暗号化解除できなかった場合でも、キーの再生成が続行されます。 マスター _ キーを開けない場合を使用して、 [RESTORE MASTER KEY](../../t-sql/statements/restore-master-key-transact-sql.md)をバックアップから、マスター _ キーを復元するステートメント。 FORCE オプションは、マスター キーを取得できないか、暗号化解除が失敗する場合にのみ使用してください。 取得できないキーによってのみ暗号化されている情報は失われます。  
  
 DROP ENCRYPTION BY SERVICE MASTER KEY オプションを指定すると、データベース マスター キーの暗号化がサービス マスター キーによって解除されます。  
  
 ADD ENCRYPTION BY SERVICE MASTER KEY を指定すると、マスター キーのコピーがサービス マスター キーを使用して暗号化され、現在のデータベースおよびマスターの両方に格納されます。  
  
## <a name="permissions"></a>Permissions  
 データベースに対する CONTROL 権限が必要です。 データベース マスター キーがパスワードで暗号化されている場合は、パスワードの情報も必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、新しいデータベースのマスター_キー、`AdventureWorks`し、暗号化階層の下位にあるキーによりまで再び暗号化します。  
  
```  
USE AdventureWorks2012;  
ALTER MASTER KEY REGENERATE WITH ENCRYPTION BY PASSWORD = 'dsjdkflJ435907NnmM#sX003';  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例では、新しいデータベースのマスター_キー、`AdventureWorksPDW2012`暗号化階層の下にあるキーが再暗号化します。  
  
```  
USE master;  
ALTER MASTER KEY REGENERATE WITH ENCRYPTION BY PASSWORD = 'dsjdkflJ435907NnmM#sX003';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [CREATE MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-master-key-transact-sql.md)   
 [MASTER KEY &#40; を開くTRANSACT-SQL と #41 です。](../../t-sql/statements/open-master-key-transact-sql.md)   
 [CLOSE MASTER KEY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/close-master-key-transact-sql.md)   
 [BACKUP MASTER KEY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/backup-master-key-transact-sql.md)   
 [RESTORE MASTER KEY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/restore-master-key-transact-sql.md)   
 [DROP MASTER KEY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-master-key-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [データベースのデタッチとアタッチ &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)  
  
  

