---
title: "DataSpace (ADO - WFC 構文) |Microsoft ドキュメント"
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
helpviewer_keywords: DataSpace collection [ADO], ADO/WFC syntax
ms.assetid: 950d45d8-07de-467b-b255-f9a7b997204c
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2fcb4480b7dcbc31849e213b01dd442df3d4c1d7
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="dataspace-ado---wfc-syntax"></a>DataSpace (ADO - WFC 構文)
**CreateObject**のメソッド、 **DataSpace**クラスがクライアント アプリケーションの要求を処理する、両方のビジネス オブジェクトを指定します (*progid*) との通信プロトコルサーバー (*接続*)。 **createObject**を返します、 [ObjectProxy](../../../ado/reference/ado-api/objectproxy-ado-wfc-syntax.md)サーバーを表すオブジェクト。  
  
## <a name="package-commswfcdata"></a>パッケージ com.ms.wfc.data  
  
### <a name="constructor"></a>コンス トラクター  
  
```  
public DataSpace()  
```  
  
### <a name="methods"></a>メソッド  
  
```  
public static ObjectProxy DataSpace.createObject(String  
    progid, String connection)  
```  
  
### <a name="properties"></a>[プロパティ]  
  
```  
public static int getInternetTimeout()  
public static void setInternetTimeout(int plInetTimeout)  
```  
  
## <a name="see-also"></a>参照  
 [DataSpace オブジェクト (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)
