---
title: "ad hoc distributed queries サーバー構成オプション | Microsoft Docs"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OPENROWSET function, ad hoc distributed queries option
- Ad Hoc Distributed Queries option
- ad hoc distributed queries
- 7415 (Database Engine Error)
- OPENDATASOURCE function, ad hoc distributed queries option
- ad hoc access
ms.assetid: 5b982015-e196-44c3-83b8-275fb9d769b2
caps.latest.revision: "29"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: e871bd2f5a6c54be5152f2259b82048fc3b2d237
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="ad-hoc-distributed-queries-server-configuration-option"></a>ad hoc distributed queries サーバー構成オプション
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定では、OPENROWSET および OPENDATASOURCE を使用したアドホックな分散クエリは実行できません。 このオプションを 1 に設定すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でアドホック アクセスを実行できます。 このオプションを設定しなかった場合または 0 に設定した場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でアドホック アクセスを実行できません。  
  
 アドホック分散クエリの実行時には、OLE DB を使用するリモート データ ソースへの接続に OPENROWSET 関数および OPENDATASOURCE 関数が使用されます。 OPENROWSET 関数および OPENDATASOURCE 関数は、アクセス頻度の低い OLE DB データ ソースを参照する目的のみに使用してください。 何度もアクセスするデータ ソースに対しては、リンク サーバーを定義してください。  
  
> [!IMPORTANT]  
>  アドホック名を使用できるようにすると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への認証済みログインであればプロバイダーにアクセスできるようになります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の管理者は、ローカル ログインからアクセスされても安全なプロバイダーに対してのみ、この機能を有効にしてください。  
  
## <a name="remarks"></a>解説  
 **アドホック分散クエリ** を有効にせずにアドホック接続を試みると、次のエラーが発生します (メッセージ 7415、レベル 16、状態 1、行 1)。  
  
 OLE DB プロバイダー 'Microsoft.ACE.OLEDB.12.0' へのアドホック アクセスが拒否されました。 リンク サーバー経由でこのプロバイダーにアクセスしてください。  
  
## <a name="examples"></a>使用例  
 次の例では、アドホック分散クエリを有効にし、 `Seattle1` 関数を使用して `OPENROWSET` という名前のサーバーにクエリを実行します。  
  
```  
sp_configure 'show advanced options', 1;  
RECONFIGURE;
GO 
sp_configure 'Ad Hoc Distributed Queries', 1;  
RECONFIGURE;  
GO  
  
SELECT a.*  
FROM OPENROWSET('SQLNCLI', 'Server=Seattle1;Trusted_Connection=yes;',  
     'SELECT GroupName, Name, DepartmentID  
      FROM AdventureWorks2012.HumanResources.Department  
      ORDER BY GroupName, Name') AS a;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [リンク サーバー &#40;データベース エンジン&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md)   
 [OPENROWSET &#40;Transact-SQL&#41;](../../t-sql/functions/openrowset-transact-sql.md)   
 [OPENDATASOURCE &#40;Transact-SQL&#41;](../../t-sql/functions/opendatasource-transact-sql.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)  
  
  
