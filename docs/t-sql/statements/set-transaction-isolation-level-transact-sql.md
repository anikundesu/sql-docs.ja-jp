---
title: "TRANSACTION ISOLATION LEVEL (TRANSACT-SQL) を設定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/04/2017
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
- LEVEL
- LEVEL_TSQL
- SET TRANSACTION ISOLATION LEVEL
- ISOLATION
- ISOLATION_TSQL
- SET_TRANSACTION_ISOLATION_LEVEL_TSQL
dev_langs: TSQL
helpviewer_keywords:
- SET TRANSACTION ISOLATION LEVEL statement
- row versioning [SQL Server], isolation levels
- TRANSACTION ISOLATION LEVEL option
- isolation levels [SQL Server], setting
- locking [SQL Server], isolation levels
- transactions [SQL Server], isolation levels
ms.assetid: 016fb05e-a702-484b-bd2a-a6eabd0d76fd
caps.latest.revision: "80"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: cde588fed7aad439e90c97de99ba89633a1df2c5
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="set-transaction-isolation-level-transact-sql"></a>SET TRANSACTION ISOLATION LEVEL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  ロックおよび行のバージョン管理動作を制御[!INCLUDE[tsql](../../includes/tsql-md.md)]への接続によって実行されたステートメント[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

## <a name="syntax"></a>構文

```
-- Syntax for SQL Server and Azure SQL Database
  
SET TRANSACTION ISOLATION LEVEL
    { READ UNCOMMITTED
    | READ COMMITTED
    | REPEATABLE READ
    | SNAPSHOT
    | SERIALIZABLE
    }
```

```
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse
  
SET TRANSACTION ISOLATION LEVEL READ UNCOMMITTED
```

## <a name="arguments"></a>引数  
 READ UNCOMMITTED  
 他のトランザクションで変更されたが、まだコミットされていない行を、ステートメントで読み取れるように指定します。  
  
 READ UNCOMMITTED レベルで実行されるトランザクションでは共有ロックが取得されないため、現在のトランザクションで読み取り中のデータが他のトランザクションで変更されることがあります。 また、READ UNCOMMITTED トランザクションは排他ロックによってブロックされないため、他のトランザクションで変更された後まだコミットされていない行を、現在のトランザクションで読み取ることができます。 このオプションが設定されている場合に、コミットされていない変更が読み取られた場合、これをダーティ リードと呼びます。 この場合、トランザクションが終了していなくても、データの値を変更したり、データセットの行を挿入または削除することができます。 このオプションは、トランザクション内のすべての SELECT ステートメントで、すべてのテーブルに対して NOLOCK を設定するのと同じ効果があります。 これは分離レベルの中で最も制限の緩やかなオプションです。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、コミットされていないデータ変更のダーティ リードが行われないようトランザクションを保護しながら、ロックの競合を最小限にすることもできます。これには、次のいずれかを使用します。  
  
-   READ_COMMITTED_SNAPSHOT データベース オプションを使用して READ COMMITTED 分離レベルは、ON に設定します。  
  
-   SNAPSHOT 分離レベル。  
  
 READ COMMITTED  
 他のトランザクションで変更されたが、まだコミットされていないデータを、ステートメントで読み取れないように指定します。 これにより、ダーティ リードを防ぐことができます。 現在のトランザクション内にある各ステートメント間では、他のトランザクションによるデータの変更が可能です。この結果、反復不能読み取りやファントム データが発生することがあります。 このオプションは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]既定値です。  
  
 READ COMMITTED の動作は、READ_COMMITTED_SNAPSHOT データベース オプションの設定によって異なります。  
  
