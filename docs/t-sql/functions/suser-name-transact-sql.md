---
title: "SUSER_NAME (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SUSER_NAME
- SUSER_NAME_TSQL
dev_langs: TSQL
helpviewer_keywords:
- security identification names [SQL Server]
- logins [SQL Server], users
- identification names for logins [SQL Server]
- users [SQL Server], logins
- SUSER_NAME function
- logins [SQL Server], names
- names [SQL Server], logins
ms.assetid: ae598d9f-9baa-49b8-b1c1-042854206de4
caps.latest.revision: "29"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: cb236dc3ae7f74ad77ba398e328d4a0bf93a079b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="susername-transact-sql"></a>SUSER_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

  ユーザーのログイン識別名を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
SUSER_NAME ( [ server_user_id ] )   
```  
  
## <a name="arguments"></a>引数  
 *server_user_id*  
 ユーザーのログイン ID 番号です。 *server_user_id*、これは省略可能では、 **int**です。*server_user_id*任意のログイン id 番号を指定できます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインまたは[!INCLUDE[msCoName](../../includes/msconame-md.md)]Windows ユーザーまたはグループのインスタンスに接続する権限を持つ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 場合*server_user_id*が指定されていない、現在のユーザーのログインの識別名が返されます。 パラメーターに "NULL" という語が含まれていると、NULL が返されます。  
  
## <a name="return-types"></a>戻り値の型  
 **nvarchar (128)**  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]バージョン 7.0 では、セキュリティ id 番号 (SID) には、サーバー ユーザー識別番号 (SUID) が置き換えられます。  
  
 SUSER_NAME は、内のエントリを持つログインに対してのみログイン名を返します、 **syslogins**システム テーブル。  
  
 SUSER_NAME は、選択リストや WHERE 句、および式が許可される場所であればどこでも使用できます。ただし、パラメーターを指定しない場合であっても、その後に常にかっこを指定する必要があります。  
  
## <a name="examples"></a>使用例  
 次の例のログイン id 番号を持つユーザーのログインの識別名を返します`1`です。  
  
```  
SELECT SUSER_NAME(1);  
```  
  
## <a name="see-also"></a>参照  
 [SUSER_ID と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/suser-id-transact-sql.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
