---
title: "sp_help_spatial_geography_histogram (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help_spatial_geography_histogram_TSQL
- sp_help_spatial_geography_histogram
dev_langs: TSQL
helpviewer_keywords: sp_help_spatial_geography_histogram
ms.assetid: 5c5bd319-055d-4cd6-8c5a-06354cc056cc
caps.latest.revision: "13"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c65b21ab76c3ca5880c709e09255ad083ad05def
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="sphelpspatialgeographyhistogram-transact-sql"></a>sp_help_spatial_geography_histogram (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  空間インデックス用のグリッドのパラメーターのキー設定を容易にします。  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_spatial_geography_histogram [ @tabname =] 'tabname'   
     [ , [ @colname = ] 'columnname' ]   
     [ , [ @resolution = ] 'resolution' ]  
     [ , [ @sample = ] 'tablesample' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@tabname =**] **'***tabname $***'**  
 空間インデックスが指定されているテーブルの修飾名または非修飾名です。  
  
 引用符が必要なのは、修飾されたテーブルを指定する場合のみです。 データベース名を含む完全修飾名を指定する場合、データベース名は現在のデータベースの名前である必要があります。 *tabname $*は**sysname**、既定値はありません。  
  
 [  **@colname =** ] **'***columnname***'**  
 指定されている空間列の名前です。 *columnname*は、 **sysname**、既定値はありません。  
  
 [  **@resolution =** ] **'***解決***'**  
 境界ボックスの解像度です。 有効な値は 10 ～ 5000 です。 *解像度*は、 **tinyint**、既定値はありません。  
  
 [  **@sample =** ] **'***サンプル***'**  
 使用するテーブルの割合を指定します。 有効な値は、0 ～ 100 です。 *tablesample*は、 **float**です。 既定値は 100 です。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 テーブルの値が返されます。 テーブルの列の内容を次の表に示します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**cellid**|**int**|開始カウントが 1 の各セルの一意の ID を表します。|  
|**セル**|**geography**|それぞれのセルを表す四角形です。 セルの形は、空間インデックス作成用に使用されたセルの形と同じです。|  
|**row_count**|**bigint**|セルに接しているかまたはセルを含む空間オブジェクトの数を示します。|  
  
## <a name="permissions"></a>Permissions  
 ユーザーのメンバーである必要があります、**パブリック**ロール。 サーバーとオブジェクトに対する READ ACCESS 権限が必要です。  
  
## <a name="remarks"></a>解説  
 SSMS 空間タブでは、結果がグラフィカルに表示されます。 空間ウィンドウに対して結果をクエリすることにより、結果アイテムの概算数を取得できます。  
  
> [!NOTE]  
>  テーブル内のオブジェクトは 1 つ以上のセルをカバーしている場合があるため、テーブルのセルの合計が実際のオブジェクトの数より大きくなることがあります。  
  
 境界ボックス、 **geography**型は、地球全体です。  
  
## <a name="examples"></a>使用例  
 次の例では**sp_help_spatial_geography_histogram**上、`Person.Address`テーブルに、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。  
  
```  
EXEC sp_help_spatial_geography_histogram @tabname = Person.Address, @colname = SpatialLocation, @resolution = 64, @sample = 30;  
```  
  
## <a name="see-also"></a>参照  
 [空間インデックス ストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](http://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)  
  
  
