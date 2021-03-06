---
title: "接続 (Visual C++ 構文のインデックス #import) |Microsoft ドキュメント"
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
apitype: COM
dev_langs: C++
helpviewer_keywords: 'Connection collection [ADO], Visual C++ syntax index with #import'
ms.assetid: 03f47eda-840d-4cab-83d9-ccddd873f342
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 612860b13b0b739c49a046d3563c1980bb9195e3
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="connection-visual-c-syntax-index-with-import"></a>接続 (Visual C++ 構文のインデックス #import)
## <a name="methods"></a>メソッド  
  
```  
HRESULT Cancel( );  
HRESULT Close( );  
_RecordsetPtr Execute( _bstr_t CommandText, VARIANT *  
    RecordsAffected,     long Options );  
long BeginTrans( );  
HRESULT CommitTrans( );  
HRESULT RollbackTrans( );  
HRESULT Open( _bstr_t ConnectionString, _bstr_t UserID,  
    _bstr_t Password,     long Options );  
_RecordsetPtr OpenSchema( enum SchemaEnum Schema, const  
    _variant_t &     Restrictions = vtMissing, const _variant_t &   
    SchemaID = vtMissing );  
```  
  
## <a name="properties"></a>[プロパティ]  
  
```  
_bstr_t GetConnectionString( );  
void PutConnectionString( _bstr_t pbstr );  
__declspec(property(get=GetConnectionString,put=PutConnectionString))  
    _bstr_t ConnectionString;  
long GetCommandTimeout( );  
void PutCommandTimeout( long plTimeout );  
__declspec(property(get=GetCommandTimeout,put=PutCommandTimeout)) long  
    CommandTimeout;  
long GetConnectionTimeout( );  
void PutConnectionTimeout( long plTimeout );  
__declspec(property(get=GetConnectionTimeout,put=PutConnectionTimeout))  
    long ConnectionTimeout;  
_bstr_t GetVersion( );  
__declspec(property(get=GetVersion)) _bstr_t Version;  
ErrorsPtr GetErrors( );  
__declspec(property(get=GetErrors)) ErrorsPtr Errors;  
_bstr_t GetDefaultDatabase( );  
void PutDefaultDatabase( _bstr_t pbstr );  
__declspec(property(get=GetDefaultDatabase,put=PutDefaultDatabase))  
    _bstr_t DefaultDatabase;  
enum IsolationLevelEnum GetIsolationLevel( );  
void PutIsolationLevel( enum IsolationLevelEnum Level );  
__declspec(property(get=GetIsolationLevel,put=PutIsolationLevel)) enum  
    IsolationLevelEnum IsolationLevel;  
long GetAttributes( );  
void PutAttributes( long plAttr );  
__declspec(property(get=GetAttributes,put=PutAttributes)) long  
    Attributes;  
enum CursorLocationEnum GetCursorLocation( );  
void PutCursorLocation( enum CursorLocationEnum plCursorLoc );  
__declspec(property(get=GetCursorLocation,put=PutCursorLocation)) enum  
    CursorLocationEnum CursorLocation;  
enum ConnectModeEnum GetMode( );  
void PutMode( enum ConnectModeEnum plMode );  
__declspec(property(get=GetMode,put=PutMode)) enum ConnectModeEnum  
    Mode;  
_bstr_t GetProvider( );  
void PutProvider( _bstr_t pbstr );  
__declspec(property(get=GetProvider,put=PutProvider)) _bstr_t  
    Provider;  
long GetState( );  
__declspec(property(get=GetState)) long State;  
```  
  
## <a name="see-also"></a>参照  
 [Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
