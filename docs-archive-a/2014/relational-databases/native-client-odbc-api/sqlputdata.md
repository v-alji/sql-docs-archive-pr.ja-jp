---
title: SQLPutData |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLPutData function
ms.assetid: d39aaa5b-7fbc-4315-a7f2-5a7787e04f25
author: rothja
ms.author: jroth
ms.openlocfilehash: 31da9c21f9e4323a492a25629a979c66a4f7d365
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645021"
---
# <a name="sqlputdata"></a><span data-ttu-id="41616-102">SQLPutData</span><span class="sxs-lookup"><span data-stu-id="41616-102">SQLPutData</span></span>
  <span data-ttu-id="41616-103">SQLPutData を使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL_LONGVARCHAR ( `text` )、SQL_WLONGVARCHAR ( `ntext` )、または SQL_LONGVARBINARY () 列に対して65535バイトを超えるデータ 400 (SQL Server バージョン6.0 以降) を送信する場合は、次の制限が適用され `image` ます。</span><span class="sxs-lookup"><span data-stu-id="41616-103">The following restrictions apply when using SQLPutData to send more than 65,535 bytes of data (for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 4.21a) or 400 KB of data (for SQL Server version 6.0 and later) for a SQL_LONGVARCHAR (`text`), SQL_WLONGVARCHAR (`ntext`) or SQL_LONGVARBINARY (`image`) column:</span></span>  
  
-   <span data-ttu-id="41616-104">参照されるパラメーターには、INSERT ステートメント内の*insert_value*を指定できます。</span><span class="sxs-lookup"><span data-stu-id="41616-104">The referenced parameter can be the *insert_value* in an INSERT statement.</span></span>  
  
-   <span data-ttu-id="41616-105">参照されるパラメーターは、UPDATE ステートメントの SET 句の*式*にすることができます。</span><span class="sxs-lookup"><span data-stu-id="41616-105">The referenced parameter can be an *expression* in the SET clause of an UPDATE statement.</span></span>  
  
 <span data-ttu-id="41616-106">を実行しているサーバーにブロック内のデータを提供する SQLPutData 呼び出しのシーケンスをキャンセルすると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バージョン6.5 以前を使用しているときに列の値が部分的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="41616-106">Canceling a sequence of SQLPutData calls that provide data in blocks to a server running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] causes a partial update of the column's value when using version 6.5 or earlier.</span></span> <span data-ttu-id="41616-107">`text` `ntext` SQLCancel が呼び出されたときに参照された、、または `image` 列は、中間プレースホルダー値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="41616-107">The `text`, `ntext`, or `image` column that was referenced when SQLCancel was called is set to an intermediate placeholder value.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="41616-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 以前のバージョンへの接続をサポートしません。</span><span class="sxs-lookup"><span data-stu-id="41616-108">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver does not support connecting to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 6.5 and earlier.</span></span>  
  
## <a name="diagnostics"></a><span data-ttu-id="41616-109">診断</span><span class="sxs-lookup"><span data-stu-id="41616-109">Diagnostics</span></span>  
 <span data-ttu-id="41616-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SQLPutData には、Native Client 固有の SQLSTATE が1つあります。</span><span class="sxs-lookup"><span data-stu-id="41616-110">There is one [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client specific SQLSTATE for SQLPutData:</span></span>  
  
|<span data-ttu-id="41616-111">SQLSTATE</span><span class="sxs-lookup"><span data-stu-id="41616-111">SQLSTATE</span></span>|<span data-ttu-id="41616-112">エラー</span><span class="sxs-lookup"><span data-stu-id="41616-112">Error</span></span>|<span data-ttu-id="41616-113">説明</span><span class="sxs-lookup"><span data-stu-id="41616-113">Description</span></span>|  
|--------------|-----------|-----------------|  
|<span data-ttu-id="41616-114">22026</span><span class="sxs-lookup"><span data-stu-id="41616-114">22026</span></span>|<span data-ttu-id="41616-115">文字列データの長さが合致しません</span><span class="sxs-lookup"><span data-stu-id="41616-115">String data, length mismatch</span></span>|<span data-ttu-id="41616-116">たとえば SQL_LEN_DATA_AT_EXEC (*n*) を使用して、送信されるデータの長さ (バイト単位) がアプリケーションによって指定されている場合 ( *n*が0を超える場合)、sqlputdata を使用してアプリケーションで指定されたバイト数の合計が、指定された長さと一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="41616-116">If the length of data in bytes to be sent has been specified by an application, for example, with SQL_LEN_DATA_AT_EXEC(*n*) where *n* is greater than 0, the total number of bytes given by the application via SQLPutData must match the specified length.</span></span>|  
  
