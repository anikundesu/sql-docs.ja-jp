---
title: "sp_dropmessage (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_dropmessage_TSQL
- sp_dropmessage
dev_langs: TSQL
helpviewer_keywords: sp_dropmessage
ms.assetid: 17287a15-cdde-43d1-bb18-9f920bc15db8
caps.latest.revision: "32"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f5673871097f702a8e370fefb4998b378af26d91
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spdropmessage-transact-sql"></a>sp_dropmessage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  インスタンスから指定したユーザー定義エラー メッセージを削除、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]です。 使用してユーザー定義メッセージを表示することができます、 **sys.messages**カタログ ビューです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dropmessage [ @msgnum = ] message_number  
    [ , [ @lang = ] 'language' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@msgnum =** ]*使用しました。*  
 削除するメッセージ番号を指定します。 *使用した*ユーザー定義のメッセージをメッセージの番号 50000 より大きい値を持つ必要があります。 *使用した*は**int**、既定値は NULL です。  
  
 [  **@lang =** ] **'***言語***'**  
 メッセージを削除する言語です。 場合**すべて**が指定されているすべての言語バージョン*使用した*削除されます。 *言語*は**sysname**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 [なし] :  
  
## <a name="permissions"></a>Permissions  
 メンバーシップが必要、 **sysadmin**と**serveradmin**固定サーバー ロール。  
  
## <a name="remarks"></a>解説  
 しない限り、**すべて**が指定されて*言語*、すべてのローカライズされた米国の前に、メッセージのバージョンを削除する必要がありますそのメッセージのすべてのローカライズ版を削除する必要があります。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-dropping-a-user-defined-message"></a>A. ユーザー定義メッセージを削除する  
 次の例は、数、ユーザー定義メッセージを削除`50001`から**sys.messages**です。  
  
```  
USE master;  
GO  
EXEC sp_dropmessage 50001;  
```  
  
### <a name="b-dropping-a-user-defined-message-that-includes-a-localized-version"></a>B. ローカライズ版を含むユーザー定義メッセージを削除する  
 次の例は、数、ユーザー定義メッセージを削除`60000`メッセージのローカライズされたバージョンを含むです。  
  
```  
USE master;  
GO  
  
-- Create a user-defined message in U.S. English  
EXEC sp_addmessage   
    @msgnum = 60000,  
    @severity = 16,  
    @msgtext = N'The item named %s already exists in %s.',   
    @lang = 'us_english';  
  
-- Create a localized version of the same message.  
EXEC sp_addmessage   
    @msgnum = 60000,  
    @severity = 16,  
    @msgtext = N'L''élément nommé %1! existe déjà dans %2!',  
    @lang = 'French';  
GO  
  
-- This statement will fail as long as the localized version  
-- of the message exists.  
EXEC sp_dropmessage 60000;  
GO  
  
-- This statement will drop the message.  
EXEC sp_dropmessage  
    @msgnum = 60000,  
    @lang = 'all';  
GO  
```  
  
### <a name="c-dropping-a-localized-version-of-a-user-defined-message"></a>C. ユーザー定義メッセージのローカライズ版を削除する  
 次の例は、ユーザー定義メッセージ数のローカライズ版を削除`60000`、メッセージ全体を削除しない限りです。  
  
```  
USE master;  
GO  
  
-- Create a user-defined message in U.S. English  
EXEC sp_addmessage   
    @msgnum = 60000,  
    @severity = 16,  
    @msgtext = N'The item named %s already exists in %s.',   
    @lang = 'us_english';  
  
-- Create a localized version of the same message.  
EXEC sp_addmessage   
    @msgnum = 60000,  
    @severity = 16,  
    @msgtext = N'L''élément nommé %1! existe déjà dans %2!',  
    @lang = 'French';  
GO  
-- This statement will remove only the localized version of the   
-- message.  
EXEC sp_dropmessage  
    @msgnum = 60000,  
    @lang = 'French';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [sp_addmessage &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md)   
 [sp_altermessage &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-altermessage-transact-sql.md)   
 [FORMATMESSAGE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/formatmessage-transact-sql.md)   
 [sys.messages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
