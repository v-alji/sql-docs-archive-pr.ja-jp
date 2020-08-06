---
title: bcp_setbulkmode |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bcp_setbulkmode function
ms.assetid: de56f206-1f7e-4c03-bf22-da9c7f9f4433
author: rothja
ms.author: jroth
ms.openlocfilehash: 1b7a68dfb3c868422b2e01cccf511a623d3afe52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642063"
---
# <a name="bcp_setbulkmode"></a><span data-ttu-id="31d87-102">bcp_setbulkmode</span><span class="sxs-lookup"><span data-stu-id="31d87-102">bcp_setbulkmode</span></span>
  <span data-ttu-id="31d87-103">bcp_setbulkmode を使用すると、一括コピー操作で列の形式を指定し、1回の関数呼び出しですべての列の属性を設定できます。</span><span class="sxs-lookup"><span data-stu-id="31d87-103">bcp_setbulkmode lets you specify the column format in a bulk copy operation, setting all the column attributes in a single function call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31d87-104">構文</span><span class="sxs-lookup"><span data-stu-id="31d87-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_setbulkmode (  
   HDBC   
hdbc  
,  
   INT   
property  
,  
   void *   
pField  
,  
   INT   
cbField  
,  
   void *   
pRow  
,  
   INT   
cbRow  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="31d87-105">引数</span><span class="sxs-lookup"><span data-stu-id="31d87-105">Arguments</span></span>  
 <span data-ttu-id="31d87-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="31d87-106">*hdbc*</span></span>  
 <span data-ttu-id="31d87-107">一括コピーが有効な ODBC 接続ハンドルです。</span><span class="sxs-lookup"><span data-stu-id="31d87-107">The bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="31d87-108">*property*</span><span class="sxs-lookup"><span data-stu-id="31d87-108">*property*</span></span>  
 <span data-ttu-id="31d87-109">BYTE 型の定数です。</span><span class="sxs-lookup"><span data-stu-id="31d87-109">A constant of type BYTE.</span></span> <span data-ttu-id="31d87-110">定数の一覧については、「解説」の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31d87-110">See the table in the Remarks section for a list of the constants.</span></span>  
  
 <span data-ttu-id="31d87-111">*pField*</span><span class="sxs-lookup"><span data-stu-id="31d87-111">*pField*</span></span>  
 <span data-ttu-id="31d87-112">フィールド ターミネータ値を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="31d87-112">The pointer to the field terminator value.</span></span>  
  
 <span data-ttu-id="31d87-113">*cbField*</span><span class="sxs-lookup"><span data-stu-id="31d87-113">*cbField*</span></span>  
 <span data-ttu-id="31d87-114">フィールドターミネータ値の長さ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="31d87-114">The length (in bytes) of the field terminator value.</span></span>  
  
 <span data-ttu-id="31d87-115">*pRow*</span><span class="sxs-lookup"><span data-stu-id="31d87-115">*pRow*</span></span>  
 <span data-ttu-id="31d87-116">行ターミネータ値を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="31d87-116">The pointer to the row terminator value.</span></span>  
  
 <span data-ttu-id="31d87-117">*cbRow*</span><span class="sxs-lookup"><span data-stu-id="31d87-117">*cbRow*</span></span>  
 <span data-ttu-id="31d87-118">行ターミネータ値の長さです (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="31d87-118">The length in bytes of the row terminator value.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="31d87-119">戻り値</span><span class="sxs-lookup"><span data-stu-id="31d87-119">Returns</span></span>  
 <span data-ttu-id="31d87-120">SUCCEED または FAIL を返します。</span><span class="sxs-lookup"><span data-stu-id="31d87-120">SUCCEED or FAIL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31d87-121">解説</span><span class="sxs-lookup"><span data-stu-id="31d87-121">Remarks</span></span>  
 <span data-ttu-id="31d87-122">bcp_setbulkmode を使用すると、クエリまたはテーブルのいずれかから一括コピーできます。</span><span class="sxs-lookup"><span data-stu-id="31d87-122">bcp_setbulkmode can be used to bulk copy out of either a query or a table.</span></span> <span data-ttu-id="31d87-123">Bcp_setbulkmode を使用してクエリステートメントを一括コピーする場合は、BCP_HINT で bcp_control を呼び出す前に、このステートメントを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="31d87-123">When bcp_setbulkmode is used to bulk copy out a query statement, it must be called before calling bcp_control with BCP_HINT.</span></span>  
  
 <span data-ttu-id="31d87-124">bcp_setbulkmode は[bcp_setcolfmt](bcp-setcolfmt.md)と[bcp_columns](bcp-columns.md)を使用する代わりに、関数呼び出しごとに1つの列の形式を指定できるようにするためのものです。</span><span class="sxs-lookup"><span data-stu-id="31d87-124">bcp_setbulkmode is an alternative to using [bcp_setcolfmt](bcp-setcolfmt.md) and [bcp_columns](bcp-columns.md), which only let you specify the format of one column per function call.</span></span>  
  
 <span data-ttu-id="31d87-125">*property* パラメーターとして使用できる定数の一覧を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="31d87-125">The following table lists the constants for the *property* parameter.</span></span>  
  
|<span data-ttu-id="31d87-126">プロパティ</span><span class="sxs-lookup"><span data-stu-id="31d87-126">Property</span></span>|<span data-ttu-id="31d87-127">説明</span><span class="sxs-lookup"><span data-stu-id="31d87-127">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="31d87-128">BCP_OUT_CHARACTER_MODE</span><span class="sxs-lookup"><span data-stu-id="31d87-128">BCP_OUT_CHARACTER_MODE</span></span>|<span data-ttu-id="31d87-129">文字出力モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="31d87-129">Specifies character output mode.</span></span><br /><br /> <span data-ttu-id="31d87-130">BCP.EXE の-c オプションに対応し、プロパティがに設定されたを bcp_setcolfmt し `BCP_FMT_TYPE` `SQLCHARACTER` ます。</span><span class="sxs-lookup"><span data-stu-id="31d87-130">Corresponds to the -c option in BCP.EXE, and to bcp_setcolfmt with `BCP_FMT_TYPE` property set to `SQLCHARACTER`.</span></span>|  
|<span data-ttu-id="31d87-131">BCP_OUT_WIDE_CHARACTER_MODE</span><span class="sxs-lookup"><span data-stu-id="31d87-131">BCP_OUT_WIDE_CHARACTER_MODE</span></span>|<span data-ttu-id="31d87-132">Unicode 出力モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="31d87-132">Specifies Unicode output mode.</span></span><br /><br /> <span data-ttu-id="31d87-133">BCP.EXE の-w オプションと、プロパティがに設定された bcp_setcolfmt に対応し `BCP_FMT_TYPE` `SQLNCHAR` ます。</span><span class="sxs-lookup"><span data-stu-id="31d87-133">Corresponds to the -w option in BCP.EXE and bcp_setcolfmt with `BCP_FMT_TYPE` property set to `SQLNCHAR`.</span></span>|  
|<span data-ttu-id="31d87-134">BCP_OUT_NATIVE_TEXT_MODE</span><span class="sxs-lookup"><span data-stu-id="31d87-134">BCP_OUT_NATIVE_TEXT_MODE</span></span>|<span data-ttu-id="31d87-135">文字型以外にネイティブ型を指定し、文字型に Unicode を指定します。</span><span class="sxs-lookup"><span data-stu-id="31d87-135">Specifies native types for non-character types and Unicode for character types.</span></span><br /><br /> <span data-ttu-id="31d87-136">BCP.EXE の-N オプション bcp_setcolfmt と、 `BCP_FMT_TYPE` `SQLNCHAR` 列の型が文字列である場合はに設定されたプロパティ (文字列でない場合は既定値) に対応します。</span><span class="sxs-lookup"><span data-stu-id="31d87-136">Corresponds to the -N option in BCP.EXE and bcp_setcolfmt with `BCP_FMT_TYPE` property set to `SQLNCHAR` if the column type is a string (default if not a string).</span></span>|  
|<span data-ttu-id="31d87-137">BCP_OUT_NATIVE_MODE</span><span class="sxs-lookup"><span data-stu-id="31d87-137">BCP_OUT_NATIVE_MODE</span></span>|<span data-ttu-id="31d87-138">ネイティブ データベース型を指定します。</span><span class="sxs-lookup"><span data-stu-id="31d87-138">Specifies native database types.</span></span><br /><br /> <span data-ttu-id="31d87-139">BCP.EXE の-n オプションと `BCP_FMT_TYPE` 、プロパティが既定値に設定された bcp_setcolfmt に対応します。</span><span class="sxs-lookup"><span data-stu-id="31d87-139">Corresponds to the -n option in BCP.EXE and bcp_setcolfmt with `BCP_FMT_TYPE` property set to the default.</span></span>|  
  
 <span data-ttu-id="31d87-140">Bcp_setcolfmt、bcp_control、および bcp_readfmt を含む関数呼び出しのシーケンスと共に bcp_setbulkmode を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="31d87-140">You should not use bcp_setbulkmode with a sequence of function calls that includes bcp_setcolfmt, bcp_control, and bcp_readfmt.</span></span> <span data-ttu-id="31d87-141">たとえば、bcp_control (BCPTEXTFILE) および bcp_setbulkmode を呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="31d87-141">For example, you should not call bcp_control(BCPTEXTFILE) and bcp_setbulkmode.</span></span>  
  
 <span data-ttu-id="31d87-142">Bcp_setbulkmode と競合しない bcp_control オプションを bcp_control と bcp_setbulkmode を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="31d87-142">You can call bcp_control and bcp_setbulkmode for bcp_control options that do not conflict with bcp_setbulkmode.</span></span> <span data-ttu-id="31d87-143">たとえば、bcp_control (BCPFIRST) と bcp_setbulkmode を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="31d87-143">For example, you can call bcp_control(BCPFIRST) and bcp_setbulkmode.</span></span>  
  
 <span data-ttu-id="31d87-144">Bcp_setcolfmt、bcp_control、および bcp_readfmt を含む関数呼び出しのシーケンスを使用して bcp_setbulkmode を呼び出そうとすると、関数呼び出しの1つで、シーケンスエラーエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="31d87-144">If you attempt to call bcp_setbulkmode with a sequence of function calls that includes bcp_setcolfmt, bcp_control, and bcp_readfmt, one of the function calls will return a sequence error failure.</span></span> <span data-ttu-id="31d87-145">エラーの修正を選択した場合は、bcp_init を呼び出してすべての設定をリセットし、最初からやり直してください。</span><span class="sxs-lookup"><span data-stu-id="31d87-145">If you choose to correct the failure, call bcp_init to reset all the settings and start over.</span></span>  
  
 <span data-ttu-id="31d87-146">次の表に、関数のシーケンス エラーが発生する関数呼び出しの例をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="31d87-146">The following table presents some examples of function calls that result in a function sequence error:</span></span>  
  
 <span data-ttu-id="31d87-147">呼び出しシーケンス</span><span class="sxs-lookup"><span data-stu-id="31d87-147">Call sequence</span></span>  
  
```  
bcp_init("table", DB_IN);  
bcp_setbulkmode();  
```  
  
```  
bcp_init("table", DB_OUT);  
bcp_setbulkmode();  
bcp_readfmt();  
```  
  
```  
bcp_init(NULL, DB_OUT);  
bcp_control(BCPHINTS, "select ...");  
bcp_setbulkmode();  
```  
  
```  
bcp_init("table", DB_OUT);  
bcp_setbulkmode();  
bcp_setcolfmt();  
```  
  
```  
bcp_init("table", DB_OUT);  
bcp_control(BCPDELAYREADFMT, true);  
bcp_readfmt();  
bcp_setcolfmt();  
```  
  
```  
bcp_init(NULL, DB_OUT);  
bcp_control(BCPDELAYREADFMT, true);  
bcp_setbulkmode();  
bcp_control(BCPHINTS, "select ...");  
bcp_readfmt();  
```  
  
```  
bcp_init("table", DB_OUT);  
bcp_control(BCPDELAYREADFMT, true);  
bcp_columns();  
```  
  
```  
bcp_init("table", DB_OUT);  
bcp_control(BCPDELAYREADFMT, true);  
bcp_setcolfmt();  
```  
  
## <a name="example"></a><span data-ttu-id="31d87-148">例</span><span class="sxs-lookup"><span data-stu-id="31d87-148">Example</span></span>  
 <span data-ttu-id="31d87-149">次のサンプルでは、bcp_setbulkmode の異なる設定を使用して、4 つのファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="31d87-149">The following sample creates four files using different settings of bcp_setbulkmode.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="31d87-150">参照</span><span class="sxs-lookup"><span data-stu-id="31d87-150">See Also</span></span>  
 [<span data-ttu-id="31d87-151">一括コピー関数</span><span class="sxs-lookup"><span data-stu-id="31d87-151">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
