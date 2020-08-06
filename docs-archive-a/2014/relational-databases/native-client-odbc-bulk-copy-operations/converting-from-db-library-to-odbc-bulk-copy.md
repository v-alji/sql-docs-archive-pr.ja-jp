---
title: DB-LIBRARY から ODBC への一括コピー |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- converting DB-Library to ODBC bulk copy
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], DB-Library bulk copy
- ODBC, bulk copy operations
- DB-Library bulk copy
ms.assetid: 0bc15bdb-f19f-4537-ac6c-f249f42cf07f
author: rothja
ms.author: jroth
ms.openlocfilehash: 866900606e582f08695fd4695a1098f34fb2b426
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643311"
---
# <a name="converting-from-db-library-to-odbc-bulk-copy"></a><span data-ttu-id="53625-102">DB-Library から ODBC への一括コピーの変換</span><span class="sxs-lookup"><span data-stu-id="53625-102">Converting from DB-Library to ODBC Bulk Copy</span></span>
  <span data-ttu-id="53625-103">Native Client ODBC ドライバーでサポートされている一括コピー関数は DB-LIBRARY の一括コピー関数に似ているため、DB-LIBRARY 一括コピープログラムを ODBC に変換するのは簡単です [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。ただし、次のような例外があります。</span><span class="sxs-lookup"><span data-stu-id="53625-103">Converting a DB-Library bulk copy program to ODBC is easy because the bulk copy functions supported by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver are similar to the DB-Library bulk copy functions, with the following exceptions:</span></span>  
  
-   <span data-ttu-id="53625-104">DB-Library アプリケーションでは、DBPROCESS 構造体を指すポインターを一括コピー関数の最初のパラメーターに渡します。</span><span class="sxs-lookup"><span data-stu-id="53625-104">DB-Library applications pass a pointer to a DBPROCESS structure as the first parameter of bulk copy functions.</span></span> <span data-ttu-id="53625-105">ODBC アプリケーションでは、DBPROCESS ポインターが ODBC 接続ハンドルに置き換わります。</span><span class="sxs-lookup"><span data-stu-id="53625-105">In ODBC applications, the DBPROCESS pointer is replaced with an ODBC connection handle.</span></span>  
  
-   <span data-ttu-id="53625-106">DB-LIBRARY アプリケーションは、接続する前に**BCP_SETL**を呼び出し、DBPROCESS での一括コピー操作を有効にします。</span><span class="sxs-lookup"><span data-stu-id="53625-106">DB-Library applications call **BCP_SETL** before connecting to enable bulk copy operations on a DBPROCESS.</span></span> <span data-ttu-id="53625-107">ODBC アプリケーションでは、接続ハンドルに対して一括操作を有効にするために接続する前に[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="53625-107">ODBC applications instead call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) before connecting to enable bulk operations on a connection handle:</span></span>  
  
    ```  
    SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP,  
        (void *)SQL_BCP_ON, SQL_IS_INTEGER);  
    ```  
  
-   <span data-ttu-id="53625-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーでは、db-library メッセージとエラーハンドラーがサポートされていません。 odbc 一括コピー関数によって発生したエラーとメッセージを取得するには、 **SQLGetDiagRec**を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="53625-108">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver does not support DB-Library message and error handlers; you must call **SQLGetDiagRec** to get errors and messages raised by the ODBC bulk copy functions.</span></span> <span data-ttu-id="53625-109">ODBC バージョンの一括コピー関数は、標準的な一括コピーのリターン コードである SUCCEED または FAILED を返しますが、SQL_SUCCESS や SQL_ERROR など、ODBC 形式のリターン コードを返しません。</span><span class="sxs-lookup"><span data-stu-id="53625-109">The ODBC versions of bulk copy functions return the standard bulk copy return codes of SUCCEED or FAILED, not ODBC-style return codes, such as SQL_SUCCESS or SQL_ERROR.</span></span>  
  
-   <span data-ttu-id="53625-110">DB-LIBRARY [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)の*varlen*パラメーターに指定された値は、ODBC **bcp_bind**の_cbdata_パラメーターとは異なる解釈になります。</span><span class="sxs-lookup"><span data-stu-id="53625-110">The values specified for the DB-Library [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)*varlen* parameter are interpreted differently than the ODBC **bcp_bind**_cbData_ parameter.</span></span>  
  
    |<span data-ttu-id="53625-111">指定された条件</span><span class="sxs-lookup"><span data-stu-id="53625-111">Condition indicated</span></span>|<span data-ttu-id="53625-112">DB-LIBRARY の*varlen*値</span><span class="sxs-lookup"><span data-stu-id="53625-112">DB-Library *varlen* value</span></span>|<span data-ttu-id="53625-113">ODBC *Cbdata*値</span><span class="sxs-lookup"><span data-stu-id="53625-113">ODBC *cbData* value</span></span>|  
    |-------------------------|--------------------------------|-------------------------|  
    |<span data-ttu-id="53625-114">NULL 値が指定された場合</span><span class="sxs-lookup"><span data-stu-id="53625-114">Null values supplied</span></span>|<span data-ttu-id="53625-115">0</span><span class="sxs-lookup"><span data-stu-id="53625-115">0</span></span>|<span data-ttu-id="53625-116">-1 (SQL_NULL_DATA)</span><span class="sxs-lookup"><span data-stu-id="53625-116">-1 (SQL_NULL_DATA)</span></span>|  
    |<span data-ttu-id="53625-117">可変長のデータが指定された場合</span><span class="sxs-lookup"><span data-stu-id="53625-117">Variable data supplied</span></span>|<span data-ttu-id="53625-118">-1</span><span class="sxs-lookup"><span data-stu-id="53625-118">-1</span></span>|<span data-ttu-id="53625-119">-10 (SQL_VARLEN_DATA)</span><span class="sxs-lookup"><span data-stu-id="53625-119">-10 (SQL_VARLEN_DATA)</span></span>|  
    |<span data-ttu-id="53625-120">長さが 0 の文字列またはバイナリ文字列の場合</span><span class="sxs-lookup"><span data-stu-id="53625-120">Zero length character or binary string</span></span>|<span data-ttu-id="53625-121">NA</span><span class="sxs-lookup"><span data-stu-id="53625-121">NA</span></span>|<span data-ttu-id="53625-122">0</span><span class="sxs-lookup"><span data-stu-id="53625-122">0</span></span>|  
  
     <span data-ttu-id="53625-123">DB-LIBRARY では、 *varlen*値-1 は、可変長データが指定されていることを示します。これは、ODBC *CBDATA*で、NULL 値のみが指定されていることを意味します。</span><span class="sxs-lookup"><span data-stu-id="53625-123">In DB-Library, a *varlen* value of -1 indicates that variable length data is being supplied, which in the ODBC *cbData* is interpreted to mean that only NULL values are being supplied.</span></span> <span data-ttu-id="53625-124">DB-LIBRARY のすべての*varlen*仕様 (-1) を SQL_VARLEN_DATA に、および0のすべての*varlen*仕様を SQL_NULL_DATA に変更します。</span><span class="sxs-lookup"><span data-stu-id="53625-124">Change any DB-Library *varlen* specifications of -1 to SQL_VARLEN_DATA and any *varlen* specifications of 0 to SQL_NULL_DATA.</span></span>  
  
-   <span data-ttu-id="53625-125">DB-LIBRARY **bcp \_ colfmt**_file \_ collen_と ODBC [bcp_colfmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md)*cbuserdata*には、上記の**bcp_bind**の_varlen_および*cbdata*パラメーターと同じ問題があります。</span><span class="sxs-lookup"><span data-stu-id="53625-125">The DB-Library **bcp\_colfmt**_file\_collen_ and the ODBC [bcp_colfmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md)*cbUserData* have the same issue as the **bcp_bind**_varlen_ and *cbData* parameters noted above.</span></span> <span data-ttu-id="53625-126">-1 の DB-LIBRARY *file_collen*仕様をすべて SQL_VARLEN_DATA に変更*file_collen*し、0を SQL_NULL_DATA に設定します。</span><span class="sxs-lookup"><span data-stu-id="53625-126">Change any DB-Library *file_collen* specifications of -1 to SQL_VARLEN_DATA and any *file_collen* specifications of 0 to SQL_NULL_DATA.</span></span>  
  
-   <span data-ttu-id="53625-127">ODBC [bcp_control](../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)関数の*ivalue*パラメーターは void ポインターです。</span><span class="sxs-lookup"><span data-stu-id="53625-127">The *iValue* parameter of the ODBC [bcp_control](../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) function is a void pointer.</span></span> <span data-ttu-id="53625-128">DB-LIBRARY では、 *Ivalue*は整数でした。</span><span class="sxs-lookup"><span data-stu-id="53625-128">In DB-Library, *iValue* was an integer.</span></span> <span data-ttu-id="53625-129">ODBC *Ivalue*の値を void \* にキャストします。</span><span class="sxs-lookup"><span data-stu-id="53625-129">Cast the values for the ODBC *iValue* to void \*.</span></span>  
  
-   <span data-ttu-id="53625-130">**Bcp_control**オプション BCPMAXERRS では、一括コピー操作が失敗する前にエラーが発生する個々の行の数を指定します。</span><span class="sxs-lookup"><span data-stu-id="53625-130">The **bcp_control** option BCPMAXERRS specifies how many individual rows can have errors before a bulk copy operation fails.</span></span> <span data-ttu-id="53625-131">BCPMAXERRS の既定値は 0 (最初のエラーの場合は fail) で、ODBC バージョンでは**bcp_control**と10の db-library バージョンでは10です。</span><span class="sxs-lookup"><span data-stu-id="53625-131">The default for BCPMAXERRS is 0 (fail on first error) in the DB-Library version of **bcp_control** and 10 in the ODBC version.</span></span> <span data-ttu-id="53625-132">既定値の0に依存して一括コピー操作を終了する DB-LIBRARY アプリケーションは、BCPMAXERRS を0に設定するために ODBC **bcp_control**を呼び出すように変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="53625-132">DB-Library applications that depend on the default of 0 to terminate a bulk copy operation must be changed to call the ODBC **bcp_control** to set BCPMAXERRS to 0.</span></span>  
  
-   <span data-ttu-id="53625-133">ODBC **bcp_control**関数は、 **bcp_control**の db-library バージョンでサポートされていない次のオプションをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="53625-133">The ODBC **bcp_control** function supports the following options not supported by the DB-Library version of **bcp_control**:</span></span>  
  
    -   <span data-ttu-id="53625-134">BCPODBC</span><span class="sxs-lookup"><span data-stu-id="53625-134">BCPODBC</span></span>  
  
         <span data-ttu-id="53625-135">TRUE に設定すると、文字形式で保存される**datetime**と**smalldatetime**の値に、ODBC タイムスタンプエスケープシーケンスのプレフィックスとサフィックスが含まれるように指定します。</span><span class="sxs-lookup"><span data-stu-id="53625-135">When set to TRUE, specifies that **datetime** and **smalldatetime** values saved in character format will have the ODBC timestamp escape sequence prefix and suffix.</span></span> <span data-ttu-id="53625-136">これは、BCP_OUT 操作に対してのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="53625-136">This only applies to BCP_OUT operations.</span></span>  
  
         <span data-ttu-id="53625-137">BCPODBC.BCP を FALSE に設定すると、文字列に変換される**datetime**値は次のように出力されます。</span><span class="sxs-lookup"><span data-stu-id="53625-137">With BCPODBC set to FALSE, a **datetime** value converted to a character string is output as:</span></span>  
  
        ```  
        1997-01-01 00:00:00.000  
        ```  
  
         <span data-ttu-id="53625-138">BCPODBC.BCP を TRUE に設定すると、同じ**datetime**値が次のように出力されます。</span><span class="sxs-lookup"><span data-stu-id="53625-138">With BCPODBC set to TRUE, the same **datetime** value is output as:</span></span>  
  
        ```  
        {ts '1997-01-01 00:00:00.000' }  
        ```  
  
    -   <span data-ttu-id="53625-139">BCPKEEPIDENTITY</span><span class="sxs-lookup"><span data-stu-id="53625-139">BCPKEEPIDENTITY</span></span>  
  
         <span data-ttu-id="53625-140">TRUE に設定した場合、一括コピー関数で、ID 制約を含む列に対して指定したデータ値が挿入されることを示します。</span><span class="sxs-lookup"><span data-stu-id="53625-140">When set to TRUE, specifies that bulk copy functions insert data values supplied for columns with identity constraints.</span></span> <span data-ttu-id="53625-141">このオプションを設定しないと、挿入される行に対して新しい ID 値が生成されます。</span><span class="sxs-lookup"><span data-stu-id="53625-141">If this is not set, new identity values are generated for the inserted rows.</span></span>  
  
    -   <span data-ttu-id="53625-142">BCPHINTS</span><span class="sxs-lookup"><span data-stu-id="53625-142">BCPHINTS</span></span>  
  
         <span data-ttu-id="53625-143">一括コピーのさまざまな最適化を指定します。</span><span class="sxs-lookup"><span data-stu-id="53625-143">Specifies various bulk copy optimizations.</span></span> <span data-ttu-id="53625-144">このオプションは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 以前のバージョンでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="53625-144">This option cannot be used on 6.5 or earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
    -   <span data-ttu-id="53625-145">BCPFILECP</span><span class="sxs-lookup"><span data-stu-id="53625-145">BCPFILECP</span></span>  
  
         <span data-ttu-id="53625-146">一括コピー ファイルのコード ページを指定します。</span><span class="sxs-lookup"><span data-stu-id="53625-146">Specifies the code page of the bulk copy file.</span></span>  
  
    -   <span data-ttu-id="53625-147">BCPUNICODEFILE</span><span class="sxs-lookup"><span data-stu-id="53625-147">BCPUNICODEFILE</span></span>  
  
         <span data-ttu-id="53625-148">キャラクター モードの一括コピー ファイルが Unicode ファイルであることを指定します。</span><span class="sxs-lookup"><span data-stu-id="53625-148">Specifies that a character mode bulk copy file is a Unicode file.</span></span>  
  
-   <span data-ttu-id="53625-149">Odbc の**bcp_colfmt**関数では、odbc SQLCHAR typedef と競合するため、SQLCHAR の*file_type*インジケーターはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="53625-149">The ODBC **bcp_colfmt** function does not support the *file_type* indicator of SQLCHAR because it conflicts with the ODBC SQLCHAR typedef.</span></span> <span data-ttu-id="53625-150">**Bcp_colfmt**ではなく sqlcharacter を使用してください。</span><span class="sxs-lookup"><span data-stu-id="53625-150">Use SQLCHARACTER instead for **bcp_colfmt**.</span></span>  
  
-   <span data-ttu-id="53625-151">ODBC バージョンの一括コピー関数では、文字列内の**datetime**値と**smalldatetime**値を操作するための形式は、yyyy-mm-dd hh: MM: ss の odbc 形式です。**smalldatetime**の値には、yyyy-mm-dd hh: mm: SS の ODBC 形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="53625-151">In the ODBC versions of bulk copy functions, the format for working with **datetime** and **smalldatetime** values in character strings is the ODBC format of yyyy-mm-dd hh:mm:ss.sss; **smalldatetime** values use the ODBC format of yyyy-mm-dd hh:mm:ss.</span></span>  
  
     <span data-ttu-id="53625-152">DB-LIBRARY バージョンの一括コピー関数では、いくつかの形式を使用して、文字列内の**datetime**値と**smalldatetime**値を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="53625-152">The DB-Library versions of the bulk copy functions accept **datetime** and **smalldatetime** values in character strings using several formats:</span></span>  
  
    -   <span data-ttu-id="53625-153">既定の形式は*mmm dd yyyy hh: mmxx*です。ここで*XX*は、AM または PM です。</span><span class="sxs-lookup"><span data-stu-id="53625-153">The default format is *mmm dd yyyy hh:mmxx* where *xx* is either AM or PM.</span></span>  
  
    -   <span data-ttu-id="53625-154">DB-LIBRARY **dbconvert**関数でサポートされている任意の形式の**datetime**文字列および**smalldatetime**文字列。</span><span class="sxs-lookup"><span data-stu-id="53625-154">**datetime** and **smalldatetime** character strings in any format supported by the DB-Library **dbconvert** function.</span></span>  
  
    -   <span data-ttu-id="53625-155">クライアントネットワークユーティリティの [DB-LIBRARY**オプション**] タブで [**インターナショナル設定を使用する**] チェックボックスをオンにすると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] db-library 一括コピー関数は、クライアントコンピューターのレジストリのロケール設定に定義されている地域の日付形式の日付も受け入れます。</span><span class="sxs-lookup"><span data-stu-id="53625-155">When the **Use international settings** box is checked on the DB-Library **Options** tab of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client Network Utility, the DB-Library bulk copy functions also accept dates in the regional date format defined for the locale setting of the client computer registry.</span></span>  
  
     <span data-ttu-id="53625-156">DB-LIBRARY 一括コピー関数では、ODBC **datetime**および**smalldatetime**形式は使用できません。</span><span class="sxs-lookup"><span data-stu-id="53625-156">The DB-Library bulk copy functions do not accept the ODBC **datetime** and **smalldatetime** formats.</span></span>  
  
     <span data-ttu-id="53625-157">SQL_SOPT_SS_REGIONALIZE ステートメント属性を SQL_RE_ON に設定すると、ODBC の一括コピー関数はクライアント コンピューターのレジストリのロケール設定に定義された地域別の日付形式のデータを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="53625-157">If the SQL_SOPT_SS_REGIONALIZE statement attribute is set to SQL_RE_ON, the ODBC bulk copy functions accept dates in the regional date format defined for the locale setting of the client computer registry.</span></span>  
  
-   <span data-ttu-id="53625-158">文字形式で**通貨**値を出力する場合、ODBC 一括コピー関数では、有効桁数が4桁、コンマ区切り文字が指定されません。DB-LIBRARY バージョンでは、2桁の有効桁数が指定され、コンマ区切り記号が含まれます。</span><span class="sxs-lookup"><span data-stu-id="53625-158">When outputting **money** values in character format, ODBC bulk copy functions supply four digits of precision and no comma separators; DB-Library versions only supply two digits of precision and include the comma separators.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53625-159">参照</span><span class="sxs-lookup"><span data-stu-id="53625-159">See Also</span></span>  
 <span data-ttu-id="53625-160">[ODBC&#41;&#40;の一括コピー操作の実行](performing-bulk-copy-operations-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="53625-160">[Performing Bulk Copy Operations &#40;ODBC&#41;](performing-bulk-copy-operations-odbc.md) </span></span>  
 [<span data-ttu-id="53625-161">一括コピー関数</span><span class="sxs-lookup"><span data-stu-id="53625-161">Bulk Copy Functions</span></span>](../native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
