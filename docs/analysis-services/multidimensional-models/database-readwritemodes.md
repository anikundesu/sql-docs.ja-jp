---
title: "データベースの Readwritemode |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
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
helpviewer_keywords:
- databases [Analysis Services], read/write
- databases [Analysis Services], read-only
ms.assetid: 03d7cb5c-7ff0-4e15-bcd2-7075d1b0dd69
caps.latest.revision: "19"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b7c48381d6f4cc1c7c92802f2028c73f8afb402d
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="database-readwritemodes"></a>データベースの ReadWriteMode
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]状況はよくときに、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベース管理者 (dba) が読み取り専用のデータベースを読み取り/書き込みデータベースを変更するまたはその逆です。 こうした状況は、ソリューションのスケールアウトやパフォーマンスの向上のために 1 つのデータベース フォルダーを複数のサーバー間で共有するなど、ビジネス上のニーズによって頻繁に発生します。 このような場合は、 **ReadWriteMode** データベース プロパティを使用すると、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] DBA はデータベースの動作モードを容易に変更できます。  
  
## <a name="readwritemode-database-property"></a>ReadWriteMode データベース プロパティ  
 **ReadWriteMode** データベース プロパティは、データベースが読み取り/書き込みモードと読み取り専用モードのどちらであるかを指定します。 このプロパティの使用可能な値は 2 つだけです。 データベースが読み取り専用モードの場合は、変更または更新をデータベースに適用できません。 一方、データベースが読み取り/書き込みモードの場合は、変更や更新を行うことができます。 **ReadWriteMode** データベース プロパティは読み取り専用プロパティとして定義されています。このプロパティは、 **Attach** コマンドを使用してのみ設定できます。  
  
 データベースが読み取り専用モードの場合は、一定の制限が適用され、データベースに許可されている通常の操作に影響を与えます。 制限される操作については、次の表を参照してください。  
  
|ReadOnly モード|制限される操作|  
|-------------------|---------------------------|  
|XML/A コマンド<br /><br /> <br /><br /> 注: これらのコマンドのいずれかを実行すると、エラーが発生します。|**作成**<br /><br /> **Alter**<br /><br /> **Del**<br /><br /> **[処理]**<br /><br /> **MergePartitions**<br /><br /> **DesignAggregations**<br /><br /> **CommitTransaction**<br /><br /> **復元**<br /><br /> **Synchronize**<br /><br /> **Insert**<br /><br /> **Update**<br /><br /> **Drop**<br /><br /> <br /><br /> 注: 読み取り専用に設定されているデータベースでは、セルの書き戻しは許可されていますが、変更はコミットできません。|  
|MDX ステートメント<br /><br /> <br /><br /> 注: これらのステートメントのいずれかを実行すると、エラーが発生します。|**COMMIT TRAN**<br /><br /> **CREATE SESSION CUBE**<br /><br /> **ALTER CUBE**<br /><br /> **ALTER DIMENSION**<br /><br /> **CREATE DIMENSION MEMBER**<br /><br /> **DROP DIMENSION MEMBER**<br /><br /> **ALTER DIMENSION**<br /><br /> <br /><br /> 注: Excel ユーザーは、ピボット テーブルのグループ化機能を使用できません。この機能は、 **CREATE SESSION CUBE** コマンドを使用して内部的に実装されているためです。|  
|DMX ステートメント<br /><br /> <br /><br /> 注: これらのステートメントのいずれかを実行すると、エラーが発生します。|**CREATE [SESSION] MINING STRUCTURE**<br /><br /> **ALTER MINING STRUCTURE**<br /><br /> **DROP MINING STRUCTURE**<br /><br /> **CREATE [SESSION] MINING MODEL**<br /><br /> **DROP MINING MODEL**<br /><br /> **IMPORT**<br /><br /> **SELECT INTO**<br /><br /> **INSERT**<br /><br /> **UPDATE**<br /><br /> **DELETE**|  
|バックグラウンド操作|データベースを変更するすべてのバックグラウンド処理は無効になっています。 これには、レイジー処理およびプロアクティブ キャッシュが含まれています。|  
  
## <a name="readwritemode-usage"></a>ReadWriteMode の使用方法  
 **ReadWriteMode** データベース プロパティは、 **Attach** データベース コマンドの一部として使用されます。 **Attach** コマンドを使うと、データベース プロパティに **ReadWrite** または **ReadOnly**を設定できます。 **ReadWriteMode** データベース プロパティの値は、読み取り専用として定義されているため、直接更新することはできません。 データベースは、 **ReadWriteMode** プロパティが **ReadWrite**に設定された状態で作成されます。 データベースを読み取り専用モードで作成することはできません。  
  
 **ReadWriteMode** データベース プロパティの **ReadWrite** と **ReadOnly**を切り替えるには、 **Detach/Attach** コマンド シーケンスを実行する必要があります。  
  
 **Attach**を除き、すべてのデータベース操作では、 **ReadWriteMode** データベース プロパティが現在の状態で維持されます。 たとえば、 **Alter**、 **Backup**、 **Restore**および **Synchronize** などの操作では、 **ReadWriteMode** 値が保持されます。  
  
> [!NOTE]  
>  ローカル キューブは、読み取り専用データベースから作成できます。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [アタッチし、Analysis Services データベースのデタッチ](../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [Analysis Services データベースを移動します。](../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)   
 [Detach 要素](../../analysis-services/xmla/xml-elements-commands/detach-element.md)   
 [Attach 要素](../../analysis-services/xmla/xml-elements-commands/attach-element.md)  
  
  
