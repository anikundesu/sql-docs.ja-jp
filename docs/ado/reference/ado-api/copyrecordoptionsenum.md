---
title: "CopyRecordOptionsEnum |Microsoft ドキュメント"
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
f1_keywords: CopyRecordOptionsEnum
helpviewer_keywords: CopyRecordOptionsEnum enumeration [ADO]
ms.assetid: 2fa4eec5-d50b-4fd3-8ae7-40af441ba12b
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 74c11976ea9abec1521b9137012694273440cda7
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="copyrecordoptionsenum"></a>CopyRecordOptionsEnum
動作を指定します、[つまり](../../../ado/reference/ado-api/copyrecord-method-ado.md)メソッドです。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adCopyAllowEmulation**|4|示します、*ソース*ダウンロードを使用して、コピーのシミュレーションや、ためにこのメソッドが失敗した場合、操作をアップロードしようとプロバイダー*先*別のサーバー上にあるものまたは異なるによって処理されます以外のプロバイダー*ソース*です。 プロバイダーの機能のさまざまなパフォーマンスが低下したりデータが失われることに注意してください。|  
|**adCopyNonRecursive**|2|現在のディレクトリが、そのサブディレクトリのいずれもを先にコピーします。 コピー操作は、再帰的ではありません。|  
|**adCopyOverWrite**|@shouldalert|場合に、ファイルまたはディレクトリを上書き、*先*既存のファイルまたはディレクトリをポイントします。|  
|**adCopyUnspecified**|-1|既定値です。 既定のコピー操作を実行します。 変換先ファイルまたはディレクトリが既に存在する場合、操作は失敗し、操作のコピーを再帰的にします。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 これらの定数には、対応する ADO/WFC はありません。  
  
## <a name="applies-to"></a>適用対象  
 [CopyRecord メソッド (ADO)](../../../ado/reference/ado-api/copyrecord-method-ado.md)
