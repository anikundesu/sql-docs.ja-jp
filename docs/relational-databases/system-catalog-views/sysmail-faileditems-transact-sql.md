---
title: "sysmail_faileditems (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysmail_faileditems
- sysmail_faileditems_TSQL
dev_langs: TSQL
helpviewer_keywords: sysmail_faileditems database mail view
ms.assetid: a31562c5-358e-4cfc-a72d-b3faccc53851
caps.latest.revision: "18"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9872591d38bfedcd0b6c4e0f28a7922ace26b849
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysmailfaileditems-transact-sql"></a>sysmail_faileditems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース メール メッセージごとに 1 行が含まれています、**失敗**状態です。 このビューは、正しく送信されなかったメッセージを特定するときに使用できます。  
  
 データベース メールで処理されるすべてのメッセージを表示する[sysmail_allitems (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sysmail-allitems-transact-sql.md). 未送信のメッセージだけを表示する[sysmail_unsentitems (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sysmail-unsentitems-transact-sql.md). 送信されたメッセージのみを表示する[sysmail_sentitems (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sysmail-sentitems-transact-sql.md). 電子メールの添付ファイルを表示する[sysmail_mailattachments (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sysmail-mailattachments-transact-sql.md).  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**mailitem_id**|**int**|メール キュー内のメール アイテムの識別子。|  
|**profile_id**|**int**|メッセージの送信に使用されたプロファイルの識別子。|  
|**受信者**|**varchar(max)**|メッセージ受信者の電子メール アドレス。|  
|**@copy_recipients**|**varchar(max)**|CC としてメッセージのコピーを受け取る受信者の電子メール アドレス。|  
|**@blind_copy_recipients**|**varchar(max)**|BCC としてメッセージのコピーを受け取る受信者の電子メール アドレス。この受信者の名前は、メッセージ ヘッダーには表示されません。|  
|**件名**|**nvarchar(510)**|メッセージの件名。|  
|**本文**|**varchar(max)**|メッセージの本文。|  
|**body_format**|**varchar (20)**|メッセージの本文の書式。 可能な値は TEXT と HTML です。|  
|**重要度**|**varchar (6)**|**重要度**メッセージのパラメーターです。|  
|**小文字の区別**|**varchar (12)**|**感度**メッセージのパラメーターです。|  
|**@file_attachments**|**varchar(max)**|電子メール メッセージに添付されたファイル名の、セミコロン区切りの一覧。|  
|**Attachment_encoding**|**varchar (20)**|添付ファイルの種類。|  
|**Query**|**varchar(max)**|メール プログラムによって実行されたクエリ。|  
|**@execute_query_database**|**sysname**|メール プログラムによってクエリが実行されたデータベース コンテキスト。|  
|**attach_query_result_as_file**|**bit**|値が 0 の場合、クエリの結果が電子メール メッセージ本文内に取り込まれ、本文内容の後に追加されていることを示します。 値が 1 の場合、結果が添付ファイルとして返されたことを示します。|  
|**query_result_header**|**bit**|値が 1 の場合、クエリの結果に列のヘッダーが含まれていることを示します。 値が 0 の場合、クエリの結果に列のヘッダーが含まれていないことを示します。|  
|**query_result_width**|**int**|**Query_result_width**メッセージのパラメーターです。|  
|**@query_result_separator**|**char (1)**|クエリの出力で列の区切りに使用された文字。|  
|**exclude_query_output**|**bit**|**Exclude_query_output**メッセージのパラメーターです。 詳細については、次を参照してください。 [sp_send_dbmail &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md).|  
|**append_query_error**|**bit**|**Append_query_error**メッセージのパラメーターです。 0 は、クエリにエラーがあった場合、データベース メールで電子メール メッセージが送信されないことを示します。|  
|**send_request_date**|**datetime**|メッセージがメール キューに挿入された日時。|  
|**send_request_user**|**sysname**|メッセージを送信したユーザー。 これはメッセージの [差出人] フィールドに表示されるユーザーではなく、データベース メール プロシージャのユーザー コンテキストです。|  
|**sent_account_id**|**int**|メッセージの送信に使用されたデータベース メール アカウントの識別子。 このビューでは常に NULL になります。|  
|**sent_status**|**varchar (8)**|メールの状態。 常に**失敗**このビューにします。|  
|**sent_date**|**datetime**|メッセージがメール キューから削除された日時。|  
|**last_mod_date**|**datetime**|行が最後に変更された日時。|  
|**last_mod_user**|**sysname**|行を最後に変更したユーザー。|  
  
## <a name="remarks"></a>解説  
 使用して、 **sysmail_faileditems**をデータベース メールで送信されていないどのメッセージを表示するビュー。 データベース メールのトラブルシューティングを行うとき、このビューでは送信されなかったメッセージの属性を確認できるので、問題の性質を特定するのに役立ちます。 表示するには、失敗の理由で失敗したメッセージのエントリを参照してください、 [sysmail_event_log &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sysmail-event-log-transact-sql.md)ビュー。  
  
## <a name="permissions"></a>Permissions  
 付与された**sysadmin**固定サーバー ロールと**databasemailuserrole**データベース ロール。 メンバーによって実行されると、 **sysadmin**固定サーバー ロール、このビューはすべて失敗したメッセージを表示します。 その他のユーザーの場合は、送信が失敗したメッセージのうち、自分が送信したものだけを確認できます。  
  
  
