---
title: "アーキテクチャ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/03/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: python
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: f9a7802848f5355b3bab8a45cd5d2f55b861bfe9
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2017
---
# <a name="architecture-overview-for-machine-learning-services-with-python"></a>Python の Machine Learning のサービスのアーキテクチャの概要

このトピックでは、Python を外部スクリプトの実行をサポートするデータベース エンジンと SQL Server での Python の相互運用性を有効にする新しいコンポーネントのセキュリティ モデルでは、コンポーネントを含む、SQL Server と統合する方法の概要を示します。 詳細については、リンク先のトピックを参照してください。

> [!IMPORTANT]
> Python のサポートは、SQL Server 2017 CTP 2.0 から使用可能です。 このプレリリース機能は変更されます。

## <a name="python-interoperability"></a>Python の相互運用性

SQL Server マシン ラーニング Services (In-database) は、Python の Anaconda ディストリビューション Python 3.5 ランタイムおよびインタープリターをインストールします。 これにより、標準の Python ソリューションとの互換性を近く完了します。 Python は、データベース操作が侵害されていないことを保証するために、SQL Server から別のプロセスで実行されます。

Python の SQL Server の相互作用の詳細については、次を参照してください[Python の相互運用性。](../../advanced-analytics/python/python-interoperability.md)

## <a name="components-that-support-python-integration"></a>Python の統合をサポートするコンポーネント

これで、SQL Server 2016 で導入された拡張機能フレームワークでは、新しい言語固有のコンポーネントの追加により、Python スクリプトの実行をサポートします。 これらのコンポーネントは、データ交換の速度を向上させ、セキュリティで保護された、パフォーマンスの高いプラットフォームを提供する外部スクリプトの実行中の圧縮を実行できます。

など、Python をサポートするコンポーネントの詳細については、[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]と PythonLauncher を参照してください[新しいコンポーネント](../../advanced-analytics/python/new-components-in-sql-server-to-support-python-integration.md)です。

## <a name="security"></a>Security

Python のタスクは、セキュリティと管理容易性を提供する、SQL Server プロセス外で実行します。

すべてのタスクは、ジョブ オブジェクトを Windows または SQL Server のセキュリティによって保護されます。 データは、テーブル、データベース、およびインスタンス レベルでの SQL Server のセキュリティを適用することで、コンプライアンスの境界内に保持されます。 データベース管理者は、Python のジョブを実行する、ユーザーが Python スクリプトの使用状況を監視および消費するリソースを表示する権限を持っているユーザーを制御できます。

詳細については、「 [Python のセキュリティ](../../advanced-analytics/python/security-overview-sql-server-python-services.md)

## <a name="resource-governance"></a>リソース管理:

SQL Server Enterprise Edition では、管理、および外部スクリプトの操作を使用して、R スクリプトと Python スクリプトを含むリソースの使用状況を監視するリソース ガバナーを使用できます。

詳細については、次を参照してください。 [R のリソース管理](../../advanced-analytics/r/resource-governance-for-r-services.md)です。

## <a name="next-steps"></a>次の手順

[T-SQL を使用して実行の Python](../tutorials/run-python-using-t-sql.md)
