---
title: 文字変換を処理するときの ODBC ドライバーの動作の変更 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 682a232a-bf89-4849-88a1-95b2fbac1467
author: rothja
ms.author: jroth
ms.openlocfilehash: 5334b4268559ba155a53b3be655d87f7867779df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714265"
---
# <a name="odbc-driver-behavior-change-when-handling-character-conversions"></a><span data-ttu-id="de072-102">文字変換処理での ODBC ドライバーの動作の変更</span><span class="sxs-lookup"><span data-stu-id="de072-102">ODBC Driver Behavior Change When Handling Character Conversions</span></span>
  <span data-ttu-id="de072-103">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]Native CLIENT ODBC ドライバー (SQLNCLI11.dll) では、SQL_WCHAR \* (NCHAR/nvarchar/nvarchar (max)) と SQL_CHAR \* (CHAR/VARCHAR/NARCHAR (max)) 変換の動作が変更されました。</span><span class="sxs-lookup"><span data-stu-id="de072-103">The [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client ODBC Driver (SQLNCLI11.dll) changed how it does of SQL_WCHAR\* (NCHAR/NVARCHAR/NVARCHAR(MAX)) and SQL_CHAR\* (CHAR/VARCHAR/NARCHAR(MAX)) conversions.</span></span> <span data-ttu-id="de072-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2012 Native Client ODBC ドライバーを使用する場合、SQLGetData、SQLBindCol、SQLBindParameter などの ODBC 関数では長さまたはインジケーターのパラメーターとして (-4) SQL_NO_TOTAL が返されます。</span><span class="sxs-lookup"><span data-stu-id="de072-104">ODBC functions, such as SQLGetData, SQLBindCol, SQLBindParameter, return (-4) SQL_NO_TOTAL as the length/indicator parameter when using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2012 Native Client ODBC driver.</span></span> <span data-ttu-id="de072-105">以前のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは長さの値が返されましたが、これは誤りである可能性があります。</span><span class="sxs-lookup"><span data-stu-id="de072-105">Prior versions of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver returned a length value, which can be incorrect.</span></span>  
  
## <a name="sqlgetdata-behavior"></a><span data-ttu-id="de072-106">SQLGetData の動作</span><span class="sxs-lookup"><span data-stu-id="de072-106">SQLGetData Behavior</span></span>  
 <span data-ttu-id="de072-107">多くの Windows 関数ではバッファー サイズに 0 を指定できます。返される長さは、返されるデータのサイズです。</span><span class="sxs-lookup"><span data-stu-id="de072-107">Many Windows functions let you specify a buffer size of 0 and the returned length is the size of the returned data.</span></span> <span data-ttu-id="de072-108">以下は、Windows プログラミングで一般的なパターンです。</span><span class="sxs-lookup"><span data-stu-id="de072-108">The following pattern is common for Windows programmers:</span></span>  
  
```  
int iSize = 0;  
BYTE * pBuffer = NULL;  
GetMyFavoriteAPI(pBuffer, &iSize);   // Returns needed size in iSize  
pBuffer = new BYTE[iSize];   // Allocate buffer   
GetMyFavoriteAPI(pBuffer, &iSize);   // Retrieve actual data  
```  
  
 <span data-ttu-id="de072-109">ただし、このシナリオでは**SQLGetData**を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="de072-109">However, **SQLGetData** should not be used in this scenario.</span></span> <span data-ttu-id="de072-110">次のパターンは使用できません。</span><span class="sxs-lookup"><span data-stu-id="de072-110">The following pattern should not be used:</span></span>  
  
```  
// bad  
int iSize = 0;  
WCHAR * pBuffer = NULL;  
SQLGetData(hstmt, SQL_W_CHAR, ...., (SQLPOINTER*)0x1, 0, &iSize);   // Get storage size needed  
pBuffer = new WCHAR[(iSize/sizeof(WCHAR)) + 1];   // Allocate buffer  
SQLGetData(hstmt, SQL_W_CHAR, ...., (SQLPOINTER*)pBuffer, iSize, &iSize);   // Retrieve data  
```  
  
 <span data-ttu-id="de072-111">**SQLGetData**は、実際のデータのチャンクを取得するためにのみ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="de072-111">**SQLGetData** can only be called to retrieve chunks of actual data.</span></span> <span data-ttu-id="de072-112">**SQLGetData**を使用してデータのサイズを取得することはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="de072-112">Using **SQLGetData** to get the size of data is not unsupported.</span></span>  
  
 <span data-ttu-id="de072-113">次に、不適切なパターンを使用した場合のドライバーの変更による影響を示します。</span><span class="sxs-lookup"><span data-stu-id="de072-113">The following shows the impact of the driver change when you use the incorrect pattern.</span></span> <span data-ttu-id="de072-114">このアプリケーションでは `varchar` 列およびバインドを Unicode (SQL_UNICODE/SQL_WCHAR) としてクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="de072-114">This application queries a `varchar` column and binding as Unicode (SQL_UNICODE/SQL_WCHAR):</span></span>  
  
 <span data-ttu-id="de072-115">照会`select convert(varchar(36), '123')`</span><span class="sxs-lookup"><span data-stu-id="de072-115">Query:  `select convert(varchar(36), '123')`</span></span>  
  
```  
SQLGetData(hstmt, SQL_WCHAR, ....., (SQLPOINTER*) 0x1, 0 , &iSize);   // Attempting to determine storage size needed  
```  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="de072-116">Native Client ODBC ドライバーのバージョン</span><span class="sxs-lookup"><span data-stu-id="de072-116">Native Client ODBC Driver version</span></span>|<span data-ttu-id="de072-117">長さまたはインジケーターの結果</span><span class="sxs-lookup"><span data-stu-id="de072-117">Length or Indicator Outcome</span></span>|<span data-ttu-id="de072-118">説明</span><span class="sxs-lookup"><span data-stu-id="de072-118">Description</span></span>|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] <span data-ttu-id="de072-119">Native Client 以前</span><span class="sxs-lookup"><span data-stu-id="de072-119">Native Client or earlier</span></span>|<span data-ttu-id="de072-120">6</span><span class="sxs-lookup"><span data-stu-id="de072-120">6</span></span>|<span data-ttu-id="de072-121">ドライバーには、CHAR から WCHAR への変換が長さ \* 2 として実行できるという誤った想定がありました。</span><span class="sxs-lookup"><span data-stu-id="de072-121">The driver incorrectly assumed that converting CHAR to WCHAR could be accomplished as length \* 2.</span></span>|  
|[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] <span data-ttu-id="de072-122">Native Client (Version 11.0.2100.60) 以降</span><span class="sxs-lookup"><span data-stu-id="de072-122">Native Client (version 11.0.2100.60) or later</span></span>|<span data-ttu-id="de072-123">-4 (SQL_NO_TOTAL)</span><span class="sxs-lookup"><span data-stu-id="de072-123">-4 (SQL_NO_TOTAL)</span></span>|<span data-ttu-id="de072-124">ドライバーは、CHAR から WCHAR または WCHAR から CHAR への変換が、(乗算) \* 2 または (除算)/2 アクションであると想定しなくなりました。</span><span class="sxs-lookup"><span data-stu-id="de072-124">The driver no longer assumes that converting from CHAR to WCHAR or WCHAR to CHAR is a (multiply) \*2 or (divide)/2 action.</span></span><br /><br /> <span data-ttu-id="de072-125">**SQLGetData**を呼び出すと、予期される変換の長さが返されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="de072-125">Calling **SQLGetData** no longer returns the length of the expected conversion.</span></span> <span data-ttu-id="de072-126">ドライバーでは CHAR と WCHAR との間の変換が検出され、誤りの可能性のある \*2 または /2 の動作の代わりに (-4) SQL_NO_TOTAL が返されます。</span><span class="sxs-lookup"><span data-stu-id="de072-126">The driver detects the conversion to or from CHAR and WCHAR and returns (-4) SQL_NO_TOTAL instead of \*2 or /2 behavior that could be incorrect.</span></span>|  
  
 <span data-ttu-id="de072-127">**SQLGetData**を使用して、データのチャンクを取得します。</span><span class="sxs-lookup"><span data-stu-id="de072-127">Use **SQLGetData** to retrieve the chunks of the data.</span></span> <span data-ttu-id="de072-128">(擬似コードを示します)。</span><span class="sxs-lookup"><span data-stu-id="de072-128">(Pseudo code shown:)</span></span>  
  