## <a name="sqlputdata-and-table-valued-parameters"></a><span data-ttu-id="41616-117">SQLPutData とテーブル値パラメーター</span><span class="sxs-lookup"><span data-stu-id="41616-117">SQLPutData and Table-Valued Parameters</span></span>  
 <span data-ttu-id="41616-118">SQLPutData は、テーブル値パラメーターとの変数行バインドを使用する場合に、アプリケーションによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="41616-118">SQLPutData is used by an application when using variable row binding with table-valued parameters.</span></span> <span data-ttu-id="41616-119">*StrLen_Or_Ind*パラメーターは、ドライバーがテーブル値パラメーターデータの次の行または行のデータを収集できる状態であること、または使用可能な行がないことを示します。</span><span class="sxs-lookup"><span data-stu-id="41616-119">The *StrLen_Or_Ind* parameter indicates that it is ready for the driver to collect data for the next row or rows of table-valued parameter data, or that no more rows are available:</span></span>  
  
-   <span data-ttu-id="41616-120">値が 0 を超える場合は、次の行の値のセットを使用できることを示します。</span><span class="sxs-lookup"><span data-stu-id="41616-120">A value greater than 0 indicates that the next set of row values is available.</span></span>  
  
-   <span data-ttu-id="41616-121">値が 0 の場合は、送信される行がなくなったことを示します。</span><span class="sxs-lookup"><span data-stu-id="41616-121">A value of 0 indicates that there are no more rows to be sent.</span></span>  
  
-   <span data-ttu-id="41616-122">値が 0 未満の場合は、エラーが発生し、"文字列長またはバッファー長が正しくありません" というメッセージで SQLState HY090 の診断レコードが記録されます。</span><span class="sxs-lookup"><span data-stu-id="41616-122">Any value less than 0 is an error and results in a diagnostic record being logged with SQLState HY090 and the messaage "Invalid string or buffer length".</span></span>  
  
 <span data-ttu-id="41616-123">*DataPtr*パラメーターは無視されますが、NULL 以外の値に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="41616-123">The *DataPtr* parameter is ignored, but must be set to a non-NULL value.</span></span> <span data-ttu-id="41616-124">詳細については、「バインド」の「変数 TVP 行バインド」[と「テーブル値パラメーターと列の値のデータ転送](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="41616-124">For more information, see the section on Variable TVP row binding in [Binding and Data Transfer of Table-Valued Parameters and Column Values](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).</span></span>  
  
 <span data-ttu-id="41616-125">*StrLen_Or_Ind*に SQL_DEFAULT_PARAM 以外の値または0と SQL_PARAMSET_SIZE (つまり、SQLBindParameter の*columnsize*パラメーター) の数値が含まれている場合、エラーになります。</span><span class="sxs-lookup"><span data-stu-id="41616-125">If *StrLen_Or_Ind* has any value other than SQL_DEFAULT_PARAM or a number between 0 and the SQL_PARAMSET_SIZE (that is, the *ColumnSize* parameter of SQLBindParameter), it is an error.</span></span> <span data-ttu-id="41616-126">このエラーが発生すると、SQLPutData は、"文字列長またはバッファー長が正しくありません" というメッセージで SQLSTATE=HY090 の SQL_ERROR を返します。</span><span class="sxs-lookup"><span data-stu-id="41616-126">This error causes SQLPutData to return SQL_ERROR: SQLSTATE=HY090, "Invalid string or buffer length".</span></span>  
  
 <span data-ttu-id="41616-127">テーブル値パラメーターの詳細については、「[テーブル値パラメーター &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="41616-127">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="sqlputdata-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="41616-128">SQLPutData による機能強化された日付と時刻のサポート</span><span class="sxs-lookup"><span data-stu-id="41616-128">SQLPutData Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="41616-129">日付型または時刻型のパラメーター値は、「 [C から SQL への変換](../native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md)」で説明されているように変換されます。</span><span class="sxs-lookup"><span data-stu-id="41616-129">Parameter values of date/time types are converted as described in [Conversions from C to SQL](../native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md).</span></span>  
  
 <span data-ttu-id="41616-130">詳細については、「[日付と時刻の機能強化 &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="41616-130">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlputdata-support-for-large-clr-udts"></a><span data-ttu-id="41616-131">SQLPutData による大きな CLR UDT のサポート</span><span class="sxs-lookup"><span data-stu-id="41616-131">SQLPutData Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="41616-132">`SQLPutData` は、大きな CLR ユーザー定義型 (UDT) をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="41616-132">`SQLPutData` supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="41616-133">詳細については、「[大容量の CLR ユーザー定義型 &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="41616-133">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41616-134">参照</span><span class="sxs-lookup"><span data-stu-id="41616-134">See Also</span></span>  
 <span data-ttu-id="41616-135">[SQLPutData 関数](https://go.microsoft.com/fwlink/?LinkId=59365) </span><span class="sxs-lookup"><span data-stu-id="41616-135">[SQLPutData Function](https://go.microsoft.com/fwlink/?LinkId=59365) </span></span>  
 [<span data-ttu-id="41616-136">ODBC API 実装の詳細</span><span class="sxs-lookup"><span data-stu-id="41616-136">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
