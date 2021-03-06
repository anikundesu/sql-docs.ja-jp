---
title: "キャッシュ接続マネージャー | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: connection-manager
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.dts.designer.cacheconnection.f1
helpviewer_keywords: Cache connection manager
ms.assetid: bdc92038-3720-4795-8a5c-79b963f2c952
caps.latest.revision: "23"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: df50fb19024245379a92dbb5486d2c2ab035f851
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="cache-connection-manager"></a>キャッシュ接続マネージャー
  キャッシュ接続マネージャーでは、キャッシュ変換またはキャッシュ ファイル (.caw) からデータを読み取り、そのデータをキャッシュ ファイルに保存できます。 キャッシュ ファイルを使用するようにキャッシュ接続マネージャーを構成したかどうかに関係なく、データは常にメモリに格納されます。  
  
 キャッシュ変換を使用して、データ フロー内の接続されているデータ ソースのデータをキャッシュ接続マネージャーに書き込みます。 パッケージ内の参照変換は、データに対する参照を実行します。  
  
> [!NOTE]  
>  キャッシュ接続マネージャーでは、バイナリ ラージ オブジェクト (BLOB) データ型 DT_TEXT、DT_NTEXT、および DT_IMAGE はサポートされません。 参照データセットに BLOB データ型が含まれている場合、パッケージを実行するとコンポーネントは失敗します。 **[キャッシュ接続マネージャー エディター]** を使用して、列のデータ型を変更できます。 詳細については、「 [キャッシュ接続マネージャー エディター](cache-connection-manager-editor.md)」をご覧ください。  
  
