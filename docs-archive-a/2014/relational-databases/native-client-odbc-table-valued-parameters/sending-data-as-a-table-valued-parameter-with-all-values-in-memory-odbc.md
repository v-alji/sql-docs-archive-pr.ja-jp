---
title: メモリ内のすべての値を含むテーブル値パラメーターとしてのデータの送信 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), sending data to a stored procedure with all values in memory
ms.assetid: 8b96282f-00d5-4e28-8111-0a87ae6d7781
author: rothja
ms.author: jroth
ms.openlocfilehash: f53e129ea49b1faa08be5247c51b5e74353e2f31
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740898"
---
# <a name="sending-data-as-a-table-valued-parameter-with-all-values-in-memory-odbc"></a><span data-ttu-id="c681c-102">すべての値がメモリ内にある場合にテーブル値パラメーターとしてデータを送信 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="c681c-102">Sending Data as a Table-Valued Parameter with All Values in Memory (ODBC)</span></span>
  <span data-ttu-id="c681c-103">このトピックでは、すべての値がメモリ内にある場合に、データをテーブル値パラメーターとしてストアド プロシージャに送信する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c681c-103">This topic describes how to send data to a stored procedure as a table-valued parameter when all values are in memory.</span></span> <span data-ttu-id="c681c-104">テーブル値パラメーターを示す別のサンプルについては、「[テーブル値パラメーターの使用 &#40;ODBC&#41;](table-valued-parameters-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c681c-104">For another sample demonstrating table-valued parameters, see [Use Table-Valued Parameters &#40;ODBC&#41;](table-valued-parameters-odbc.md).</span></span>  
  
## <a name="prerequisite"></a><span data-ttu-id="c681c-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="c681c-105">Prerequisite</span></span>  
 <span data-ttu-id="c681c-106">この手順では、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] がサーバーで実行されていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="c681c-106">This procedure assumes that the following [!INCLUDE[tsql](../../includes/tsql-md.md)] has been executed on the server:</span></span>  
  
```  
create type TVParam as table(ProdCode integer, Qty integer)  
create procedure TVPOrderEntry(@CustCode varchar(5), @Items TVPParam,   
            @OrdNo integer output, @OrdDate datetime output)  
         as   
         set @OrdDate = GETDATE();  
         insert into TVPOrd (OrdDate, CustCode)   
values (@OrdDate, @CustCode) output OrdNo);   
         select @OrdNo = SCOPE_IDENTITY();   
         insert into TVPItem (OrdNo, ProdCode, Qty)  
select @OrdNo, @Items.ProdCode, @Items.Qty   
from @Items  
```  
  
## <a name="to-send-the-data"></a><span data-ttu-id="c681c-107">データを送信するには</span><span class="sxs-lookup"><span data-stu-id="c681c-107">To Send the Data</span></span>  
  
1.  <span data-ttu-id="c681c-108">SQL パラメーターの変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="c681c-108">Declare variables for the SQL parameters.</span></span> <span data-ttu-id="c681c-109">この場合、テーブル値はすべてメモリ内に保持されているため、テーブル値の列の値は配列として宣言されます。</span><span class="sxs-lookup"><span data-stu-id="c681c-109">In this case, the table value is held entirely in memory, so values for the columns of the table value are declared as arrays.</span></span>  
  
    ```  
    SQLRETURN r;  
    // Variables for SQL parameters.  
    #define ITEM_ARRAY_SIZE 20  
  
    SQLCHAR CustCode[6];  
    SQLCHAR *TVP = (SQLCHAR *) "TVParam";  
    SQLINTEGER ProdCode[ITEM_ARRAY_SIZE], Qty[ITEM_ARRAY_SIZE];  
    SQLINTEGER OrdNo;  
    char OrdDate[23];  
  
    // Variables for indicator/length variables associated with parameters.  
    SQLLEN cbCustCode, cbTVP, cbProdCode[ITEM_ARRAY_SIZE], cbQty[ITEM_ARRAY_SIZE], cbOrdNo, cbOrdDate;  
    ```  
  
2.  <span data-ttu-id="c681c-110">パラメーターをバインドします。</span><span class="sxs-lookup"><span data-stu-id="c681c-110">Bind the parameters.</span></span> <span data-ttu-id="c681c-111">テーブル値パラメーターが使用されている場合、パラメーターのバインドは 2 段階の処理になります。</span><span class="sxs-lookup"><span data-stu-id="c681c-111">Binding parameters is a two stage process when table-valued parameters are used.</span></span> <span data-ttu-id="c681c-112">第 1 段階として、次のように、ストアド プロシージャのパラメーターを通常の方法でバインドします。</span><span class="sxs-lookup"><span data-stu-id="c681c-112">In the first stage, step parameters for the stored procedure are bound in the normal way, as follows.</span></span>  
  
    ```  
    // Bind parameters for call to TVPOrderEntryDirect.  
    // 1 - Custcode input  
    r = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT,SQL_VARCHAR, SQL_C_CHAR, 5, 0, CustCode, sizeof(CustCode), &cbCustCode);  
  
    // 2 - Items TVP  
    r = SQLBindParameter(hstmt,   
        2,// ParameterNumber  
        SQL_PARAM_INPUT,// InputOutputType  
        SQL_C_DEFAULT,// ValueType   
        SQL_SS_TABLE,// Parametertype  
        ITEM_ARRAY_SIZE,// ColumnSize: For a table-valued parameter this is the row array size.  
        0,// DecimalDigits: For a table-valued parameter this is always 0.   
        TVP,// ParameterValuePtr: For a table-valued parameter this is the type name of the   
    //table-valued parameter, and also a token returned by SQLParamData.  
        SQL_NTS,// BufferLength: For a table-valued parameter this is the length of the type name or SQL_NTS.  
        &cbTVP);// StrLen_or_IndPtr: For a table-valued parameter this is the number of rows actually used.  
  
    // 3 - OrdNo output  
    r = SQLBindParameter(hstmt, 3, SQL_PARAM_OUTPUT,SQL_INTEGER, SQL_C_LONG, 0, 0, &OrdNo,  
       sizeof(SQLINTEGER), &cbOrdNo);  
    // 4 - OrdDate output  
    r = SQLBindParameter(hstmt, 4, SQL_PARAM_OUTPUT,SQL_TYPE_TIMESTAMP, SQL_C_CHAR, 23, 3, &OrdDate,   
       sizeof(OrdDate), &cbOrdDate);  
    ```  
  
