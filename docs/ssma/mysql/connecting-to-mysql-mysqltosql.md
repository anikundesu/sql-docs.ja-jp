---
title: "MySQL (MySQLToSQL) への接続 |Microsoft ドキュメント"
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
helpviewer_keywords:
- Connecting to MySQL, MySQL permission
- Connecting to MySQL,reconnecting
ms.assetid: 084c7020-f729-4f91-90e0-143f85fa68d1
caps.latest.revision: "13"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: a0ecb0ea00a9ae5438657943e65d3bfcea635872
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="connecting-to-mysql-mysqltosql"></a>MySQL (MySQLToSQL) に接続します。
MySQL データベースを他の SQL Server または SQL Azure に移行するには、移行する MySQL データベースに接続する必要があります。 接続すると、SSMA は、すべての MySQL スキーマに関するメタデータを取得し、MySQL メタデータ エクスプ ローラー ペインに表示します。 SSMA は、データベース サーバーに関する情報を格納しますが、パスワードは保存されません。  
  
プロジェクトを終了するまで、データベースへの接続をアクティブに保ちます。 プロジェクトを再度開くと、データベースにアクティブに接続する場合を再接続する必要があります。  
  
MySQL データベースについてのメタデータは自動的に更新されません。 代わりに、MySQL メタデータ エクスプ ローラー内のメタデータを更新する場合は、手動で更新してください。 詳細については、このトピックの「「MySQL メタデータを更新する」セクションを参照してください。  
  
## <a name="required-mysql-permissions"></a>MySQL が必要なアクセス許可  
MySQL データベースへの接続に使用されるアカウントが少なくとも必要**接続**アクセス許可。 これにより、SSMA を接続しているユーザーが所有するスキーマからメタデータを取得します。 他のスキーマ内のオブジェクトのメタデータを取得し、それらのスキーマ内のオブジェクトを変換は、次のアクセス許可がアカウントに必要です。  
  
-   データベース オブジェクトに対する権限を表示する  
  
-   'Information_schema' の 'SELECT' の権限  
  
-   (Udf) の mysql の 'SELECT' の権限  
  
## <a name="establishing-a-connection-to-mysql"></a>MySQL への接続を確立します。  
データベースに接続して SSMA データベースのメタデータを読み取り、プロジェクト ファイルにこのメタデータが追加されます。 オブジェクトを SQL Server または SQL Azure の構文に変換するとき、および SQL Server または SQL Azure にデータを移行したときに、このメタデータを SSMA によって使用されます。 MySQL メタデータ エクスプ ローラー ウィンドウでこのメタデータを参照して、個々 のデータベース オブジェクトのプロパティを確認できます。  
  
> [!IMPORTANT]  
> 接続は、ことを確認しようとする前に、データベース サーバーが実行されていると、接続を受け入れることができます。  
  
**MySQL を接続するには**  
  
1.  **ファイル**メニューの  **MySQL への接続**(このオプションが有効にするプロジェクトの作成後に)。  
  
    以前 MySQL を接続している場合、コマンド名になります**MySQL への再接続**です。  
  
2.  **プロバイダー**ボックスで、MySQL 5.1 Odbc (信頼関係) を選択します。 これは、標準モードの既定のプロバイダーです。  
  
3.  **モード**ボックスで、**標準モード**です。 これは既定のモードです。  
  
    標準モードを使用すると、サーバー名とポートを指定できます。  
  
4.  **標準モード**、次の値を指定します。  
  
    1.  **サーバー名**ボックスに、MySQL サーバーの名前を入力します。 **サーバー ポート**ボックスで、3306 するポート番号を入力します。 これは、既定のポートです。  
  
    2.  **ユーザー名**ボックスで、必要なアクセス許可を持つ MySQL アカウントを入力します。  
  
    3.  **パスワード**ボックスで、指定されたユーザー名のパスワードを入力します。  
  
