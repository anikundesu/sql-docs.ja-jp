---
title: "変更をキャプチャするために選択したテーブルに対する変更 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: change-data-capture
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: makChanToTab
ms.assetid: a309f82a-c6ef-464d-a6ef-df555bfb609a
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4d6df6c0e20cb81a1525998da5934637d6ad6c29
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="make-changes-to-the-tables-selected-for-capturing-changes"></a>変更をキャプチャするために選択したテーブルに対する変更
  このダイアログ ボックスでは、選択したテーブルから変更をキャプチャする特定の列を選択できます。 **[セキュリティ ロール]** と **[キャプチャ インスタンス]** の情報を編集することもできます。  
  
 このダイアログ ボックスでは、変更をキャプチャするために選択したテーブルに次の変更を加えることができます。  
  
 **CDC インスタンスに含める列の変更**  
  
 次のいずれかまたは両方の操作を行います。  
  
-   CDC インスタンスに含める追加の列の横のチェック ボックスをオンにします。  
  
-   CDC インスタンスに含めない列の横のチェック ボックスをオフにします。  
  
 **特定の列のデータ型の変更**  
  
 特定の列に別のデータ型を選択することができます。 元のデータ型と互換性のあるデータ型への変更のみが可能です。  
  
 データ型を変更するには、 **[データ型]** 列をクリックし、別のデータ型を選択します。 元のデータ型と互換性のあるデータ型のみを選択できます。  
  
> [!NOTE]  
>  他に選択できるデータ型がない場合は、ドロップダウン リストが表示されません。  
  
 **セキュリティ ロールの変更**  
  
 **"セキュリティ ロール"** フィールドで、セキュリティ ゲーティング ロールの新しい名前を入力するか、既存の名前を編集します。  
  
 **キャプチャ インスタンスの変更または追加**  
  
 **"キャプチャ インスタンス"** フィールドに、キャプチャ インスタンスの名前を入力します。  
  
## <a name="see-also"></a>参照  
 [SQL Server 変更データベース インスタンスを作成する方法](../../integration-services/change-data-capture/how-to-create-the-sql-server-change-database-instance.md)   
 [Oracle のテーブルおよび列の選択](../../integration-services/change-data-capture/select-oracle-tables-and-columns.md)  
  
  
