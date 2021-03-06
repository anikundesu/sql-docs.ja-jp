---
title: "文字列ストレージとテーブル モデルでの照合順序 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8516f0ad-32ee-4688-a304-e705143642ca
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 90b110552e0ea5469258581c1d1e26d4ebd86d36
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="string-storage-and-collation-in-tabular-models"></a>テーブル モデルの文字列ストレージと照合順序
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]文字列 (テキスト値); の表形式モデルには、圧縮率の高い形式に格納されます。この圧縮により、全体または部分文字列を取得するときに予期しない結果を取得できます。 文字列のロケールと照合順序は最も近い親プロジェクトから階層的に継承されるため、文字列の言語が明示的に定義されていない場合、親のロケールと照合順序は、文字列の格納方法、および文字列が一意であるか親の照合順序の定義に従って同様の文字列と結合されるかに影響することがあります。  
  
 このトピックでは、文字列を圧縮および格納するメカニズムについて説明し、照合順序と言語がテーブル モデルのテキスト式の結果に与える影響の例を示します。  
  
## <a name="storage"></a>ストレージ  
 テーブル モデルでは、すべてのデータがより効率よくメモリに収まるように高度に圧縮されます。 その結果、構文的に等価と見なされるすべての文字列が 1 回だけ格納されます。 文字列の最初のインスタンスが正規表現として使用され、等価な各文字列は最初の出現と同じ圧縮値にインデックス付けされます。  
  
 重要な問題は、構文的に等価な文字列を構成するものは何かということです。 2 つの文字列は、同じ単語と見なされる場合に構文的に等価と見なされます。 たとえば、英語では、 **violin** という単語を辞書で検索すると、辞書の編集方針に応じて **Violin** または **violin**というエントリが見つかりますが、一般にはどちらの単語も等価と見なされ、大文字と小文字の違いは無視されます。 テーブル モデルでは、2 つの文字列が構文的に等価であるかどうかを決定する要因は、編集方針やユーザー設定ではなく、列に割り当てられたロケールと照合順序です。  
  
 したがって、大文字と小文字を同じものとして扱うか異なるものとして扱うかは、照合順序とロケールによって決まります。 ロケール内の単語について、特定の列内に最初に見つかったため単語および文字列の正規表現として使用される単語が非圧縮形式で格納されます。  他のすべての文字列は最初の出現に照らしてテストされ、等価テストで一致した場合は最初の出現の圧縮値に割り当てられます。 後で圧縮値が取得されるときに、それらの圧縮値は文字列の最初の出現の非圧縮値を使用して表現されます。  
  
 このしくみを明確にするのには例が役立ちます。 次の「分類 - 英語」列は、植物と木の情報を含むテーブルから抽出しました。 各植物 (ここでは植物の名前を示しません) について、分類列に植物の一般カテゴリが示されます。  
  
|分類 - 英語|  
|-------------------------------|  
|trEE|  
|PlAnT|  
|trEE|  
|PlAnT|  
|PlAnT|  
|trEE|  
|PlAnT|  
|trEE|  
|trEE|  
|PlAnT|  
|trEE|  
  
 データは多くの異なるソースから取得される可能性が高いため、大文字と小文字の違いやアクセントの使用には一貫性がなく、リレーショナル データベースにはこれらの違いがそのまま格納されています。 ただし、一般に値は **Plant** または **Tree**であり、大文字と小文字のみ異なります。  
  
 米国英語の既定の照合順序と並べ替え順序を使用するテーブル モデルにこれらの値を読み込む場合、大文字と小文字の区別は重要でないため、列全体に対して 2 つの値のみ格納されます。  
  
|分類 - 英語|  
|-------------------------------|  
|trEE|  
|PlAnT|  
  
 モデルで **「分類 – 英語」**列を使用する場合、植物の分類を表示するときにさまざまな方法で大文字と小文字を使用している元の値は表示されず、最初のインスタンスのみ表示されます。 その理由は、この照合順序とロケールでは **tree** の大文字と小文字のすべてのバリエーションが等価と見なされるため、1 つの文字列のみ保持され、システムで検出されたその文字列の最初のインスタンスが保存されるためです。  
  
