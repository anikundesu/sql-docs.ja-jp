---
title: "HelloData: 単純な ADO アプリケーション |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HelloData sample application [ADO]
- ADO, samples
ms.assetid: de4bcd56-dac2-45e6-95ab-9fd7f25878fc
caps.latest.revision: "16"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e1c2733381221139373764577df07afa22e40e49
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="hellodata-a-simple-ado-application"></a>HelloData: 単純な ADO アプリケーション
この単純なアプリケーションをステップ実行の 4 つの主要な ADO 操作: を取得する、検査、編集、およびデータを更新します。 これらの操作は、Microsoft® SQL Server に含まれている、Northwind サンプル データベースに対して実行されます。 ADO の基礎に集中し、コードの煩雑さを防ぐためには、エラー処理の例では最小限です。  
  
### <a name="to-run-hellodata"></a>HelloData を実行するには  
  
1.  ADO ライブラリを参照する新しい標準 EXE Visual Basic プロジェクトを作成します。 詳細については、次を参照してください。 [ADO ライブラリを参照する](../../../ado/guide/referencing-the-ado-libraries.md)です。  
  
2.  フォームの上部にある 4 つのコマンド ボタンを作成、**名前**と**キャプション**プロパティをこのトピックの最後の表に示す値。  
  
3.  ボタンの下に、追加、 **Microsoft DataGrid コントロール**(Msdatgrd.ocx)。 Msdatgrd.ocx ファイルは、Visual Basic に付属しているしは \windows\system32 または \winnt\system32 ディレクトリにあります。 DataGrid コントロールを Visual Basic [ツールボックス] ウィンドウに追加するには、選択**コンポーネント.**から、**プロジェクト**メニュー。 チェック ボックスをオン の横に"Microsoft データ グリッド コントロール 6.0 (SP3) (OLEDB)"をクリックし、 **ok**です。 コントロールをプロジェクトに追加するには、Visual Basic フォームをツールボックスから DataGrid コントロールをドラッグします。  
  
4.  作成、  **テキスト ボックス**グリッドの下のフォーム上の表に示すように、そのプロパティを設定します。 フォームが完了したら、次の図のようになります。  
  
5.  最後に記載されているコードをコピー [HelloData コード](../../../ado/guide/data/hellodata-code.md)、し、フォームのコード エディター ウィンドウに貼り付けます。 キーを押して**f5 キーを押して**コードを実行します。  
  
> [!NOTE]
>  次の例では、およびこのガイドには、ユーザー id"123 abc"のパスワードを使用して"MyId"は、サーバーに対する認証に使用されます。 サーバーの有効なログオンの資格情報でこれらの値を置き換える必要があります。 また、サーバーの名前を持つ"MySQLServer"値に置き換えます。  
  
 コードの詳細については、次を参照してください。 [HelloData に関するコメント](../../../ado/guide/data/comments-on-hellodata.md)です。  
  
 ![HelloData VB アプリケーションの Form1 を示しています](../../../ado/guide/data/media/hellodata.gif "HelloData。")  
  
|コントロール型|プロパティ|値|  
|------------------|--------------|-----------|  
|Form|[オブジェクト名]|Form1|  
||[高さ]|6500|  
||[幅]|6500|  
|MS DataGrid|[オブジェクト名]|grdDisplay1|  
|テキスト ボックス|[オブジェクト名]|txtDisplay1|  
||複数行|true|  
|コマンド ボタン|[オブジェクト名]|cmdGetData|  
||[キャプション]|Get Data|  
|コマンド ボタン|[オブジェクト名]|cmdExamineData|  
||[キャプション]|データを調べる|  
|コマンド ボタン|[オブジェクト名]|cmdEditData|  
||[キャプション]|データを編集します。|  
|コマンド ボタン|[オブジェクト名]|cmdUpdateData|  
||[キャプション]|更新データ|
