---
title: "時間 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 6/7/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- time_TSQL
- time
dev_langs: TSQL
helpviewer_keywords:
- time [SQL Server], data types
- time [SQL Server]
- date and time [SQL Server], time
- data types [SQL Server], date and time
- time data type [SQL Server]
ms.assetid: 30a6c681-8190-48e4-94d0-78182290a402
caps.latest.revision: "45"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 4a5a46eee481e9da3f388f88e982d705dbe150ea
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="time-transact-sql"></a>time (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  1 日の時刻を定義します。 時刻は 24 時間形式でタイム ゾーンは認識されません。  
  
  > [!NOTE]  
  > Informatica コネクタを使用して PDW 顧客の Informatica の情報を提供します。 
  
## <a name="time-description"></a>time の説明  
  
|プロパティ|値|  
|--------------|-----------|  
|構文|**時間**[(*小数部の 2 番目のスケール*)]|  
|使用方法|宣言@MyTime **time (7)**<br /><br /> Table1 のテーブルの作成 (Column1 **time (7)** )|  
|*秒の小数部の桁数*|秒の小数点以下の有効桁数を指定します。<br /><br /> 0 ～ 7 の整数を指定できます。 Informatica の 0 から 3 の整数を指定できます。<br /><br /> 既定の小数部のスケールは、7 (100 ns) です。|  
|既定の文字列リテラル形式<br /><br /> (下位のクライアントに使用)|Informatica の hh:mm:ss [.nnnnnnn])<br /><br /> 詳細については、これに続く「ダウンレベルのクライアントの旧バージョンとの互換性」セクションを参照してください.|  
|範囲|00:00:00.0000000 から 23:59:59.9999999 (00:00:00.000 Informatica の 23:59:59.999 経由)|  
|要素範囲|hh は、0 ～ 23 の時を表す 2 桁の数字です。<br /><br /> mm は、0 ～ 59 の分を表す 2 桁の数字です。<br /><br /> ss は、0 ～ 59 の秒を表す 2 桁の数字です。<br /><br /> n\*0 ~ 9999999、秒の小数部を表す、0 ~ 7 桁の数字です。 Informatica での n\* 0 から 999 まで 3 桁の数字のゼロです。|  
|文字長|最大 16 (hh:mm:ss.nnnnnnn) に 8 文字以上 (hh:mm:ss)。 Informatica、最大値は 12 (hh:mm:ss.nnn) です。|  
|有効桁数、小数点以下桁数<br /><br /> (ユーザーは小数点以下桁数のみ指定)|次の表を参照してください。|  
|ストレージのサイズ|既定では 5 バイト固定 (秒部分の既定の有効桁数は 100ns) です。 Informatica、既定値は 4 バイト、小数部を 1 ミリ秒の既定値は、固定有効桁数を 2 番目です。|  
|精度|100 ナノ秒 (Informatica で 1 ミリ秒)。|  
|既定値|00:00:00<br /><br /> この値はの追加された時刻の部分からの暗黙的な変換の使用**日付**に**datetime2**または**datetimeoffset**です。|  
|ユーザー定義の 1 秒未満の秒の有効桁数|可|  
|タイム ゾーン オフセットへの対応と保持|不可|  
|夏時間への対応|不可|  
  
|指定した小数点以下桁数|結果 (有効桁数、小数点以下桁数)|列長 (バイト単位)|1 秒未満の<br /><br /> seconds<br /><br /> 有効桁数 (precision)|  
|---------------------|---------------------------------|-----------------------------|------------------------------------------|  
|**time**|(16,7) [(12,3) で Informatica]|5 (Informatica では 4)|7 (Informatica の 3)|  
|**time(0)**|(8,0)|3|0-2|  
|**time(1)**|(10,1)|3|0-2|  
|**time(2)**|(11,2)|3|0-2|  
|**time(3)**|(12,3)|4|3-4|  
|**time(4)**<br /><br /> Informatica でサポートされていません。|(13,4)|4|3-4|  
|**time(5)**<br /><br /> Informatica でサポートされていません。|(14,5)|5|5-7|  
|**time(6)**<br /><br /> Informatica でサポートされていません。|(15,6)|5|5-7|  
|**time(7)**<br /><br /> Informatica でサポートされていません。|(16,7)|5|5-7|  
  