-   READ_COMMITTED_SNAPSHOT が OFF に設定されている場合 (既定)、[!INCLUDE[ssDE](../../includes/ssde-md.md)]では共有ロックが使用され、現在のトランザクションでの読み取り操作中に他のトランザクションによって行が変更されるのを防ぐことができます。 また、ステートメントが他のトランザクションで変更された行を読み取ろうとしても、そのトランザクションが完了するまでステートメントはブロックされます。 いつ解放されるかは、共有ロックの種類によって決まります。 行ロックは、次の行が処理される前に解放されます。 次のページが読み取られ、ステートメントの終了時にテーブル ロックがリリースされたときに、ページ ロックが解放されます。  
  
    > [!NOTE]  
    >  READ_COMMITTED_SNAPSHOT が ON に設定されている場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]では行のバージョン管理が使用され、各ステートメントでは、トランザクション全体で一貫性のあるデータのスナップショットが使用されます。このスナップショットは、ステートメント開始時点に存在したデータのスナップショットです。 ただし、他のトランザクションによるデータ更新を防ぐためのロックは使用されません。  
    >   
    >  スナップショット分離は、FILESTREAM データをサポートします。 スナップショット分離モードでは、トランザクションの任意のステートメントによって読み取られる FILESTREAM データは、トランザクションの開始時に存在していたデータのバージョンとトランザクション的な一貫性があります。  
  
 READ_COMMITTED_SNAPSHOT データベース オプションが ON の場合は、READ_COMMITTED 分離レベルで実行されるトランザクションの各ステートメントで行のバージョン管理を使用する代わりに、READCOMMITTEDLOCK テーブル ヒントを使用して共有ロックを要求することもできます。  
  
> [!NOTE]  
>  READ_COMMITTED_SNAPSHOT オプションを設定すると、そのデータベースでは ALTER DATABASE コマンドを実行する接続のみが許可されます。 ALTER DATABASE が完了するまで、そのデータベースには他に開かれた接続が存在しないようにする必要があります。 データベースをシングル ユーザー モードに設定する必要はありません。  
  
 REPEATABLE READ  
 他のトランザクションで変更されたが、コミットされていないデータをステートメントで読み取れないように指定すると共に、現在のトランザクションが完了するまでは現在のトランザクションで読み取ったデータを他のトランザクションで変更できないように指定します。  
  
 トランザクションの各ステートメントで読み取ったすべてのデータには共有ロックが設定され、トランザクションが完了するまでその状態が保持されます。 これにより、現在のトランザクションで読み取った行は、他のトランザクションで変更できなくなります。 他のトランザクションでは、現在のトランザクションで実行されているステートメントの検索条件に一致する行を新しく挿入することができます。 その後、現在のトランザクションでステートメントが再試行された場合は新しい行が取得されるので、この結果ファントム読み取りが発生します。 共有ロックはステートメントが完了するたびに解除されるのではなく、トランザクションが完了するまで保持されるため、同時実行性は既定の READ COMMITTED 分離レベルよりも低くなります。 このオプションは、必要な場合にのみ使用してください。  
  
 SNAPSHOT  
 トランザクションの各ステートメントで、トランザクション全体で一貫性のあるデータを読み取るように指定します。このデータは、トランザクション開始時点に存在したデータです。 データの変更は、トランザクションの開始前にコミットされたものだけが認識されます。 現在のトランザクションが開始されてから他のトランザクションによってデータが変更されても、現在のトランザクションで実行されるステートメントではデータの変更は認識されません。 このオプションでは、トランザクションの各ステートメントにおいて、トランザクションの開始時点でコミットされていたデータのスナップショットを取得するのと同じ効果が得られます。  
  
 データベースが復旧中の場合を除いて、SNAPSHOT トランザクションではデータの読み取り時にロックが要求されません。 SNAPSHOT トランザクションでデータが読み取られている間も、他のトランザクションによるデータの書き込みはブロックされません。 トランザクションでデータが書き込まれている間も、SNAPSHOT トランザクションではデータを読み取ることができます。  
  
 データベースの復旧でロールバックが行われており、ロールバック中のトランザクションによってデータがロックされている場合に、そのデータの読み取りが試行されると、SNAPSHOT トランザクションではロックが要求されます。 トランザクションのロールバックが完了するまで SNAPSHOT トランザクションはブロックされ、 許可が与えられるとすぐロックは解除されます。  
  
 SNAPSHOT 分離レベルを使用するトランザクションを開始する前には、ALLOW_SNAPSHOT_ISOLATION データベース オプションを ON に設定する必要があります。 SNAPSHOT 分離レベルを使用するトランザクションで複数のデータベースのデータへアクセスする場合は、各データベースで ALLOW_SNAPSHOT_ISOLATION を ON に設定する必要があります。  
  
 他の分離レベルで開始されたトランザクションに SNAPSHOT 分離レベルを設定することはできません。設定すると、トランザクションは中止されます。 トランザクションを SNAPSHOT 分離レベルで開始した場合は、他の分離レベルに変更することができ、その後 SNAPSHOT に戻すことができます。 トランザクションの開始は、初めてデータにアクセスした時点からになります。  
  
 SNAPSHOT 分離レベルで実行されているトランザクションでは、そのトランザクションで行った変更が認識されます。 たとえば、トランザクションでテーブルの UPDATE を実行した後、同じテーブルに対して SELECT ステートメントを実行した場合、結果セットには変更後のデータが含まれます。  
  
