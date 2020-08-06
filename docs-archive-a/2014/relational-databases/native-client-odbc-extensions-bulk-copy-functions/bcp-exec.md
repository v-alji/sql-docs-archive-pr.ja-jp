---
title: bcp_exec |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_exec
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_exec function
ms.assetid: b23ea2cc-8545-4873-b0c1-57e76b0a3a7b
author: rothja
ms.author: jroth
ms.openlocfilehash: f925c6cb1e3a36f79ba4f560a06c5b6d499ece4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630988"
---
# <a name="bcp_exec"></a><span data-ttu-id="92bea-102">bcp_exec</span><span class="sxs-lookup"><span data-stu-id="92bea-102">bcp_exec</span></span>
  <span data-ttu-id="92bea-103">データベース テーブルとユーザー ファイル間でデータの完全な一括コピーを実行します。</span><span class="sxs-lookup"><span data-stu-id="92bea-103">Executes a complete bulk copy of data between a database table and a user file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92bea-104">構文</span><span class="sxs-lookup"><span data-stu-id="92bea-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_exec (  
HDBC   
hdbc  
,  
LPDBINT   
pnRowsProcessed  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="92bea-105">引数</span><span class="sxs-lookup"><span data-stu-id="92bea-105">Arguments</span></span>  
 <span data-ttu-id="92bea-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="92bea-106">*hdbc*</span></span>  
 <span data-ttu-id="92bea-107">一括コピーが有効な ODBC 接続ハンドルです。</span><span class="sxs-lookup"><span data-stu-id="92bea-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="92bea-108">*pnRowsProcessed*</span><span class="sxs-lookup"><span data-stu-id="92bea-108">*pnRowsProcessed*</span></span>  
 <span data-ttu-id="92bea-109">DBINT へのポインターです。</span><span class="sxs-lookup"><span data-stu-id="92bea-109">Is a pointer to a DBINT.</span></span> <span data-ttu-id="92bea-110">**Bcp_exec**関数は、正常にコピーされた行の数をこの DBINT に設定します。</span><span class="sxs-lookup"><span data-stu-id="92bea-110">The **bcp_exec** function fills this DBINT with the number of rows successfully copied.</span></span> <span data-ttu-id="92bea-111">*PnRowsProcessed*が NULL の場合、 **bcp_exec**によって無視されます。</span><span class="sxs-lookup"><span data-stu-id="92bea-111">If *pnRowsProcessed* is NULL, it is ignored by **bcp_exec**.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="92bea-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="92bea-112">Returns</span></span>  
 <span data-ttu-id="92bea-113">SUCCEED、SUCCEED_ASYNC、または FAIL のいずれかを返します。</span><span class="sxs-lookup"><span data-stu-id="92bea-113">SUCCEED, SUCCEED_ASYNC, or FAIL.</span></span> <span data-ttu-id="92bea-114">すべての行がコピーされると、 **bcp_exec**関数は成功を返します。</span><span class="sxs-lookup"><span data-stu-id="92bea-114">The **bcp_exec** function returns SUCCEED if all rows are copied.</span></span> <span data-ttu-id="92bea-115">非同期の一括コピー操作がまだ未解決である場合、 **bcp_exec**は SUCCEED_ASYNC を返します。</span><span class="sxs-lookup"><span data-stu-id="92bea-115">**bcp_exec** returns SUCCEED_ASYNC if an asynchronous bulk copy operation is still outstanding.</span></span> <span data-ttu-id="92bea-116">**bcp_exec**は、完全なエラーが発生した場合、またはエラーを生成した行数が[bcp_control](bcp-control.md)を使用して BCPMAXERRS に指定された値に達した場合に失敗します。</span><span class="sxs-lookup"><span data-stu-id="92bea-116">**bcp_exec** returns FAIL if a complete failure occurs, or if the number of rows generating errors reaches the value specified for BCPMAXERRS using [bcp_control](bcp-control.md).</span></span> <span data-ttu-id="92bea-117">BCPMAXERRS の既定値は 10 です。</span><span class="sxs-lookup"><span data-stu-id="92bea-117">BCPMAXERRS defaults to 10.</span></span> <span data-ttu-id="92bea-118">BCPMAXERRS オプションの影響を受けるのは、データ ファイルの行 (サーバーに送信される行以外) を読み取る間にプロバイダーで検出される構文エラーのみです。</span><span class="sxs-lookup"><span data-stu-id="92bea-118">The BCPMAXERRS option affects only the syntax errors detected by the provider while reading the rows from the data file (and not the rows sent to the server).</span></span> <span data-ttu-id="92bea-119">ある行でエラーが検出されると、サーバーはバッチを中止します。</span><span class="sxs-lookup"><span data-stu-id="92bea-119">Server aborts the batch when it detects an error with a row.</span></span> <span data-ttu-id="92bea-120">*PnRowsProcessed*パラメーターで、正常にコピーされた行の数を確認します。</span><span class="sxs-lookup"><span data-stu-id="92bea-120">Check the *pnRowsProcessed* parameter for the number of rows successfully copied.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92bea-121">解説</span><span class="sxs-lookup"><span data-stu-id="92bea-121">Remarks</span></span>  
 <span data-ttu-id="92bea-122">この関数は、 [bcp_init](bcp-init.md)の*edirection*パラメーターの値に応じて、ユーザーファイルからデータベーステーブルへ、またはその逆のデータをコピーします。</span><span class="sxs-lookup"><span data-stu-id="92bea-122">This function copies data from a user file to a database table or vice versa, depending on the value of the *eDirection* parameter in [bcp_init](bcp-init.md).</span></span>  
  
 <span data-ttu-id="92bea-123">**Bcp_exec**を呼び出す前に、有効なユーザーファイル名を使用して**bcp_init**を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="92bea-123">Before calling **bcp_exec**, call **bcp_init** with a valid user file name.</span></span> <span data-ttu-id="92bea-124">この操作を行わないと、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="92bea-124">Failure to do so results in an error.</span></span>  
  
 <span data-ttu-id="92bea-125">**bcp_exec**は、任意の期間に未処理である可能性のある唯一の一括コピー関数です。</span><span class="sxs-lookup"><span data-stu-id="92bea-125">**bcp_exec** is the only bulk copy function that is likely to be outstanding for any length of time.</span></span> <span data-ttu-id="92bea-126">そのため、非同期モードをサポートする唯一の一括コピー関数でもあります。</span><span class="sxs-lookup"><span data-stu-id="92bea-126">It is therefore the only bulk copy function that supports asynchronous mode.</span></span> <span data-ttu-id="92bea-127">非同期モードを設定するには、 [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)を使用して**bcp_exec**を呼び出す前に SQL_ATTR_ASYNC_ENABLE を SQL_ASYNC_ENABLE_ON に設定します。</span><span class="sxs-lookup"><span data-stu-id="92bea-127">To set asynchronous mode, use [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) to set SQL_ATTR_ASYNC_ENABLE to SQL_ASYNC_ENABLE_ON before calling **bcp_exec**.</span></span> <span data-ttu-id="92bea-128">完了をテストするには、同じパラメーターを使用して**bcp_exec**を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="92bea-128">To test for completion, call **bcp_exec** with the same parameters.</span></span> <span data-ttu-id="92bea-129">一括コピーがまだ完了していない場合、 **bcp_exec**は SUCCEED_ASYNC を返します。</span><span class="sxs-lookup"><span data-stu-id="92bea-129">If the bulk copy has not yet completed, **bcp_exec** returns SUCCEED_ASYNC.</span></span> <span data-ttu-id="92bea-130">また、 *pnRowsProcessed*は、サーバーに送信された行数の状態カウントを返します。</span><span class="sxs-lookup"><span data-stu-id="92bea-130">It also returns in *pnRowsProcessed* a status count of the number of rows that have been sent to the server.</span></span> <span data-ttu-id="92bea-131">サーバーに送信された行は、バッチの終わりに到達するまではコミットされません。</span><span class="sxs-lookup"><span data-stu-id="92bea-131">Rows sent to the server are not committed until the end of a batch has been reached.</span></span>  
  
 <span data-ttu-id="92bea-132">での一括コピーの重大な変更については [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 、「 [ODBC&#41;&#40;の一括コピー操作の実行](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92bea-132">For information about a breaking change in bulk-copying beginning in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], see [Performing Bulk Copy Operations &#40;ODBC&#41;](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="92bea-133">例</span><span class="sxs-lookup"><span data-stu-id="92bea-133">Example</span></span>  
 <span data-ttu-id="92bea-134">次の例では、 **bcp_exec**を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="92bea-134">The following example shows how to use **bcp_exec**:</span></span>  
  
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
if (bcp_init(hdbc, _T("pubs..authors"), _T("authors.sav"), NULL, DB_OUT)  
   == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Now, execute the bulk copy.   
if (bcp_exec(hdbc, &nRowsProcessed) == FAIL)  
   {  
   if (nRowsProcessed == -1)  
      {  
      printf_s("No rows processed on bulk copy execution.\n");  
      }  
   else  
      {  
      printf_s("Incomplete bulk copy.   Only %ld row%s copied.\n",  
         nRowsProcessed, (nRowsProcessed == 1) ? "": "s");  
      }  
   return;  
   }  
  
printf_s("%ld rows processed.\n", nRowsProcessed);  
  
// Carry on.  
```  
  
## <a name="see-also"></a><span data-ttu-id="92bea-135">参照</span><span class="sxs-lookup"><span data-stu-id="92bea-135">See Also</span></span>  
 [<span data-ttu-id="92bea-136">一括コピー関数</span><span class="sxs-lookup"><span data-stu-id="92bea-136">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