## <a name="supported-string-literal-formats-for-time"></a>time でサポートされる文字列リテラル形式  
 次の表は、有効な文字列リテラル形式を**時間**データ型。  
  
|SQL Server|Description|  
|----------------|-----------------|  
|hh:mm[:ss][:fractional seconds][AM][PM]<br /><br /> hh:mm[:ss][.fractional seconds][AM][PM]<br /><br /> hhAM[PM]<br /><br /> hh AM[PM]|AM を指定したかどうかに関係なく、時刻値 0 は午前 0 時を表します。 時刻値が 0 のときに PM を指定することはできません。<br /><br /> AM と PM のどちらも指定していない場合、01 から 11 までの時刻値は午前の時刻を表します。 これらの値は、AM を指定した場合も午前の時刻を表します。 PM を指定すると、午後の時刻を表します。<br /><br /> AM と PM のどちらも指定していない場合、時刻値 12 は正午を表します。 AM を指定すると、午前 0 時を表します。 PM を指定すると、正午を表します。 たとえば、12時 01分は 1 分、午後後 12時 01分 PM; は、12時 01分 AM は午前 0 時から 1 分経ったです。 12:01 AM と指定しても、00:01 または 00:01 AM と指定した場合と同じ時刻を表します。<br /><br /> 13 から 23 までの時刻値は、AM または PM を指定していなくても、午後の時刻を表します。 値を表す場合も、午後の時刻を午後が指定されている場合。 時刻値が 13 から 23 までの場合、AM を指定することはできません。<br /><br /> 24 という時刻値は無効です。 午前 0 時を表すには、12:00 AM または 00:00 とします。<br /><br /> ミリ秒の前には、コロン (:) またはピリオド (.) を付けます。 コロンを付けると、後続の値は、1000 分の 1 秒単位になります。 ピリオドを付けると、数字が 1 桁なら 10 分の 1 秒単位に、2 桁なら 100 分の 1 秒単位に、3 桁なら 1000 分の 1 秒単位になります。 たとえば、"12:30:20:1" は 12 時 30 分 20 秒を 1000 分の 1 秒過ぎた時刻を表し、"12:30:20.1" は 12 時 30 分 20 秒を 10 分の 1 秒過ぎた時刻を表します。|  
  
|ISO 8601|注|  
|--------------|-----------|  
|hh:mm:ss<br /><br /> hh:mm[:ss][.fractional seconds]|hh は、タイム ゾーン オフセットの時間数を表す 0 ～ 14 の 2 桁の数字です。<br /><br /> mm は、タイム ゾーン オフセットの付加的な分数を表す 0 ～ 59 の 2 桁の数字です。|  
  
|ODBC|注|  
|----------|-----------|  
|{t 'hh:mm:ss[.fractional seconds]'}|ODBC API 固有です。|  
  
## <a name="compliance-with-ansi-and-iso-8601-standards"></a>ANSI および ISO 8601 への準拠  
 ISO 8601 (5.3.2 および 5.3) では、午前 0 時を表す時刻値 24 や、59 を超えるうるう秒の使用が定義されていますが、こうした用法は、下位互換性および既存の日付時刻型との一貫性を保つためサポート対象外となります。  
  
 下位クライアントに使用される既定の文字列リテラル形式は、hh:mm:ss[.nnnnnnn] として定義されている SQL 標準形式に準拠しています。 この形式は、1 秒未満の秒を除き、TIME に対する ISO 8601 の定義と似ています。  
  
##  <a name="BackwardCompatibilityforDownlevelClients"></a>ダウンレベル クライアントの旧バージョンとの互換性  
 一部のダウンレベルのクライアントをサポートしていない、**時間**、**日付**、 **datetime2**と**datetimeoffset**データ型。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の上位インスタンスと下位クライアントの間のデータ型マッピングを次の表に示します。  
  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型|下位クライアントに渡される既定の文字列リテラル形式|下位 ODBC|下位 OLEDB|下位 JDBC|下位 SQLCLIENT|  
