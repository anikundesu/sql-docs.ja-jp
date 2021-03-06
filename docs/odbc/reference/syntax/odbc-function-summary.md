---
title: "ODBC 関数の概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: functions [ODBC], listed by task
ms.assetid: 7aa635da-e6b7-439f-8e9b-c3860e24de5e
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bce96e014e56a783f4f367120f1ba6f911d91ed5
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="odbc-function-summary"></a>ODBC 関数の概要
次の表は、ODBC 関数をタスクの種類別にグループ化し、の適合性表記と各関数の目的の簡単な説明が含まれています。 準拠の詳細については、次を参照してください。 [ODBC と標準の CLI](../../../odbc/reference/odbc-and-the-standard-cli.md)です。 各関数のセマンティクスと構文に関する詳細については、次を参照してください。 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 アプリケーションが呼び出すことができます、 **SQLGetInfo**ドライバーに関する準拠情報を取得します。 ドライバーでは、特定の関数のサポートに関する情報を取得するアプリケーションを呼び出すことができます**SQLGetFunctions**です。  
  
|タスク|関数名|準拠|用途|  
|----------|-------------------|-----------------|-------------|  
|データ ソースへの接続|[SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)|ISO 92|環境、接続、ステートメント、または記述子ハンドルを取得します。|  
||[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|ISO 92|データ ソース名、ユーザー ID とパスワードによって特定のドライバーに接続します。|  
||[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|ODBC|接続文字列または要求が、ドライバー マネージャーとドライバーがユーザーの接続 ダイアログ ボックスを表示することによって、特定のドライバーに接続します。|  
||[SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|ODBC|連続するレベルの接続属性と有効な属性値を返します。 各接続属性の値を指定すると、データ ソースに接続します。|  
|ドライバーとデータ ソースに関する情報の取得|[SQLDataSources](../../../odbc/reference/syntax/sqldatasources-function.md)<br /><br /> [SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)|ISO 92<br /><br /> ODBC|使用可能なデータ ソースの一覧を返します。<br /><br /> インストールされているドライバーとその属性の一覧を返します。|  
||[SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)|ISO 92|特定のドライバーとデータ ソースに関する情報を返します。|  
||[SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md)|ISO 92|返しますには、ドライバー関数がサポートされています。|  
||[SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)|ISO 92|サポートされるデータ型に関する情報を返します。|  
|設定およびドライバーの属性を取得します。|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)<br /><br /> [SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|ISO 92<br /><br /> ISO 92|接続属性を設定します。<br /><br /> 接続属性の値を返します。|  
||[SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|ISO 92|環境属性を設定します。|  
||[SQLGetEnvAttr](../../../odbc/reference/syntax/sqlgetenvattr-function.md)|ISO 92|環境属性の値を返します。|  
||[SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|ISO 92|ステートメント属性を設定します。|  
||[SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|ISO 92|ステートメント属性の値を返します。|  
|設定および記述子フィールドを取得します。|[SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)<br /><br /> [SQLGetDescRec](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|ISO 92<br /><br /> ISO 92|1 つの記述子フィールドの値を返します。<br /><br /> 複数の記述子フィールドの値を返します。|  
||[SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|ISO 92|1 つの記述子フィールドを設定します。|  
||[SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|ISO 92|複数の記述子フィールドを設定します。|  
||[SQLCopyDesc](../../../odbc/reference/syntax/sqlcopydesc-function.md)|ISO 92|別の記述子が 1 つのハンドルから記述子情報をコピーします。|  
|SQL の準備を要求します。|[SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|ISO 92|後で実行する SQL ステートメントを準備します。|  
||[SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|ODBC|SQL ステートメントにパラメーターの記憶域を割り当てます。|  
||[SQLGetCursorName](../../../odbc/reference/syntax/sqlgetcursorname-function.md)|ISO 92|ステートメント ハンドルに関連付けられているカーソル名を返します。|  
||[SQLSetCursorName](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|ISO 92|カーソル名を指定します。|  
||[SQLSetScrollOptions](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md)|ODBC|カーソルの動作を制御するオプションを設定します。|  
|要求を送信します。|[SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)<br /><br /> [SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|ISO 92<br /><br /> ISO 92|準備されたステートメントを実行します。<br /><br /> ステートメントを実行します。|  
||[SQLNativeSql](../../../odbc/reference/syntax/sqlnativesql-function.md)|ODBC|ドライバーによって変換された SQL ステートメントのテキストを返します。|  
||[SQLDescribeParam](../../../odbc/reference/syntax/sqldescribeparam-function.md)|ODBC|ステートメントでは、特定のパラメーターの説明を返します。|  
||[SQLNumParams](../../../odbc/reference/syntax/sqlnumparams-function.md)|ISO 92|ステートメントでパラメーターの数を返します。|  
||[SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)|ISO 92|組み合わせて使用**SQLPutData**実行時にパラメーター データを指定します。 (長い形式のデータ値に役立ちます。)|  
||[SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|ISO 92|パラメーターのデータ値の一部またはすべてを送信します。 (長い形式のデータ値に役立ちます。)|  
|結果と結果に関する情報を取得します。|[SQLRowCount](../../../odbc/reference/syntax/sqlrowcount-function.md)<br /><br /> [SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|ISO 92<br /><br /> ISO 92|Insert、update、または delete 要求を受けた行の数を返します。<br /><br /> 結果セット内の列数を返します。|  
||[SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|ISO 92|結果セット内の列について説明します。|  
||[SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|ISO 92|結果セットの列の属性について説明します。|  
||[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|ISO 92|結果列のストレージを割り当て、データ型を指定します。|  
||[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|ISO 92|複数の結果行を返します。|  
||[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|ISO 92|スクロール可能な結果の行を返します。|  
||[SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|ISO 92|返します。 一部またはすべての結果の 1 つの行の 1 つの列の次のように設定します。 (長い形式のデータ値に役立ちます。)|  
||[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|ODBC|データのフェッチされたブロック内でカーソルを配置し、により、アプリケーション、行セット内のデータを更新するか、結果セット内のデータ更新または削除します。|  
||[SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|ODBC|一括挿入や一括ブックマークを実行する操作 (更新プログラムを含む) は、削除、およびブックマークでフェッチします。|  
||[SQLMoreResults](../../../odbc/reference/syntax/sqlmoreresults-function.md)|ODBC|以上の結果は、使用可能な設定し場合は、次の結果セットの処理を初期化します。 があるかどうかを判断します。|  
||[SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)|ISO 92|追加の診断情報 (診断データの構造体の 1 つのフィールド) を返します。|  
||[SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|ISO 92|追加の診断情報 (診断データの構造体の複数のフィールド) を返します。|  
|データ ソースのシステム テーブル (カタログ関数) に関する情報の取得|[SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)<br /><br /> [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)|ODBC<br /><br /> [グループを開く]|列と 1 つまたは複数のテーブルの関連する権限の一覧を返します。<br /><br /> 指定されたテーブル内の列名の一覧を返します。|  
||[SQLForeignKeys](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|ODBC|指定したテーブルに存在する場合は、外部キーを構成する列名の一覧を返します。|  
||[SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|ODBC|テーブルの主キーを構成する列名の一覧を返します。|  
||[SQLProcedureColumns](../../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|ODBC|入力と出力パラメーター、および指定したプロシージャの結果セットを構成する列の一覧を返します。|  
||[SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md)|ODBC|特定のデータ ソースに格納されているプロシージャ名の一覧を返します。|  
||[SQLSpecialColumns](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|[グループを開く]|指定されたテーブル内の行を一意に識別する列または行の任意の値が、トランザクションによって更新されたときに自動的に更新される列の最適なセットに関する情報を返します。|  
||[SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|ISO 92|1 つのテーブルとテーブルに関連付けられているインデックスの一覧に関する統計を返します。|  
||[SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|ODBC|テーブルと各テーブルに関連付けられている権限の一覧を返します。|  
||[SQLTables](../../../odbc/reference/syntax/sqltables-function.md)|[グループを開く]|特定のデータ ソースに格納されているテーブル名の一覧を返します。|  
|ステートメントの終了|[SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)|ISO 92|終了ステートメントの処理、保留中の結果を破棄し、必要に応じて、ステートメント ハンドルに関連付けられているすべてのリソースを解放します。|  
||[SQLCloseCursor](../../../odbc/reference/syntax/sqlclosecursor-function.md)|ISO 92|ステートメント ハンドルで開かれたカーソルを閉じます。|  
||[SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|ISO 92|ステートメントで処理をキャンセルします。|  
||[SQLCancelHandle](../../../odbc/reference/syntax/sqlcancelhandle-function.md)|ODBC|ステートメントまたは接続に対して処理をキャンセルします。|  
||[SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|ISO 92|コミットまたはトランザクションをロールバックします。|  
|接続の終了|[SQLDisconnect](../../../odbc/reference/syntax/sqldisconnect-function.md)<br /><br /> [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)|ISO 92<br /><br /> ISO 92|接続を閉じます。<br /><br /> 環境、接続、ステートメント、または記述子ハンドルを解放します。|
