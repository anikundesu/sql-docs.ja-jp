---
title: "bcp_setbulkmode |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-extensions-bulk-copy-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: bcp_setbulkmode function
ms.assetid: de56f206-1f7e-4c03-bf22-da9c7f9f4433
caps.latest.revision: "12"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 01826284e36aacd7b65677a260305010243a057a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="bcpsetbulkmode"></a>bcp_setbulkmode
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  bcp_setbulkmode では、1 つの関数の呼び出しですべての列属性を設定、一括コピー操作で列の形式を指定できます。  
  
## <a name="syntax"></a>構文  
  
```  
  
RETCODE bcp_setbulkmode (  
   HDBC hdbc,  
   INT property,  
   void * pField,  
   INT cbField,  
   void * pRow,  
   INT cbRow  
);  
```  
  
## <a name="arguments"></a>引数  
 *hdbc*  
 一括コピーが有効な ODBC 接続ハンドルです。  
  
 *プロパティ*  
 BYTE 型の定数です。 定数の一覧については、「解説」の表を参照してください。  
  
 *pField*  
 フィールド ターミネータ値を指すポインターです。  
  
 *cbField*  
 フィールド ターミネータ値の長さをバイト単位で。  
  
 *pRow*  
 行ターミネータ値を指すポインターです。  
  
 *cbRow*  
 行ターミネータ値の長さです (バイト単位)。  
  
## <a name="returns"></a>返します。  
 SUCCEED または FAIL を返します。  
  
## <a name="remarks"></a>解説  
 bcp_setbulkmode は、クエリまたはテーブルの一括コピー出力を使用できます。 Bcp_setbulkmode 使用すると、クエリ ステートメントの一括コピーには、BCP_HINT を bcp_control を呼び出す前に呼び出す必要があります。  
  
 bcp_setbulkmode が使用する代わりに[bcp_setcolfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-setcolfmt.md)と[bcp_columns](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md)、のみ関数呼び出しごとに 1 列の形式を指定することができます。  
  
 次の表に、定数を*プロパティ*パラメーター。  
  
|プロパティ|Description|  
|--------------|-----------------|  
|BCP_OUT_CHARACTER_MODE|文字出力モードを指定します。<br /><br /> BCP で – c オプションに対応します。EXE とで bcp_setcolfmt **BCP_FMT_TYPE**プロパティに設定**SQLCHARACTER**です。|  
|BCP_OUT_WIDE_CHARACTER_MODE|Unicode 出力モードを指定します。<br /><br /> BCP の – w オプションに対応します。EXE およびで bcp_setcolfmt **BCP_FMT_TYPE**プロパティに設定**SQLNCHAR**です。|  
|BCP_OUT_NATIVE_TEXT_MODE|文字型以外にネイティブ型を指定し、文字型に Unicode を指定します。<br /><br /> BCP の – N オプションに対応します。EXE およびで bcp_setcolfmt **BCP_FMT_TYPE**プロパティに設定**SQLNCHAR**列のデータ型が文字列 (既定値文字列でない場合)。|  
|BCP_OUT_NATIVE_MODE|ネイティブ データベース型を指定します。<br /><br /> BCP の – n オプションに対応します。EXE およびで bcp_setcolfmt **BCP_FMT_TYPE**プロパティを既定値に設定します。|  
  
 Bcp_setcolfmt、bcp_control、および bcp_readfmt を含む関数呼び出しのシーケンスでは、bcp_setbulkmode を使用する必要があります。 たとえば、bcp_control(BCPTEXTFILE) と bcp_setbulkmode をいない呼び出す必要があります。  
  
 Bcp_setbulkmode と競合しない bcp_control オプションについては、bcp_control と bcp_setbulkmode を呼び出すことができます。 たとえば、bcp_control(BCPFIRST) と bcp_setbulkmode を呼び出すことができます。  
  
 Bcp_setcolfmt、bcp_control、および bcp_readfmt を含む関数呼び出しのシーケンスを持つ bcp_setbulkmode を呼び出すしようとする場合は、シーケンス エラーが関数呼び出しのいずれかが戻ります。 エラーを解決することを選択する場合は、すべての設定をリセットして最初からやり直す bcp_init を呼び出します。  
  
 関数のシーケンス エラーが発生する関数呼び出しの例をいくつか次に示します。  
  
