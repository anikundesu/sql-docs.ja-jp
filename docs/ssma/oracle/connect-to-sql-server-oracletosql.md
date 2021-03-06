---
title: "SQL Server (OracleToSQL) への接続 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-oracle
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ef384ea-5f3e-4f70-ad7c-b62d7b0da628
caps.latest.revision: "3"
author: Shamikg
ms.author: Shamikg
manager: v-pelars
ms.workload: Inactive
ms.openlocfilehash: ee72004a627a7fd99f347677575b82fd1d9fd7b8
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="connect-to-sql-server--oracletosql"></a>SQL Server (OracleToSQL) への接続します。
使用して、 **SQL Server への接続** ダイアログ ボックスのインスタンスに接続する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]に移行します。 アクセスする、 **SQL Server への接続** ダイアログ ボックスで、**ファイル** メニューのをクリックして**SQL Server への接続**です。  
  
## <a name="options"></a>オプション  
**サーバー名**  
入力またはへの接続に SQL Server のインスタンスを選択します。 既定では、最後に接続しているインスタンスが表示されます。  
  
-   ローカル コンピューターの既定のインスタンスに接続する場合は、いずれかを入力**localhost**またはドット (**.**)。  
  
-   別のコンピューターの既定のインスタンスに接続する場合は、コンピューターの名前を入力します。  
  
-   別のコンピューターの名前付きインスタンスに接続する場合は、入力、コンピューター名、バック スラッシュ、およびインスタンス名など*MyServer*\\*MyInstance*です。  
  
**[サーバー ポート]**  
場合のインスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]が既定の接続のポート (1433)、ポート番号を入力を受け入れるように構成されていません。 それ以外の場合、この値を空白のままにします。  
  
**データベース**  
オブジェクトとデータを移行するデータベースを指定します。 このオプションに再接続するときは使用できません[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
**[認証]**  
接続に使用される認証方法の選択[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 現在の Windows アカウントを使用するのには、Windows 認証を選択します。 指定する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ログインとパスワードで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]認証します。  
  
**ユーザー名**  
使用している場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]認証では、インスタンスのログイン名を入力[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 Windows 認証を使用している場合はこのオプションは利用できません。  
  
**Password**  
使用している場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]認証では、そのインスタンス上のログインのパスワードを入力[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 Windows 認証を使用している場合はこのオプションは利用できません。  
  
**[暗号化接続]**  
SQL Server に安全に接続する場合は、調べることにより、暗号化接続の使用、**接続を暗号化**チェック ボックスをオンします。  
  
**[Trust Server Certificate]**  
このオプションを使用する場合は、選択、 **Trust Server Certificate**チェック ボックスをオンします。  
  
> [!NOTE]  
> 有効にする**Trust Server Certificate**に設定する必要があります「暗号化」 **True**です。  
  
