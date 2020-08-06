---
title: bcp_moretext |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_moretext
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_moretext function
ms.assetid: 23e98015-a8e4-4434-9b3f-9c7350cf965f
author: rothja
ms.author: jroth
ms.openlocfilehash: 00c0eb1c8739e94380b12034cebc70d8e22b79c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634515"
---
# <a name="bcp_moretext"></a><span data-ttu-id="b7782-102">bcp_moretext</span><span class="sxs-lookup"><span data-stu-id="b7782-102">bcp_moretext</span></span>
  <span data-ttu-id="b7782-103">長い可変長データ型の値の一部を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に送信します。</span><span class="sxs-lookup"><span data-stu-id="b7782-103">Sends part of a long, variable-length data type value to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7782-104">構文</span><span class="sxs-lookup"><span data-stu-id="b7782-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_moretext (  
HDBC   
hdbc  
,  
DBINT   
cbData  
,  
LPCBYTE   
pData  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="b7782-105">引数</span><span class="sxs-lookup"><span data-stu-id="b7782-105">Arguments</span></span>  
 <span data-ttu-id="b7782-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="b7782-106">*hdbc*</span></span>  
 <span data-ttu-id="b7782-107">一括コピーが有効な ODBC 接続ハンドルです。</span><span class="sxs-lookup"><span data-stu-id="b7782-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="b7782-108">*cbData*</span><span class="sxs-lookup"><span data-stu-id="b7782-108">*cbData*</span></span>  
 <span data-ttu-id="b7782-109">*PData*によって参照されるデータから SQL Server にコピーされるデータのバイト数を指定します。</span><span class="sxs-lookup"><span data-stu-id="b7782-109">Is the number of bytes of data being copied to SQL Server from the data referenced by *pData*.</span></span> <span data-ttu-id="b7782-110">値 SQL_NULL_DATA は、NULL を示します。</span><span class="sxs-lookup"><span data-stu-id="b7782-110">A value of SQL_NULL_DATA indicates NULL.</span></span>  
  
 <span data-ttu-id="b7782-111">*pData*</span><span class="sxs-lookup"><span data-stu-id="b7782-111">*pData*</span></span>  
 <span data-ttu-id="b7782-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に送信する、サポートされている長い可変長データ チャンクへのポインターです。</span><span class="sxs-lookup"><span data-stu-id="b7782-112">Is a pointer to the supported, long, variable-length data chunk to be sent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="returns"></a><span data-ttu-id="b7782-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="b7782-113">Returns</span></span>  
 <span data-ttu-id="b7782-114">SUCCEED または FAIL。</span><span class="sxs-lookup"><span data-stu-id="b7782-114">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7782-115">解説</span><span class="sxs-lookup"><span data-stu-id="b7782-115">Remarks</span></span>  
 <span data-ttu-id="b7782-116">この関数を[bcp_bind](bcp-bind.md)および[bcp_sendrow](bcp-sendrow.md)と組み合わせて使用すると、長い可変長のデータ値を多数の小さなチャンクで SQL Server にコピーできます。</span><span class="sxs-lookup"><span data-stu-id="b7782-116">This function can be used in conjunction with [bcp_bind](bcp-bind.md) and [bcp_sendrow](bcp-sendrow.md) to copy long, variable-length data values to SQL Server in a number of smaller chunks.</span></span> <span data-ttu-id="b7782-117">**bcp_moretext**は、、、、、、 `text` `ntext` `image` `varchar(max)` `nvarchar(max)` `varbinary(max)` 、ユーザー定義型 (UDT)、および XML の SQL Server 各データ型を持つ列で使用できます。</span><span class="sxs-lookup"><span data-stu-id="b7782-117">**bcp_moretext** can be used with columns that have the following SQL Server data types: `text`, `ntext`, `image`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, user-defined type (UDT), and XML.</span></span> <span data-ttu-id="b7782-118">**bcp_moretext**は、データ変換をサポートしていません。指定されたデータは、ターゲット列のデータ型と一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7782-118">**bcp_moretext** does not support data conversions, the data supplied must match the data type of the target column.</span></span>  
  
 <span data-ttu-id="b7782-119">**Bcp_moretext**でサポートされているデータ型に対して null 以外の*pData*パラメーターを指定して**bcp_bind**を呼び出すと、は `bcp_sendrow` 長さに関係なく、データ値全体を送信します。</span><span class="sxs-lookup"><span data-stu-id="b7782-119">If **bcp_bind** is called with a nonNULL *pData* parameter for data types that are supported by **bcp_moretext**, `bcp_sendrow` sends the entire data value, regardless of length.</span></span> <span data-ttu-id="b7782-120">ただし、 **bcp_bind**がサポートされているデータ型に対して NULL の*pData*パラメーターを持っている場合、 **bcp_moretext**を使用して、 `bcp_sendrow` データが存在するバインド列が処理されたことを示すから正常に返された直後にデータをコピーできます。</span><span class="sxs-lookup"><span data-stu-id="b7782-120">If, however, **bcp_bind** has a NULL *pData* parameter for supported data types, **bcp_moretext** can be used to copy data immediately after a successful return from `bcp_sendrow` indicating that any bound columns with data present have been processed.</span></span>  
  
 <span data-ttu-id="b7782-121">**Bcp_moretext**を使用して、サポートされているデータ型の列を1つの行で送信する場合は、その行でサポートされている他のすべてのデータ型の列を送信するためにも使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7782-121">If you use **bcp_moretext** to send one supported data type column in a row, you must also use it to send all other supported data type columns in the row.</span></span> <span data-ttu-id="b7782-122">列はスキップされません。</span><span class="sxs-lookup"><span data-stu-id="b7782-122">No columns may be skipped.</span></span> <span data-ttu-id="b7782-123">サポートされるデータ型は、SQLTEXT、SQLNTEXT、SQLIMAGE、SQLUDT、および SQLXML です。</span><span class="sxs-lookup"><span data-stu-id="b7782-123">Supported data types are SQLTEXT, SQLNTEXT, SQLIMAGE, SQLUDT and SQLXML.</span></span> <span data-ttu-id="b7782-124">列の型が varchar(max)、nvarchar(max)、または varbinary(max) の場合、SQLCHARACTER、SQLVARCHAR、SQNCHAR、SQLBINARY、SQLVARBINARY も、サポート対象となります。</span><span class="sxs-lookup"><span data-stu-id="b7782-124">SQLCHARACTER, SQLVARCHAR, SQNCHAR, SQLBINARY and SQLVARBINARY also fall into this category if the column is a varchar(max), nvarchar(max) or varbinary(max), respectively.</span></span>  
  
 <span data-ttu-id="b7782-125">**Bcp_bind**または[bcp_collen](bcp-collen.md)のいずれかを呼び出すと、SQL Server 列にコピーされるすべてのデータパーツの合計長が設定されます。</span><span class="sxs-lookup"><span data-stu-id="b7782-125">Calling either **bcp_bind** or [bcp_collen](bcp-collen.md) sets the total length of all data parts to be copied to the SQL Server column.</span></span> <span data-ttu-id="b7782-126">**Bcp_bind**への呼び出しで指定されたよりも多くのバイト SQL Server を送信しようとしたか、 `bcp_collen` エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="b7782-126">An attempt to send SQL Server more bytes than specified in the call to **bcp_bind** or `bcp_collen` generates an error.</span></span> <span data-ttu-id="b7782-127">このエラーは、たとえば、 `bcp_collen` SQL Server の列の使用可能なデータの長さを4500に設定するために使用されたアプリケーションで、 `text` データバッファーの長さが1000バイトであることを各呼び出しに対して示す**bcp_moretext** 5 回呼び出された場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="b7782-127">This error would arise, for example, in an application which used `bcp_collen` to set the length of available data for an SQL Server `text` column to 4500, then called **bcp_moretext** five times while indicating on each call that the data buffer length was 1000 bytes long.</span></span>  
  
 <span data-ttu-id="b7782-128">コピーされた行に複数の長い可変長列が含まれている場合、 **bcp_moretext**は最初にそのデータを最も低い順序の列に送信し、次に、その後に最も低い2番目の列に番号が付けられます。</span><span class="sxs-lookup"><span data-stu-id="b7782-128">If a copied row contains more than one long, variable-length column, **bcp_moretext** first sends its data to the lowest ordinally numbered column, followed by the next lowest ordinally numbered column, and so on.</span></span> <span data-ttu-id="b7782-129">コピーするデータの合計長を正しく設定することが重要です。</span><span class="sxs-lookup"><span data-stu-id="b7782-129">Correct setting of the total length of expected data is important.</span></span> <span data-ttu-id="b7782-130">長さの設定以外に、一括コピーによって列のすべてのデータを受け取ったことを示す方法はありません。</span><span class="sxs-lookup"><span data-stu-id="b7782-130">There is no way to signal, outside of the length setting, that all data for a column has been received by bulk copy.</span></span>  
  
 <span data-ttu-id="b7782-131">`var(max)`Bcp_sendrow と bcp_moretext を使用して値がサーバーに送信される場合、列の長さを設定するために bcp_collen を呼び出す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b7782-131">When `var(max)` values are sent to the server using bcp_sendrow and bcp_moretext, it is not necessary to call bcp_collen to set the column length.</span></span> <span data-ttu-id="b7782-132">代わりに、これらの型に対してのみ、長さ0の bcp_sendrow を呼び出すことによって値が終了します。</span><span class="sxs-lookup"><span data-stu-id="b7782-132">Instead, for these types only, the value is terminated by calling bcp_sendrow with a length of zero.</span></span>  
  
 <span data-ttu-id="b7782-133">通常、アプリケーションでは `bcp_sendrow` 、ループ内でを呼び出し、 **bcp_moretext**して、多数のデータ行を送信します。</span><span class="sxs-lookup"><span data-stu-id="b7782-133">An application normally calls `bcp_sendrow` and **bcp_moretext** within loops to send a number of rows of data.</span></span> <span data-ttu-id="b7782-134">2つの列を含むテーブルに対してこれを行う方法の概要を次に示し `text` ます。</span><span class="sxs-lookup"><span data-stu-id="b7782-134">Here's an outline of how to do this for a table containing two `text` columns:</span></span>  
  
```  
while (there are still rows to send)  
{  
bcp_sendrow(...);  
  
for (all the data in the first varbinary(max) column)  
bcp_moretext(...);  
bcp_moretext(hdbc, 0, NULL);  
  
for (all the data in the second varbinary(max) column)  
bcp_moretext(...);  
bcp_moretext(hdbc, 0, NULL);  
  
}  
  
```  
  
## <a name="example"></a><span data-ttu-id="b7782-135">例</span><span class="sxs-lookup"><span data-stu-id="b7782-135">Example</span></span>  
 <span data-ttu-id="b7782-136">この例では、 **bcp_bind**とで**bcp_moretext**を使用する方法を示し `bcp_sendrow` ます。</span><span class="sxs-lookup"><span data-stu-id="b7782-136">This example shows how to use **bcp_moretext** with **bcp_bind** and `bcp_sendrow`:</span></span>  
  
```  
// Variables like henv not specified.  
HDBC      hdbc;  
DBINT      idRow = 5;  
char*      pPart1 = "This text value isn't very long,";  
char*      pPart2 = " but it's broken into three parts";  
char*      pPart3 = " anyhow.";  
DBINT      cbAllParts;  
DBINT      nRowsProcessed;  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source, return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bulk copy.   
if (bcp_init(hdbc, "comdb..articles", NULL, NULL, DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Bind program variables to table columns.   
if (bcp_bind(hdbc, (LPCBYTE) &idRow, 0, SQL_VARLEN_DATA, NULL, 0,  
   SQLINT4, 1)    == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
cbAllParts = (DBINT) (strnlen(pPart1, sizeof(pPart1) + 1) + strnlen(pPart2, sizeof(pPart2) + 1) + strnlen(pPart3, sizeof(pPart3) + 1));  
if (bcp_bind(hdbc, NULL, 0, cbAllParts, NULL, 0, SQLTEXT, 2) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Send this row, with the text value broken into three chunks.   
if (bcp_sendrow(hdbc) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_moretext(hdbc, (DBINT) strnlen(pPart1, sizeof(pPart1) + 1), pPart1) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
if (bcp_moretext(hdbc, (DBINT) strnlen(pPart2, sizeof(pPart2) + 1), pPart2) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
if (bcp_moretext(hdbc, (DBINT) strnlen(pPart3, sizeof(pPart3) + 1), pPart3) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// All done. Get the number of rows processed (should be one).  
nRowsProcessed = bcp_done(hdbc);  
  
// Carry on.  
```  
  
## <a name="see-also"></a><span data-ttu-id="b7782-137">参照</span><span class="sxs-lookup"><span data-stu-id="b7782-137">See Also</span></span>  
 [<span data-ttu-id="b7782-138">一括コピー関数</span><span class="sxs-lookup"><span data-stu-id="b7782-138">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
