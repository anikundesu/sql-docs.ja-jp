---
title: "SQL Server Express LocalDB インスタンス API リファレンス |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: localdb
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: faec46da-0536-4de3-96f3-83e607c8a8b6
caps.latest.revision: "11"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c6b2adadcc52a19e5dab6eadc135a6b1e1a03b85
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sql-server-express-localdb-reference---instance-apis"></a>SQL Server Express LocalDB リファレンス - インスタンスの Api
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]従来型のサービス ベースの SQL Server 環境では、1 台のコンピューターにインストールされている個々 の SQL Server インスタンスが物理的に分離;各インスタンス インストールする必要は個別に削除、別のバイナリのセットと持って別のサービス プロセスで実行されます。 ユーザーが接続する先の SQL Server インスタンスは、SQL Server インスタンス名を使用して指定されます。  
  
 SQL Server Express LocalDB インスタンス API は、簡略化された "軽量な" インスタンス モデルを使用しています。 個々の LocalDB インスタンスは、ディスク上とレジストリ内で独立していますが、同じ 1 組の共有 LocalDB バイナリを使用します。 また、LocalDB ではサービスが使用されません。LocalDB インスタンスは、LocalDB インスタンス API 呼び出しを介して要求時に起動されます。 LocalDB では、ユーザーが使用する LocalDB インスタンスを指定するために、インスタンス名が使用されます。  
  
 個々の LocalDB インスタンスは、常に単一のユーザーによって所有されます。インスタンス共有が有効化されていない限り、表示およびアクセスが可能になるのは、そのユーザーのコンテキストからのみです。  
  
 厳密には、LocalDB インスタンスは従来の SQL Server インスタンスとは異なりますが、意図されている用途はほぼ同じです。 呼び出された*インスタンス*この類似性を強調しより直感的な SQL Server のユーザーにします。  
  
 LocalDB では、自動インスタンス (AI) と名前付きインスタンス (NI) という 2 種類のインスタンスがサポートされています。 LocalDB インスタンスの識別子は、インスタンス名です。  
  
## <a name="automatic-localdb-instances"></a>自動 LocalDB インスタンス  
 自動 LocalDB インスタンスは、"パブリック" です。ユーザーのために自動的に作成および管理され、任意のアプリケーションから使用できます。 どのバージョンの LocalDB に対しても、ユーザーのコンピューターにインストールされている自動 LocalDB インスタンスが 1 つ存在します。  
  
 自動 LocalDB インスタンスを使用すると、シームレスなインスタンス管理を実行できます。 ユーザーがインスタンスを作成する必要はありません。 これにより、ユーザーはアプリケーションのインストールや、複数の異なるコンピューターへの移行を容易に行うことができます。 対象コンピューターに指定バージョンの LocalDB がインストールされている場合、そのコンピューターでは、同じバージョンの自動 LocalDB インスタンスも使用できます。  
  
### <a name="automatic-instance-management"></a>自動インスタンス管理  
 ユーザーは、自動 LocalDB インスタンスを作成する必要はありません。 指定バージョンの LocalDB がユーザーのコンピューターにインストールされている場合、インスタンスは、初回使用時に自動的に作成されます。 ユーザーから見ると、LocalDB バイナリが存在する場合は、自動インスタンスが必ず存在するということになります。  
  
 自動インスタンスには、削除、共有、共有解除など、その他のインスタンス管理操作も使用できます。 特に、自動インスタンスを削除すると、そのインスタンスが効果的にリセットされ、次回の起動操作時に再作成されます。 システム データベースが破損した場合は、自動インスタンスの削除が必要になる場合があります。  
  
### <a name="automatic-instance-naming-rules"></a>自動インスタンスの名前付け規則  
 自動 LocalDB インスタンスのインスタンス名には特殊なパターンがあり、これは予約済み名前空間に属します。 このようなパターンが必要になるのは、名前付き LocalDB インスタンスと名前が競合するのを防ぐためです。  
  
 自動インスタンス名は、LocalDB ベースライン リリース バージョン番号の前に "v" という 1 文字が付いた名前になります。 言い換えると、"v" の後に番号を 2 つ付加し、番号と番号の間にピリオドを 1 つ挿入した形 ("v11.0"、"V12.00" など) になります。  
  
 無効な自動インスタンス名の例を次に示します。  
  
-   11.0 (先頭の "v" 文字がありません)  
  
-   v11 (ピリオドと 2 番目のバージョン番号がありません)  
  
-   v11. (2 番目のバージョン番号がありません)  
  
-   v11.0.1.2 (バージョン番号の数が 2 つを超えています)  
  
## <a name="named-localdb-instances"></a>名前付き LocalDB インスタンス  
 名前付き LocalDB インスタンスは、"プライベート" です。インスタンスは、そのインスタンスの作成と管理を行う単一のアプリケーションによって所有されます。 名前付き LocalDB インスタンスを使用すると、そのインスタンスを分離することで、パフォーマンスの向上を図ることができます。  
  
### <a name="named-instance-creation"></a>名前付きインスタンスの作成  
 名前付きインスタンスは、ユーザーが LocalDB 管理 API を通じて明示的に作成するか、マネージ アプリケーションの app.config ファイルを通じて暗黙的に作成する必要があります。 この API は、マネージ アプリケーションでも使用できます。  
  
 各名前付きインスタンスには、特定の LocalDB バージョンが関連付けらています。つまり、各名前付きインスタンスは、LocalDB バイナリの特定のセットを指しています。 名前付きインスタンスのバージョンは、インスタンス作成時に設定されます。  
  
