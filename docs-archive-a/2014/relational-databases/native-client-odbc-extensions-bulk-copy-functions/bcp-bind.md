---
title: bcp_bind |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_bind
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_bind function
ms.assetid: 6e335a5c-64b2-4bcf-a88f-35dc9393f329
author: rothja
ms.author: jroth
ms.openlocfilehash: db0a58398bf47bd0bb96bd1ef587d41890ed8461
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714333"
---
# <a name="bcp_bind"></a><span data-ttu-id="5242f-102">bcp_bind</span><span class="sxs-lookup"><span data-stu-id="5242f-102">bcp_bind</span></span>
  <span data-ttu-id="5242f-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に一括コピーするために、プログラム変数からテーブル列にデータをバインドします。</span><span class="sxs-lookup"><span data-stu-id="5242f-103">Binds data from a program variable to a table column for bulk copy into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5242f-104">構文</span><span class="sxs-lookup"><span data-stu-id="5242f-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_bind (  
HDBC   
hdbc  
,   
LPCBYTE   
pData  
,  
INT   
cbIndicator  
,  
DBINT   
cbData  
,  
LPCBYTE   
pTerm  
,  
INT   
cbTerm  
,  
INT   
eDataType  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="5242f-105">引数</span><span class="sxs-lookup"><span data-stu-id="5242f-105">Arguments</span></span>  
 <span data-ttu-id="5242f-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="5242f-106">*hdbc*</span></span>  
 <span data-ttu-id="5242f-107">一括コピーが有効な ODBC 接続ハンドルです。</span><span class="sxs-lookup"><span data-stu-id="5242f-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="5242f-108">*pData*</span><span class="sxs-lookup"><span data-stu-id="5242f-108">*pData*</span></span>  
 <span data-ttu-id="5242f-109">コピーされたデータへのポインターです。</span><span class="sxs-lookup"><span data-stu-id="5242f-109">Is a pointer to the data copied.</span></span> <span data-ttu-id="5242f-110">*Edatatype*が SQLTEXT、SQLNTEXT、SQLXML、sqlntext、sqlntext、sqlntext、sqlntext、SQLNTEXT、sqlntext、または SQLIMAGE の場合は、 *pData*を NULL にすることができます。</span><span class="sxs-lookup"><span data-stu-id="5242f-110">If *eDataType* is SQLTEXT, SQLNTEXT, SQLXML, SQLUDT, SQLCHARACTER, SQLVARCHAR, SQLVARBINARY, SQLBINARY, SQLNCHAR or SQLIMAGE, *pData* can be NULL.</span></span> <span data-ttu-id="5242f-111">NULL *pData*は、長いデータ値が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [bcp_moretext](bcp-moretext.md)を使用してチャンクに送信されることを示します。</span><span class="sxs-lookup"><span data-stu-id="5242f-111">A NULL *pData* indicates that long data values will be sent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in chunks using [bcp_moretext](bcp-moretext.md).</span></span> <span data-ttu-id="5242f-112">ユーザーは、ユーザーバインドフィールドに対応する列が BLOB 列の場合、 *pData*を NULL に設定する必要があります。それ以外の場合、 **bcp_bind**は失敗します。</span><span class="sxs-lookup"><span data-stu-id="5242f-112">The user should only set *pData* to NULL if the column corresponding to the user bound field is a BLOB column otherwise **bcp_bind** will fail.</span></span>  
  
 <span data-ttu-id="5242f-113">データ内にインジケーターが存在する場合、それらのインジケーターはメモリ内ではデータの直前にあります。</span><span class="sxs-lookup"><span data-stu-id="5242f-113">If indicators are present in the data, they appear in memory directly before the data.</span></span> <span data-ttu-id="5242f-114">この場合、 *pData*パラメーターはインジケーター変数を指します。インジケーターの幅 ( *cbindicator*パラメーター) は、一括コピーによってユーザーデータを正しくアドレス指定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="5242f-114">The *pData* parameter points to the indicator variable in this case, and the width of the indicator, the *cbIndicator* parameter, is used by bulk copy to address user data correctly.</span></span>  
  
 <span data-ttu-id="5242f-115">*cbIndicator*</span><span class="sxs-lookup"><span data-stu-id="5242f-115">*cbIndicator*</span></span>  
 <span data-ttu-id="5242f-116">列のデータに関する長さのインジケーターや NULL インジケーターのバイト単位の長さです。</span><span class="sxs-lookup"><span data-stu-id="5242f-116">Is the length, in bytes, of a length or null indicator for the column's data.</span></span> <span data-ttu-id="5242f-117">インジケーターの長さの有効値は、0 (インジケーターを使用しない場合)、1、2、4、または 8 です。</span><span class="sxs-lookup"><span data-stu-id="5242f-117">Valid indicator length values are 0 (when using no indicator), 1, 2, 4, or 8.</span></span> <span data-ttu-id="5242f-118">インジケーターは、メモリ内ではすべてのデータの直前にあります。</span><span class="sxs-lookup"><span data-stu-id="5242f-118">Indicators appear in memory directly before any data.</span></span> <span data-ttu-id="5242f-119">たとえば、一括コピーを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに整数値を挿入するには、次のような構造体の型定義を使用します。</span><span class="sxs-lookup"><span data-stu-id="5242f-119">For example, the following structure type definition could be used to insert integer values into an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table using bulk copy:</span></span>  
  
