---
title: "プロセスのデータベース権限を付与 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: 69ba952e-09ae-49a9-9297-00e32e8e89a8
caps.latest.revision: "17"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: bdeda5d56ce61482e1ba46d697fa8e49ce0ebdef
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="lesson-10---granting-process-database-permissions"></a>レッスン 10 - プロセス データベース権限の許可
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]インスタンスをインストールした後[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のすべてのメンバー、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンス内でサーバー管理者ロールのインスタンスで任意のタスクを実行するサーバー全体のアクセス許可がある[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]です。 既定では、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンス内のオブジェクトを管理および表示する権限は他のユーザーに一切与えられません。  
  
サーバー管理者ロールのメンバーは、他のユーザーをロールのメンバーにすることにより、サーバー全体にわたる管理アクセス権をそのユーザーに許可できます。 また、データベース レベルで制限付きの、または完全な管理権限やアクセス権を他のユーザーに付与することで、より狭い範囲の権限をそのユーザーに与えることもできます。 制限付きの管理権限として、データベース レベル、キューブ レベル、またはディメンション レベルでの定義の処理権限や読み取り権限があります。  
  
このトピックの作業では、Process Database Objects というセキュリティ ロールを定義します。このロールのメンバーには、すべてのデータベース オブジェクトを処理する権限が与えられますが、データベース内のデータを表示する権限は与えられません。  
  
## <a name="defining-a-process-database-objects-security-role"></a>Process Database Objects セキュリティ ロールの定義  
  
1.  ソリューション エクスプローラーで **[ロール]** を右クリックし、 **[新しいロール]** をクリックして、ロール デザイナーを開きます。  
  
2.  **[データベースの処理]** チェック ボックスをオンにします。  
  
3.  プロパティ ウィンドウで、この新しいロールの **Name** プロパティを「 **Process Database Objects Role**」に変更します。  
  
    ![ロール デザイナー](../analysis-services/media/l10-security-1.png "ロール デザイナー")  
  
4.  ロール デザイナーの **[メンバーシップ]** タブに切り替えて、 **[追加]**をクリックします。  
  
5.  このロールのメンバーになる Windows ドメイン ユーザーまたはグループのアカウントを入力します。 アカウント情報を確認するために **[名前の確認]** をクリックし、 **[OK]**をクリックします。  
  
6.  ロール デザイナーの **[キューブ]** タブに切り替えます。  
  
    次の図に示すとおり、このロールのメンバーにはこのデータベースを処理する権限が与えられていますが、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブ内のデータへのアクセス権がなく、ローカル キューブ/ドリルスルー アクセスを行うことができません。  
  
    ![ロール デザイナーの [キューブ] タブ](../analysis-services/media/l10-security-2.png "ロール デザイナーの [キューブ] タブ")  
  
7.  ロール デザイナーの **[ディメンション]** タブに切り替えます。  
  
    このロールのメンバーにはこのデータベース内のすべてのディメンション オブジェクトを処理する権限が与えられ、既定では、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial データベース内の各ディメンション オブジェクトにアクセスするための読み取り権限も与えられます。  
  
8.  **[ビルド]** メニューの **[Analysis Services Tutorial の配置]**をクリックします。  
  
    これで、Process Database Objects セキュリティ ロールが正常に定義され、配置されました。 キューブが実稼働環境に配置された後、その配置されたキューブの管理者は、ユーザーをこのロールに追加することにより、処理作業を必要に応じて特定のユーザーに委任することができます。  
  
> [!NOTE]  
> レッスン 10 の操作内容が反映されたプロジェクトを入手するには、サンプルをダウンロードしてインストールしてください。 詳細については、「 [Analysis Services 多次元モデリング チュートリアル用のサンプル データおよびプロジェクトのインストール](../analysis-services/install-sample-data-and-projects.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[ロールと権限 &#40;Analysis Services&#41;](../analysis-services/multidimensional-models/roles-and-permissions-analysis-services.md)  
  
  
  
