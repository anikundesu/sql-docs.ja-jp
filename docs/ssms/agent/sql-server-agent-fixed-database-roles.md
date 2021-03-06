---
title: "SQL Server エージェントの固定データベース ロール | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- roles [SQL Server], SQL Server Agent
- SQL Server Agent, roles
- SQLAgentUserRole database role
- SQLAgentReaderRole database role
- multiple roles
- security [SQL Server Agent], fixed database roles
- fixed database roles [SQL Server]
- SQLAgentOperatorRole database role
ms.assetid: 719ce56b-d6b2-414a-88a8-f43b725ebc79
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: cc6c25e52402bcf7e4d1a3a9899e9b3ce6449b73
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="sql-server-agent-fixed-database-roles"></a>SQL Server エージェントの固定データベース ロール
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] には、次の **msdb** データベースの固定データベース ロールが用意されています。これらのロールを使用することで、管理者は [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントへのアクセスをより細かく制御できます。 特権レベルの低いロールから順に、次に示します。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
上記のどのロールのメンバーでもないユーザーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]に接続しても、オブジェクト エクスプローラーには **[SQL Server エージェント]** ノードは表示されません。 **エージェントを使用するユーザーは、上記のいずれかの固定データベース ロールのメンバーであるか、または固定サーバー ロール** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] のメンバーである必要があります。  
  
## <a name="permissions-of-sql-server-agent-fixed-database-roles"></a>SQL Server エージェントの固定データベース ロールの権限  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントのデータベース ロールの各権限の相互関係は、同心構造になっています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント オブジェクト (警告、オペレーター、ジョブ、スケジュール、プロキシなど) に対して、高いレベルの特権を持つロールは、低いレベルの特権を持つロールの権限を継承します。 たとえば、最も特権レベルの低い **SQLAgentUserRole** のメンバーが proxy_A へのアクセスを許可された場合、 **SQLAgentReaderRole** および **SQLAgentOperatorRole** の両方のメンバーは、proxy_A へのアクセスが明示的に許可されていなくても、このプロキシへのアクセス権が自動的に与えられていることになります。 これは、セキュリティに影響することがあります。セキュリティ上の影響については、次のセクションの各ロールの説明に記載します。  
  
### <a name="sqlagentuserrole-permissions"></a>SQLAgentUserRole の権限  
**SQLAgentUserRole** には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントの固定データベース ロールのうち、最も低い特権レベルが設定されています。 オペレーター、ローカル ジョブ、ジョブ スケジュールのみに対する権限があります。 **SQLAgentUserRole** のメンバーは、所有しているローカル ジョブおよびジョブ スケジュールのみに対する権限を持っています。 このメンバーが、マルチサーバー ジョブ (マスター サーバーと対象サーバーのジョブ) を使用することはできません。また、ジョブの所有権を変更して、所有していないジョブへのアクセス権を得ることもできません。 **SQLAgentUserRole** のメンバーは、 **の** [ジョブ ステップのプロパティ] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]ダイアログ ボックスでのみ、使用できるプロキシのリストを表示できます。 **SQLAgentUserRole** のメンバーに対しては、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] オブジェクト エクスプローラーには **[ジョブ]**ノードだけが表示されます。  
  
> [!IMPORTANT]  
> ****[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]**エージェント データベース ロール**のメンバーに対してプロキシへのアクセスを許可する前に、セキュリティ上の影響について検討してください。 **SQLAgentReaderRole** および **SQLAgentOperatorRole** は、自動的に **SQLAgentUserRole**のメンバーになります。 つまり、 **SQLAgentReaderRole** および **SQLAgentOperatorRole** のメンバーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SQLAgentUserRole **に許可されたすべての** エージェント プロキシにアクセスし、これらのプロキシを使用できることになります。  
  
次の表に、 **エージェント オブジェクトに対する** SQLAgentUserRole [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] の権限の概要を示します。  
  
|操作|演算子|ローカル ジョブ<br /><br />(所有しているジョブのみ)|ジョブ スケジュール<br /><br />(所有しているスケジュールのみ)|プロキシ|  
|----------|-------------|-----------------------------------|-------------------------------------------|-----------|  
|作成/変更/削除|いいえ|可<br /><br />ジョブの所有権は変更できません。|可|いいえ|  
|リストの表示 (列挙)|可<br /><br />**sp_notify_operator** および Management Studio の **[ジョブのプロパティ]** ダイアログ ボックスで使用できるオペレーターのリストを取得できます。|可|可|可<br /><br />プロキシのリストは、Management Studio の **[ジョブ ステップのプロパティ]** ダイアログ ボックスにのみ表示できます。|  
|有効化/無効化|いいえ|はい|可|適用なし|  
|プロパティの表示|いいえ|はい|可|いいえ|  
|実行/停止/開始|適用なし|可|適用なし|適用なし|  
|ジョブ履歴の表示|適用なし|可|適用なし|適用なし|  
|ジョブ履歴の削除|適用なし|いいえ<br /><br />所有しているジョブのジョブ履歴を削除するには、 **SQLAgentUserRole** のメンバーは、 **sp_purge_jobhistory** に対する EXECUTE 権限が明示的に許可されている必要があります。 他のジョブのジョブ履歴は削除できません。|適用なし|適用なし|  
|アタッチ/デタッチ|適用なし|適用なし|可|適用なし|  
  
