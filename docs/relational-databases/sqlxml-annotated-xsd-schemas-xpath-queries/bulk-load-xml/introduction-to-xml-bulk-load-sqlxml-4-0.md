---
title: "XML 一括読み込み (SQLXML 4.0) の概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- nontransacted XML Bulk Load operations
- XML Bulk Load [SQLXML], about XML Bulk Load
- bulk load [SQLXML], about bulk load
- transacted XML Bulk Load operations
- streaming XML data
ms.assetid: 38bd3cbd-65ef-4c23-9ef3-e70ecf6bb88a
caps.latest.revision: "13"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f687a25a48ff38ee8b109161e332f7306d64f177
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="introduction-to-xml-bulk-load-sqlxml-40"></a>XML 一括読み込みの概要 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]Microsoft に半構造化 XML データを読み込むことができますをスタンドアロン COM オブジェクトは、XML 一括読み込み[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]テーブル。  
  
 INSERT ステートメントと OPENXML 関数を使用すれば、XML データを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースに挿入できますが、大量の XML データを挿入する必要があるときには、一括読み込みユーティリティを使用すると効率的です。  
  
 XML 一括読み込みオブジェクト モデルの Execute メソッドは、次の 2 つのパラメーターを受け取ります。  
  
-   注釈付き XML Schema Definition (XSD) または XML-Data Reduced (XDR) スキーマ。 XML 一括読み込みユーティリティでは、このスキーマで指定されたマッピング スキーマと注釈が解釈され、XML データを挿入する SQL Server テーブルが特定されます。  
  
-   XML ドキュメント、またはドキュメント フラグメント (単一の最上位要素がないドキュメント)。 XML 一括読み込みで読み込むことができるファイル名またはストリームを指定できます。  
  
 XML 一括読み込みではマッピング スキーマが解釈されて、XML データを挿入するテーブルが特定されます。  
  
 ユーザーは、次の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 機能について理解していることを前提としています。  
  
-   注釈付き XSD および XDR スキーマ。 注釈付き XSD スキーマの詳細については、次を参照してください[注釈付き XSD スキーマ &#40; の概要。SQLXML 4.0 &#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md). 注釈付き XDR スキーマについては、次を参照してください。[注釈付き XDR スキーマ &#40; SQLXML 4.0 &#41; で推奨されなくなった](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)です。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の BULK INSERT ステートメント、bcp ユーティリティなどの [!INCLUDE[tsql](../../../includes/tsql-md.md)] 一括挿入メカニズム。 詳細については、次を参照してください。[一括挿入 (&) #40 です。TRANSACT-SQL と #41 です。](../../../t-sql/statements/bulk-insert-transact-sql.md)と[bcp ユーティリティ](../../../tools/bcp-utility.md)です。  
  
## <a name="streaming-of-xml-data"></a>XML データのストリーミング  
 ソースの XML ドキュメントは大きい可能性があるため、一括読み込み処理では、メモリにドキュメント全体は読み込まれません。 代わりに、XML 一括読み込みでは XML データがストリームとして解釈され読み取られます。 データが読み取られるとき、このユーティリティではデータベース テーブルが特定され、XML データ ソースを基に適切なレコードが生成された後、そのレコードが挿入のため [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に送信されます。  
  
 たとえば、次のソース XML ドキュメントから成る**\<顧客 >**要素および**\<順序 >**子要素。  
  
```  
<Customer ...>  
    <Order.../>  
    <Order .../>  
     ...  
</Customer>  
...  
```  
  
 XML 一括読み込みの読み取りを始めると、 **\<顧客 >**要素、Customertable のレコードが生成されます。 読み取られる、  **\</Customer >**終了タグ、XML 一括読み込みの挿入でテーブルに記録する[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]です。 同じで、それを読み取るとき、 **\<順序 >**要素、XML 一括読み込みが、Ordertable のレコードの生成およびにそのレコードを挿入、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]読み取り時にテーブル、  **\</注文 >**タグを終了します。  
  
## <a name="transacted-and-nontransacted-xml-bulk-load-operations"></a>トランザクション モードとトランザクション以外のモードでの XML 一括読み込みの操作  
 XML 一括読み込みは、トランザクション モードまたはトランザクション以外のモードで操作できます。 パフォーマンスは通常、トランザクション以外のモードで一括読み込みを行う場合に最適な: トランザクションのプロパティが FALSE に設定は、) 次の条件のいずれかが true とします。  
  
-   データの一括読み込みの対象テーブルが空で、インデックスが作成されていない。  
  
-   テーブルにデータと一意のインデックスが格納されている。  
  
 トランザクション以外のモードで一括読み込みを実行する場合は、一括読み込み中に問題が発生したとしてもロールバックは保証されません (ただし、部分ロールバックは実行されることがあります)。 トランザクション以外のモードでの一括読み込みは、データベースが空の場合に適しています。 この場合、問題が発生したらデータベースの内容を消去して、XML 一括読み込みを再実行できます。  
  
> [!NOTE]  
>  トランザクション以外のモードの場合、XML 一括読み込みでは既定の内部トランザクションが使用され、そのトランザクションがコミットされます。 トランザクションのプロパティが TRUE に設定されている場合は、XML 一括読み込みはこのトランザクションのコミットを呼び出しません。  
  
 トランザクションのプロパティが TRUE に設定されている場合、XML 一括読み込みは一時ファイル、マッピング スキーマで識別されるテーブルごとに 1 つを作成します。 ソース XML ドキュメントからのレコードは、最初に XML 一括読み込みによってこれらの一時ファイルに保存され、 次に [!INCLUDE[tsql](../../../includes/tsql-md.md)] BULK INSERT ステートメントによって一時ファイルから取得されて、対応するテーブルに保存されます。 TempFilePath プロパティを使用して、これらの一時ファイルの場所を指定できます。 XML 一括読み込みで使用される [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] アカウントからは、このパスにアクセスできる必要があります。 TempFilePath プロパティが指定されていない場合、TEMP 環境変数で指定されている既定のファイル パスは一時ファイルの作成に使用されます。  
  
 トランザクションのプロパティが FALSE (既定の設定) に設定されている場合に、一括読み込みデータを OLE DB インターフェイス IRowsetFastLoad XML 一括読み込みでいます。  
  
 ConnectionString プロパティは、接続文字列を設定すると、トランザクションのプロパティが TRUE に設定、XML 一括読み込みは、独自のトランザクション コンテキストで動作します。 たとえば、XML 一括読み込みでは自身のトランザクションが開始され、必要に応じてコミットまたはロールバックが行われます。  
  
 ConnectionCommand プロパティを設定する場合は、既存の接続オブジェクトとトランザクションのプロパティとの接続が TRUE に設定されている、XML 一括読み込みが成功または失敗の場合、COMMIT または ROLLBACK ステートメントをそれぞれ発行しません。 エラーが発生した場合、XML 一括読み込みでは適切なエラー メッセージが返されます。 COMMIT または ROLLBACK ステートメントを発行するかどうかは、一括読み込みを実行したクライアントで決定されます。 XML 一括読み込みに使用される接続オブジェクトは、型 ICommand であるか、ADO コマンド オブジェクトであるください。  
  
 SQLXML 4.0 で、トランザクション セットを持つプロパティを FALSE に、ConnectionObject は使用できません。 渡されたセッションの 1 つ以上の IRowsetFastLoad インターフェイスを開くことはできませんので、トランザクション以外のモードは、ConnectionObject でサポートされていません。  
  
  