|-----------------------------------------|----------------------------------------------------------------|----------------------|-----------------------|----------------------|---------------------------|  
|**time**|hh:mm:ss[.nnnnnnn]|SQL_WVARCHAR または SQL_VARCHAR|DBTYPE_WSTR または DBTYPE_STR|Java.sql.String|String または SqString|  
|**date**|-YYYY-MM-DD|SQL_WVARCHAR または SQL_VARCHAR|DBTYPE_WSTR または DBTYPE_STR|Java.sql.String|String または SqString|  
|**datetime2**|YYYY-MM-DD hh:mm:ss[.nnnnnnn]|SQL_WVARCHAR または SQL_VARCHAR|DBTYPE_WSTR または DBTYPE_STR|Java.sql.String|String または SqString|  
|**datetimeoffset**|YYYY-MM-DD hh:mm:ss [.nnnnnnn] [+ &#124;-] hh:mm|SQL_WVARCHAR または SQL_VARCHAR|DBTYPE_WSTR または DBTYPE_STR|Java.sql.String|String または SqString|  
  
## <a name="converting-date-and-time-data"></a>日付型データと時刻型データの変換  
 日付と時刻のデータ型に変換するときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]日付や時刻として認識できないすべての値を拒否します。 CAST および CONVERT 関数の日付と時刻のデータの使用方法については、次を参照してください。 [CAST および CONVERT &#40;です。TRANSACT-SQL と&#41; です。](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
### <a name="converting-timen-data-type-to-other-date-and-time-types"></a>time(n) データ型から他の日付/時刻データ型への変換  
 このセクションでは、どうなるかについて説明しますと、**時間**データ型は他の日付と時刻のデータ型に変換します。  
  
 ときに、変換を**time (n)**時間、分、および秒がコピーされます。 変換先の有効桁数が、ソースの有効桁数よりも小さい場合、秒の小数部は変換先の有効桁数に合わせて切り上げられます。 次の例は、`time(4)` 値を `time(3)` 値に変換した結果を示しています。  
  
```  
DECLARE @timeFrom time(4) = '12:34:54.1237';  
DECLARE @timeTo time(3) = @timeFrom;  
  
SELECT @timeTo AS 'time(3)', @timeFrom AS 'time(4)';  
  
--Results  
--time(3)      time(4)  
-------------- -------------  
--12:34:54.124 12:34:54.1237  
--  
--(1 row(s) affected)  
```  
  
 変換する場合  
                    **日付**変換は失敗し、発生するエラー メッセージ 206:"オペランド型の不整合: 日付は時間と互換性がありません"です。  
  
 ときに、変換を**datetime**時間、分、および 2 番目の値がコピーされ、日付部分に設定 ' 1900-01-01' です。 場合の秒の小数部の有効桁数、 **time (n)**値が 3 桁の数字より大きい、 **datetime**結果は切り捨てられます。 次のコードは、変換した結果を示しています、`time(4)`値を`datetime`値。  
  
```  
DECLARE @time time(4) = '12:15:04.1237';  
DECLARE @datetime datetime= @time;  
SELECT @time AS '@time', @datetime AS '@datetime';  
  
--Result  
--@time         @datetime  
--------------- -----------------------  
--12:15:04.1237 1900-01-01 12:15:04.123  
--  
--(1 row(s) affected)  
  
```  
  
 ときに、変換を**smalldatetime**日付は 1900 に ' に設定されている-01-01'、および時間と分の値は切り上げられます。 秒と秒の小数部は 0 に設定されます。 次のコードは、変換した結果を示しています、`time(4)`値を`smalldatetime`値。  
  
```  
-- Shows rounding up of the minute value.  
DECLARE @time time(4) = '12:15:59.9999';   
DECLARE @smalldatetime smalldatetime= @time;    
SELECT @time AS '@time', @smalldatetime AS '@smalldatetime';   
  
--Result  
@time            @smalldatetime  
---------------- -----------------------  
12:15:59.9999    1900-01-01 12:16:00--  
--(1 row(s) affected)  
  
-- Shows rounding up of the hour value.  
DECLARE @time time(4) = '12:59:59.9999';   
DECLARE @smalldatetime smalldatetime= @time;    
  
SELECT @time AS '@time', @smalldatetime AS '@smalldatetime';  
@time            @smalldatetime  
---------------- -----------------------  
12:59:59.9999    1900-01-01 13:00:00  
  
(1 row(s) affected)  
  
```  
  
 場合は、変換**datetimeoffset (n)**日付は 1900 に ' に設定されている-01-01'、および時刻がコピーされます。 タイム ゾーン オフセットが +00:00 に設定されます。 場合の秒の小数部の有効桁数、 **time (n)**値が、有効桁数より大きい、 **datetimeoffset (n)**値、値は切り上げに合わせてです。 次の例は、`time(4)` 値を `datetimeoffset(3)` 型に変換した結果を示しています。  
  
```  
DECLARE @time time(4) = '12:15:04.1237';  
DECLARE @datetimeoffset datetimeoffset(3) = @time;  
  
SELECT @time AS '@time', @datetimeoffset AS '@datetimeoffset';  
  
--Result  
--@time         @datetimeoffset  
--------------- ------------------------------  
--12:15:04.1237 1900-01-01 12:15:04.124 +00:00  
--  
--(1 row(s) affected)  
  
```  
  
 変換するときに**datetime2 (n)**日付は 1900 に ' に設定されている-01-01'、時刻部分がコピーされ、タイム ゾーン オフセットが 00時 00分に設定します。 場合の秒の小数部の有効桁数、 **datetime2 (n)**値がより大きい、 **time (n)**値、値は切り上げられますに合わせてです。  次の例は、`time(4)` 値を `datetime2(2)` 値に変換した結果を示しています。  
  
```  
DECLARE @time time(4) = '12:15:04.1237';  
DECLARE @datetime2 datetime2(3) = @time;  
  
SELECT @datetime2 AS '@datetime2', @time AS '@time';  
  
--Result  
--@datetime2              @time  
------------------------- -------------  
--1900-01-01 12:15:04.124 12:15:04.1237  
--  
--(1 row(s) affected)  
```  
  
### <a name="converting-string-literals-to-timen"></a>文字列リテラルの time(n) への変換  
 文字列リテラルから日付/時刻データ型への変換は、文字列のすべての部分が有効な形式になっている場合に可能になります。 それ以外の場合は実行時エラーが発生します。 日付/時刻データ型から文字列リテラルへの暗黙的な変換や、スタイルを指定しない明示的な変換では、現在のセッションの既定の形式が使用されます。 次の表はリテラルを文字列に変換するための規則は、**時間**データ型。  
  
|入力文字列リテラル|変換規則|  
|--------------------------|---------------------|  
|ODBC 日付|ODBC 文字列リテラルにマップされる、 **datetime**データ型。 ODBC 日付時刻リテラルから代入演算を行う**時間**型間の暗黙的な変換の場合は**datetime**この型の変換規則で定義されているとします。|  
|ODBC 時刻|ODBC 日付の規則の上記を参照してください。|  
|ODBC 日付時刻|ODBC 日付の規則の上記を参照してください。|  
|日付のみ|既定値が設定される|  
|時刻のみ|単純変換|  
|タイム ゾーンのみ|既定値が設定される|  
|日付 + 時刻|入力文字列の時刻部分が使用される|  
|日付 + タイム ゾーン|許可されていません。|  
|時刻 + タイム ゾーン|入力文字列の時刻部分が使用される|  
|日付 + 時刻 + タイム ゾーン|ローカル datetime の時刻部分が使用される|  
  
## <a name="examples"></a>使用例  
  
### <a name="a-comparing-date-and-time-data-types"></a>A. 日付と時刻のデータ型の比較  
 次の例は、文字列をそれぞれをキャストした結果を比較**日付**と**時間**データ型。  
  
```  
SELECT   
     CAST('2007-05-08 12:35:29. 1234567 +12:15' AS time(7)) AS 'time'   
    ,CAST('2007-05-08 12:35:29. 1234567 +12:15' AS date) AS 'date'   
    ,CAST('2007-05-08 12:35:29.123' AS smalldatetime) AS   
        'smalldatetime'   
    ,CAST('2007-05-08 12:35:29.123' AS datetime) AS 'datetime'   
    ,CAST('2007-05-08 12:35:29. 1234567 +12:15' AS datetime2(7)) AS   
        'datetime2'  
    ,CAST('2007-05-08 12:35:29.1234567 +12:15' AS datetimeoffset(7)) AS   
        'datetimeoffset';  
```  
  
|データ型|出力|  
|---------------|------------|  
|**time**|12:35:29. 1234567|  
|**date**|2007-05-08|  
|**smalldatetime**|2007-05-08 12:35:00|  
|**datetime**|2007-05-08 12:35:29.123|  
|**datetime2**|2007-05-08 12:35:29. 1234567|  
|**datetimeoffset**|2007-05-08 12:35:29.1234567 +12:15|  
  
###  <a name="ExampleB"></a> B. 有効な時刻文字列リテラルを time(7) 列に挿入する  
 次の表に、データ型の列に挿入できる各種の文字列リテラル**time (7)**し、その列に格納される値を使用します。  
  
|各種の文字列リテラル形式|挿入する文字列リテラル|格納される time(7) 値|Description|  
|--------------------------------|-----------------------------|------------------------------------|-----------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|'01:01:01:123AM'|01:01:01.1230000|1 秒未満の秒の有効桁数の前にコロン (:) を付けた場合、小数点以下桁数が 3 桁を超えると、エラーが生成されます。|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|'01:01:01.1234567 AM'|01:01:01.1234567|AM または PM を指定した場合、時刻は 24 時間形式で格納され、リテラルの AM または PM は格納されません。|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|'01:01:01.1234567 PM'|13:01:01.1234567|AM または PM を指定した場合、時刻は 24 時間形式で格納され、リテラルの AM または PM は格納されません。|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|'01:01:01.1234567PM'|13:01:01.1234567|AM または PM の前の空白は省略できます。|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|'01AM'|01:00:00.0000000|時だけを指定した場合、他のすべての値は 0 になります。|  
|SQL Server|'01 AM'|01:00:00.0000000|AM または PM の前の空白は省略できます。|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|'01:01:01'|01:01:01.0000000|1 秒未満の秒の有効桁数を指定しなかった場合、データ型で定義されている各桁が 0 になります。|  
|ISO 8601|'01:01:01.1234567'|01:01:01.1234567|ISO 8601 に準拠するには、AM または PM を付けずに、24 時間形式を使用します。|  
|ISO 8601|'01:01:01.1234567 +01:01'|01:01:01.1234567|TZD (Time Zone Difference) は省略可能で、入力はできますが保存されません。|  
  
### <a name="c-inserting-time-string-literal-into-columns-of-each-date-and-time-date-type"></a>C. date 型と time 型のそれぞれの列に対して時間の文字列リテラルを挿入する  
 次の表の 1 列目は、2 列目に示した date データ型または time データ型のデータベース テーブル列に挿入する時間の文字列リテラルを示しています。 3 列目は、データベース テーブル列に格納される値を示しています。  
  
|挿入する文字列リテラル|[列データ型]|列に格納される値|Description|  
|-----------------------------|----------------------|------------------------------------|-----------------|  
|'12:12:12.1234567'|**time(7)**|12:12:12.1234567|1 秒未満の秒の有効桁数が、列に指定された値を超えた場合、エラーは生成せずに文字列が切り詰められます。|  
|'2007-05-07'|**date**|NULL|time 値により、INSERT ステートメントが失敗します。|  
|'12:12:12'|**smalldatetime**|1900-01-01 12:12:00|1 秒未満の秒の有効桁数の値によって、INSERT ステートメントが失敗します。|  
|'12:12:12.123'|**datetime**|1900-01-01 12:12:12.123|秒の有効桁数が 3 桁を超えると、INSERT ステートメントが失敗します。|  
|'12:12:12.1234567'|**datetime2(7)**|1900-01-01 12:12:12.1234567|1 秒未満の秒の有効桁数が、列に指定された値を超えた場合、エラーは生成せずに文字列が切り詰められます。|  
|'12:12:12.1234567'|**datetimeoffset (7)**|1900-01-01 12:12:12.1234567 +00:00|1 秒未満の秒の有効桁数が、列に指定された値を超えた場合、エラーは生成せずに文字列が切り詰められます。|  
  
## <a name="see-also"></a>参照  
 [CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  