### <a name="sqlagentreaderrole-permissions"></a>SQLAgentReaderRole の権限  
**SQLAgentReaderRole** には、すべての **SQLAgentUserRole** の権限、および使用できるマルチサーバー ジョブのリスト、ジョブのプロパティ、およびジョブの履歴を表示する権限が含まれています。 このロールのメンバーは、所有しているジョブとジョブ スケジュールだけでなく、使用できるすべてのジョブとジョブ スケジュール、およびそのプロパティのリストを表示することもできます。 **SQLAgentReaderRole** のメンバーは、ジョブの所有権を変更して、所有していないジョブへのアクセス権を得ることはできません。 **SQLAgentReaderRole** のメンバーに対しては、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] オブジェクト エクスプローラーには **[ジョブ]**ノードだけが表示されます。  
  
> [!IMPORTANT]  
> ****[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]**エージェント データベース ロール**のメンバーに対してプロキシへのアクセスを許可する前に、セキュリティ上の影響について検討してください。 **SQLAgentReaderRole** のメンバーは、自動的に **SQLAgentUserRole**のメンバーになります。 つまり、 **SQLAgentReaderRole** のメンバーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SQLAgentUserRole **に対して許可されたすべての** エージェント プロキシにアクセスし、これらのプロキシを使用できることになります。  
  
次の表に、 **エージェント オブジェクトに対する** SQLAgentReaderRole [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] の権限の概要を示します。  
  
|操作|演算子|ローカル ジョブ|マルチサーバー ジョブ|ジョブ スケジュール|プロキシ|  
|----------|-------------|--------------|--------------------|-----------------|-----------|  
|作成/変更/削除|いいえ|可 (所有しているジョブのみ)<br /><br />ジョブの所有権は変更できません。|いいえ|可 (所有しているスケジュールのみ)|いいえ|  
|リストの表示 (列挙)|可<br /><br />**sp_notify_operator** および Management Studio の **[ジョブのプロパティ]** ダイアログ ボックスで使用できるオペレーターのリストを取得できます。|可|可|可|可<br /><br />プロキシのリストは、Management Studio の **[ジョブ ステップのプロパティ]** ダイアログ ボックスにのみ表示できます。|  
|有効化/無効化|いいえ|可 (所有しているジョブのみ)|いいえ|可 (所有しているスケジュールのみ)|適用なし|  
|プロパティの表示|いいえ|はい|可|可|いいえ|  
|プロパティの編集|いいえ|可 (所有しているジョブのみ)|いいえ|可 (所有しているスケジュールのみ)|いいえ|  
|実行/停止/開始|適用なし|可 (所有しているジョブのみ)|いいえ|適用なし|適用なし|  
|ジョブ履歴の表示|適用なし|可|可|適用なし|適用なし|  
|ジョブ履歴の削除|適用なし|いいえ<br /><br />所有しているジョブのジョブ履歴を削除するには、 **SQLAgentReaderRole** のメンバーは、 **sp_purge_jobhistory** に対する EXECUTE 権限が明示的に許可されている必要があります。 他のジョブのジョブ履歴は削除できません。|いいえ|適用なし|適用なし|  
|アタッチ/デタッチ|適用なし|適用なし|適用なし|可 (所有しているスケジュールのみ)|適用なし|  
  
### <a name="sqlagentoperatorrole-permissions"></a>SQLAgentOperatorRole の権限  
**SQLAgentOperatorRole** には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントの固定データベース ロールのうち、最も高いレベルの特権が設定されています。 これには、 **SQLAgentUserRole** および **SQLAgentReaderRole**のすべての権限が含まれています。 このロールのメンバーは、オペレーターおよびプロキシのプロパティを表示することも、サーバー上で使用できるプロキシおよび警告を列挙することもできます。  
  
**SQLAgentOperatorRole** のメンバーは、ローカル ジョブおよびスケジュールに関する追加の権限を持っています。 すべてのローカル ジョブを実行、停止、または開始したり、サーバー上のローカル ジョブのジョブ履歴を削除できます。 また、サーバー上のすべてのローカル ジョブおよびスケジュールを、有効または無効にすることもできます。 ローカル ジョブまたはスケジュールを有効または無効にするには、このロールのメンバーはストアド プロシージャ **sp_update_job** および **sp_update_schedule**を使用する必要があります。 **SQLAgentOperatorRole** のメンバーは、ジョブまたはスケジュールの名前か ID を指定するパラメーターと **@enabled** パラメーターのみを指定できます。 他のパラメーターを指定すると、ストアド プロシージャの実行は失敗します。 **SQLAgentOperatorRole** のメンバーは、ジョブの所有権を変更して、所有していないジョブへのアクセス権を得ることはできません。  
  
