---
title: "セキュリティで保護された開発 (Reporting Services) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: extensions
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- development security [Reporting Services]
- security [Reporting Services], development
- security [Reporting Services], strategies
ms.assetid: 12161a6c-b93b-4312-9d27-0c922561eb9b
caps.latest.revision: "15"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 5a82e0223882d98db52cd9837ea8f9cb1ae832de
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="secure-development-reporting-services"></a>セキュリティで保護された開発 (Reporting Services)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] は、厳しく制約され、管理者が定義したセキュリティ コンテキストでコードを実行できる堅固なセキュリティ システムを備えています。 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] は、コード アクセス セキュリティまたは証拠ベース セキュリティとも呼ばれる [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] のセキュリティ システムを使用します。 コード アクセス セキュリティの管理下では、リソースにアクセスする場合にユーザーが信頼されます。ただし、ユーザーが実行するコードが信頼されていない場合は、リソースへのアクセスが拒否されます。  
  
 コードに基づいたセキュリティは、特定のユーザーに基づいたものとは異なり、カスタム アセンブリまたは [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 向けに開発するデータ、配信、表示、セキュリティの各拡張機能に対する権限の表現を許可します。 拡張機能のコードは多数の [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ユーザーによって実行される可能性があり、どのようなユーザーが実行するかは開発時にはわかりません。 開発するカスタム アセンブリや拡張機能には、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] の特定のセキュリティ ポリシーが必要です。 これらのセキュリティ ポリシーは、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] の種類として表されます。 コード アクセス セキュリティの詳細については、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] ドキュメントの「コード アクセス セキュリティ」をご覧ください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Reporting Services のコード アクセス セキュリティ](../../../reporting-services/extensions/secure-development/code-access-security-in-reporting-services.md)  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のカスタム アセンブリおよび拡張機能で使用するコード アクセス セキュリティとポリシー構成について説明します。  
  
 [セキュリティ ポリシーの概要](../../../reporting-services/extensions/secure-development/understanding-security-policies.md)  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] の各種アセンブリとコード アクセス セキュリティがコード権限に及ぼす影響について説明します。  
  
 [Reporting Services セキュリティ ポリシー ファイルの使用](../../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md)  
 各種 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] コンポーネントおよび対応するポリシー構成ファイルについて説明します。  
  
  
