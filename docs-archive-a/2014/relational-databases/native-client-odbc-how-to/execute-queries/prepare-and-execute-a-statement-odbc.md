---
title: ステートメントの準備と実行 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statement execution
- statement preparation
ms.assetid: 0adecc63-4da5-486c-bc48-09a004a2fae6
author: rothja
ms.author: jroth
ms.openlocfilehash: 607d8ad1509eca1204f6d029842b04120d3f5d9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739871"
---
# <a name="prepare-and-execute-a-statement-odbc"></a><span data-ttu-id="ad3e9-102">ステートメントの準備と実行 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="ad3e9-102">Prepare and Execute a Statement (ODBC)</span></span>
    
### <a name="to-prepare-a-statement-once-and-then-execute-it-multiple-times"></a><span data-ttu-id="ad3e9-103">ステートメントを 1 回だけ準備して複数回実行するには</span><span class="sxs-lookup"><span data-stu-id="ad3e9-103">To prepare a statement once, and then execute it multiple times</span></span>  
  
1.  <span data-ttu-id="ad3e9-104">[SQLPrepare 関数](https://go.microsoft.com/fwlink/?LinkId=59360)を呼び出して、ステートメントを準備します。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-104">Call [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360) to prepare the statement.</span></span>  
  
2.  <span data-ttu-id="ad3e9-105">必要に応じて、 [Sqlnumparams](https://go.microsoft.com/fwlink/?LinkId=58404)を呼び出して、準備されたステートメント内のパラメーターの数を確認します。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-105">Optionally, call [SQLNumParams](https://go.microsoft.com/fwlink/?LinkId=58404) to determine the number of parameters in the prepared statement.</span></span>  
  
3.  <span data-ttu-id="ad3e9-106">必要に応じて、準備されたステートメント内の各パラメーターに対して次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-106">Optionally, for each parameter in the prepared statement:</span></span>  
  
    -   <span data-ttu-id="ad3e9-107">[SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md)を呼び出して、パラメーター情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-107">Call [SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md) to get parameter information.</span></span>  
  
    -   <span data-ttu-id="ad3e9-108">[SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md)を使用して、各パラメーターをプログラム変数にバインドします。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-108">Bind each parameter to a program variable by using [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md).</span></span> <span data-ttu-id="ad3e9-109">実行時データ パラメーターをセットアップします。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-109">Set up any data-at-execution parameters.</span></span>  
  
4.  <span data-ttu-id="ad3e9-110">準備されたステートメントの各実行に対して次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-110">For each execution of a prepared statement:</span></span>  
  
    -   <span data-ttu-id="ad3e9-111">ステートメントにパラメーター マーカーがある場合は、バインドされたパラメーター バッファーにデータ値を格納します。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-111">If the statement has parameter markers, put the data values into the bound parameter buffer.</span></span>  
  
    -   <span data-ttu-id="ad3e9-112">[Sqlexecute](https://go.microsoft.com/fwlink/?LinkId=58400)を呼び出して、準備されたステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-112">Call [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) to execute the prepared statement.</span></span>  
  
    -   <span data-ttu-id="ad3e9-113">実行時データ入力パラメーターが使用されている場合、 [Sqlexecute](https://go.microsoft.com/fwlink/?LinkId=58400)は SQL_NEED_DATA を返します。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-113">If data-at-execution input parameters are used, [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) returns SQL_NEED_DATA.</span></span> <span data-ttu-id="ad3e9-114">[Sqlparamdata](https://go.microsoft.com/fwlink/?LinkId=58405)と[sqlparamdata](../../native-client-odbc-api/sqlputdata.md)を使用して、データをチャンク単位で送信します。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-114">Send the data in chunks by using [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) and [SQLPutData](../../native-client-odbc-api/sqlputdata.md).</span></span>  
  
### <a name="to-prepare-a-statement-with-column-wise-parameter-binding"></a><span data-ttu-id="ad3e9-115">列方向のパラメーターのバインドを使用してステートメントを準備するには</span><span class="sxs-lookup"><span data-stu-id="ad3e9-115">To prepare a statement with column-wise parameter binding</span></span>  
  
1.  <span data-ttu-id="ad3e9-116">[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)を呼び出して、次の属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-116">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the following attributes:</span></span>  
  
    -   <span data-ttu-id="ad3e9-117">SQL_ATTR_PARAMSET_SIZE に、パラメーターのセット数 (S) を設定します。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-117">Set SQL_ATTR_PARAMSET_SIZE to the number of sets (S) of parameters.</span></span>  
  
    -   <span data-ttu-id="ad3e9-118">SQL_ATTR_PARAM_BIND_TYPE を SQL_PARAMETER_BIND_BY_COLUMN に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-118">Set SQL_ATTR_PARAM_BIND_TYPE to SQL_PARAMETER_BIND_BY_COLUMN.</span></span>  
  
    -   <span data-ttu-id="ad3e9-119">SQL_ATTR_PARAMS_PROCESSED_PTR 属性を、処理されたパラメーターの数を格納する SQLUINTEGER 変数を指すように設定します。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-119">Set the SQL_ATTR_PARAMS_PROCESSED_PTR attribute to point to a SQLUINTEGER variable to hold the number of parameters processed.</span></span>  
  
    -   <span data-ttu-id="ad3e9-120">SQL_ATTR_PARAMS_STATUS_PTR を、パラメーターの状態インジケーターを格納する SQLUSSMALLINT 変数の配列[S] を指すように設定します。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-120">Set SQL_ATTR_PARAMS_STATUS_PTR to point to an array[S] of SQLUSSMALLINT variables to hold parameter status indicators.</span></span>  
  
2.  <span data-ttu-id="ad3e9-121">SQLPrepare を呼び出して、ステートメントを準備します。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-121">Call SQLPrepare to prepare the statement.</span></span>  
  
3.  <span data-ttu-id="ad3e9-122">必要に応じて、 [Sqlnumparams](https://go.microsoft.com/fwlink/?LinkId=58404)を呼び出して、準備されたステートメント内のパラメーターの数を確認します。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-122">Optionally, call [SQLNumParams](https://go.microsoft.com/fwlink/?LinkId=58404) to determine the number of parameters in the prepared statement.</span></span>  
  
4.  <span data-ttu-id="ad3e9-123">必要に応じて、準備されたステートメントの各パラメーターに対して SQLDescribeParam を呼び出して、パラメーター情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-123">Optionally, for each parameter in the prepared statement, call SQLDescribeParam to get parameter information.</span></span>  
  
5.  <span data-ttu-id="ad3e9-124">各パラメーター マーカーについて、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-124">For each parameter marker:</span></span>  
  
    -   <span data-ttu-id="ad3e9-125">データ値を格納する S パラメーター バッファーの配列を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-125">Allocate an array of S parameter buffers to store data values.</span></span>  
  
    -   <span data-ttu-id="ad3e9-126">データの長さを格納する S パラメーター バッファーの配列を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-126">Allocate an array of S parameter buffers to store data lengths.</span></span>  
  
    -   <span data-ttu-id="ad3e9-127">SQLBindParameter を呼び出して、パラメーターのデータ値とデータ長の配列をステートメントパラメーターにバインドします。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-127">Call SQLBindParameter to bind the parameter data value and data length arrays to the statement parameter.</span></span>  
  
    -   <span data-ttu-id="ad3e9-128">パラメーターが実行時データの text または image パラメーターである場合は、それをセットアップします。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-128">If the parameter is a data-at-execution text or image parameter, set it up.</span></span>  
  
    -   <span data-ttu-id="ad3e9-129">実行時データ パラメーターを使用する場合は、それらをセットアップします。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-129">If any data-at-execution parameters are used, set them up.</span></span>  
  
6.  <span data-ttu-id="ad3e9-130">準備されたステートメントの各実行に対して次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-130">For each execution of a prepared statement:</span></span>  
  
    -   <span data-ttu-id="ad3e9-131">S データ値と S データ長をバインドされたパラメーター配列に格納します。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-131">Put the S data values and S data lengths into the bound parameter arrays.</span></span>  
  
    -   <span data-ttu-id="ad3e9-132">SQLExecute を呼び出して、準備されたステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-132">Call SQLExecute to execute the prepared statement.</span></span>  
  
    -   <span data-ttu-id="ad3e9-133">実行時データ入力パラメーターが使用されている場合、SQLExecute は SQL_NEED_DATA を返します。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-133">If data-at-execution input parameters are used, SQLExecute returns SQL_NEED_DATA.</span></span> <span data-ttu-id="ad3e9-134">SQLParamData と Sqlparamdata を使用して、データをチャンク単位で送信します。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-134">Send the data in chunks by using SQLParamData and SQLPutData.</span></span>  
  
### <a name="to-prepare-a-statement-with-row-wise-bound-parameters"></a><span data-ttu-id="ad3e9-135">行方向にバインドされたパラメーターを使用してステートメントを準備するには</span><span class="sxs-lookup"><span data-stu-id="ad3e9-135">To prepare a statement with row-wise bound parameters</span></span>  
  
1.  <span data-ttu-id="ad3e9-136">構造体の配列[S] を割り当てます。この S は行パラメーターのセット数です。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-136">Allocate an array[S] of structures, where S is the number of sets of parameters.</span></span> <span data-ttu-id="ad3e9-137">構造体には各パラメーターについて 1 つの要素があり、各要素は次の 2 つの部分で構成されています。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-137">The structure has one element for each parameter, and each element has two parts:</span></span>  
  
    -   <span data-ttu-id="ad3e9-138">最初の部分は、パラメーター データを格納する適切なデータ型の変数です。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-138">The first part is a variable of the appropriate data type to hold the parameter data.</span></span>  
  
    -   <span data-ttu-id="ad3e9-139">2 つ目の部分は、状態インジケーターを格納する SQLINTEGER 変数です。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-139">The second part is a SQLINTEGER variable to hold the status indicator.</span></span>  
  
2.  <span data-ttu-id="ad3e9-140">[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)を呼び出して、次の属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-140">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the following attributes:</span></span>  
  
    -   <span data-ttu-id="ad3e9-141">SQL_ATTR_PARAMSET_SIZE に、パラメーターのセット数 (S) を設定します。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-141">Set SQL_ATTR_PARAMSET_SIZE to the number of sets (S) of parameters.</span></span>  
  
    -   <span data-ttu-id="ad3e9-142">SQL_ATTR_PARAM_BIND_TYPE を、手順 1. で割り当てた構造体のサイズに設定します。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-142">Set SQL_ATTR_PARAM_BIND_TYPE to the size of the structure allocated in Step 1.</span></span>  
  
    -   <span data-ttu-id="ad3e9-143">SQL_ATTR_PARAMS_PROCESSED_PTR 属性を、処理されたパラメーターの数を格納する SQLUINTEGER 変数を指すように設定します。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-143">Set the SQL_ATTR_PARAMS_PROCESSED_PTR attribute to point to a SQLUINTEGER variable to hold the number of parameters processed.</span></span>  
  
    -   <span data-ttu-id="ad3e9-144">SQL_ATTR_PARAMS_STATUS_PTR を、パラメーターの状態インジケーターを格納する SQLUSSMALLINT 変数の配列[S] を指すように設定します。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-144">Set SQL_ATTR_PARAMS_STATUS_PTR to point to an array[S] of SQLUSSMALLINT variables to hold parameter status indicators.</span></span>  
  
3.  <span data-ttu-id="ad3e9-145">SQLPrepare を呼び出して、ステートメントを準備します。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-145">Call SQLPrepare to prepare the statement.</span></span>  
  
4.  <span data-ttu-id="ad3e9-146">各パラメーターマーカーについて、SQLBindParameter を呼び出して、手順 1. で割り当てた構造体の配列の最初の要素にあるパラメーターのデータ値とデータ長ポインターをポイントします。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-146">For each parameter marker, call SQLBindParameter to point the parameter data value and data length pointer to their variables in the first element of the array of structures allocated in Step 1.</span></span> <span data-ttu-id="ad3e9-147">パラメーターが実行時データ パラメーターである場合は、そのパラメーターをセットアップします。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-147">If the parameter is a data-at-execution parameter, set it up.</span></span>  
  
5.  <span data-ttu-id="ad3e9-148">準備されたステートメントの各実行に対して次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-148">For each execution of a prepared statement:</span></span>  
  
    -   <span data-ttu-id="ad3e9-149">バインドされたパラメーターのバッファー配列にデータ値を入力します。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-149">Fill the bound parameter buffer array with data values.</span></span>  
  
    -   <span data-ttu-id="ad3e9-150">SQLExecute を呼び出して、準備されたステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-150">Call SQLExecute to execute the prepared statement.</span></span> <span data-ttu-id="ad3e9-151">ドライバーによって、S 回 (パラメーターのセットごとに 1 回) SQL ステートメントが効率よく実行されます。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-151">The driver efficiently executes the SQL statement S times, once for each set of parameters.</span></span>  
  
    -   <span data-ttu-id="ad3e9-152">実行時データ入力パラメーターが使用されている場合、SQLExecute は SQL_NEED_DATA を返します。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-152">If data-at-execution input parameters are used, SQLExecute returns SQL_NEED_DATA.</span></span> <span data-ttu-id="ad3e9-153">SQLParamData と Sqlparamdata を使用して、データをチャンク単位で送信します。</span><span class="sxs-lookup"><span data-stu-id="ad3e9-153">Send the data in chunks by using SQLParamData and SQLPutData.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad3e9-154">参照</span><span class="sxs-lookup"><span data-stu-id="ad3e9-154">See Also</span></span>  
 [<span data-ttu-id="ad3e9-155">クエリの実行方法に関するトピック &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="ad3e9-155">Executing Queries How-to Topics &#40;ODBC&#41;</span></span>](executing-queries-how-to-topics-odbc.md)  
  
  
