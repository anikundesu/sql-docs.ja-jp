---
title: "[パッケージのプロパティ] ダイアログ ボックス | Microsoft Docs"
ms.custom: 
ms.date: 08/26/2016
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: service
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ssis.ssms.ispackageprop.general.f1
- sql13.ssis.ssms.packageproperties.f1
ms.assetid: a70acbf4-5f5c-4606-8ce4-8eb3684233de
caps.latest.revision: "27"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e706ebef82469e3c7bb2950fda64e461247f4f26
ms.sourcegitcommit: 6bbecec786b0900db86203a04afef490c8d7bfab
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2017
---
# <a name="package-properties-dialog-box"></a>[パッケージのプロパティ] ダイアログ ボックス
  **[パッケージのプロパティ]** ダイアログ ボックスでは、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに格納されているパッケージのプロパティを表示できます。  
  
 詳細については、「[Integration Services &#40;SSIS&#41; Packages](../integration-services-ssis-packages.md)」(Integration Services &#40;SSIS&#41; のパッケージ) を参照してください。  
  
 **目的に合ったトピックをクリックしてください**  
  
-   [[パッケージのプロパティ] ダイアログ ボックスを開く](#open_dialog)  
  
-   [オプションの構成](#options)  
  
##  <a name="open_dialog"></a> [パッケージのプロパティ] ダイアログ ボックスを開く  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]から [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに接続します。  
  
     SSISDB データベースをホストする [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続されます。  
  
2.  オブジェクト エクスプローラーで、ツリーを展開して、 **[Integration Services カタログ]** ノードを表示します。  
  
3.  **[SSISDB]** ノードを展開します。  
  
4.  プロパティを表示するパッケージが格納されているフォルダーを展開します。  
  
5.  パッケージを右クリックし、 **[プロパティ]**をクリックします。  
  
##  <a name="options"></a> オプションの構成  
 **[全般]** ページでは、選択されているパッケージのプロパティを表示できます。  
  
 **[全般]** ページに表示されるすべてのプロパティは読み取り専用です。  
  
 **名前**  
 パッケージの名前が表示されます。  
  
 **[Identifier]**  
 パッケージ ID を一覧表示します。  
  
 **エントリ ポイント**  
 値 **True** は、パッケージが直接起動されることを示します。 値 **False** は、パッケージ実行タスクを使用して、パッケージが別のパッケージによって起動されることを示します。 既定値は **True**です。  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で親パッケージと子パッケージの両方に対してこのプロパティを設定するには、ソリューション エクスプローラーでパッケージを右クリックし、 **[エントリ ポイント パッケージ]**をクリックします。  
  
 **Description**  
 省略可能なパッケージの説明が表示されます。  
  
  
