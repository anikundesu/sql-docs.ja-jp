---
title: "ゲージ パネルへのインジケーターとゲージの配置 (レポート ビルダーおよび SSRS) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-design
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4dff9b67-b483-4c51-a822-6dbe706a6840
caps.latest.revision: "8"
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 863d9eb4f059fa46b0f8584af09718cb46dec859
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="include-indicators-and-gauges-in-a-gauge-panel-report-builder-and-ssrs"></a>ゲージ パネルへのインジケーターとゲージの配置 (レポート ビルダーおよび SSRS)
  ゲージ パネルは、1 つ以上のゲージとインジケーターを格納する最上位のコンテナーです。 インジケーターは、ゲージに埋め込んだり、ゲージ パネルのゲージの横に配置したりできます。  
  
 ゲージ パネルでインジケーターとゲージが隣接し、異なるフィールドのデータを表示している場合は、ゲージとインジケーターのデータを区別しやすいようにラベルを追加することをお勧めします。  
  
 ゲージとインジケーターのオプションは、式を使用して設定できます。 詳細については、「[式 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-embed-an-indicator-in-a-gauge"></a>ゲージにインジケーターを埋め込むには  
  
1.  表示するデータのテーブルおよびマトリックスが含まれる既存のレポートを開くか、新しいレポートを作成します。   
  
2.  テーブルまたはマトリックスに列を挿入します。 詳細については、「[列の挿入または削除 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/insert-or-delete-a-column-report-builder-and-ssrs.md)」を参照してください。  
  
3.  **[挿入]** タブの **[データ領域]** グループで **[ゲージ]**をクリックし、次に新しい列のセルをクリックします。 **[ゲージの種類の選択]** ダイアログ ボックスが表示されます。  
  
4.  **[放射状]**をクリックします。 最初の放射状ゲージが選択されます。  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  ゲージをクリックします。 **ゲージ データ** ペインが開きます。  
  
7.  **[値]** 領域の **[(未指定)]** ボックスの一覧で、ゲージに値を表示するフィールドをクリックします。 または、使用するフィールドをレポート データセットからドラッグします。  
  
8.  ゲージを右クリックし、 **[インジケーターの追加]**をクリックして、 **[子]**をクリックします。 **[インジケーター スタイルの選択]** ダイアログ ボックスが表示されます。  
  
9. 左側のペインの **[インジケーター スタイルの選択]** ダイアログ ボックスで、目的のインジケーター タイプをクリックし、インジケーター セットをクリックします。  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
11. インジケーターをクリックします。 **ゲージ データ** ペインが開きます。  
  
12. **[値]** 領域の **[(未指定)]** ボックスの一覧で、インジケーターとして値を表示するフィールドをクリックします。 または、使用するフィールドをレポート データセットからドラッグします。  
  
     このフィールドは、ゲージで使用するフィールドと同じでも別でもかまいません。  
  
13. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-show-an-indicator-and-gauge-side-by-side"></a>インジケーターとゲージを並べて表示するには  
  
1.  表示するデータのテーブルおよびマトリックスが含まれる既存のレポートを開くか、新しいレポートを作成します。  
  
2.  テーブルまたはマトリックスに列を挿入します。 詳細については、「[列の挿入または削除 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/insert-or-delete-a-column-report-builder-and-ssrs.md)」を参照してください。  
  
3.  **[挿入]** タブの **[データ領域]** グループで **[ゲージ]**をクリックし、挿入した列のセルをクリックします。 **[ゲージの種類の選択]** ダイアログ ボックスが表示されます。  
  
4.  **[放射状]**をクリックします。 最初の放射状ゲージが選択されます。  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  ゲージをクリックします。 **ゲージ データ** ペインが開きます。  
  
7.  **[値]** 領域の **[(未指定)]** ボックスの一覧で、ゲージに値を表示するフィールドをクリックします。 または、使用するフィールドをレポート データセットからドラッグします。  
  
8.  ゲージを右クリックし、 **[インジケーターの追加]**をクリックして、 **[隣接]**をクリックします。 **[インジケーター スタイルの選択]** ダイアログ ボックスが表示されます。  
  
9. 左側のペインの **[インジケーター スタイルの選択]** ダイアログ ボックスで、目的のインジケーター タイプをクリックし、インジケーター セットをクリックします。  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
11. インジケーターをクリックします。 **ゲージ データ** ペインが開きます。  
  
12. **[値]** 領域の **[(未指定)]** ボックスの一覧で、インジケーターとして値を表示するフィールドをクリックします。 または、使用するフィールドをレポート データセットからドラッグします。  
  
     このフィールドは、ゲージで使用するフィールドと同じでも別でもかまいません。  
  
13. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
14. ゲージ パネルを右クリックして、 **[ラベルの追加]**をクリックします。 ラベルがゲージ パネルに追加されます。 もう一度繰り返します。  
  
     ゲージ パネルに 2 つのラベルが表示されます。  
  
15. 各ラベルをゲージまたはインジケーターの近くにドラッグします。  
  
16. ゲージの近くのラベルを右クリックし、 **[ラベルのプロパティ]**をクリックして、 **[テキスト]** ボックスにテキストを入力します。  
  
17. インジケーターの近くのラベルを右クリックし、 **[ラベルのプロパティ]**をクリックして、 **[テキスト]** ボックスにテキストを入力します。  
  
18. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>参照  
 [インジケーター &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/indicators-report-builder-and-ssrs.md)  
  
  
