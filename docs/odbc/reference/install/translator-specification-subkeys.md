---
title: "トランスレーター仕様サブキー |Microsoft ドキュメント"
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
helpviewer_keywords:
- translator subkey [ODBC]
- registry entries for components [ODBC], translator specification subkeys
- translator specification subkeys [ODBC]
- subkeys [ODBC], translator specification subkeys
ms.assetid: 3c0edeee-d43a-4466-a177-bf2d2435707a
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ec8f2b705ca226f94f2fcea9cf79aa8a7cdc31c4
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="translator-specification-subkeys"></a>変換プログラムの仕様のサブキー
ODBC 変換器サブキーに表示されている各翻訳には、独自のサブキーがあります。 このサブキーは、ODBC 変換器のサブキーの下の対応する値として同じ名前を持ちます。 このサブキーの下の値は、変換、変換プログラムのセットアップ Dll と使用率カウントの完全パスを一覧表示します。 値の形式は、次の表に示すようにします。  
  
|名前|データ型|data|  
|----------|---------------|----------|  
|[変換者]|REG_SZ|*トランスレーター DLL パス*|  
|セットアップ|REG_SZ|*セットアップ DLL パス*|  
|UsageCount|REG_DWORD|*count*|  
  
 使用状況カウントの詳細については、次を参照してください。[使用状況カウント](../../../odbc/reference/install/usage-counting.md)このセクションで前述しました。  
  
 アプリケーションでは、使用率カウントは設定しないでください。 ODBC では、この数が維持されます。  
  
 たとえば、Microsoft のコード ページ変換プログラム翻訳トランスレーター セットアップ関数が、同じ DLL に含まれる Mscpxl32.dll をという名前の DLL があり、3 回、変換プログラムがインストールされているとします。 Microsoft コード ページ変換プログラムのサブキーの下の値は次のあります。  
  
```  
Translator : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
Setup : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
UsageCount : REG_DWORD : 0x3  
```
