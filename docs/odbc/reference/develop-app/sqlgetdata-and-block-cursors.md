---
title: "SQLGetData とブロック カーソル |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cursors [ODBC], block
- SQLGetData function [ODBC], block cursors
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 12599cdc-7725-4faf-bcae-e163ea0f5851
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 53164213af044fc23cee6fa6e83ac5a934e7067a
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sqlgetdata-and-block-cursors"></a>SQLGetData とブロック カーソル
**SQLGetData**単一行の 1 つの列に対して演算を行い、複数の行からデータを格納する配列をフェッチできません。 これは、プライマリの使用のため**SQLGetData**パーツ で、長い形式のデータをフェッチするにはこれを行う複数の行を一度にほとんどまたはまったくない理由があるとします。  
  
 使用する**SQLGetData**アプリケーションの最初の呼び出し、ブロック カーソルと**SQLSetPos**に 1 つの行にカーソルを移動します。 呼び出して**SQLGetData**内の該当する行の列にします。 ただし、この動作はオプションです。 ドライバーがの使用をサポートしているかを判断する**SQLGetData**ブロック カーソルとアプリケーションが呼び出す**SQLGetInfo** SQL_GETDATA_EXTENSIONS オプションを使用します。
