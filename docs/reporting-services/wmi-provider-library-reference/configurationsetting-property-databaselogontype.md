---
title: "DatabaseLogonType プロパティ (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: wmi-provider-library-reference
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
apiname: DatabaseLogonType
apilocation: reportingservices.mof
apitype: MOFDef
helpviewer_keywords: DatabaseLogonType property
ms.assetid: 6b592582-4c35-4029-ab86-982fff47d8d6
caps.latest.revision: "24"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: b4ba1c2cccc149648b123e41bb3f792c8ecb6244
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="configurationsetting-property---databaselogontype"></a>ConfigurationSetting プロパティ - DatabaseLogonType
  レポート サーバーが [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows サービス アカウント、Windows ユーザー アカウント、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインのうちどれを使用してレポート サーバー データベースにアクセスするかを指定します。 読み取り専用です。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Dim DatabaseLogonType As Integer  
```  
  
```csharp  
public int DatabaseLogonType;  
```  
  
## <a name="property-values"></a>プロパティ値  
 ログインの種類を表す **整数** オブジェクト。  
  
## <a name="example-code"></a>コード例  
 [MSReportServer_ConfigurationSetting クラス](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="remarks"></a>解説  
 値は次のとおりです。  
  
-   Windows ログインの場合は 0  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインの場合は 1  
  
-   サービスとしてログインする場合は 2  
  
 0 (Windows) を指定する場合は、 [DatabaseLogonAccount](../../reporting-services/wmi-provider-library-reference/configurationsetting-property-databaselogonaccount.md) プロパティの値を、有効な Windows ユーザー アカウントに設定する必要があります。  
  
 1 (SQL Server) を指定する場合は、 [DatabaseLogonAccount](../../reporting-services/wmi-provider-library-reference/configurationsetting-property-databaselogonaccount.md) の値が有効な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインであることを確認してください。  
  
 2 (Windows サービス) を指定する場合、レポート サーバーは [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] アカウントと Windows サービス アカウントを使用してレポート サーバー データベースにアクセスします。 DatabaseLogonAccount プロパティは無視されます。  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
