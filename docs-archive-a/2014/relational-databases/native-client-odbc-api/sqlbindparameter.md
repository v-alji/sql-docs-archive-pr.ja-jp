---
title: SQLBindParameter |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLBindParameter function
ms.assetid: c302c87a-e7f4-4d2b-a0a7-de42210174ac
author: rothja
ms.author: jroth
ms.openlocfilehash: 6e50886457c4c20110880cc5b75ec594fd3eaba5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645040"
---
# <a name="sqlbindparameter"></a><span data-ttu-id="0f040-102">SQLBindParameter</span><span class="sxs-lookup"><span data-stu-id="0f040-102">SQLBindParameter</span></span>
  <span data-ttu-id="0f040-103">`SQLBindParameter`を使用すると、Native Client ODBC ドライバーにデータを提供するときに、データ変換の負担をなくすことができます。これにより、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アプリケーションのクライアントコンポーネントとサーバーコンポーネントの両方でパフォーマンスを大幅に向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="0f040-103">`SQLBindParameter` can eliminate the burden of data conversion when used to provide data for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver, resulting in significant performance gains for both the client and server components of applications.</span></span> <span data-ttu-id="0f040-104">その他に、概数データ型を挿入または更新するときに有効桁数を失うことが少なくなるという利点もあります。</span><span class="sxs-lookup"><span data-stu-id="0f040-104">Other benefits include reduced loss of precision when inserting or updating approximate numeric data types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0f040-105">`char` 型と `wchar` 型のデータを image 型の列に挿入するときは、バイナリ形式に変換後のデータのサイズではなく、渡すデータのサイズを使用します。</span><span class="sxs-lookup"><span data-stu-id="0f040-105">When inserting `char` and `wchar` type data into an image column, the size of the data being passed in is used, as opposed to the size of the data after conversion to a binary format.</span></span>  
  
 <span data-ttu-id="0f040-106">パラメーター配列の配列要素の 1 つで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバー エラーが発生しても、残りの配列要素に対しては引き続きステートメントが実行されます。</span><span class="sxs-lookup"><span data-stu-id="0f040-106">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver encounters an error on a single array element of an array of parameters, the driver continues to execute the statement for the remaining array elements.</span></span> <span data-ttu-id="0f040-107">アプリケーションがこのステートメントのパラメーター状態要素の配列をバインドした場合は、その配列を基にして、エラーが発生したパラメーター行を特定できます。</span><span class="sxs-lookup"><span data-stu-id="0f040-107">If the application has bound an array of parameter status elements for the statement, the rows of parameters generating errors can be determined from the array.</span></span>  
  
 <span data-ttu-id="0f040-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーを使用する場合は、入力パラメーターのバインド時に SQL_PARAM_INPUT を指定します。</span><span class="sxs-lookup"><span data-stu-id="0f040-108">When using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver, specify SQL_PARAM_INPUT when binding input parameters.</span></span> <span data-ttu-id="0f040-109">OUTPUT キーワードで定義されたストアド プロシージャ パラメーターをバインドするときは、SQL_PARAM_OUTPUT または SQL_PARAM_INPUT_OUTPUT のみを指定してください。</span><span class="sxs-lookup"><span data-stu-id="0f040-109">Only specify SQL_PARAM_OUTPUT or SQL_PARAM_INPUT_OUTPUT when binding stored procedure parameters defined with the OUTPUT keyword.</span></span>  
  
 <span data-ttu-id="0f040-110">[SQLRowCount](sqlrowcount.md)は、バインドされた [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パラメーター配列の配列要素によってステートメントの実行でエラーが発生した場合に、Native Client ODBC ドライバーと互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="0f040-110">[SQLRowCount](sqlrowcount.md) is unreliable with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver if an array element of a bound-parameter array causes an error in statement execution.</span></span> <span data-ttu-id="0f040-111">また、ODBC ステートメント属性 SQL_ATTR_PARAMS_PROCESSED_PTR は、エラーが発生する前に処理された行数を報告します。</span><span class="sxs-lookup"><span data-stu-id="0f040-111">The ODBC statement attribute SQL_ATTR_PARAMS_PROCESSED_PTR reports the number of rows processed before the error occurs.</span></span> <span data-ttu-id="0f040-112">その後、必要に応じてパラメーター状態配列全体をアプリケーションで調査することにより、正常に実行されたステートメント数を検出できます。</span><span class="sxs-lookup"><span data-stu-id="0f040-112">The application can then traverse its parameter status array to discover the number of statements successfully executed, if necessary.</span></span>  
  
## <a name="binding-parameters-for-sql-character-types"></a><span data-ttu-id="0f040-113">SQL 文字型のパラメーターのバインド</span><span class="sxs-lookup"><span data-stu-id="0f040-113">Binding Parameters for SQL Character Types</span></span>  
 <span data-ttu-id="0f040-114">渡された SQL データ型が文字型の場合、 *Columnsize*は文字数 (バイト数ではない) のサイズになります。</span><span class="sxs-lookup"><span data-stu-id="0f040-114">If the SQL data type passed in is a character type, *ColumnSize* is the size in characters (not bytes).</span></span> <span data-ttu-id="0f040-115">データ文字列の長さが8000を超える場合、 *Columnsize*をに設定する必要があり `SQL_SS_LENGTH_UNLIMITED` ます。これは、SQL 型のサイズに制限がないことを示します。</span><span class="sxs-lookup"><span data-stu-id="0f040-115">If the length of the data string in bytes is greater than 8000, *ColumnSize* should be set to `SQL_SS_LENGTH_UNLIMITED`, indicating that there is no limit to the size of the SQL type.</span></span>  
  
 <span data-ttu-id="0f040-116">たとえば、SQL データ型がの場合、 `SQL_WVARCHAR` *columnsize*を4000より大きくすることはできません。</span><span class="sxs-lookup"><span data-stu-id="0f040-116">For instance, if the SQL data type is `SQL_WVARCHAR`, *ColumnSize* should not be greater than 4000.</span></span> <span data-ttu-id="0f040-117">実際のデータの長さが4000より大きい場合は*ColumnSize* 、 `SQL_SS_LENGTH_UNLIMITED` `nvarchar(max)` ドライバーによって使用されるように columnsize をに設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0f040-117">If the actual data length is greater than 4000, then *ColumnSize* should be set to `SQL_SS_LENGTH_UNLIMITED` so that `nvarchar(max)` will be used by driver.</span></span>  
  
## <a name="sqlbindparameter-and-table-valued-parameters"></a><span data-ttu-id="0f040-118">SQLBindParameter とテーブル値パラメーター</span><span class="sxs-lookup"><span data-stu-id="0f040-118">SQLBindParameter and Table-Valued Parameters</span></span>  
 <span data-ttu-id="0f040-119">他のパラメーターの型と同様に、テーブル値パラメーターは SQLBindParameter によってバインドされます。</span><span class="sxs-lookup"><span data-stu-id="0f040-119">Like other parameter types, table-valued parameters are bound by SQLBindParameter.</span></span>  
  
 <span data-ttu-id="0f040-120">テーブル値パラメーターがバインドされた後、そのパラメーターの列もバインドされます。</span><span class="sxs-lookup"><span data-stu-id="0f040-120">After a table-valued parameter has been bound, its columns are also bound.</span></span> <span data-ttu-id="0f040-121">列をバインドするには、 [SQLSetStmtAttr](sqlsetstmtattr.md)を呼び出して、テーブル値パラメーターの序数に SQL_SOPT_SS_PARAM_FOCUS を設定します。</span><span class="sxs-lookup"><span data-stu-id="0f040-121">To bind the columns, you call [SQLSetStmtAttr](sqlsetstmtattr.md) to set SQL_SOPT_SS_PARAM_FOCUS to the ordinal of the table-valued parameter.</span></span> <span data-ttu-id="0f040-122">次に、テーブル値パラメーターの各列に対して SQLBindParameter を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0f040-122">Then, call SQLBindParameter for each column in the table-valued parameter.</span></span> <span data-ttu-id="0f040-123">最上位パラメーター バインドに戻るには、SQL_SOPT_SS_PARAM_FOCUS に 0 を設定します。</span><span class="sxs-lookup"><span data-stu-id="0f040-123">To return to the top-level parameter bindings, set SQL_SOPT_SS_PARAM_FOCUS to 0.</span></span>  
  
 <span data-ttu-id="0f040-124">テーブル値パラメーターの記述子フィールドへのパラメーターのマッピングの詳細については、「[テーブル値パラメーターと列の値のバインドとデータ転送](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f040-124">For information about mapping parameters to descriptor fields for table-valued parameters, see [Binding and Data Transfer of Table-Valued Parameters and Column Values](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).</span></span>  
  
 <span data-ttu-id="0f040-125">テーブル値パラメーターの詳細については、「[テーブル値パラメーター &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f040-125">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="sqlbindparameter-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="0f040-126">SQLBindParameter による機能強化された日付と時刻のサポート</span><span class="sxs-lookup"><span data-stu-id="0f040-126">SQLBindParameter Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="0f040-127">日付型または時刻型のパラメーター値は、「 [C から SQL への変換](../native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md)」で説明されているように変換されます。</span><span class="sxs-lookup"><span data-stu-id="0f040-127">Parameter values of date/time types are converted as described in [Conversions from C to SQL](../native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md).</span></span> <span data-ttu-id="0f040-128">型および型のパラメーター `time` に `datetimeoffset` は、 *ValueType*をとして指定する `SQL_C_DEFAULT` か、 `SQL_C_BINARY` 対応する構造 ( `SQL_SS_TIME2_STRUCT` および `SQL_SS_TIMESTAMPOFFSET_STRUCT` ) が使用されている必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0f040-128">Note that parameters of type `time` and `datetimeoffset` must have *ValueType* specified as `SQL_C_DEFAULT` or `SQL_C_BINARY` if their corresponding structures (`SQL_SS_TIME2_STRUCT` and `SQL_SS_TIMESTAMPOFFSET_STRUCT`) are used.</span></span>  
  
 <span data-ttu-id="0f040-129">詳細については、「[日付と時刻の機能強化 &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f040-129">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlbindparameter-support-for-large-clr-udts"></a><span data-ttu-id="0f040-130">SQLBindParameter による大きな CLR UDT のサポート</span><span class="sxs-lookup"><span data-stu-id="0f040-130">SQLBindParameter Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="0f040-131">`SQLBindParameter` は、大きな CLR ユーザー定義型 (UDT) をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="0f040-131">`SQLBindParameter` supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="0f040-132">詳細については、「[大容量の CLR ユーザー定義型 &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f040-132">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f040-133">参照</span><span class="sxs-lookup"><span data-stu-id="0f040-133">See Also</span></span>  
 <span data-ttu-id="0f040-134">[ODBC API の実装の詳細](odbc-api-implementation-details.md) </span><span class="sxs-lookup"><span data-stu-id="0f040-134">[ODBC API Implementation Details](odbc-api-implementation-details.md) </span></span>  
 [<span data-ttu-id="0f040-135">SQLBindParameter 関数</span><span class="sxs-lookup"><span data-stu-id="0f040-135">SQLBindParameter Function</span></span>](https://go.microsoft.com/fwlink/?LinkId=59328)  
  
  