```  
while( (SQL_SUCCESS or SQL_SUCCESS_WITH_INFO) == SQLFetch(...) ) {  
   SQLNumCols(...iTotalCols...)  
   for(int iCol = 1; iCol < iTotalCols; iCol++) {  
      WCHAR* pBufOrig, pBuffer = new WCHAR[100];  
      SQLGetData(.... iCol ... pBuffer, 100, &iSize);   // Get original chunk  
      while(NOT ALL DATA RETREIVED (SQL_NO_TOTAL, ...) ) {  
         pBuffer += 50;   // Advance buffer for data retrieved  
         // May need to realloc the buffer when you reach current size  
         SQLGetData(.... iCol ... pBuffer, 100, &iSize);   // Get next chunk  
      }  
   }  
}  
```  
  
## <a name="sqlbindcol-behavior"></a><span data-ttu-id="de072-129">SQLBindCol の動作</span><span class="sxs-lookup"><span data-stu-id="de072-129">SQLBindCol Behavior</span></span>  
 <span data-ttu-id="de072-130">照会`select convert(varchar(36), '1234567890')`</span><span class="sxs-lookup"><span data-stu-id="de072-130">Query:  `select convert(varchar(36), '1234567890')`</span></span>  
  
```  
SQLBindCol(... SQL_W_CHAR, ...)   // Only bound a buffer of WCHAR[4] - Expecting String Data Right Truncation behavior  
```  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="de072-131">Native Client ODBC ドライバーのバージョン</span><span class="sxs-lookup"><span data-stu-id="de072-131">Native Client ODBC Driver version</span></span>|<span data-ttu-id="de072-132">長さまたはインジケーターの結果</span><span class="sxs-lookup"><span data-stu-id="de072-132">Length or Indicator Outcome</span></span>|<span data-ttu-id="de072-133">説明</span><span class="sxs-lookup"><span data-stu-id="de072-133">Description</span></span>|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] <span data-ttu-id="de072-134">Native Client 以前</span><span class="sxs-lookup"><span data-stu-id="de072-134">Native Client or earlier</span></span>|<span data-ttu-id="de072-135">20</span><span class="sxs-lookup"><span data-stu-id="de072-135">20</span></span>|<span data-ttu-id="de072-136">-   **Sqlfetch**は、データの右側に切り捨てがあることを報告します。</span><span class="sxs-lookup"><span data-stu-id="de072-136">-   **SQLFetch** reports that there is a truncation on the right side of the data.</span></span><br /><span data-ttu-id="de072-137">-Length は、返されるデータの長さであり、格納されたデータではありません (グリフに対して正しくない場合がある \* 2 CHAR から WCHAR への変換が想定されます)。</span><span class="sxs-lookup"><span data-stu-id="de072-137">-   Length is the length of the data returned, not what was stored (assumes \*2 CHAR to WCHAR conversion which can be incorrect for glyphs).</span></span><br /><span data-ttu-id="de072-138">-バッファーに格納されているデータは 123 \ 0 です。</span><span class="sxs-lookup"><span data-stu-id="de072-138">-   Data stored in buffer is 123\0.</span></span> <span data-ttu-id="de072-139">バッファーは NULL 終端であることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="de072-139">Buffer is guaranteed to be NULL terminated.</span></span>|  
|[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] <span data-ttu-id="de072-140">Native Client (Version 11.0.2100.60) 以降</span><span class="sxs-lookup"><span data-stu-id="de072-140">Native Client (version 11.0.2100.60) or later</span></span>|<span data-ttu-id="de072-141">-4 (SQL_NO_TOTAL)</span><span class="sxs-lookup"><span data-stu-id="de072-141">-4 (SQL_NO_TOTAL)</span></span>|<span data-ttu-id="de072-142">-   **Sqlfetch**は、データの右側に切り捨てがあることを報告します。</span><span class="sxs-lookup"><span data-stu-id="de072-142">-   **SQLFetch** reports that there is a truncation on the right side of the data.</span></span><br /><span data-ttu-id="de072-143">-データの残りの部分が変換されていないため、-4 (SQL_NO_TOTAL) を指定します。</span><span class="sxs-lookup"><span data-stu-id="de072-143">-   Length indicates -4 (SQL_NO_TOTAL) because the rest of the data was not converted.</span></span><br /><span data-ttu-id="de072-144">-バッファーに格納されているデータは 123 \ 0 です。</span><span class="sxs-lookup"><span data-stu-id="de072-144">-   Data stored in the buffer is 123\0.</span></span> <span data-ttu-id="de072-145">- バッファーは NULL 終端であることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="de072-145">- Buffer is guaranteed to be NULL terminated.</span></span>|  
  