```  
typedef struct tagBCPBOUNDINT  
    {  
    int iIndicator;  
    int Value;  
    } BCPBOUNDINT;  
```  
  
 <span data-ttu-id="5242f-120">この例では、 *pData*パラメーターは、構造体の宣言されたインスタンスのアドレス (BCPBOUNDINT *iindicator*構造体メンバーのアドレス) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="5242f-120">In the example case, the *pData* parameter would be set to the address of a declared instance of the structure, the address of the BCPBOUNDINT *iIndicator* structure member.</span></span> <span data-ttu-id="5242f-121">*Cbindicator*パラメーターは整数のサイズ (sizeof (int)) に設定され、 *cbindicator*パラメーターはもう一度整数のサイズ (sizeof (int)) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="5242f-121">The *cbIndicator* parameter would be set to the size of an integer (sizeof(int)), and the *cbData* parameter would again be set to the size of an integer (sizeof(int)).</span></span> <span data-ttu-id="5242f-122">バインドされた列に NULL 値が含まれているサーバーに行を一括コピーするには、インスタンスの*Iindicator*メンバーの値を SQL_NULL_DATA に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5242f-122">To bulk copy a row to the server containing a NULL value for the bound column, the value of the instance's *iIndicator* member should be set to SQL_NULL_DATA.</span></span>  
  
 <span data-ttu-id="5242f-123">*cbData*</span><span class="sxs-lookup"><span data-stu-id="5242f-123">*cbData*</span></span>  
 <span data-ttu-id="5242f-124">プログラム変数内のデータのバイト数です。長さのインジケーター、NULL インジケーター、およびターミネータの長さは含まれません。</span><span class="sxs-lookup"><span data-stu-id="5242f-124">Is the count of bytes of data in the program variable, not including the length of any length or null indicator or terminator.</span></span>  
  
 <span data-ttu-id="5242f-125">*Cbdata*を SQL_NULL_DATA に設定すると、サーバーにコピーされるすべての行に列の NULL 値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="5242f-125">Setting *cbData* to SQL_NULL_DATA signifies that all rows copied to the server contain a NULL value for the column.</span></span>  
  
 <span data-ttu-id="5242f-126">*Cbdata*を SQL_VARLEN_DATA に設定すると、システムは、文字列ターミネータ (またはその他の方法) を使用してコピーされるデータの長さを決定します。</span><span class="sxs-lookup"><span data-stu-id="5242f-126">Setting *cbData* to SQL_VARLEN_DATA indicates that the system will use a string terminator, or other method, to determine the length of data copied.</span></span>  
  
 <span data-ttu-id="5242f-127">整数などの固定長データ型の場合、データ型によってデータの長さがシステムに示されます。</span><span class="sxs-lookup"><span data-stu-id="5242f-127">For fixed-length data types, such as integers, the data type indicates the length of the data to the system.</span></span> <span data-ttu-id="5242f-128">したがって、固定長データ型の場合は、 *Cbdata*を安全に SQL_VARLEN_DATA することも、データの長さを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="5242f-128">Therefore, for fixed-length data types, *cbData* can safely be SQL_VARLEN_DATA or the length of the data.</span></span>  
  
 <span data-ttu-id="5242f-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]文字データ型およびバイナリデータ型の場合、 *cbdata*には SQL_VARLEN_DATA、SQL_NULL_DATA、正の値、または0を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5242f-129">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] character and binary data types, *cbData* can be SQL_VARLEN_DATA, SQL_NULL_DATA, some positive value, or 0.</span></span> <span data-ttu-id="5242f-130">*Cbdata*が SQL_VARLEN_DATA 場合、システムは長さ/null インジケーター (存在する場合) またはターミネータシーケンスを使用してデータの長さを決定します。</span><span class="sxs-lookup"><span data-stu-id="5242f-130">If *cbData* is SQL_VARLEN_DATA, the system uses either a length/null indicator (if present) or a terminator sequence to determine the length of the data.</span></span> <span data-ttu-id="5242f-131">インジケーターとターミネータ シーケンスの両方を指定した場合、システムでは、コピーされるデータ量が少なくなる方法が使用されます。</span><span class="sxs-lookup"><span data-stu-id="5242f-131">If both are supplied, the system uses the one that results in the least amount of data being copied.</span></span> <span data-ttu-id="5242f-132">*Cbdata*が SQL_VARLEN_DATA 場合、列のデータ型は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 文字型またはバイナリ型で、長さのインジケーターもターミネータシーケンスも指定されていないと、システムはエラーメッセージを返します。</span><span class="sxs-lookup"><span data-stu-id="5242f-132">If *cbData* is SQL_VARLEN_DATA, the data type of the column is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] character or binary type, and neither a length indicator nor a terminator sequence is specified, the system returns an error message.</span></span>  
  
 <span data-ttu-id="5242f-133">*Cbdata*が0または正の値の場合、システムではデータ長として*cbdata*が使用されます。</span><span class="sxs-lookup"><span data-stu-id="5242f-133">If *cbData* is 0 or a positive value, the system uses *cbData* as the data length.</span></span> <span data-ttu-id="5242f-134">ただし、正の*Cbdata*値に加えて、長さのインジケーターまたはターミネータシーケンスが指定されている場合、システムは、コピーされるデータ量が最小になるメソッドを使用してデータ長を決定します。</span><span class="sxs-lookup"><span data-stu-id="5242f-134">However, if, in addition to a positive *cbData* value, a length indicator or terminator sequence is provided, the system determines the data length by using the method that results in the least amount of data being copied.</span></span>  
  
 <span data-ttu-id="5242f-135">*Cbdata*パラメーター値は、データのバイト数を表します。</span><span class="sxs-lookup"><span data-stu-id="5242f-135">The *cbData* parameter value represents the count of bytes of data.</span></span> <span data-ttu-id="5242f-136">文字データが Unicode ワイド文字で表されている場合、 *cbdata*パラメーターの正の値は、各文字のサイズ (バイト単位) を乗算した文字数を表します。</span><span class="sxs-lookup"><span data-stu-id="5242f-136">If character data is represented by Unicode wide characters, then a positive *cbData* parameter value represents the number of characters multiplied by the size in bytes of each character.</span></span>  
  
 <span data-ttu-id="5242f-137">*pTerm*</span><span class="sxs-lookup"><span data-stu-id="5242f-137">*pTerm*</span></span>  
 <span data-ttu-id="5242f-138">このプログラム変数の終了位置をマークするバイト パターンがある場合、そのバイト パターンを指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="5242f-138">Is a pointer to the byte pattern, if any, that marks the end of this program variable.</span></span> <span data-ttu-id="5242f-139">たとえば、通常、ANSI 文字列と MBCS C 文字列には 1 バイトのターミネータ (\0) があります。</span><span class="sxs-lookup"><span data-stu-id="5242f-139">For example, ANSI and MBCS C strings usually have a 1-byte terminator (\0).</span></span>  
  
 <span data-ttu-id="5242f-140">変数にターミネータがない場合は、 *Pterm*を NULL に設定します。</span><span class="sxs-lookup"><span data-stu-id="5242f-140">If there is no terminator for the variable, set *pTerm* to NULL.</span></span>  
  
 <span data-ttu-id="5242f-141">C NULL ターミネータをプログラム変数のターミネータとして指定する場合、空文字列 ("") を使用できます。</span><span class="sxs-lookup"><span data-stu-id="5242f-141">You can use an empty string ("") to designate the C null terminator as the program-variable terminator.</span></span> <span data-ttu-id="5242f-142">Null で終わる空の文字列は1バイト (ターミネータバイト自体) を構成するので、 *Cbterm*を1に設定します。</span><span class="sxs-lookup"><span data-stu-id="5242f-142">Because the null-terminated empty string constitutes a single byte (the terminator byte itself), set *cbTerm* to 1.</span></span> <span data-ttu-id="5242f-143">たとえば、 *szName*の文字列が null で終了し、長さを示すためにターミネータを使用する必要があることを示すには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="5242f-143">For example, to indicate that the string in *szName* is null-terminated and that the terminator should be used to indicate the length:</span></span>  
  
