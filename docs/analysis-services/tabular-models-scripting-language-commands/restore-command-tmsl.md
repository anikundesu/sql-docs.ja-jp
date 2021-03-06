---
title: "Restore コマンド (TMSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/30/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 360a1567-67ae-459d-8865-9a2bef8d4186
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 45e4461956c78278d367715e8ef665821d487e3f
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="restore-command-tmsl"></a>Restore コマンド (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]バックアップ ファイルから Analysis Services データベースを復元します。  
  
## <a name="request"></a>要求  
  
```  
    {  
"restore": {  
            "description": "Parameters of Restore command of Analysis Services JSON API",  
            "properties": {  
            "database": {  
                "type": "string"  
            },  
            "file": {  
                "type": "string"  
            },  
            "password": {  
                "type": "string"  
            },  
            "dbStorageLocation": {  
                "type": "string"  
            },  
            "allowOverwrite": {  
                "type":boolean  
            },  
            "readWriteMode": {  
                "enum": [  
                "readWrite",  
                "readOnly",  
                "readOnlyExclusive"  
                ]  
. . .   
```  
  
 **復元**はいくつかのプロパティがあります。  
  
||||  
|-|-|-|  
|**プロパティ**|**[Default]**|**Description**|  
|database|[必須]|復元するデータベース オブジェクトの名前。|  
|file|[必須]|バックアップ ファイル名またはパス。|  
|パスワード|空|バックアップ ファイルを復号化に使用するパスワード。|  
|allowOverwrite|False|True の場合、バックアップ ファイルがすでに存在することを示すブール値が上書きされます。それ以外の場合は false。|  
|readWriteMode|読み取り/書き込み|データベースに許可されるアクセス モードを示す列挙値。<br /><br /> **列挙値は次のとおりです。**<br /><br /> – 読み取り/書き込み、読み取り/書き込みアクセスが許可されます。<br /><br /> – 読み取り専用、読み取り専用のアクセスが許可されます。<br /><br /> readOnlyExclusive –、読み取り専用の排他アクセスが許可されます。|  
|dbStorageLocation|空|復元されたデータベースの格納場所。|  
  
## <a name="response"></a>応答  
 コマンドが成功した場合は、空の結果を返します。 それ以外の場合、XMLA 例外が返されます。  
  
## <a name="example"></a>例  
 **例 1** -ローカル フォルダーからデータベースを復元します。  
  
```  
{   
   "restore": {   
      "database":"AdventureWorksDW2014",  
      "file":"c:\\awdbdwfile.abf",  
      "security":"...",  
      "allowOverwrite":"true",  
      "password":"..",  
      "locations":"d:\\SQL Server Analysis Services\\data\\",  
      "storageLocation":".."  
   }  
}  
```  
  
## <a name="usage-endpoints"></a>使用状況 (エンドポイント)  
 このコマンドの要素がのステートメントで使用される、[メソッドの実行 &#40;です。XMLA &#41;](../../analysis-services/xmla/xml-elements-methods-execute.md)呼び出しで、次の方法で公開される XMLA エンドポイント。  
  
-   SQL Server Management Studio (SSMS) での XMLA ウィンドウとして  
  
-   入力ファイルとして、**呼び出す ascmd** PowerShell コマンドレット  
  
-   SSIS タスクまたは SQL Server エージェント ジョブへの入力として  
  
 SSMS からこのコマンドのあらかじめ用意されているスクリプトを生成するには、[復元] ダイアログ ボックスの [スクリプト] ボタンをクリックします。  
  
 [ \[MS-t SSAS\]: QL Server Analysis Services Tabular (SQL Server の技術的なプロトコル)](http://go.microsoft.com/fwlink/p/?LinkId=784855) JSON 表形式メタデータ コマンドとオブジェクトの構造を説明するセクション 3.1.5.2.2 がドキュメントに含まれています。 現時点では、そのドキュメントでは、コマンドや TMSL スクリプトで実装されていない機能について説明します。 トピックを参照してください[表形式モデル スクリプト言語 &#40;です。TMSL &#41;参照](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)明確にする新機能がサポートされている.  
  
## <a name="see-also"></a>参照  
 [表形式モデルのスクリプト言語 (TMSL) リファレンス](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Analysis Services データベースのバックアップと復元](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
