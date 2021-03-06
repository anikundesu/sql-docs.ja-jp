---
title: "属性の KeyColumn プロパティを変更する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
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
- binding attributes [Analysis Services]
- attributes [Analysis Services], binding
- key columns [Analysis Services]
ms.assetid: a2643be4-8123-4cc3-baf9-e5ec54a1669d
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d661563b794e205b554d3f11bcd2eb495d7d3a08
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="attribute-properties---modify-the-keycolumn-property"></a>属性のプロパティ - KeyColumn プロパティの変更
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]変更することができます、 **KeyColumns**属性のプロパティです。 たとえば、単一キーではなく複合キーをその属性のキーとして指定する場合があります。  
  
### <a name="to-modify-the-keycolumns-property-of-an-attribute"></a>属性の KeyColumns プロパティを変更するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、 **KeyColumns** プロパティを変更するプロジェクトを開きます。  
  
2.  次のいずれかの手順を実行して、ディメンション デザイナーを開きます。  
  
    -   **ソリューション エクスプローラー**では、 **[ディメンション]** フォルダー内のディメンションを右クリックし、 **[開く]** または **[デザイナーの表示]**をクリックします。  
  
         - または -  
  
    -   キューブ デザイナーで、上、 **キューブ構造**  タブで、キューブ ディメンションを展開し、**ディメンション**ペインをクリック**編集\<ディメンション >**です。  
  
3.  **[ディメンション構造]** タブの **[属性]** ペインで、変更する **KeyColumns** プロパティを含む属性をクリックします。  
  
4.  **[プロパティ]** ウィンドウで、 **KeyColumns** プロパティの値をクリックします。  
  
5.  プロパティ ボックスの値のセルに表示される参照ボタン ( **[...]** ) をクリックします。  
  
     **[キー列]** ダイアログ ボックスが表示されます。  
  
6.  既存のキー列を削除するには、**[キー列]** の一覧で列を選択し、**[\<]** をクリックします。  
  
7.  キー列を追加するには、**[使用できる列]** の一覧で列を選択し、**[>]** をクリックします。  
  
    > [!NOTE]  
    >  複数のキー列を定義する場合、**[キー列]** の一覧での列の順序が表示順序に影響します。 たとえば、Month 属性には、月および年という 2 つのキー列があります。 一覧で年の列が月の列よりも前に表示される場合は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] により、まず年順に並べ替えられ、続いて月順に並べ替えられます。 月の列が年の列よりも前に表示される場合は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] により、まず月順に並べ替えられ、続いて年順に並べ替えられます。  
  
8.  キー列の順序を変更するには、列を選択し、 **[上へ]** または **[下へ]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [ディメンションの属性のプロパティの参照](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
