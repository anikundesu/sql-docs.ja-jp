---
title: "作成および管理ロール (SSAS テーブル) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
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
f1_keywords:
- sql13.asvs.bidtoolset.rolemanager.f1
- sql13.asvs.bidtoolset.roledb.f1
ms.assetid: e23d27a8-e968-4082-9dbe-963fc724b5d9
caps.latest.revision: "17"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: cde5ecfbcaa904dc4f0f62e0b135dac5780b8ffd
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="create-and-manage-roles-ssas-tabular"></a>ロールの作成および管理 (SSAS テーブル)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]役割、テーブル モデルでは、モデルのメンバーの権限を定義します。 モデル プロジェクトのロールは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]の [ロール マネージャー] ダイアログ ボックスを使用して定義します。 モデルが配置されると、データベース管理者は [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用してロールを管理することができます。  
  
 このトピックのタスクでは、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で [ロール マネージャー] ダイアログ ボックスを使用して、モデル作成時にロールを作成し管理する方法について説明します。 配置済みモデル データベースでのロールの管理については、「[テーブル モデル ロール &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/tabular-model-roles-ssas-tabular.md)」をご覧ください。  
  
## <a name="tasks"></a>処理手順  
 ロールの作成、編集、コピー、削除の各操作を実行するには、 **[ロール マネージャー]** ダイアログ ボックスを使用します。 **[ロール マネージャー]** ダイアログ ボックスを表示するには、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]の **[モデル]** メニューをクリックし、 **[ロール マネージャー]**をクリックします。  
  
###  <a name="bkmk_new_role"></a> 新しいロールを作成するには  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、 **[モデル]** メニューをクリックし、 **[ロール マネージャー]**をクリックします。  
  
2.  **[ロール マネージャー]** ダイアログ ボックスで **[新規]**をクリックします。  
  
     新しいロールが [ロール] リストに追加され、強調表示されます。  
  
3.  **[ロール]** リストの **[名前]** フィールドに、ロールの名前を入力します。  
  
     既定では、既定ロールの名前に番号が付き、新しいロールを作成するたびにその番号が増加します。 Finance Managers や Human Resources Specialists など、メンバーの種類を明確に特定する名前を付けることをお勧めします。  
  
4.  **[権限]** フィールドで下矢印をクリックしてから、次の権限の種類から 1 つを選択します。  
  
    |権限|Description|  
    |----------------|-----------------|  
    |**なし**|メンバーは、モデル スキーマを変更したり、データをクエリしたりすることはできません。|  
    |**読み取り**|メンバーは、(行フィルターに基づいて) データをクエリできますが、モデル スキーマを変更することはできません。|  
    |**読み取りと処理**|メンバーは、(行レベル フィルターに基づいて) データをクエリでき、処理およびすべて処理の各操作も実行できますが、モデル スキーマを変更することはできません。|  
    |**[処理]**|メンバーは、処理およびすべて処理の各操作を実行できます。 モデル スキーマを変更することはできませんし、データをクエリすることもできません。|  
    |**管理者**|メンバーは、モデル スキーマを変更したり、すべてのデータをクエリしたりできます。|  
  
5.  ロールの説明を入力するには、 **[説明]** フィールドをクリックして説明を入力します。  
  
6.  作成しているロールに読み取りまたは読み取りと処理の権限がある場合、DAX 式を使用して行フィルターを追加できます。 行フィルターを追加するには、 **[行フィルター]** タブをクリックし、テーブルを選択してから、 **[DAX フィルター]** フィールドをクリックし、DAX 式を入力します。  
  
7.  このロールにメンバーを追加するには、 **[メンバー]** タブをクリックし、 **[追加]**をクリックします。  
  
    > [!NOTE]  
    >  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、配置済みモデルにロール メンバーを追加することもできます。 詳しくは、「[SSMS を使用したロールの管理 &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/manage-roles-by-using-ssms-ssas-tabular.md)」をご覧ください。  
  
8.  **[ユーザーまたはグループの選択]** ダイアログ ボックスで、メンバーとして Windows ユーザーまたは Windows グループ オブジェクトを入力します。  
  
9. **[OK]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [ロール &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/roles-ssas-tabular.md)   
 [パースペクティブ (SSAS テーブル)](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [Excel &#40; での分析します。SSAS テーブル &#41;](../../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md)   
 [USERNAME 関数 (DAX)](http://msdn.microsoft.com/en-us/22dddc4b-1648-4c89-8c93-f1151162b93f)   
 [CUSTOMDATA 関数 (DAX)](http://msdn.microsoft.com/en-us/58235ad8-226c-43cc-8a69-5a52ac19dd4e)  
  
  
