---
title: "Azure SQL DB (SybaseToSQL) への接続 |Microsoft ドキュメント"
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
ms.assetid: 96538007-1099-40c8-9902-edd07c5620ee
caps.latest.revision: "5"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d63fac7037bfe3f3646d9fa1c36200aa682b2fe3
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="connect-to-azure-sql-db--sybasetosql"></a>Azure SQL DB (SybaseToSQL) への接続します。
Azure SQL DB ダイアログ ボックスに接続を使用すると、移行する Azure SQL DB データベースへの接続します。  
  
このダイアログ ボックスにアクセスする、**ファイル**メニューの  **Azure SQL DB への接続**です。 以前接続した場合、コマンドは**Azure SQL DB に再接続します。**  
  
## <a name="options"></a>オプション  
**[サーバー名]**  
  
選択するか、Azure SQL DB に接続するためのサーバー名を入力します。  
  
**データベース**  
  
選択し、入力または**参照**データベース名。  
  
> [!IMPORTANT]  
> SSMA for Sybase は Azure SQL データベース内の master データベースへの接続をサポートしていません。  
  
**ユーザー名**  
  
SSMA は、Azure SQL DB データベースへの接続を使用してユーザー名を入力します。  
  
**Password**  
  
ユーザー名に対応するパスワードを入力します。  
  
**暗号化します。**  
  
SSMA は、Azure SQL DB に、暗号化された接続をお勧めします。  
  
## <a name="create-azure-database"></a>Azure のデータベースを作成します。  
Azure SQL DB アカウントにデータベースがない場合、は、非常に最初のデータベースを作成できます。  
  
非常に最初に、新しいデータベースを作成するには次の手順に従います  
  
1.  Azure SQL データベース ダイアログ ボックスへの接続に存在する 参照 ボタンをクリックします。  
  
2.  データベースが存在しない場合は、次の 2 つのメニュー項目が表示されます。  
  
    1.  **(データベースが見つかりません)**は無効になっているし、すべての時間がグレーで表示されます。  
  
    2.  **新しいデータベースを作成**Azure SQL DB アカウントにデータベースがない場合にのみこれを有効にします。 このメニュー項目をクリックすると、Azure データベースの作成 ダイアログ ボックスがあるデータベースの名前とサイズを使用します。  
  
3.  データベースの作成時に、次の 2 つのパラメーターは入力として指定します。  
  
    1.  **データベース名:**データベース名を入力します。  
  
    2.  **データベース サイズ:**で Azure SQL DB アカウントを作成する必要のあるデータベースのサイズを選択します。  
  
