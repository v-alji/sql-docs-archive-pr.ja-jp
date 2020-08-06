---
title: bcp_init |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_init
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_init function
ms.assetid: 6a25862c-7f31-4873-ab65-30f3abde89d2
author: rothja
ms.author: jroth
ms.openlocfilehash: 72d48b2a07e425e0863084c700c4de93d2776739
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634516"
---
# <a name="bcp_init"></a><span data-ttu-id="c5c06-102">bcp_init</span><span class="sxs-lookup"><span data-stu-id="c5c06-102">bcp_init</span></span>
  <span data-ttu-id="c5c06-103">一括コピー操作を初期化します。</span><span class="sxs-lookup"><span data-stu-id="c5c06-103">Initializes the bulk copy operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5c06-104">構文</span><span class="sxs-lookup"><span data-stu-id="c5c06-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_init (  
HDBC   
hdbc  
,  
LPCTSTR   
szTable  
,  
LPCTSTR   
szDataFile  
,  
LPCTSTR   
szErrorFile  
,  
INT   
eDirection  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="c5c06-105">引数</span><span class="sxs-lookup"><span data-stu-id="c5c06-105">Arguments</span></span>  
 <span data-ttu-id="c5c06-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="c5c06-106">*hdbc*</span></span>  
 <span data-ttu-id="c5c06-107">一括コピーが有効な ODBC 接続ハンドルです。</span><span class="sxs-lookup"><span data-stu-id="c5c06-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="c5c06-108">*szTable*</span><span class="sxs-lookup"><span data-stu-id="c5c06-108">*szTable*</span></span>  
 <span data-ttu-id="c5c06-109">コピー操作の対象になるデータベース テーブルの名前です。</span><span class="sxs-lookup"><span data-stu-id="c5c06-109">Is the name of the database table to be copied into or out of.</span></span> <span data-ttu-id="c5c06-110">この名前には、データベース名または所有者名を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="c5c06-110">This name can also include the database name or the owner name.</span></span> <span data-ttu-id="c5c06-111">たとえば、 **gracie**のようになります。 **タイトル**、 **gracie**、**タイトル**は、すべて有効なテーブル名です。</span><span class="sxs-lookup"><span data-stu-id="c5c06-111">For example, **pubs.gracie.titles**, **pubs..titles**, **gracie.titles**, and **titles** are all legal table names.</span></span>  
  
 <span data-ttu-id="c5c06-112">*Edirection*が DB_OUT の場合、 *sztable*をデータベースビューの名前にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c5c06-112">If *eDirection* is DB_OUT, *szTable* can also be the name of a database view.</span></span>  
  
 <span data-ttu-id="c5c06-113">*Edirection*が DB_OUT で、 [bcp_exec](bcp-exec.md)を呼び出す前に[BCP_CONTROL](bcp-control.md)を使用して select ステートメントを指定した場合は、 **bcp_init**_sztable_を NULL に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5c06-113">If *eDirection* is DB_OUT and a SELECT statement is specified using [bcp_control](bcp-control.md) before [bcp_exec](bcp-exec.md) is called, **bcp_init**_szTable_ must be set to NULL.</span></span>  
  
 <span data-ttu-id="c5c06-114">*szDataFile*</span><span class="sxs-lookup"><span data-stu-id="c5c06-114">*szDataFile*</span></span>  
 <span data-ttu-id="c5c06-115">コピー操作の対象になるユーザー ファイルの名前です。</span><span class="sxs-lookup"><span data-stu-id="c5c06-115">Is the name of the user file to be copied into or out of.</span></span> <span data-ttu-id="c5c06-116">[Bcp_sendrow](bcp-sendrow.md)を使用して変数からデータを直接コピーする場合は、 *SZDATAFILE ファイル*を NULL に設定します。</span><span class="sxs-lookup"><span data-stu-id="c5c06-116">If data is being copied directly from variables by using [bcp_sendrow](bcp-sendrow.md), set *szDataFile* to NULL.</span></span>  
  
 <span data-ttu-id="c5c06-117">*szErrorFile*</span><span class="sxs-lookup"><span data-stu-id="c5c06-117">*szErrorFile*</span></span>  
 <span data-ttu-id="c5c06-118">進行状況メッセージ、エラー メッセージ、および何かの理由でユーザー ファイルからテーブルにコピーできなかった任意の行のコピーを書き込むエラー ファイルの名前です。</span><span class="sxs-lookup"><span data-stu-id="c5c06-118">Is the name of the error file to be filled with progress messages, error messages, and copies of any rows that, for any reason, could not be copied from a user file to a table.</span></span> <span data-ttu-id="c5c06-119">NULL が*Szerrorfile*として渡された場合、エラーファイルは使用されません。</span><span class="sxs-lookup"><span data-stu-id="c5c06-119">If NULL is passed as *szErrorFile*, no error file is used.</span></span>  
  
 <span data-ttu-id="c5c06-120">*eDirection*</span><span class="sxs-lookup"><span data-stu-id="c5c06-120">*eDirection*</span></span>  
 <span data-ttu-id="c5c06-121">コピーの方向です。この値は DB_IN または DB_OUT になります。</span><span class="sxs-lookup"><span data-stu-id="c5c06-121">Is the direction of the copy, either DB_IN or DB_OUT.</span></span> <span data-ttu-id="c5c06-122">DB_IN は、プログラム変数またはユーザー ファイルからテーブルへのコピーを示します。</span><span class="sxs-lookup"><span data-stu-id="c5c06-122">DB_IN indicates a copy from program variables or a user file to a table.</span></span> <span data-ttu-id="c5c06-123">DB_OUT は、データベース テーブルからユーザー ファイルへのコピーを示します。</span><span class="sxs-lookup"><span data-stu-id="c5c06-123">DB_OUT indicates a copy from a database table to a user file.</span></span> <span data-ttu-id="c5c06-124">DB_OUT を指定する場合は、ユーザー ファイル名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5c06-124">You must specify a user file name with DB_OUT.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="c5c06-125">戻り値</span><span class="sxs-lookup"><span data-stu-id="c5c06-125">Returns</span></span>  
 <span data-ttu-id="c5c06-126">SUCCEED または FAIL。</span><span class="sxs-lookup"><span data-stu-id="c5c06-126">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5c06-127">解説</span><span class="sxs-lookup"><span data-stu-id="c5c06-127">Remarks</span></span>  
 <span data-ttu-id="c5c06-128">他の一括コピー関数を呼び出す前に**bcp_init**を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c5c06-128">Call **bcp_init** before calling any other bulk-copy function.</span></span> <span data-ttu-id="c5c06-129">**bcp_init**は、ワークステーションとの間のデータの一括コピーに必要な初期化を実行し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="c5c06-129">**bcp_init** performs the necessary initializations for a bulk copy of data between the workstation and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="c5c06-130">**Bcp_init**関数は、一括コピー関数で使用できるように ODBC 接続ハンドルが有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5c06-130">The **bcp_init** function must be provided with an ODBC connection handle enabled for use with bulk copy functions.</span></span> <span data-ttu-id="c5c06-131">ハンドルを有効にするには、SQL_COPT_SS_BCP が割り当てられていて、接続されていない接続ハンドルで SQL_BCP_ON に設定されている[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="c5c06-131">To enable the handle, use [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_BCP set to SQL_BCP_ON on an allocated, but not connected, connection handle.</span></span> <span data-ttu-id="c5c06-132">接続済みのハンドルの属性を割り当てようとすると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="c5c06-132">Attempting to assign the attribute on a connected handle results in an error.</span></span>  
  
 <span data-ttu-id="c5c06-133">データファイルを指定すると、 **bcp_init**によって、データファイルではなく、データベースのソースまたは対象のテーブルの構造が調べられます。</span><span class="sxs-lookup"><span data-stu-id="c5c06-133">When a data file is specified, **bcp_init** examines the structure of the database source or target table, not the data file.</span></span> <span data-ttu-id="c5c06-134">**bcp_init**は、データベーステーブル、ビュー、または SELECT 結果セットの各列に基づいて、データファイルのデータ形式値を指定します。</span><span class="sxs-lookup"><span data-stu-id="c5c06-134">**bcp_init** specifies data format values for the data file based on each column in the database table, view, or SELECT result set.</span></span> <span data-ttu-id="c5c06-135">このデータ形式値には、各列のデータ型、長さや NULL のインジケーターとターミネータのバイト文字列がデータ内に存在するかどうか、および固定長データ型の幅の指定などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c5c06-135">This specification includes the data type of each column, the presence or absence of a length or null indicator and terminator byte strings in the data, and the width of fixed-length data types.</span></span> <span data-ttu-id="c5c06-136">**bcp_init**は、次のように値を設定します。</span><span class="sxs-lookup"><span data-stu-id="c5c06-136">**bcp_init** sets these values as follows:</span></span>  
  
-   <span data-ttu-id="c5c06-137">指定するデータ型は、データベース テーブル、ビュー、または SELECT 結果セット内の列のデータ型です。</span><span class="sxs-lookup"><span data-stu-id="c5c06-137">The data type specified is the data type of the column in the database table, view, or SELECT result set.</span></span> <span data-ttu-id="c5c06-138">データ型は、sqlncli.h に指定されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ネイティブ データ型によって列挙されます。</span><span class="sxs-lookup"><span data-stu-id="c5c06-138">The data type is enumerated by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native data types specified in sqlncli.h.</span></span> <span data-ttu-id="c5c06-139">データ自体はそのコンピューターの形式で表されます。</span><span class="sxs-lookup"><span data-stu-id="c5c06-139">Data itself is represented in its computer form.</span></span> <span data-ttu-id="c5c06-140">つまり、**整数**データ型の列のデータは、データファイルを作成したコンピューターに基づいて、ビッグエンディアンまたはリトルエンディアンの4バイトのシーケンスによって表されます。</span><span class="sxs-lookup"><span data-stu-id="c5c06-140">That is, data from a column of **integer** data type is represented by a four-byte sequence that is big-or little-endian based on the computer that created the data file.</span></span>  
  
-   <span data-ttu-id="c5c06-141">データベースのデータ型が固定長の場合は、データ ファイルのデータも固定長になります。</span><span class="sxs-lookup"><span data-stu-id="c5c06-141">If a database data type is fixed in length, the data file data is also fixed in length.</span></span> <span data-ttu-id="c5c06-142">データを処理する一括コピー関数 ( [bcp_exec](bcp-exec.md)など) では、データ行の解析で、データファイル内のデータの長さが、データベーステーブル、ビュー、または選択列リストで指定されたデータの長さと同一である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5c06-142">Bulk-copy functions that process data (for example, [bcp_exec](bcp-exec.md)) parse data rows expecting the length of the data in the data file to be identical to the length of the data specified in the database table, view, or SELECT column list.</span></span> <span data-ttu-id="c5c06-143">たとえば、 **char (13)** として定義されているデータベース列のデータは、ファイル内のデータ行ごとに13文字で表す必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5c06-143">For example, data for a database column defined as **char(13)** must be represented by 13 characters for each row of data in the file.</span></span> <span data-ttu-id="c5c06-144">データベース列で NULL 値を許容する場合は、固定長データにプレフィックスとして NULL インジケーターを付けることができます。</span><span class="sxs-lookup"><span data-stu-id="c5c06-144">Fixed-length data can be prefixed with a null indicator if the database column allows null values.</span></span>  
  
-   <span data-ttu-id="c5c06-145">ターミネータ バイト シーケンスを定義すると、ターミネータ バイト シーケンスの長さが 0 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="c5c06-145">When terminator-byte sequence is defined, the length of the terminator-byte sequence is set to 0.</span></span>  
  
-   <span data-ttu-id="c5c06-146">データを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にコピーするときは、データ ファイルにデータベース テーブル内の各列に格納するデータが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5c06-146">When copying to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the data file must have data for each column in the database table.</span></span> <span data-ttu-id="c5c06-147">データを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からコピーするときは、データベース テーブル、ビュー、または SELECT 結果セット内のすべての列のデータがデータ ファイルにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="c5c06-147">When copying from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], data from all columns in the database table, view, or SELECT result set are copied to the data file.</span></span>  
  
-   <span data-ttu-id="c5c06-148">データを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にコピーするときは、データ ファイル内の列の序数位置がデータベース テーブル内の列の序数位置と同じであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="c5c06-148">When copying to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the ordinal position of a column in the data file must be identical to the ordinal position of the column in the database table.</span></span> <span data-ttu-id="c5c06-149">からコピーする場合 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、 **bcp_exec**は、データベーステーブル内の列の序数位置に基づいてデータを格納します。</span><span class="sxs-lookup"><span data-stu-id="c5c06-149">When copying from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], **bcp_exec** places data based on the ordinal position of the column in the database table.</span></span>  
  
-   <span data-ttu-id="c5c06-150">データベースのデータ型が可変長 (たとえば、 **varbinary (22)**) の場合、またはデータベース列に null 値を含めることができる場合は、データファイル内のデータの先頭に長さ/null インジケーターが付きます。</span><span class="sxs-lookup"><span data-stu-id="c5c06-150">If a database data type is variable in length (for example, **varbinary(22)**) or if a database column can contain null values, data in the data file is prefixed by a length/null indicator.</span></span> <span data-ttu-id="c5c06-151">インジケーターの幅は、データ型と一括コピーのバージョンによって異なります。</span><span class="sxs-lookup"><span data-stu-id="c5c06-151">The width of the indicator varies based on the data type and version of bulk copy.</span></span>  
  
 <span data-ttu-id="c5c06-152">データファイルに対して指定されたデータ形式の値を変更するには、 [bcp_columns](bcp-columns.md)を呼び出し、 [bcp_colfmt](bcp-colfmt.md)します。</span><span class="sxs-lookup"><span data-stu-id="c5c06-152">To change data format values specified for a data file, call [bcp_columns](bcp-columns.md) and [bcp_colfmt](bcp-colfmt.md).</span></span>  
  
 <span data-ttu-id="c5c06-153">インデックスを含まないテーブルの場合は、データベース復旧モデルを SIMPLE または BULK_LOGGED に設定することで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への一括コピーを最適化できます。</span><span class="sxs-lookup"><span data-stu-id="c5c06-153">Bulk copies to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can be optimized for tables that do not contain indexes by setting the database recovery model to SIMPLE or BULK_LOGGED.</span></span> <span data-ttu-id="c5c06-154">詳細については、「[一括インポートで最小ログ記録を行うための前提条件](../import-export/prerequisites-for-minimal-logging-in-bulk-import.md)」および「 [ALTER database](/sql/t-sql/statements/alter-database-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5c06-154">For more information, see [Prerequisites for Minimal Logging in Bulk Import](../import-export/prerequisites-for-minimal-logging-in-bulk-import.md) and [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
 <span data-ttu-id="c5c06-155">データファイルが使用されていない場合は、 [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)を呼び出して、データファイルと各列のメモリ内の形式と場所を指定してから、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [bcp_sendrow](bcp-sendrow.md)を使用してデータ行をにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5c06-155">If no data file is used, you must call [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) to specify the format and location in memory of the data fsor each column, then copy data rows to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using [bcp_sendrow](bcp-sendrow.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5c06-156">例</span><span class="sxs-lookup"><span data-stu-id="c5c06-156">Example</span></span>  
 <span data-ttu-id="c5c06-157">このサンプルでは、ODBC bcp_init 関数をフォーマット ファイルと共に使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c5c06-157">This sample shows how to use the ODBC bcp_init function with a format file.</span></span>  
  
 <span data-ttu-id="c5c06-158">この C++ コードをコンパイルして実行する前に、次の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5c06-158">Before you compile and run the C++ code, you need to do the following:</span></span>  
  
-   <span data-ttu-id="c5c06-159">Test という ODBC データ ソースを作成し、</span><span class="sxs-lookup"><span data-stu-id="c5c06-159">Create an ODBC data source called Test.</span></span> <span data-ttu-id="c5c06-160">任意のデータベースに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="c5c06-160">You can associate this data source with any database.</span></span>  
  
-   <span data-ttu-id="c5c06-161">そのデータベースに対して次の [!INCLUDE[tsql](../../includes/tsql-md.md)] を実行します。</span><span class="sxs-lookup"><span data-stu-id="c5c06-161">Run the following [!INCLUDE[tsql](../../includes/tsql-md.md)] on the database:</span></span>  
  
    ```  
    CREATE TABLE BCPDate (cola int, colb datetime);  
    ```  
  
-   <span data-ttu-id="c5c06-162">アプリケーションを実行するディレクトリに Bcpfmt.fmt というファイルを追加して、そのファイルに次の内容を追加します。</span><span class="sxs-lookup"><span data-stu-id="c5c06-162">In the directory where you will run the application, add a file called Bcpfmt.fmt, and add this to the file:</span></span>  
  
    ```  
    8.0  
    2  
    1SQLCHAR04"\t"1colaSQL_Latin1_General_Cp437_Bin  
    2SQLCHAR08"\r\n"2colbSQL_Latin1_General_Cp437_Bin  
    ```  
  
-   <span data-ttu-id="c5c06-163">アプリケーションを実行するディレクトリに Bcpodbc.bcp というファイルを追加して、そのファイルに次の内容を追加します。</span><span class="sxs-lookup"><span data-stu-id="c5c06-163">In the directory where you will run the application, add a file called Bcpodbc.bcp, and add this to the file:</span></span>  
  
    ```  
    1  
    2  
    ```  
  
 <span data-ttu-id="c5c06-164">以上で、この C++ コードをコンパイルして実行できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="c5c06-164">Now you are ready to compile and run the C++ code.</span></span>  
  
```  
// compile with: odbc32.lib sqlncli11.lib  
#include <stdio.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
SQLHENV henv = SQL_NULL_HENV;  
HDBC hdbc1 = SQL_NULL_HDBC;   
  
void Cleanup() {  
   if (hdbc1 != SQL_NULL_HDBC) {  
      SQLDisconnect(hdbc1);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   }  
  
   if (henv != SQL_NULL_HENV)  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
int main() {  
   RETCODE retcode;  
   SDWORD cRows;  
  
   // Allocate the ODBC environment and save handle.  
   retcode = SQLAllocHandle (SQL_HANDLE_ENV, NULL, &henv);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(Env) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Notify ODBC that this is an ODBC 3.0 app.  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER) SQL_OV_ODBC3, SQL_IS_INTEGER);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetEnvAttr(ODBC version) Failed\n\n");  
      Cleanup();  
      return(9);      
   }  
  
   // Allocate ODBC connection handle, set BCP mode, and connect.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   retcode = SQLSetConnectAttr(hdbc1, SQL_COPT_SS_BCP, (void *)SQL_BCP_ON, SQL_IS_INTEGER);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetConnectAttr(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Sample uses Integrated Security. Create SQL Server DSN using Windows NT authentication.  
   retcode = SQLConnect(hdbc1, (UCHAR*)"Test", SQL_NTS, (UCHAR*)"", SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Initialize the bulk copy.  
   retcode = bcp_init(hdbc1, "BCPDate", "BCPODBC.bcp", NULL, DB_IN);  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_init(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Read the format file.  
   retcode = bcp_readfmt(hdbc1, "BCPFMT.fmt");  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_readfmt(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Execute the bulk copy.  
   retcode = bcp_exec(hdbc1, &cRows);  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_exec(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   printf("Number of rows bulk copied in = %d.\n", cRows);  
  
   // Cleanup  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="c5c06-165">参照</span><span class="sxs-lookup"><span data-stu-id="c5c06-165">See Also</span></span>  
 [<span data-ttu-id="c5c06-166">一括コピー関数</span><span class="sxs-lookup"><span data-stu-id="c5c06-166">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