### <a name="named-instance-naming-rules"></a>名前付きインスタンスの名前付け規則  
 LocalDB インスタンス名は 128 文字までの合計持つことができます (によって制限されます、 **sysname**データ型)。 これは、従来の SQL Server インスタンス名と比較すると、大きく異なります。従来は、16 の ASCII 文字で構成される NetBIOS 名に制限されていました。 この相違が生じたのは、ユーザーが従来より自由にインスタンス名を選択できるように、LocalDB ではデータベースがファイルとして扱われ、ファイルベースのセマンティクスが使用されるようになったためです。  
  
 LocalDB のインスタンス名には、ファイル名コンポーネント内で有効な任意の Unicode 文字を使用できます。 ファイル名のコンポーネントに無効な文字が一般に、次の文字を含める: ASCII または Unicode 文字が 1 から 31、引用符 (") より小さい (\<)、大なり (>)、パイプ (|)、バック スペース (\b)、タブ (\t)、コロン (:)、アスタリスク (*)疑問符 (?)、円記号 (\\)、スラッシュ (/) を転送します。 null 文字 (\0) は、文字列の終端として許可されています。最初に検出された null 文字以降は、すべての文字が無視されます。  
  
> [!NOTE]  
>  無効な文字はオペレーティング システムによって異なり、今後のリリースで変わることもあります。  
  
 インスタンス名の先頭と末尾の空白は無視され、トリミングされます。  
  
 名前の LocalDB をという名前の競合を回避するには、インスタンスことはできません、自動インスタンスの名前付けパターンに続く名前「自動インスタンス名前付け規則」で既に説明したよう 効果的に自動インスタンスの名前付けパターンに続く名前を持つ名前付きインスタンスを作成する場合は、既定のインスタンスを作成します。  
  
## <a name="sql-server-express-localdb-reference-topics"></a>SQL Server Express LocalDB リファレンス トピック  
 [SQL Server Express LocalDB ヘッダーとバージョン情報](../../relational-databases/express-localdb-instance-apis/sql-server-express-localdb-header-and-version-information.md)  
 LocalDB インスタンス API を見つけるためのヘッダー ファイル情報とレジストリ キーを提供します。  
  
 [コマンド ライン管理ツール: SqlLocalDB.exe](../../relational-databases/express-localdb-instance-apis/command-line-management-tool-sqllocaldb-exe.md)  
 コマンド ラインから LocalDB インスタンスを管理するツールである SqlLocalDB.exe について説明します。  
  
 [LocalDBCreateInstance 関数](../../relational-databases/express-localdb-instance-apis/localdbcreateinstance-function.md)  
 LocalDB インスタンスを新規作成するための関数について説明します。  
  
 [LocalDBDeleteInstance 関数](../../relational-databases/express-localdb-instance-apis/localdbdeleteinstance-function.md)  
 LocalDB インスタンスを削除する関数について説明します。  
  
 [LocalDBFormatMessage 関数](../../relational-databases/express-localdb-instance-apis/localdbformatmessage-function.md)  
 LocalDB エラーのローカライズされた説明を返す関数について説明します。  
  
 [LocalDBGetInstanceInfo 関数](../../relational-databases/express-localdb-instance-apis/localdbgetinstanceinfo-function.md)  
 LocalDB インスタンスの情報 (バージョン情報、存在するかどうか、実行中かどうかなど) を取得する関数について説明します。  
  
 [LocalDBGetInstances 関数](../../relational-databases/express-localdb-instance-apis/localdbgetinstances-function.md)  
 指定されたバージョンの LocalDB インスタンスをすべて返す関数について説明します。  
  
 [LocalDBGetVersionInfo 関数](../../relational-databases/express-localdb-instance-apis/localdbgetversioninfo-function.md)  
 指定された LocalDB バージョンの情報を返す関数について説明します。  
  
 [LocalDBGetVersions 関数](../../relational-databases/express-localdb-instance-apis/localdbgetversions-function.md)  
 コンピューターにインストールされているすべての LocalDB バージョンを返す関数について説明します。  
  
 [LocalDBShareInstance 関数](../../relational-databases/express-localdb-instance-apis/localdbshareinstance-function.md)  
 指定された LocalDB インスタンスを共有するための関数について説明します。  
  
 [LocalDBStartInstance 関数](../../relational-databases/express-localdb-instance-apis/localdbstartinstance-function.md)  
 指定された LocalDB インスタンスを起動する関数について説明します。  
  
 [LocalDBStartTracing 関数](../../relational-databases/express-localdb-instance-apis/localdbstarttracing-function.md)  
 ユーザーの API トレースを有効にする関数について説明します。  
  
 [LocalDBStopInstance 関数](../../relational-databases/express-localdb-instance-apis/localdbstopinstance-function.md)  
 指定された LocalDB インスタンスの実行を停止する関数について説明します。  
  
 [LocalDBStopTracing 関数](../../relational-databases/express-localdb-instance-apis/localdbstoptracing-function.md)  
 ユーザーの API トレースを無効にする関数について説明します。  
  
 [LocalDBUnshareInstance 関数](../../relational-databases/express-localdb-instance-apis/localdbunshareinstance-function.md)  
 指定された LocalDB インスタンスの共有を停止する関数について説明します。  
  
  