## <a name="sqlbindparameter-output-parameter-behavior"></a><span data-ttu-id="de072-146">SQLBindParameter (出力パラメーターの動作)</span><span class="sxs-lookup"><span data-stu-id="de072-146">SQLBindParameter (OUTPUT Parameter Behavior)</span></span>  
 <span data-ttu-id="de072-147">照会`create procedure spTest @p1 varchar(max) OUTPUT`</span><span class="sxs-lookup"><span data-stu-id="de072-147">Query:  `create procedure spTest @p1 varchar(max) OUTPUT`</span></span>  
  
 `select @p1 = replicate('B', 1234)`  
  
```  
SQLBindParameter(... SQL_W_CHAR, ...)   // Only bind up to first 64 characters  
```  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="de072-148">Native Client ODBC ドライバーのバージョン</span><span class="sxs-lookup"><span data-stu-id="de072-148">Native Client ODBC Driver version</span></span>|<span data-ttu-id="de072-149">長さまたはインジケーターの結果</span><span class="sxs-lookup"><span data-stu-id="de072-149">Length or Indicator Outcome</span></span>|<span data-ttu-id="de072-150">説明</span><span class="sxs-lookup"><span data-stu-id="de072-150">Description</span></span>|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] <span data-ttu-id="de072-151">Native Client 以前</span><span class="sxs-lookup"><span data-stu-id="de072-151">Native Client or earlier</span></span>|<span data-ttu-id="de072-152">2468</span><span class="sxs-lookup"><span data-stu-id="de072-152">2468</span></span>|<span data-ttu-id="de072-153">-   **Sqlfetch**は、使用可能なデータがないことを返します。</span><span class="sxs-lookup"><span data-stu-id="de072-153">-   **SQLFetch** returns no more data available.</span></span><br /><span data-ttu-id="de072-154">-   **Sqlmoreresults**は、これ以上使用できるデータを返しません。</span><span class="sxs-lookup"><span data-stu-id="de072-154">-   **SQLMoreResults** returns no more data available.</span></span><br /><span data-ttu-id="de072-155">-Length は、サーバーから返されるデータのサイズを示します。バッファーに格納されません。</span><span class="sxs-lookup"><span data-stu-id="de072-155">-   Length indicates the size of the data returned from server, not stored in buffer.</span></span><br /><span data-ttu-id="de072-156">-元のバッファーには、63バイトと NULL 終端文字が含まれています。</span><span class="sxs-lookup"><span data-stu-id="de072-156">-   Original buffer contains 63 bytes and a NULL terminator.</span></span> <span data-ttu-id="de072-157">バッファーは NULL 終端であることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="de072-157">Buffer is guaranteed to be NULL terminated.</span></span>|  
|[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] <span data-ttu-id="de072-158">Native Client (Version 11.0.2100.60) 以降</span><span class="sxs-lookup"><span data-stu-id="de072-158">Native Client (version 11.0.2100.60) or later</span></span>|<span data-ttu-id="de072-159">-4 (SQL_NO_TOTAL)</span><span class="sxs-lookup"><span data-stu-id="de072-159">-4 (SQL_NO_TOTAL)</span></span>|<span data-ttu-id="de072-160">-   **Sqlfetch**は、使用可能なデータがないことを返します。</span><span class="sxs-lookup"><span data-stu-id="de072-160">-   **SQLFetch** returns no more data available.</span></span><br /><span data-ttu-id="de072-161">-   **Sqlmoreresults**は、これ以上使用できるデータを返しません。</span><span class="sxs-lookup"><span data-stu-id="de072-161">-   **SQLMoreResults** returns no more data available.</span></span><br /><span data-ttu-id="de072-162">-データの残りの部分が変換されなかったため、が (-4) SQL_NO_TOTAL を示します。</span><span class="sxs-lookup"><span data-stu-id="de072-162">-   Length indicates (-4) SQL_NO_TOTAL because the rest of the data was not converted.</span></span><br /><span data-ttu-id="de072-163">-元のバッファーには、63バイトと NULL 終端文字が含まれています。</span><span class="sxs-lookup"><span data-stu-id="de072-163">-   Original buffer contains 63 bytes and a NULL terminator.</span></span> <span data-ttu-id="de072-164">バッファーは NULL 終端であることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="de072-164">Buffer is guaranteed to be NULL terminated.</span></span>|  
  