```  
bcp_bind(hdbc, szName, 0,  
   SQL_VARLEN_DATA, "", 1,  
   SQLCHARACTER, 2)  
```  
  
 <span data-ttu-id="5242f-144">この例では、終了しない形式の場合、 *szName*変数からバインドされたテーブルの2番目の列に15文字をコピーすることを示している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5242f-144">A nonterminated form of this example could indicate that 15 characters be copied from the *szName* variable to the second column of the bound table:</span></span>  
  
```  
bcp_bind(hdbc, szName, 0, 15,   
   NULL, 0, SQLCHARACTER, 2)  
```  
  
 <span data-ttu-id="5242f-145">一括コピー API では、必要に応じて Unicode から MBCS への文字変換が実行されます。</span><span class="sxs-lookup"><span data-stu-id="5242f-145">The bulk copy API performs Unicode-to-MBCS character conversion as required.</span></span> <span data-ttu-id="5242f-146">ターミネータのバイト文字列とそのバイト文字列の長さの両方を正しく設定してください。</span><span class="sxs-lookup"><span data-stu-id="5242f-146">Make sure that both the terminator byte string and the length of the byte string are set correctly.</span></span> <span data-ttu-id="5242f-147">たとえば、 *szName*の文字列が unicode ワイド文字列で、unicode の null 終端記号の値によって終了することを示すには、次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="5242f-147">For example, to indicate that the string in *szName* is a Unicode wide character string, terminated by the Unicode null terminator value:</span></span>  
  
