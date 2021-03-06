---
title: "変更データを取得および理解する | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: change-data-capture
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: incremental load [Integration Services],retrieving data
ms.assetid: af366697-6942-42bb-aea5-18fdef018965
caps.latest.revision: "30"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d6a3dfdc39808dd1b39ca93fd4dedc0531ed668e
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="retrieve-and-understand-the-change-data"></a>変更データを取得および理解する
  変更データの増分読み込みを実行する [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージのデータ フローにおいて、最初のタスクは、変更データを取得するクエリを実行することです。 このクエリは、データ フロー タスクの変換元コンポーネント内で実行します。 その後、下流にある変換や変換先を使用して、変更データを変換先に適用できます。  
  
> [!NOTE]  
>  テーブル値関数を含むクエリの作成は、変更データの増分読み込みを実行するパッケージを作成するプロセスにおける 3 番目の手順です。 このクエリの詳細については、「[変更データを取得する関数を作成する](../../integration-services/change-data-capture/create-the-function-to-retrieve-the-change-data.md)」を参照してください。 変更データの増分読み込みを実行するパッケージを作成するプロセス全体の説明については、「[変更データ キャプチャ &#40;SSIS&#41;](../../integration-services/change-data-capture/change-data-capture-ssis.md)」を参照してください。  
  
## <a name="adding-the-data-flow-task"></a>データ フロー タスクの追加  
 パッケージのデータ フローでは、変更データを取得し、行われた変更の種類に基づいて行を分割し、変更を変換先に適用します。  
  
#### <a name="to-add-a-data-flow-task-to-the-package"></a>データ フロー タスクをパッケージに追加するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]の **[制御フロー]** タブで、データ フロー タスクを追加します。  
  
2.  クエリ文字列を準備した先行タスクをデータ フロー タスクに連結します。  
  
## <a name="configuring-the-source-component-to-query-for-changes"></a>変更をクエリで取得するための変換元コンポーネントの構成  
 変換元コンポーネントは、変数に格納されている準備済みのクエリ文字列を使用して、変更データを取得するテーブル値関数を呼び出します。  
  
> [!NOTE]  
>  変数に格納されている準備済みのクエリ文字列の詳細については、「 [変更データのクエリを準備する](../../integration-services/change-data-capture/prepare-to-query-for-the-change-data.md)」を参照してください。 変更データを取得するテーブル値関数の詳細については、「 [変更データを取得する関数を作成する](../../integration-services/change-data-capture/create-the-function-to-retrieve-the-change-data.md)」を参照してください。  
  
#### <a name="to-configure-an-ole-db-source-to-retrieve-the-change-data"></a>変更データを取得するように OLE DB ソースを構成するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]の **[データ フロー]** タブで、OLE DB ソースを追加します。  
  
2.  **[OLE DB ソース エディター]**の **[接続マネージャー]** ページで、次のオプションを選択します。  
  
    1.  ソース データベースへの有効な接続を構成します。  
  
    2.  **[データ アクセス モード]**で **[変数からの SQL コマンド]**を選択します。  
  
    3.  **[変数名]**で **[User::SqlDataQuery]**を選択します。  
  
3.  **[OLE DB ソース エディター]**の **[列]** ページで、必要なすべての列が出力列にマップされていることを確認します。  
  
## <a name="next-step"></a>次の手順  
 変更データを取得するように OLE DB ソースを構成したら、次の手順で、パッケージのデータ フローのデザインを開始します。  
  
 **次のトピック:** [挿入、更新、および削除を処理する](../../integration-services/change-data-capture/process-inserts-updates-and-deletes.md)  
  
  