> [!NOTE]  
>  スナップショット分離モードでは、トランザクションの任意のステートメントによって読み取られる FILESTREAM データは、ステートメントの開始時ではなく、トランザクションの開始時に存在していたデータのバージョンとトランザクション的な一貫性があります。  
  
 SERIALIZABLE  
 次のことを指定します。  
  
-   他のトランザクションで変更されたが、まだコミットされていないデータは、ステートメントで読み取れない。  
  
-   現在のトランザクションが完了するまで、現在のトランザクションで読み取ったデータは他のトランザクションで変更できない。  
  
-   現在のトランザクションが完了するまで、現在のトランザクションのステートメントで読み取ったキー範囲に該当するキー値の行は、他のトランザクションで新しく挿入できない。  
  
 トランザクションで実行される各ステートメントの検索条件に一致するキー値の範囲には、範囲ロックが設定されます。 これにより、現在のトランザクションで実行されるステートメントの処理対象となる行はブロックされ、他のトランザクションによる行の更新や挿入ができなくなります。 つまり、トランザクションのステートメントが 2 度実行された場合は、2 度目も同じ行セットが読み取られます。 範囲ロックはトランザクションが完了するまで保持されます。 このオプションではキー範囲全体がロックされ、トランザクションが完了するまでその状態が保持されるので、これは最も制限の厳しい分離レベルといえます。 このオプションは同時実行性が低いため、必要なときにのみ使用してください。 このオプションは、トランザクション内のすべての SELECT ステートメントで、すべてのテーブルに対して HOLDLOCK を設定するのと同じ効果があります。  
  
