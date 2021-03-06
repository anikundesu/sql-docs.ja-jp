---
title: "ディメンションの翻訳 |Microsoft ドキュメント"
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
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- dimensions [Analysis Services], translations
- multiple language support [Analysis Services]
- international considerations [Analysis Services]
- global considerations [Analysis Services]
- LCIDs
- translations [Analysis Services], dimensions
ms.assetid: 38fc1e05-2ac9-4816-b52b-dfd19c3a43a2
caps.latest.revision: "19"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8e9b769f834d371d8b26fd5b1814ab62107b59ec
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="dimension-translations"></a>ディメンションの翻訳
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]翻訳は、1 つの言語から、表示されるラベルとキャプションを変更する単純なメカニズムです。 各翻訳は、値のペアとして定義されます。翻訳済みテキストの文字列と言語 ID の数値とのペアです。 翻訳は、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のすべてのオブジェクトで使用できます。 ディメンションは翻訳された属性値も持つことができます。 クライアント アプリケーションは、ユーザーによって定義された言語設定を検索し、すべてのキャプションとラベルの表示をその言語に切り替えます。 1 つのオブジェクトに対する翻訳の数に制限はありません。  
  
 簡単な <xref:Microsoft.AnalysisServices.Translation> オブジェクトは、言語 ID 番号およびキャプションの翻訳で構成されます。 言語 ID 番号は、**整数**言語 ID に置き換えます。 キャプションの翻訳は、翻訳されたテキストです。  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、ディメンションの翻訳は、ディメンションの名前の名前の言語に固有の表現、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]オブジェクトまたはキャプション、メンバー、または階層のレベルなど、そのメンバーのいずれか。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]もキューブ オブジェクトの翻訳をサポートします。  
  
 翻訳によって、複数言語を使用するクライアント アプリケーションをサーバーがサポートできるようになります。 キューブとキューブのディメンションは、異なる国々のユーザーによって表示されることが頻繁にあります。 キューブやキューブのディメンションのさまざまな要素を異なる言語に翻訳できれば、異なる国々のユーザーがキューブを表示し、理解するのに役立ちます。 たとえば、フランスのビジネス ユーザーは、フランス語ロケールが設定されているワークステーションからキューブにアクセスし、オブジェクト プロパティの値をフランス語で表示できます。 ドイツのビジネス ユーザーがドイツ語ロケールの設定されたワークステーションから同じキューブにアクセスした場合は、オブジェクト プロパティの値をドイツ語で表示できます。  
  
 クライアント コンピューターの照合順序と言語の情報は、ロケール識別子 (LCID) の形式で保存されます。 クライアントは接続時に [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスに LCID を渡します。 このインスタンスでは LCID を使用して、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトのメタデータを表示する際にどの翻訳セットを使用するかが決定されます。 指定された翻訳が [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトにない場合は、既定言語を使用してコンテンツがクライアントに返されます。  
  
## <a name="see-also"></a>参照  
 [キューブの翻訳](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-translations.md)   
 [Analysis Services での翻訳のサポート](../../analysis-services/translation-support-in-analysis-services.md)   
 [グローバリゼーションのヒントとベスト プラクティス (&) #40 です。Analysis Services &#41;](../../analysis-services/globalization-tips-and-best-practices-analysis-services.md)  
  
  
