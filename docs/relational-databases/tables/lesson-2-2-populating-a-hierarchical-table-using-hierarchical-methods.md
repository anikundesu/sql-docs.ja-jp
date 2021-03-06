---
title: "階層的な手法を使用した階層テーブルの作成 | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
f1_keywords: HierarchyID
helpviewer_keywords: HierarchyID
ms.assetid: 2c95fa60-5b8e-4a05-ac09-cffe2b05900a
caps.latest.revision: "22"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: e5af8385d5968daba091c05ae41cff780be8f47b
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="lesson-2-2---populating-a-hierarchical-table-using-hierarchical-methods"></a>レッスン 2-2 - 階層的な手法を使用した階層テーブルの作成
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]
[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] のマーケティング部門には 8 人の従業員が勤務しています。 従業員の階層は、次のようになります。  
  
**David**( **EmployeeID 6** ) は Marketing Manager です。 **David**には、次の 3 人の Marketing Specialist が直属します。  
  
-   **Sariya**( **EmployeeID 46** )  
  
-   **John**( **EmployeeID 271** )  
  
-   **Jill**( **EmployeeID 119** )  
  
Marketing Assistant の **Wanida** (**EmployeeID** 269) は **Sariya**に直属し、Marketing Assistant の **Mary** (**EmployeeID** 272) は **John**に直属します。  
  
### <a name="to-insert-the-root-of-the-hierarchy-tree"></a>階層ツリーのルートを挿入するには  
  
1.  次の例では、Marketing Manager である **David** を、階層のルートに位置するテーブルに挿入します。 **OrdLevel** 列は計算列です。 したがって、INSERT ステートメントの一部ではありません。 この最初のレコードでは、 [GetRoot()](../../t-sql/data-types/getroot-database-engine.md) メソッドを使用して、この最初のレコードを階層のルートとして挿入します。  
  
    ```  
    INSERT HumanResources.EmployeeOrg (OrgNode, EmployeeID, EmpName, Title)  
    VALUES (hierarchyid::GetRoot(), 6, 'David', 'Marketing Manager') ;  
    GO  
    ```  
  
2.  テーブルの最初の行を調べるには、次のコードを実行します。  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    ```  
  
    [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
    ------------ ------- -------- ---------- ------- -----------------  
    /            Ox      0        6          David   Marketing Manager  
    ```  
  
前のレッスンと同様、 `ToString()` メソッドを使用して、 **hierarchyid** データ型をよりわかりやすい形式に変換します。  
  
### <a name="to-insert-a-subordinate-employee"></a>部下を挿入するには  
  
1.  **Sariya** は **David**に直属します。 **Sariya** のノードを挿入するには、 **hierarchyid** データ型の適切な **OrgNode**値を作成する必要があります。 次のコードでは、 **hierarchyid** データ型の変数を作成して、テーブルのルート OrgNode 値をその変数に代入します。 次に、その変数を [GetDescendant()](../../t-sql/data-types/getdescendant-database-engine.md) メソッドと共に使用して、部下のノードである行を挿入します。 `GetDescendant` は、2 つの引数を受け取ります。 引数値の次のオプションを確認してください。  
  
    -   parent が NULL の場合、 `GetDescendant` は NULL を返します。  
  
    -   parent が NULL でなく、child1 と child2 の両方が NULL の場合、 `GetDescendant` は parent の子を返します。  
  
    -   parent と child1 が NULL でなく、child2 が NULL の場合、 `GetDescendant` は child1 より大きい parent の子を返します。  
  
    -   parent と child2 が NULL でなく、child1 が NULL の場合、 `GetDescendant` は child2 より小さい parent の子を返します。  
  
    -   parent、child1、child2 のすべてが NULL でない場合、 `GetDescendant` は child1 より大きく child2 より小さい parent の子を返します。  
  
    テーブルにはルート以外にまだ 1 行もないため、次のコードではルートの `(NULL, NULL)` 引数を使用します。 **Sariya**を挿入するには、次のコードを実行します。  
  
    ```  
    DECLARE @Manager hierarchyid   
    SELECT @Manager = hierarchyid::GetRoot()  
    FROM HumanResources.EmployeeOrg ;  
  
    INSERT HumanResources.EmployeeOrg (OrgNode, EmployeeID, EmpName, Title)  
    VALUES  
    (@Manager.GetDescendant(NULL, NULL), 46, 'Sariya', 'Marketing Specialist') ;  
  
    ```  
  
