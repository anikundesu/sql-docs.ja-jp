---
title: "Power Pivot for SharePoint 用 PowerShell リファレンス |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/16/2015
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c01735a8-f919-48ad-8d74-35d75a18f821
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: dcfee1ec7fa7ad9933ec81fc6d0a1c8f5187e99a
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="powershell-reference-for-power-pivot-for-sharepoint"></a>Power Pivot for SharePoint 用 PowerShell リファレンス
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]このセクションでは、構成または管理するために使用する PowerShell コマンドレットを一覧表示、[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]インストールします。 コマンドレットの有効化と組み込まれているヘルプの表示については、「 [Windows PowerShell を使用した Power Pivot の構成](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell.md)」を参照してください。  

>[!NOTE] 
>この記事には、古くなった情報と例があります。 最新バージョンには、Get-help コマンドレットを使用します。
  
## <a name="cmdlet-list"></a>コマンドレットの一覧  
 PowerShell プロンプトからコマンドレットの一覧を表示するには:  
  
1.  **[管理者として実行]** オプションを使用して SharePoint 管理シェルを開きます。  
  
2.  次のコマンドを入力します。 `Get-help *powerpivot*`  
  
|コマンドレット|Supported Versions|  
|------------|------------------------|  
|[Get-PowerPivotServiceApplication コマンドレット](../../analysis-services/powershell/get-powerpivotserviceapplication-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Get-PowerPivotSystemService コマンドレット](../../analysis-services/powershell/get-powerpivotsystemservice-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Get-PowerPivotSystemServiceInstance コマンドレット](../../analysis-services/powershell/get-powerpivotsystemserviceinstance-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[New-PowerPivotServiceApplication コマンドレット](../../analysis-services/powershell/new-powerpivotserviceapplication-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[New-PowerPivotSystemServiceInstance コマンドレット](../../analysis-services/powershell/new-powerpivotsystemserviceinstance-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Remove-PowerPivotServiceApplication コマンドレット](../../analysis-services/powershell/remove-powerpivotserviceapplication-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Remove-PowerPivotSystemServiceInstance コマンドレット](../../analysis-services/powershell/remove-powerpivotsystemserviceinstance-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Set-PowerPivotServiceApplication コマンドレット](../../analysis-services/powershell/set-powerpivotserviceapplication-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Set-PowerPivotSystemService コマンドレット](../../analysis-services/powershell/set-powerpivotsystemservice-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Update-PowerPivotSystemService コマンドレット](../../analysis-services/powershell/update-powerpivotsystemservice-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
  
 注: 次のコマンドレットは SharePoint 2010 でのみ機能し、 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] ではサポートされません。  
  
-   Get-PowerPivotEngineService  
  
-   Get-PowerPivotEngineServiceInstance  
  
-   New-PowerPivotEngineServiceInstance  
  
-   Remove-PowerPivotEngineServiceInstance  
  
-   Set-PowerPivotEngineService  
  
-   Set-PowerPivotEngineServiceInstance  
  
-   Update-PowerPivotEngineService  
  
  
