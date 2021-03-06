---
title: "データ変換の変換を使用してデータ型を変換する | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- converting data types [Integration Services]
- Data Conversion transformation
- data types [Integration Services], converting
ms.assetid: 4aabbe4f-7666-4672-865a-9627bd25fbfd
caps.latest.revision: "41"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: fcae6a724feb11400c8b6c3d4e149bc6b87504c9
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="convert-data-type-by-using-data-conversion-transformation"></a>データ変換の変換を使用してデータ型を変換する
  データ変換の変換を追加して構成するには、パッケージに 1 つ以上のデータ フロー タスクと 1 つの変換元があらかじめ含まれている必要があります。  
  
### <a name="to-convert-data-to-a-different-data-type"></a>データを別のデータ型に変換するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。  
  
3.  **[データ フロー]** タブをクリックし、次に **[ツールボックス]**で、データ変換の変換をデザイン画面にドラッグします。  
  
4.  データ変換の変換をデータ フローに連結します。連結するには、変換元または前の変換からデータ変換の変換にコネクタをドラッグします。  
  
5.  データ変換の変換をダブルクリックします。  
  
6.  **[データ変換変換エディター]** ダイアログ ボックスの **[使用できる入力列]** テーブルで、データ型を変換する列の隣にあるチェック ボックスをオンにします。  
  
    > [!NOTE]  
    >  1 つの入力列に複数のデータ変換を適用できます。  
  
7.  必要に応じ、 **[出力の別名]** 列の既定値を変更します。  
  
8.  **[データ型]** 一覧で、列の新しいデータ型を選択します。 既定のデータ型は、入力列のデータ型です。  
  
9. 選択したデータ型によっては、必要に応じて **[長さ]**、 **[有効桁数]**、 **[小数点以下桁数]**、および **[コード ページ]** 列の値を更新します。  
  
10. エラー出力を構成するには、 **[エラー出力の構成]**をクリックします。 詳細については、「 [データ フローのデバッグ](../../../integration-services/troubleshooting/debugging-data-flow.md)」を参照してください。  
  
11. **[OK]**をクリックします。  
  
12. 更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [Data Conversion Transformation](../../../integration-services/data-flow/transformations/data-conversion-transformation.md)   
 [Integration Services の変換](../../../integration-services/data-flow/transformations/integration-services-transformations.md)   
 [Integration Services のパス](../../../integration-services/data-flow/integration-services-paths.md)   
 [Integration Services のデータ型](../../../integration-services/data-flow/integration-services-data-types.md)   
 [データ フロー タスク](../../../integration-services/control-flow/data-flow-task.md)  
  
  