```  
bcp_bind(hdbc, szName, 0,   
   SQL_VARLEN_DATA, L"",  
   sizeof(WCHAR), SQLNCHAR, 2)  
```  
  
 <span data-ttu-id="5242f-148">バインドされた [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 列がワイド文字の場合、 [bcp_sendrow](bcp-sendrow.md)に対して変換は実行されません。</span><span class="sxs-lookup"><span data-stu-id="5242f-148">If the bound [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] column is wide character, no conversion is performed on [bcp_sendrow](bcp-sendrow.md).</span></span> <span data-ttu-id="5242f-149">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 列が MBCS 文字型の場合、データが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に送信されるときに、ワイド文字がマルチバイト文字に変換されます。</span><span class="sxs-lookup"><span data-stu-id="5242f-149">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] column is an MBCS character type, wide character to multibyte character conversion is performed as the data is sent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="5242f-150">*cbTerm*</span><span class="sxs-lookup"><span data-stu-id="5242f-150">*cbTerm*</span></span>  
 <span data-ttu-id="5242f-151">プログラム変数にターミネータがある場合は、そのターミネータを構成するバイト数です。</span><span class="sxs-lookup"><span data-stu-id="5242f-151">Is the count of bytes present in the terminator for the program variable, if any.</span></span> <span data-ttu-id="5242f-152">変数にターミネータがない場合は、 *Cbterm*を0に設定します。</span><span class="sxs-lookup"><span data-stu-id="5242f-152">If there is no terminator for the variable, set *cbTerm* to 0.</span></span>  
  
 <span data-ttu-id="5242f-153">*eDataType*</span><span class="sxs-lookup"><span data-stu-id="5242f-153">*eDataType*</span></span>  
 <span data-ttu-id="5242f-154">プログラム変数の C データ型です。</span><span class="sxs-lookup"><span data-stu-id="5242f-154">Is the C data type of the program variable.</span></span> <span data-ttu-id="5242f-155">プログラム変数内のデータは、データベース列の型に変換されます。</span><span class="sxs-lookup"><span data-stu-id="5242f-155">The data in the program variable is converted to the type of the database column.</span></span> <span data-ttu-id="5242f-156">このパラメーターが 0 の場合、変換は実行されません。</span><span class="sxs-lookup"><span data-stu-id="5242f-156">If this parameter is 0, no conversion is performed.</span></span>  
  
 <span data-ttu-id="5242f-157">*Edatatype*パラメーターは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC C データ型の列挙子ではなく、sqlncli のデータ型のトークンによって列挙されます。</span><span class="sxs-lookup"><span data-stu-id="5242f-157">The *eDataType* parameter is enumerated by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type tokens in sqlncli.h, not the ODBC C data type enumerators.</span></span> <span data-ttu-id="5242f-158">たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固有の SQLINT2 型を使用して、ODBC の SQL_C_SHORT 型の 2 バイトの整数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5242f-158">For example, you can specify a two-byte integer, ODBC type SQL_C_SHORT, using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific type SQLINT2.</span></span>  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]<span data-ttu-id="5242f-159">では、paramenter での SQLXML および SQLUDT データ型のトークンのサポートが導入されました *`eDataType`* 。</span><span class="sxs-lookup"><span data-stu-id="5242f-159">introduced support for SQLXML and SQLUDT data type tokens in the *`eDataType`* paramenter.</span></span>  
  
 <span data-ttu-id="5242f-160">*idxServerCol*</span><span class="sxs-lookup"><span data-stu-id="5242f-160">*idxServerCol*</span></span>  
 <span data-ttu-id="5242f-161">データベース テーブル内にある、データのコピー先となる列の序数位置です。</span><span class="sxs-lookup"><span data-stu-id="5242f-161">Is the ordinal position of the column in the database table to which the data is copied.</span></span> <span data-ttu-id="5242f-162">テーブル内の最初の列は列 1 です。</span><span class="sxs-lookup"><span data-stu-id="5242f-162">The first column in a table is column 1.</span></span> <span data-ttu-id="5242f-163">列の序数位置は[Sqlcolumns](../native-client-odbc-api/sqlcolumns.md)によって報告されます。</span><span class="sxs-lookup"><span data-stu-id="5242f-163">The ordinal position of a column is reported by [SQLColumns](../native-client-odbc-api/sqlcolumns.md).</span></span>  
  