3.  <span data-ttu-id="c681c-113">第 2 段階として、テーブル値パラメーターの列をバインドします。</span><span class="sxs-lookup"><span data-stu-id="c681c-113">The second stage of parameter binding is to bind the columns for the table-valued parameter.</span></span> <span data-ttu-id="c681c-114">最初、テーブル値パラメーターの序数にフォーカスが設定されます。</span><span class="sxs-lookup"><span data-stu-id="c681c-114">The parameter focus is first set to the ordinal of the table-valued parameter.</span></span> <span data-ttu-id="c681c-115">次に、テーブル値の列は、ストアドプロシージャのパラメーターである場合と同じように、SQLBindParameter を使用してバインドされます。ただし、ParameterNumber には列序数が使用されます。</span><span class="sxs-lookup"><span data-stu-id="c681c-115">Then columns of the table value are bound by using SQLBindParameter in the same way as they would be if they were parameters of the stored procedure, but with column ordinals for ParameterNumber.</span></span> <span data-ttu-id="c681c-116">テーブル値パラメーターがまだある場合は、順番にフォーカスを設定し、その列をバインドします。</span><span class="sxs-lookup"><span data-stu-id="c681c-116">If there were more table-valued parameters, we would set the focus to each in turn and bind their columns.</span></span> <span data-ttu-id="c681c-117">最後に、パラメーターのフォーカスが 0 にリセットされます。</span><span class="sxs-lookup"><span data-stu-id="c681c-117">Finally, the parameter focus is reset to 0.</span></span>  
  
    ```  
    // Bind columns for the table-valued parameter (param 2).  
    // First set focus on param 2.  
    r = SQLSetStmtAttr(hstmt, SQL_SOPT_SS_PARAM_FOCUS, (SQLPOINTER) 2, SQL_IS_INTEGER);  
  
    // Col 1 - ProdCode  
    r = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT,SQL_INTEGER, SQL_C_LONG, 0, 0, ProdCode, sizeof(SQLINTEGER), cbProdCode);  
    // Col 2 - Qty  
    r = SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT,SQL_INTEGER, SQL_C_LONG, 0, 0, Qty, sizeof(SQLINTEGER), cbQty);  
  
    // Reset param focus.  
    r = SQLSetStmtAttr(hstmt, SQL_SOPT_SS_PARAM_FOCUS, (SQLPOINTER) 0, SQL_IS_INTEGER);  
    ```  
  
4.  <span data-ttu-id="c681c-118">パラメーターのバッファーを設定します。</span><span class="sxs-lookup"><span data-stu-id="c681c-118">Populate the parameter buffers.</span></span> <span data-ttu-id="c681c-119">`cbTVP` は、サーバーに送信される行数に設定されます。</span><span class="sxs-lookup"><span data-stu-id="c681c-119">`cbTVP` is set to the number of rows to be sent to the server.</span></span>  
  
    ```  
    // Populate parameters.  
    cbTVP = 0; // Number of rows available for input.  
    strcpy_s((char *) CustCode, sizeof(CustCode), "CUST1"); cbCustCode = SQL_NTS;  
  
    ProdCode[cbTVP] = 1215;cbProdCode[cbTVP] = sizeof(SQLINTEGER);   
    Qty[cbTVP] = 5;cbQty[cbTVP] = sizeof(SQLINTEGER);   
    cbTVP++; // Number of rows available for input  
  
    ProdCode[cbTVP] = 1017;cbProdCode[cbTVP] = sizeof(SQLINTEGER);   
    Qty[cbTVP] = 2;cbQty[cbTVP] = sizeof(SQLINTEGER);   
    cbTVP++; // Number of rows available for input.  
    ```  
  
5.  <span data-ttu-id="c681c-120">プロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c681c-120">Call the procedure:</span></span>  
  
    ```  
    // Call the procedure.  
    r = SQLExecDirect(hstmt, (SQLCHAR *) "{call TVPOrderEntry(?, ?, ?, ?)}",SQL_NTS);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c681c-121">参照</span><span class="sxs-lookup"><span data-stu-id="c681c-121">See Also</span></span>  
 [<span data-ttu-id="c681c-122">ODBC テーブル値パラメーターのプログラミング例</span><span class="sxs-lookup"><span data-stu-id="c681c-122">ODBC Table-Valued Parameter Programming Examples</span></span>](../../database-engine/dev-guide/odbc-table-valued-parameter-programming-examples.md)  
  
  
