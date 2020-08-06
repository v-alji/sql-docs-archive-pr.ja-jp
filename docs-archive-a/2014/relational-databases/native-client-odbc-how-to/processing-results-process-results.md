---
title: 結果の処理 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- processing results [ODBC]
ms.assetid: 4810fe3f-78ee-4f0d-8bcc-a4659fbcf46f
author: rothja
ms.author: jroth
ms.openlocfilehash: 8a22e9d7280f88de7799c31d2d0611e5299043d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738293"
---
# <a name="process-results-odbc"></a><span data-ttu-id="358dc-102">結果の処理 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="358dc-102">Process Results (ODBC)</span></span>
    
### <a name="to-process-results"></a><span data-ttu-id="358dc-103">結果を処理するには</span><span class="sxs-lookup"><span data-stu-id="358dc-103">To process results</span></span>  
  
1.  <span data-ttu-id="358dc-104">結果セットの情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="358dc-104">Retrieve result set information.</span></span>  
  
2.  <span data-ttu-id="358dc-105">バインドされた列が使用されている場合は、バインド先の列ごとに[SQLBindCol](../native-client-odbc-api/sqlbindcol.md) を呼び出して、プログラム バッファーを列にバインドします。</span><span class="sxs-lookup"><span data-stu-id="358dc-105">If bound columns are used, for each column you want to bind to, call [SQLBindCol](../native-client-odbc-api/sqlbindcol.md) to bind a program buffer to the column.</span></span>  
  
3.  <span data-ttu-id="358dc-106">結果セット内の各行に対して次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="358dc-106">For each row in the result set:</span></span>  
  
    -   <span data-ttu-id="358dc-107">[SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) を呼び出して次の行を取得します。</span><span class="sxs-lookup"><span data-stu-id="358dc-107">Call [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) to get the next row.</span></span>  
  
    -   <span data-ttu-id="358dc-108">バインドされた列が使用されている場合は、バインドされた列のバッファー内で現在使用可能なデータを使用します。</span><span class="sxs-lookup"><span data-stu-id="358dc-108">If bound columns are used, use the data now available in the bound column buffers.</span></span>  
  
    -   <span data-ttu-id="358dc-109">バインドされていない列が使用されている場合は、[SQLGetData](../native-client-odbc-api/sqlgetdata.md) を 1 回以上呼び出して、バインドされている最後の列の後に、バインドされていない列のデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="358dc-109">If unbound columns are used, call [SQLGetData](../native-client-odbc-api/sqlgetdata.md) one or more times to get the data for unbound columns after the last bound column.</span></span> <span data-ttu-id="358dc-110">の呼び出し `SQLGetData` は、列番号の昇順にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="358dc-110">Calls to `SQLGetData` should be in increasing order of column number.</span></span>  
  
    -   <span data-ttu-id="358dc-111">`SQLGetData` を複数回呼び出して、text または image 列からデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="358dc-111">Call `SQLGetData` multiple times to get data from a text or image column.</span></span>  
  
4.  <span data-ttu-id="358dc-112">[SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) が SQL_NO_DATA を返すことによって結果セットの終了を示したら、[SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) を呼び出して、使用可能な結果セットが他にあるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="358dc-112">When [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) signals the end of the result set by returning SQL_NO_DATA, call [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) to determine if another result set is available.</span></span>  
  
    -   <span data-ttu-id="358dc-113">SQL_SUCCESS が返された場合は、別の結果セットを使用できます。</span><span class="sxs-lookup"><span data-stu-id="358dc-113">If it returns SQL_SUCCESS, another result set is available.</span></span>  
  
    -   <span data-ttu-id="358dc-114">SQL_NO_DATA が返された場合は、他に使用できる結果セットはありません。</span><span class="sxs-lookup"><span data-stu-id="358dc-114">If it returns SQL_NO_DATA, no more result sets are available.</span></span>  
  
    -   <span data-ttu-id="358dc-115">SQL_SUCCESS_WITH_INFO または SQL_ERROR が返された場合は、[SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) を呼び出して、PRINT ステートメントまたは RAISERROR ステートメントからの出力が使用可能かどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="358dc-115">If it returns SQL_SUCCESS_WITH_INFO or SQL_ERROR, call [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) to determine if the output from a PRINT or RAISERROR statement is available.</span></span>  
  
         <span data-ttu-id="358dc-116">バインドされたステートメントのパラメーターが出力パラメーターまたはストアド プロシージャの戻り値に使用されている場合は、バインドされたパラメーターのバッファーでデータを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="358dc-116">If bound statement parameters are used for output parameters or the return value of a stored procedure, use the data now available in the bound parameter buffers.</span></span> <span data-ttu-id="358dc-117">バインドされたパラメーターが使用される場合は、[SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) または [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) への各呼び出しで、SQL ステートメントが *S* 回実行されます。*S* は、バインドされたパラメーターの配列内にある要素の数です。</span><span class="sxs-lookup"><span data-stu-id="358dc-117">Also, when bound parameters are used, each call to [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) or [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) will have executed the SQL statement *S* times, where *S* is the number of elements in the array of bound parameters.</span></span> <span data-ttu-id="358dc-118">つまり、処理する結果のセットが *S* 個あることを意味します。これらの結果の各セットには、結果セット、出力パラメーター、および通常 SQL ステートメントの 1 回の実行で返されるリターン コードがすべて含まれます。</span><span class="sxs-lookup"><span data-stu-id="358dc-118">This means that there will be *S* sets of results to process, where each set of results comprises all of the result sets, output parameters, and return codes usually returned by a single execution of the SQL statement.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="358dc-119">結果セットに計算行が含まれている場合、各計算行は個々の結果セットとして使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="358dc-119">When a result set contains compute rows, each compute row is made available as a separate result set.</span></span> <span data-ttu-id="358dc-120">これらの計算結果セットは標準行内に点在し、標準行は複数の結果セットに分割されます。</span><span class="sxs-lookup"><span data-stu-id="358dc-120">These compute result sets are interspersed within the normal rows and break normal rows into multiple result sets.</span></span>  
  
5.  <span data-ttu-id="358dc-121">必要に応じて、SQL_UNBIND を使用して [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) を呼び出し、バインドされた列バッファーを解放します。</span><span class="sxs-lookup"><span data-stu-id="358dc-121">Optionally, call [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) with SQL_UNBIND to release any bound column buffers.</span></span>  
  
6.  <span data-ttu-id="358dc-122">別の結果セットが使用できる場合は、手順 1 に戻ります。</span><span class="sxs-lookup"><span data-stu-id="358dc-122">If another result set is available, go to Step 1.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="358dc-123">[SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) によって SQL_NO_DATA が返される前に結果セットの処理を取り消すには、[SQLCloseCursor](../native-client-odbc-api/sqlclosecursor.md) を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="358dc-123">To cancel processing a result set before [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) returns SQL_NO_DATA, call [SQLCloseCursor](../native-client-odbc-api/sqlclosecursor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="358dc-124">参照</span><span class="sxs-lookup"><span data-stu-id="358dc-124">See Also</span></span>  
 [<span data-ttu-id="358dc-125">結果の処理方法に関するトピック &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="358dc-125">Processing Results How-to Topics &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md)  
  
  
