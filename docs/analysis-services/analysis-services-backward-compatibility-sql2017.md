---
title: "SQL Server 2017 Analysis Services の旧バージョンと互換性 |Microsoft ドキュメント"
ms.date: 07/11/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installing Analysis Services, backward compatibility
- backward compatibility [Analysis Services]
- compatibility [Analysis Services]
- Analysis Services, backward compatibility
- upgrading Analysis Services
- SSAS, backward compatibility
- SQL Server Analysis Services, backward compatibility
ms.assetid: 
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 972ab981eccb6271dfa2f18e0b482f43020ff36b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="analysis-services-backward-compatibility-sql-2017"></a>Analysis Services の旧バージョンとの互換性 (SQL 2017)
[!INCLUDE[ssas-appliesto-sql2017](../includes/ssas-appliesto-sql2017.md)]

この記事では、機能の可用性と現在のリリースと、以前のリリースの間での動作の変更について説明します。

## <a name="deprecated-features"></a>非推奨機能
A*非推奨の機能*将来のリリースで製品から廃止されますが、まだサポートされ、旧バージョンとの互換性を維持するために、現在のリリースに含まれています。 今後のリリースとの互換性を維持するために新規および既存のプロジェクトでは非推奨機能を使用して停止するをお勧めします。

このリリースでは、次の機能が廃止されました。
  
|||  
|-|-|  
|**モード/カテゴリ**|**機能**|
|テーブル|リモート リンク メジャー グループ|
|テーブル|1100 と 1103 互換性レベル モデル|
|テーブル|表形式オブジェクト モデルのプロパティ: Column.TableDetailPosition、Column.IsDefaultLabel、Column.IsDefaultImage|
|多次元|データ マイニング|

## <a name="discontinued-features"></a>廃止された機能
A*提供が中止された機能*以前のリリースでは推奨されなくなりました。 現在のリリースに含まれる継続可能性がありますが、現在サポートされていません。 廃止された機能を削除することがあります、将来のリリースか更新します。

次の機能は、以前のリリースで非推奨となったし、このリリースではサポートされなくです。
  
|||  
|-|-|  
|**モード/カテゴリ**|**機能**|  
|テーブル|VertipaqPagingPolicy メモリ プロパティの値 (2)、メモリを使用してディスクへのページングを有効にするには、ファイルがマップされています。|
|多次元|リモート パーティション|  
|多次元|リモート リンク メジャー グループ|  
|多次元|ディメンションの書き戻し|  
|多次元|リンク ディメンション|
|ツール|SQL Server Profiler for Trace Capture<br /><br /> この機能に代えて、SQL Server Management Studio に組み込まれている Extended Events Profiler を使用します。  <br /> 「 [Monitor Analysis Services with SQL Server Extended Events](../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md)」を参照してください。|  
|ツール|Server Profiler for Trace Replay <br />置換します。 これに代わる機能はありません。|  
|トレース管理オブジェクトおよびトレース API|Microsoft.AnalysisServices.Trace オブジェクト (Analysis Services Trace および Replay オブジェクトの API を含みます)。 置き換えは、複数の手順で行います。<br /><br /> - トレース構成:  Microsoft.SqlServer.Management.XEvent<br />- トレース読み取り:  Microsoft.SqlServer.XEvent.Linq<br />- トレース再生: なし|  

## <a name="breaking-changes"></a>重大な変更
A*互換性に影響する変更*現在のリリースにアップグレードした後、機能、データ モデル、アプリケーション コードまたはスクリプトが機能しなくをによりします。

このリリースでは、互換性に影響する変更はありません。

## <a name="behavior-changes"></a>動作の変更
A*動作の変更*現在のリリース以前のリリースと比較して同じ機能の動作に影響します。 重要な動作の変更のみを説明します。 ユーザー インターフェイスの変更は含まれません。

このリリースでの動作の変更はありません。


## <a name="see-also"></a>参照
[Analysis Services の旧バージョンとの互換性 (SQL Server 2016)](analysis-services-backward-compatibility.md)