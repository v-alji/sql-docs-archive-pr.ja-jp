---
title: パラメーターのバインド |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, parameters
- parameters [SQL Server Native Client], ODBC
- statements [ODBC], parameters
- binding parameters [SQL Server Native Client]
- parameter markers [ODBC]
- unbound parameter markers
- SQLBindParameter function
- ODBC applications, parameters
- bound parameter markers [SQL Server Native Client]
ms.assetid: d6c69739-8f89-475f-a60a-b2f6c06576e2
author: rothja
ms.author: jroth
ms.openlocfilehash: 3402a7efce43d0ce94a20c93504ac1dcb2c7b48f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631856"
---
# <a name="binding-parameters"></a><span data-ttu-id="2f9ff-102">パラメーターのバインド</span><span class="sxs-lookup"><span data-stu-id="2f9ff-102">Binding Parameters</span></span>
  <span data-ttu-id="2f9ff-103">SQL ステートメントの各パラメーター マーカーは、ステートメントを実行する前にアプリケーション内の変数に関連付ける、つまりバインドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f9ff-103">Each parameter marker in an SQL statement must be associated, or bound, to a variable in the application before the statement can be executed.</span></span> <span data-ttu-id="2f9ff-104">これは、 [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md)関数を呼び出すことによって行われます。</span><span class="sxs-lookup"><span data-stu-id="2f9ff-104">This is done by calling the [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) function.</span></span> <span data-ttu-id="2f9ff-105">**SQLBindParameter**は、ドライバーへのプログラム変数 (Address、C データ型など) を記述します。</span><span class="sxs-lookup"><span data-stu-id="2f9ff-105">**SQLBindParameter** describes the program variable (address, C data type, and so on) to the driver.</span></span> <span data-ttu-id="2f9ff-106">また、序数値を示すことでパラメーター マーカーを識別してから、そのパラメーター マーカーが表す SQL オブジェクト表現 (SQL データ型、有効桁数など) を記述します。</span><span class="sxs-lookup"><span data-stu-id="2f9ff-106">It also identifies the parameter marker by indicating its ordinal value and then describes the characteristics of the SQL object it represents (SQL data type, precision, and so on).</span></span>

 <span data-ttu-id="2f9ff-107">パラメーター マーカーは、ステートメントの実行前にいつでもバインドまたは再バインドできます。</span><span class="sxs-lookup"><span data-stu-id="2f9ff-107">Parameter markers can be bound or rebound at any time before a statement is executed.</span></span> <span data-ttu-id="2f9ff-108">次のいずれかの操作を行うまでは、パラメーターのバインドは有効なままです。</span><span class="sxs-lookup"><span data-stu-id="2f9ff-108">A parameter binding remains in effect until one of the following occurs:</span></span>

-   <span data-ttu-id="2f9ff-109">*Option*パラメーターをに設定して[SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md)を呼び出すと、ステートメントハンドルにバインドされているすべてのパラメーターが SQL_RESET_PARAMS 解放されます。</span><span class="sxs-lookup"><span data-stu-id="2f9ff-109">A call to [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) with the *Option* parameter set to SQL_RESET_PARAMS frees all parameters bound to the statement handle.</span></span>

-   <span data-ttu-id="2f9ff-110">*Parameternumber*をバインドされたパラメーターマーカーの序数に設定して**SQLBindParameter**を呼び出すと、前のバインドが自動的に解放されます。</span><span class="sxs-lookup"><span data-stu-id="2f9ff-110">A call to **SQLBindParameter** with *ParameterNumber* set to the ordinal of a bound parameter marker automatically releases the previous binding.</span></span>

 <span data-ttu-id="2f9ff-111">アプリケーションでは、パラメーターをプログラム変数の配列にバインドし、SQL ステートメントをバッチで処理することもできます。</span><span class="sxs-lookup"><span data-stu-id="2f9ff-111">An application can also bind parameters to arrays of program variables to process an SQL statement in batches.</span></span> <span data-ttu-id="2f9ff-112">配列のバインドには、次の 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="2f9ff-112">There are two types of array binding:</span></span>

-   <span data-ttu-id="2f9ff-113">列方向のバインドは、各パラメーターを変数の独自の配列にバインドすることで行います。</span><span class="sxs-lookup"><span data-stu-id="2f9ff-113">Column-wise binding is done when each individual parameter is bound to its own array of variables.</span></span>

     <span data-ttu-id="2f9ff-114">列方向のバインドは、*属性*を SQL_ATTR_PARAM_BIND_TYPE に設定し、 *valueptr*を SQL_PARAM_BIND_BY_COLUMN に設定して、 [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)を呼び出すことによって指定します。</span><span class="sxs-lookup"><span data-stu-id="2f9ff-114">Column-wise binding is specified by calling [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) with *Attribute* set to SQL_ATTR_PARAM_BIND_TYPE and *ValuePtr* set to SQL_PARAM_BIND_BY_COLUMN.</span></span>

