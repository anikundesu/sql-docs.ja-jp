---
title: "サービス プロバイダーとコンポーネント |Microsoft ドキュメント"
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
- OLE DB providers [ADO]
- ADO, OLE DB providers
- service providers [ADO]
ms.assetid: 1fd7a374-587b-4ca9-9204-3a4019b67a71
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d44d3ce48da69c734b381058637b15b7afd0736c
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="service-providers-and-components"></a>サービス プロバイダーとコンポーネント
サービス プロバイダーは、データ ストアでネイティブにサポートされていない拡張インターフェイスを実装するデータ プロバイダーの機能を拡張するコンポーネントです。  
  
 Universal Data Access の提供、*コンポーネント アーキテクチャ*低機能のストアの上にデータベースの機能、または「サービス」の個別のセットを実装する、特殊化された個々 のコンポーネントをことができます。 したがって、独自の拡張機能の実装を提供するには、各データ ストアまたはデータベースの機能を内部的に実装する汎用アプリケーションの強制ではなくサービス コンポーネントを提供任意のアプリケーションができる共通の実装任意のデータ ストアにアクセスするときに使用します。 一部の機能が実装されるネイティブ データ ストアと汎用コンポーネントを介してによってファクトは、アプリケーションに対して透過的です。  
  
 たとえば、カーソル エンジンなど[for OLE DB カーソル サービス](http://msdn.microsoft.com/en-us/57638feb-4ecd-4051-becb-8f828d21cf44)、スクロール可能なデータを生成するために、シーケンシャル、前方参照専用のデータ ストアからデータを使用できるサービス コンポーネントです。 ADO でよく使用されるその他のサービス プロバイダーが含まれて、 [Microsoft OLE DB Persistence Provider (ADO サービス プロバイダー)](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md) (データ ファイルに保存する)、用、 [Microsoft Data Shaping Service for OLE DB (ADO サービス プロバイダー)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) (の階層**レコード セット**)、および[Microsoft OLE DB のリモート処理のプロバイダー (ADO サービス プロバイダー)](../../../ado/guide/appendixes/microsoft-ole-db-remoting-provider-ado-service-provider.md) (リモート コンピューター上のデータ プロバイダーの呼び出し) 用です。  
  
 サービスとデータ プロバイダーの詳細については、次を参照してください。[付録 a: プロバイダー](../../../ado/guide/appendixes/appendix-a-providers.md)です。