## <a name="performing-char-and-wchar-conversions"></a><span data-ttu-id="de072-165">CHAR と WCHAR の変換の実行</span><span class="sxs-lookup"><span data-stu-id="de072-165">Performing CHAR and WCHAR Conversions</span></span>  
 <span data-ttu-id="de072-166">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client ODBC ドライバーには、CHAR と WCHAR の変換を実行する方法が複数用意されています。</span><span class="sxs-lookup"><span data-stu-id="de072-166">The [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client ODBC driver offers several ways to perform CHAR and WCHAR conversions.</span></span> <span data-ttu-id="de072-167">ロジックは、blob の操作 (varchar (max)、nvarchar (max)、...) に似ています。</span><span class="sxs-lookup"><span data-stu-id="de072-167">The logic is similar to manipulating blobs (varchar(max), nvarchar(max), ...):</span></span>  
  
-   <span data-ttu-id="de072-168">**SQLBindCol**または**SQLBindParameter**にバインドする場合、データは指定されたバッファーに保存されるか、または切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="de072-168">Data is saved or truncated into the specified buffer when binding with **SQLBindCol** or **SQLBindParameter**.</span></span>  
  
-   <span data-ttu-id="de072-169">バインドしない場合は、 **SQLGetData**と**sqlparamdata**を使用して、データをチャンク単位で取得できます。</span><span class="sxs-lookup"><span data-stu-id="de072-169">If you do not bind, you can retrieve the data in chunks by using **SQLGetData** and **SQLParamData**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de072-170">参照</span><span class="sxs-lookup"><span data-stu-id="de072-170">See Also</span></span>  
 [<span data-ttu-id="de072-171">SQL Server Native Client の機能</span><span class="sxs-lookup"><span data-stu-id="de072-171">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  
