---
title: ストレージの割り当て |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- column-wise binding [ODBC]
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- SQLBindCol function
- storing data [ODBC]
- result sets [ODBC], storage
- SQL Server Native Client ODBC driver, data storage
- row-wise binding
- binding result sets [SQL Server Native Client]
- array binding
ms.assetid: 11c81955-5300-495f-925f-9256f2587b58
author: rothja
ms.author: jroth
ms.openlocfilehash: ada18c91493d91b36ced51bf84c32513a0c5f5df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643280"
---
# <a name="assigning-storage"></a><span data-ttu-id="17227-102">ストレージの割り当て</span><span class="sxs-lookup"><span data-stu-id="17227-102">Assigning Storage</span></span>
  <span data-ttu-id="17227-103">アプリケーションでは、SQL ステートメントの実行前後に、結果用のストレージを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="17227-103">An application can assign storage for results before or after it executes a SQL statement.</span></span> <span data-ttu-id="17227-104">アプリケーションで最初に SQL ステートメントを準備または実行すると、結果のストレージを割り当てる前に、結果セットに関する情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="17227-104">If an application prepares or executes the SQL statement first, it can inquire about the result set before it assigns storage for results.</span></span> <span data-ttu-id="17227-105">たとえば、結果セットが不明であれば、アプリケーションでは、列にストレージを割り当てる前に、列数を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17227-105">For example, if the result set is unknown, the application must retrieve the number of columns before it can assign storage for them.</span></span>  
  
 <span data-ttu-id="17227-106">データの列にストレージを関連付けるために、アプリケーションは[SQLBindCol](../native-client-odbc-api/sqlbindcol.md)を呼び出し、それを渡します。</span><span class="sxs-lookup"><span data-stu-id="17227-106">To associate storage for a column of data, an application calls [SQLBindCol](../native-client-odbc-api/sqlbindcol.md)and passes it:</span></span>  
  
-   <span data-ttu-id="17227-107">データの変換先のデータ型。</span><span class="sxs-lookup"><span data-stu-id="17227-107">The data type to which the data is to be converted.</span></span>  
  
-   <span data-ttu-id="17227-108">データの出力バッファーのアドレス。</span><span class="sxs-lookup"><span data-stu-id="17227-108">The address of an output buffer for the data.</span></span>  
  
     <span data-ttu-id="17227-109">アプリケーションではこのバッファーを割り当てる必要があります。このバッファーは、変換後の形式でデータを保持するのに十分な大きさを確保する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17227-109">The application must allocate this buffer, and it must be large enough to hold the data in the form to which it is converted.</span></span>  
  
-   <span data-ttu-id="17227-110">出力バッファーの長さ。</span><span class="sxs-lookup"><span data-stu-id="17227-110">The length of the output buffer.</span></span>  
  
     <span data-ttu-id="17227-111">この値は、返されるデータが C の固定幅データ (整数、実数、日付構造体など) の場合は無視されます。</span><span class="sxs-lookup"><span data-stu-id="17227-111">This value is ignored if the returned data has a fixed width in C, such as an integer, real number, or date structure.</span></span>  
  
-   <span data-ttu-id="17227-112">使用できるデータのバイト数を返すストレージ バッファーのアドレス。</span><span class="sxs-lookup"><span data-stu-id="17227-112">The address of a storage buffer in which to return the number of bytes of available data.</span></span>  
  
 <span data-ttu-id="17227-113">また、アプリケーションは、結果セットの列をプログラム変数の配列にバインドして、結果セットの行をブロック単位でフェッチする機能をサポートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="17227-113">An application can also bind result set columns to arrays of program variables to support fetching result set rows in blocks.</span></span> <span data-ttu-id="17227-114">配列バインディングには、次の2種類があります。</span><span class="sxs-lookup"><span data-stu-id="17227-114">There are two different types of array binding:</span></span>  
  
-   <span data-ttu-id="17227-115">列方向のバインドは、各列を変数の独自の配列にバインドすると終了します。</span><span class="sxs-lookup"><span data-stu-id="17227-115">Column-wise binding is finished when each column is bound to its own array of variables.</span></span>  
  
     <span data-ttu-id="17227-116">列方向のバインドは、*属性*を SQL_ATTR_ROW_BIND_TYPE に設定し、 *valueptr*を SQL_BIND_BY_COLUMN に設定して、 [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)を呼び出すことによって指定します。</span><span class="sxs-lookup"><span data-stu-id="17227-116">Column-wise binding is specified by calling [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) with *Attribute* set to SQL_ATTR_ROW_BIND_TYPE and *ValuePtr* set to SQL_BIND_BY_COLUMN.</span></span> <span data-ttu-id="17227-117">すべての配列には、同じ数の要素を保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17227-117">All the arrays must have the same number of elements.</span></span>  
  
-   <span data-ttu-id="17227-118">行方向のバインドは、SQL ステートメント内のすべてのパラメーターを 1 単位として、パラメーターの各変数を保持する構造体の配列にバインドすると終了します。</span><span class="sxs-lookup"><span data-stu-id="17227-118">Row-wise binding is finished when all the parameters in the SQL statement are bound as a unit to an array of structures that contain the individual variables for the parameters.</span></span>  
  
     <span data-ttu-id="17227-119">行**方向のバインド**を指定するには、*属性*を SQL_ATTR_ROW_BIND_TYPE に設定し、 *valueptr*に結果セットの列を受け取る変数を保持する構造体のサイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="17227-119">Row-wise binding is specified by calling **SQLSetStmtAttr** with *Attribute* set to SQL_ATTR_ROW_BIND_TYPE and *ValuePtr* set to the size of the structure holding the variables that will receive the result set columns.</span></span>  
  
 <span data-ttu-id="17227-120">また、アプリケーションでは、SQL_ATTR_ROW_ARRAY_SIZE を列または行の配列内の要素数に設定し、SQL_ATTR_ROW_STATUS_PTR と SQL_ATTR_ROWS_FETCHED_PTR も設定します。</span><span class="sxs-lookup"><span data-stu-id="17227-120">The application also sets SQL_ATTR_ROW_ARRAY_SIZE to the number of elements in the column or row arrays and sets SQL_ATTR_ROW_STATUS_PTR and SQL_ATTR_ROWS_FETCHED_PTR.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17227-121">参照</span><span class="sxs-lookup"><span data-stu-id="17227-121">See Also</span></span>  
 [<span data-ttu-id="17227-122">ODBC&#41;&#40;結果の処理</span><span class="sxs-lookup"><span data-stu-id="17227-122">Processing Results &#40;ODBC&#41;</span></span>](processing-results-odbc.md)  
  
  
