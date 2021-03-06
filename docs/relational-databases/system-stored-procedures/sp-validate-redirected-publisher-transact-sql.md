---
title: "sp_validate_redirected_publisher (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_validate_redirected_publisher
- sp_validate_redirected_publisher_TSQL
helpviewer_keywords: sp_validate_redirected_publisher
ms.assetid: 2b7fdbad-17e4-4442-b0b2-9b5e8f84b91d
caps.latest.revision: "9"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bafe71c88b5fc47c822275ebfb9be102db65b22b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spvalidateredirectedpublisher-transact-sql"></a>sp_validate_redirected_publisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  パブリッシング データベースの現在のホストがレプリケーションをサポートできることを確認します。 ディストリビューション データベースから実行する必要があります。 このプロシージャを呼び出す**sp_get_redirected_publisher**です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
      sp_validate_redirected_publisher   
    [ @original_publisher = ] 'original_publisher',  
    [ @publisher_db = ] 'database_name',   
    [ @redirected_publisher = ] 'new_publisher' output  
```  
  
## <a name="arguments"></a>引数  
 [  **@original_publisher**  =] **'***original_publisher***'**  
 インスタンスの名前[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースを最初に発行します。 *original_publisher*は**sysname**、既定値はありません。  
  
 [  **@publisher_db**  =] **'***publisher_db***'**  
 パブリッシュされるデータベースの名前。 *publisher_db*は**sysname**、既定値はありません。  
  
 [  **@redirected_publisher**  =] **'***redirected_publisher***'**  
 リダイレクトの対象では、ときに指定された**sp_redirect_publisher**パブリッシャー/データベース ペアに対して呼び出されました。 *redirected_publisher*は**sysname**、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 [なし] :  
  
## <a name="remarks"></a>解説  
 パブリッシャーとパブリッシングのデータベースのエントリが存在しない場合**sp_validate_redirected_publisher**は出力パラメーターに null を返します *@redirected_publisher*です。 エントリが存在する場合は、成功した場合も失敗した場合も出力パラメーターでそのエントリが返されます。  
  
 検証が成功すると、 **sp_validate_redirected_publisher**成功を示す値を返します。  
  
 検証が失敗した場合は、失敗を説明するエラーが発生します。  
  
## <a name="permissions"></a>Permissions  
 呼び出し元必要がありますいずれかのメンバーである、 **sysadmin**固定サーバー ロール、 **db_owner**定義済みパブリケーションのパブリケーション アクセス リストのメンバーまたはディストリビューション データベースの固定データベース ロールパブリッシャー データベースと関連付けられています。  
  
## <a name="see-also"></a>参照  
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_get_redirected_publisher &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-get-redirected-publisher-transact-sql.md)   
 [sp_redirect_publisher &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-redirect-publisher-transact-sql.md)   
 [sp_validate_replica_hosts_as_publishers &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-validate-replica-hosts-as-publishers-transact-sql.md)  
  
  
