---
title: "セットの正確なコマンド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SET EXACT command [ODBC]
ms.assetid: 9533d3e0-e7c1-49de-a3a3-0cc4373a91cb
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dcb836649993ddb644006986f284f0c0a362ed81
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="set-exact-command"></a>セットの正確なコマンド
異なる長さの 2 つの文字列を比較するための規則を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SET EXACT ON | OFF  
```  
  
## <a name="arguments"></a>引数  
 ON  
 正規表現が等価である文字の文字に一致する必要がありますを指定します。 比較式の後に続く空白は無視されます。 比較、2 つの式のうち短い方が右側に空白長い式の長さが一致するように埋め込まれます。  
  
 OFF  
 (既定)。、等価である、式と一致するが文字を文字の右側にある式の末尾に到達するまでを指定します。  
  
## <a name="remarks"></a>解説  
 両方の文字列が同じ長さである場合は、正確な設定の設定を指定しても効果がありません。  
  
## <a name="string-comparisons"></a>文字列の比較  
 Visual FoxPro には、等しいかどうかをテストする 2 つの関係演算子があります。  
  
 = 演算子が同じ型の 2 つの値の比較を実行します。 この演算子は、文字、数値、日付、および論理データの比較に適しています。  
  
 含む文字式を比較するときに、演算子、= 結果できない可能性があります正確に期待どおりに表示します。 文字式の比較は左から右の式の右側にあるを終了するまで、他のと等しくない、式のいずれかになるまでの文字の文字、= (SET 正確な OFF)、オペレーターが不在の両方の式が終了するまで、または(設定の正確な ON) に達しました。  
  
 = = 演算子は、文字データの正確な比較が必要なときに使用できます。 2 つの文字式と比較する場合、演算子の両側の式を = =、= = 演算子がまったく同じ文字、等しいと見なされる空白を含むを含める必要があります。 使用して文字の文字列を比較するときに、正確な設定の設定は無視 = = です。  
  
 次の表では、演算子の選択と設定の正確な設定に比較に影響する方法を示します。 (アンダー スコアは、空白を表します)。  
  
|比較|= オフ正確です|= で正確です|= = 正確な ON または OFF|  
|----------------|------------------|-----------------|--------------------------|  
|"abc""abc"を =|一致します。|一致します。|一致します。|  
|"ab"="abc"|一致なし|一致なし|一致なし|  
|"abc"="ab"|一致します。|一致なし|一致なし|  
|"abc"="ab_"|一致なし|一致なし|一致なし|  
|"ab"="ab_"|一致なし|一致します。|一致なし|  
|"ab_"="ab"|一致します。|一致します。|一致なし|  
|""="ab"|一致なし|一致なし|一致なし|  
|"ab"=""|一致します。|一致なし|一致なし|  
|"__" = ""|一致します。|一致します。|一致なし|  
|"" = "___"|一致なし|一致します。|一致なし|  
|TRIM("___") =""|一致します。|一致します。|一致します。|  
|""TRIM("___") を =|一致します。|一致します。|一致します。|  
  
## <a name="see-also"></a>参照  
 [SET ANSI コマンド](../../odbc/microsoft/set-ansi-command.md)