5.  **SSL:** MySQL に安全に接続する場合は、利用の Secure Socket Layer (SSL) をチェックして、 **SSL**チェック ボックスをオンします。  
  
6.  **構成します。** MySQL Secure Socket Layer (SSL) を介してへの接続を構成するオプションを提供します。  
  
    > [!NOTE]  
    > 有効にする**構成**に SSL を設定する必要があります**True**です。  
  
    [構成] ボタンをクリックすると、ダイアログ ボックスが表示されます。 MySQL データベースを次の 3 つの証明書ファイル ダイアログ ボックス内に存在するパスに接続する必要があります中に暗号化を使用するには、[プライバシー強化メール証明書 (PEM)] に定義されています。  
  
    -   **SSL 証明機関:**信頼の SSL の Ca の一覧で、ファイルへのパスを指定します。  
  
    -   **SSL 証明書:**をセキュリティで保護された接続の確立に使用する SSL 証明書ファイルの名前を指定します。  
  
    -   **SSL キー:**セキュリティで保護された接続の確立に使用する SSL のキー ファイルの名前を指定します。  
  
    > [!NOTE]  
    > -   **OK**必要な情報が提供されているときにボタンが有効にします。 ファイルのパスのいずれかの情報が有効でない場合は、[OK] ボタンが無効になります。  
    > -   **キャンセル**ボタンがダイアログ ボックスを閉じますと**をオフに**SSL オプションで、メイン接続フォーム。  
  
7.  詳細については、次を参照してください[MySQL &#40; への接続。MySQLToSQL &#41;](../../ssma/mysql/connect-to-mysql-mysqltosql.md)  
  
## <a name="reconnecting-to-mysql"></a>MySQL への再接続  
プロジェクトを終了するまで、データベース サーバーへの接続をアクティブに保ちます。 プロジェクトを再度開くと、データベースにアクティブに接続する場合を再接続する必要があります。 メタデータを更新して、SQL Server または SQL Azure にデータベース オブジェクトを読み込むし、データを移行するまで、オフライン作業できます。  
  
## <a name="refreshing-mysql-metadata"></a>MySQL のメタデータの更新  
MySQL データベースについてのメタデータは、自動的に更新されません。 MySQL メタデータ エクスプ ローラー内のメタデータは、最初に接続したときのメタデータまたはメタデータを手動で更新された前回のスナップショットです。 すべてのスキーマ、1 つのスキーマ、または個々 のデータベース オブジェクトのメタデータを手動で更新することができます。  
  
**メタデータを更新するには**  
  
1.  データベースに接続していることを確認します。  
  
2.  MySQL メタデータ エクスプ ローラーで、更新する各スキーマまたはデータベース オブジェクトの横にあるチェック ボックスを選択します。  
  
3.  右クリック**スキーマ**、または個々 のスキーマまたはデータベース オブジェクトをクリックし **データベースから更新**です。  
  
    SSMA が表示されます、アクティブな接続があるない場合、 **MySQL への接続** ダイアログ ボックスの接続できるようにします。  
  
4.  [データベース] ダイアログ ボックスから、更新では、更新するには、どのオブジェクトを指定します。  
  
    -   オブジェクトを更新するには、クリックして、 **Active**矢印が表示されるまで、オブジェクトの横にあるフィールドです。  
  
    -   オブジェクトが更新されていることを防ぐためにクリックして、 **Active**までオブジェクトの横にあるフィールド、 **X**が表示されます。  
  
    -   更新か、オブジェクトのカテゴリを拒否するかをクリックして、 **Active**カテゴリ フォルダーの横にあるフィールドです。  
  
    -   色の設定の定義を表示する をクリックして、**凡例**ボタンをクリックします。  
  
5.  **[OK]** をクリックします。  
  
## <a name="next-step"></a>次の手順  
移行プロセスの次の手順は[SQL Server &#40; に接続します。MySQLToSQL &#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
## <a name="see-also"></a>参照  
[SQL Server - Azure SQL DB &#40; への MySQL データベースの移行MySQLToSql &#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
