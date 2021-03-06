---
title: "グローバル設定 (ログ) (OracleToSQL) |Microsoft ドキュメント"
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
ms.assetid: 12dbcd77-2b90-4fa1-9cf9-239231ea5773
caps.latest.revision: "4"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: f349382a1a94ea621a4c7902f20ac16d381aa2fe
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="global-settings-logging-oracletosql"></a>グローバル設定 (ログ) (OracleToSQL)
使用して、**グローバル設定**ダイアログ ボックスを SSMA のログ設定を指定します。 通常、製品のサポートを使用する場合にのみこれらの設定を変更するは。  
  
このダイアログ ボックスにアクセスする、**ツール**メニューの **グローバル設定**をクリックし、**ログ**左側のウィンドウの下部にあるボタンをクリックします。  
  
## <a name="options"></a>オプション  
**メッセージ レベル**  
次のオプションが 利用可能な**メッセージ レベル**:  
  
|オプション|Description|  
|----------|---------------|  
|**[すべてのカテゴリ]**|次のオプションのすべてのログ記録レベルを設定するために使用します。|  
|**コレクター**|送信元スキーマについてのメタデータを収集し、プロジェクトに保存します。|  
|**コンバーター**|対応するテーブルおよびストアド プロシージャなど、ソース データベース オブジェクトの構造体に変換[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]構造体。|  
|**データの移行**|ソース データベースからデータを移行[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。|  
|**フォーマッタ**|用のスクリプトを生成するコンバーターのサブコンポーネント、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]スキーマです。|  
|**グラフィカル ユーザー インターフェイス**|SSMA ツールを使用するときに表示されるメッセージです。|  
|**リンカー**|SQL 識別子を解決し、その他のコンポーネントに情報を提供します。|  
|**その他**|その他のカテゴリに含まれていないすべてのメッセージ。|  
|**パーサー**|送信元スキーマを解析します。|  
|**シンクロナイザー**|ソースにデータベース オブジェクトの読み込み[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。|  
|**TreeConverter**|ソースのメタデータ内のオブジェクトに変換します[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ。|  
|**テスト担当者**|SSMA Tester を使用するときに表示されるメッセージです。|  
  
各オプションの下の**メッセージ レベル**SSMA の次のログ記録レベルのいずれかを構成します。  
  
|||  
|-|-|  
|**致命的なエラー**|致命的なエラー メッセージのみをログに書き込みます。|  
|**[エラー]**|エラーと致命的なエラー メッセージをログに書き込みます。|  
|**警告**|警告、エラー、および致命的なエラー メッセージをログに書き込みます。|  
|**情報**|情報、警告、エラー、および致命的なエラー メッセージをログに書き込みます。|  
|**デバッグ**|デバッグのログへのメッセージを含む、すべてのメッセージを記述します。|  
  
**ログ ファイルのパス**  
ファイルのパスと SSMA ログ ファイルの名前。 別の名前を指定する、現在のパス をクリックし、クリックし、参照ボタン (**.**) ボタンをクリックします。  
  
**ログ ファイルのサイズ**  
サポート技術情報のログ ファイルの最大サイズ。 最小サイズは、10 KB です。 既定のサイズは 10240 KB です。  
  
**ログ ファイルの合計数**  
1 つのログがいっぱいになる、SSMA は、ログ ファイルの名前を変更し、新しいを開始します。 この設定を使用すると、保持するログ ファイルの最大数を指定します。 最小値は 2 です。  
  
