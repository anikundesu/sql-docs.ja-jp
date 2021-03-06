---
title: "使用中でないときにオブジェクトを閉じる |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce8f9b35-c761-4b0c-9a46-985eef2c2e0b
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1c7f6a0421355676909de0edb1b6d1349c84e785
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="closing-objects-when-not-in-use"></a>使用されていないオブジェクトを閉じる
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  オブジェクトを操作するときに[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]、特に[SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)などのオブジェクトのステートメントのいずれかまたは[SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)、 [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)または[SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)、不要になったときに、閉じる方法を使用して、それらに明示的に閉じる必要があります。 これにより、Java 仮想マシンのガベージ コレクターによる処理を待たずに、迅速にドライバーとサーバーのリソースを解放できるため、パフォーマンスが向上します。  
  
 スクロール ロックを使用しているときに、サーバー上で適切な同時実行を維持するためには、オブジェクトを閉じることが特に重要となります。 最後にアクセスしたフェッチ バッファーのスクロール ロックは、結果セットが閉じられるまで保持されます。 同様に、ステートメントの準備されたハンドルは、ステートメントが閉じられるまで保持されます。 複数のステートメントで接続を再利用する場合は、スコープから出る前にステートメントを閉じることで、サーバーが準備されたハンドルを早期にクリーンアップできるようになります。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーによるパフォーマンスと信頼性の強化](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  