## <a name="returns"></a><span data-ttu-id="5242f-164">戻り値</span><span class="sxs-lookup"><span data-stu-id="5242f-164">Returns</span></span>  
 <span data-ttu-id="5242f-165">SUCCEED または FAIL。</span><span class="sxs-lookup"><span data-stu-id="5242f-165">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5242f-166">解説</span><span class="sxs-lookup"><span data-stu-id="5242f-166">Remarks</span></span>  
 <span data-ttu-id="5242f-167">プログラム変数からのテーブルにデータをコピーする高速で効率的な方法には、 **bcp_bind**を使用し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="5242f-167">Use **bcp_bind** for a fast, efficient way to copy data from a program variable into a table in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="5242f-168">このまたはその他の一括コピー関数を呼び出す前に[bcp_init](bcp-init.md)を呼び出してください。</span><span class="sxs-lookup"><span data-stu-id="5242f-168">Call [bcp_init](bcp-init.md) before calling this or any other bulk-copy function.</span></span> <span data-ttu-id="5242f-169">**Bcp_init**を呼び出すと、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 一括コピーの対象テーブルが設定されます。</span><span class="sxs-lookup"><span data-stu-id="5242f-169">Calling **bcp_init** sets the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] target table for bulk copy.</span></span> <span data-ttu-id="5242f-170">**Bcp_bind**と[bcp_sendrow](bcp-sendrow.md)で使用するために**bcp_init**を呼び出すと、データファイルを示す**BCP_INIT**の_szdatafile_ファイルパラメーターが NULL に設定されます。**bcp_init**_edirection_パラメーターが DB_IN に設定されています。</span><span class="sxs-lookup"><span data-stu-id="5242f-170">When calling **bcp_init** for use with **bcp_bind** and [bcp_sendrow](bcp-sendrow.md), the **bcp_init** _szDataFile_ parameter, indicating the data file, is set to NULL; the **bcp_init**_eDirection_ parameter is set to DB_IN.</span></span>  
  
 <span data-ttu-id="5242f-171">コピー先のテーブル内のすべての列に対して、個別の**bcp_bind**呼び出しを作成 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] します。</span><span class="sxs-lookup"><span data-stu-id="5242f-171">Make a separate **bcp_bind** call for every column in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table into which you want to copy.</span></span> <span data-ttu-id="5242f-172">必要な**bcp_bind**の呼び出しが行われたら、 **bcp_sendrow**を呼び出して、プログラム変数からにデータ行を送信し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="5242f-172">After the necessary **bcp_bind** calls have been made, then call **bcp_sendrow** to send a row of data from your program variables to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5242f-173">列の再バインドはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="5242f-173">Rebinding a column is not supported.</span></span>  
  
 <span data-ttu-id="5242f-174">既に受信した行をコミットする場合は常に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、 [bcp_batch](bcp-batch.md)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5242f-174">Whenever you want [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to commit the rows already received, call [bcp_batch](bcp-batch.md).</span></span> <span data-ttu-id="5242f-175">たとえば、1000行が挿入されるたびに、またはその他の間隔で1回**bcp_batch**を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5242f-175">For example, call **bcp_batch** once for every 1000 rows inserted or at any other interval.</span></span>  
  
 <span data-ttu-id="5242f-176">挿入する行がなくなった場合は、 [bcp_done](bcp-done.md)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5242f-176">When there are no more rows to be inserted, call [bcp_done](bcp-done.md).</span></span> <span data-ttu-id="5242f-177">この操作を行わないと、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="5242f-177">Failure to do so results in an error.</span></span>  
  
 <span data-ttu-id="5242f-178">[Bcp_control](bcp-control.md)で指定されたコントロールパラメーターの設定は、 **bcp_bind**の行転送には影響しません。</span><span class="sxs-lookup"><span data-stu-id="5242f-178">Control parameter settings, specified with [bcp_control](bcp-control.md), have no effect on **bcp_bind** row transfers.</span></span>  
  
 <span data-ttu-id="5242f-179">列の値が[bcp_moretext](bcp-moretext.md)の呼び出しによって指定されるため、列の*pData*が null に設定されている場合は、 *EDATATYPE*が SQLTEXT、SQLNTEXT、SQLXML、SQLNTEXT、SQLNTEXT、SQLNTEXT、SQLNTEXT、sqlntext、sqlntext、または SQLIMAGE に設定されている後続の列も*pdata*に設定する必要があり `bcp_moretext` ます。また</span><span class="sxs-lookup"><span data-stu-id="5242f-179">If *pData* for a column is set to NULL because its value will be supplied by calls to [bcp_moretext](bcp-moretext.md), any subsequent columns with *eDataType* set to SQLTEXT, SQLNTEXT, SQLXML, SQLUDT, SQLCHARACTER, SQLVARCHAR, SQLVARBINARY, SQLBINARY, SQLNCHAR, or SQLIMAGE must also be bound with *pData* set to NULL, and their values must also be supplied by calls to `bcp_moretext`.</span></span>  
  
 <span data-ttu-id="5242f-180">、、などの新しい大きな値型の場合は、 `varchar(max)` `varbinary(max)` `nvarchar(max)` *edatatype*パラメーターで型インジケーターとして sqlcharacter、SQLCHARACTER、sqlcharacter、SQLCHARACTER、および sqlcharacter を使用できます。</span><span class="sxs-lookup"><span data-stu-id="5242f-180">For new large value types, such as `varchar(max)`, `varbinary(max)`, or `nvarchar(max)`, you can use SQLCHARACTER, SQLVARCHAR, SQLVARBINARY, SQLBINARY, and SQLNCHAR as type indicators in the *eDataType* parameter.</span></span>  
  
 <span data-ttu-id="5242f-181">*Cbterm*が0でない場合は、すべての値 (1、2、4、または 8) がプレフィックス (*cbterm*) に対して有効です。</span><span class="sxs-lookup"><span data-stu-id="5242f-181">If *cbTerm* is not 0, any value (1, 2, 4, or 8) is valid for the prefix (*cbIndicator*).</span></span> <span data-ttu-id="5242f-182">この場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client はターミネータを検索し、ターミネータ (*i*) に対してデータの長さを計算し、 *cbdata*を i の小さい値と prefix の値に設定します。</span><span class="sxs-lookup"><span data-stu-id="5242f-182">In this situation, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client will search for the terminator, calculate data length with respect to the terminator (*i*), and set the *cbData* to the smaller value of i and the value of prefix.</span></span>  
  
 <span data-ttu-id="5242f-183">*Cbterm*が0で、 *cbterm* (プレフィックス) が0でない場合、 *cbterm*は8である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5242f-183">If *cbTerm* is 0 and *cbIndicator* (the prefix) is not 0, *cbIndicator* must be 8.</span></span> <span data-ttu-id="5242f-184">8 バイトのプレフィックスでは、次の値を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="5242f-184">The 8 byte prefix can take the following values:</span></span>  
  
