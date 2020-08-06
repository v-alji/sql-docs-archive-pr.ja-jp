---
title: bcp_colfmt |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_colfmt
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_colfmt function
ms.assetid: 5c3b6299-80c7-4e84-8e69-4ff33009548e
author: rothja
ms.author: jroth
ms.openlocfilehash: f646f3aaf9a8f640d829020bd6762c07c406b61f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742017"
---
# <a name="bcp_colfmt"></a><span data-ttu-id="de78e-102">bcp_colfmt</span><span class="sxs-lookup"><span data-stu-id="de78e-102">bcp_colfmt</span></span>
  <span data-ttu-id="de78e-103">ユーザー ファイルのデータのコピー元またはコピー先の形式を指定します。</span><span class="sxs-lookup"><span data-stu-id="de78e-103">Specifies the source or target format of the data in a user file.</span></span> <span data-ttu-id="de78e-104">ソース形式として使用する場合、 **bcp_colfmt**は、テーブルへの一括コピーのデータソースとして使用される既存のデータファイルの形式を指定し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="de78e-104">When used as a source format, **bcp_colfmt** specifies the format of an existing data file used as the source of data in a bulk copy to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="de78e-105">ターゲット形式として使用する場合は、 **bcp_colfmt**で指定された列形式を使用してデータファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="de78e-105">When used as a target format, the data file is created using the column formats specified with **bcp_colfmt**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de78e-106">構文</span><span class="sxs-lookup"><span data-stu-id="de78e-106">Syntax</span></span>  
  