```  
bcp_init(“table”, DB_IN);  
bcp_setbulkmode();  
```  
  
```  
bcp_init(“table”, DB_OUT);  
bcp_setbulkmode();  
bcp_readfmt();  
```  
  
```  
bcp_init(NULL, DB_OUT);  
bcp_control(BCPHINTS, “select …”);  
bcp_setbulkmode();  
```  
  
```  
bcp_init(“table”, DB_OUT);  
bcp_setbulkmode();  
bcp_setcolfmt();  
```  
  
```  
bcp_init(“table”, DB_OUT);  
bcp_control(BCPDELAYREADFMT, true);  
bcp_readfmt();  
bcp_setcolfmt();  
```  
  
```  
bcp_init(NULL, DB_OUT);  
bcp_control(BCPDELAYREADFMT, true);  
bcp_setbulkmode();  
bcp_control(BCPHINTS, “select …”);  
bcp_readfmt();  
```  
  
```  
bcp_init(“table”, DB_OUT);  
bcp_control(BCPDELAYREADFMT, true);  
bcp_columns();  
```  
  
```  
bcp_init(“table”, DB_OUT);  
bcp_control(BCPDELAYREADFMT, true);  
bcp_setcolfmt();  
```  
  
## <a name="example"></a>例  
 次のサンプルでは、bcp_setbulkmode の異なる設定を使用して、4 つのファイルを作成します。  
  