**SQLAgentOperatorRole**のメンバーに対しては、 **オブジェクト エクスプローラーには**[ジョブ] **ノード、**[警告] **ノード、** [オペレーター] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] ノード、および **[プロキシ]**ノードのみが表示されます。 このロールのメンバーに表示されないのは、 **[エラー ログ]** ノードだけです。  
  
> [!IMPORTANT]  
> ****[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]**エージェント データベース ロール**のメンバーに対してプロキシへのアクセスを許可する前に、セキュリティ上の影響について検討してください。 **SQLAgentOperatorRole** のメンバーは、自動的に **SQLAgentUserRole** および **SQLAgentReaderRole**のメンバーになります。 つまり、 **SQLAgentOperatorRole** のメンバーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SQLAgentUserRole **または** SQLAgentReaderRole **に対して許可されたすべての** エージェント プロキシにアクセスし、これらのプロキシを使用できることになります。  
  
次の表に、 **エージェント オブジェクトに対する** SQLAgentOperatorRole [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] の権限の概要を示します。  
  
|操作|オブジェクト エクスプローラーには|演算子|ローカル ジョブ|マルチサーバー ジョブ|ジョブ スケジュール|プロキシ|  
|----------|----------|-------------|--------------|--------------------|-----------------|-----------|  
|作成/変更/削除|いいえ|いいえ|可 (所有しているジョブのみ)<br /><br />ジョブの所有権は変更できません。|いいえ|可 (所有しているスケジュールのみ)|いいえ|  
|リストの表示 (列挙)|可|可<br /><br />**sp_notify_operator** および Management Studio の **[ジョブのプロパティ]** ダイアログ ボックスで使用できるオペレーターのリストを取得できます。|可|可|可|可|  
|有効化/無効化|いいえ|いいえ|可<br /><br />**SQLAgentOperatorRole** のメンバーは、ストアド プロシージャ **sp_update_job** を使用し、 **@enabled** および **@job_id** (または **@job_name**) パラメーターの値を指定することにより、所有していないローカル ジョブを有効または無効にできます。 このロールのメンバーが、このストアド プロシージャに対して他のパラメーターを指定した場合、プロシージャの実行は失敗します。|いいえ|可<br /><br />**SQLAgentOperatorRole** のメンバーは、ストアド プロシージャ **sp_update_schedule** を使用し、 **@enabled** および **@schedule_id** (または **@name**) パラメーターの値を指定することにより、所有していないローカル ジョブを有効または無効にできます。 このロールのメンバーが、このストアド プロシージャに対して他のパラメーターを指定した場合、プロシージャの実行は失敗します。|適用なし|  
|プロパティの表示|可|可|可|可|可|可|  
|プロパティの編集|いいえ|いいえ|可 (所有しているジョブのみ)|いいえ|可 (所有しているスケジュールのみ)|いいえ|  
|実行/停止/開始|適用なし|適用なし|可|いいえ|適用なし|適用なし|  
|ジョブ履歴の表示|適用なし|適用なし|可|可|適用なし|適用なし|  
|ジョブ履歴の削除|適用なし|適用なし|可|いいえ|適用なし|適用なし|  
|アタッチ/デタッチ|適用なし|適用なし|適用なし|適用なし|可 (所有しているスケジュールのみ)|適用なし|  
  
## <a name="assigning-users-multiple-roles"></a>ユーザーへの複数のロールの割り当て  
固定サーバー ロール **sysadmin** のメンバーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントのすべての機能にアクセスできます。 **sysadmin** ロールのメンバーではないが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントの複数の固定データベース ロールのメンバーであるユーザーの場合、これらのロールの同心構造権限モデルについて覚えておくことが重要です。 特権レベルの高いロールには常に、そのロールよりも特権レベルが低いロールの権限がすべて含まれているため、複数のロールのメンバーであるユーザーは、そのユーザーがメンバーとして属しているロールの中で、最も特権レベルの高いロールに関連付けられた権限を自動的に持っていることになります。  
  
## <a name="see-also"></a>参照  
[SQL Server エージェントのセキュリティの実装](../../ssms/agent/implement-sql-server-agent-security.md)  
[sp_update_job (Transact-SQL)](http://msdn.microsoft.com/en-us/cbdfea38-9e42-47f3-8fc8-5978b82e2623)  
[sp_update_schedule (Transact-SQL)](http://msdn.microsoft.com/en-us/97b3119b-e43e-447a-bbfb-0b5499e2fefe)  
[sp_notify_operator (Transact-SQL)](http://msdn.microsoft.com/en-us/c440f5c9-9884-4196-b07c-55d87afb17c3)  
[sp_purge_jobhistory (Transact-SQL)](http://msdn.microsoft.com/en-us/237f9bad-636d-4262-9bfb-66c034a43e88)  
  
