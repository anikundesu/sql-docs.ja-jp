---
title: "パーティションの書き戻しの設定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- write-enabled partitions [Analysis Services]
- partitions [Analysis Services], writeback
- partitions [Analysis Services], write-enabled
- writeback [Analysis Services], partitions
ms.assetid: 38bb09cc-2652-4971-8373-0cf468cdc7a6
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d2e7e571a9fd2b807375046653953098d722556d
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="set-partition-writeback"></a>パーティションの書き戻しの設定
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]場合は書き込みを有効にする、メジャー グループ、エンドユーザーは、キューブ データやソース データではなく、書き戻しテーブルという別個のテーブルで変更を保存する場所を参照しながらキューブ データを変更できます。 書き込み許可パーティションを参照しているエンド ユーザーは、そのパーティションの書き戻しテーブルを見れば、すべての変更の最終結果を確認できます。  
  
 書き戻しデータは、参照または削除できます。 また、書き戻しデータをパーティションに変換することもできます。 書き込み許可パーティションの場合、キューブ ロールを使用して、ユーザーまたはユーザー グループに読み取り/書き込みアクセス権を許可し、パーティション内の特定のセルまたはセル グループへのアクセスを制限できます。  
  
 書き戻しに関する簡単な紹介ビデオについては、「 [Excel 2010 での Analysis Services への書き戻し](http://go.microsoft.com/fwlink/p/?LinkId=394951)」を参照してください。 書き戻し機能の詳細については、ブログ投稿「 [Analysis Services を使用した書き戻しアプリケーションの構築 (ブログ)](http://go.microsoft.com/fwlink/?LinkId=394977)」を参照してください。  
  
> [!NOTE]  
>  書き戻しは、SQL Server リレーショナル データベースとデータ マート、および [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 多次元モデルでのみサポートされます。  
  
## <a name="how-to-write-enable-a-partition"></a>パーティションを書き込み許可にする方法  
 パーティションのメジャー グループを書き込み許可にするには、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] や [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のキューブ デザイナーでパーティション自体に書き込み許可を設定します。  
  
-   キューブ デザイナーの [パーティション] タブで、パーティションを右クリックし、 **[書き戻しの設定]**をクリックします。  
  
-   [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]で、データベース | キューブ | メジャー グループを展開し、 **[書き戻し]** を右クリックして、 **[書き戻しの有効化]**をクリックします。  
  
 書き戻しは、SUM 集計を使用するメジャーに対してのみサポートされます。 AdventureWorks サンプル データベースでは、Sales Targets メジャー グループを使用して、書き戻しの動作をテストできます。  
  
 パーティションを書き込み許可する場合は、書き戻しテーブルを保存するためのテーブル名とデータ ソースを指定します。 その後のメジャー グループの変更は、このテーブルに記録されます。  
  
## <a name="browse-writeback-data-in-a-partition"></a>パーティションの書き戻しデータの参照  
 **[データの参照]** ダイアログ ボックスでは、キューブの書き戻しテーブルの内容を参照できます。このダイアログ ボックスにアクセスするには、キューブ デザイナーの **[パーティション]** タブで、書き込み許可パーティションを右クリックします。  
  
## <a name="delete-writeback-data-or-disable-writeback"></a>書き戻しデータの削除と書き戻しの無効化  
 書き戻しデータを削除すると、ライトバック キャッシュが消去されます。つまり、データが削除されるとすぐに、追加の書き戻し作業が白紙の状態から実行されます。 キューブ パーティションの書き戻しを無効にすると、そのパーティションの書き戻しがオフになります。  
  
## <a name="convert-writeback-data-to-a-partition"></a>書き戻しデータからパーティションへの変換  
 パーティションの書き戻しテーブルに含まれるデータは、パーティションに変換できます。 この手順により、書き戻しテーブルは新しいパーティションのファクト テーブルになります。  
  
> [!CAUTION]  
>  パーティションの使い方が不適切な場合、キューブ データが不正確になることがあります。 詳細については、「[ローカル パーティションの作成と管理 (Analysis Services)](../../analysis-services/multidimensional-models/create-and-manage-a-local-partition-analysis-services.md)」を参照してください。  
  
 書き戻しデータ テーブルをパーティションに変換すると、パーティションの書き込みも無効になります。 パーティションのセルの無制限読み取り/書き込みポリシーと読み取り/書き込み (Read/Write) 権限はすべて無効になり、エンド ユーザーは表示されるキューブ データを変更できなくなります。 無制限読み取り/書き込みポリシーまたは読み取り/書き込み権限が無効であるエンド ユーザーでもキューブを参照できます。読み取り (Read) 権限と条件付き読み取り (Read-Contingent) 権限は影響を受けません。  
  
 書き戻しデータをパーティションに変換するには、**[パーティションに変換]** ダイアログ ボックスを使用します。このダイアログ ボックスにアクセスするには、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で書き込み可能なパーティションの書き戻しテーブルを右クリックします。 ここで、パーティションの名前と、パーティションの集計のデザインを作成後に行うか同時に行うかを指定します。 パーティションの選択と同時に集計を作成するには、既存のパーティションから集計のデザインをコピーするように選択する必要があります。 これは、必ずというわけではありませんが、通常は現在の書き戻しパーティションです。 また、パーティションの作成と同時に処理するように選択することもできます。  
  
## <a name="see-also"></a>参照  
 [書き込み許可パーティション](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-write-enabled-partitions.md)   
 [Excel 2010 のセル レベルの OLAP キューブへの書き戻しを有効にします。](http://go.microsoft.com/fwlink/p/?LinkId=394952)   
 [有効にして、Analysis Services の書き戻しデータ エントリのセキュリティ保護](http://go.microsoft.com/fwlink/p/?LinkId=394953)  
  
  