-   <span data-ttu-id="5242f-185">0xFFFFFFFFFFFFFFFF は、フィールドの NULL 値を示します。</span><span class="sxs-lookup"><span data-stu-id="5242f-185">0xFFFFFFFFFFFFFFFF means a null value for the field</span></span>  
  
-   <span data-ttu-id="5242f-186">0xFFFFFFFFFFFFFFFE は、データをチャンク単位でサーバーに効率的に送信するために使用する特別なプレフィックスの値として処理されます。</span><span class="sxs-lookup"><span data-stu-id="5242f-186">0xFFFFFFFFFFFFFFFE is treated as a special prefix value which is used for efficiently sending data in chunks to the server.</span></span> <span data-ttu-id="5242f-187">この特別なプレフィックス値を含むデータは、次のような形式になります。</span><span class="sxs-lookup"><span data-stu-id="5242f-187">The format of data with this special prefix is:</span></span>  
  
-   <span data-ttu-id="5242f-188"><SPECIAL_PREFIX> \<0 or more  DATA CHUNKS> <ZERO_CHUNK の場所:</span><span class="sxs-lookup"><span data-stu-id="5242f-188"><SPECIAL_PREFIX> \<0 or more  DATA CHUNKS> <ZERO_CHUNK> where:</span></span>  
  
