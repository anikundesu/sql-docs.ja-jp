---
title: "コマンド プロンプトからの更新プログラムのインストール | Microsoft Docs"
ms.custom: 
ms.date: 09/08/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: install-windows
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc98ba2b-aae9-4d01-aa85-d4c36428cb0b
caps.latest.revision: "18"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.openlocfilehash: c04481fbe3cb71606509483e542747140b565ca8
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="installing-updates-from-the-command-prompt"></a>コマンド プロンプトからの更新プログラムのインストール
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] インストール スクリプトをテストし、必要に応じて変更してください。 
 
## <a name="sample-syntax-for-installation"></a>インストールのサンプル構文 
更新プログラム パッケージの名前はさまざまであり、言語、エディション、およびプロセッサ コンポーネントが含まれる場合があります。 コマンド プロンプトで更新プログラムを適用する際に、<package_name> の部分は実際の更新プログラム パッケージの名前に置き換えてください。 
 
- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の 1 つのインスタンスと、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] や管理ツールなどのすべての共有コンポーネントを更新します。インスタンスを指定するには、InstanceName パラメーターまたは InstanceID パラメーターを使用します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の準備済みインスタンスを更新するには、InstanceID パラメーターを指定する必要があります。

    ```
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /InstanceName=MyInstance
    ```
    または 
    ```
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /InstanceID=\<Instance ID>. 
    ```

- セットアップでは、メインの製品と使用可能な更新プログラムが同時にインストールされるように、最新の製品の更新プログラムとメインの製品のインストールを統合できます。 製品の更新プログラムを含むようにデータベース エンジン インスタンスのインストールを準備することができます。 

    ```
    setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=PrepareImage /UpdateEnabled=True /UpdateEnabled=True /UpdateSource=\<path where the update is downloaded> /INSTANCEID=\<Instance ID> /FEATURES=SQLEngine. 
    ```

- [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] や管理ツールなどの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 共有コンポーネントのみを更新します。 

    ```
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch 
    ```

- コンピューター上のすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスと、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] や管理ツールなどのすべての共有コンポーネントを更新します。 

    ```
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /AllInstances. 
    ```

- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の 1 つのインスタンスと [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] や管理ツールなどのすべての共有コンポーネントから更新プログラムを削除します。 

    ```
    <package_name>.exe /qs /Action=RemovePatch /InstanceName=MyInstance. 
    ```

- [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] や管理ツールなどの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 共有コンポーネントのみから更新プログラムを削除します。 

    ```
    <package_name>.exe /qs /Action=RemovePatch 
    ```

  > [!NOTE] 
  > 更新プログラムのインストーラーによって、共有コンポーネントが常に最上位レベルのインスタンスのバージョンと同じかまたはそれ以上であることが保証されます。 
 
## <a name="supported-parameters"></a>サポートされているパラメーター 
 
> [!IMPORTANT] 
> セキュリティ資格情報は、できるだけ実行時に入力してください。 資格情報をスクリプト ファイルに含める必要がある場合は、不正なアクセスが行われないようにファイルをセキュリティで保護してください。 
 
|スイッチ|説明| 
|------------|-----------------| 
|**/?**|自動インストールのコマンド プロンプト ヘルプを表示します。| 
|**/action=Patch または /action=RemovePatch**|インストール動作 (Patch または RemovePatch) を指定します。| 
|**/allinstances**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更新プログラムを、すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスとすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネント (共有、インスタンス非対応) に適用します。| 
|**/instancename=InstanceName***|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更新プログラムを、InstanceName という名前の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスとすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネント (共有、インスタンス非対応) に適用します。| 
|**/InstanceID=Inst1**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更新プログラムを、Inst1 という [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスとすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネント (共有、インスタンス非対応) に適用します。| 
|**/quiet**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更新プログラムのセットアップを自動モードで実行します。| 
|**/qs**|進行状況 UI ダイアログのみを表示します。| 
|**/UpdateEnabled**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップが製品の更新プログラムを検出し、それらを含める必要があるかどうかを指定します。 有効値は True および False または 1 および 0 です。 既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップには検出された更新プログラムが含まれます。| 
|**/IAcceptSQLServerLicenseTerms**|自動インストールのために /Q パラメーターまたは /QS パラメーターを指定した場合にのみ必須です。| 
 
 *準備済み [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスに更新プログラムを適用するために、このパラメーターを指定することはできません。 代わりに /instanceID パラメーターを指定してください。 
 
## <a name="see-also"></a>参照 
 [SQL Server サービスのインストールの概要](http://msdn.microsoft.com/library/6a9fd19b-2367-4908-b638-363b1e929e1e) 
 
 
