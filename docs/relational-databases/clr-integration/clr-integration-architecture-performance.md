---
title: "CLR 統合のパフォーマンス |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], performance
- common language runtime [SQL Server], compilation process
- performance [CLR integration]
ms.assetid: 7ce2dfc0-4b1f-4dcb-a979-2c4f95b4cb15
caps.latest.revision: "43"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 485a37af0cb6d9d5f7d34986f99db151e59c4628
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="clr-integration-architecture----performance"></a>CLR 統合アーキテクチャのパフォーマンス
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]このトピックでは一部のパフォーマンスを向上させる設計の選択肢の[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]との統合、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 共通言語ランタイム (CLR)。  
  
## <a name="the-compilation-process"></a>コンパイル処理  
 SQL 式のコンパイル時に、マネージ ルーチンへの参照が検出されると、MSIL ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Intermediate Language) スタブが生成されます。 このスタブには、ルーチン パラメーターを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から CLR にマーシャリングして関数を呼び出し、結果を返すコードが含まれています。 この "グルー" (接着剤) コードは、パラメーターの型とパラメーターの方向 (入力、出力、または参照) に基づいています。  
  
 グルー コードを使用することで、型固有の最適化を行い、NULL 値の許容、制約ファセット、値渡し、標準の例外処理などの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セマンティクスを効率的に適用できます。 引数に真数型を使用するコードを生成することで、複数の呼び出しにまたがる型の強制またはラッパー オブジェクト作成によるコストを回避 ("ボックス化") できます。  
  
 生成されたスタブは、CLR の JIT (just-in-time) コンパイル サービスによって、ネイティブ コードへのコンパイル、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行している特定のハードウェア アーキテクチャに合わせた最適化が行われます。 JIT サービスはメソッド レベルで呼び出され、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と CLR 両方を実行するための単一のコンパイル単位を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ホスティング環境で作成できます。 スタブをコンパイルすると、コンパイルされた関数のポインターが関数の実行時の実装になります。 このコード生成方式によって、実行時にリフレクションやメタデータのアクセスのために追加の呼び出しを行うコストを回避することができます。  
  
### <a name="fast-transitions-between-sql-server-and-clr"></a>SQL Server と CLR の高速切り替え  
 コンパイル処理の結果、実行時にネイティブ コードから呼び出すことのできる関数ポインターが生成されます。 ユーザー定義スカラー値関数の場合、関数が行ごとに呼び出されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と CLR の切り替えコストを最小限にするために、マネージ呼び出しを行うステートメントには対象になるアプリケーション ドメインを識別する起動処理があります。 この識別処理により、行ごとの切り替えコストを抑えます。  
  
## <a name="performance-considerations"></a>パフォーマンスに関する考慮事項  
 次に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の CLR 統合固有のパフォーマンスに関する考慮事項を要約します。 詳細な情報が見つかりません"[SQL Server 2005 で CLR 統合を使用して](http://go.microsoft.com/fwlink/?LinkId=50332)"MSDN Web サイトです。 マネージ コードのパフォーマンスに関する一般情報は含まれて"[.NET アプリケーション パフォーマンスの向上とスケーラビリティ](http://go.microsoft.com/fwlink/?LinkId=50333)"MSDN Web サイトです。  
  
### <a name="user-defined-functions"></a>ユーザー定義関数  
 CLR 関数は、[!INCLUDE[tsql](../../includes/tsql-md.md)] のユーザー定義関数に比べて呼び出し手順が速いという利点があります。 また、マネージ コードはプロシージャ コード、計算、および文字列操作のパフォーマンスが [!INCLUDE[tsql](../../includes/tsql-md.md)] に比べて決定的に優れています。 計算中心の CLR 関数およびデータ アクセスを行わない CLR 関数は、マネージ コードで記述する方が適切です。 ただし、データ アクセスは [!INCLUDE[tsql](../../includes/tsql-md.md)] 関数の方が CLR 統合に比べて効率的です。  
  
### <a name="user-defined-aggregates"></a>ユーザー定義集計  
 マネージ コードを使用すると、カーソル ベースの集計よりも大幅に優れたパフォーマンスを発揮できます。 一般的には、組み込みの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 集計関数に比べてマネージ コードはわずかに低速です。 ネイティブの組み込み集計関数が存在する場合は、その関数を使用することをお勧めします。 必要な集計がネイティブにサポートされていない場合、パフォーマンス上の理由からカーソル ベースの実装よりも CLR ユーザー定義集計の使用を検討してください。  
  
### <a name="streaming-table-valued-functions"></a>テーブル値関数のストリーミング  
 関数を呼び出した結果として、テーブルを返す必要性が生じる場合がよくあります。 たとえば、インポート操作の一環としてファイルから表形式のデータを読み取る場合や、コンマ区切りの値をリレーショナル表現に変換する場合などです。 一般的に、このような作業を実現するには、テーブルを呼び出し元で使用する前に、結果テーブルを具体化して値を格納する必要があります。 CLR を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に統合することで、STVF (ストリーミング テーブル値関数) という新しい拡張方式を使用できます。 マネージ STVF は、同様の拡張ストアド プロシージャを実装した場合に比べて、優れたパフォーマンスを発揮します。  
  
 Stvf はマネージ関数を返す、 **IEnumerable**インターフェイスです。 **IEnumerable**は STVF が返した結果セット内を移動する方法があります。 STVF が呼び出されたときに、返された**IEnumerable**クエリ プランに直接接続されています。 クエリ プランの呼び出し**IEnumerable**行をフェッチする必要があるときに、方法です。 このような反復的なモデルにより、テーブル全体に値が格納されるまで待たなくても、最初の行が生成された直後から結果を使用できます。 関数の呼び出しに伴うメモリの消費を大幅に抑えることもできます。  
  
