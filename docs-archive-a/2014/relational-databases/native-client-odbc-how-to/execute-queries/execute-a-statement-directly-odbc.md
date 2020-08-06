---
title: ステートメントを直接実行する (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statement execution
ms.assetid: b690f9de-66e1-4ee5-ab6a-121346fb5f85
author: rothja
ms.author: jroth
ms.openlocfilehash: 2aeada906a925cff93455ffd92e7c17822a80124
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630978"
---
# <a name="execute-a-statement-directly-odbc"></a><span data-ttu-id="a9dd6-102">ステートメントの直接実行 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="a9dd6-102">Execute a Statement Directly (ODBC)</span></span>
    
### <a name="to-execute-a-statement-directly-and-one-time-only"></a><span data-ttu-id="a9dd6-103">ステートメントを直接一度だけ実行するには</span><span class="sxs-lookup"><span data-stu-id="a9dd6-103">To execute a statement directly and one time only</span></span>  
  
1.  <span data-ttu-id="a9dd6-104">ステートメントにパラメーターマーカーがある場合は、 [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md)を使用して、各パラメーターをプログラム変数にバインドします。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-104">If the statement has parameter markers, use [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) to bind each parameter to a program variable.</span></span> <span data-ttu-id="a9dd6-105">プログラム変数にデータ値を入力してから、実行時データ パラメーターをセットアップします。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-105">Fill the program variables with data values, and then set up any data-at-execution parameters.</span></span>  
  
2.  <span data-ttu-id="a9dd6-106">[SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)を呼び出して、ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-106">Call [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) to execute the statement.</span></span>  
  
3.  <span data-ttu-id="a9dd6-107">実行時データ入力パラメーターが使用されている場合、 [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)は SQL_NEED_DATA を返します。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-107">If data-at-execution input parameters are used, [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) returns SQL_NEED_DATA.</span></span> <span data-ttu-id="a9dd6-108">[Sqlparamdata](https://go.microsoft.com/fwlink/?LinkId=58405)と[sqlparamdata](../../native-client-odbc-api/sqlputdata.md)を使用して、データをチャンク単位で送信します。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-108">Send the data in chunks by using [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) and [SQLPutData](../../native-client-odbc-api/sqlputdata.md).</span></span>  
  
### <a name="to-execute-a-statement-multiple-times-by-using-column-wise-parameter-binding"></a><span data-ttu-id="a9dd6-109">列方向のパラメーターのバインドを使用してステートメントを複数回実行するには</span><span class="sxs-lookup"><span data-stu-id="a9dd6-109">To execute a statement multiple times by using column-wise parameter binding</span></span>  
  
1.  <span data-ttu-id="a9dd6-110">[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)を呼び出して、次の属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-110">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the following attributes:</span></span>  
  
     <span data-ttu-id="a9dd6-111">SQL_ATTR_PARAMSET_SIZE に、パラメーターのセット数 (S) を設定します。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-111">Set SQL_ATTR_PARAMSET_SIZE to the number of sets (S) of parameters.</span></span>  
  
     <span data-ttu-id="a9dd6-112">SQL_ATTR_PARAM_BIND_TYPE を SQL_PARAMETER_BIND_BY_COLUMN に設定します。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-112">Set SQL_ATTR_PARAM_BIND_TYPE to SQL_PARAMETER_BIND_BY_COLUMN.</span></span>  
  
     <span data-ttu-id="a9dd6-113">SQL_ATTR_PARAMS_PROCESSED_PTR 属性を、処理されたパラメーターの数を格納する SQLUINTEGER 変数を指すように設定します。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-113">Set the SQL_ATTR_PARAMS_PROCESSED_PTR attribute to point to a SQLUINTEGER variable to hold the number of parameters processed.</span></span>  
  
     <span data-ttu-id="a9dd6-114">パラメーターの状態インジケーターを保持する SQLUSSMALLINT 変数の配列 [S] をポイントするように SQL_ATTR_PARAMS_STATUS_PTR を設定します。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-114">Set SQL_ATTR_PARAMS_STATUS_PTR to point to an array[S] of SQLUSSMALLINT variables to hold the parameter status indicators.</span></span>  
  
2.  <span data-ttu-id="a9dd6-115">各パラメーター マーカーについて、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-115">For each parameter marker:</span></span>  
  
     <span data-ttu-id="a9dd6-116">データ値を格納する S パラメーター バッファーの配列を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-116">Allocate an array of S parameter buffers to store data values.</span></span>  
  
     <span data-ttu-id="a9dd6-117">データの長さを格納する S パラメーター バッファーの配列を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-117">Allocate an array of S parameter buffers to store data lengths.</span></span>  
  
     <span data-ttu-id="a9dd6-118">[SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md)を呼び出して、パラメーターのデータ値とデータ長の配列をステートメントパラメーターにバインドします。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-118">Call [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) to bind the parameter data value and data length arrays to the statement parameter.</span></span>  
  
     <span data-ttu-id="a9dd6-119">実行時データ テキストまたはイメージ パラメーターをセットアップします。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-119">Set up any data-at-execution text or image parameters.</span></span>  
  
     <span data-ttu-id="a9dd6-120">S データ値および S データの長さを、バインドされたパラメーター配列に置きます。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-120">Put S data values and S data lengths into the bound parameter arrays.</span></span>  
  
3.  <span data-ttu-id="a9dd6-121">[SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)を呼び出して、ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-121">Call [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) to execute the statement.</span></span> <span data-ttu-id="a9dd6-122">ドライバーによって、S 回 (パラメーターのセットごとに 1 回) ステートメントが効率よく実行されます。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-122">The driver efficiently executes the statement S times, once for each set of parameters.</span></span>  
  
4.  <span data-ttu-id="a9dd6-123">実行時データ入力パラメーターが使用されている場合、 [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)は SQL_NEED_DATA を返します。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-123">If data-at-execution input parameters are used, [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) returns SQL_NEED_DATA.</span></span> <span data-ttu-id="a9dd6-124">[Sqlparamdata](https://go.microsoft.com/fwlink/?LinkId=58405)と[sqlparamdata](../../native-client-odbc-api/sqlputdata.md)を使用して、データをチャンク単位で送信します。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-124">Send the data in chunks by using [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) and [SQLPutData](../../native-client-odbc-api/sqlputdata.md).</span></span>  
  
### <a name="to-execute-a-statement-multiple-times-by-using-row-wise-parameter-binding"></a><span data-ttu-id="a9dd6-125">行方向のパラメーターのバインドを使用してステートメントを複数回実行するには</span><span class="sxs-lookup"><span data-stu-id="a9dd6-125">To execute a statement multiple times by using row-wise parameter binding</span></span>  
  
1.  <span data-ttu-id="a9dd6-126">構造体の配列[S] を割り当てます。この S は行パラメーターのセット数です。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-126">Allocate an array[S] of structures, where S is the number of sets of parameters.</span></span> <span data-ttu-id="a9dd6-127">構造体には各パラメーターについて 1 つの要素があり、各要素は次の 2 つの部分で構成されています。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-127">The structure has one element for each parameter, and each element has two parts:</span></span>  
  
     <span data-ttu-id="a9dd6-128">最初の部分は、パラメーター データを格納する適切なデータ型の変数です。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-128">The first part is a variable of the appropriate data type to hold the parameter data.</span></span>  
  
     <span data-ttu-id="a9dd6-129">2 つ目の部分は、状態インジケーターを格納する SQLINTEGER 変数です。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-129">The second part is a SQLINTEGER variable to hold the status indicator.</span></span>  
  
2.  <span data-ttu-id="a9dd6-130">[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)を呼び出して、次の属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-130">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the following attributes:</span></span>  
  
     <span data-ttu-id="a9dd6-131">SQL_ATTR_PARAMSET_SIZE に、パラメーターのセット数 (S) を設定します。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-131">Set SQL_ATTR_PARAMSET_SIZE to the number of sets (S) of parameters.</span></span>  
  
     <span data-ttu-id="a9dd6-132">SQL_ATTR_PARAM_BIND_TYPE を、手順 1. で割り当てた構造体のサイズに設定します。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-132">Set SQL_ATTR_PARAM_BIND_TYPE to the size of the structure allocated in Step 1.</span></span>  
  
     <span data-ttu-id="a9dd6-133">SQL_ATTR_PARAMS_PROCESSED_PTR 属性を、処理されたパラメーターの数を格納する SQLUINTEGER 変数を指すように設定します。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-133">Set the SQL_ATTR_PARAMS_PROCESSED_PTR attribute to point to a SQLUINTEGER variable to hold the number of parameters processed.</span></span>  
  
     <span data-ttu-id="a9dd6-134">パラメーターの状態インジケーターを保持する SQLUSSMALLINT 変数の配列 [S] をポイントするように SQL_ATTR_PARAMS_STATUS_PTR を設定します。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-134">Set SQL_ATTR_PARAMS_STATUS_PTR to point to an array[S] of SQLUSSMALLINT variables to hold the parameter status indicators.</span></span>  
  
3.  <span data-ttu-id="a9dd6-135">パラメーターマーカーごとに、 [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md)を呼び出して、パラメーターのデータ値とデータ長のポインターが、手順 1. で割り当てた構造体の配列の最初の要素にある変数を指すようにします。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-135">For each parameter marker, call [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) to point the parameter's data value and data length pointer to their variables in the first element of the array of structures allocated in Step 1.</span></span> <span data-ttu-id="a9dd6-136">パラメーターが実行時データ パラメーターである場合は、そのパラメーターをセットアップします。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-136">If the parameter is a data-at-execution parameter, set it up.</span></span>  
  
4.  <span data-ttu-id="a9dd6-137">バインドされたパラメーターのバッファー配列にデータ値を入力します。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-137">Fill the bound parameter buffer array with data values.</span></span>  
  
5.  <span data-ttu-id="a9dd6-138">[SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)を呼び出して、ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-138">Call [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) to execute the statement.</span></span> <span data-ttu-id="a9dd6-139">ドライバーによって、S 回 (パラメーターのセットごとに 1 回) ステートメントが効率よく実行されます。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-139">The driver efficiently executes the statement S times, once for each set of parameters.</span></span>  
  
6.  <span data-ttu-id="a9dd6-140">実行時データ入力パラメーターが使用されている場合、 [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)は SQL_NEED_DATA を返します。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-140">If data-at-execution input parameters are used, [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) returns SQL_NEED_DATA.</span></span> <span data-ttu-id="a9dd6-141">[Sqlparamdata](https://go.microsoft.com/fwlink/?LinkId=58405)と[sqlparamdata](../../native-client-odbc-api/sqlputdata.md)を使用して、データをチャンク単位で送信します。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-141">Send the data in chunks by using [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) and [SQLPutData](../../native-client-odbc-api/sqlputdata.md).</span></span>  
  
 <span data-ttu-id="a9dd6-142">**メモ**列方向と行方向のバインドは、通常、 [SQLPrepare 関数](https://go.microsoft.com/fwlink/?LinkId=59360)と[SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)ではなく[sqlexecute](https://go.microsoft.com/fwlink/?LinkId=58400)と組み合わせて使用されます。</span><span class="sxs-lookup"><span data-stu-id="a9dd6-142">**Note** Column-wise and row-wise binding are more typically used in conjunction with [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360) and [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) than with [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9dd6-143">参照</span><span class="sxs-lookup"><span data-stu-id="a9dd6-143">See Also</span></span>  
 [<span data-ttu-id="a9dd6-144">クエリの実行方法に関するトピック &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="a9dd6-144">Executing Queries How-to Topics &#40;ODBC&#41;</span></span>](executing-queries-how-to-topics-odbc.md)  
  
  
