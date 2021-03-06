---
title: "SQL モード (MySQLToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-mysql
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: d840ee51-b863-4e77-84aa-37d3f094bfed
caps.latest.revision: "4"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 17254008fad944edba94e0f24a180dba1d4bb8ed
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="sql-modes-mysqltosql"></a>SQL モード (MySQLToSQL)
SSMA for MySQL は別の SQL モードで動作し、さまざまなクライアントの異なる方法でこれらのモードを適用できます。  
  
モードは、MySQL がサポートする SQL 構文を定義し、データの検証の種類を実行する必要がありますをチェックします。 これにより、別の環境に MySQL を使用して SQL Server と MySQL を使用して簡単にします。  
  
## <a name="sql-modes-grid"></a>SQL モード グリッド:  
  
-   ルート レベルでの SQL モードのグリッドに、次の列が含まれています: **SQL モード名**、 **SQL モードの読み込まれた**、および**効果的な SQL モード**です。  
  
-   データベース カテゴリ、データベース、テーブル カテゴリ、ステートメントのカテゴリ、カテゴリのビュー、テーブル、ビュー、関数、プロシージャ、UDF、およびイベント オブジェクト レベルの SQL モードのグリッドには、次の列が含まれています: **SQL モード名**、 **SQL モードの継承**、および**効果的な SQL モード**です。  
  
-   SQL のモード レベルのグリッドにストアド プロシージャ、格納されている関数、およびトリガーには、次の列が含まれています: **SQL モード名**、**元の SQL モード**、および**効果的な SQL モード**です。  
  
> [!NOTE]  
> グループのモードに表示される 'SQL モード Name' を列の下にある太字にします。  
  
## <a name="loaded-sql-modes"></a>読み込まれた SQL モード  
これらは、セッションまたはルート レベルで設定されている SQL モードです。 ターゲット データベースに読み込まれる SQL モードを編集または変更することはできません。  
  
## <a name="inherited-sql-modes"></a>継承された SQL モード  
これらは、対応する親ノードから継承された SQL のモードです。  
  
関数のカテゴリ、プロシージャのカテゴリ、イベントのカテゴリ、およびトリガー、を除きはこれらの SQL のモードはすべてのレベル (データベース、テーブル カテゴリ、ステートメントのカテゴリ、ビューのカテゴリ、テーブル、ビュー、関数、プロシージャ、UDF、およびイベント オブジェクト) に存在します。  
  
> [!NOTE]  
> 選択して、**親から継承**SQL モードの継承 チェック ボックスは、親ノードから継承することができます。 既定では、このチェック ボックスは、選択されたままです。  
  
## <a name="original-sql-modes"></a>元の SQL モード  
これらは、関数、プロシージャ、およびトリガー レベルのみである SQL モードです。  
  
> [!NOTE]  
> 選択して、**使用元**チェック ボックスで、最初に、対応する関数で使用された SQL モードと、プロシージャまたはトリガーを使用できます。 既定では、このチェック ボックスは、選択されたままです。  
  
## <a name="effective-sql-modes"></a>有効な SQL モード  
有効な SQL モードは、次のようにさまざまなレベルで定義できます。  
  
-   **セッション レベル。**  
  
    1.  すべての読み込まれた SQL モード呼び出せる、「有効な SQL モード」です。  
  
    2.  このレベルで有効な SQL モード直接と明示的に変更できます。  
  
    3.  明示的に設定されている有効な SQL モードでは、読み込まれた SQL モードとして反映されていないされ、オブジェクトを最後に適用されます。  
  
-   **関数またはプロシージャまたはトリガーのレベル。**  
  
    1.  すべての元の SQL モードを呼び出すことができます、「有効な SQL モード」。  
  
    2.  このレベルで有効な SQL モード明示的に変更できる場合にのみ、**使用元** チェック ボックスがオフになっています。  
  
    3.  明示的に設定されている有効な SQL モードでは、元の SQL モードは反映されていないされ、オブジェクトを最後に適用されます。  
  
-   **関数またはプロシージャまたはトリガーのレベル以外のノード。**  
  
    1.  すべての継承 SQL モード呼び出せる、「有効な SQL モード」です。  
  
    2.  このレベルで有効な SQL モード明示的に変更できる場合にのみ、**親から継承** チェック ボックスがオフになっています。  
  
    3.  明示的に設定されている有効な SQL モードでは、SQL モードの継承は反映されていないされ、オブジェクトを最後に適用されます。  
  