> [!WARNING]  
>  適切と思われる文字列に応じて格納する最初の文字列を定義することもできますが、この処理は非常に困難な可能性があります。 すべての値が同じと見なされる場合に、エンジンによって最初に処理される行をあらかじめ決定する簡単な方法はありません。 代わりに、標準値を設定する必要がある場合は、モデルを読み込む前にすべての文字列をクレンジングする必要があります。  
  
## <a name="locale-and-collation-order"></a>ロケールと照合順序  
 文字列 (テキスト値) を比較する場合、一般に等価性は文字列が解釈される方法のカルチャによって定義されます。 一部のカルチャでは、文字のアクセントや大文字と小文字の違いによって文字列の意味がまったく異なる場合があるため、通常、特定の言語や地域に対して等価性を判断するときにはこのような違いが考慮されます。  
  
 通常、コンピューターを使用する場合、コンピューターは独自のカルチャによる要請や言語の動作と一致するように既に構成されており、テキスト値の並べ替えや比較などの文字列操作は期待どおりに動作します。 言語固有の動作を制御する設定は、Windows の **地域と言語** の設定で定義します。 アプリケーションはこれらの設定を読み取り、この設定に従って動作を変更します。 場合によっては、アプリケーションに、アプリケーションのカルチャ動作または文字列の比較方法を変更できる機能があります。  
  
 テーブル モデル データベースの作成時に、データベースは既定でこれらのカルチャおよび言語設定を言語識別子と照合順序の形式で継承します。  
  
-   言語識別子では、文字列に使用する文字セットがカルチャに従って定義されます。  
  
-   照合順序では、文字の順序とその等価性が定義されます。  
  
 言語識別子は言語を識別するだけでなく、言語が使用されている国または地域も識別することに注意してください。 各言語識別子には、既定の照合順序も指定されています。 言語識別子の詳細については、「 [Microsoft によって割り当てられているロケール ID](http://msdn.microsoft.com/goglobal/bb964664.aspx)」を参照してください。 LCID Dec 列を使用して、値を手動で挿入するときに適切な ID を取得できます。 SQL での照合順序の概念の詳細については、「[COLLATE &#40;Transact-SQL&#41;](../../t-sql/statements/collations.md)」を参照してください。 Windows の照合順序名の照合順序指定子および比較スタイルの詳細については、「[Windows 照合順序名 &#40;Transact-SQL&#41;](../../t-sql/statements/windows-collation-name-transact-sql.md)」を参照してください。 「[SQL Server 照合順序名 &#40;Transact-SQL&#41;](../../t-sql/statements/sql-server-collation-name-transact-sql.md)」のトピックでは、Windows 照合順序名を SQL で使用される名前にマップします。  
  
 テーブル モデル データベースの作成後に、モデル内のすべての新規オブジェクトが言語および照合順序の属性をデータベースの属性から継承します。 これは、すべてのオブジェクトに適用されます。 継承パスはオブジェクトから開始し、継承する言語および照合順序の属性の親を参照し、何も見つからない場合は一番上まで進んでデータベース レベルの言語および照合順序の属性を探します。 つまり、オブジェクトの言語および照合順序の属性を指定しない場合、オブジェクトは既定でその最も近い親から属性を継承します。  
  
 列の場合、言語および照合順序の属性は次のルールに従って作成時に継承されます。  
  
1.  親ディメンション オブジェクトで言語および照合順序の属性が検索されます。 両方の値が存在する場合は、それらが列の属性にコピーされます。一方のみ存在する場合、他方は既存の属性から継承され、両方が割り当てられます。両方とも存在しない場合は次の手順に進みます。  
  
2.  手順 1. でディメンションについて説明したのと同じプロセスを使用してデータベース オブジェクトが検索されます。属性が見つからない場合は、次の手順に進みます。  
  
3.  手順 1. でディメンションについて説明したのと同じプロセスを使用してサーバー オブジェクトが検索されます。属性が見つからない場合、列では Windows 言語識別子が使用され、その値の照合順序属性が推測されます。  
  
 通常、ソース データベースでの言語識別子と照合順序はテーブル モデルの列に値が格納される方法にほとんど影響しないかまったく影響しないことに注意してください。 例外は、ソース データベースが要求された値を変換またはフィルター選択する場合です。  
  
  