2.  テーブルにクエリを実行してエントリがどのように表示されるかを確認するには、最初の手順のクエリを繰り返します。  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    ```  
  
    [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
    ------------ ------- -------- ---------- ------- -----------------  
    /            Ox      0        6          David   Marketing Manager  
    /1/          0x58    1        46         Sariya  Marketing Specialist  
    ```  
  
### <a name="to-create-a-procedure-for-entering-new-nodes"></a>新しいノードを入力するためのプロシージャを作成するには  
  
1.  データの入力を簡略化するには、次のストアド プロシージャを作成して、 **EmployeeOrg** テーブルに従業員を追加します。 このプロシージャは、追加される従業員に関する入力値を受け取ります。 これには、新しい従業員の管理者の **EmployeeID** 、新しい従業員の **EmployeeID** 番号、従業員の名と役職が含まれます。 このプロシージャでは、 `GetDescendant()` と [GetAncestor()](../../t-sql/data-types/getancestor-database-engine.md) メソッドも使用します。 プロシージャを作成するには、次のコードを実行します。  
  
    ```  
    CREATE PROC AddEmp(@mgrid int, @empid int, @e_name varchar(20), @title varchar(20))   
    AS   
    BEGIN  
       DECLARE @mOrgNode hierarchyid, @lc hierarchyid  
       SELECT @mOrgNode = OrgNode   
       FROM HumanResources.EmployeeOrg   
       WHERE EmployeeID = @mgrid  
       SET TRANSACTION ISOLATION LEVEL SERIALIZABLE  
       BEGIN TRANSACTION  
          SELECT @lc = max(OrgNode)   
          FROM HumanResources.EmployeeOrg   
          WHERE OrgNode.GetAncestor(1) =@mOrgNode ;  
  
          INSERT HumanResources.EmployeeOrg (OrgNode, EmployeeID, EmpName, Title)  
          VALUES(@mOrgNode.GetDescendant(@lc, NULL), @empid, @e_name, @title)  
       COMMIT  
    END ;  
    GO  
    ```  
  
2.  次の例では、 **David**の直接または間接的な部下である残り 4 人の従業員を追加します。  
  
    ```  
    EXEC AddEmp 6, 271, 'John', 'Marketing Specialist' ;  
    EXEC AddEmp 6, 119, 'Jill', 'Marketing Specialist' ;  
    EXEC AddEmp 46, 269, 'Wanida', 'Marketing Assistant' ;  
    EXEC AddEmp 271, 272, 'Mary', 'Marketing Assistant' ;  
    ```  
  
3.  **EmployeeOrg** テーブルの行を調べるには、再び次のクエリを実行します。  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    GO  
    ```  
  
    [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
    ------------ ------- -------- ---------- ------- -----------------  
    /            Ox      0        6          David   Marketing Manager  
    /1/          0x58    1        46         Sariya  Marketing Specialist  
    /1/1/        0x5AC0  2        269        Wanida  Marketing Assistant  
    /2/          0x68    1        271        John    Marketing Specialist  
    /2/1/        0x6AC0  2        272        Mary    Marketing Assistant  
    /3/          0x78    1        119        Jill    Marketing Specialist  
    ```  
  
テーブルに、マーケティング組織が完全に作成されました。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[階層的な手法を使用した階層テーブルのクエリ](../../relational-databases/tables/lesson-2-3-querying-a-hierarchical-table-using-hierarchy-methods.md)  
  
  
  
