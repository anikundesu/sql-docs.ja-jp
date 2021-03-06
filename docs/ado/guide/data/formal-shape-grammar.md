---
title: "図形の正式な文法 |Microsoft ドキュメント"
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
helpviewer_keywords:
- shape commands [ADO], shape grammar
- data shaping [ADO], shape grammar
ms.assetid: ea691475-0f03-4abe-a785-b77e77712d1d
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 09f578dc3467c10be247e34c4ebb89807543052f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="formal-shape-grammar"></a>図形の正式な文法
これは、正式な文法任意図形のコマンドを作成するためです。  
  
-   必要な文法的な用語では、山かっこ ("<>") で区切られたテキスト文字列を示します。  
  
-   省略可能な条件は、角かっこ ("") で区切られます。  
  
-   代替手段は、縦棒で示されます ("&#124;") です。  
  
-   繰り返しの代替手段は、省略記号 ([...]) によって示されます。  
  
-   *アルファ*英文字の文字列を示します。  
  
-   *桁*数値の文字列を示します。  
  
-   *Unicode 桁*unicode の数字の文字列を示します。  
  
 その他のすべての用語は、リテラルを示します。  
  
|項目|定義|  
|----------|----------------|  
|\<shape コマンド >|図形 [\<テーブル exp > [と]\<エイリアス >] [\<図形アクション >]|  
|\<テーブル exp >|{\<プロバイダー コマンド テキスト >} &#124; です。<br /><br /> (\<shape コマンド >) &#124;<br /><br /> テーブル\<引用符で囲まれた名 > &#124; です。<br /><br /> \<引用符で囲まれた名前 >|  
|\<アクション図形 >|APPEND\<エイリアス フィールド リスト > &#124; です。<br /><br /> コンピューティング\<エイリアス > [BY\<フィールド リスト >]|  
|\<エイリアス >|\<エイリアス フィールド > [、\<エイリアス フィールド… >]|  
|\<エイリアス フィールド >|\<フィールド exp > [と]\<エイリアス >]|  
|\<フィールド exp >|(\<関係 exp >) &#124;<br /><br /> \<計算 exp > &#124; です。<br /><br /> \<集計 exp > &#124; です。<br /><br /> \<新しい exp >|  
|< relation_exp >|\<テーブル exp > [と]\<エイリアス >]<br /><br /> 関連付け\<関係の条件付きの一覧 >|  
|\<関係条件の一覧 >|\<関係条件 > [、\<関係条件 >...]|  
|\<関係条件 >|\<フィールド名 > に\<子 ref >|  
|\<子 ref >|\<フィールド名 > &#124; です。<br /><br /> パラメーター \<param ref >|  
|\<param ref >|\<番号 >|  
|\<フィールドの一覧 >|\<フィールド名 > [、\<フィールド名 >]|  
|\<集計 exp >|SUM (\<修飾されたフィールド名 >) &#124;<br /><br /> AVG (\<修飾されたフィールド名 >) &#124;<br /><br /> MIN (\<修飾されたフィールド名 >) &#124;<br /><br /> MAX (\<修飾されたフィールド名 >) &#124;<br /><br /> カウント (\<修飾されたエイリアス > &#124; です。\<修飾名 >) &#124;<br /><br /> STDEV (\<修飾されたフィールド名 >) &#124;<br /><br /> 任意 (\<修飾されたフィールド名 >)|  
|\<計算 exp >|計算 (\<式 >)|  
|\<修飾されたフィールドの名前 >|\<エイリアス >。[\<エイリアス >...]\<フィールド名 >|  
|\<エイリアス >|\<引用符で囲まれた名前 >|  
|\<フィールド名 >|\<引用符で囲まれた名前 > [と]\<エイリアス >]|  
|\<引用符で囲まれた名前 >|"\<文字列 >"&#124; です。<br /><br /> '\<文字列 >' &#124;<br /><br /> [\<文字列 >] &#124; です。<br /><br /> \<名 >|  
|\<修飾名 >|エイリアス [.alias...]|  
|\<名 >|アルファ [alpha &#124; 数字 &#124; 以外の場合は _ &#124; # &#124; : &#124;...]|  
|\<番号 >|[数字] の数字|  
|\<新しい exp >|新しい\<フィールド型 > [(\<番号 > [、\<番号 >])]|  
|\<フィールドの種類 >|OLE DB または ADO データ型です。|  
|\<文字列 >|unicode char [unicode 文字...]|  
|\<式 >|アプリケーションの式のオペランドが同じ行の場合は、他の非計算列用の Visual Basic の場合。|  
  
## <a name="see-also"></a>参照  
 [階層のレコード セット内の行にアクセスします。](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)   
 [データ シェイプの概要](../../../ado/guide/data/data-shaping-overview.md)   
 [データ シェイプに必要なプロバイダー](../../../ado/guide/data/required-providers-for-data-shaping.md)   
 [図形の APPEND 句](../../../ado/guide/data/shape-append-clause.md)   
 [一般的な図形コマンド](../../../ado/guide/data/shape-commands-in-general.md)   
 [図形の COMPUTE 句](../../../ado/guide/data/shape-compute-clause.md)   
 [Visual Basic for Applications の関数](../../../ado/guide/data/visual-basic-for-applications-functions.md)