-   <span data-ttu-id="5242f-189">SPECIAL_PREFIX には 0xFFFFFFFFFFFFFFFE を指定します。</span><span class="sxs-lookup"><span data-stu-id="5242f-189">SPECIAL_PREFIX is 0xFFFFFFFFFFFFFFFE</span></span>  
  
-   <span data-ttu-id="5242f-190">DATA_CHUNK には、チャンクの長さを含む 4 バイトのプレフィックスを指定し、その後に 4 バイトのプレフィックスで長さを指定した実際のデータを指定します。</span><span class="sxs-lookup"><span data-stu-id="5242f-190">DATA_CHUNK is a 4 byte prefix containing length of the chunk,followed by the actual data whose length is specified in the 4 byte prefix.</span></span>  
  
-   <span data-ttu-id="5242f-191">ZERO_CHUNK には、データの終了を示す、すべてがゼロの 4 バイトの値 (00000000) を指定します。</span><span class="sxs-lookup"><span data-stu-id="5242f-191">ZERO_CHUNK is a 4 byte value containing all zeros (00000000) indicating the end of data.</span></span>  
  
-   <span data-ttu-id="5242f-192">その他の有効な 8 バイト長は、通常のデータ長として処理されます。</span><span class="sxs-lookup"><span data-stu-id="5242f-192">Any other valid 8 byte length is treated as a regular data length.</span></span>  
  
 <span data-ttu-id="5242f-193">**Bcp_bind**を使用するときに[bcp_columns](bcp-columns.md)を呼び出すと、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="5242f-193">Calling [bcp_columns](bcp-columns.md) when using **bcp_bind** results in an error.</span></span>  
  