### <a name="arrays-vs-cursors"></a>配列とカーソル  
 配列として簡単に表現できるデータを [!INCLUDE[tsql](../../includes/tsql-md.md)] カーソルでスキャンする必要がある場合、マネージ コードを使用するとパフォーマンスが大幅に向上します。  
  
### <a name="string-data"></a>文字列データ  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]など、データの文字**varchar**、マネージ関数で SqlString または SqlChars 型を指定できます。 SqlString 変数は値全体のインスタンスをメモリに作成します。 SqlChars 変数には、ストリーミング インターフェイスが用意されており、これを使用すると、値全体のインスタンスをメモリに作成しないことでパフォーマンスおよびスケーラビリティを高めることができます。 このことは、特に LOB (ラージ オブジェクト) データにとって重要です。 さらに、XML データをサーバーから使用できますが返すストリーミング インターフェイス**SqlXml.CreateReader()**です。  
  
### <a name="clr-vs-extended-stored-procedures"></a>CLR と拡張ストアド プロシージャ  
 マネージ プロシージャから結果セットをクライアントに返す Microsoft.SqlServer.Server API (アプリケーション プログラミング インターフェイス) は、拡張ストアド プロシージャにより使用される ODS (オープン データ サービス) API に比べパフォーマンスに優れています。 また、System.Data.SqlServer Api サポート データなどの型**xml**、 **varchar (max)**、 **nvarchar (max)**、および**varbinary(max)**で導入された、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]となる一方で、新しいデータ型をサポートするために、ODS Api が拡張されていません。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではマネージ コードによってメモリ、スレッド、同期などのリソースの使用状況が管理されます。 これらのリソースを公開するマネージ API が、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リソース マネージャーの上位に実装されるためです。 逆に、拡張ストアド プロシージャは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によってリソースの使用状況が監視または制御されることがありません。 たとえば、拡張ストアド プロシージャで大量の CPU リソースまたはメモリ リソースが消費されていても、それを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で検出したり制御することはできません。 一方、マネージ コードでは、特定のスレッドが長期間リソースを占有していることを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で検出して、タスクからリソースを解放し、他の作業のスケジュールを設定できるようになります。 つまり、マネージ コードを使用すると、スケーラビリティやシステム リソースの使用状況が改善されます。  
  
 マネージ コードを使用すると、実行環境の保持およびセキュリティ チェックの実施に必要なオーバーヘッドが発生することがあります。 たとえば、([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はネイティブ コードと行き来する際にスレッド固有の設定を保つ必要があるので、) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内でコードを実行し、マネージ コードとネイティブ コードの切り替えを何度も行う必要がある場合などにオーバーヘッドが生じます。 つまり、マネージ コードとネイティブ コードの切り替えが頻発する場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内で実行されるマネージ コードに比べて、拡張ストアド プロシージャの方が高いパフォーマンスを発揮できます。  
  
> [!NOTE]  
>  この機能の使用は推奨されないため、拡張ストアド プロシージャを新規作成しないことをお勧めします。  
  
### <a name="native-serialization-for-user-defined-types"></a>ユーザー定義型のネイティブ シリアル化  
 UDT (ユーザー定義型) は、スカラー型システムの拡張方式として設計されています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]という Udt のシリアル化形式が実装されて**Format.Native**です。 コンパイルのとき、型の定義に合わせてカスタマイズされた MSIL を生成するために型の構造を検査します。  
  
 ネイティブ シリアル化は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定の実装です。 ユーザー定義のシリアル化を行うと、型の作成者がシリアル化のために定義したメソッドが呼び出されます。 **Format.Native**シリアル化可能な場合に最適なパフォーマンスに使用します。  
  
### <a name="normalization-of-comparable-udts"></a>同等の UDT の正規化  
 UDT の並べ替え、比較などのリレーショナル操作で、値のバイナリ表現を直接操作します。 これを行うには、ディスクに UDT の状態を正規化した (バイナリ順にした) 表現を格納します。  
  
 正規化には 2 つの利点があります。1 つは、型のインスタンスの作成やメソッド呼び出しのオーバヘッドが発生しないようにすることで比較操作のコストが大幅に抑えられることです。もう 1 つは、UDT のバイナリ領域が作成され、ヒストグラム、インデックス、およびその型の値のヒストグラムが作成できるようになることです。 つまり、メソッド呼び出しを伴わない操作では、正規化した UDT はネイティブの組み込み型と変わらないパフォーマンスを発揮します。  
  
### <a name="scalable-memory-usage"></a>スケーラビリティを確保するメモリの使用方法  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージ ガベージ コレクションのパフォーマンスやスケーラビリティを高めるには、大量のメモリを 1 単位として割り当てないようにしてください。 88 KB を超える割り当てはラージ オブジェクト ヒープに配置されます。その結果、小規模の割り当てをいくつも行った場合に比べて、ガベージ コレクションのパフォーマンスやスケーラビリティが低下します。 たとえば、大きな多次元配列を割り当てる場合、ジャグ (散在した) 配列を割り当てることをお勧めします。  
  
## <a name="see-also"></a>参照  
 [CLR ユーザー定義型](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
  
  
