---
title: "srv_paramsetoutput (拡張ストアド プロシージャ API) | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: srv_paramsetoutput
apilocation: opends60.dll
apitype: DLLExport
dev_langs: C++
helpviewer_keywords: srv_paramsetoutput
ms.assetid: f2810e19-e513-458b-8925-5756b6ee1313
caps.latest.revision: "29"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2a1878227f13fda83fe6a7b7d096b033614356ef
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="srvparamsetoutput-extended-stored-procedure-api"></a>srv_paramsetoutput (拡張ストアド プロシージャ API)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]代わりに CLR Integration をご使用ください。  
  
 戻りパラメーターの値を設定します。 この関数は、**srv_paramset** 関数に代わるものです。  
  
## <a name="syntax"></a>構文  
  
```  
  
int srv_paramsetoutput (  
SRV_PROC *  
srvproc  
,  
int  
n  
,  
BYTE *  
pbData  
,  
ULONG   
cbLen  
,  
BOOL  
fNull   
);  
```  
  
## <a name="arguments"></a>引数  
 *srvproc*  
 クライアント接続のためのハンドルです。  
  
 *n*  
 設定するパラメーターの序数です。 最初のパラメーターは 1 です。  
  
 *pbData*  
 プロシージャの戻りパラメーターとしてクライアントに返されるデータ値を指すポインターです。  
  
 *cbLen*  
 返されるデータの実際の長さです。 パラメーターのデータ型が固定長の値を指定しており、NULL 値を許容しない型 (*srvbit*、*srvint1* など) である場合、*cbLen* は無視されます。 *fNull* が FALSE の場合、値 0 は長さ 0 のデータを示します。  
  
 *fNull*  
 戻りパラメーターの値が NULL かどうかを示すフラグです。 パラメーターを NULL に設定する必要がある場合は、このフラグを TRUE に設定します。 既定値は FALSE です。 *fNull* を TRUE に設定した場合は、*cbLen* を 0 に設定する必要があります。このように設定しないと関数は失敗します。  
  
## <a name="returns"></a>戻り値  
 パラメーター情報が正常に設定された場合は SUCCEED を返し、それ以外の場合は FAIL を返します。 FAIL が返されるのは、次の場合です。  
  
-   パラメーターが戻りパラメーターでない場合。  
  
-   *cbLen* 引数が無効である場合。  
  
## <a name="remarks"></a>解説  
 **セキュリティに関する注意** 拡張ストアド プロシージャのソース コードを十分に確認し、コンパイルした DLL をテストしたうえで実稼働サーバーにインストールしてください。 セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/)をご覧ください。  
  
  