## <a name="remarks"></a>解説  
 分離レベル オプションは一度に 1 つだけ設定でき、設定したオプションは明示的に変更されない限り、その接続で継続的に使用されます。 ステートメントの FROM 句内にあるテーブル ヒントで、テーブルに対して別のロック動作やバージョン管理動作が指定されない限り、トランザクションのすべての読み取り操作は、指定した分離レベルのルールに従って実行されます。  
  
 トランザクションの分離レベルでは、読み取り操作に対して取得されるロックの種類が定義されます。 READ COMMITTED または REPEATABLE READ で取得される共有ロックは通常、行ロックです。読み取り操作でページまたはテーブルの行が大量に参照される場合は、ページ ロックまたはテーブル ロックに変更される場合があります。 トランザクションで行の読み取り後に変更が行われる場合、そのトランザクションでは排他ロックによって行が保護され、トランザクションが完了するまでその状態が保持されます。 たとえば REPEATABLE READ トランザクションで、行に対する共有ロックが取得され、その行が変更される場合、共有行ロックは排他行ロックに変わります。  
  
 分離レベルはトランザクションの実行中いつでも変更できます。ただし、 どの分離レベルでも、SNAPSHOT 分離レベルに変更した場合は例外が発生します。 このときトランザクションは失敗し、ロールバックされます。 SNAPSHOT 分離で開始したトランザクションを他の任意の分離レベルに変更することはできます。  
  
 トランザクションの分離レベルを変更した場合、変更後に読み取られるリソースは、新しいレベルのルールに従って保護されます。 変更前に読み取られたリソースは、引き続き以前のレベルのルールに従って保護されます。 たとえば、トランザクションが READ COMMITTED から SERIALIZABLE に変更された場合、変更後に取得される共有ロックは、トランザクションの終了まで保持されるようになります。  
  
 SET TRANSACTION ISOLATION LEVEL をストアド プロシージャまたはトリガーで実行した場合は、オブジェクトから制御が返されると、分離レベルはオブジェクトの呼び出し時に使用されていたレベルに再設定されます。 たとえば、バッチで REPEATABLE READ を設定し、このバッチからストアド プロシージャを呼び出して分離レベルを SERIALIZABLE に設定した場合、ストアド プロシージャからバッチに制御が返されると、分離レベルの設定は REPEATABLE READ に戻ります。  
  
> [!NOTE]  
>  ユーザー定義関数と共通言語ランタイム (CLR) ユーザー定義型では、SET TRANSACTION ISOLATION LEVEL は実行できません。 ただし、テーブル ヒントを使用して分離レベルを指定することはできます。 詳細については、「[テーブル ヒント &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-table.md)」を参照してください。  
  
 sp_bindsession を使用して 2 つのセッションをバインドすると、各セッションではそれぞれの分離レベル設定が保持されます。 SET TRANSACTION ISOLATION LEVEL を使用してセッションの分離レベル設定を変更しても、そのセッションにバインドしている他のセッションの設定に影響はありません。  
  
 SET TRANSACTION ISOLATION LEVEL は、解析時ではなく実行時に有効なレベルです。  
  
 ヒープに対して最適化された一括読み込み操作を行うと、次の分離レベルで実行されるクエリがブロックされます。  
  
-   SNAPSHOT  
  
-   READ UNCOMMITTED  
  
-   READ COMMITTED (行のバージョン管理を使用する場合)  
  
 一方、これらの分離レベルでクエリを実行すると、ヒープに対する最適化された一括読み込み操作がブロックされます。 一括読み込み操作の詳細については、次を参照してください。[一括インポートし、データ ファイルのエクスポート &#40;です。SQL Server &#41;](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md).  
  
 FILESTREAM が有効なデータベースでは、次のトランザクション分離レベルがサポートされています。  
  
|分離レベル|Transact SQL アクセス|ファイル システム アクセス|  
|---------------------|-------------------------|------------------------|  
|READ UNCOMMITTED|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|サポートされていない|  
|読み取りのコミット|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|REPEATABLE READ|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|サポートされていない|  
|Serializable|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|サポートされていない|  
|READ COMMITTED SNAPSHOP|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|スナップショット|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
  
## <a name="examples"></a>使用例  
 次の例のセット、`TRANSACTION ISOLATION LEVEL`セッションのです。 後続の各 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントに対して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではトランザクションが完了するまですべての共有ロックが保持されます。  
  
```  
USE AdventureWorks2012;  
GO  
SET TRANSACTION ISOLATION LEVEL REPEATABLE READ;  
GO  
BEGIN TRANSACTION;  
GO  
SELECT *   
    FROM HumanResources.EmployeePayHistory;  
GO  
SELECT *   
    FROM HumanResources.Department;  
GO  
COMMIT TRANSACTION;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [DBCC USEROPTIONS &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/database-console-commands/dbcc-useroptions-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [テーブル ヒント &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-table.md)  
  
  