## <a name="bcp_bind-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="5242f-194">bcp_bind による機能強化された日付と時刻のサポート</span><span class="sxs-lookup"><span data-stu-id="5242f-194">bcp_bind Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="5242f-195">日付型または時刻型の*Edatatype*パラメーターで使用される型の詳細については、「 [&#40;OLE DB および ODBC&#41;の拡張された日付/時刻型に対する一括コピーの変更](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5242f-195">For information about the types used with the *eDataType* parameter for date/time types, see [Bulk Copy Changes for Enhanced Date and Time Types &#40;OLE DB and ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).</span></span>  
  
 <span data-ttu-id="5242f-196">詳細については、「[日付と時刻の機能強化 &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5242f-196">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5242f-197">例</span><span class="sxs-lookup"><span data-stu-id="5242f-197">Example</span></span>  
  
```  
#include sql.h  
#include sqlext.h  
#include odbcss.h  
// Variables like henv not specified.  
HDBC      hdbc;  
char         szCompanyName[MAXNAME];  
DBINT      idCompany;  
DBINT      nRowsProcessed;  
DBBOOL      bMoreData;  
char*      pTerm = "\t\t";  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source; return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bcp.   
if (bcp_init(hdbc, "comdb..accounts_info", NULL, NULL  
   DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Bind program variables to table columns.   
if (bcp_bind(hdbc, (LPCBYTE) &idCompany, 0, sizeof(DBINT), NULL, 0,  
   SQLINT4, 1)    == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
if (bcp_bind(hdbc, (LPCBYTE) szCompanyName, 0, SQL_VARLEN_DATA,  
   (LPCBYTE) pTerm, strnlen(pTerm, sizeof(pTerm)), SQLCHARACTER, 2) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
while (TRUE)  
   {  
   // Retrieve and process program data.   
   if ((bMoreData = getdata(&idCompany, szCompanyName)) == TRUE)  
      {  
      // Send the data.   
      if (bcp_sendrow(hdbc) == FAIL)  
         {  
         // Raise error and return.  
         return;  
         }  
      }  
   else  
      {  
      // Break out of loop.  
      break;  
      }  
   }  
  
// Terminate the bulk copy operation.  
if ((nRowsProcessed = bcp_done(hdbc)) == -1)  
   {  
   printf_s("Bulk-copy unsuccessful.\n");  
   return;  
   }  
  
printf_s("%ld rows copied.\n", nRowsProcessed);  
```  
  
## <a name="see-also"></a><span data-ttu-id="5242f-198">参照</span><span class="sxs-lookup"><span data-stu-id="5242f-198">See Also</span></span>  
 [<span data-ttu-id="5242f-199">一括コピー関数</span><span class="sxs-lookup"><span data-stu-id="5242f-199">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
