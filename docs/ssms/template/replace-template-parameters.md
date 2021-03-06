---
title: "テンプレート パラメーターを置き換える | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-templates
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.templates.replaceparameters.f1
helpviewer_keywords:
- template parameters [Template Explorer]
- templates [Transact-SQL], replacing parameters
- Replace (Query) Template Parameters dialog box
- replacing template parameters
ms.assetid: 1234aa14-3464-4a3e-922a-5cfb8fb23627
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cae991dbfcdfb2b00a3229746455c58b59f39bd5
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="replace-template-parameters"></a>[テンプレート パラメーターの置換]
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] テンプレートには、テンプレートを使用するたびに実装固有の値に置き換えることができるパラメーターが含まれています。 コード エディターでテンプレートを開いた後、パラメーターを実装に関する値に置き換えることができます。  
  
## <a name="before-you-begin"></a>はじめに  
**[テンプレート パラメーターの値の指定]** ダイアログは、3 つの列を含むグリッドです。 **[パラメーター]** 列と **[種類]** 列は読み取り専用であり、変更できません。 **[値]** 列の内容を確認し、既定値を実装に応じた値に変更します。  
  
このダイアログ ボックスを使用するには、スクリプトに山かっこ (`< >`) で囲んだパラメーターを `<`*parameter_name*`,` *data_type*`,` *default_value*`>`の形式で含める必要があります。  
  
## <a name="replace-template-parameters"></a>[テンプレート パラメーターの置換]  
コード エディター ウィンドウでテンプレートを開いた後、次の操作を行います。  
  
1.  **[クエリ]** メニューの **[テンプレート パラメーターの値の指定]**をクリックします。  
  
2.  **[テンプレート パラメーターの値の指定]** ダイアログ ボックスの **[値]** 列には、各パラメーターの推奨値が表示されます。 推奨値をそのまま使用するか、または別の値を入力します。  
  
3.  **[OK]** をクリックして **[テンプレート パラメーターを置き換える]** ダイアログ ボックスを閉じ、クエリ エディターでスクリプトを変更します。  
  
## <a name="see-also"></a>参照  
[Template Explorer](../../ssms/template/template-explorer.md)  
[テンプレートを開く](../../ssms/template/open-a-template.md)  
  
