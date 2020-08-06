---
title: FILESTREAM を使用したデータの増分送信と受信 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: b82ecf4c-f151-4a99-8717-a73ee5ec994f
author: rothja
ms.author: jroth
ms.openlocfilehash: c7a47f0b0647516430f50dec433a93b4da2d2b49
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640887"
---
# <a name="send-and-receive-data-incrementally-with-filestream-odbc"></a><span data-ttu-id="609c8-102">FILESTREAM を使用したデータのインクリメンタル式での送受信 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="609c8-102">Send and Receive Data Incrementally with FILESTREAM (ODBC)</span></span>
  <span data-ttu-id="609c8-103">このサンプルでは、FILESTREAM 機能を使用して、SQLPutData と SQLGetData でデータをインクリメンタル式に送受信する方法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="609c8-103">This sample shows how to use the FILESTREAM feature to send and receive data incrementally with SQLPutData and SQLGetData.</span></span>  
  
 <span data-ttu-id="609c8-104">FILESTREAM 機能の詳細については、「 [Filestream Support &#40;ODBC&#41;](../native-client/odbc/filestream-support-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="609c8-104">For more information about the FILESTREAM feature, see [FILESTREAM Support &#40;ODBC&#41;](../native-client/odbc/filestream-support-odbc.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="609c8-105">例</span><span class="sxs-lookup"><span data-stu-id="609c8-105">Example</span></span>  
 <span data-ttu-id="609c8-106">このサンプルをコンパイルして実行する前に、FILESTREAM のサポートを有効にしてください (「[FILESTREAM の有効化と構成](../blob/enable-and-configure-filestream.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="609c8-106">Before you compile and run this sample, enable FILESTREAM support ([Enable and Configure FILESTREAM](../blob/enable-and-configure-filestream.md)).</span></span>  
  
 <span data-ttu-id="609c8-107">1 つ目の ([!INCLUDE[tsql](../../includes/tsql-md.md)]) コード リストは、このサンプルで使用するデータベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="609c8-107">The first ([!INCLUDE[tsql](../../includes/tsql-md.md)]) code listing creates a database used by this sample.</span></span> <span data-ttu-id="609c8-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスには、このスクリプトを実行するための書き込みアクセス許可が必要です (たとえば、ローカル システム アカウントでログオンしてください)。</span><span class="sxs-lookup"><span data-stu-id="609c8-108">Your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must have write access to run this script (for example, log on as a local system account).</span></span>  
  
 <span data-ttu-id="609c8-109">2 つ目のコード リストは C++ コードです。</span><span class="sxs-lookup"><span data-stu-id="609c8-109">The second code listing is the C++ code.</span></span> <span data-ttu-id="609c8-110">サーバーを指定する必要があります。C++ コード リストで、"MyServer" を有効なサーバー名に変更してください。</span><span class="sxs-lookup"><span data-stu-id="609c8-110">You must specify a server; in the C++ code listing, change "MyServer" to a valid server name.</span></span> <span data-ttu-id="609c8-111">INCLUDE 環境変数に、sqlncli を含むディレクトリが含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="609c8-111">Make sure your INCLUDE environment variable includes the directory that contains sqlncli.h.</span></span> <span data-ttu-id="609c8-112">odbc32.lib、user32.lib、/D "_UNICODE"、/D "UNICODE"、odbc32.lib、および /EHsc を使用して C++ コード リストをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="609c8-112">Compile the C++ code listing with odbc32.lib, user32.lib, /D "_UNICODE", /D "UNICODE", odbc32.lib, and /EHsc.</span></span>  
  
 <span data-ttu-id="609c8-113">3 つ目の ([!INCLUDE[tsql](../../includes/tsql-md.md)]) コード リストは、このサンプルで使用したデータベースを削除します。</span><span class="sxs-lookup"><span data-stu-id="609c8-113">The third ([!INCLUDE[tsql](../../includes/tsql-md.md)]) code listing deletes the database used by this sample.</span></span>  
  
```  
USE master  
GO  
  
-- enable file stream  
exec sp_configure 'filestream access level', 2  
GO  
  
-- create directory for filestream database  
EXEC sp_configure 'show advanced options', 1  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'xp_cmdshell', 1  
GO  
RECONFIGURE  
GO  
EXEC xp_cmdshell 'md c:\filestreamdemo'  
GO  
  
-- Drop the filestream demo database  
IF EXISTS (SELECT name FROM master..sysdatabases WHERE name = 'myfilestreamdb')  
    DROP DATABASE [myfilestreamdb]  
GO  
  
-- Create filestream demo database  
CREATE DATABASE [myfilestreamdb] ON PRIMARY  
    (NAME=[myfilestreamdbprimary], FILENAME='c:\filestreamdemo\dbf.mdf'),  
    FILEGROUP [fsgrp] CONTAINS FILESTREAM (NAME=[fscnt],FILENAME='c:\filestreamdemo\fscnt')  
    LOG ON (NAME=[dblog], FILENAME='c:\filestreamdemo\db1.ldf', SIZE=5MB, MAXSIZE=3000MB, FILEGROWTH=5MB)  
GO  
  
-- Create table that contain filestream column  
CREATE TABLE [myfilestreamdb]..[mydocs]  
(  
    id UNIQUEIDENTIFIER ROWGUIDCOL NOT NULL UNIQUE,  
    doc VARBINARY(MAX) FILESTREAM  
)  
GO  
```  
  
```  
// compile with: /D "_UNICODE" /D "UNICODE" odbc32.lib /EHsc  
#pragma once  
#define WIN32_LEAN_AND_MEAN  
#include <tchar.h>  
#include <windows.h>  
#include <stdio.h>  
#include <sql.h>  
#include <sqlext.h>  
  
#define _SQLNCLI_ODBC_  
#include <sqlncli.h>  
  
#define SUCCESS(x) (!((x) & 0xFFFE))  
  
#define CHKRC(stmt) do { \  
                        rc = (stmt); \  
                        if (!SUCCESS(rc)) \  
                            throw (RETCODE) rc; \  
                    } while(0);  
  
void PrintError(SQLSMALLINT HandleType, SQLHANDLE Handle) {  
    RETCODE rc = SQL_SUCCESS;  
    SQLTCHAR szSqlState[6], szMessage[1024];  
    SQLSMALLINT i = 1, msgLen = 0;  
    SQLINTEGER NativeError;  
  
    do {  
       i = 1;  
       while (SQL_NO_DATA != (rc = SQLGetDiagRec(HandleType, Handle, i, szSqlState, &NativeError, szMessage, sizeof(szMessage)/sizeof(SQLTCHAR), &msgLen)) && SUCCESS(rc)) {  
            _tprintf(_T("SQLState=%s, NativeError=%ld, Message=%s\r\n"), szSqlState, NativeError, szMessage);  
            i++;  
        }  
    }   
    while (SQL_NO_DATA != (rc = SQLMoreResults(Handle)) && SUCCESS(rc));  
}  
  
int _tmain(int argc, _TCHAR* argv[]) {  
    RETCODE rc = SQL_SUCCESS;  
    HENV henv = SQL_NULL_HENV;  
    HDBC hdbc = SQL_NULL_HDBC;  
    SQLHSTMT hstmt = SQL_NULL_HSTMT;  
    SQLTCHAR * pszConnection = _T("DRIVER={SQL Server Native Client 10.0};")  
                               _T("Server=MyServer;")  
                               _T("Trusted_Connection=Yes;");  
    SQLLEN cbBuffer = SQL_DATA_AT_EXEC;  
    BYTE rgbDoc[1024];  
    SQLLEN cbDoc;  
  
    try {  
        CHKRC(SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HENV, &henv));  
        CHKRC(SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER)SQL_OV_ODBC3, 0));  
        CHKRC(SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc));  
        CHKRC(SQLDriverConnect(hdbc, NULL, pszConnection, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT));  
  
        CHKRC(SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt));  
        CHKRC(SQLPrepare(hstmt,  (SQLTCHAR *)_T("INSERT INTO [myfilestreamdb]..[mydocs] VALUES(newid(), ?)"), SQL_NTS));  
        CHKRC(SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_BINARY, SQL_VARBINARY, SQL_SS_LENGTH_UNLIMITED, 0, (SQLPOINTER)1, 0, &cbBuffer));  
  
        rc = ::SQLExecute(hstmt);  
        if (SQL_NEED_DATA == rc) {  
            SQLPOINTER pParam = NULL;  
            while (SQL_NEED_DATA == (rc = ::SQLParamData(hstmt, (SQLPOINTER *)&pParam))) {  
                CHKRC(SQLPutData(hstmt, "Hello ", 6));  
                CHKRC(SQLPutData(hstmt, "World!", 6));  
            }  
        }  
  
        CHKRC(SQLFreeStmt(hstmt, SQL_CLOSE));  
        CHKRC(SQLExecDirect(hstmt, _T("SELECT doc FROM [myfilestreamdb]..[mydocs]"), SQL_NTS));  
        CHKRC(SQLBindCol(hstmt, 1, SQL_C_BINARY, (SQLPOINTER)rgbDoc, sizeof(rgbDoc), &cbDoc));  
        CHKRC(SQLFetch(hstmt));  
  
        rgbDoc[cbDoc] = '\0';  
        printf("%s\r\n", (LPSTR)rgbDoc);  
    }  
    catch (RETCODE retcode) {  
        rc = retcode;  
    }  
  
    if (!SUCCESS(rc))  
        if (hstmt)  
            PrintError(SQL_HANDLE_STMT, hstmt);  
        else if (hdbc)  
            PrintError(SQL_HANDLE_DBC, hdbc);  
        else if(henv)  
            PrintError(SQL_HANDLE_ENV, henv);  
  
    if (hstmt)  
        SQLFreeHandle(SQL_HANDLE_STMT, hstmt);  
  
    if (hdbc) {  
        SQLDisconnect(hdbc);  
        SQLFreeHandle(SQL_HANDLE_DBC, hdbc);  
    }  
  
    if (henv)  
        SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
```  
USE master  
GO  
-- Drop the filestream demo database  
sp_detach_db 'myfilestreamdb'  
IF EXISTS (SELECT name FROM master..sysdatabases WHERE name = 'myfilestreamdb')  
    DROP DATABASE [myfilestreamdb]  
EXEC xp_cmdshell 'rd /s /q c:\filestreamdemo'  
GO  
```  
  
  
