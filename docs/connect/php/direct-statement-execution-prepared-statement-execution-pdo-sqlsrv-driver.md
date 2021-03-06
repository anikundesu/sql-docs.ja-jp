---
title: "ステートメントの準備されたステートメントの実行の PDO_SQLSRV ドライバーを直接 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05544ca6-1e07-486c-bf03-e8c2c25b3024
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8df460f169a1890c9e30bd2b72baa4a38fd4bf31
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="direct-statement-execution-and-prepared-statement-execution-in-the-pdosqlsrv-driver"></a>Direct Statement Execution and Prepared Statement Execution in the PDO_SQLSRV Driver (PDO_SQLSRV ドライバーでの直接ステートメント実行と準備されたステートメントの実行)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

このトピックでは、pdo::sqlsrv_attr_direct_query 属性を使用して、既定値は、準備されたステートメントの実行ではなく、直接のステートメントの実行を指定する方法について説明します。  ドライバーは、ステートメントを準備、複数回バインドされているパラメーターを使用してステートメントを実行する場合のパフォーマンスが向上結果ことができます。  
  
## <a name="remarks"></a>解説  
送信する場合、[!INCLUDE[tsql](../../includes/tsql_md.md)]ステートメントでは、ドライバーによってステートメントの準備なしでサーバーに直接、pdo::sqlsrv_attr_direct_query 属性を設定する[pdo::setattribute](../../connect/php/pdo-setattribute.md) (に渡されるドライバーのオプションとしてまたは[:: _ _Construct](../../connect/php/pdo-construct.md)) を呼び出したときまたは[pdo::prepare](../../connect/php/pdo-prepare.md)です。 既定では、pdo::sqlsrv_attr_direct_query の値が False (準備されたステートメントの実行を使用します)。  
  
使用する場合[pdo::query](../../connect/php/pdo-query.md)、直接実行ことができます。 呼び出しの前に[pdo::query](../../connect/php/pdo-query.md)、呼び出す[pdo::setattribute](../../connect/php/pdo-setattribute.md) pdo::sqlsrv_attr_direct_query を True に設定します。  各呼び出し[pdo::query](../../connect/php/pdo-query.md) pdo::sqlsrv_attr_direct_query の異なる設定で実行できます。  
  
使用する場合[pdo::prepare](../../connect/php/pdo-prepare.md)と[pdostatement::execute](../../connect/php/pdostatement-execute.md)クエリを複数回実行する準備されたステートメントの実行、バインドされたパラメーターを使用して最適化されます繰り返されるクエリを実行します。  そのような状況で呼び出す[pdo::prepare](../../connect/php/pdo-prepare.md)で pdo::sqlsrv_attr_direct_query のドライバーのオプション配列パラメーターで False に設定します。 必要な場合は、pdo::sqlsrv_attr_direct_query は False に設定と準備されたステートメントを実行できます。  
  
呼び出した後[pdo::prepare](../../connect/php/pdo-prepare.md)、準備されたクエリを実行するときに pdo::sqlsrv_attr_direct_query の値を変更することはできません。  
  
クエリは、前のクエリで設定されたコンテキストを必要とする場合は、pdo::sqlsrv_attr_direct_query True に設定すると、クエリを実行する必要があります。 たとえば場合は、クエリで一時テーブルを使用すると、pdo::sqlsrv_attr_direct_query を True に設定する必要があります。  
  
次の例では、前のステートメントからのコンテキストが必要な場合は、pdo::sqlsrv_attr_direct_query を True に設定する必要がありますを示します。  このサンプルでは、一時テーブルは、するには、プログラム内の後続のステートメントを直接のクエリの実行を使用します。  
  
```  
<?php  
   $conn = new PDO('sqlsrv:Server=(local)', '', '');  
   $conn->setAttribute(constant('PDO::SQLSRV_ATTR_DIRECT_QUERY'), true);  
  
   $stmt1 = $conn->query("DROP TABLE #php_test_table");  
  
   $stmt2 = $conn->query("CREATE TABLE #php_test_table ([c1_int] int, [c2_int] int)");  
  
   $v1 = 1;  
   $v2 = 2;  
  
   $stmt3 = $conn->prepare("INSERT INTO #php_test_table (c1_int, c2_int) VALUES (:var1, :var2)");  
  
   if ($stmt3) {  
      $stmt3->bindValue(1, $v1);  
      $stmt3->bindValue(2, $v2);  
  
      if ($stmt3->execute())  
         echo "Execution succeeded\n";       
      else  
         echo "Execution failed\n";  
   }  
   else  
      var_dump($conn->errorInfo());  
  
   $stmt4 = $conn->query("DROP TABLE #php_test_table");  
?>  
```  
  
## <a name="see-also"></a>参照  
[プログラミング ガイド](../../connect/php/programming-guide-for-php-sql-driver.md)
  
