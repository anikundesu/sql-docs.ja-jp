---
title: "getColumns メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerDatabaseMetaData.getColumns
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: f173fa5d-e114-4a37-a5c4-2baad9ff3af1
caps.latest.revision: "39"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8d13702e93a5979c53a9bf8fa7e6d7beec161f83
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="getcolumns-method-sqlserverdatabasemetadata"></a>getColumns メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたカタログで使用できるテーブル列の記述を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.ResultSet getColumns(java.lang.String catalog,  
                                     java.lang.String schema,  
                                     java.lang.String table,  
                                     java.lang.String col)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *カタログ*  
  
 A**文字列**カタログ名を格納しています。  
  
 *スキーマ*  
  
 A**文字列**スキーマ名のパターンを格納しています。  
  
 *テーブル*  
  
 A**文字列**テーブル名のパターンを格納しています。  
  
 *col*  
  
 A**文字列**列名のパターンを格納しています。  
  
## <a name="return-value"></a>戻り値  
 A [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getColumns メソッドは、java.sql.DatabaseMetaData インターフェイスの getColumns メソッドによって指定されます。  
  
 GetColumns メソッドによって返される結果セットには、次の情報が含まれます。  
  
|名前|型|Description|  
|----------|----------|-----------------|  
|TABLE_CAT|**文字列**|カタログ名。|  
|TABLE_SCHEM|**文字列**|テーブル スキーマ名です。|  
|TABLE_NAME|**文字列**|テーブル名。|  
|COLUMN_NAME|**文字列**|列名。|  
|DATA_TYPE|**smallint**|java.sql.Types の SQL データ型です。|  
|TYPE_NAME|**文字列**|データ型の名前です。|  
|COLUMN_SIZE|**int**|列の完全桁数です。|  
|BUFFER_LENGTH|**smallint**|データの転送サイズです。|  
|DECIMAL_DIGITS|**smallint**|列の小数点以下の桁数です。|  
|NUM_PREC_RADIX|**smallint**|列の基数です。|  
|NULLABLE|**smallint**|列が null を許容するかどうかを示します。 次の値のいずれかを指定できます。<br /><br /> columnNoNulls (0)<br /><br /> columnNullable (1)|  
|REMARKS|**文字列**|列に関連付けられているコメントです。<br /><br /> **注:** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]常にこの列の null を返します。|  
|COLUMN_DEF|**文字列**|列の既定値です。|  
|SQL_DATA_TYPE|**smallint**|記述子の TYPE フィールドでの SQL データ型の値です。 datetime データ型と SQL-92 interval データ型以外は、DATA_TYPE 列と同じです。 この列は、常に値を返します。|  
|SQL_DATETIME_SUB|**smallint**|datetime および SQL-92 interval データ型のサブタイプ コードです。 他のデータ型の場合、この列は NULL を返します。|  
|CHAR_OCTET_LENGTH|**int**|列の最大バイト数です。|  
|ORDINAL_POSITION|**int**|テーブル内の列のインデックスです。|  
|IS_NULLABLE|**文字列**|列で null 値が許容されるかどうかを示します。|  
|SS_IS_SPARSE|**smallint**|列がスパース列の場合は、値 1 になります。それ以外の場合、0 を返します。<sup>1</sup>|  
|SS_IS_COLUMN_SET|**smallint**|列がスパース column_set 列の場合は 1、それ以外の場合は 0 になります。 <sup>1</sup>|  
|SS_IS_COMPUTED|**smallint**|TABLE_TYPE の列が計算列であるかどうかを示します。 <sup>1</sup>|  
|IS_AUTOINCREMENT|**文字列**|列が自動インクリメントされる場合は "YES" です。 列が自動インクリメントされない場合は "NO" です。 列が自動インクリメントされるかどうかをドライバーが判断できない場合は "" (空の文字列) です。 <sup>1</sup>|  
|SS_UDT_CATALOG_NAME|**文字列**|ユーザー定義型 (UDT) を含むカタログの名前。 <sup>1</sup>|  
|SS_UDT_SCHEMA_NAME|**文字列**|UDT (ユーザー定義型) を含むスキーマの名前です。 <sup>1</sup>|  
|SS_UDT_ASSEMBLY_TYPE_NAME|**文字列**|完全修飾名の UDT (ユーザー定義型) です。 <sup>1</sup>|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|**文字列**|XML スキーマ コレクション名が定義されているカタログの名前です。 カタログ名が見つからない場合、この変数には、空の文字列が含まれています。 <sup>1</sup>|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|**文字列**|XML スキーマ コレクション名が定義されているスキーマの名前です。 スキーマ名が見つからない場合は、空文字列です。 <sup>1</sup>|  
|SS_XML_SCHEMACOLLECTION_NAME|**文字列**|XML スキーマ コレクションの名前です。 名前が見つからない場合は、空文字列です。 <sup>1</sup>|  
|SS_DATA_TYPE|**tinyint**|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]拡張ストアド プロシージャによって使用されるデータ型。<br /><br /> **注**によって返されるデータ型の詳細については[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]、「データ型 (TRANSACT-SQL)」を参照してください[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]オンライン ブック。|  
  
 (1) この列に接続している場合に含まれません[!INCLUDE[ssVersion2005](../../../includes/ssversion2005_md.md)]です。  
  
