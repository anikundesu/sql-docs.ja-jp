---
title: "SQL Server Management Studio の機能 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], about SQL Server Management Studio
- scripts [SQL Server], SQL Server Management Studio
ms.assetid: e75504b9-7968-4e3b-8411-fd79fe09021e
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 82a8f1c09d51ad35b9d61e68b6878dc90b7d617c
ms.lasthandoff: 04/11/2017

---
# <a name="features-in-sql-server-management-studio"></a>SQL Server Management Studio の機能
[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] には、以下のような全般的な機能が用意されています。  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)]のほとんどの管理タスクをサポートしています。  
  
-   [!INCLUDE[ssDEnoversion](../includes/ssdenoversion_md.md)] の管理と作成のための一元的な統合環境。  
  
-   [!INCLUDE[ssDEnoversion](../includes/ssdenoversion_md.md)]、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)]、および [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion_md.md)]のオブジェクトを管理するためのダイアログ。これらのダイアログでは、各種の操作をすぐに実行することも、コード エディターに送ることも、後から実行するためにスクリプト化することもできます。  
  
-   サイズ変更が可能な非モーダル ダイアログ。ダイアログを開いたまま複数のツールにアクセスできます。  
  
-   共通のスケジュール設定ダイアログ。管理ダイアログの操作を後で実行できます。  
  
-   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] のサーバー登録を [!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)] 環境間でエクスポート/インポートできます。  
  
-   SQL Server Profiler によって生成される XML プラン表示ファイルやデッドロック ファイルの保存や印刷を行えるので、それらのファイルを後で検討したり、分析のために管理者に送ることが可能です。  
  
-   エラーと情報に関する新しいメッセージ ボックス。これにはさらに多くの情報が表示されるようになり、メッセージに関するコメントを [!INCLUDE[msCoName](../includes/msconame_md.md)] に送信することや、メッセージをクリップボードにコピーすること、サポート チームに電子メールの形でメッセージを簡単に送信することも可能です。  
  
-   MSDN やオンライン ヘルプをすばやく参照するための統合 Web ブラウザー。  
  
-   オンライン コミュニティとヘルプ システムの統合  
  
-   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] のチュートリアルを行えば、多くの新しい機能をすぐに活用して生産性を向上させるのに役立ちます。  
  
-   フィルター機能や自動更新機能が付いた新しい利用状況モニター。  
  
-   統合データベース電子メール インターフェイス。  
  
## <a name="new-scripting-capabilities"></a>新しいスクリプト機能  
[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] のコンポーネントであるコード エディターには、 [!INCLUDE[tsql](../includes/tsql_md.md)]、MDX、DMX、XML/A の各スクリプトを作成するための統合スクリプト エディターがそれぞれ組み込まれています。 主な機能は、以下のとおりです。  
  
-   ダイナミック ヘルプによって、作業中に関連情報をすばやく表示できます。  
  
-   豊富なテンプレートが用意されており、カスタム テンプレートも作成できます。  
  
-   サーバーに接続しないでクエリやスクリプトの作成や編集を行えます。  
  
-   SQLCMD のクエリやスクリプトがサポートされています。  
  
-   XML 結果を表示するための新しいインターフェイスが用意されています。  
  
-   ソリューションやスクリプト プロジェクトのための統合ソース管理によって、スクリプトのコピーを格納し、スクリプトの開発過程を管理できます。  
  
-   [!INCLUDE[msCoName](../includes/msconame_md.md)] IntelliSense によって MDX ステートメントがサポートされています。  
  
## <a name="object-explorer-features"></a>オブジェクト エクスプローラーの機能  
[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] のコンポーネントであるオブジェクト エクスプローラーは、あらゆる種類のサーバー内のオブジェクトを表示して管理するための統合ツールです。 主な機能は、以下のとおりです。  
  
-   名前、スキーマ、日付の全体または一部に基づくフィルターを適用できます。  
  
-   オブジェクトの非同期設定が可能であり、メタデータに基づくフィルターをオブジェクトに適用することもできます。  
  
-   管理作業のためにレプリケーション サーバー上の [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] エージェントにアクセスできます。  
  
詳細については、「 [オブジェクト エクスプローラー](../ssms/object/object-explorer.md)」を参照してください。  
  
## <a name="extensibility"></a>機能拡張  
[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] は Visual Studio の分離シェルに基づいて構築されているため、機能拡張 (アドイン/プラグイン) を本質的にサポートします。 Visual Studio の機能拡張サービスを活用すると、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)]内のカスタム機能を外部に公開できますが、このような機能拡張はサポートされていません。  
  
ユーザーやサードパーティが [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)]の拡張機能を開発していることがあります。 禁止はしていませんが、そのような機能拡張はサポートされないので、前方/後方互換性の問題が発生する可能性があることに留意してください。 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)]の拡張に関するドキュメントは Microsoft からは公開していません。 ただし、利用できる可能性があるコミュニティ ブログやサンプル コードは存在します。  
  
マイクロソフトでは、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] の拡張機能を適用した [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] のインストールをサポートしていません。そのため、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] の拡張機能をインストール済みの場合は、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] の問題に関してマイクロソフト カスタマー サポートにお問い合わせいただく前に、それらを削除する必要があります。  
  
## <a name="see-also"></a>参照  
[SQL Server Management Studio の使用 [SQL Server]](../ssms/use-sql-server-management-studio.md)  
  