```  
  
RETCODE bcp_colfmt (  
HDBC   
hdbc  
,  
INT  
idxUserDataCol  
,  
BYTE   
eUserDataType  
,  
INT   
cbIndicator  
,  
DBINT   
cbUserData  
,  
LPCBYTE   
pUserDataTerm  
,  
INT   
cbUserDataTerm  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="de78e-107">引数</span><span class="sxs-lookup"><span data-stu-id="de78e-107">Arguments</span></span>  
 <span data-ttu-id="de78e-108">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="de78e-108">*hdbc*</span></span>  
 <span data-ttu-id="de78e-109">一括コピーが有効な ODBC 接続ハンドルです。</span><span class="sxs-lookup"><span data-stu-id="de78e-109">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="de78e-110">*idxUserDataCol*</span><span class="sxs-lookup"><span data-stu-id="de78e-110">*idxUserDataCol*</span></span>  
 <span data-ttu-id="de78e-111">ユーザー データ ファイルの、形式が指定される列の序数です。</span><span class="sxs-lookup"><span data-stu-id="de78e-111">Is the ordinal column number in the user data file for which the format is being specified.</span></span> <span data-ttu-id="de78e-112">最初の列は 1 です。</span><span class="sxs-lookup"><span data-stu-id="de78e-112">The first column is 1.</span></span>  
  
 <span data-ttu-id="de78e-113">*eUserDataType*</span><span class="sxs-lookup"><span data-stu-id="de78e-113">*eUserDataType*</span></span>  
 <span data-ttu-id="de78e-114">ユーザー ファイル内にある列のデータ型です。</span><span class="sxs-lookup"><span data-stu-id="de78e-114">Is the data type of this column in the user file.</span></span> <span data-ttu-id="de78e-115">データベーステーブル (*Idxservercolumn*) の対応する列のデータ型と異なる場合は、可能であれば一括コピーによってデータが変換されます。</span><span class="sxs-lookup"><span data-stu-id="de78e-115">If different from the data type of the corresponding column in the database table (*idxServerColumn*), bulk copy converts the data if possible.</span></span>  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]<span data-ttu-id="de78e-116">では、 *Euserdatatype*パラメーターでの SQLXML および sqludt データ型のトークンのサポートが導入されました。</span><span class="sxs-lookup"><span data-stu-id="de78e-116">introduced support for SQLXML and SQLUDT data type tokens in the *eUserDataType* parameter.</span></span>  
  
 <span data-ttu-id="de78e-117">*Euserdatatype*パラメーターは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC C データ型の列挙子ではなく、sqlncli のデータ型のトークンによって列挙されます。</span><span class="sxs-lookup"><span data-stu-id="de78e-117">The *eUserDataType* parameter is enumerated by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type tokens in sqlncli.h, not the ODBC C data type enumerators.</span></span> <span data-ttu-id="de78e-118">たとえば、固有の型 SQLCHARACTER を使用して、文字列、ODBC 型 SQL_C_CHAR を指定でき [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="de78e-118">For example, you can specify a character string, ODBC type SQL_C_CHAR, using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific type SQLCHARACTER.</span></span>  
  
 <span data-ttu-id="de78e-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ型に対して既定のデータ表現を指定するには、このパラメーターに 0 を設定します。</span><span class="sxs-lookup"><span data-stu-id="de78e-119">To specify the default data representation for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type, set this parameter to 0.</span></span>  
  
 <span data-ttu-id="de78e-120">ファイルへの一括コピーを行う [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 場合、 *Euserdatatype*が SQLDECIMAL または sqldecimal の場合は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="de78e-120">For a bulk copy out of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] into a file, when *eUserDataType* is SQLDECIMAL or SQLNUMERIC:</span></span>  
  
-   <span data-ttu-id="de78e-121">ソース列が**decimal**または**numeric**でない場合は、既定の有効桁数と小数点以下桁数が使用されます。</span><span class="sxs-lookup"><span data-stu-id="de78e-121">If the source column is not **decimal** or **numeric**, the default precision and scale are used.</span></span>  
  
-   <span data-ttu-id="de78e-122">ソース列が**decimal**または**numeric**の場合は、ソース列の有効桁数と小数点以下桁数が使用されます。</span><span class="sxs-lookup"><span data-stu-id="de78e-122">If the source column is **decimal** or **numeric**, the precision and scale of the source column are used.</span></span>  
  
 <span data-ttu-id="de78e-123">*cbIndicator*</span><span class="sxs-lookup"><span data-stu-id="de78e-123">*cbIndicator*</span></span>  
 <span data-ttu-id="de78e-124">列データ内にある長さのインジケーターや NULL インジケーターのバイト単位の長さです。</span><span class="sxs-lookup"><span data-stu-id="de78e-124">Is the length, in bytes, of a length/null indicator within the column data.</span></span> <span data-ttu-id="de78e-125">インジケーターの長さの有効値は、0 (インジケーターを使用しない場合)、1、2、4、または 8 です。</span><span class="sxs-lookup"><span data-stu-id="de78e-125">Valid indicator length values are 0 (when using no indicator), 1, 2, 4, or 8.</span></span>  
  
 <span data-ttu-id="de78e-126">一括コピーのインジケーターの既定の使用方法を指定するには、このパラメーターに SQL_VARLEN_DATA を設定します。</span><span class="sxs-lookup"><span data-stu-id="de78e-126">To specify default bulk copy indicator usage, set this parameter to SQL_VARLEN_DATA.</span></span>  
  
 <span data-ttu-id="de78e-127">インジケーターは、メモリ内ではすべてのデータの直前に、データ ファイル内ではインジケーターを適用するデータの直前に配置します。</span><span class="sxs-lookup"><span data-stu-id="de78e-127">Indicators appear in memory directly before any data, and in the data file directly before the data to which they apply.</span></span>  
  
 <span data-ttu-id="de78e-128">複数の方法 (インジケーターと列の最大長、インジケーターとターミネータ シーケンスなど) を使用してデータ ファイルの列長を指定すると、一括コピーではコピーするデータの量が最も少なくなる方法が使用されます。</span><span class="sxs-lookup"><span data-stu-id="de78e-128">If more than one means of specifying a data file column length is used (such as an indicator and a maximum column length, or an indicator and a terminator sequence), bulk copy chooses the one that results in the least amount of data being copied.</span></span>  
  
 <span data-ttu-id="de78e-129">ユーザーの操作でデータの形式が調整されずに一括コピーで生成されたデータ ファイルには、列データの長さが異なる場合や、列の値に NULL が許容される場合にインジケーターが含まれます。</span><span class="sxs-lookup"><span data-stu-id="de78e-129">Data files generated by bulk copy when no user intervention adjusts the format of the data contain indicators when the column data can vary in length or the column can accept NULL as a value.</span></span>  
  
 <span data-ttu-id="de78e-130">*cbUserData*</span><span class="sxs-lookup"><span data-stu-id="de78e-130">*cbUserData*</span></span>  
 <span data-ttu-id="de78e-131">ユーザー ファイル内にある列データの最大長 (バイト単位)。長さのインジケーターやターミネータの長さは含まれません。</span><span class="sxs-lookup"><span data-stu-id="de78e-131">Is the maximum length, in bytes, of this column's data in the user file, not including the length of any length indicator or terminator.</span></span>  
  
 <span data-ttu-id="de78e-132">*Cbuserdata*を SQL_NULL_DATA に設定すると、データファイルの列のすべての値がであるか、NULL に設定する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="de78e-132">Setting *cbUserData* to SQL_NULL_DATA indicates that all values in the data file column are, or should be set to NULL.</span></span>  
  
 <span data-ttu-id="de78e-133">*Cbuserdata*を SQL_VARLEN_DATA に設定すると、各列のデータの長さがシステムによって決定されることになります。</span><span class="sxs-lookup"><span data-stu-id="de78e-133">Setting *cbUserData* to SQL_VARLEN_DATA indicates that the system should determine the length of data in each column.</span></span> <span data-ttu-id="de78e-134">これは、列によっては、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からコピーされるデータの前に長さのインジケーターや NULL インジケーターを生成したり、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にコピーするデータにインジケーターが必要になる場合があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="de78e-134">For some columns, this could mean that a length/null indicator is generated to precede data on a copy from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or that the indicator is expected in data copied to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="de78e-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]文字データ型とバイナリデータ型の場合、 *Cbuserdata*には SQL_VARLEN_DATA、SQL_NULL_DATA、0、または正の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="de78e-135">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] character and binary data types, *cbUserData* can be SQL_VARLEN_DATA, SQL_NULL_DATA, 0, or some positive value.</span></span> <span data-ttu-id="de78e-136">*Cbuserdata*が SQL_VARLEN_DATA 場合、システムは長さインジケーター (存在する場合) またはターミネータシーケンスを使用してデータの長さを決定します。</span><span class="sxs-lookup"><span data-stu-id="de78e-136">If *cbUserData* is SQL_VARLEN_DATA, the system uses either the length indicator, if present, or a terminator sequence to determine the length of the data.</span></span> <span data-ttu-id="de78e-137">長さのインジケーターとターミネータ シーケンスの両方を指定した場合、一括コピーはコピーするデータ量が少なくなる方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="de78e-137">If both a length indicator and a terminator sequence are supplied, bulk copy uses the one that results in the least amount of data being copied.</span></span> <span data-ttu-id="de78e-138">*Cbuserdata*が SQL_VARLEN_DATA 場合、データ型は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 文字型またはバイナリ型で、長さのインジケーターもターミネータシーケンスも指定されていないと、システムはエラーメッセージを返します。</span><span class="sxs-lookup"><span data-stu-id="de78e-138">If *cbUserData* is SQL_VARLEN_DATA, the data type is an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] character or binary type, and neither a length indicator nor a terminator sequence is specified, the system returns an error message.</span></span>  
  
 <span data-ttu-id="de78e-139">*cbUserData* が 0 または正の値の場合、システムは最大データ長として *cbUserData* を使用します。</span><span class="sxs-lookup"><span data-stu-id="de78e-139">If *cbUserData* is 0 or a positive value, the system uses *cbUserData* as the maximum data length.</span></span> <span data-ttu-id="de78e-140">ただし、*cbUserData* に正の値を指定し、長さのインジケーターやターミネータ シーケンスを指定した場合、システムはコピーするデータ量が少なくなる方法を使用してデータ長を決定します。</span><span class="sxs-lookup"><span data-stu-id="de78e-140">However, if, in addition to a positive *cbUserData*, a length indicator or terminator sequence is provided, the system determines the data length by using the method that results in the least amount of data being copied.</span></span>  
  
 <span data-ttu-id="de78e-141">*cbUserData* の値はデータのバイト数を表します。</span><span class="sxs-lookup"><span data-stu-id="de78e-141">The *cbUserData* value represents the count of bytes of data.</span></span> <span data-ttu-id="de78e-142">文字データが Unicode ワイド文字で表されている場合、*cbUserData* パラメーターが正の値のときは、各文字のサイズ (バイト数) に文字数を掛けた数を表します。</span><span class="sxs-lookup"><span data-stu-id="de78e-142">If character data is represented by Unicode wide characters, then a positive *cbUserData* parameter value represents the number of characters multiplied by the size, in bytes, of each character.</span></span>  
  
 <span data-ttu-id="de78e-143">*pUserDataTerm*</span><span class="sxs-lookup"><span data-stu-id="de78e-143">*pUserDataTerm*</span></span>  
 <span data-ttu-id="de78e-144">列に使用するターミネータ シーケンスです。</span><span class="sxs-lookup"><span data-stu-id="de78e-144">Is the terminator sequence to be used for this column.</span></span> <span data-ttu-id="de78e-145">このパラメーターは主に文字データ型に対して有効です。これは、他のすべての型は固定長であったり、バイト数を正確に記録するために長さのインジケーターが必要になる (バイナリ データの場合) ためです。</span><span class="sxs-lookup"><span data-stu-id="de78e-145">This parameter is useful mainly for character data types because all other types are of fixed length or, in the case of binary data, require an indicator of length to accurately record the number of bytes present.</span></span>  
  
 <span data-ttu-id="de78e-146">抽出されるデータが途中で終了されないようにしたり、ユーザー ファイル内のデータが途中で終了していないことを示すには、このパラメーターに NULL を設定します。</span><span class="sxs-lookup"><span data-stu-id="de78e-146">To avoid terminating extracted data, or to indicate that data in a user file is not terminated, set this parameter to NULL.</span></span>  
  
 <span data-ttu-id="de78e-147">複数の方法 (ターミネータと長さのインジケーター、ターミネータと列の最大長など) を使用してユーザー ファイルの列長を指定すると、一括コピーはコピーするデータの量が最も少なくなる方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="de78e-147">If more than one means of specifying a user-file column length is used (such as a terminator and a length indicator, or a terminator and a maximum column length), bulk copy chooses the one that results in the least amount of data being copied.</span></span>  
  
 <span data-ttu-id="de78e-148">一括コピー API では、必要に応じて Unicode から MBCS への文字変換が実行されます。</span><span class="sxs-lookup"><span data-stu-id="de78e-148">The bulk copy API performs Unicode-to-MBCS character conversion as required.</span></span> <span data-ttu-id="de78e-149">このため、ターミネータのバイト文字列とそのバイト文字列の長さの両方を正しく設定するように注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="de78e-149">Care must be taken to ensure that both the terminator byte string and the length of the byte string are set correctly.</span></span>  
  
 <span data-ttu-id="de78e-150">*cbUserDataTerm*</span><span class="sxs-lookup"><span data-stu-id="de78e-150">*cbUserDataTerm*</span></span>  
 <span data-ttu-id="de78e-151">列に使用するターミネータ シーケンスの長さ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="de78e-151">Is the length, in bytes, of the terminator sequence to be used for this column.</span></span> <span data-ttu-id="de78e-152">データ内にターミネータが存在しないか不要な場合は、この値を 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="de78e-152">If no terminator is present or desired in the data, set this value to 0.</span></span>  
  
 <span data-ttu-id="de78e-153">*idxServerCol*</span><span class="sxs-lookup"><span data-stu-id="de78e-153">*idxServerCol*</span></span>  
 <span data-ttu-id="de78e-154">データベーステーブル内の列の序数位置です。</span><span class="sxs-lookup"><span data-stu-id="de78e-154">Is the ordinal position of the column in the database table.</span></span> <span data-ttu-id="de78e-155">最初の列の序数は 1 です。</span><span class="sxs-lookup"><span data-stu-id="de78e-155">The first column number is 1.</span></span> <span data-ttu-id="de78e-156">列の序数位置は[Sqlcolumns](../native-client-odbc-api/sqlcolumns.md)によって報告されます。</span><span class="sxs-lookup"><span data-stu-id="de78e-156">The ordinal position of a column is reported by [SQLColumns](../native-client-odbc-api/sqlcolumns.md).</span></span>  
  
 <span data-ttu-id="de78e-157">この値が 0 の場合、一括コピーではデータ ファイル内のこの列が無視されます。</span><span class="sxs-lookup"><span data-stu-id="de78e-157">If this value is 0, bulk copy ignores the column in the data file.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="de78e-158">戻り値</span><span class="sxs-lookup"><span data-stu-id="de78e-158">Returns</span></span>  
 <span data-ttu-id="de78e-159">SUCCEED または FAIL。</span><span class="sxs-lookup"><span data-stu-id="de78e-159">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de78e-160">解説</span><span class="sxs-lookup"><span data-stu-id="de78e-160">Remarks</span></span>  
 <span data-ttu-id="de78e-161">**Bcp_colfmt**関数を使用すると、一括コピーのユーザーファイル形式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="de78e-161">The **bcp_colfmt** function allows you to specify the user-file format for bulk copies.</span></span> <span data-ttu-id="de78e-162">次に、一括コピーに使用するフォーマットの内容を示します。</span><span class="sxs-lookup"><span data-stu-id="de78e-162">For bulk copy, a format contains the following parts:</span></span>  
  
-   <span data-ttu-id="de78e-163">ユーザー ファイルの列からデータベース列へのマッピング</span><span class="sxs-lookup"><span data-stu-id="de78e-163">A mapping from user-file columns to database columns.</span></span>  
  
-   <span data-ttu-id="de78e-164">ユーザー ファイルの各列のデータ型</span><span class="sxs-lookup"><span data-stu-id="de78e-164">The data type of each user-file column.</span></span>  
  
-   <span data-ttu-id="de78e-165">各列の省略可能なインジケーターの長さ</span><span class="sxs-lookup"><span data-stu-id="de78e-165">The length of the optional indicator for each column.</span></span>  
  
-   <span data-ttu-id="de78e-166">ユーザー ファイルの各列におけるデータの最大長</span><span class="sxs-lookup"><span data-stu-id="de78e-166">The maximum length of data per user-file column.</span></span>  
  
-   <span data-ttu-id="de78e-167">各列の省略可能なターミネータ バイト シーケンス</span><span class="sxs-lookup"><span data-stu-id="de78e-167">The optional terminating byte sequence for each column.</span></span>  
  
-   <span data-ttu-id="de78e-168">省略可能なターミネータ バイト シーケンスの長さ</span><span class="sxs-lookup"><span data-stu-id="de78e-168">The length of the optional terminating byte sequence.</span></span>  
  
 <span data-ttu-id="de78e-169">**Bcp_colfmt**を呼び出すたびに、1つのユーザーファイル列の形式が指定されます。</span><span class="sxs-lookup"><span data-stu-id="de78e-169">Each call to **bcp_colfmt** specifies the format for one user-file column.</span></span> <span data-ttu-id="de78e-170">たとえば、5つの列から構成されるユーザーデータファイルの3つの列の既定の設定を変更するには、まず[bcp_columns](bcp-columns.md)**(5)** を呼び出し、 **bcp_colfmt**次に5回呼び出します。これらの呼び出しのうち3つを使用して、カスタム形式を設定します。</span><span class="sxs-lookup"><span data-stu-id="de78e-170">For example, to change the default settings for three columns in a five-column user data file, first call [bcp_columns](bcp-columns.md)**(5)**, and then call **bcp_colfmt** five times, with three of those calls setting your custom format.</span></span> <span data-ttu-id="de78e-171">残りの2つの呼び出しでは、 *Euserdatatype*を0に設定し、 *cbindicator*、 *Cbuserdata*、および*cbuserdataterm*をそれぞれ0、SQL_VARLEN_DATA、および0に設定します。</span><span class="sxs-lookup"><span data-stu-id="de78e-171">For the remaining two calls, set *eUserDataType* to 0, and set *cbIndicator*, *cbUserData*, and *cbUserDataTerm* to 0, SQL_VARLEN_DATA, and 0 respectively.</span></span> <span data-ttu-id="de78e-172">このプロシージャでは、5 つの列すべてをコピーします。それらの列のうち 3 つはカスタマイズされた形式でコピーされ、2 つは既定の形式でコピーされます。</span><span class="sxs-lookup"><span data-stu-id="de78e-172">This procedure copies all five columns, three with your customized format and two with the default format.</span></span>  
  
 <span data-ttu-id="de78e-173">*Cbindicator*の場合、大きな値の型が有効であることを示す値8。</span><span class="sxs-lookup"><span data-stu-id="de78e-173">For *cbIndicator*, a value of 8 to indicate a large value type is now valid.</span></span> <span data-ttu-id="de78e-174">フィールドにプレフィックスを指定し、そのフィールドに対応する列が新しい max 型である場合、この値は 8 にしか設定できません。</span><span class="sxs-lookup"><span data-stu-id="de78e-174">If the prefix is specified for a field whose corresponding column is a new max type, it can only be set to 8.</span></span> <span data-ttu-id="de78e-175">詳細については、「 [bcp_bind](bcp-bind.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de78e-175">For details, see [bcp_bind](bcp-bind.md).</span></span>  
  
 <span data-ttu-id="de78e-176">**Bcp_colfmt**を呼び出す前に、 **bcp_columns**関数を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="de78e-176">The **bcp_columns** function must be called before any calls to **bcp_colfmt**.</span></span>  
  
 <span data-ttu-id="de78e-177">ユーザーファイルの各列に対して**bcp_colfmt**を1回呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="de78e-177">You must call **bcp_colfmt** once for each column in the user file.</span></span>  
  
 <span data-ttu-id="de78e-178">ユーザーファイルの列に対して複数回**bcp_colfmt**を呼び出すと、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="de78e-178">Calling **bcp_colfmt** more than once for any user-file column causes an error.</span></span>  
  
 <span data-ttu-id="de78e-179">ユーザー ファイル内のすべてのデータを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルにコピーする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="de78e-179">You do not need to copy all data in a user file to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="de78e-180">列をスキップするには、列のデータの形式を指定し、 *Idxservercol*パラメーターを0に設定します。</span><span class="sxs-lookup"><span data-stu-id="de78e-180">To skip a column, specify the format of the data for the column, setting the *idxServerCol* parameter to 0.</span></span> <span data-ttu-id="de78e-181">列をスキップする場合でも、その列の型を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="de78e-181">If you want to skip a column, you must specify its type.</span></span>  
  
 <span data-ttu-id="de78e-182">[Bcp_writefmt](bcp-writefmt.md)関数は、書式指定を永続化するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="de78e-182">The [bcp_writefmt](bcp-writefmt.md) function can be used to persist the format specification.</span></span>  
  
## <a name="bcp_colfmt-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="de78e-183">bcp_colfmt による機能強化された日付と時刻のサポート</span><span class="sxs-lookup"><span data-stu-id="de78e-183">bcp_colfmt Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="de78e-184">日付型または時刻型に対して*Euserdatatype*パラメーターと共に使用される型の詳細については、「 [&#40;OLE DB および ODBC&#41;の拡張された日付/時刻型に対する一括コピーの変更](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de78e-184">For information aboutt he types used with the *eUserDataType* parameter for date/time types, see [Bulk Copy Changes for Enhanced Date and Time Types &#40;OLE DB and ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).</span></span>  
  
 <span data-ttu-id="de78e-185">詳細については、「[日付と時刻の機能強化 &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de78e-185">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de78e-186">参照</span><span class="sxs-lookup"><span data-stu-id="de78e-186">See Also</span></span>  
 [<span data-ttu-id="de78e-187">一括コピー関数</span><span class="sxs-lookup"><span data-stu-id="de78e-187">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
