---
title: "米国英語と英国英語に使用されるワード ブレーカーの変更 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: search
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-search
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b5d2177-db98-47f5-b32e-4b80a2f74ffe
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f6af23630a01f510b7e345cce694d5d675c95742
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="change-the-word-breaker-used-for-us-english-and-uk-english"></a>米国英語と英国英語に使用されるワード ブレーカーの変更
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、英語用のワード ブレーカーおよびステマーの新しいバージョン (バージョン 14.0.4999.1038) がインストールされて、前のバージョン (バージョン 12.0.6828.0) が置き換えられます。 新しいコンポーネントで変更された動作の詳細については、「 [フルテキスト検索の動作の変更](http://msdn.microsoft.com/library/573444e8-51bc-4f3d-9813-0037d2e13b8f)」を参照してください。 このトピックでは、これらのコンポーネントの新しいバージョンを前のバージョンに切り替えたり、前のバージョンから新しいバージョンに切り替えたりする方法について説明します。 クラスターのインストールでは、これらの変更を、すべてのプライマリ ノードとパッシブ ノードで行う必要があります。  
  
 前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、米国英語 (LCID 1033) と英国英語 (LCID 2057) に対し、異なる CLSID で表される異なるワード ブレーカーが使用されていました。 このリリースでは、次の表に示すように、両方の LCID で同じ CLSID を持つ同じコンポーネントが使用されます。  
  
|LCID (LCID)|以前のバージョンでインストールされたワード ブレーカー<br /><br /> バージョン 12.0.6828.0|以前のバージョンでインストールされたステマー|このバージョンでインストールされるワード ブレーカー<br /><br /> バージョン 14.0.4999.1038|このバージョンでインストールされるステマー|  
|----------|-------------------------------------------------------------------------|--------------------------------------------|-----------------------------------------------------------------------|---------------------------------------|  
|1033<br />(米国英語)|188D6CC5-CB03-4C01-912E-47D21295D77E|EEED4C20-7F1B-11CE-BE57-00AA0051FE20|9faed859-0b30-4434-ae65-412e14a16fb8|e1e5ef84-c4a6-4e50-8188-99aef3de2659|  
|2057<br />(英国英語)|173C97E2-AEBE-437C-9445-01B237ABF2F6|D99F7670-7F1A-11CE-BE57-00AA0051FE20|9faed859-0b30-4434-ae65-412e14a16fb8|e1e5ef84-c4a6-4e50-8188-99aef3de2659|  
  
 このトピックで説明するコンポーネントは、 `MSSQL\Binn` インスタンスの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フォルダーにインストールされる DLL ファイルです。 通常、完全なパスは `C:\Program Files\Microsoft SQL Server\<instance>\MSSQL\Binn`です。  
  
 ワード ブレーカーとステマーの詳細については、「 [検索用のワード ブレーカーとステミング機能の構成と管理](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)」を参照してください。  
  
## <a name="switching-from-the-current-english-word-breaker-to-the-previous-english-word-breakers"></a>現在の英語用ワード ブレーカーから前の英語用ワード ブレーカーへの切り替え  
  
#### <a name="to-switch-from-the-current-version-of-the-us-english-word-breaker-to-the-previous-version"></a>米国英語用のワード ブレーカーを現在のバージョンから前のバージョンに切り替えるには  
  
1.  レジストリで、**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID** ノードに移動します。  
  
2.  次の手順を使用して、LCID 1033 の前の米国英語用ワード ブレーカー インターフェイスおよびステマー インターフェイスに対応する COM ClassID の新しいキーを追加します。  
  
    1.  前のワード ブレーカー用に値が **{188D6CC5-CB03-4C01-912E-47D21295D77E}** の新しいキーを追加します。  
  
    2.  このキー値の [(既定)] のデータを **langwrbk.dll**に更新します。  
  
    3.  前のステマー用に値が **{EEED4C20-7F1B-11CE-BE57-00AA0051FE20}** の新しいキーを追加します。  
  
    4.  このキー値の [(既定)] のデータを **infosoft.dll** に更新します。  
  
3.  レジストリで、**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\enu** ノードに移動します。  
  
4.  **WBreakerClass** キー値を **{188D6CC5-CB03-4C01-912E-47D21295D77E}** に更新します。  
  
5.  **StemmerClass** キー値を **{EEED4C20-7F1B-11CE-BE57-00AA0051FE20}**に更新します。  
  
6.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を再起動します。  
  
#### <a name="to-switch-from-the-current-version-of-the-uk-english-word-breaker-to-the-previous-version"></a>英国英語用のワード ブレーカーを現在のバージョンから前のバージョンに切り替えるには  
  
1.  レジストリで、**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID** ノードに移動します。  
  
2.  次の手順を使用して、LCID 2057 の前の英国英語用ワード ブレーカー インターフェイスおよびステマー インターフェイスに対応する COM ClassID の新しいキーを追加します。  
  
    1.  前のワード ブレーカー用に値が **{173C97E2-AEBE-437C-9445-01B237ABF2F6}** の新しいキーを追加します。  
  
    2.  このキー値の [(既定)] のデータを **langwrbk.dll**に更新します。  
  
    3.  前のステマー用に値が **{D99F7670-7F1A-11CE-BE57-00AA0051FE20}** の新しいキーを追加します。  
  
    4.  このキー値の [(既定)] のデータを **infosoft.dll** に更新します。  
  
3.  レジストリで、**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\eng** ノードに移動します。  
  
4.  **WBreakerClass** キー値を **{173C97E2-AEBE-437C-9445-01B237ABF2F6}** に更新します。  
  
5.  **StemmerClass** キー値を **{D99F7670-7F1A-11CE-BE57-00AA0051FE20}**に更新します。  
  
6.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を再起動します。  
  
## <a name="switching-back-from-the-previous-english-word-breakers-to-the-current-english-word-breaker"></a>前の英語用ワード ブレーカーから現在の英語用ワード ブレーカーへの切り替え  
  
#### <a name="to-switch-back-from-the-previous-version-of-the-us-english-word-breaker-to-the-current-version"></a>米国英語用のワード ブレーカーを前のバージョンから現在のバージョンに切り替えるには  
  
1.  レジストリで、**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID** ノードに移動します。  
  
2.  次のキーが存在しない場合は、次の手順を使用して、LCID 1033 の現在の米国英語用ワード ブレーカー インターフェイスおよびステマー インターフェイスに対応する COM ClassID の新しいキーを追加します。  
  
    1.  現在のワード ブレーカー用に値が **{9faed859-0b30-4434-ae65-412e14a16fb8}** の新しいキーを追加します。  
  
    2.  このキー値の [(既定)] のデータを **MsWb7.dll**に更新します。  
  
    3.  現在のステマー用に値が **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** の新しいキーを追加します。  
  
    4.  このキー値の [(既定)] のデータを **MsWb7.dll** に更新します。  
  
3.  レジストリで、**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\eng** ノードに移動します。  
  
4.  **WBreakerClass** キー値を **{9faed859-0b30-4434-ae65-412e14a16fb8}** に更新します。  
  
5.  **StemmerClass** キー値を **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}**に更新します。  
  
