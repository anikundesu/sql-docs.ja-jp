---
title: "SSIS ツールボックス | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.toolboxfavorites.F1
- sql13.dts.designer.toolbox.F1
- sql13.dts.designer.toolboxcommon.F1
ms.assetid: 552ff592-eeef-46e8-b4a2-9b2384c869aa
caps.latest.revision: "16"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: dfbca740ee6d88dd9baafa286903254ffdd0ec5d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="ssis-toolbox"></a>SSIS ツールボックス
  **SSIS ツールボックス**には、ローカル コンピューターにインストールされているすべてのコンポーネントが表示されます。 他のコンポーネントをインストールするときは、ツールボックスの内側を右クリックし、 **[ツールボックスの更新]** をクリックして、コンポーネントを追加します。  
 
 新しい SSIS プロジェクトを作成するか、既存のプロジェクトを開くと、**SSIS ツールボックス**が自動的に表示されます。 ツールボックスは、パッケージ デザイン画面の右上端にあるツールボックス ボタンをクリックするか、[ビュー] -> [その他のウィンドウ] -> [SSIS ツールボックス] をクリックして開くこともできます。
 
 > [!NOTE]
> ツールボックスが表示されない場合は、[ビュー] -> [その他のウィンドウ] -> [SSIS ツールボックス] の順に選択します。
 
ツールボックス内のコンポーネントについての詳細情報を得るには、そのコンポーネントをクリックすると、ツールボックスの下部に説明が表示されます。 一部のコンポーネントでは、コンポーネントを構成および使用する方法を示すサンプルにアクセスすることもできます。 サンプルは、 [MSDN](http://go.microsoft.com/fwlink/?LinkId=259189)から利用できます。 **SSIS ツールボックス**からサンプルにアクセスするには、説明の下に表示される **[サンプルの検索]** リンクをクリックします。  
  
> [!NOTE]
> ツールボックスからインストールされているコンポーネントを*削除*することはできません。  

## <a name="toolbox-categories"></a>ツールボックス カテゴリ
 **SSIS ツールボックス**では、制御フローとデータ フローのコンポーネントがカテゴリ別にまとめられています。  カテゴリを展開したり折りたたんだり、コンポーネントを再配置することができます。  ツールボックスの内側を右クリックして **[既定のツールボックスの復元]**をクリックして、既定の編成に戻します。  
  
 **[制御フロー]** タブ、 **[データ フロー]** タブ、および **[イベント ハンドラー]**タブを選択すると、 **[お気に入り]**カテゴリおよび **[共通]** カテゴリがツールボックスに表示されます。 **[制御フロー]** タブまたは **[イベント ハンドラー]** タブを選択すると、 **[その他のタスク]** カテゴリがツールボックスに表示されます。**[データ フロー]**タブを選択すると、 **[その他の変換]**、 **[その他の変換元]** 、 **[その他の変換先]** の各カテゴリがツールボックスに表示されます。  

 ## <a name="add-azure-components-to-the-toolbox"></a>Azure のコンポーネントをツールボックスに追加する  
 Integration Services 用の Azure Feature Pack には、Azure データソースとタスクに接続して、Azure の一般的な操作を実行するための接続マネージャーが含まれています。 これらのアイテムをツールボックスに追加するには機能パックをインストールします。 詳細については、「[Azure Feature Pack for Integration Services &#40;SSIS&#41; (Integration Services 用の Azure Feature Pack &#40;SSIS&#41;)](../integration-services/azure-feature-pack-for-integration-services-ssis.md)」を参照してください。  

## <a name="move-a-toolbox-item-to-another-category"></a>ツールボックス アイテムを別のカテゴリに移動する  
  
1.  SSIS ツールボックスのアイテムを右クリックして、次のいずれかをクリックします。  
  
    -   **お気に入りに移動**  
  
    -   **共通に移動**  
  
    -   **その他の変換元に移動**  
  
    -   **その他の変換先に移動**  
  
    -   **その他の変換に移動**  
  
    -   **その他のタスクに移動**  
  
## <a name="refresh-the-ssis-toolbox"></a>SSIS ツールボックスを更新する  
  
1.  SSIS ツールボックスを右クリックして、 **[ツールボックスの更新]**をクリックします。  

