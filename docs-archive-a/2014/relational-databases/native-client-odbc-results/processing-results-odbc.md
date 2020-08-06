---
title: 結果の処理 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC], about result sets
- SQLRowCount function
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- COMPUTE clause
- result sets [ODBC]
- COMPUTE BY clause
ms.assetid: 61a8db19-6571-47dd-84e8-fcc97cb60b45
author: rothja
ms.author: jroth
ms.openlocfilehash: 72c0d15231b07a23f10a03b0fca270d1d014891c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741970"
---
# <a name="processing-results-odbc"></a><span data-ttu-id="7d0ef-102">結果の処理 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="7d0ef-102">Processing Results (ODBC)</span></span>
  <span data-ttu-id="7d0ef-103">アプリケーションで SQL ステートメントが実行されると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では結果として生成されるすべてのデータを 1 つ以上の結果セットとして返します。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-103">After an application submits a SQL statement, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] returns any resulting data as one or more result sets.</span></span> <span data-ttu-id="7d0ef-104">結果セットとは、クエリの条件に一致する行と列の集まりです。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-104">A result set is a set of rows and columns that match the criteria of the query.</span></span> <span data-ttu-id="7d0ef-105">SELECT ステートメント、カタログ関数、および一部のストアド プロシージャでは、アプリケーションで使用できる結果セットが表形式で生成されます。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-105">SELECT statements, catalog functions, and some stored procedures produce a result set made available to an application in tabular form.</span></span> <span data-ttu-id="7d0ef-106">実行される SQL ステートメントがストアド プロシージャ、複数のコマンドを含むバッチ、またはキーワードを含む SELECT ステートメントの場合、処理対象の結果セットが複数生成されます。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-106">If the executed SQL statement is a stored procedure, a batch containing multiple commands, or a SELECT statement containing keywords, there will be multiple result sets to process.</span></span>  
  
 <span data-ttu-id="7d0ef-107">ODBC カタログ関数では、データを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-107">ODBC catalog functions also can retrieve data.</span></span> <span data-ttu-id="7d0ef-108">たとえば、 [Sqlcolumns](../native-client-odbc-api/sqlcolumns.md)はデータソース内の列に関するデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-108">For example, [SQLColumns](../native-client-odbc-api/sqlcolumns.md) retrieves data about columns in the data source.</span></span> <span data-ttu-id="7d0ef-109">これらの結果セットには、0 行以上の行を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-109">These result sets can contain zero or more rows.</span></span>  
  
 <span data-ttu-id="7d0ef-110">GRANT や REVOKE など、結果セットが返されない SQL ステートメントもあります。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-110">Other SQL statements, such as GRANT or REVOKE, do not return result sets.</span></span> <span data-ttu-id="7d0ef-111">これらのステートメントでは、通常、 **Sqlexecute**または**SQLExecDirect**からのリターンコードだけがステートメントが成功したことを示しています。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-111">For these statements, the return code from **SQLExecute** or **SQLExecDirect** is usually the only indication the statement was successful.</span></span>  
  
 <span data-ttu-id="7d0ef-112">INSERT ステートメント、UPDATE ステートメント、および DELETE ステートメントからは、変更によって処理された行数だけを含む結果セットが返されます。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-112">Each INSERT, UPDATE, and DELETE statement returns a result set containing only the number of rows affected by the modification.</span></span> <span data-ttu-id="7d0ef-113">この数は、アプリケーションが[SQLRowCount](../native-client-odbc-api/sqlrowcount.md)を呼び出したときに使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-113">This count is made available when application calls [SQLRowCount](../native-client-odbc-api/sqlrowcount.md).</span></span> <span data-ttu-id="7d0ef-114">ODBC 3.*x*アプリケーションは、 **SQLRowCount**を呼び出して結果セットを取得するか、 [sqlmoreresults](../native-client-odbc-api/sqlmoreresults.md)を呼び出して取り消す必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-114">ODBC 3.*x* applications must either call **SQLRowCount** to retrieve the result set or [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) to cancel it.</span></span> <span data-ttu-id="7d0ef-115">複数の INSERT、UPDATE、または DELETE ステートメントを含むバッチまたはストアドプロシージャを実行する場合は、各変更ステートメントの結果セットを**SQLRowCount**を使用して処理するか、 **Sqlmoreresults**を使用して取り消す必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-115">When an application executes a batch or stored procedure containing multiple INSERT, UPDATE, or DELETE statements, the result set from each modification statement must be processed using **SQLRowCount** or cancelled using **SQLMoreResults**.</span></span> <span data-ttu-id="7d0ef-116">バッチやストアド プロシージャに SET NOCOUNT ON ステートメントを含めることで、これらの数をキャンセルできます。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-116">These counts can be cancelled by including a SET NOCOUNT ON statement in the batch or stored procedure.</span></span>  
  
 <span data-ttu-id="7d0ef-117">Transact-SQL には、NOCOUNT ステートメントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-117">Transact-SQL includes the SET NOCOUNT statement.</span></span> <span data-ttu-id="7d0ef-118">NOCOUNT オプションが on に設定されている場合、SQL Server は、ステートメントの影響を受ける行の数を返しません。また、 **SQLRowCount**は0を返します。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-118">When the NOCOUNT option is set on, SQL Server does not return the counts of the rows affected by a statement and **SQLRowCount** returns 0.</span></span> <span data-ttu-id="7d0ef-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーのバージョンでは、SQL_SOPT_SS_NOCOUNT_STATUS、NOCOUNT オプションがオンとオフのどちらであるかを報告するために、ドライバー固有の[SQLGetStmtAttr](../native-client-odbc-api/sqlgetstmtattr.md)オプションが導入されています。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-119">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver version introduces a driver-specific [SQLGetStmtAttr](../native-client-odbc-api/sqlgetstmtattr.md) option, SQL_SOPT_SS_NOCOUNT_STATUS, to report on whether the NOCOUNT option is on or off.</span></span> <span data-ttu-id="7d0ef-120">**SQLRowCount**は常に0を返し、アプリケーションは SQL_SOPT_SS_NOCOUNT_STATUS をテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-120">Anytime **SQLRowCount** returns 0, the application should test SQL_SOPT_SS_NOCOUNT_STATUS.</span></span> <span data-ttu-id="7d0ef-121">SQL_NC_ON が返された場合、 **SQLRowCount**の値が0の場合は、SQL Server によって行数が返されなかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-121">If SQL_NC_ON is returned, the value of 0 from **SQLRowCount** only indicates that SQL Server has not returned a row count.</span></span> <span data-ttu-id="7d0ef-122">SQL_NC_OFF が返された場合は、NOCOUNT が無効になっていることを意味し、 **SQLRowCount**からの値が0の場合は、ステートメントが行に影響していないことを示します。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-122">If SQL_NC_OFF is returned, it means that NOCOUNT is off and the value of 0 from **SQLRowCount** indicates that the statement did not affect any rows.</span></span> <span data-ttu-id="7d0ef-123">SQL_SOPT_SS_NOCOUNT_STATUS が SQL_NC_OFF 場合、アプリケーションには**SQLRowCount**の値が表示されません。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-123">Applications should not display the value of **SQLRowCount** when SQL_SOPT_SS_NOCOUNT_STATUS is SQL_NC_OFF.</span></span> <span data-ttu-id="7d0ef-124">大きなバッチやストアド プロシージャには、複数の SET NOCOUNT ステートメントが含まれていることがあるので、プログラマは SQL_SOPT_SS_NOCOUNT_STATUS が一定であると想定することはできません。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-124">Large batches or stored procedures may contain multiple SET NOCOUNT statements so programmers cannot assume SQL_SOPT_SS_NOCOUNT_STATUS remains constant.</span></span> <span data-ttu-id="7d0ef-125">**SQLRowCount**が0を返すたびに、オプションをテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-125">The option should be tested each time **SQLRowCount** returns 0.</span></span>  
  
 <span data-ttu-id="7d0ef-126">他のいくつかの Transact-SQL ステートメントは、結果セットではなく、メッセージにデータを含めて返します。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-126">Several other Transact-SQL statements return their data in messages rather than result sets.</span></span> <span data-ttu-id="7d0ef-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーは、これらのメッセージを受信すると SQL_SUCCESS_WITH_INFO を返して、情報メッセージが使用可能であることをアプリケーションに知らせます。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-127">When the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver receives these messages, it returns SQL_SUCCESS_WITH_INFO to let the application know that informational messages are available.</span></span> <span data-ttu-id="7d0ef-128">その後、アプリケーションは**SQLGetDiagRec**を呼び出してこれらのメッセージを取得できます。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-128">The application can then call **SQLGetDiagRec** to retrieve these messages.</span></span> <span data-ttu-id="7d0ef-129">このように機能する [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを次に示します。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-129">The [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that work this way are:</span></span>  
  
-   <span data-ttu-id="7d0ef-130">DBCC</span><span class="sxs-lookup"><span data-stu-id="7d0ef-130">DBCC</span></span>  
  
-   <span data-ttu-id="7d0ef-131">SET SHOWPLAN (以前のバージョンの SQL Server で使用可能)</span><span class="sxs-lookup"><span data-stu-id="7d0ef-131">SET SHOWPLAN (available with earlier versions of SQL Server)</span></span>  
  
-   <span data-ttu-id="7d0ef-132">SET STATISTICS</span><span class="sxs-lookup"><span data-stu-id="7d0ef-132">SET STATISTICS</span></span>  
  
-   <span data-ttu-id="7d0ef-133">PRINT</span><span class="sxs-lookup"><span data-stu-id="7d0ef-133">PRINT</span></span>  
  
-   <span data-ttu-id="7d0ef-134">RAISERROR</span><span class="sxs-lookup"><span data-stu-id="7d0ef-134">RAISERROR</span></span>  
  
 <span data-ttu-id="7d0ef-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーは、重大度が11以上の RAISERROR で SQL_ERROR を返します。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-135">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver returns SQL_ERROR on a RAISERROR with a severity of 11 or higher.</span></span> <span data-ttu-id="7d0ef-136">RAISERROR の重大度が 19 以上の場合は、接続も削除されます。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-136">If the severity of the RAISERROR is 19 or higher, the connection is also dropped.</span></span>  
  
 <span data-ttu-id="7d0ef-137">アプリケーションでは、SQL ステートメントから返される結果セットを処理するために次の処理を行います。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-137">To process the result sets from an SQL statement, the application:</span></span>  
  
-   <span data-ttu-id="7d0ef-138">結果セットの特性を判断します。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-138">Determines the characteristics of the result set.</span></span>  
  
-   <span data-ttu-id="7d0ef-139">プログラム変数に列をバインドします。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-139">Binds the columns to program variables.</span></span>  
  
-   <span data-ttu-id="7d0ef-140">1 つの値、値の行全体、または値の複数の行を取得します。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-140">Retrieves a single value, an entire row of values, or multiple rows of values.</span></span>  
  
-   <span data-ttu-id="7d0ef-141">さらに結果セットが存在するかどうかを確認するテストを行い、存在する場合は、新しい結果セットの特性を判断する処理まで戻って、それ以降をループ処理します。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-141">Tests to see if there are more result sets, and if so, loops back to determining the characteristics of the new result set.</span></span>  
  
 <span data-ttu-id="7d0ef-142">データ ソースから行を取得し、取得した行をアプリケーションに返す処理をフェッチと呼びます。</span><span class="sxs-lookup"><span data-stu-id="7d0ef-142">The process of retrieving rows from the data source and returning them to the application is called fetching.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7d0ef-143">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="7d0ef-143">In This Section</span></span>  
  
-   [<span data-ttu-id="7d0ef-144">ODBC&#41;&#40;結果セットの特性の決定</span><span class="sxs-lookup"><span data-stu-id="7d0ef-144">Determining the Characteristics of a Result Set &#40;ODBC&#41;</span></span>](determining-the-characteristics-of-a-result-set-odbc.md)  
  
-   [<span data-ttu-id="7d0ef-145">ストレージの割り当て</span><span class="sxs-lookup"><span data-stu-id="7d0ef-145">Assigning Storage</span></span>](assigning-storage.md)  
  
-   [<span data-ttu-id="7d0ef-146">結果データのフェッチ</span><span class="sxs-lookup"><span data-stu-id="7d0ef-146">Fetching Result Data</span></span>](fetching-result-data.md)  
  
-   [<span data-ttu-id="7d0ef-147">ODBC&#41;&#40;のデータ型のマッピング</span><span class="sxs-lookup"><span data-stu-id="7d0ef-147">Mapping Data Types &#40;ODBC&#41;</span></span>](mapping-data-types-odbc.md)  
  
-   [<span data-ttu-id="7d0ef-148">データ型の使用方法</span><span class="sxs-lookup"><span data-stu-id="7d0ef-148">Data Type Usage</span></span>](data-type-usage.md)  
  
-   [<span data-ttu-id="7d0ef-149">文字データの自動変換</span><span class="sxs-lookup"><span data-stu-id="7d0ef-149">Autotranslation of Character Data</span></span>](autotranslation-of-character-data.md)  
  
## <a name="see-also"></a><span data-ttu-id="7d0ef-150">参照</span><span class="sxs-lookup"><span data-stu-id="7d0ef-150">See Also</span></span>  
 <span data-ttu-id="7d0ef-151">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="7d0ef-151">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span></span>  
 [<span data-ttu-id="7d0ef-152">結果の処理方法に関するトピック &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="7d0ef-152">Processing Results How-to Topics &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md)  
  
  
