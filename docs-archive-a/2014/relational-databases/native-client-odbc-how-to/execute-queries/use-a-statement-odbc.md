---
title: ステートメントを使用する (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statements [ODBC]
ms.assetid: f7573f8f-6f21-4e03-8dd5-a5f2ea4878cc
author: rothja
ms.author: jroth
ms.openlocfilehash: 8ff3bc8c545cc9b55f0da3bb31d68d1ecbb5b547
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739876"
---
# <a name="use-a-statement-odbc"></a><span data-ttu-id="94f26-102">ステートメントの使用 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="94f26-102">Use a Statement (ODBC)</span></span>
    
### <a name="to-use-a-statement"></a><span data-ttu-id="94f26-103">ステートメントを使用するには</span><span class="sxs-lookup"><span data-stu-id="94f26-103">To use a statement</span></span>  
  
1.  <span data-ttu-id="94f26-104">*HandleType* を SQL_HANDLE_STMT として [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) を呼び出し、ステートメント ハンドルを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="94f26-104">Call [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) with a *HandleType* of SQL_HANDLE_STMT to allocate a statement handle.</span></span>  
  
2.  <span data-ttu-id="94f26-105">また、[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) を呼び出してステートメント オプションを設定するか、[SQLGetStmtAttr](../../native-client-odbc-api/sqlgetstmtattr.md) を呼び出してステートメント属性を取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="94f26-105">Optionally, call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set statement options or [SQLGetStmtAttr](../../native-client-odbc-api/sqlgetstmtattr.md) to get statement attributes.</span></span>  
  
     <span data-ttu-id="94f26-106">サーバー カーソルを使用するには、カーソルの属性を既定値以外の値に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="94f26-106">To use server cursors, you must set cursor attributes to values other than their defaults.</span></span>  
  
3.  <span data-ttu-id="94f26-107">また、ステートメントを複数回実行する場合は、[SQLPrepare 関数](https://go.microsoft.com/fwlink/?LinkId=59360)を使用して実行するステートメントを準備します。</span><span class="sxs-lookup"><span data-stu-id="94f26-107">Optionally, if the statement will be executed several times, prepare the statement for execution with [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360).</span></span>  
  
4.  <span data-ttu-id="94f26-108">ステートメントにバインドされたパラメーター マーカーが含まれている場合は、必要に応じて、[SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) を使用してパラメーター マーカーをプログラム変数にバインドします。</span><span class="sxs-lookup"><span data-stu-id="94f26-108">Optionally, if the statement has bound parameter markers, bind the parameter markers to program variables by using [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md).</span></span> <span data-ttu-id="94f26-109">ステートメントが準備されている場合は、[SQLNumParams](https://go.microsoft.com/fwlink/?LinkId=58404) および [SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md) を呼び出して、パラメーターの数と特性を検索できます。</span><span class="sxs-lookup"><span data-stu-id="94f26-109">If the statement was prepared, you can call [SQLNumParams](https://go.microsoft.com/fwlink/?LinkId=58404) and [SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md) to find the number and characteristics of the parameters.</span></span>  
  
5.  <span data-ttu-id="94f26-110">SQLExecDirect を使用してステートメントを直接実行します。</span><span class="sxs-lookup"><span data-stu-id="94f26-110">Execute a statement directly by using SQLExecDirect.</span></span>  
  
     <span data-ttu-id="94f26-111">\- または</span><span class="sxs-lookup"><span data-stu-id="94f26-111">\- or -</span></span>  
  
     <span data-ttu-id="94f26-112">ステートメントが準備されている場合は、[SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) を使用してそのステートメントを複数回実行します。</span><span class="sxs-lookup"><span data-stu-id="94f26-112">If the statement was prepared, execute it multiple times by using [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400).</span></span>  
  
     <span data-ttu-id="94f26-113">\- または</span><span class="sxs-lookup"><span data-stu-id="94f26-113">\- or -</span></span>  
  
     <span data-ttu-id="94f26-114">カタログ関数を呼び出すと、結果が返されます。</span><span class="sxs-lookup"><span data-stu-id="94f26-114">Call a catalog function, which returns results.</span></span>  
  
6.  <span data-ttu-id="94f26-115">結果セット列をプログラム変数にバインドするか、[SQLGetData](../../native-client-odbc-api/sqlgetdata.md) を使用して結果セット列からプログラム変数にデータを移動するか、あるいはこれらの 2 つの方法を組み合わせて結果を処理します。</span><span class="sxs-lookup"><span data-stu-id="94f26-115">Process the results by binding the result set columns to program variables, by moving data from the result set columns to program variables by using [SQLGetData](../../native-client-odbc-api/sqlgetdata.md), or a combination of the two methods.</span></span>  
  
     <span data-ttu-id="94f26-116">ステートメントの結果セットを一度に 1 行ずつフェッチします。</span><span class="sxs-lookup"><span data-stu-id="94f26-116">Fetch through the result set of a statement one row at a time.</span></span>  
  
     <span data-ttu-id="94f26-117">\- または</span><span class="sxs-lookup"><span data-stu-id="94f26-117">\- or -</span></span>  
  
     <span data-ttu-id="94f26-118">ブロック カーソルを使用して一度に複数行の結果セットをフェッチします。</span><span class="sxs-lookup"><span data-stu-id="94f26-118">Fetch through the result set several rows at a time by using a block cursor.</span></span>  
  
     <span data-ttu-id="94f26-119">\- または</span><span class="sxs-lookup"><span data-stu-id="94f26-119">\- or -</span></span>  
  
     <span data-ttu-id="94f26-120">[SQLRowCount](../../native-client-odbc-api/sqlrowcount.md) を呼び出して、INSERT、UPDATE、または DELETE ステートメントの影響を受ける行数を確認します。</span><span class="sxs-lookup"><span data-stu-id="94f26-120">Call [SQLRowCount](../../native-client-odbc-api/sqlrowcount.md) to determine the number of rows affected by an INSERT, UPDATE, or DELETE statement.</span></span>  
  
     <span data-ttu-id="94f26-121">SQL ステートメントに複数の結果セットが含まれている可能性がある場合は、各結果セットの最後に [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) を呼び出して、処理する追加の結果セットがあるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="94f26-121">If the SQL statement can have multiple result sets, call [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) at the end of each result set to see if there are additional result sets to process.</span></span>  
  
7.  <span data-ttu-id="94f26-122">結果が処理されたら、ステートメント ハンドルで新しいステートメントを実行できるように、次のアクションが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="94f26-122">After results are processed, the following actions may be necessary to make the statement handle available to execute a new statement:</span></span>  
  
    -   <span data-ttu-id="94f26-123">SQL_NO_DATA が返されるまで [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) を呼び出さなかった場合は、[SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) を呼び出してカーソルを閉じます。</span><span class="sxs-lookup"><span data-stu-id="94f26-123">If you did not call [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) until it returned SQL_NO_DATA, call [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) to close the cursor.</span></span>  
  
    -   <span data-ttu-id="94f26-124">パラメーター マーカーをプログラム変数にバインドした場合は、*Option* を SQL_RESET_PARAMS に設定して [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) を呼び出し、バインドされたパラメーターを解放します。</span><span class="sxs-lookup"><span data-stu-id="94f26-124">If you bound parameter markers to program variables, call [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) with *Option* set to SQL_RESET_PARAMS to free the bound parameters.</span></span>  
  
    -   <span data-ttu-id="94f26-125">結果セット列をプログラム変数にバインドした場合は、*Option* を SQL_UNBIND に設定して [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) を呼び出し、バインドされた列を解放します。</span><span class="sxs-lookup"><span data-stu-id="94f26-125">If you bound result set columns to program variables, call [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) with *Option* set to SQL_UNBIND to free the bound columns.</span></span>  
  
    -   <span data-ttu-id="94f26-126">ステートメント ハンドルを再利用するには、手順 2. に進みます。</span><span class="sxs-lookup"><span data-stu-id="94f26-126">To reuse the statement handle, go to Step 2.</span></span>  
  
8.  <span data-ttu-id="94f26-127">*HandleType* を SQL_HANDLE_STMT として [SQLFreeHandle](../../native-client-odbc-api/sqlfreehandle.md) を呼び出し、ステートメント ハンドルを解放します。</span><span class="sxs-lookup"><span data-stu-id="94f26-127">Call [SQLFreeHandle](../../native-client-odbc-api/sqlfreehandle.md) with a *HandleType* of SQL_HANDLE_STMT to free the statement handle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94f26-128">参照</span><span class="sxs-lookup"><span data-stu-id="94f26-128">See Also</span></span>  
 [<span data-ttu-id="94f26-129">クエリの実行方法に関するトピック &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="94f26-129">Executing Queries How-to Topics &#40;ODBC&#41;</span></span>](executing-queries-how-to-topics-odbc.md)  
  
  
