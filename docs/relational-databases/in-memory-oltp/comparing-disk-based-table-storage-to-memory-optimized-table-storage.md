---
title: "ディスク ベース テーブル ストレージとメモリ最適化テーブル ストレージの比較 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: in-memory-oltp
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eacf443c-001a-445f-ad1c-5f5a45eca6f4
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a76126f9af218e8810e61a9a42ff8c5a92b629d2
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="comparing-disk-based-table-storage-to-memory-optimized-table-storage"></a>ディスク ベース テーブル ストレージとメモリ最適化テーブル ストレージの比較
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  
  
|カテゴリ|ディスク ベース テーブル|持続性のあるメモリ最適化テーブル|  
|----------------|-----------------------|-------------------------------------|  
|DDL (DDL)|メタデータ情報は、データベースのプライマリ ファイル グループのシステム テーブルに格納され、カタログ ビューを使用してアクセスできます。|メタデータ情報は、データベースのプライマリ ファイル グループのシステム テーブルに格納され、カタログ ビューを使用してアクセスできます。|  
|構造体|行は 8 KB 単位のページに格納されます。 1 ページには同じテーブルの行だけが格納されます。|行は個別の行として格納されます。 ページ構造はありません。 データ ファイル内の連続する 2 行はそれぞれ別のメモリ最適化テーブルに属することができます。|  
|インデックス|インデックスは、データ行と同様のページ構造に格納されます。|(インデックス行ではなく) インデックス定義のみが保存されます。 インデックスはメモリ内に保持され、データベース再起動の一部としてメモリ最適化テーブルがメモリに読み込まれるときに再生成されます。 インデックス行は持続しないので、インデックスの変更に対してログ記録は実行されません。|  
|DML 操作|最初の手順は、ページを見つけてバッファー プールに読み込むことです。<br /><br /> Insert<br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、クラスター化インデックスの場合に行の順序を考慮して、ページ上に行を挿入します。<br /><br /> Del<br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、ページ上の削除する行を検索し、削除のマークを付けます。<br /><br /> Update<br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、ページ上の行を検索します。 更新は非キー列に対してインプレースで実行されます。 キー列の更新は削除と挿入操作によって実行されます。<br /><br /> DML 操作の完了後、影響を受けるページは、最小ログ記録操作に関するバッファー プール ポリシー、チェックポイント、またはトランザクションのコミットの一部としてディスクにフラッシュされます。 ページに対する読み取り/書き込みの両方が不要な I/O につながります。|メモリ最適化テーブルの場合、データがメモリに格納されるので、DML 操作はメモリ内で直接実行されます。 メモリ最適化テーブルのログ レコードを読み取ってデータ ファイルとデルタ ファイルに保存するバックグラウンド スレッドがあります。 更新では新しい行バージョンが生成されます。 ただし、更新は削除としてログに記録され、その後に挿入が続きます。|  
|データの断片化|データ操作のフラグメント データにより、一部分しか入力されていないページや、ディスクでは連続していない論理的に連続するページが生じる可能性があります。 これにより、データ アクセスのパフォーマンスが低下するため、データのデフラグが必要になります。|メモリ最適化データはページに格納されないので、データの断片化はありません。 ただし、行が更新または削除されると、データ ファイルとデルタ ファイルは圧縮が必要になります。 これは、マージ ポリシーに基づいて、バックグラウンドの MERGE スレッドで実行されます。|  
  
## <a name="see-also"></a>参照  
 [メモリ最適化オブジェクト用ストレージの作成と管理](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
