---
title: "ADO.NET でのユーザー定義型へのアクセス |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- ADO.NET [CLR integration]
- UDTs [CLR integration], ADO.NET
- user-defined types [CLR integration], ADO.NET
ms.assetid: 4b0d876c-8066-490e-8e18-327c0e942b19
caps.latest.revision: "12"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 267f7513c3cc7342106b04232c137ffdd1621cf9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="accessing-user-defined-types-in-adonet"></a>ADO.NET でのユーザー定義型へのアクセス
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]サポートされる言語のいずれかを使用してユーザー定義型 (Udt) を記述、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 共通言語ランタイム (CLR) 検証可能なコードを生成します。 サポートされる言語には、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# や [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic などがあります。 UDT では、オブジェクトやカスタム データ構造を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに格納できます。 データは、.NET Framework のクラスまたは構造体のパブリック メンバーとして公開され、動作は .NET Framework のクラスまたは構造体のメソッドによって定義されます。 UDT の変数として、テーブルの列の定義として使用できる、[!INCLUDE[tsql](../../includes/tsql-md.md)]バッチ、またはの引数として、[!INCLUDE[tsql](../../includes/tsql-md.md)]関数またはストアド プロシージャです。  
  
 ADO.NET では、 **System.Data.SqlClient**プロバイダーは、次の方法で Udt が公開します。  
  
-   を介して、 **System.Data.SqlClient.SqlDataReader**オブジェクトとして。  
  
-   を介して、 **SqlDataReader**未処理のバイトとして。  
  
-   パラメーターとして、 **System.Data.SqlClient.SqlParameter**オブジェクト。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [UDT データの取得](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-retrieving-udt-data.md)  
 UDT データを取得する方法とパラメーターを指定する方法について説明します。  
  
 [Dataadapter による UDT 列の更新](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-updating-udt-columns-with-dataadapters.md)  
 Udt を操作する方法について説明します**データセット**UDT を使用してデータを更新する方法と**Dataadapter**です。  
  
## <a name="see-also"></a>参照  
 [CLR ユーザー定義型](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
  
  
