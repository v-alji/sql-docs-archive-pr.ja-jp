---
title: bcp_readfmt |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_readfmt
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_readfmt function
ms.assetid: 654001c8-ae9f-425c-b820-f0191bf89367
author: rothja
ms.author: jroth
ms.openlocfilehash: 37032ec276be8b914d73e834453cc5d87cdedbbe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634512"
---
# <a name="bcp_readfmt"></a><span data-ttu-id="a383b-102">bcp_readfmt</span><span class="sxs-lookup"><span data-stu-id="a383b-102">bcp_readfmt</span></span>
  <span data-ttu-id="a383b-103">指定されたフォーマット ファイルからデータ ファイル形式の定義を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="a383b-103">Reads a data file format definition from the specified format file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a383b-104">構文</span><span class="sxs-lookup"><span data-stu-id="a383b-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_readfmt (  
HDBC   
hdbc  
,  
LPCTSTR   
szFormatFile  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="a383b-105">引数</span><span class="sxs-lookup"><span data-stu-id="a383b-105">Arguments</span></span>  
 <span data-ttu-id="a383b-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="a383b-106">*hdbc*</span></span>  
 <span data-ttu-id="a383b-107">一括コピーが有効な ODBC 接続ハンドルです。</span><span class="sxs-lookup"><span data-stu-id="a383b-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="a383b-108">*szFormatFile*</span><span class="sxs-lookup"><span data-stu-id="a383b-108">*szFormatFile*</span></span>  
 <span data-ttu-id="a383b-109">データ ファイルの形式の値を含むファイルに関するパスとファイル名です。</span><span class="sxs-lookup"><span data-stu-id="a383b-109">Is the path and file name of the file containing the format values for the data file.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="a383b-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="a383b-110">Returns</span></span>  
 <span data-ttu-id="a383b-111">SUCCEED または FAIL。</span><span class="sxs-lookup"><span data-stu-id="a383b-111">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a383b-112">解説</span><span class="sxs-lookup"><span data-stu-id="a383b-112">Remarks</span></span>  
 <span data-ttu-id="a383b-113">は、 `bcp_readfmt` 書式設定値を読み取った後、 [bcp_columns](bcp-columns.md)と[bcp_colfmt](bcp-colfmt.md)に対する適切な呼び出しを行います。</span><span class="sxs-lookup"><span data-stu-id="a383b-113">After `bcp_readfmt` reads the format values, it makes the appropriate calls to [bcp_columns](bcp-columns.md) and [bcp_colfmt](bcp-colfmt.md).</span></span> <span data-ttu-id="a383b-114">ユーザーがフォーマット ファイルを解析し、このような呼び出しを行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a383b-114">There is no need for you to parse a format file and make these calls.</span></span>  
  
 <span data-ttu-id="a383b-115">フォーマットファイルを永続化するには、 [bcp_writefmt](bcp-writefmt.md)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a383b-115">To persist a format file, call [bcp_writefmt](bcp-writefmt.md).</span></span> <span data-ttu-id="a383b-116">の呼び出しで `bcp_readfmt` は、保存された形式を参照できます。</span><span class="sxs-lookup"><span data-stu-id="a383b-116">Calls to `bcp_readfmt` can reference saved formats.</span></span> <span data-ttu-id="a383b-117">詳細については、「 [bcp_init](bcp-init.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a383b-117">For more information, see [bcp_init](bcp-init.md).</span></span>  
  
 <span data-ttu-id="a383b-118">また、一括コピーユーティリティ (**bcp**) では、で参照できるファイルにユーザー定義データ形式を保存することもでき `bcp_readfmt` ます。</span><span class="sxs-lookup"><span data-stu-id="a383b-118">Alternately, the bulk-copy utility (**bcp**) can save user-defined data formats in files that can be referenced by `bcp_readfmt`.</span></span> <span data-ttu-id="a383b-119">**Bcp**ユーティリティと**bcp**データフォーマットファイルの構造の詳細については、「[データ &#40;SQL Server&#41;の一括インポートと一括エクスポート](../import-export/bulk-import-and-export-of-data-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a383b-119">For more information about the **bcp** utility and the structure of **bcp** data format files, see [Bulk Import and Export of Data &#40;SQL Server&#41;](../import-export/bulk-import-and-export-of-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="a383b-120">`BCPDELAYREADFMT` [Bcp_control](bcp-control.md)の*eOption*パラメーターの値によって、bcp_readfmt の動作が変更されます。</span><span class="sxs-lookup"><span data-stu-id="a383b-120">The `BCPDELAYREADFMT` value of the *eOption* parameter of [bcp_control](bcp-control.md) modifies the behavior of bcp_readfmt.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a383b-121">フォーマットファイルは、 **bcp**ユーティリティのバージョン4.2 以降で作成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a383b-121">The format file must have been produced by version 4.2 or later of the **bcp** utility.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a383b-122">例</span><span class="sxs-lookup"><span data-stu-id="a383b-122">Example</span></span>  
  
```  
// Variables like henv not specified.  
HDBC      hdbc;  
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
if (bcp_init(hdbc, _T("myTable"), _T("myData.csv"),  
   _T("myErrors"),    DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_readfmt(hdbc, _T("myFmtFile.fmt")) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_exec(hdbc, &nRowsProcessed) == SUCCEED)  
   {  
   cout << nRowsProcessed << " rows copied to SQL Server\n";  
   }  
  
// Carry on.  
```  
  
## <a name="see-also"></a><span data-ttu-id="a383b-123">参照</span><span class="sxs-lookup"><span data-stu-id="a383b-123">See Also</span></span>  
 [<span data-ttu-id="a383b-124">一括コピー関数</span><span class="sxs-lookup"><span data-stu-id="a383b-124">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
