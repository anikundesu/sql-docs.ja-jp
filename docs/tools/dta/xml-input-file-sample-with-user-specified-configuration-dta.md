---
title: "XML 入力ファイルのユーザーが指定した構成サンプル (DTA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: dta
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: XML
helpviewer_keywords: sample applications [DTA]
ms.assetid: b29c9716-e5c3-4003-9efb-3ade2197b630
caps.latest.revision: "21"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0a8f6fb06e3e587410321dbe3a205df08f421356
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="xml-input-file-sample-with-user-specified-configuration-dta"></a>ユーザー指定の構成を指定した XML 入力ファイルのサンプル (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]コピーし、ユーザー指定の構成を指定する XML 入力ファイルのこのサンプルを貼り付け、**構成**要素を使い慣れた XML エディターまたはテキスト エディターにします。 これにより、"what-if" 分析を行うことができます。 "What-if" 分析では、 **Configuration** 要素を使用して、チューニング対象のデータベースに対して仮想的な物理設計構造のセットを指定します。 その後、データベース エンジン チューニング アドバイザーを使用して、この仮想的な構成に対してワークロードを実行した場合の影響を分析し、クエリ処理のパフォーマンスが向上するかどうかを調べます。 このタイプの分析には、実際に実装しなくても新しい構成を評価できるという利点があります。 仮想の構成で、期待したパフォーマンスの向上が得られなかった場合は、簡単に構成を変更でき、望ましい結果を生成する構成になるまで分析を繰り返し行えます。  
  
 このサンプルを編集ツールにコピーした後に、 **Server**、 **Database**、 **Schema**、 **Table**、 **Workload**、 **TuningOptions**、および **Configuration** 要素で指定する値を、特定のチューニング セッションの値に置き換えてください。 これらの要素で使用できるすべての属性および子要素の詳細については、「 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)」を参照してください。 以下のサンプルでは、使用できる属性や子要素の一部だけを使用しています。  
  
## <a name="code"></a>コード  
  
```  
<?xml version="1.0" encoding="utf-16" ?>  
<DTAXML xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.microsoft.com/sqlserver/2004/07/dta">  
  <DTAInput>  
    <Server>  
      <Name>MyServerName</Name>  
<!-- To tune multiple databases, list them and their associated tables in the following section. -->  
      <Database>  
        <Name>MyDatabaseName</Name>  
        <Schema>  
          <Name>MyDatabaseSchemaName</Name>  
<!-- You can list as many tables as necessary in the following section. -->  
          <Table>  
            <Name>MyTableName1</Name>  
          </Table>  
          <Table>  
            <Name>MyTableName2</Name>  
          </Table>  
        </Schema>  
      </Database>  
    </Server>  
    <Workload>  
<!-- The following element specifies a workload file, which can be a trace file or a Transact-SQL script file. -->  
      <File>c:\PathToYourWorkloadFile</File>  
    </Workload>  
    <TuningOptions>  
      <TuningTimeInMin>180</TuningTimeInMin>  
      <StorageBoundInMB>10000</StorageBoundInMB>  
      <FeatureSet>IDX_IV</FeatureSet>  
      <Partitioning>NONE</Partitioning>  
      <KeepExisting>NONE</KeepExisting>  
      <OnlineIndexOperation>OFF</OnlineIndexOperation>  
    </TuningOptions>  
    <Configuration SpecificationMode="Absolute">  
      <Server>  
        <Name>MyServerName</Name>  
          <Database>  
            <Name>MyDatabaseName</Name>  
            <Schema>  
              <Name>MyDatabaseSchemaName</Name>  
                <Table>  
                  <Name>MyTableName1</Name>  
                  <Recommendation>  
                    <Create>  
                      <Index Clustered="true" Unique="false" Online="false" IndexSizeInMB="873.75">  
                        <Name>MyIndexName</Name>  
                        <Column Type="KeyColumn" SortOrder="Ascending">  
                          <Name>MyColumnName1</Name>  
                        </Column>  
                        <Filegroup>MyFileGroupName1</FileGroup>  
                      </Index>  
                    </Create>  
                  </Recommendation>  
                </Table>  
            </Schema>  
          </Database>  
      </Server>  
    </Configuration>  
  </DTAInput>  
</DTAXML>  
```  
  
## <a name="comments"></a>コメント  
  
-   **Configuration** 要素に **Absolute** モードを指定した場合 (`Configuration SpecificationMode="Absolute"`)、物理設計構造の削除はサポートされません。  
  
-   **Configuration** 要素のいずれのモードでも ( **Relative**または **Absolute** )、同一の物理設計構造の作成と削除はできません。  
  
## <a name="see-also"></a>参照  
 [データベース エンジン チューニング アドバイザーの起動および使用](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)   
 [データベース エンジン チューニング アドバイザーからの出力の表示および操作](../../relational-databases/performance/view-and-work-with-the-output-from-the-database-engine-tuning-advisor.md)   
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
