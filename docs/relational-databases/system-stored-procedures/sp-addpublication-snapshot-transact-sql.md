---
title: "sp_addpublication_snapshot (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_addpublication_snapshot_TSQL
- sp_addpublication_snapshot
helpviewer_keywords: sp_addpublication_snapshot
ms.assetid: 192b6214-df6e-44a3-bdd4-9d933a981619
caps.latest.revision: "39"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9de7dc82dd63e8ea6b23d9c561a8fd7ea83da435
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spaddpublicationsnapshot-transact-sql"></a>sp_addpublication_snapshot (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたパブリケーションのスナップショット エージェントを作成します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
> [!IMPORTANT]  
>  リモート ディストリビューターを使用するパブリッシャーを構成する場合は、 *job_login* および *job_password*を含むすべてのパラメーターに指定された値がディストリビューターにプレーン テキストとして送信されます。 このストアド プロシージャを実行する前に、パブリッシャーとリモート ディストリビューターの間の接続を暗号化する必要があります。 詳細については、「[データベース エンジンへの暗号化接続の有効化 &#40;SQL Server 構成マネージャー&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addpublication_snapshot [ @publication= ] 'publication'  
    [ , [ @frequency_type= ] frequency_type ]  
    [ , [ @frequency_interval= ] frequency_interval ]  
    [ , [ @frequency_subday= ] frequency_subday ]  
    [ , [ @frequency_subday_interval= ] frequency_subday_interval ]  
    [ , [ @frequency_relative_interval= ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor= ] frequency_recurrence_factor ]  
    [ , [ @active_start_date= ] active_start_date ]  
    [ , [ @active_end_date= ] active_end_date ]  
    [ , [ @active_start_time_of_day= ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day= ] active_end_time_of_day ]  
    [ , [ @snapshot_job_name = ] 'snapshot_agent_name' ]  
    [ , [ @publisher_security_mode = ] publisher_security_mode ]  
    [ , [ @publisher_login = ] 'publisher_login' ]  
    [ , [ @publisher_password = ] 'publisher_password' ]   
    [ , [ @job_login = ] 'job_login' ]  
    [ , [ @job_password = ] 'job_password' ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@publication=**] **'***パブリケーション***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@frequency_type=**] *frequency_type*  
 スナップショット エージェントの実行頻度を指定します。 *frequency_type*は**int**値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|1 回のみ|  
|**4** (既定値)|毎日|  
|**8**|毎週|  
|**16**|毎月|  
|**32**|月単位に frequency_interval で示される間隔|  
|**64**|ときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントが起動します。|  
|**128**|コンピューターがアイドル状態のときに実行|  
  
 [  **@frequency_interval=**] *frequency_interval*  
 設定した頻度に適用する値は、 *frequency_type*です。 *frequency_interval*は**int**値は次のいずれかを指定できます。  
  
|frequency_type の値|frequency_interval への影響|  
|------------------------------|-----------------------------------|  
|**1**|*frequency_interval*は使用されません。|  
|**4** (既定値)|各*frequency_interval*既定値は日単位、日。|  
|**8**|*frequency_interval*は、次の 1 つ以上 (と組み合わせて、 [&#124;です。(ビットごとの OR)](../../t-sql/language-elements/bitwise-or-transact-sql.md)論理演算子)。<br /><br /> **1**日曜日 &#124;です。<br /><br /> **2** = 月曜日 &#124;です。<br /><br /> **4** = 火曜日 &#124;です。<br /><br /> **8** = 水曜日 &#124;です。<br /><br /> **16** = 木曜日 &#124;です。<br /><br /> **32** = 金曜日 &#124;です。<br /><br /> **64** = 土曜日|  
|**16**|*Frequency_interval*します月の日です。|  
|**32**|*frequency_interval*は、次のいずれか。<br /><br /> **1**日曜日 &#124;です。<br /><br /> **2** = 月曜日 &#124;です。<br /><br /> **3** = 火曜日 &#124;です。<br /><br /> **4** = 水曜日 &#124;です。<br /><br /> **5** = 木曜日 &#124;です。<br /><br /> **6** = 金曜日 &#124;です。<br /><br /> **7** = 土曜日 &#124;です。<br /><br /> **8** = 日 &#124;です。<br /><br /> **9** = 平日 &#124;です。<br /><br /> **10** = 土日|  
|**64**|*frequency_interval*は使用されません。|  
|**128**|*frequency_interval*は使用されません。|  
  
 [  **@frequency_subday=**] *frequency_subday*  
 単位です*freq_subday_interval*です。 *frequency_subday*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|1 回。|  
|**2**|第 2 週|  
|**4** (既定値)|Minute|  
|**8**|Hour|  
  
 [  **@frequency_subday_interval=**] *frequency_subday_interval*  
 間隔は、 *frequency_subday*です。 *frequency_subday_interval*は**int**5、既定値は 5 分を意味します。  
  
 [  **@frequency_relative_interval=**] *frequency_relative_interval*  
 スナップショット エージェントを実行する日付を指定します。 *frequency_relative_interval*は**int**、既定値は 1 です。  
  
 [  **@frequency_recurrence_factor=**] *frequency_recurrence_factor*  
 によって使用される定期実行係数*frequency_type*です。 *frequency_recurrence_factor*は**int**、既定値は 0 です。  
  
 [  **@active_start_date=**] *active_start_date*  
 スナップショット エージェントを最初にスケジュール設定する日付を、YYYYMMDD 形式で指定します。 *active_start_date*は**int**、既定値は 0 です。  
  
 [  **@active_end_date=**] *active_end_date*  
 スナップショット エージェントのスケジュール設定を停止する日付を、YYYYMMDD 形式で指定します。 *active_end_date*は**int**99991231、既定値は 9999 年 12 月 31 日です。  
  
 [  **@active_start_time_of_day=**] *active_start_time_of_day*  
 スナップショット エージェントを最初にスケジュール設定する時刻を HHMMSS 形式で指定します。 *active_start_time_of_day*は**int**、既定値は 0 です。  
  
 [  **@active_end_time_of_day=**] *active_end_time_of_day*  
 スナップショット エージェントのスケジュール設定を停止する時刻を HHMMSS 形式で指定します。 *active_end_time_of_day*は**int**、既定値は 235959、午後 11時 59分: 59 を意味 24 時間制です。  
  
 [  **@snapshot_job_name =** ] **'***snapshot_agent_name***'**  
 既存のジョブが使用されている場合、既存のスナップショット エージェントのジョブ名を指定します。 *snapshot_agent_name*は**nvarchar (100)**で、既定値は NULL です。 このパラメーターは内部でのみ使用するため、新しいパブリケーションを作成するときに指定する必要はありません。 場合*snapshot_agent_name*が指定すると、 *job_login*と*job_password* NULL にする必要があります。  
  
 [  **@publisher_security_mode** =] *publisher_security_mode*  
 パブリッシャーへの接続時にエージェントが使用するセキュリティ モードを指定します。 *publisher_security_mode*は**smallint**、既定値は 1 です。 **0**指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証、および**1** Windows 認証を指定します。 値**0**を指定する必要があります以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
 [  **@publisher_login** =] **'***publisher_login***'**  
 パブリッシャーへの接続時に使用するログインを指定します。 *publisher_login*は**sysname**、既定値は NULL です。 *publisher_login*場合に指定する必要があります*publisher_security_mode*は**0**します。 場合*publisher_login* null と*publisher_security_mode*は**1**で指定した Windows アカウント*job_login*使用されますパブリッシャーへの接続時に  
  
 [  **@publisher_password** =] **'***publisher_password***'**  
 パブリッシャーへの接続時に使用するパスワードを指定します。 *publisher_password*は**sysname**、既定値は NULL です。  
  
> [!IMPORTANT]  
>  スクリプト ファイルに認証情報を格納しないでください。 セキュリティを強化するため、実行時にログイン名とパスワードを指定することをお勧めします。  
  
 [  **@job_login** =] **'***job_login***'**  
 エージェントを実行する Windows アカウント用のログインを指定します。 *job_login*は**nvarchar (257)**、既定値は NULL です。 この Windows アカウントはディストリビューターへのエージェント接続で常に使用されます。 新しいスナップショット エージェント ジョブを作成するときにはこのパラメーターを指定する必要があります。  
  
> [!NOTE]  
>  非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーの場合、こので指定された同じログインをする必要があります[sp_adddistpublisher &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md).  
  
 [  **@job_password** =] **'***job_password***'**  
 エージェントを実行する Windows アカウント用のパスワードを指定します。 *job_password*は**sysname**、既定値はありません。 新しいスナップショット エージェント ジョブを作成するときにはこのパラメーターを指定する必要があります。  
  
> [!IMPORTANT]  
>  スクリプト ファイルに認証情報を格納しないでください。 セキュリティを強化するため、実行時にログイン名とパスワードを指定することをお勧めします。  
  
 [  **@publisher** =] **'***パブリッシャー***'**  
 指定以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  *パブリッシャー*でスナップショット エージェントを作成するときに使用しないで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_addpublication_snapshot**はスナップショット レプリケーション、トランザクション レプリケーション、およびマージ レプリケーションで使用します。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_AddTranPub](../../relational-databases/replication/codesnippet/tsql/sp-addpublication-snapsh_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_addpublication_snapshot**です。  
  
## <a name="see-also"></a>参照  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [スナップショットの作成および適用](../../relational-databases/replication/create-and-apply-the-snapshot.md)   
 [sp_addpublication &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)   
 [sp_changepublication_snapshot &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md)   
 [sp_startpublication_snapshot &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-startpublication-snapshot-transact-sql.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
