---
title: "接続 (Excel 用 MDS アドイン) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: microsoft-excel-add-in
ms.reviewer: 
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f2b2f9d-7744-460e-83cd-56d34ea70ff0
caps.latest.revision: "12"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 40102bd465cc7b2cfce29b7f1da79723a04b3104
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="connections-mds-add-in-for-excel"></a>接続 (Excel 用 MDS アドイン)
  データを [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]にダウンロードするには、まず接続を作成する必要があります。 接続とは、 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web サービスがどの MDS データベースに接続するかを認識する方法です。  
  
 通常、接続文字列は [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションの URL (`http://contoso/mds` など) です。  
  
 Excel を起動するたびに、MDS リポジトリに接続する必要があります。 ただし、アクティブなワークシートに MDS によって管理されるデータが既に含まれている場合だけは例外です。 この場合は、シート内のデータを更新またはパブリッシュするたびに接続が自動的に確立されます。  
  
 接続は複数作成することができます。 最後にアクセスした接続が既定と見なされます。  
  
 複数のユーザーが同時に接続できます。 ただし、複数のユーザーが同じデータをパブリッシュしようとすると競合が発生する可能性があります。 詳細については、「[概要: Excel からのデータのインポート (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)」を参照してください。  
  
## <a name="connect-automatically-and-load-frequently-used-data"></a>自動接続とよく使用するデータの読み込み  
 常に同じサーバーに接続して同じデータ セットを読み込む場合は、接続およびフィルター情報を含むショートカット クエリ ファイルを作成できます。 クエリ ファイルの詳細については、「 [ショートカット クエリ ファイル (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/shortcut-query-files-mds-add-in-for-excel.md)」を参照してください。  
  
## <a name="data-quality-services"></a>Data Quality Services  
 [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] には、MDS リポジトリにパブリッシュする前にデータを照合するための Data Quality Services 機能が用意されています。 接続時に、DQS データベースが MDS データベースと同じ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにインストールされている場合は、リボンに DQS ボタンが表示されます。 DQS_Main データベースがインスタンスに存在しない場合、DQS ボタンは表示されず、データ品質機能を使用することはできません。  
  
## <a name="related-tasks"></a>関連タスク  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースへの接続を作成します。|[MDS リポジトリへの接続 (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/connect-to-an-mds-repository-mds-add-in-for-excel.md)|  
|MDS データを Excel に読み込みます。|[マスター データ サービスから Excel へのデータのエクスポート](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md)|  
|Excel に読み込む前に MDS データをフィルター処理します。|[エクスポート前のデータのフィルター処理 (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/filter-data-before-exporting-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>関連コンテンツ  
  
-   [概要: Excel へのデータのエクスポート (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
-   [ショートカット クエリ ファイル (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/shortcut-query-files-mds-add-in-for-excel.md)  
  
-   [Microsoft Excel 用マスター データ サービス アドイン](../../master-data-services/microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md)  
  
  
