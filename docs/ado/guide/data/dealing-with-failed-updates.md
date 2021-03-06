---
title: "失敗した更新を処理する |Microsoft ドキュメント"
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
helpviewer_keywords: updates [ADO], dealing with failed updates
ms.assetid: 299c37bd-19ff-4261-8571-b9665687e075
caps.latest.revision: "3"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 36abbe53e5217ab9e7bf7d0927bf0f91a375c1e1
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="dealing-with-failed-updates"></a>失敗した更新を処理します。
更新プログラムは、エラーの終了時にエラーを解決する方法、種類と、エラーの重大度、およびアプリケーションのロジックに依存します。 ただし、データベースは他のユーザーと共有される場合、一般的なエラーを行う前に、フィールドを変更他のユーザーです。 この種類のエラーは、競合と呼ばれます。 ADO では、このような状況を検出し、エラーを報告します。  
  
## <a name="remarks"></a>解説  
 更新エラーがある場合は、エラー処理ルーチンにトラップされます。 競合する行のみが表示されるように競合定数とレコード セットをフィルター処理します。 この例では、エラーの解決方法は、単表示、著者の姓と名 (au_fname および au_lname)。  
  
 更新の競合ユーザーに警告するコードは、次のようになります。  
  
```  
objRs.Filter = adFilterConflictingRecords  
objRs.MoveFirst  
Do While Not objRst.EOF  
   Debug.Print "Conflict: Name =  "; objRs!au_fname; " "; objRs!au_lname  
   objRs.MoveNext  
Loop  
```  
  
## <a name="see-also"></a>参照  
 [バッチ モード](../../../ado/guide/data/batch-mode.md)
