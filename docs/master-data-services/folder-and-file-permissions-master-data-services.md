---
title: "フォルダーとファイルのアクセス許可 (マスター データ サービス) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Master Data Services], file and folder
- folders [Master Data Services]
- files [Master Data Services]
ms.assetid: 6402d81d-7349-47b1-95ca-99b0c0f4f373
caps.latest.revision: "10"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4a8793f71d09da12c30a5e79989f5d87d5b5b8e2
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="folder-and-file-permissions-master-data-services"></a>フォルダーとファイルの権限 (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]のインストール時に、ファイル システムで指定のインストール パスにフォルダーとファイルが [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 共有機能用にインストールされます。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 共有機能に既定のインストール パスを使用する場合、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] のインストール パスは *drive*:\Program Files\Microsoft SQL Server\130\Master Data Services です。 共有機能のインストール パスは変更できますが、親フォルダーから継承される権限と [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]に対して明示的に設定されている権限に注意する必要があります。  
  
## <a name="inherited-permissions"></a>継承された権限  
 **Microsoft SQL Server** フォルダー、 **Master Data Services** フォルダー、および大半のサブフォルダーとファイルは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のセットアップで指定した親フォルダーから権限を継承します。 既定のインストール場所を使用している場合、権限の継承元の親フォルダーは *drive*:\Program Files です。 次の表では、 **Program Files**に対する既定の権限について説明します。  
  
> [!NOTE]  
>  **Program Files**に対する既定の権限を変更するか、または別のインストール場所を選択すると、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] のフォルダーとファイルは対応する親フォルダーから権限を継承します。そのため、次の表で説明する権限と異なる場合があります。  
  
###### <a name="program-files-default-permissions"></a>Program Files の既定の権限  
  
|グループ名またはアカウント名|アクセス許可|  
|---------------------------|-----------------|  
|CREATOR OWNER|特別な権限|  
|SYSTEM|特別な権限|  
|管理者|特別な権限|  
|ユーザー|読み取りと実行、フォルダー内容の一覧表示、読み取り|  
|TrustedInstaller|フォルダー内容の一覧表示、特別な権限|  
  
## <a name="explicit-permissions"></a>明示的権限  
 **MDSTempDir** フォルダーと [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web.config ファイル ( **WebApplication** フォルダーにあります) は、権限を継承しません。 これらには、選択したインストール パスに関係なく、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]をインストールするときに明示的に設定された権限があります。 これらの権限を変更しないでください。  
  
###### <a name="mdstempdir-permissions"></a>MDSTempDir 権限  
  
|グループ名またはアカウント名|アクセス許可|  
|---------------------------|-----------------|  
|SYSTEM|変更、読み取りと実行、フォルダー内容の一覧表示、読み取り、書き込み|  
|管理者|変更、読み取りと実行、フォルダー内容の一覧表示、読み取り、書き込み|  
|MDS_ServiceAccounts|変更、読み取りと実行、フォルダー内容の一覧表示、読み取り、書き込み|  
  
###### <a name="webconfig-permissions"></a>Web.config 権限  
  
|グループ名またはアカウント名|アクセス許可|  
|---------------------------|-----------------|  
|SYSTEM|フル コントロール、変更、読み取りと実行、読み取り、書き込み|  
|管理者|フル コントロール、変更、読み取りと実行、読み取り、書き込み|  
|MDS_ServiceAccounts|読み取りと実行、読み取り|  
  
 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web.config ファイルのコンテンツの詳細については、「[Web 設定リファレンス (マスター データ サービス)](../master-data-services/web-configuration-reference-master-data-services.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [マスター データ サービスのインストール](../master-data-services/install-windows/install-master-data-services.md)  
  
  
