---
title: "SetCurrentCertificate メソッド (SInstance クラス) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: wmi
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: SetCurrentCertificate Method (SInstance Class)
apilocation: sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords: SetCurrentCertificate method
ms.assetid: 7349fb87-b973-4160-a2be-cab73abf5b31
caps.latest.revision: "14"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a392000ab30313fb0833c1c51bf67d2e5ee64c4b
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="setcurrentcertificate-method-sinstance-class"></a>SetCurrentCertificate メソッド (SInstance クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]現在のセキュリティ証明書を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.SetCurrentCertificate(SHA)  
```  
  
## <a name="parts"></a>要素  
 *オブジェクト*  
 [SInstance クラス](../../../relational-databases/wmi-provider-configuration-classes/sinstance-class/sinstance-class.md)のインスタンス上のサーバー設定を表すオブジェクト[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]です。  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|Description|  
|---------------|-----------------|  
|*SHA*|現在のセキュリティ証明書を指定する文字列値|  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 **uint32** 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [サーバー ネットワーク プロトコルとネットワーク ライブラリの構成](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
