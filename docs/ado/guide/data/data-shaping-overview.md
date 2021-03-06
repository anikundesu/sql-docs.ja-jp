---
title: "データ シェイプの概要 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: data shaping [ADO], overview
ms.assetid: 4cb5fd29-4e56-46ac-ae48-a6771c321c0c
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9720e3312332fe0c4a00bac01cbaa82908125dfb
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="data-shaping-overview"></a>データ シェイプの概要
*データ シェイプ*クエリ内の 2 つ以上の論理エンティティ間の階層関係を構築することを意味します。 階層が 1 つのレコード間の親子関係でわかるように[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)、および別の 1 つまたは複数のレコード (章とも呼ばれます)**レコード セット**です。 親子関係で、親**Recordset**子を含む**レコード セット**です。 このような階層リレーションシップの例は、顧客と注文です。 データベース内のすべての顧客の 0 個以上の注文があります。 階層リレーションシップには、再帰的孫レコードが子レコード内に入れ子にすることがあります。 原則として、階層レコードを任意の深さに入れ子にできます。 実際には、ADO は 512 の最大再帰を制限**Recordset**s。  
  
 形状の [全般]、列に**レコード セット**Microsoft® SQL Server などの別の参照データ プロバイダーからデータを含めることができます**Recordset**値は、の単一行の計算から派生**レコード セット**、全体の列に対して操作から派生した値または**Recordset**です。 列もでき、新しく作成された空です。  
  
 別の参照を含む列の値を取得する場合**レコード セット**、ADO に自動的に返す実際**レコード セット**参照によって表されます。 参照を**Recordset**と呼ばれる、子のサブセットへの参照を実際には、*章*です。 1 つの親は 1 つ以上の子を参照できる**Recordset**です。  
  
 データ シェイプに ADO サポートでは、データ ソースのクエリを返すことができます、 **Recordset** (親) レコードが (子) を表す**レコード セット**です。 顧客と注文のシナリオでは、整形を行う単一のクエリでは、各顧客の注文と顧客の情報を取得するデータを使用できます。 結果**レコード セット**の整形とも呼ばれる**Recordset**です。  
  
 さらに、データの整形を ado を使用すると、新規作成**Recordset**オブジェクトを使用して、基になるデータ ソースを使用せず、**新規**親と子のフィールドについて説明するキーワード**レコード セット**です。 新しい**Recordset**オブジェクトでデータを設定し、永続的に保存します。 開発者には、さまざまな計算や集計もを実行できます (たとえば、**合計**、 **AVG**、および**MAX**) 子フィールドにします。 データ シェイプ作成することも、親**Recordset**子から**レコード セット**子のレコードをグループ化して、親、子グループごとに 1 つの行を配置することです。  
  
 正規 SQL を使用してデータを取得することができます**参加**構文が、このでき、非効率的な扱いにくく、指定された親子リレーションシップの返された各レコードの冗長な親データで繰り返されるためです。 親内の 1 つの親レコードを関連付けることができるデータの整形**レコード セット**子の複数の子レコードを**レコード セット**の冗長性を回避する、**参加**です。 ほとんどのユーザーにとっては、親-子複数**Recordset**プログラミング モデルより自然で 1 つ以上の操作が容易に**レコード セットに参加**モデル。
