---
title: "SetFlag メソッド (ClientNetworkProtocolProperty クラス) |Microsoft ドキュメント"
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
apiname: SetFlag Method (ClientNetworkProtocolProperty Class)
apilocation: sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords: SetFlag method
ms.assetid: 0407520f-2f84-4f68-b2b7-429697286c1b
caps.latest.revision: "29"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 66a3625411e2f403264af70c9816f08fbb63ee91
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="setflag-method-clientnetworkprotocolproperty-class"></a>SetFlag メソッド (ClientNetworkProtocolProperty クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]によって参照される現在のプロパティのフラグを設定、 [PropertyIdx プロパティ (ClientNetworkProtocolProperty クラス)](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/propertyidx-property-clientnetworkprotocolproperty-class.md)値。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.SetFlag(BoolValue) [=]  
```  
  
## <a name="parts"></a>要素  
 *オブジェクト*  
 A [ClientNetworkProtocolProperty クラス](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md)によって使用されるネットワーク プロトコルの属性を表すオブジェクト、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]クライアント。  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|Description|  
|---------------|-----------------|  
|*BoolValue*|フラグの新しい値を指定するブール値|  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 **uint32** 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [クライアント プロトコルの構成](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  
