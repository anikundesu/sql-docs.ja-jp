---
title: "データの更新 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data updates [ADO], about data updates
- updating data [ADO], about updating data
ms.assetid: 6508e4e9-e33a-4dad-b340-5d632fd78a91
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c8138aeea7e5ea40e659a6fed5f5d5f551b1c69d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="updating-data"></a>データの更新
更新プログラムの動作と機能に大きく依存モード (ロックの種類)、カーソルの種類、およびカーソルの場所を更新します。  
  
 使用して、**更新**の現在のレコードに対して行った変更を保存する方法、**レコード セット**呼び出し元からのオブジェクト、 **AddNew**メソッドまたはフィールド値を変更した後既存のレコードです。 **Recordset**オブジェクトが更新をサポートする必要があります。  
  
 場合、 **Recordset**オブジェクトは、バッチ更新をサポートしている、1 つまたは複数のレコードを複数の変更をキャッシュするには、ローカルで呼び出されるまで、 **UpdateBatch**メソッドです。 現在のレコードを編集または呼び出すときに、新しいレコードを追加する場合、 **UpdateBatch**メソッド、ADO の呼び出しは自動的に、**更新**する前に現在のレコードに保留中の変更を保存する方法プロバイダーにバッチ処理された変更を送信します。  
  
 現在のレコードを呼び出した後、**更新**または**UpdateBatch**メソッドです。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [イミディ エイト モード](../../../ado/guide/data/immediate-mode.md)  
  
-   [バッチ モード](../../../ado/guide/data/batch-mode.md)  
  
-   [トランザクション処理](../../../ado/guide/data/transaction-processing.md)