6.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を再起動します。  
  
#### <a name="to-switch-back-from-the-previous-version-of-the-uk-english-word-breaker-to-the-current-version"></a>英国英語用のワード ブレーカーを前のバージョンから現在のバージョンに切り替えるには  
  
1.  レジストリで、**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID** ノードに移動します。  
  
2.  次のキーが存在しない場合は、次の手順を使用して、LCID 2057 の現在の英国英語用ワード ブレーカー インターフェイスおよびステマー インターフェイスに対応する COM ClassID の新しいキーを追加します。  
  
    1.  現在のワード ブレーカー用に値が **{9faed859-0b30-4434-ae65-412e14a16fb8}** の新しいキーを追加します。  
  
    2.  このキー値の [(既定)] のデータを **MsWb7.dll**に更新します。  
  
    3.  現在のステマー用に値が **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** の新しいキーを追加します。  
  
    4.  このキー値の [(既定)] のデータを **MsWb7.dll** に更新します。  
  
3.  レジストリで、**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\eng** ノードに移動します。  
  
4.  **WBreakerClass** キー値を **{9faed859-0b30-4434-ae65-412e14a16fb8}** に更新します。  
  
5.  **StemmerClass** キー値を **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}**に更新します。  
  
6.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を再起動します。  
  
## <a name="see-also"></a>参照  
 [検索で使用するワード ブレーカーを以前のバージョンに戻す](../../relational-databases/search/revert-the-word-breakers-used-by-search-to-the-previous-version.md)   
 [フルテキスト検索の動作の変更](http://msdn.microsoft.com/library/573444e8-51bc-4f3d-9813-0037d2e13b8f)  
  
  