-   <span data-ttu-id="2f9ff-115">行方向のバインドは、SQL ステートメント内のすべてのパラメーターを 1 単位として、パラメーターの各変数を保持する構造体の配列にバインドすることで行います。</span><span class="sxs-lookup"><span data-stu-id="2f9ff-115">Row-wise binding is done when all of the parameters in the SQL statement are bound as a unit to an array of structures that contain the individual variables for the parameters.</span></span>

     <span data-ttu-id="2f9ff-116">行方向のバインドは、*属性*を SQL_ATTR_PARAM_BIND_TYPE に設定し、 *valueptr*をプログラム変数を保持する構造体のサイズに設定して、 **SQLSetStmtAttr**を呼び出すことによって指定します。</span><span class="sxs-lookup"><span data-stu-id="2f9ff-116">Row-wise binding is specified by calling **SQLSetStmtAttr** with *Attribute* set to SQL_ATTR_PARAM_BIND_TYPE and *ValuePtr* set to the size of the structure holding the program variables.</span></span>

 <span data-ttu-id="2f9ff-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーは、文字またはバイナリ文字列パラメーターをサーバーに送信するときに、 **SQLBindParameter** *columnsize*パラメーターで指定された長さに値を埋め込みます。</span><span class="sxs-lookup"><span data-stu-id="2f9ff-117">When the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver sends character or binary string parameters to the server, it pads the values to the length specified in **SQLBindParameter** *ColumnSize* parameter.</span></span> <span data-ttu-id="2f9ff-118">ODBC 2.x アプリケーションで*Columnsize*に0が指定されている場合、ドライバーは、パラメーター値をデータ型の有効桁数に埋め込みます。</span><span class="sxs-lookup"><span data-stu-id="2f9ff-118">If an ODBC 2.x application specifies 0 for *ColumnSize*, the driver pads the parameter value to the precision of the data type.</span></span> <span data-ttu-id="2f9ff-119">有効桁数は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サーバーに接続している場合は 8,000、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続している場合は 255 です。</span><span class="sxs-lookup"><span data-stu-id="2f9ff-119">The precision is 8000 when connected to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] servers, 255 when connected to earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2f9ff-120">バリアント型の列の場合、 *Columnsize*はバイト単位です。</span><span class="sxs-lookup"><span data-stu-id="2f9ff-120">*ColumnSize* is in bytes for variant columns.</span></span>

 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="2f9ff-121">では、ストアド プロシージャ パラメーターの名前を定義できます。</span><span class="sxs-lookup"><span data-stu-id="2f9ff-121">supports defining names for stored procedure parameters.</span></span> <span data-ttu-id="2f9ff-122">また、ODBC 3.5 では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ストアド プロシージャを呼び出すときに使用する名前付きパラメーターのサポートも導入されました。</span><span class="sxs-lookup"><span data-stu-id="2f9ff-122">ODBC 3.5 also introduced support for named parameters used when calling [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedures.</span></span> <span data-ttu-id="2f9ff-123">このサポートは次の目的に使用します。</span><span class="sxs-lookup"><span data-stu-id="2f9ff-123">This support can be used to:</span></span>

-   <span data-ttu-id="2f9ff-124">ストアド プロシージャを呼び出し、そのストアド プロシージャ用に定義したパラメーターのサブセットに値を提供します。</span><span class="sxs-lookup"><span data-stu-id="2f9ff-124">Call a stored procedure and provide values for a subset of the parameters defined for the stored procedure.</span></span>

-   <span data-ttu-id="2f9ff-125">アプリケーション内で、ストアド プロシージャの作成時に指定した順序とは異なる順序でパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="2f9ff-125">Specify the parameters in a different order in the application than the order specified when the stored procedure was created.</span></span>

 <span data-ttu-id="2f9ff-126">名前付きパラメーターは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] `EXECUTE` ステートメントまたは ODBC CALL エスケープシーケンスを使用してストアドプロシージャを実行する場合にのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="2f9ff-126">Named parameters are only supported when using the [!INCLUDE[tsql](../../includes/tsql-md.md)] `EXECUTE` statement or the ODBC CALL escape sequence to execute a stored procedure.</span></span>

 <span data-ttu-id="2f9ff-127">ストアド プロシージャ パラメーターに `SQL_DESC_NAME` を設定する場合、クエリ内のすべてのストアド プロシージャ パラメーターにも `SQL_DESC_NAME` を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f9ff-127">If `SQL_DESC_NAME` is set for a stored procedure parameter, all stored procedure parameters in the query should also set `SQL_DESC_NAME`.</span></span>  <span data-ttu-id="2f9ff-128">パラメーターが設定されているストアドプロシージャの呼び出しでリテラルを使用する場合、リテラルでは `SQL_DESC_NAME` *' name*value ' という形式を使用する必要があり = *value*ます。ここで、 *name*はストアドプロシージャのパラメーター名 (たとえば、 @p1 ) です。</span><span class="sxs-lookup"><span data-stu-id="2f9ff-128">If literals are used in stored procedure calls, where parameters have `SQL_DESC_NAME` set, the literals should use the format *'name*=*value*', where *name* is the stored procedure parameter name (for example, @p1).</span></span> <span data-ttu-id="2f9ff-129">詳細については、「[名前によるパラメーターのバインド (名前付きパラメーター)](https://go.microsoft.com/fwlink/?LinkId=167215)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f9ff-129">For more information, see [Binding Parameters by Name (Named Parameters)](https://go.microsoft.com/fwlink/?LinkId=167215).</span></span>

## <a name="see-also"></a><span data-ttu-id="2f9ff-130">参照</span><span class="sxs-lookup"><span data-stu-id="2f9ff-130">See Also</span></span>
 [<span data-ttu-id="2f9ff-131">ステートメント パラメーターの使用</span><span class="sxs-lookup"><span data-stu-id="2f9ff-131">Using Statement Parameters</span></span>](using-statement-parameters.md)


