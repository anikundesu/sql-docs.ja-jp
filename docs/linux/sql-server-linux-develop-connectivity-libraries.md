---
title: "接続ライブラリとフレームワーク |Microsoft ドキュメント"
description: "クライアント アプリは、さまざまな言語を使用してオンプレミスで実行して Microsoft SQL Server やクラウドでは、Linux、Windows または Docker と Azure SQL データベースと Azure SQL Data Warehouse に接続を接続ドライバーの一覧を示します。"
author: sanagama
ms.author: sanagama
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 80efe5ff-09ba-48a0-ac93-a91d62cff47c
ms.workload: Inactive
ms.openlocfilehash: 91327a1f067f6a8ef11481b489e6d296870c6c86
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="connectivity-libraries-and-frameworks-for-microsoft-sql-server"></a>接続ライブラリと Microsoft SQL Server のフレームワーク

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

チェック アウト、[チュートリアル入門](http://aka.ms/sqldev)をすばやく c#、Java、Node.js、PHP、Python などのプログラミング言語で作業を開始し、macos Linux または Windows Docker で SQL Server を使用してアプリをビルドします。

次の表に、接続ライブラリを表示または*ドライバー*またはクラウドでは、Linux、Windows または Docker ともに Azure SQL Database と Azure SQL Data Warehouse に接続し、オンプレミスで実行して Microsoft SQL Server を使用する言語のさまざまなクライアント アプリケーションを使用できることです。 

| 言語 | プラットフォーム | その他のリソース | ダウンロード | 開始するには |
| :-- | :-- | :-- | :-- | :-- |
| C# | Windows、Linux、macOS | [Microsoft ADO.NET for SQL Server](http://msdn.microsoft.com/library/mt657768.aspx) | [ダウンロード](https://msdn.microsoft.com/vstudio/aa496123.aspx) | [作業を開始します。](https://www.microsoft.com/en-us/sql-server/developer-get-started/csharp/ubuntu)
| Java | Windows、Linux、macOS | [Microsoft SQL Server 用 JDBC Driver](http://msdn.microsoft.com/library/mt484311.aspx) | [ダウンロード](http://go.microsoft.com/fwlink/?LinkId=245496) |  [作業を開始します。](https://www.microsoft.com/en-us/sql-server/developer-get-started/java/ubuntu)
| PHP (PHP) | Windows、Linux、macOS| [SQL Server 用 PHP SQL ドライバー](http://msdn.microsoft.com/library/dn865013.aspx) | オペレーティング システム： <br/> \*[Windows](https://www.microsoft.com/download/details.aspx?id=20098) <br/> \*[Linux](https://github.com/Microsoft/msphpsql/tree/dev#install-unix) <br/> \*[macOS](https://github.com/Microsoft/msphpsql/tree/dev#install-unix) |  [作業を開始します。](https://www.microsoft.com/en-us/sql-server/developer-get-started/php/ubuntu)
| Node.js | Windows、Linux、macOS | [Node.js Driver for SQL Server](../connect/node-js/node-js-driver-for-sql-server.md) |  [作業を開始します。](https://www.microsoft.com/en-us/sql-server/developer-get-started/node/ubuntu)
| Python | Windows、Linux、macOS | [Python SQL ドライバー](../connect/python/python-driver-for-sql-server.md) <br/> \*[pyodbc](http://msdn.microsoft.com/library/mt763257.aspx) |  [作業を開始します。](https://www.microsoft.com/en-us/sql-server/developer-get-started/python/ubuntu)
| Ruby | Windows、Linux、macOS | [Ruby Driver for SQL Server](../connect/ruby/ruby-driver-for-sql-server.md) | [作業を開始します。](https://www.microsoft.com/en-us/sql-server/developer-get-started/ruby/ubuntu)
| C++ | Windows、Linux、macOS | [Microsoft ODBC Driver for SQL Server](https://msdn.microsoft.com/en-us/library/mt654048(v=sql.1).aspx) | [ダウンロード](https://msdn.microsoft.com/en-us/library/mt654048(v=sql.1).aspx) |  

次の表は、Linux、Windows や Docker と Azure SQL データベースと Azure SQL Data Warehouse にも、クラウド内には、オブジェクト リレーショナル マッピング (ORM) フレームワークとクライアント アプリケーションは、オンプレミスで実行して Microsoft SQL Server またはを使用している web フレームワークのいくつかの例を示します。 

| 言語 | プラットフォーム | ORM(s) |
| :-- | :-- | :-- |
| C# | Windows、Linux、macOS | [Entity Framework](https://docs.microsoft.com/en-us/ef)<br>[Entity Framework Core](https://docs.microsoft.com/en-us/ef/core/index) |
| Java | Windows、Linux、macOS |[ORM を休止状態します。](http://hibernate.org/orm)|
| PHP (PHP) | Windows、Linux | [Laravel (やすい)](https://laravel.com/docs/5.0/eloquent) |
| Node.js | Windows、Linux、macOS | [Sequelize ORM](http://docs.sequelizejs.com) |
| Python | Windows、Linux、macOS |[Django](https://www.djangoproject.com/) |
| Ruby | Windows、Linux、macOS | [レールを ruby](http://rubyonrails.org/) |

## <a name="related-links"></a>関連リンク
- [SQL Server ドライバー](http://msdn.microsoft.com/library/mt654049.aspx)クライアント アプリケーションから接続するため
