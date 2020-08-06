---
title: SQLGetData |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetData function
ms.assetid: 204848be-8787-45b4-816f-a60ac9d56fcf
author: rothja
ms.author: jroth
ms.openlocfilehash: c351cf7340bc7b0afeb76b139bd75aa429f56e10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631001"
---
# <a name="sqlgetdata"></a><span data-ttu-id="73b51-102">SQLGetData</span><span class="sxs-lookup"><span data-stu-id="73b51-102">SQLGetData</span></span>
  <span data-ttu-id="73b51-103">**SQLGetData**は、列の値をバインドせずに結果セットのデータを取得するために使用します。</span><span class="sxs-lookup"><span data-stu-id="73b51-103">**SQLGetData** is used to retrieve result set data without binding column values.</span></span> <span data-ttu-id="73b51-104">**SQLGetData**を同じ列に対して連続して呼び出すと、 **text**、 **ntext**、または**image**データ型の列から大量のデータを取得できます。</span><span class="sxs-lookup"><span data-stu-id="73b51-104">**SQLGetData** can be called successively on the same column to retrieve large amounts of data from a column with a **text**, **ntext**, or **image** data type.</span></span>  
  
 <span data-ttu-id="73b51-105">アプリケーションでは、変数をバインドして結果セット データをフェッチする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="73b51-105">There is no requirement that an application bind variables to fetch result set data.</span></span> <span data-ttu-id="73b51-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **SQLGetData**を使用して、Native Client ODBC ドライバーから任意の列のデータを取得できます。</span><span class="sxs-lookup"><span data-stu-id="73b51-106">The data of any column can be retrieved from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver by using **SQLGetData**.</span></span>  
  
 <span data-ttu-id="73b51-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーでは、ランダム列の順序でデータを取得するための**SQLGetData**の使用はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="73b51-107">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver does not support using **SQLGetData** to retrieve data in random column order.</span></span> <span data-ttu-id="73b51-108">**SQLGetData**で処理されるすべてのバインドされていない列には、結果セット内のバインドされた列よりも大きな列序数が必要です。</span><span class="sxs-lookup"><span data-stu-id="73b51-108">All unbound columns processed with **SQLGetData** must have higher column ordinals than the bound columns in the result set.</span></span> <span data-ttu-id="73b51-109">アプリケーションでは、バインドされていない列の値を、列序数の小さい列から大きい列へと処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="73b51-109">The application must process data from the lowest unbound ordinal column value to the highest.</span></span> <span data-ttu-id="73b51-110">前に処理した列よりも列序数が小さい列からデータを取得しようとすると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="73b51-110">Attempting to retrieve data from a lower ordinally numbered column results in an error.</span></span> <span data-ttu-id="73b51-111">アプリケーションで、結果セット行を報告するためにサーバー カーソルを使用している場合は、現在の行を再フェッチしてから列の値をフェッチできます。</span><span class="sxs-lookup"><span data-stu-id="73b51-111">If the application is using server cursors to report result set rows, the application can refetch the current row and then fetch the value of a column.</span></span> <span data-ttu-id="73b51-112">ステートメントが既定の読み取り専用、順方向専用カーソルで実行される場合、ステートメントを再実行して**SQLGetData**をバックアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="73b51-112">If a statement is executed on the default read-only, forward-only cursor, you must re-execute the statement to back up **SQLGetData**.</span></span>  
  
 <span data-ttu-id="73b51-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーでは、 **SQLGetData**を使用して取得した**text**型、 **ntext**型、および**image**型のデータの長さが正確に報告されます。</span><span class="sxs-lookup"><span data-stu-id="73b51-113">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver accurately reports the length of **text**, **ntext**, and **image** data retrieved using **SQLGetData**.</span></span> <span data-ttu-id="73b51-114">アプリケーションでは、 *StrLen_or_IndPtr*パラメーターの戻り値を使用して、長いデータを迅速に取得することができます。</span><span class="sxs-lookup"><span data-stu-id="73b51-114">The application can make good use of the *StrLen_or_IndPtr* parameter return to retrieve long data rapidly.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="73b51-115">大きな値型の場合、 *StrLen_or_IndPtr*はデータの切り捨て時に SQL_NO_TOTAL を返します。</span><span class="sxs-lookup"><span data-stu-id="73b51-115">For large value types, *StrLen_or_IndPtr* will return SQL_NO_TOTAL in cases of data truncation.</span></span>  
  
