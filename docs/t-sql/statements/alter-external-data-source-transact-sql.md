---
title: "外部データ ソース (TRANSACT-SQL) を ALTER |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER EXTERNAL DATA SOURCE
- ALTER_EXTERNAL_DATA_SOURCE
dev_langs: TSQL
helpviewer_keywords:
- polybase, alter external data source statement
- ALTER EXTERNAL DATA SOURCE statement
ms.assetid: a34b9e90-199d-46d0-817a-a7e69387bf5f
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 028a300c8dc6b295a0f10b3cb137809c81c4af95
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="alter-external-data-source-transact-sql"></a>変更する外部データ ソース (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  外部テーブルを作成するために使用する外部データ ソースを変更します。 外部データ ソースは、Hadoop または Azure blob ストレージ (WASB) にすることができます。  
  
## <a name="syntax"></a>構文  
  
```  
-- Modify an external data source
-- Applies to: SQL Server (2016 or later)
ALTER EXTERNAL DATA SOURCE data_source_name SET
    {   
        LOCATION = 'server_name_or_IP' [,] |
        RESOURCE_MANAGER_LOCATION = <'IP address;Port'> [,] |
        CREDENTIAL = credential_name
    }  
    [;]  

-- Modify an external data source pointing to Azure Blob storage
-- Applies to: SQL Server (starting with 2017)
ALTER EXTERNAL DATA SOURCE data_source_name
    WITH (
        TYPE = BLOB_STORAGE,
        LOCATION = 'https://storage_account_name.blob.core.windows.net'
        [, CREDENTIAL = credential_name ]
    )  
```  
  
## <a name="arguments"></a>引数  
 data_source_name では、データ ソースのユーザー定義の名前を指定します。 名前は一意である必要があります。
  
 場所 = 'server_name_or_IP' は、サーバーまたは IP アドレスの名前を指定します。
  
 RESOURCE_MANAGER_LOCATION = '\<IP アドレスです。ポート >' Hadoop リソース マネージャーの場所を指定します。 指定した場合、クエリ オプティマイザーは Hadoop の計算の機能を使用して、PolyBase クエリのデータを事前処理こともできます。 これは、コストベースの判断です。 述語のプッシュ ダウンが呼び出されると、この Hadoop と SQL の間で転送されるデータ量を大幅に削減し、クエリのパフォーマンス向上します。
  
 資格情報の名前付きの資格情報 = Credential_Name を指定します。 参照してください[CREATE DATABASE SCOPED CREDENTIAL &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/create-database-scoped-credential-transact-sql.md).

型 BLOB_STORAGE を =   
**適用対象:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]」を参照してください。
一括操作のみ、`LOCATION`有効にする必要があります Azure Blob ストレージへの URL。 配置しない **/** 、ファイル名、または共有アクセス署名のパラメーターの最後に、 `LOCATION` URL。
使用して、使用する資格情報を作成する必要があります`SHARED ACCESS SIGNATURE`id として。 Shared Access Signature に関する詳細については、「[Shared Access Signature (SAS) を使用](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1)」を参照してください。

  
  
## <a name="remarks"></a>解説
 一度に 1 つのソースを変更できます。 同時実行の要求を同じソースを変更するには、待機する 1 つのステートメントが発生します。 ただし、さまざまなソースは、同時に変更できます。 このステートメントは、その他のステートメントと同時に実行できます。
  
## <a name="permissions"></a>Permissions  
 任意の外部データ ソースの ALTER 権限が必要です。
 > [!IMPORTANT]  
 >  任意の外部データ ソースの ALTER 権限は、任意のプリンシパルを作成し、任意の外部データ ソース オブジェクトを変更する権限を付与し、そのため、データベース上のすべてのデータベース スコープ資格情報にアクセスする権限付与もします。 このアクセス許可する必要がありますと見なされる高度な権限し、そのため、システムで信頼されたプリンシパルにのみ付与する必要があります。

  
## <a name="examples"></a>使用例  
 次の例では、既存のデータ ソースのリソース マネージャーの場所と場所を変更します。
  
```  
ALTER EXTERNAL DATA SOURCE hadoop_eds SET
     LOCATION = 'hdfs://10.10.10.10:8020',
     RESOURCE_MANAGER_LOCATION = '10.10.10.10:8032'
    ;
  
```  

 次の例では、既存のデータ ソースへの接続に資格情報を変更します。
  
```  
ALTER EXTERNAL DATA SOURCE hadoop_eds SET
   CREDENTIAL = new_hadoop_user
    ;
```
