---
title: "スクリプト言語と ADO の併用 |Microsoft ドキュメント"
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
- scripting languages [ADO]
- ADO, scripting languages
ms.assetid: 76fc4d00-0c9f-422b-af5c-af6ed8fb29d8
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c7551fd26f6c0862115f0212777fb738a68e548a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="using-ado-with-scripting-languages"></a>スクリプト言語と ADO の併用
ADO では、スクリプト環境では、サーバー側のスクリプトを使用してデータを公開できます。 この場合は、ADO では、基になる OLE DB プロバイダーを使用して、特定のデータ ストアを参照するために必要なその他のコンポーネントは、インターネット インフォメーション サービス (IIS) を実行しているサーバーにインストールされています。 Active Server Pages (ASP) を使用して、ADO は、たとえば、HTML を生成するスクリプトで参照されるコンポーネントです。 この HTML コンテンツは、クライアントの Web ブラウザーに HTTP 経由で渡すことができます。 スクリプトを使用して Web ページは、サーバー側のスクリプトは、更新、移動、および特定のデータを表示することができますに戻す操作を送信できます。  
  
 Web ページで、ActiveX オブジェクトを使用する前に、オブジェクトがスクリプトに対して安全かどうかを知る必要があります。 オブジェクトは、スクリプトを実行しても安全と見なされます、コントロールがユーザーのコンピューターの有害なアクションを実行することはできず、そのため、ユーザーの承認を求められることがなく実行できることを示します。 次の表は、ADO オブジェクトの一覧し、スクリプト作成のため安全であるかどうかを示します。  
  
|Object|スクリプト作成のため安全ですか。|  
|------------|-------------------------|  
|ADO 接続|可|  
|ADO コマンド|不可|  
|ADO パラメーター|不可|  
|ADO レコード セット|可|  
|ADO レコード|可|  
|ADO ストリーム|可|  
|ADO エラーです。|不可|  
|ADOX カタログ|不可|  
|ADOX セルセット|不可|  
|RDS DataControl|可|  
|RDS DataSpace|可|  
|RDS DataFactory|不可|  
  
 次の表は、Windows DAC/MDAC では、含まれているプロバイダーの一覧し、スクリプト作成のため安全であるかどうかを示します。  
  
|プロバイダー|スクリプト作成のため安全ですか。|  
|--------------|-------------------------|  
|図形|可|  
|永続化します。|可|  
|Remote|可|  
|OLE DB Provider for SQL Server (SQLOLEDB)|不可|  
|OLE DB Provider for ODBC (MSDASQL)|不可|  
  
## <a name="odbc-data-sources"></a>ODBC データ ソース  
 ADO コードをスクリプト化し、非スクリプトの 1 つの大きな違いは、使用する場合に、ODBC データ ソースがします。 非スクリプト アプリケーションの ODBC データ ソース アドミニストレーターでユーザー DSN を作成できます。 IIS で実行されるスクリプトには、システム DSN を作成する必要があります。それ以外の場合、スクリプトには、作成したデータ ソースは認識されません。 これは、Microsoft IIS を介した ODBC 用 Microsoft OLE DB プロバイダーを使用する ADO スクリプト アプリケーションに適用されます。  
  
## <a name="referencing-the-ado-library"></a>ADO ライブラリを参照します。  
 スクリプト言語では適用されません。  
  
## <a name="handling-events"></a>イベントを処理  
 スクリプト言語では適用されません。  
  
 次のトピックでは、スクリプト言語と ADO の併用の詳細についてを紹介します。  
  
-   [VBScript での ADO プログラミング](../../../ado/guide/appendixes/vbscript-ado-programming.md)  
  
-   [JScript での ADO プログラミング](../../../ado/guide/appendixes/jscript-ado-programming.md)  
  
## <a name="see-also"></a>参照  
 [Microsoft ActiveX Data Objects (ADO)](../../../ado/microsoft-activex-data-objects-ado.md)   
 [Microsoft Visual Basic と ADO を使用します。](../../../ado/guide/appendixes/using-ado-with-microsoft-visual-basic.md)   
 [Microsoft Visual C++ での ADO の使用](../../../ado/guide/appendixes/using-ado-with-microsoft-visual-c.md)   
