---
title: "プロジェクトの設定 (読み込みシステム オブジェクト) (DB2ToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-db2
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 9a545233-1b0a-488a-a1ec-c33aa608dcc1
caps.latest.revision: "4"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8769159a97f41c7127ccd65d4ee193a9c11ef40c
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="project-settingsloading-system-objects-db2tosql"></a>プロジェクトの設定 (読み込みシステム オブジェクト) (DB2ToSQL)
[システム オブジェクトの読み込み] ページ、**プロジェクト設定** ダイアログ ボックスでは、SSMA に変換し、読み込みます DB2 システム オブジェクトを指定できます。[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
システム オブジェクトの読み込み ウィンドウで使用できる、**プロジェクト設定**と**プロジェクト設定の既定の** ダイアログ ボックス。  
  
-   すべての SSMA プロジェクトの設定を指定する、**ツール**メニューの **プロジェクト設定の既定の**、設定は表示または変更に必要な移行プロジェクトの種類を選択**移行対象のバージョン**をクリックしてドロップダウン**全般**クリックして、左側のウィンドウの下部にある**システム オブジェクトの読み込み**です。  
  
-   現在のプロジェクトの設定を指定する、**ツール**メニューの [**プロジェクト設定**、] をクリックして**全般**クリックして、左側のウィンドウの下部にある**システム オブジェクトの読み込み**です。  
  
## <a name="default-settings"></a>既定の設定  
システム オブジェクトを変換するシステム リソースを消費し、時間がかかります。 パフォーマンスを向上させるのには、SSMA は、次の一覧に示すように最もよく使用されるシステム オブジェクトのみを選択します。  
  
-   SYS です。DBMS_OUTPUT  
  
-   SYS です。DBMS_PIPE  
  
-   SYS です。DBMS_UTILITY  
  
-   SYS です。標準  
  
-   SYS です。UTL_FILE  
  
-   SYS です。DBMS_LOB  
  
-   SYS です。DBMS_SQL  
  
-   SYS です。DBMS_SESSION  
  
場合は、DB2 オブジェクトは、その他のシステム オブジェクトを参照して、それらのオブジェクトを選択します。 DB2 データベース オブジェクトによって参照されているシステム オブジェクトを選択しない場合は、SSMA で変換エラーを報告します。 システム オブジェクトの不足によって発生する変換エラーが発生した場合は、このダイアログ ボックスで、不足しているオブジェクトを選択します。 必要に応じて変換を行うことができます。  
  
