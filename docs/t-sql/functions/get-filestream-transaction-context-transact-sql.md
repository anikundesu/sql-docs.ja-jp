---
title: "GET_FILESTREAM_TRANSACTION_CONTEXT (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GET_FILESTREAM_TRANSACTION_CONTEXT_TSQL
- GET_FILESTREAM_TRANSACTION_CONTEXT
dev_langs: TSQL
helpviewer_keywords: GET_FILESTREAM_TRANSACTION_CONTEXT FILESTREAM [SQL Server]
ms.assetid: 459e6b79-4420-41e6-85bf-89d90f43b4f1
caps.latest.revision: "20"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ca5d2fac23dfa3c74689265915c498a4d6858fbc
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="getfilestreamtransactioncontext-transact-sql"></a>GET_FILESTREAM_TRANSACTION_CONTEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  セッションの現在のトランザクション コンテキストを表すトークンを返します。 アプリケーションでは、このトークンを使用して、FILESTREAM のファイル システム ストリーミング操作をトランザクションにバインドします。 FILESTREAM のトピックの一覧は、次を参照してください。[バイナリ ラージ オブジェクト &#40;です。Blob &#41;データ &#40;です。SQL Server &#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
GET_FILESTREAM_TRANSACTION_CONTEXT ()  
```  
  
## <a name="return-type"></a>戻り値の型  
 **varbinary(max)**  
  
## <a name="return-value"></a>戻り値  
 トランザクションが開始されていないか、キャンセルまたはコミットされている場合、NULL が返されます。  
  
## <a name="remarks"></a>解説  
 トランザクションは明示的にする必要があります。 BEGIN TRANSACTION に続けて、COMMIT TRANSACTION または ROLLBACK TRANSACTION を使用します。  
  
 GET_FILESTREAM_TRANSACTION_CONTEXT を呼び出すと、トランザクションへのファイル システム アクセス権が呼び出し元に与えられます。このアクセス権は、トランザクションが完了するまで有効です。 トランザクションに対するファイル システム経由のアクセスを別のユーザーに許可するには、EXECUTE AS を使用して、別のユーザーとして GET_FILESTREAM_TRANSACTION_CONTEXT を実行します。  
  
## <a name="examples"></a>使用例  
 次の例で`GET_FILESTREAM_TRANSACTION_CONTEXT`で、[!INCLUDE[tsql](../../includes/tsql-md.md)]トランザクションをトランザクション コンテキストを取得します。  
  
```csharp  
using System;  
using System.Data.SqlClient;  
using System.Data;  
  
namespace ConsoleApplication  
{  
    /// <summary>  
    /// This class is a wrapper that contains methods for:  
    ///   
    ///     GetTransactionContect() - Returns the current transaction context.  
    ///     BeginTransaction() - Begins a transaction.  
    ///     CommmitTransaction() - Commits the current transaction.  
    ///   
    /// </summary>  
  
    class SqlAccessWrapper  
    {  
        /// <summary>  
        /// Returns a byte array that contains the current transaction  
        /// context.  
        /// </summary>  
        /// <param name="sqlConnection">  
        /// SqlConnection object that represents the instance of SQL Server  
        /// from which to obtain the transaction context.   
        /// </param>  
        /// <returns>  
        /// If there is a current transaction context, the return  
        /// value is an Object that represents the context.  
        /// If there is not a current transaction context, the  
        /// value returned is DBNull.Value.  
        /// </returns>  
  
        public Object GetTransactionContext(SqlConnection sqlConnection)  
        {  
            SqlCommand cmd = new SqlCommand();  
            cmd.CommandText = "SELECT GET_FILESTREAM_TRANSACTION_CONTEXT()";  
            cmd.CommandType = CommandType.Text;  
            cmd.Connection = sqlConnection;  
  
            return cmd.ExecuteScalar();  
  
        }  
  
        /// <summary>  
        /// Begins the transaction.  
        /// </summary>  
        /// <param name="sqlConnection">  
        /// SqlConnection object that represents the server  
        /// on which to run the BEGIN TRANSACTION statement.  
        /// </param>  
  
        public void BeginTransaction(SqlConnection sqlConnection)  
        {  
            SqlCommand cmd = new SqlCommand();  
  
            cmd.CommandText = "BEGIN TRANSACTION";  
            cmd.CommandType = CommandType.Text;  
            cmd.Connection = sqlConnection;  
  
            cmd.ExecuteNonQuery();  
        }  
  
        /// <summary>  
        /// Commits the transaction.  
        /// </summary>  
        /// <param name="sqlConnection">  
        /// SqlConnection object that represents the instance of SQL Server  
        /// on which to run the COMMIT statement.  
        /// </param>  
  
        public void CommitTransaction(SqlConnection sqlConnection)  
        {  
            SqlCommand cmd = new SqlCommand();  
  
            cmd.CommandText = "COMMIT TRANSACTION";  
            cmd.CommandType = CommandType.Text;  
            cmd.Connection = sqlConnection;  
  
            cmd.ExecuteNonQuery();  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            //Open a connection to the local instance of SQL Server.  
  
            SqlConnection sqlConnection = new SqlConnection("Integrated Security=true;server=(local)");  
            sqlConnection.Open();  
  
            SqlAccessWrapper sql = new SqlAccessWrapper();  
  
            //Create a transaction so that sql.GetTransactionContext() will succeed.  
            sql.BeginTransaction(sqlConnection);  
  
            //The transaction context will be stored in this array.  
            Byte[] transactionToken;     
  
            Object txObj = sql.GetTransactionContext(sqlConnection);  
            if (DBNull.Value != txObj)  
            {  
                transactionToken = (byte[])txObj;  
                Console.WriteLine("Transaction context obtained.\n");  
            }  
  
            sql.CommitTransaction(sqlConnection);  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Data.SqlClient  
Imports System.Data  
  
Namespace ConsoleApplication  
    ''' <summary>   
    ''' This class is a wrapper that contains methods for:   
    '''   
    ''' GetTransactionContect() - Returns the current transaction context.   
    ''' BeginTransaction() - Begins a transaction.   
    ''' CommmitTransaction() - Commits the current transaction.   
    '''   
    ''' </summary>   
  
    Class SqlAccessWrapper  
        ''' <summary>   
        ''' Returns a byte array that contains the current transaction   
        ''' context.   
        ''' </summary>   
        ''' <param name="sqlConnection">   
        ''' SqlConnection object that represents the instance of SQL Server   
        ''' from which to obtain the transaction context.   
        ''' </param>   
        ''' <returns>   
        ''' If there is a current transaction context, the return   
        ''' value is an Object that represents the context.   
        ''' If there is not a current transaction context, the   
        ''' value returned is DBNull.Value.   
        ''' </returns>   
  
        Public Function GetTransactionContext(ByVal sqlConnection As SqlConnection) As Object  
            Dim cmd As New SqlCommand()  
            cmd.CommandText = "SELECT GET_FILESTREAM_TRANSACTION_CONTEXT()"  
            cmd.CommandType = CommandType.Text  
            cmd.Connection = sqlConnection  
  
            Return cmd.ExecuteScalar()  
  
        End Function  
  
        ''' <summary>   
        ''' Begins the transaction.   
        ''' </summary>   
        ''' <param name="sqlConnection">   
        ''' SqlConnection object that represents the server   
        ''' on which to run the BEGIN TRANSACTION statement.   
        ''' </param>   
  
        Public Sub BeginTransaction(ByVal sqlConnection As SqlConnection)  
            Dim cmd As New SqlCommand()  
  
            cmd.CommandText = "BEGIN TRANSACTION"  
            cmd.CommandType = CommandType.Text  
            cmd.Connection = sqlConnection  
  
            cmd.ExecuteNonQuery()  
        End Sub  
  
        ''' <summary>   
        ''' Commits the transaction.   
        ''' </summary>   
        ''' <param name="sqlConnection">   
        ''' SqlConnection object that represents the instance of SQL Server   
        ''' on which to run the COMMIT statement.   
        ''' </param>   
  
        Public Sub CommitTransaction(ByVal sqlConnection As SqlConnection)  
            Dim cmd As New SqlCommand()  
  
            cmd.CommandText = "COMMIT TRANSACTION"  
            cmd.CommandType = CommandType.Text  
            cmd.Connection = sqlConnection  
  
            cmd.ExecuteNonQuery()  
        End Sub  
    End Class  
  
    Class Program  
        Shared Sub Main()  
            '''Open a connection to the local instance of SQL Server.  
  
            Dim sqlConnection As New SqlConnection("Integrated Security=true;server=(local)")  
            sqlConnection.Open()  
  
            Dim sql As New SqlAccessWrapper()  
  
            '''Create a transaction so that sql.GetTransactionContext() will succeed.   
            sql.BeginTransaction(sqlConnection)  
  
            '''The transaction context will be stored in this array.   
            Dim transactionToken As Byte()  
  
            Dim txObj As Object = sql.GetTransactionContext(sqlConnection)  
  
            '''If the returned object is not NULL, there is a valid transaction  
            '''token, and it must be converted into a format that is usable within  
            '''the application.  
  
            If Not txObj.Equals(DBNull.Value) Then  
                transactionToken = DirectCast(txObj, Byte())  
                Console.WriteLine("Transaction context obtained." & Chr(10) & "")  
            End If  
  
            sql.CommitTransaction(sqlConnection)  
        End Sub  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a>参照  
 [パス名 &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/pathname-transact-sql.md)   
 [バイナリ ラージ オブジェクト &#40;Blob&#41; データ &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md)  
  
  
