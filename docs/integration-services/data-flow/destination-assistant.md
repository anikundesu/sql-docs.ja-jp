---
title: "変換先アシスタント | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.destinationassistant.f1
- sql13.DTS.DESIGNER.DESTINATIONASSIST.F1
ms.assetid: 10a40921-a2c2-4ac8-be28-311f8500fbf6
caps.latest.revision: "13"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 21ce9dc332f5a31fa95ea57e5cbe63a2757f198a
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="destination-assistant"></a>デスティネーション アシスタント
  変換先アシスタント コンポーネントを使用すると、変換先コンポーネントおよび接続マネージャーを作成できます。 このコンポーネントは、SSIS ツールボックスの **[お気に入り]** セクションにあります。  
  
> [!NOTE]  
>  変換先アシスタントは、Integration Services 接続プロジェクトと対応するウィザードに置き換わるものです。  

## <a name="add-a-destination-with-destination-assistant"></a>変換先アシスタントを使用して変換先を追加する
このトピックでは、変換先アシスタントを使用して新しい変換先を追加する手順について説明します。また、 **[新しい変換先の追加]** ダイアログで使用できるオプションも示します。このダイアログは、変換先アシスタントを SSIS デザイナーにドラッグ アンド ドロップしたときに表示されます。  

1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、変換先コンポーネントを追加する [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。  
  
2.  **変換先アシスタント** コンポーネントを SSIS ツールボックスから **[データ フロー]** タブにドラッグします。**[新しい変換先の追加]** ダイアログ ボックスが表示されます。 次のセクションでは、ダイアログ ボックスで使用できるオプションについて詳しく説明します。  
  
3.  **[種類]** 一覧で、変換先の種類を選択します。  
  
4.  **[接続マネージャー]** 一覧で既存の接続マネージャーを選択するか、**[\<新規作成>]** を選択して新しい接続マネージャーを作成します。  
  
5.  既存の接続マネージャーを選択した場合は、**[OK]** をクリックして **[新しい変換先の追加]** ダイアログ ボックスを閉じます。 変換先と接続マネージャーがデータ フローに追加されます。  
  
6.  **[\<新規作成>]** をクリックして新しい接続マネージャーを作成する場合は、**[接続マネージャー]** ダイアログ ボックスが表示され、接続のパラメーターを指定できます。 新しい接続マネージャーの作成が完了すると、変換先と接続マネージャーが SSIS デザイナーに表示されます。 
  
## <a name="add-new-destination-dialog-box"></a>[新しい変換先の追加] ダイアログ ボックス
次の表に、**[新しい変換先の追加]** ダイアログ ボックスで使用できるオプションをリストします。  
  
|オプション|Description|  
|------------|-----------------|  
|型|変換先の種類を選択します。|  
|接続マネージャー|既存の接続マネージャーを選択するか、**[\<新規作成>]** をクリックして新しい接続マネージャーを作成します。|  
|インストールされているもののみを表示する|インストールされている変換先のみを表示するかどうかを指定します。|  
|OK|変更を保存し、後続のダイアログ ボックスを開いてその他のオプションを構成する場合にクリックします。|  