## <a name="sqlgetdata-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="73b51-116">SQLGetData による機能強化された日付と時刻のサポート</span><span class="sxs-lookup"><span data-stu-id="73b51-116">SQLGetData Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="73b51-117">Date 型または time 型の結果列の値は、「 [SQL から C への変換](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md)」で説明されているように変換されます。</span><span class="sxs-lookup"><span data-stu-id="73b51-117">Result column values of date/time types are converted as described in [Conversions from SQL to C](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md).</span></span>  
  
 <span data-ttu-id="73b51-118">詳細については、「[日付と時刻の機能強化 &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73b51-118">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlgetdata-support-for-large-clr-udts"></a><span data-ttu-id="73b51-119">SQLGetData による大きな CLR UDT のサポート</span><span class="sxs-lookup"><span data-stu-id="73b51-119">SQLGetData Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="73b51-120">**SQLGetData**は、大きな CLR ユーザー定義型 (udt) をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="73b51-120">**SQLGetData** supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="73b51-121">詳細については、「[大容量の CLR ユーザー定義型 &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73b51-121">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="73b51-122">例</span><span class="sxs-lookup"><span data-stu-id="73b51-122">Example</span></span>  
  
```  
SQLHDBC     hDbc = NULL;  
SQLHSTMT    hStmt = NULL;  
long        lEmpID;  
PBYTE       pPicture;  
SQLINTEGER  pIndicators[2];  
  
// Get an environment, connection, and so on.  
...  
  
// Get a statement handle and execute a command.  
SQLAllocHandle(SQL_HANDLE_STMT, hDbc, &hStmt);  
  
if (SQLExecDirect(hStmt,  
    (SQLCHAR*) "SELECT EmployeeID, Photo FROM Employees",  
    SQL_NTS) == SQL_ERROR)  
    {  
    // Handle error and return.  
    }  
  
// Retrieve data from row set.  
SQLBindCol(hStmt, 1, SQL_C_LONG, (SQLPOINTER) &lEmpID, sizeof(long),  
    &pIndicators[0]);  
  
while (SQLFetch(hStmt) == SQL_SUCCESS)  
    {  
    cout << "EmployeeID: " << lEmpID << "\n";  
  
    // Call SQLGetData to determine the amount of data that's waiting.  
    if (SQLGetData(hStmt, 2, SQL_C_BINARY, pPicture, 0, &pIndicators[1])  
        == SQL_SUCCESS_WITH_INFO)  
        {  
        cout << "Photo size: " pIndicators[1] << "\n\n";  
  
        // Get all the data at once.  
        pPicture = new BYTE[pIndicators[1]];  
        if (SQLGetData(hStmt, 2, SQL_C_DEFAULT, pPicture,  
            pIndicators[1], &pIndicators[1]) != SQL_SUCCESS)  
            {  
            // Handle error and continue.  
            }  
  
        delete [] pPicture;  
        }  
    else  
        {  
        // Handle error on attempt to get data length.  
        }  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="73b51-123">参照</span><span class="sxs-lookup"><span data-stu-id="73b51-123">See Also</span></span>  
 <span data-ttu-id="73b51-124">[SQLGetData 関数](https://go.microsoft.com/fwlink/?LinkId=59350) </span><span class="sxs-lookup"><span data-stu-id="73b51-124">[SQLGetData Function](https://go.microsoft.com/fwlink/?LinkId=59350) </span></span>  
 [<span data-ttu-id="73b51-125">ODBC API 実装の詳細</span><span class="sxs-lookup"><span data-stu-id="73b51-125">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
