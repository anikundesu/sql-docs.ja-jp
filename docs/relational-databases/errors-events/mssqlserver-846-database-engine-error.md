---
title: MSSQLSERVER_846 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 846 (Database Engine error)
ms.assetid: ccf367eb-06b0-42b8-b4d6-2b88f4a502d3
caps.latest.revision: "17"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9aa5db91ca324f96b69206d23f211f07a046d09a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver846"></a>MSSQLSERVER_846
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|846|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|なし|  
|メッセージ テキスト|バッファー ラッチを待機中にタイムアウトが発生しました。型 %d、BP %p、ページ %d:%d、状態 %#x、データベース ID: %d、アロケーション ユニット ID: %I64d%ls、タスク 0x%p : %d、待機時間 %d、フラグ 0x%I64x、所有しているタスク 0x%p。 待機は続行されません。|  
  
## <a name="explanation"></a>説明  
コンピューターが応答を停止 (ハング) するか、タイムアウトなどにより通常の操作が中断されますが、これと同時に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によってバッファー ラッチ エラーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログに書き込まれています。  
  
メッセージの状態フィールドの値 0x04 がオンの場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は I/O 操作を待機しています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログにメッセージ [MSSQLSERVER_833](~/relational-databases/errors-events/mssqlserver-833-database-engine-error.md) を受信する場合もあります。  
  
メッセージの状態フィールドの値 0x04 がオフの場合、ページに対して多数の競合が存在します。 オブジェクトがデータ ページの場合、非効率なコード デザインに起因している可能性があります。 データ以外のページの場合、ハードウェア リソースの不足など、サーバーのボトルネックによってエラーが発生した可能性があります。  
  
## <a name="user-action"></a>ユーザーの操作  
この問題を回避するには、環境に応じて次の 1 つ以上の手順を実行します。これにより、エラー メッセージの発生を回避または減らすことができる可能性があります。  
  
-   ハードウェアにボトルネックがあるかどうかを判断します。 必要な場合、使用している環境の構成、クエリ、および負荷要件がサポートされるように、ハードウェアをアップグレードします。 ボトルネックの詳細については、「[Identify Bottlenecks](~/relational-databases/performance/identify-bottlenecks.md)」 (ボトルネックの特定) を参照してください。  
  
-   記録されたエラーを確認し、ハードウェア ベンダーの提供する診断を実行します。  
  
-   ディスク ドライブが圧縮されていないことを確認してください。 データ ファイルやログ ファイルを圧縮ドライブに格納することはできません。 物理的ファイルの詳細については、「[Database Files and Filegroups](~/relational-databases/databases/database-files-and-filegroups.md)」 (データベース ファイルとファイル グループ) をご覧ください。  
  
-   次のオプションをオフに設定して、エラー メッセージが消えるかどうかを確認します。  
  
    -   SQL Server の priority boost 構成オプション  
  
    -   簡易プーリング (ファイバー モード) オプション  
  
    -   set working set size オプション  
  
    > [!NOTE]  
    > これらの設定を既定のオフから変更すると、多くの場合、効率が悪化します。 詳細については、「[Server Configuration Options &#40;SQL Server&#41;](~/database-engine/configure-windows/server-configuration-options-sql-server.md)」 (サーバー構成オプション (SQL Server)) を参照してください。  
  
-   クエリをチューニングして、システムで使用するリソースを削減します。 パフォーマンス チューニングは、システム負荷の削減と、個々のクエリの応答時間改善に役立ちます。  
  
-   AUTO_SHRINK オプションをオフにして、データベース サイズに対する変更のオーバーヘッドを軽減します。  
  
-   FILEGROWTH オプションに、頻繁になりすぎないように十分な大きさを持った増分値を設定するようにします。 データベース内で使用可能な領域を確認するジョブをスケジュールし、ピーク時以外にデータベース サイズを大きくします。  
  
