---
title: "変更または Analysis Services データベースの削除 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
- databases [Analysis Services], modifying
- removing databases
- deleting databases
- dropping databases
- databases [Analysis Services], deleting
- modifying databases
ms.assetid: e48e3988-c091-4379-aabc-4da62f709a7e
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 41cb7d7f1c2da7ef2664de3e41c17613019094d6
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="modify-or-delete-an-analysis-services-database"></a>Analysis Services データベースの変更または削除
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]説明と名前を変更することができます、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]で展開する前にデータベース[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で配置後に[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]です。 また、環境に応じて [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの追加の設定を調整することもできます。  
  
> [!NOTE]  
>  オンライン モードで [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] を使用して、データベースのプロパティを変更することはできません。  
  
## <a name="modifying-databases-using-sql-server-management-studio"></a>SQL Server Management Studio を使用したデータベースの変更  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの配置後は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、データベース内のデータ ソースに接続するときに [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で使用される権限借用モードを変更できます。 権限借用モードを使用すると、処理、参照、またはドリルスルーの目的でデータ ソースに接続するときに [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で使用されるセキュリティ コンテキストを指定できます。  
  
## <a name="modifying-databases-using-sql-server-data-tools"></a>SQL Server データ ツールを使用したデータベースの変更  
 プロジェクト モードで [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] を使用すると、データベースの定義に使用する [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトのキャプションや説明の翻訳を変更できます。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースでの翻訳の使用方法については、「 [Analysis Services のグローバリゼーションのシナリオ](../../analysis-services/globalization-scenarios-for-analysis-services.md)」をご覧ください。  
  
 データベースに含まれているディメンションの勘定科目属性で使用される勘定科目の種類に関連付けられている別名や集計関数を設定することもできます。 別名を使用すると、勘定科目一覧表の勘定科目の種類に対して組織が使用するビジネス固有の用語を選択できます。 勘定科目属性のメンバーは、勘定科目の種類を使用して、各メンバーのメジャーを集計する方法を示します。集計は、データベース内の各勘定科目の種類に指定されている集計関数を使用して行います。 勘定科目属性の詳細については、「 [属性と属性階層](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)」をご覧ください。  
  
## <a name="deleting-databases"></a>消去、データベース  
 既存の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを削除すると、データベースとすべてのキューブ、ディメンション、およびデータベース内のマイニング モデルが削除されます。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、既存の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]データベースのみを削除できます。  
  
#### <a name="to-delete-an-analysis-services-database"></a>Analysis Services データベースを削除するには  
  
1.  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスに接続します。  
  
2.  **オブジェクト エクスプローラー**で、接続した [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのノードを展開し、削除するオブジェクトを表示します。  
  
3.  削除するオブジェクトを右クリックし、 **[削除]**をクリックします。  
  
4.  **[オブジェクトの削除]** ダイアログ ボックスで **[OK]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [Analysis Services データベースのドキュメントとスクリプトの作成](../../analysis-services/multidimensional-models/document-and-script-an-analysis-services-database.md)  
  
  