> [!NOTE]  
>  GetColumns メソッドによって返されるデータに関する詳細については、「sp_columns (TRANSACT-SQL)」を参照してください[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]オンライン ブック。  
  
 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] JDBC Driver 3.0 では、次の動作が以前のバージョンの JDBC Driver から変更表示されます。  
  
 DATA_TYPE 列には、次の変更点があります。  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]データ型|JDBC Driver 2.0 では型を返す (またはに接続されている[!INCLUDE[ssVersion2005](../../../includes/ssversion2005_md.md)]) と関連付けられている定数の数値|接続しているときに、JDBC Driver 3.0 での型を返す[!INCLUDE[ssKatmai](../../../includes/sskatmai_md.md)]以降|  
|-------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|  
|8 KB を超えるユーザー定義型|LONGVARBINARY (-4)|VARBINARY (-3)|  
|geography|LONGVARBINARY (-4)|VARBINARY (-3)|  
|geometry|LONGVARBINARY (-4)|VARBINARY (-3)|  
|varbinary(max)|LONGVARBINARY (-4)|VARBINARY (-3)|  
|nvarchar(max)|LONGVARCHAR (-1) または LONGNVARCHAR (JDBC 4) (-16)|VARCHAR (12) または NVARCHAR (JDBC 4) (-9)|  
|varchar(max)|LONGVARCHAR (-1)|VARCHAR (12)|  
|time|VARCHAR (12) または NVARCHAR (JDBC 4) (-9)|TIME (-154)|  
|date|VARCHAR (12) または NVARCHAR (JDBC 4) (-9)|DATE (91)|  
|datetime2|VARCHAR (12) または NVARCHAR (JDBC 4) (-9)|TIMESTAMP (93)|  
|datetimeoffset|VARCHAR (12) または NVARCHAR (JDBC 4) (-9)|microsoft.sql.Types.DATETIMEOFFSET (-155)|  
  
 COLUMN_SIZE 列には、次の変更点があります。  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]データ型|JDBC Driver 2.0 での戻り値の型|JDBC Driver 3.0 での戻り値の型|  
|-------------------------------------------------------------------|------------------------------------|------------------------------------|  
|nvarchar(max)|1073741823|2147483647 (データベースのメタデータ)|  
|xml|1073741823|2147483647 (データベースのメタデータ)|  
|8 KB 以下のユーザー定義型|8 KB (結果セットとパラメーターのメタデータ)|ストアド プロシージャによって返される実際のサイズです。|  
|time||この型の文字列表記の長さ (文字数) です (秒部分に許容される最大有効桁数を想定)。|  
|date||time と同じです。|  
|datetime2||time と同じです。|  
|datetimeoffset||time と同じです。|  
  
 BUFFER_LENGTH 列には、次の変更点があります。  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]データ型|JDBC Driver 2.0 での戻り値の型|JDBC Driver 3.0 での戻り値の型|  
|-------------------------------------------------------------------|------------------------------------|------------------------------------|  
|8 KB を超えるユーザー定義型||2147483647|  
  
 TYPE_NAME 列には、次の変更点があります。  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]データ型|JDBC Driver 2.0 での戻り値の型|JDBC Driver 3.0 での戻り値の型|  
|-------------------------------------------------------------------|------------------------------------|------------------------------------|  
|varchar(max)|text|varchar|  
|varbinary(max)|image|varbinary|  
  
 DECIMAL_DIGITS 列には、次の変更点があります。  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] の型|JDBC Driver 2.0|JDBC Driver 3.0|  
|--------------------------------------------------------------|---------------------|---------------------|  
|time|null|7 (または、指定した場合はそれより少なくなります)|  
|date|null|null|  
|datetime2|null|7 (または、指定した場合はそれより少なくなります)|  
|datetimeoffset|null|7 (または、指定した場合はそれより少なくなります)|  
  
 SQL_DATA_TYPE 列には、次の変更点があります。  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]データ型|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]JDBC Driver 2.0 での 2008年のデータ値|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]JDBC Driver 3.0 での 2008年のデータ値|  
|-------------------------------------------------------------------|--------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|  
|varchar(max)|-10|-9|  
|nvarchar(max)|-1|-9|  
|xml|-10|-152|  
|8 KB 以下のユーザー定義型|-3|-151|  
|8 KB を超えるユーザー定義型|JDBC Driver 2.0 では使用できません。|-151|  
|geography|-4|-151|  
|geometry|-4|-151|  
|hierarchyid|-4|-151|  
|time|-9|92|  
|date|-9|91|  
|datetime2|-9|93|  
|datetimeoffset|-9|-155|  
  
## <a name="example"></a>例  
 次の例では Person.Contact テーブル内の情報を返す getColumns メソッドを使用する方法、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]サンプル データベース。  
  
```  
import java.sql.*;  
public class c1 {  
   public static void main(String[] args) {  
      String connectionUrl = "jdbc:sqlserver://localhost:1433;databaseName=AdventureWorks;integratedsecurity=true";  
  
      Connection con = null;  
      Statement stmt = null;  
      ResultSet rs = null;  
  
      try {  
         Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
         con = DriverManager.getConnection(connectionUrl);  
         DatabaseMetaData dbmd = con.getMetaData();  
         rs = dbmd.getColumns("AdventureWorks", "Person", "Contact", "FirstName");  
  
         ResultSet r = dbmd.getColumns(null, null, "Contact", null);  
         ResultSetMetaData rm = r.getMetaData();   
         int noofcols = rm.getColumnCount();  
  
         if (r.next())  
            for (int i = 0 ; i < noofcols ; i++ )  
            System.out.println(rm.getColumnName( i + 1 ) + ": \t\t" + r.getString( i + 1 ));  
      }  
  
      catch (Exception e) {}  
      finally {}  
   }  
}  
```  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