```  
// compile with: sqlncli11.lib odbc32.lib  
  
#include <windows.h>  
#include <stdio.h>  
#include <tchar.h>  
#include <sqlext.h>  
#include "sqlncli.h"  
  
// Global variables  
SQLHENV g_hEnv = NULL;  
SQLHDBC g_hDbc = NULL;  
  
void ODBCCleanUp() {  
   if (g_hDbc) {  
      SQLDisconnect(g_hDbc);  
      SQLFreeHandle(SQL_HANDLE_DBC, g_hDbc);  
      g_hDbc = NULL;  
   }  
   if (g_hEnv) {  
      SQLFreeHandle(SQL_HANDLE_ENV, g_hEnv);  
      g_hEnv = NULL;  
   }  
}  
  
BOOL MakeODBCConnection(TCHAR * pszServer) {  
   TCHAR szConnectionString[500];  
   TCHAR szOutConnectionString[500];  
   SQLSMALLINT iLen;  
   SQLRETURN rc;  
  
   _sntprintf_s(szConnectionString, 500, TEXT("DRIVER={SQL Server Native Client 11.0};Server=%s;Trusted_connection=yes;"), pszServer);  
   rc = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE,&g_hEnv);  
   if (SQL_SUCCESS != rc && SQL_SUCCESS_WITH_INFO != rc) {  
      printf("SQLAllocHandle(SQL_HANDLE_ENV...) failed\n");  
      return false;  
   }  
   rc = SQLSetEnvAttr(g_hEnv,SQL_ATTR_ODBC_VERSION, (SQLPOINTER)SQL_OV_ODBC3, SQL_IS_UINTEGER);  
   if (SQL_SUCCESS != rc && SQL_SUCCESS_WITH_INFO != rc) {  
      printf("SQLSetEnvAttr failed\n");  
      SQLFreeHandle(SQL_HANDLE_ENV, g_hEnv);  
      return false;  
   }  
   rc = SQLAllocHandle( SQL_HANDLE_DBC, g_hEnv , &g_hDbc);  
   if (SQL_SUCCESS != rc && SQL_SUCCESS_WITH_INFO != rc) {  
      printf("SQLAllocHandle(SQL_HANDLE_DBC...) failed\n");  
      SQLFreeHandle(SQL_HANDLE_ENV, g_hEnv);  
      return false;  
   }  
   // Enable BCP  
   rc = SQLSetConnectAttr(g_hDbc, SQL_COPT_SS_BCP, (SQLPOINTER)SQL_BCP_ON, SQL_IS_INTEGER);  
   if (SQL_SUCCESS != rc && SQL_SUCCESS_WITH_INFO != rc) {  
      printf("SQLSetConnectAttr(.. SQL_COPT_SS_BCP, (SQLPOINTER)SQL_BCP_ON ...) failed\n");  
      ODBCCleanUp();  
      return false;  
   }  
   // connecting ...  
   rc = SQLDriverConnect(g_hDbc,NULL, (SQLTCHAR*)szConnectionString, SQL_NTS, (SQLTCHAR*)szOutConnectionString, 500, &iLen, SQL_DRIVER_NOPROMPT);  
   if (SQL_SUCCESS != rc && SQL_SUCCESS_WITH_INFO != rc) {  
      printf("SQLDriverConnect(SQL_HANDLE_DBC...) failed\n");  
      ODBCCleanUp();  
      return false;  
   }  
   return true;  
}  
  
BOOL BCPSetBulkMode(TCHAR * pszServer, TCHAR * pszQureryOut, char BCPType, TCHAR * pszDataFile) {  
   SQLRETURN rc;  
  
   if (!MakeODBCConnection(pszServer))  
      return false;  
   rc = bcp_init(g_hDbc, NULL, pszDataFile, NULL, DB_OUT);   // bcp init for queryout  
   if (SUCCEED != rc) {  
      printf("bcp_init failed\n");  
      ODBCCleanUp();  
      return false;  
   }  
   // setbulkmode  
   char ColTerm[] = "\t";  
   char RowTerm[] = "\r\n";  
   wchar_t wColTerm[] = L"\t";  
   wchar_t wRowTerm[] = L"\r\n";  
   BYTE * pColTerm = NULL;  
   int cbColTerm = NULL;  
   BYTE * pRowTerm = 0;  
   int cbRowTerm = 0;  
   int bulkmode = -1;  
  
   if (BCPType == 'c') {   // bcp -c  
      pColTerm = (BYTE*)ColTerm;  
      pRowTerm = (BYTE*)RowTerm;  
      cbColTerm = 1;  
      cbRowTerm = 2;  
      bulkmode = BCP_OUT_CHARACTER_MODE;  
   }  
   else  
      if (BCPType == 'w') {   // bcp -w   
         pColTerm = (BYTE*)wColTerm;  
         pRowTerm = (BYTE*)wRowTerm;  
         cbColTerm = 2;  
         cbRowTerm = 4;  
         bulkmode = BCP_OUT_WIDE_CHARACTER_MODE;  
      }  
      else  
         if (BCPType == 'n')   // bcp -n  
            bulkmode = BCP_OUT_NATIVE_MODE;  
         else  
            if (BCPType == 'N')   // bcp -n  
               bulkmode = BCP_OUT_NATIVE_TEXT_MODE;  
            else {  
               printf("unknown bcp mode\n");  
               ODBCCleanUp();  
               return false;  
            }  
            rc = bcp_setbulkmode(g_hDbc, bulkmode, pColTerm, cbColTerm, pRowTerm, cbRowTerm);  
            if (SUCCEED != rc) {  
               printf("bcp_setbulkmode failed\n");  
               ODBCCleanUp();  
               return false;  
            }  
            // set queryout TSQL statement  
            rc = bcp_control(g_hDbc, BCPHINTS , pszQureryOut);  
            if (SUCCEED != rc) {  
               printf("bcp_control(..BCP_OPTION_HINTS..) failed\n");  
               ODBCCleanUp();  
               return false;  
            }  
            // bcp copy  
            DBINT nRowsInserted = 0;  
            rc = bcp_exec(g_hDbc, &nRowsInserted);  
            if (SUCCEED != rc) {  
               printf("bcp_exec failed\n");  
               ODBCCleanUp();  
               return false;  
            }  
            printf("bcp done\n");  
            ODBCCleanUp();  
            return true;  
}  
  
int main() {  
   BCPSetBulkMode(TEXT("localhost"), TEXT("SELECT 'this is a bcp -c test', 1,2") , 'c', TEXT("bcpc.dat"));  
   BCPSetBulkMode(TEXT("localhost"), TEXT("SELECT 'this is a bcp -w test', 1,2") , 'w', TEXT("bcpw.dat"));  
   BCPSetBulkMode(TEXT("localhost"), TEXT("SELECT 'this is a bcp -c test', 1,2") , 'n', TEXT("bcpn.dat"));  
   BCPSetBulkMode(TEXT("localhost"), TEXT("SELECT 'this is a bcp -w test', 1,2") , 'N', TEXT("bcp_N.dat"));  
}  
```  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
