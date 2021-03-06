---
title: "ディメンション (Analysis Services) に対するアクセス許可を与える |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
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
f1_keywords: sql13.asvs.roledesignerdialog.dimensions.f1
helpviewer_keywords:
- dimensions [Analysis Services], security
- read/write permissions
- user access rights [Analysis Services], dimensions
- permissions [Analysis Services], dimensions
ms.assetid: be5b2746-0336-4b12-827e-131462bdf605
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ccf0f7d014bfd85f3368633058984089005101ec
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="grant-permissions-on-a-dimension-analysis-services"></a>ディメンションに対する権限の付与 (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]ディメンション セキュリティを使用すると、そのデータではなく、ディメンション オブジェクトに対する権限を設定します。 通常、ディメンションに対する権限を設定する場合は、処理操作へのアクセスを許可または拒否することが主な目的です。  
  
 ただし、処理操作ではなく、ディメンションまたはディメンションに含まれる属性および階層へのデータ アクセスを制御することが目的である場合があります。 たとえば、地域の販売部門がある会社で、部門外の人が販売実績情報にアクセスできないようにする場合があります。 異なる構成要素のディメンション データ部分へのアクセスを許可または拒否するには、ディメンション属性およびディメンション メンバーに対する権限を設定します。 ただし、個々のディメンション オブジェクト自体へのアクセスは拒否できず、そのデータへのアクセスのみを拒否できます。 当面の目的が個々の属性階層へのアクセス権などディメンション メンバーへのアクセスを許可または拒否することである場合は、「 [ディメンション データへのカスタム アクセス権の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-custom-access-to-dimension-data-analysis-services.md) 」で詳細を確認してください。  
  
 このトピックでは以後、ディメンション オブジェクト自体に対して設定できる、次のような権限について説明します。  
  
-   読み取りまたは読み取り/書き込み権限 (読み取りまたは読み取り/書き込みのいずれかのみが選択可能であり、「none」を指定することはできません)。 説明したように、目的がディメンション データへのアクセスを制限することである場合は、「 [ディメンション データへのカスタム アクセス権の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-custom-access-to-dimension-data-analysis-services.md) 」で詳細を確認してください。  
  
-   処理権限 (個々のオブジェクトに対するカスタム権限を必要とする処理方法が必要となる場合)。  
  
-   定義の読み取り権限 (通常、ツールで対話型の処理がサポートされるようにするか、またはモデルの可視化を実現するために設定します。 定義の読み取りを使用すると、ディメンションのデータに対する権限がない場合やディメンションの定義を変更できない場合でも、ディメンションの構造を参照できます)。  
  
 ディメンションのロールを定義する場合、使用可能な権限は、オブジェクトがスタンドアロンのデータベース ディメンション (データベースにとっては内部、キューブにとっては外部であるディメンション) であるか、キューブ ディメンションであるかによって異なります。  
  
> [!NOTE]  
>  既定では、データベース ディメンションに対する権限はキューブ ディメンションに継承されます。 たとえば、Customer データベース ディメンションに対する **[読み取り/書き込み]** を有効にすると、Customer キューブ ディメンションは現在のロールのコンテキストで **[読み取り/書き込み]** を継承します。 権限設定を上書きする場合は、継承された権限を消去できます。  
  
## <a name="set-permissions-on-a-database-dimension"></a>データベース ディメンションに対する権限の設定  
 データベース ディメンションはデータベース内のスタンドアロン オブジェクトであり、同じモデル内でディメンションを再利用できます。 あるモデルで Order Date、Ship Date、Due Date の各キューブ ディメンションとして複数回使用される DATE データベース ディメンションがあるとします。 キューブおよびデータベース ディメンションはデータベースのピア オブジェクトであるため、各オブジェクトに個別に処理権限を設定できます。  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに接続し、オブジェクト エクスプローラーで適切なデータベースの **[ロール]** を展開し、データベース ロールをクリックするか、新しいデータベース ロールを作成します。  
  
2.  **[ディメンション]** ペインで、ディメンション セットは **[すべてのデータベース ディメンション]**に設定されているはずです。  
  
     既定では、権限は **[読み取り]**に設定されます。  
  
     **[読み取り/書き込み]** が使用可能ですが、この権限は使用しないことをお勧めします。 **[読み取り/書き込み]** はディメンションの書き戻しシナリオに使用されますが、このシナリオは推奨されなくなりました。 「 [SQL Server 2016 に含まれている非推奨の Analysis Services 機能](../../analysis-services/deprecated-analysis-services-features-in-sql-server-2016.md)」を参照してください。  
  
     必要に応じて、個々のディメンション オブジェクトに対して **[定義の読み取り]** 権限および **[処理]** 権限を設定できますが、それらの権限がまだデータベース レベルで設定されていない場合に限ります。 詳細については、「[処理権限の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-process-permissions-analysis-services.md)」と「[オブジェクト メタデータに対する定義の読み取り権限の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-read-definition-permissions-on-object-metadata-analysis-services.md)」を参照してください。  
  
## <a name="set-permissions-on-a-cube-dimension"></a>キューブ ディメンションに対する権限の設定  
 キューブ ディメンションは、キューブに追加されたデータベース ディメンションです。 したがって、キューブ ディメンションの構造は関連付けられたメジャー グループに依存します。 これらのオブジェクトはアトミックに処理できますが、承認の観点から、キューブおよびキューブ ディメンションは単一のエンティティとして扱うのが適切です。  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに接続し、オブジェクト エクスプローラーで適切なデータベースの **[ロール]** を展開し、データベース ロールをクリックするか、新しいデータベース ロールを作成します。  
  
2.  **ディメンション**ディメンションに設定 ウィンドウで、変更\<キューブ名 >**キューブ ディメンション**です。  
  
     既定では、権限は対応するデータベース ディメンションから継承されます。 **[継承]** チェック ボックスをオフにして、権限を **[読み取り]** から **[読み取り/書き込み]**に変更します。 **[読み取り/書き込み]**を使用する前に、前のセクションの注意事項を必ずお読みください。  
  
> [!IMPORTANT]  
>  分析管理オブジェクト (AMO) を使用してデータベース ロール権限を構成する場合、キューブの DimensionPermission 属性内のキューブ ディメンションを参照することによって、データベースの DimensionPermission 属性からの権限継承は行われなくなります。 詳細については、「[分析管理オブジェクト &#40;AMO&#41; による開発](../../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ロールと権限 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/roles-and-permissions-analysis-services.md)   
 [キューブ権限またはモデル権限の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-cube-or-model-permissions-analysis-services.md)   
 [データ マイニング構造およびモデル &#40; に対する権限を付与します。Analysis Services &#41;](../../analysis-services/multidimensional-models/grant-permissions-on-data-mining-structures-and-models-analysis-services.md)   
 [データ &#40; をディメンションにカスタムのアクセスを許可します。Analysis Services &#41;](../../analysis-services/multidimensional-models/grant-custom-access-to-dimension-data-analysis-services.md)   
 [セル データへのカスタム アクセス権の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-custom-access-to-cell-data-analysis-services.md)  
  
  