> [!NOTE]  
>  パッケージの保護レベルは、キャッシュ ファイルに適用されません。 キャッシュ ファイルに機密情報が含まれている場合は、アクセス制御リスト (ACL) を使用して、ファイルを格納している場所またはフォルダーへのアクセスを制限します。 特定のアカウントに対してのみアクセスを有効にする必要があります。 詳細については、「 [パッケージで使用されるファイルへのアクセス](../../integration-services/security/security-overview-integration-services.md#files)」を参照してください。  
  
## <a name="configuration-of-the-cache-connection-manager"></a>キャッシュ接続マネージャーの構成  
 キャッシュ接続マネージャーは、次の方法で構成できます。  
  
-   キャッシュ ファイルを使用するかどうかを示します。  
  
     キャッシュ ファイルを使用するようにキャッシュ接続マネージャーを構成すると、接続マネージャーは、次のいずれかの処理を実行します。  
  
    -   データ フロー内のデータ ソースからキャッシュ接続マネージャーにデータが書き込まれるようにキャッシュ変換が構成されている場合は、データをファイルに保存します。  
  
    -   キャッシュ ファイルからデータを読み取ります。  
  
     詳しくは、「 [Cache Transform](../../integration-services/data-flow/transformations/cache-transform.md)」をご覧ください。  
  
-   キャッシュに格納されている列のメタデータを変更します。  
  
-   式を使用して ConnectionString プロパティを設定し、実行時にキャッシュ ファイル名を更新します。 詳細については、「 [パッケージでプロパティ式を使用する](../../integration-services/expressions/use-property-expressions-in-packages.md)」を参照してください。  
  
 プロパティを設定するには [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 プログラムによる接続マネージャーの構成方法については、「<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>」および「[プログラムによる接続の追加](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md)」を参照してください。  
  
## <a name="cache-connection-manager-editor"></a>[キャッシュ接続マネージャー エディター]
  キャッシュ接続マネージャーでは、キャッシュ変換またはキャッシュ ファイル (.caw) から参照データセットを読み取り、そのデータをキャッシュ ファイルに保存できます。 データは常にメモリに格納されます。  
  
> [!NOTE]  
>  キャッシュ接続マネージャーでは、バイナリ ラージ オブジェクト (BLOB) データ型 DT_TEXT、DT_NTEXT、および DT_IMAGE はサポートされません。 参照データセットに BLOB データ型が含まれている場合、パッケージを実行するとコンポーネントは失敗します。 **[キャッシュ接続マネージャー エディター]** を使用して、列のデータ型を変更できます。  
  
 参照変換は、参照データセットで参照を実行します。  
  
 **[キャッシュ接続マネージャー エディター]** ダイアログ ボックスには、次のタブがあります。  
  
###  <a name="generaltab"></a> [全般] タブ  
 **[キャッシュ接続マネージャー エディター]** ダイアログ ボックスの **[全般]** タブを使用すると、ファイルからキャッシュを読み取るか、キャッシュをファイルに保存するかを指定できます。  
  
#### <a name="options"></a>オプション  
 **[接続マネージャー名]**  
 ワークフローにおけるキャッシュ接続マネージャーの一意な名前を指定します。 指定された名前は、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーに表示されます。  
  
 **Description**  
 接続の説明を記述します。 パッケージを自己文書化して目的を明確にし、保守が容易になるように、接続の目的に従って記述することをお勧めします。  
  
 **[ファイル キャッシュを使用する]**  
 キャッシュ ファイルを使用するかどうかを示します。  
  
> [!NOTE]  
>  パッケージの保護レベルは、キャッシュ ファイルに適用されません。 キャッシュ ファイルに機密情報が含まれている場合は、アクセス制御リスト (ACL) を使用して、ファイルを格納している場所またはフォルダーへのアクセスを制限します。 特定のアカウントに対してのみアクセスを有効にする必要があります。 詳細については、「 [パッケージで使用されるファイルへのアクセス](../../integration-services/security/security-overview-integration-services.md#files)」を参照してください。  
  
 キャッシュ ファイルを使用するようにキャッシュ接続マネージャーを構成すると、接続マネージャーは、次のいずれかの処理を実行します。  
  
-   データ フロー内のデータ ソースからキャッシュ接続マネージャーにデータが書き込まれるようにキャッシュ変換が構成されている場合は、データをファイルに保存します。 詳しくは、「 [Cache Transform](../../integration-services/data-flow/transformations/cache-transform.md)」をご覧ください。  
  
-   キャッシュ ファイルからデータを読み取ります。  
  
 **ファイル名**  
 キャッシュ ファイルのパスと名前を入力します。  
  
 **参照**  
 キャッシュ ファイルを指定します。  
  
 **[メタデータの更新]**  
 キャッシュ接続マネージャーで列のメタデータを削除し、選択したキャッシュ ファイルの列のメタデータでキャッシュ接続マネージャーを再設定します。  
  
###  <a name="columnstab"></a> [列] タブ  
 **[キャッシュ接続マネージャー エディター]** ダイアログ ボックスの **[列]** タブを使用すると、キャッシュ内の各列のプロパティを構成できます。  
  
#### <a name="options"></a>オプション  
 **列**  
 列名を指定します。  
  
 **[インデックス位置]**  
 各列のインデックス位置を指定して、インデックス列として使用する列を指定します。 インデックスは 1 つまたは複数の列のコレクションです。  
  
 インデックス以外の列の場合、インデックス位置は 0 です。  
  
 インデックス列の場合、インデックスの位置は連続した正の数になります。 この数は、参照変換が参照データセットの行と入力データ ソースの行を比較する順序を示します。 最も固有な値を含む列に、最も小さいインデックス位置を指定する必要があります。  
  
> [!NOTE]  
>  参照変換がキャッシュ接続マネージャーを使用するように構成されている場合、参照データセット内のインデックス列のみ入力列にマップできます。 また、すべてのインデックス列をマップする必要があります。  
  
 **型**  
 列のデータ型を指定します。  
  
 **長さ**  
 列のデータ型を指定します。 **[長さ]**は、そのデータ型で使用できる範囲内であれば更新できます。  
  
 **有効桁数**  
 特定の列のデータ型の有効桁数を指定します。 有効桁数は、数値全体の桁数です。 **[有効桁数]**は、そのデータ型で使用できる範囲内であれば更新できます。  
  
 **Scale**  
 特定の列のデータ型の小数点以下桁数を指定します。 小数点以下桁数は、数値の中で小数点より右側の桁数です。 **[小数点以下桁数]**は、そのデータ型で使用できる範囲内であれば更新できます。  
  
 **コード ページ**  
 列の型のコード ページを指定します。 **[コード ページ]**は、そのデータ型で使用できる範囲内であれば更新できます。  
  
## <a name="related-tasks"></a>関連タスク  
 [キャッシュ接続マネージャーの変換を使用してフル キャッシュ モードの参照変換を実装する](lookup-transformation-full-cache-mode-cache-connection-manager.md)  
  
  
