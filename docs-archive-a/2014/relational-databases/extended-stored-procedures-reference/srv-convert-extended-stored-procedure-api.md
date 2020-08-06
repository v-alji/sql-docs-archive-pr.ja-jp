---
title: srv_convert (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_convert
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_convert
ms.assetid: 216b4a31-786e-4361-8a33-e5f6e9790f90
author: rothja
ms.author: jroth
ms.openlocfilehash: 30a0ea356f017ed3d1b3ecc85cf483b4553e120a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645074"
---
# <a name="srv_convert-extended-stored-procedure-api"></a><span data-ttu-id="6bb34-102">srv_convert (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="6bb34-102">srv_convert (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="6bb34-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="6bb34-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="6bb34-104">データを別のデータ型に変換します。</span><span class="sxs-lookup"><span data-stu-id="6bb34-104">Changes data from one data type to another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bb34-105">構文</span><span class="sxs-lookup"><span data-stu-id="6bb34-105">Syntax</span></span>  
  
```  
  
int srv_convert (  
SRV_PROC *  
srvproc  
,  
int  
srctype  
,  
void *  
src  
,  
DBINT  
srclen  
,  
int  
desttype  
,  
void *  
dest  
,  
DBINT  
destlen  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="6bb34-106">引数</span><span class="sxs-lookup"><span data-stu-id="6bb34-106">Arguments</span></span>  
 <span data-ttu-id="6bb34-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="6bb34-107">*srvproc*</span></span>  
 <span data-ttu-id="6bb34-108">特定のクライアント接続のためのハンドルである SRV_PROC 構造体を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="6bb34-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="6bb34-109">この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API で使用するすべての制御情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="6bb34-109">The structure contains all the control information that the Extended Stored Procedure API uses to manage communications and data between the application and the client.</span></span> <span data-ttu-id="6bb34-110">*srvproc* ハンドルが指定されている場合、エラーが発生すると、拡張ストアド プロシージャ API エラー ハンドラー関数に渡されます。</span><span class="sxs-lookup"><span data-stu-id="6bb34-110">If the *srvproc* handle is supplied, it is passed to the Extended Stored Procedure API error handler function when an error occurs.</span></span>  
  
 <span data-ttu-id="6bb34-111">*srctype*</span><span class="sxs-lookup"><span data-stu-id="6bb34-111">*srctype*</span></span>  
 <span data-ttu-id="6bb34-112">変換元データのデータ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="6bb34-112">Specifies the data type of the data to be converted.</span></span> <span data-ttu-id="6bb34-113">このパラメーターには、拡張ストアド プロシージャ API の任意のデータ型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="6bb34-113">This parameter can be any of the Extended Store Procedure API data types.</span></span>  
  
 <span data-ttu-id="6bb34-114">*src*</span><span class="sxs-lookup"><span data-stu-id="6bb34-114">*src*</span></span>  
 <span data-ttu-id="6bb34-115">変換元データへのポインターです。</span><span class="sxs-lookup"><span data-stu-id="6bb34-115">Is a pointer to the data to be converted.</span></span> <span data-ttu-id="6bb34-116">このパラメーターには、拡張ストアド プロシージャ API の任意のデータ型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="6bb34-116">This parameter can be any of the Extended Store Procedure API data types.</span></span>  
  
 <span data-ttu-id="6bb34-117">*srclen*</span><span class="sxs-lookup"><span data-stu-id="6bb34-117">*srclen*</span></span>  
 <span data-ttu-id="6bb34-118">変換元データの長さをバイト数で指定します。</span><span class="sxs-lookup"><span data-stu-id="6bb34-118">Specifies the length, in bytes, of the data to be converted.</span></span> <span data-ttu-id="6bb34-119">*srclen* が 0 である場合、**srv_convert** は出力先変数に NULL を格納します。</span><span class="sxs-lookup"><span data-stu-id="6bb34-119">If *srclen* is 0, **srv_convert** places a null value in the destination variable.</span></span> <span data-ttu-id="6bb34-120">0 以外の場合、固定長のデータ型ではこのパラメーターが無視され、変換元データが NULL であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="6bb34-120">Unless it is 0, this parameter is ignored for fixed-length data types, in which case the source data is assumed to be NULL.</span></span> <span data-ttu-id="6bb34-121">SRVCHAR データ型のデータの場合、長さが -1 であれば、文字列が NULL 終端であることを示します。</span><span class="sxs-lookup"><span data-stu-id="6bb34-121">For data of the SRVCHAR data type, a length of -1 indicates the string is null-terminated.</span></span>  
  
 <span data-ttu-id="6bb34-122">*desttype*</span><span class="sxs-lookup"><span data-stu-id="6bb34-122">*desttype*</span></span>  
 <span data-ttu-id="6bb34-123">変換先のデータ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="6bb34-123">Specifies the data type to convert the source to.</span></span> <span data-ttu-id="6bb34-124">このパラメーターには、拡張ストアド プロシージャ API の任意のデータ型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="6bb34-124">This parameter can be any of the Extended Store Procedure API data types.</span></span>  
  
 <span data-ttu-id="6bb34-125">*先*</span><span class="sxs-lookup"><span data-stu-id="6bb34-125">*dest*</span></span>  
 <span data-ttu-id="6bb34-126">変換したデータを受け取る出力先変数を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="6bb34-126">Is a pointer to the destination variable that receives converted data.</span></span> <span data-ttu-id="6bb34-127">このポインターが NULL である場合、ユーザーが指定したエラー ハンドラーがあれば **srv_convert** はそのエラー ハンドラーを呼び出し、-1 を返します。</span><span class="sxs-lookup"><span data-stu-id="6bb34-127">If this pointer is NULL, **srv_convert** calls the user-supplied error handler ,if any, and returns -1.</span></span>  
  
 <span data-ttu-id="6bb34-128">*desttype* が SRVDECIMAL または SRVNUMERIC である場合、*dest* パラメーターは DBNUMERIC 構造体または DBDECIMAL 構造体を指すポインターである必要があります。その際、構造体の有効桁数と小数点以下桁数のフィールドには、必要な値を設定しておきます。</span><span class="sxs-lookup"><span data-stu-id="6bb34-128">If *desttype* is SRVDECIMAL or SRVNUMERIC, the *dest* parameter must be a pointer to a DBNUMERIC or DBDECIMAL structure with the precision and scale fields of the structure already set to the desired values.</span></span> <span data-ttu-id="6bb34-129">既定の有効桁数を指定するには DEFAULTPRECISION を、既定の小数点以下桁数を指定するには DEFAULTSCALE を使用できます。</span><span class="sxs-lookup"><span data-stu-id="6bb34-129">You can use DEFAULTPRECISION to specify a default precision, and DEFAULTSCALE to specify a default scale.</span></span>  
  
 <span data-ttu-id="6bb34-130">*destlen*</span><span class="sxs-lookup"><span data-stu-id="6bb34-130">*destlen*</span></span>  
 <span data-ttu-id="6bb34-131">出力先変数の長さをバイト数で指定します。</span><span class="sxs-lookup"><span data-stu-id="6bb34-131">Specifies the length, in bytes, of the destination variable.</span></span> <span data-ttu-id="6bb34-132">固定長データ型の場合、このパラメーターは無視されます。</span><span class="sxs-lookup"><span data-stu-id="6bb34-132">This parameter is ignored for fixed-length data types.</span></span> <span data-ttu-id="6bb34-133">出力先変数が SRVCHAR 型である場合、*destlen* の値を出力先バッファー領域全体の長さにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bb34-133">For a destination variable of type SRVCHAR, the value of *destlen* must be the total length of the destination buffer space.</span></span> <span data-ttu-id="6bb34-134">SRVCHAR 型または SRVBINARY 型の出力先変数の長さが -1 であれば、十分な領域があることを示します。</span><span class="sxs-lookup"><span data-stu-id="6bb34-134">A length of -1 for a destination variable of type SRVCHAR or SRVBINARY indicates there is sufficient space available.</span></span> <span data-ttu-id="6bb34-135">出力先変数が *srvchar* 型である場合、長さを -1 にすると文字列が NULL 終端になります。</span><span class="sxs-lookup"><span data-stu-id="6bb34-135">For a destination variable of type *srvchar*, a length of -1 causes the character string to be null-terminated.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="6bb34-136">戻り値</span><span class="sxs-lookup"><span data-stu-id="6bb34-136">Returns</span></span>  
 <span data-ttu-id="6bb34-137">データ型の変換が成功した場合は、変換後のデータの長さをバイト数で返します。</span><span class="sxs-lookup"><span data-stu-id="6bb34-137">The length of the converted data, in bytes, if the data type conversion succeeds.</span></span> <span data-ttu-id="6bb34-138">**srv_convert** がサポートしていないデータ型への変換要求を受けた場合は、開発者の定義したエラー ハンドラーがあればそれを呼び出し、グローバル エラー番号を設定して -1 を返します。</span><span class="sxs-lookup"><span data-stu-id="6bb34-138">When **srv_convert** encounters a request for a conversion it does not support, it calls the developer-supplied error handler, if any, sets a global error number, and returns -1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6bb34-139">解説</span><span class="sxs-lookup"><span data-stu-id="6bb34-139">Remarks</span></span>  
 <span data-ttu-id="6bb34-140">**srv_willconvert** 関数は、特定の変換が可能かどうかを判断する関数です。</span><span class="sxs-lookup"><span data-stu-id="6bb34-140">The **srv_willconvert** function determines whether a particular conversion is allowed.</span></span>  
  
 <span data-ttu-id="6bb34-141">概数データ型 SRVFLT4 または SRVFLT8 への変換では、有効桁数の一部が失われることがあります。</span><span class="sxs-lookup"><span data-stu-id="6bb34-141">Converting to the approximate numeric data types SRVFLT4 or SRVFLT8 can result in some loss of precision.</span></span> <span data-ttu-id="6bb34-142">概数データ型 SRVFLT4 または SRVFLT8 から SRVCHAR または SRVTEXT への変換でも有効桁数の一部が失われることがあります。</span><span class="sxs-lookup"><span data-stu-id="6bb34-142">Converting from the approximate numeric data types SRVFLT4 or SRVFLT8 to SRVCHAR or SRVTEXT can also result in some loss of precision.</span></span>  
  
 <span data-ttu-id="6bb34-143">SRVFLT*x*、SRVINT*x*、SRVMONEY、SRVMONEY4、SRVDECIMAL、SRVNUMERIC のいずれかに変換した結果、数値が出力先の最大値より大きい場合はオーバーフロー、最小値より小さい場合はアンダーフローになることがあります。</span><span class="sxs-lookup"><span data-stu-id="6bb34-143">Converting to SRVFLT*x*, SRVINT*x*, SRVMONEY, SRVMONEY4, SRVDECIMAL, or SRVNUMERIC can result in overflow if the number is larger than the maximum value of the destination, or in underflow if the number is smaller than the minimum value of the destination.</span></span> <span data-ttu-id="6bb34-144">SRVCHAR または SRVTEXT への変換時にオーバーフローが発生した場合、変換後の値の最初の文字はエラーを示すアスタリスク (\*) なります。</span><span class="sxs-lookup"><span data-stu-id="6bb34-144">If overflow occurs when converting to SRVCHAR or SRVTEXT, the first character of the resulting value contains an asterisk (\*) to indicate the error.</span></span>  
  
 <span data-ttu-id="6bb34-145">SRVCHAR を SRVBINARY に変換する場合、文字列に先頭ビット 0 が含まれているかどうかに関係なく、**srv_convert** は SRVCHAR を 16 進数として解釈します。</span><span class="sxs-lookup"><span data-stu-id="6bb34-145">When converting SRVCHAR to SRVBINARY, **srv_convert** interprets SRVCHAR as hexadecimal, whether or not the string contains a leading 0.</span></span> <span data-ttu-id="6bb34-146">SRVBINARY から SRVCHAR に変換する場合、**srv_convert** は先頭ビット 0 のない 16 進数文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="6bb34-146">When converting SRVBINARY to SRVCHAR, **srv_convert** creates a hexadecimal string without a leading 0.</span></span> <span data-ttu-id="6bb34-147">それ以外の、SRVBINARY データ型からの変換または SRVBINARY データ型への変換ではビット コピーを忠実に行います。</span><span class="sxs-lookup"><span data-stu-id="6bb34-147">In all other cases, a conversion to or from the SRVBINARY data type is a straight bit-copy.</span></span>  
  
 <span data-ttu-id="6bb34-148">場合によっては、同じデータ型への変換が役立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="6bb34-148">In certain cases, it can be useful to convert a data type to itself.</span></span> <span data-ttu-id="6bb34-149">たとえば、*destlen* を -1 にして SRVCHAR から SRVCHAR に変換すると、文字列に NULL 終端が追加されます。</span><span class="sxs-lookup"><span data-stu-id="6bb34-149">For example, converting SRVCHAR to SRVCHAR with a *destlen* of -1 adds a null terminator to a string.</span></span>  
  
 <span data-ttu-id="6bb34-150">データ型および拡張ストアド プロシージャ API のデータ型変換について詳しくは、「[データ型 &#40;拡張ストアド プロシージャ API&#41;](data-types-extended-stored-procedure-api.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6bb34-150">For a description of data types and Extended Store Procedure API data type conversions, see [Data Types &#40;Extended Stored Procedure API&#41;](data-types-extended-stored-procedure-api.md).</span></span>  
  
 <span data-ttu-id="6bb34-151">**srv_convert** 関数は、次の理由で変換に失敗することがあります。</span><span class="sxs-lookup"><span data-stu-id="6bb34-151">The **srv_convert** function can fail for several reasons:</span></span>  
  
-   <span data-ttu-id="6bb34-152">要求された変換がサポートされていない。</span><span class="sxs-lookup"><span data-stu-id="6bb34-152">The requested conversion is not available.</span></span>  
  
-   <span data-ttu-id="6bb34-153">変換の結果、出力先変数で切り捨て、オーバーフロー、または有効桁数の損失が発生した。</span><span class="sxs-lookup"><span data-stu-id="6bb34-153">The conversion resulted in truncation, overflow, or loss of precision in the destination variable.</span></span>  
  
-   <span data-ttu-id="6bb34-154">文字列を数値データ型に変換するときに構文エラーが発生した。</span><span class="sxs-lookup"><span data-stu-id="6bb34-154">A syntax error occurred while converting a character string to a numeric data type.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6bb34-155">拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bb34-155">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="6bb34-156">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6bb34-156">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bb34-157">参照</span><span class="sxs-lookup"><span data-stu-id="6bb34-157">See Also</span></span>  
 <span data-ttu-id="6bb34-158">[srv_setutype &#40;拡張ストアドプロシージャ API&#41;](srv-setutype-extended-stored-procedure-api.md) </span><span class="sxs-lookup"><span data-stu-id="6bb34-158">[srv_setutype &#40;Extended Stored Procedure API&#41;](srv-setutype-extended-stored-procedure-api.md) </span></span>  
 [<span data-ttu-id="6bb34-159">srv_willconvert &#40;拡張ストアド プロシージャ API&#41;</span><span class="sxs-lookup"><span data-stu-id="6bb34-159">srv_willconvert &#40;Extended Stored Procedure API&#41;</span></span>](srv-willconvert-extended-stored-procedure-api.md)  
  
  
