---
title: SQLGetDescField |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetDescField function
ms.assetid: 3e59a37a-28ee-4c91-8968-7fe3b966739d
author: rothja
ms.author: jroth
ms.openlocfilehash: 4538396dbfb5406d0464c4730c1f6f3bd5882799
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642067"
---
# <a name="sqlgetdescfield"></a><span data-ttu-id="fe9fb-102">SQLGetDescField</span><span class="sxs-lookup"><span data-stu-id="fe9fb-102">SQLGetDescField</span></span>
  <span data-ttu-id="fe9fb-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーでは、実装行記述子 (IRD) に対してのみドライバー固有の記述子フィールドが公開されます。</span><span class="sxs-lookup"><span data-stu-id="fe9fb-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver exposes driver-specific descriptor fields for the implementation row descriptor (IRD) only.</span></span> <span data-ttu-id="fe9fb-104">IRD 内で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、ドライバー固有の列属性を介して記述子フィールドが参照されます。</span><span class="sxs-lookup"><span data-stu-id="fe9fb-104">Within the IRD, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] descriptor fields are referenced through driver-specific column attributes.</span></span> <span data-ttu-id="fe9fb-105">使用可能なドライバー固有の記述子フィールドの完全な一覧については、「 [Sqlcolattribute](sqlcolattribute.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe9fb-105">For information about a complete list of available driver-specific descriptor fields, see [SQLColAttribute](sqlcolattribute.md).</span></span>  
  
 <span data-ttu-id="fe9fb-106">列 ID 文字列を含む記述子フィールドは、多くの場合、長さが 0 の文字列になります。</span><span class="sxs-lookup"><span data-stu-id="fe9fb-106">Descriptor fields that contain column identifier strings are often zero-length strings.</span></span> <span data-ttu-id="fe9fb-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固有のすべての記述子フィールドの値は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="fe9fb-107">All [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific descriptor field values are read-only.</span></span>  
  
 <span data-ttu-id="fe9fb-108">SQLColAttribute で取得される属性と同様に、行レベルの属性 (SQL_CA_SS_COMPUTE_ID など) を報告する記述子フィールドは、結果セットのすべての列について報告されます。</span><span class="sxs-lookup"><span data-stu-id="fe9fb-108">Like attributes retrieved with SQLColAttribute, descriptor fields that report row-level attributes (such as SQL_CA_SS_COMPUTE_ID) are reported for all columns in the result set.</span></span>  
  
## <a name="sqlgetdescfield-and-table-valued-parameters"></a><span data-ttu-id="fe9fb-109">SQLGetDescField とテーブル値パラメーター</span><span class="sxs-lookup"><span data-stu-id="fe9fb-109">SQLGetDescField and Table-Valued Parameters</span></span>  
 <span data-ttu-id="fe9fb-110">SQLGetDescField を使用して、テーブル値パラメーターおよびテーブル値パラメーターの列の拡張属性の値を取得できます。</span><span class="sxs-lookup"><span data-stu-id="fe9fb-110">SQLGetDescField can be used to get values for extended attributes of table-valued parameters and table-valued parameter columns.</span></span> <span data-ttu-id="fe9fb-111">テーブル値パラメーターの詳細については、「[テーブル値パラメーター &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe9fb-111">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="sqlgetdescfield-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="fe9fb-112">SQLGetDescField による機能強化された日付と時刻のサポート</span><span class="sxs-lookup"><span data-stu-id="fe9fb-112">SQLGetDescField Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="fe9fb-113">新しい日付型または時刻型で使用できる記述子フィールドの詳細については、「[パラメーターと結果のメタデータ](../native-client-odbc-date-time/metadata-parameter-and-result.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe9fb-113">For information about the descriptor fields available with the new date/time types, see [Parameter and Result Metadata](../native-client-odbc-date-time/metadata-parameter-and-result.md).</span></span>  
  
 <span data-ttu-id="fe9fb-114">詳細については、「[日付と時刻の機能強化 &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe9fb-114">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
 <span data-ttu-id="fe9fb-115">以降では [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 、アプリケーションで `SQL_C_SS_TIME2` `time` `SQL_C_SS_TIMESTAMPOFFSET` `datetimeoffset` `SQL_C_BINARY` ODBC 3.8 が使用されている場合、SQLGetDescField はの代わりに (型の場合) または (の場合) を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="fe9fb-115">Beginning in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], SQLGetDescField can return `SQL_C_SS_TIME2` (for `time` types) or `SQL_C_SS_TIMESTAMPOFFSET` (for `datetimeoffset`) instead of `SQL_C_BINARY`, if your application uses ODBC 3.8.</span></span>  
  
## <a name="sqlgetdescfield-support-for-large-clr-udts"></a><span data-ttu-id="fe9fb-116">SQLGetDescField による大きな CLR UDT のサポート</span><span class="sxs-lookup"><span data-stu-id="fe9fb-116">SQLGetDescField Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="fe9fb-117">`SQLGetDescField` は、大きな CLR ユーザー定義型 (UDT) をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="fe9fb-117">`SQLGetDescField` supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="fe9fb-118">詳細については、「[大容量の CLR ユーザー定義型 &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe9fb-118">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="sqlgetdescfield-support-for-sparse-columns"></a><span data-ttu-id="fe9fb-119">SQLGetDescField によるスパース列のサポート</span><span class="sxs-lookup"><span data-stu-id="fe9fb-119">SQLGetDescField Support for Sparse Columns</span></span>  
 <span data-ttu-id="fe9fb-120">SQLGetDescField を使用すると、新しい IRD フィールド SQL_CA_SS_IS_COLUMN_SET に対してクエリを実行し、列が列かどうかを判断でき `column_set` ます。</span><span class="sxs-lookup"><span data-stu-id="fe9fb-120">SQLGetDescField can be used to query the new IRD field SQL_CA_SS_IS_COLUMN_SET to determine if a column is a `column_set` column.</span></span>  
  
 <span data-ttu-id="fe9fb-121">詳細については、「[スパース列のサポート &#40;ODBC&#41;](../native-client/odbc/sparse-columns-support-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe9fb-121">For more information, see [Sparse Columns Support &#40;ODBC&#41;](../native-client/odbc/sparse-columns-support-odbc.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe9fb-122">例</span><span class="sxs-lookup"><span data-stu-id="fe9fb-122">Example</span></span>  
  
```  
typedef struct tagCOMPUTEBYLIST  
    {  
    SQLSMALLINT nBys;  
    SQLSMALLINT aByList[1];  
    } COMPUTEBYLIST;  
typedef COMPUTEBYLIST* PCOMPUTEBYLIST;   
  
SQLHDESC    hIRD;   
SQLINTEGER  cbIRD;   
SQLINTEGER  nSet = 0;   
  
// . . .  
// Execute a statement that contains a COMPUTE clause,  
//  then get the descriptor handle of the IRD and  
//  get some IRD values.  
  
SQLGetStmtAttr(g_hStmt, SQL_ATTR_IMP_ROW_DESC,  
    (SQLPOINTER) &hIRD, sizeof(SQLHDESC), &cbIRD);  
  
// For statement-wide column attributes, any  
//  descriptor record will do. You know that 1 exists,  
//  so use it.  
SQLGetDescField(hIRD, 1, SQL_CA_SS_NUM_COMPUTES,  
    (SQLPOINTER) &nComputes, SQL_IS_INTEGER, &cbIRD);  
  
if (nSet == 0)  
    {  
    SQLINTEGER      nOrderID;  
  
    printf_s("Normal result set.\n");  
  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        SQLGetDescField(hIRD, nCol+1,  
            SQL_CA_SS_COLUMN_ORDER,  
            (SQLPOINTER) &nOrderID, SQL_IS_INTEGER,  
            &cbIRD);  
  
        if (nOrderID != 0)  
            {  
            printf_s("Col in ORDER BY, pos: %ld",  
                nOrderID);  
            }  
            printf_s("\n");  
        }  
  
    printf_s("\n");  
    }  
else  
    {  
    PCOMPUTEBYLIST  pByList;  
    SQLSMALLINT     nBy;  
    SQLINTEGER      nColID;  
  
    printf_s("Computed result set number: %lu\n",  
        nSet);  
  
    SQLGetDescField(hIRD, 1, SQL_CA_SS_COMPUTE_BYLIST,  
        (SQLPOINTER) &pByList, SQL_IS_INTEGER,  
        &cbIRD);  
  
    if (pByList != NULL)  
        {  
        printf_s("Clause ordered by columns: ");  
        for (nBy = 0; nBy < pByList->nBys; )  
            {  
            printf_s("%u", pByList->aByList[nBy]);  
            nBy++;  
  
            if (nBy == pByList->nBys)  
                {  
                printf_s("\n");  
                }  
            else  
                {  
                printf_s(", ");  
                }  
            }  
        }  
    else  
        {  
        printf_s("Compute clause set not ordered.\n");  
        }  
  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        SQLGetDescField(hIRD, nCol+1,  
            SQL_CA_SS_COLUMN_ID, (SQLPOINTER) &nColID,  
            SQL_IS_INTEGER, &cbIRD);  
        printf_s("ColumnID: %lu, nColID);  
        }  
    printf_s("\n");  
    }  
  
if (SQLMoreResults(g_hStmt) == SQL_SUCCESS)  
    {  
    // Determine the result set indicator.  
    SQLGetDescField(hIRD, 1, SQL_CA_SS_COMPUTE_ID,  
        (SQLPOINTER) &nSet, SQL_IS_INTEGER, &cbIRD);  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="fe9fb-123">参照</span><span class="sxs-lookup"><span data-stu-id="fe9fb-123">See Also</span></span>  
 <span data-ttu-id="fe9fb-124">[SQLGetDescField 関数](https://go.microsoft.com/fwlink/?LinkId=59351) </span><span class="sxs-lookup"><span data-stu-id="fe9fb-124">[SQLGetDescField Function](https://go.microsoft.com/fwlink/?LinkId=59351) </span></span>  
 [<span data-ttu-id="fe9fb-125">ODBC API 実装の詳細</span><span class="sxs-lookup"><span data-stu-id="fe9fb-125">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
