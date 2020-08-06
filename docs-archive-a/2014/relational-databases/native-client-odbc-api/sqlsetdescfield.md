---
title: SQLSetDescField |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetDescField function
ms.assetid: de4bed15-15be-4825-994c-1046255e725a
author: rothja
ms.author: jroth
ms.openlocfilehash: 1b8290fd90c0c9bb91f08d94e119689d38fbc04e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645008"
---
# <a name="sqlsetdescfield"></a><span data-ttu-id="b7fe0-102">SQLSetDescField</span><span class="sxs-lookup"><span data-stu-id="b7fe0-102">SQLSetDescField</span></span>
  <span data-ttu-id="b7fe0-103">SQLSetDescField を使用すると、テーブル値パラメーターおよびテーブル値パラメーター列の記述子フィールドを設定できます。</span><span class="sxs-lookup"><span data-stu-id="b7fe0-103">SQLSetDescField can be used to set descriptor fields for table-valued parameters and table-valued parameter columns.</span></span> <span data-ttu-id="b7fe0-104">使用可能なフィールドの詳細については、「テーブル[値パラメーターの構成列の](../native-client-odbc-table-valued-parameters/descriptor-fields-for-table-valued-parameter-constituent-columns.md)[テーブル値パラメーターの記述子フィールド](../native-client-odbc-table-valued-parameters/table-valued-parameter-descriptor-fields.md)と記述子フィールド」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7fe0-104">For information about the available fields, see [Table-Valued Parameter Descriptor Fields](../native-client-odbc-table-valued-parameters/table-valued-parameter-descriptor-fields.md) and [Descriptor Fields for Table-Valued Parameter Constituent Columns](../native-client-odbc-table-valued-parameters/descriptor-fields-for-table-valued-parameter-constituent-columns.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7fe0-105">解説</span><span class="sxs-lookup"><span data-stu-id="b7fe0-105">Remarks</span></span>  
 <span data-ttu-id="b7fe0-106">テーブル値パラメーター列は、記述子のヘッダー フィールド SQL_SOPT_SS_PARAM_FOCUS に、SQL_DESC_TYPE が SQL_SS_TABLE に設定されているレコードの序数が設定される場合のみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="b7fe0-106">Table-valued parameter columns are only available when the descriptor header field SQL_SOPT_SS_PARAM_FOCUS is set to the ordinal of a record that has SQL_DESC_TYPE set to SQL_SS_TABLE.</span></span> <span data-ttu-id="b7fe0-107">SQL_SOPT_SS_PARAM_FOCUS の詳細については、「 [SQLSetStmtAttr](sqlsetstmtattr.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7fe0-107">For more information about SQL_SOPT_SS_PARAM_FOCUS, see [SQLSetStmtAttr](sqlsetstmtattr.md).</span></span>  
  
 <span data-ttu-id="b7fe0-108">SQL_SOPT_SS_PARAM_FOCUS をテーブル値パラメーターではないパラメーターの序数に設定しようとした場合、SQLSetStmtAttr は SQL_ERROR を返し、"属性値が無効です" というメッセージで SQLSTATE = HY024 の診断レコードが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b7fe0-108">If an attempt is made to set SQL_SOPT_SS_PARAM_FOCUS to the ordinal of a parameter that is not a table-valued parameter, SQLSetStmtAttr returns SQL_ERROR, and a diagnostic record is created with SQLSTATE = HY024 and the message "Invalid attribute value".</span></span> <span data-ttu-id="b7fe0-109">SQL_SOPT_SS_PARAM_FOCUS は、SQL_ERROR が返されたときに変更されません。</span><span class="sxs-lookup"><span data-stu-id="b7fe0-109">SQL_SOPT_SS_PARAM_FOCUS is not changed when SQL_ERROR is returned.</span></span>  
  
 <span data-ttu-id="b7fe0-110">SQL_SOPT_SS_PARAM_FOCUS に 0 を設定すると、パラメーターの記述子レコードへのアクセスが復元されます。</span><span class="sxs-lookup"><span data-stu-id="b7fe0-110">Setting SQL_SOPT_SS_PARAM_FOCUS to 0 restores access to descriptor records for parameters.</span></span>  
  
 <span data-ttu-id="b7fe0-111">テーブル値パラメーターの詳細については、「[テーブル値パラメーター &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7fe0-111">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="sqlsetdescfield-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="b7fe0-112">SQLSetDescField による機能強化された日付と時刻のサポート</span><span class="sxs-lookup"><span data-stu-id="b7fe0-112">SQLSetDescField Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="b7fe0-113">ODBC では、日付と時刻の機能が強化されました。</span><span class="sxs-lookup"><span data-stu-id="b7fe0-113">Date/time features have been enhanced in ODBC.</span></span> <span data-ttu-id="b7fe0-114">新しい日付型または時刻型に対して提供される記述子フィールドの詳細については、「[パラメーターと結果のメタデータ](../native-client-odbc-date-time/metadata-parameter-and-result.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7fe0-114">For information about the descriptor field provided for the new date/time types, see [Parameter and Result Metadata](../native-client-odbc-date-time/metadata-parameter-and-result.md).</span></span>  
  
 <span data-ttu-id="b7fe0-115">詳細については、「[日付と時刻の機能強化 &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7fe0-115">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlsetdescfield-support-for-large-clr-udts"></a><span data-ttu-id="b7fe0-116">SQLSetDescField による大きな CLR UDT のサポート</span><span class="sxs-lookup"><span data-stu-id="b7fe0-116">SQLSetDescField Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="b7fe0-117">SQLSetDescField は、大きな CLR ユーザー定義型 (Udt) をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="b7fe0-117">SQLSetDescField supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="b7fe0-118">詳細については、「[大容量の CLR ユーザー定義型 &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7fe0-118">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="sqlsetdescfield-support-for-sparse-columns"></a><span data-ttu-id="b7fe0-119">SQLSetDescField によるスパース列のサポート</span><span class="sxs-lookup"><span data-stu-id="b7fe0-119">SQLSetDescField Support for Sparse Columns</span></span>  
 <span data-ttu-id="b7fe0-120">SQLSetDecField を使用して、アプリケーションパラメーター記述子 (APD) の SQL_SOPT_SS_NAME_SCOPE を SQL_SS_NAME_SCOPE_EXTENDED と SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET の値に設定できます。</span><span class="sxs-lookup"><span data-stu-id="b7fe0-120">SQLSetDecField can be used to set SQL_SOPT_SS_NAME_SCOPE in the application parameter descriptor (APD) to the values SQL_SS_NAME_SCOPE_EXTENDED and SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET.</span></span>  
  
 <span data-ttu-id="b7fe0-121">詳細については、「[スパース列のサポート &#40;ODBC&#41;](../native-client/odbc/sparse-columns-support-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7fe0-121">For more information, see [Sparse Columns Support &#40;ODBC&#41;](../native-client/odbc/sparse-columns-support-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7fe0-122">参照</span><span class="sxs-lookup"><span data-stu-id="b7fe0-122">See Also</span></span>  
 <span data-ttu-id="b7fe0-123">[SQLSetDescField](https://go.microsoft.com/fwlink/?LinkId=80705) </span><span class="sxs-lookup"><span data-stu-id="b7fe0-123">[SQLSetDescField](https://go.microsoft.com/fwlink/?LinkId=80705) </span></span>  
 [<span data-ttu-id="b7fe0-124">ODBC API 実装の詳細</span><span class="sxs-lookup"><span data-stu-id="b7fe0-124">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
