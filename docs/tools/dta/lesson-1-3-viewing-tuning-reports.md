---
title: "チューニング レポートの表示 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: dta
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-query-tuning
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
helpviewer_keywords: tuning reports [SQL Server]
ms.assetid: daee6143-269f-428b-8458-9a3e726d586c
caps.latest.revision: "21"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d270a34d882cbe4c5ffd458e52a9033db1b16c26
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="lesson-1-3---viewing-tuning-reports"></a>レッスン 1 ~ 3 - チューニング レポートの表示
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]このレッスンの前の実習で参照する、[!INCLUDE[tsql](../../includes/tsql-md.md)]スクリプトを作成または MySession チューニング セッションの結果として生成されたデータベース エンジン チューニング アドバイザーの推奨事項でデータベース オブジェクトを削除します。 MySession チューニング セッションは「 [ワークロードのチューニング](../../tools/dta/lesson-1-1-tuning-a-workload.md)」で作成しました。  
  
スクリプトを表示する機能は、チューニング結果の実装に利用できるため非常に便利ですが、データベース エンジン チューニング アドバイザーにはこの他にも便利なレポートが多数用意されています。 これらのレポートは、チューニングするデータベースの既存の物理設計構造、および推奨される構造に関する情報を提供します。 次の実習で説明するように、チューニング レポートを表示するには **[レポート]** タブをクリックします。 この実習では、「 [ワークロードのチューニング](../../tools/dta/lesson-1-1-tuning-a-workload.md) 」および「 [チューニング推奨設定の表示](../../tools/dta/lesson-1-2-viewing-tuning-recommendations.md)」で作成した MySession および EvaluateMySession チューニング セッションを使用します。  
  
### <a name="view-tuning-reports"></a>チューニング レポートの表示  
  
1.  データベース エンジン チューニング アドバイザーを起動します。 「 [データベース エンジン チューニング アドバイザーの起動](../../tools/dta/lesson-1-1-launching-database-engine-tuning-advisor.md)」を参照してください。 このレッスンの前の実習で使用した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続していることを確認してください。  
  
    **[セッション モニター]** ペインの **[MySession]** をダブルクリックします。 このセッションからセッション情報が読み込まれます。  
  
2.  **[レポート]** タブをクリックします。  
  
3.  **[チューニング サマリー]** ペインに、このチューニング セッションに関する情報が表示されます。 このペインの内容をすべて表示するには、スクロール バーを使用します。 **[予測向上率]** と **[推奨構成で使用される容量]**を確認してください。 チューニング オプションを設定する際、推奨設定が使用する容量を制限できます。 **[チューニング オプション]** タブで、 **[詳細設定オプション]**を選択します。 **[推奨インデックス用の最大領域を定義する]** チェック ボックスをオンにし、推奨構成で使用できる最大領域を MB 単位で指定します。 このチュートリアルに戻るには、ヘルプ ブラウザーの **[戻る]** ボタンを使用します。  
  
4.  **[チューニング レポート]** ペインで、 **[レポートの選択]** ボックスの一覧から **[ステートメント コスト レポート]** を選択します。 レポートを表示するためのスペースがさらに必要な場合は、 **[セッション モニター]** ペインの境界を左方向にドラッグします。 データベース内のテーブルに対して実行される [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントのパフォーマンス コストは、ステートメントによって異なります。 テーブル内で、アクセス頻度の高い列に有効なインデックスを作成することによって、このパフォーマンス コストを軽減できます。 このレポートは、ワークロードでの元のステートメント実行コストと、チューニング推奨設定の実装後のコストを比較し、予測向上率を示します。 このレポートに表示される情報量は、ワークロードの規模と複雑さに左右されます。  
  
5.  グリッド領域で **ステートメント コスト レポート** を右クリックし、 **[ファイルへエクスポート]**をクリックします。 「 **MyReport**」という名前でレポートを保存します。 ファイル名には、拡張子 .xml が自動的に付加されます。 使い慣れた XML エディターまたは [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で MyReport.xml を開き、レポートの内容を表示できます。  
  
6.  データベース エンジン チューニング アドバイザーの **[レポート]** タブに戻り、再び **ステートメント コスト レポート** 右クリックします。 使用できるその他のオプションを確認してください。 表示しているレポートのフォントを変更することも可能です。 ここでフォントを変更すると、他のタブ付きページのフォントも変更されます。  
  
7.  **[レポートの選択]** ボックスの一覧で他のレポートをクリックし、どのようなレポートが表示されるかを確認してください。  
  
## <a name="summary"></a>概要  
データベース エンジン チューニング アドバイザー GUI の **[レポート]** タブを使用し、MySession チューニング セッションを検証しました。 同様の手順で、EvaluateMySession チューニング セッションで生成したレポートを調べることができます。 このレポートの内容を検証するには、 **[セッション モニター]** ペインの **[EvaluateMySession]** をダブルクリックします。  
  
## <a name="next-lesson"></a>次のレッスン  
[レッスン 3 : dta コマンド プロンプト ユーティリティの使用](../../tools/dta/lesson-3-using-the-dta-command-prompt-utility.md)  
  
  
  
