---
title: "同期メソッド (RDS) |Microsoft ドキュメント"
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.component: reference
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords: Synchronize method [ADO]
ms.assetid: 7af42866-7db2-4174-8251-388a2cf741f2
caps.latest.revision: "16"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c933cbb0a39486ea1ed04b645057bdc31011b05b
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2017
---
# <a name="synchronize-method-rds"></a>同期メソッド (RDS)
ADO 2.5 以降で使用する接続文字列で指定されたデータベースと特定のレコード セットを同期します。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.Synchronize(ConnectionString As String, HandlerString As String, lSynchronizeOptions As Long, ppRecordset As Object, pStatusArray, [lcid As Long], [pInformation)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ConnectionString*  
 要求が送信され、OLE DB プロバイダーへの接続に使用する文字列。 ハンドラーを使用する場合、ハンドラー可能性がありますを編集または接続文字列を置換します。  
  
 *HandlerString*  
 文字列は、この実行で使用するハンドラーを識別します。 文字列には、2 つの部分が含まれています。 最初の部分には、使用するハンドラーの名前 (ProgID) が含まれています。 文字列の 2 番目の部分には、ハンドラーに渡される引数が含まれています。 特定のハンドラーには、引数文字列を解釈する方法です。 (ただし、引数文字列には、追加のコンマを含めることがあります)、2 つの部分は、コンマ、文字列内の最初のインスタンスで区切られます。 引数は省略できます。  
  
 *lSynchronizeOptions*  
 同期オプションのビット マスクです。  
  
 1 =*UpdateTransact*データベースへの更新がトランザクションにラップされます。 更新プログラムの失敗した場合は、トランザクションが中止されました。  
  
 2 =*RefreshWithUpdate*原因行のどちらの場合に返されるステータス*更新*も*RefreshConflicts*設定されています。  
  
 4 =*更新*レコード セットは、データベースの現在のデータを更新します。 保留中の更新は、データベースにプッシュされません。 このビットが設定されていない場合は、レコード セットは更新されず、保留中の更新プログラムがデータベースにプッシュされます。  
  
 8 =*RefreshConflicts*保留中の変更を含む行が更新に失敗します。 データベースから現在のデータでは、更新に失敗した行が更新されます。  
  
 *ppRecordset*  
 同期するレコード セットへのポインター。  
  
 *pStatusArray*  
 影響を受ける行の状態を行のセーフ配列を返すために使用するバリアント型を同期します。 未設定次の同期オプションのいずれも設定されている場合: *RefreshWithUpdate*、*更新*と*RefreshConflicts*です。  
  
 *lcid*  
 返されるエラーをビルドするために使用 LCID *pInformation*です。  
  
 *pInformation*  
 によって返される情報エラーへのポインター **Execute**です。 NULL の場合、エラー情報は返されません。  
  
## <a name="remarks"></a>解説  
 *HandlerString*パラメーターを null にすることがあります。 この場合の動作は、RDS サーバーを構成する方法によって異なります。 "MSDFMAP.handler"のハンドラーの文字列では、Microsoft から提供されたハンドラー (Msdfmap.dll) を使用することを示します。 "MASDFMAP.handler,sample.ini"のハンドラー文字列は、Msdfmap.dll ハンドラーを使用することと、"sample.ini"の引数をハンドラーに渡される必要があることを示します。 Msdfmap.dll は、sample.ini を使用して、接続およびクエリ文字列を確認する方向として、引数を解釈します。  
  
## <a name="applies-to"></a>適用対象  
 [DataFactory オブジェクト (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)


