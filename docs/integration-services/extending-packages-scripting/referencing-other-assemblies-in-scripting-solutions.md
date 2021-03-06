---
title: "スクリプティング ソリューションでの他のアセンブリの参照 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-scripting
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
dev_langs: VB
helpviewer_keywords:
- SSIS Script task, .NET Framework
- Script task [Integration Services], adding references
- referencing custom assemblies
- SSIS Script task, VisualBasic namespace
- assemblies [Integration Services]
- VisualBasic namespace
- Script task [Integration Services], VisualBasic namespace
- Microsoft.VisualBasic namespace
- Script task [Integration Services], .NET Framework
- .NET Framework [Integration Services]
- referencing Web services
ms.assetid: 9b655bcd-19f6-43d8-9f89-1b4d299c6380
caps.latest.revision: "68"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1e90784bab93fa79b02add5223bebea08113a70c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="referencing-other-assemblies-in-scripting-solutions"></a>スクリプティング ソリューションでの他のアセンブリの参照
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] クラス ライブラリには、スクリプトの開発者が [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージにカスタム機能を実装するための強力なツール セットが用意されています。 スクリプト タスクとスクリプト コンポーネントでは、カスタム マネージ アセンブリも使用できます。  
  
> [!NOTE]  
>  Web サービスのオブジェクトやメソッドをパッケージで使用できるようにするには、[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) の **[Web 参照の追加]** コマンドを使用します。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の以前のバージョンでは、Web サービスを使用するためにプロキシ クラスを生成する必要がありました。  
  
## <a name="using-a-managed-assembly"></a>マネージ アセンブリの使用  
 デザイン時に [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によってマネージ アセンブリが検出されるようにするには、次の手順を実行する必要があります。  
  
1.  マネージ アセンブリをコンピューター上の任意のフォルダーに格納します。  
  
    > [!NOTE]  
    >  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の以前のバージョンで追加できたのは、%windir%\Microsoft.NET\Framework\vx.x.xxxxx フォルダーか %ProgramFiles%\Microsoft SQL Server\100\SDK\Assemblies フォルダーにあるマネージ アセンブリへの参照のみでした。  
  
2.  マネージ アセンブリへの参照を追加します。  
  
     参照を追加するには、VSTA の **[参照の追加]** ダイアログ ボックスにある **[参照]** タブで、マネージ アセンブリを探して追加します。  
  
 実行時に [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によってマネージ アセンブリが検出されるようにするには、次の手順を実行する必要があります。  
  
1.  マネージ アセンブリに厳密な名前で署名します。  
  
2.  パッケージが実行されるコンピューターのグローバル アセンブリ キャッシュに、そのアセンブリをインストールします。  
  
     詳細については、「[カスタム オブジェクトのビルド、配置、デバッグ](../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md)」を参照してください。  
  
## <a name="using-the-microsoft-net-framework-class-library"></a>Microsoft .NET Framework クラス ライブラリの使用  
 スクリプト タスクおよびスクリプト コンポーネントは、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] クラス ライブラリによって公開されている他のすべてのオブジェクトおよび機能を利用することができます。 たとえば、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] を使用すると、ユーザーの環境に関する情報を取得し、パッケージを実行中のコンピューターとやり取りできます。  
  
 使用頻度の高い [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] クラスを次に示します。  
  
-   **System.Data** ADO.NET アーキテクチャが含まれています。  
  
-   **System.IO** ファイル システムおよびファイル ストリームに対するインターフェイスを提供します。  
  
-   **System.Windows.Forms** フォームを作成できます。  
  
-   **System.Text.RegularExpressions** 正規表現を処理するためのクラスを提供します。  
  
-   **System.Environment** ローカル コンピューター、現在のユーザー、およびコンピューターとユーザーの設定に関する情報を返します。  
  
-   **System.Net** ネットワーク通信を提供します。  
  
-   **System.DirectoryServices** Active Directory を公開します。  
  
-   **System.Drawing** 広範な画像操作ライブラリを提供します。  
  
-   **System.Threading** マルチスレッド プログラミングを有効にします。  
  
 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] の詳細については、MSDN ライブラリを参照してください。  
  
## <a name="see-also"></a>参照  
 [スクリプトによるパッケージの拡張](../../integration-services/extending-packages-scripting/extending-packages-with-scripting.md)  
  
  
