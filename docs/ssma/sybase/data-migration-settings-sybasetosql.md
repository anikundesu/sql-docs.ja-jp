---
title: "データ移行の設定 (SybaseToSQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-sybase
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 94d7a083-2dbc-4e3d-94dd-92b7ff9d0c2d
caps.latest.revision: "3"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8f0877436b0f3727b8945035f4d54c3f936946d5
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="data-migration-settings-sybasetosql"></a>データ移行の設定 (SybaseToSQL)
  
## <a name="data-migration-settings"></a>データ移行の設定  
**データの移行設定**データ移行のためのカスタム クエリを記述することができます。  
  
-   このタブは、使用可能な場合に**拡張データの移行オプション**に設定されている**表示**に設定した場合は非表示と**を非表示に**プロジェクトの設定。 プロジェクトの移行設定の詳細については、次を参照してください。[プロジェクトの設定 (移行)](http://msdn.microsoft.com/en-us/82f8857f-7ab1-4738-ab6e-b1e95ea94924)です。  
  
-   実装するカスタム SQL ステートメントの解析**データの移行設定**テーブル ノードのタブ。  
  
-   使用できる 2 つのチェック ボックスは次のとおり、**データの移行設定**viz。  
  
    1.  SQL Server テーブルを切り捨てる  
  
    2.  カスタムの使用を選択します。  
  
1.  **SQL Server テーブルを切り捨てます。**  
     このオプションでは、ユーザーが対象のデータベースに移行したデータを明確に表示します。  
  
    -   既定では、このテキスト ボックスがオンになっています。  
  
    -   このテキスト ボックスがオフの場合は、移行されるデータは対象のデータベースに既存のデータに追加されます。  
  
2.  **カスタムの使用を選択します。**  
     このオプションでは、ユーザーを変更する、**選択**ステートメントが存在 (**選択**ステートメントには、対象のデータベースに表示されるデータを選択できます)。  
  
    1.  既定では、このテキスト ボックスでは、チェックです。  
  
    2.  このテキスト ボックスをオンにしたかどうかは、ユーザーを変更することできます、**選択**ステートメントが存在します。  
  
存在する 2 つのボタンを viz。  
  
-   **適用:**クリックして**適用**変更されている設定を適用します。  
  
-   **キャンセル:**クリックして**キャンセル**変更が加えの前に存在する設定を復元します。  
  
## <a name="see-also"></a>参照  
[SQL Server または SQL Azure へ Sybase データの移行](http://msdn.microsoft.com/en-us/54a39f5e-9250-4387-a3ae-eae47c799811)  
  
