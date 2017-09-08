---
title: "RESTORE MASTER KEY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RESTORE_MASTER_KEY_TSQL
- RESTORE MASTER KEY
- LOAD_MASTER_KEY_TSQL
- LOAD MASTER KEY
dev_langs:
- TSQL
helpviewer_keywords:
- database master key [SQL Server], importing
- encryption [SQL Server], Database Master Key
- copying Database Master Keys
- importing Database Master Keys
- cryptography [SQL Server], Database Master Key
- transferring Database Master Keys
- RESTORE MASTER KEY statement
ms.assetid: 70ceb951-31a2-4fc4-a0c1-e6c18eeb3ae7
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 941c6bd886615588ca74bf92de6665e25db224a0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="restore-master-key-transact-sql"></a>RESTORE MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  バックアップ ファイルからデータベースのマスター キーをインポートします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
RESTORE MASTER KEY FROM FILE = 'path_to_file'   
    DECRYPTION BY PASSWORD = 'password'  
    ENCRYPTION BY PASSWORD = 'password'  
    [ FORCE ]  
```  
  
## <a name="arguments"></a>引数  
 ファイル ='*path_to_file*'  
 格納されているデータベース マスター キーへの完全なパスを、ファイル名を含めて指定します。 *path_to_file*ローカル パスまたはネットワーク上の場所への UNC パスを指定できます。  
  
 DECRYPTION BY PASSWORD ='*パスワード*'  
 ファイルからインポートされるデータベース マスター キーの暗号化解除に必要なパスワードを指定します。  
  
 ENCRYPTION BY PASSWORD ='*パスワード*'  
 データベースに読み込まれた後、データベース マスター キーの暗号化に使用されるパスワードを指定します。  
  
 FORCE  
 復元処理を続行する、現在のデータベース マスター_キーが開いていない場合でも、または場合を指定します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]いくつか使用して暗号化された秘密キーの暗号化を解除できません。  
  
## <a name="remarks"></a>解説  
 マスター キーを復元するとき、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では現在アクティブなマスター キーによって暗号化されたすべてのキーの暗号化が解除された後、復元されたマスター キーを使用してこれらのキーが暗号化されます。 この操作はリソースを大量に消費するため、リソース要求が少ないときに実行するように考慮してください。 現在のデータベースのマスター キーが開いていないか、開けない場合、またはマスター キーで暗号化されたキーを 1 つでも暗号化解除できない場合、復元操作は失敗します。  
  
 FORCE オプションは、マスター キーを取得できないか、暗号化解除が失敗する場合にのみ使用してください。 取得できないキーによってのみ暗号化されている情報は失われます。  
  
 マスター キーがサービス マスター キーで暗号化されている場合は、復元されたマスター キーもサービス マスター キーで暗号化されます。  
  
 現在のデータベースにマスター キーが存在しない場合は、RESTORE MASTER KEY を実行するとマスター キーが作成されます。 この新しいマスター キーは、サービス マスター キーで自動的に暗号化されません。  
  
## <a name="permissions"></a>Permissions  
 データベースに対する CONTROL 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、データベース `AdventureWorks2012` のマスター キーを復元します。  
  
```  
USE AdventureWorks2012;  
RESTORE MASTER KEY   
    FROM FILE = 'c:\backups\keys\AdventureWorks2012_master_key'   
    DECRYPTION BY PASSWORD = '3dH85Hhk003#GHkf02597gheij04'   
    ENCRYPTION BY PASSWORD = '259087M#MyjkFkjhywiyedfgGDFD';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [CREATE MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-master-key-transact-sql.md)   
 [ALTER MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-master-key-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  