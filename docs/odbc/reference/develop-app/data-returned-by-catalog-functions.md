---
title: "カタログ関数によって返されるデータ |Microsoft ドキュメント"
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
- catalog functions [ODBC], result sets
- functions [ODBC], catalog functions
ms.assetid: 399e1a64-8766-4c44-81ff-445399b7a1de
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 46b8a628b6b8e6ad9a2eb3164e6935f3f3401ec8
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="data-returned-by-catalog-functions"></a>カタログ関数によって返されるデータ
各カタログ関数では、データがその結果セットを返します。 この結果セットは、その他の結果セットから変わりません。 生成される通常、定義済みでパラメーター化された**選択**ドライバーで、ハードコーディングまたはストアド プロシージャは、データ ソース内にあるステートメントです。 結果セットからデータを取得する方法については、次を参照してください。[が、結果セットを作成しますか?](../../../odbc/reference/develop-app/was-a-result-set-created.md)です。  
  
 各カタログ関数の結果セットには、その関数の参照エントリが記載されています。 一覧の列だけでなく、結果セットは、最後の定義済みの列の後にドライバー固有の列を含めることができます。 これらの列 (存在する場合) は、ドライバーのドキュメントに記述されます。  
  
 アプリケーションでは、結果セットの末尾からの相対ドライバー固有の列をバインドする必要があります。 最後の列の数としてドライバー固有の列の数を計算する必要があります、— を使用して取得**SQLNumResultCols** : 必要な列の後に発生した列の数を引いた値。 これにより新しい列が結果に追加されたときに、アプリケーションを変更することは、ODBC のバージョンまたはドライバー将来的に設定します。 この方式が機能するには、結果セットの末尾からの相対列の数値が変わらないように、ドライバーは古いドライバー固有の列の前に、ドライバー固有の新しい列を追加する必要があります。  
  
 特殊文字が含まれている場合でも、結果セットで返される識別子に引用符がないです。 たとえば、識別子を引用符文字とします (これは特定のドライバーとを通じて返される**SQLGetInfo**) 二重引用符 (") は、および Accounts Payable の表に、顧客名をという名前の列が含まれています。 によって返される行で**SQLColumns**この列の TABLE_NAME 列の値が Accounts Payable 日、いません"Accounts Payable"、および COLUMN_NAME 列の値は、顧客名、「顧客名ではなく」です。 Accounts Payable のテーブル内の顧客の名前を取得するには、アプリケーションは、これらの名前を引用符は。  
  
```  
SELECT "Customer Name" FROM "Accounts Payable"  
```  
  
 詳細については、次を参照してください。[引用符で囲まれた識別子](../../../odbc/reference/develop-app/quoted-identifiers.md)です。  
  
 カタログ関数は、ユーザー名とパスワードに基づいての接続が確立され、ユーザーが特権を持ってデータのみが返されます SQL に似た承認モデルに基づきます。 このモデルに適合しません、個々 のファイルのパスワード保護では、ドライバー定義されます。  
  
 カタログ関数によって返される結果セットは更新可能なほとんどありませんし、これらの結果セット内のデータを変更することによって、データベースの構造を変更することができるアプリケーションを期待できません。
