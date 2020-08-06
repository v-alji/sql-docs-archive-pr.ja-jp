---
title: srv_describe (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_describe
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_describe
ms.assetid: 2115600e-5ce7-4be0-9cd3-a1dd1fab0729
author: rothja
ms.author: jroth
ms.openlocfilehash: 52a397b79f4fcecaa2ccacde7500cb852ae793fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645073"
---
# <a name="srv_describe-extended-stored-procedure-api"></a><span data-ttu-id="e062b-102">srv_describe (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="e062b-102">srv_describe (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="e062b-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="e062b-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="e062b-104">行内の特定の列について、列名および送信元と送信先のデータ型を定義します。</span><span class="sxs-lookup"><span data-stu-id="e062b-104">Defines the column name and source and destination data types for a specific column in a row.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e062b-105">構文</span><span class="sxs-lookup"><span data-stu-id="e062b-105">Syntax</span></span>  
  
```  
  
int srv_describe (  
SRV_PROC *  
srvproc  
,  
int  
colnumber  
,  
DBCHAR *  
column_name  
,  
int  
namelen  
,  
DBINT  
desttype  
,  
DBINT  
destlen  
,  
DBINT  
srctype  
,  
DBINT  
srclen  
,  
void *  
srcdata  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="e062b-106">引数</span><span class="sxs-lookup"><span data-stu-id="e062b-106">Arguments</span></span>  
 <span data-ttu-id="e062b-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="e062b-107">*srvproc*</span></span>  
 <span data-ttu-id="e062b-108">特定のクライアント接続のためのハンドル (ここでは、行を送信するクライアント) である SRV_PROC 構造体を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="e062b-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the client sending the row).</span></span> <span data-ttu-id="e062b-109">この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用するすべての情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="e062b-109">The structure contains all the information that the Extended Stored Procedure API library uses to manage communications and data between the application and the client.</span></span>  
  
 <span data-ttu-id="e062b-110">*colnumber*</span><span class="sxs-lookup"><span data-stu-id="e062b-110">*colnumber*</span></span>  
 <span data-ttu-id="e062b-111">現時点では、サポートされません。</span><span class="sxs-lookup"><span data-stu-id="e062b-111">Is currently not supported.</span></span> <span data-ttu-id="e062b-112">列は順番に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e062b-112">Columns must be described in order.</span></span> <span data-ttu-id="e062b-113">**srv_sendrow** を呼び出すには、事前にすべての列を記述しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="e062b-113">All columns must be described before **srv_sendrow** is called.</span></span>  
  
 <span data-ttu-id="e062b-114">*column_name*</span><span class="sxs-lookup"><span data-stu-id="e062b-114">*column_name*</span></span>  
 <span data-ttu-id="e062b-115">データが格納される列の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="e062b-115">Specifies the name of the column to which the data belongs.</span></span> <span data-ttu-id="e062b-116">列に名前を付けることは必須ではないので、このパラメーターは NULL になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e062b-116">This parameter can be NULL because a column is not required to have a name.</span></span>  
  
 <span data-ttu-id="e062b-117">*namelen*</span><span class="sxs-lookup"><span data-stu-id="e062b-117">*namelen*</span></span>  
 <span data-ttu-id="e062b-118">*column_name* の長さをバイト数で指定します。</span><span class="sxs-lookup"><span data-stu-id="e062b-118">Specifies the length, in bytes, of *column_name*.</span></span> <span data-ttu-id="e062b-119">*namelen* が SRV_NULLTERM である場合は、*column_name* を NULL で終端する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e062b-119">If *namelen* is SRV_NULLTERM, then *column_name* must be null-terminated.</span></span>  
  
 <span data-ttu-id="e062b-120">*desttype*</span><span class="sxs-lookup"><span data-stu-id="e062b-120">*desttype*</span></span>  
 <span data-ttu-id="e062b-121">送信先の行内の列のデータ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="e062b-121">Specifies the data type of the destination row column.</span></span> <span data-ttu-id="e062b-122">これはクライアントに送信するデータ型です。</span><span class="sxs-lookup"><span data-stu-id="e062b-122">This is the data type sent to the client.</span></span> <span data-ttu-id="e062b-123">データが NULL の場合でも、データ型を指定する必要があります。詳しく、「[データ型 &#40;拡張ストアド プロシージャ API&#41;](data-types-extended-stored-procedure-api.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e062b-123">The data type must be specified even if the data is NULL, for more information, see [Data Types &#40;Extended Stored Procedure API&#41;](data-types-extended-stored-procedure-api.md).</span></span>  
  
 <span data-ttu-id="e062b-124">*destlen*</span><span class="sxs-lookup"><span data-stu-id="e062b-124">*destlen*</span></span>  
 <span data-ttu-id="e062b-125">クライアントに送信するデータ長をバイト数で指定します。</span><span class="sxs-lookup"><span data-stu-id="e062b-125">Specifies the length, in bytes, of the data to be sent to the client.</span></span> <span data-ttu-id="e062b-126">NULL 値を許容しない固定長データ型の場合は、*destlen* が無視されます。</span><span class="sxs-lookup"><span data-stu-id="e062b-126">For fixed-length data types that do not allow null values, *destlen* is ignored.</span></span> <span data-ttu-id="e062b-127">可変長データ型と NULL 値を許容する固定長データ型の場合、*destlen* は送信先データで使用できる最大長を指定します。</span><span class="sxs-lookup"><span data-stu-id="e062b-127">For variable-length data types and fixed-length data types that allow null values, *destlen* specifies the maximum length the destination data can be.</span></span>  
  
 <span data-ttu-id="e062b-128">*srctype*</span><span class="sxs-lookup"><span data-stu-id="e062b-128">*srctype*</span></span>  
 <span data-ttu-id="e062b-129">ソース データのデータ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="e062b-129">Specifies the data type of the source data.</span></span>  
  
 <span data-ttu-id="e062b-130">*srclen*</span><span class="sxs-lookup"><span data-stu-id="e062b-130">*srclen*</span></span>  
 <span data-ttu-id="e062b-131">ソース データの長さをバイト数で指定します。</span><span class="sxs-lookup"><span data-stu-id="e062b-131">Specifies the length, in bytes, of the source data.</span></span> <span data-ttu-id="e062b-132">固定長データ型の場合、この値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="e062b-132">This value is ignored for fixed-length data types.</span></span>  
  
 <span data-ttu-id="e062b-133">*srcdata*</span><span class="sxs-lookup"><span data-stu-id="e062b-133">*srcdata*</span></span>  
 <span data-ttu-id="e062b-134">特定の列に対応するソース データ アドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="e062b-134">Provides the source data address for a particular column.</span></span> <span data-ttu-id="e062b-135">**srv_sendrow** は呼び出されると、*colnumber* のデータを *srcdata* で探します。</span><span class="sxs-lookup"><span data-stu-id="e062b-135">When **srv_sendrow** is called, it looks for the data for *colnumber* at *srcdata*.</span></span> <span data-ttu-id="e062b-136">このため、**srv_sendrow** を呼び出す前にこの引数を解放しないでください。</span><span class="sxs-lookup"><span data-stu-id="e062b-136">Therefore it should not be freed before a call to **srv_sendrow**.</span></span> <span data-ttu-id="e062b-137">ソース データ アドレスは、**srv_sendrow** の呼び出しと呼び出しの間に **srv_setcoldata** を使用して変更できます。</span><span class="sxs-lookup"><span data-stu-id="e062b-137">The source data address can be changed between calls to **srv_sendrow** by using **srv_setcoldata**.</span></span> <span data-ttu-id="e062b-138">別に **srv_setcoldata** を呼び出して列データを置き換えるか、**srv_senddone** を呼び出すまでは、*srcdata* に割り当てたメモリを解放しないでください。</span><span class="sxs-lookup"><span data-stu-id="e062b-138">Memory allocated for *srcdata* should not be freed until the column data is replaced by another call to **srv_setcoldata**, or until **srv_senddone** is called.</span></span>  
  
 <span data-ttu-id="e062b-139">*desttype* が SRVDECIMAL または SRVNUMERIC である場合、*srcdata* パラメーターは DBNUMERIC 構造体または DBDECIMAL 構造体を指すポインターである必要があります。そのとき、構造体の有効桁数と小数点以下桁数のフィールドには、必要な値を設定しておきます。</span><span class="sxs-lookup"><span data-stu-id="e062b-139">If *desttype* is SRVDECIMAL or SRVNUMERIC, the *srcdata* parameter must be a pointer to a DBNUMERIC or DBDECIMAL structure with the precision and scale fields of the structure already set to the values you want.</span></span> <span data-ttu-id="e062b-140">既定の有効桁数を指定するには DEFAULTPRECISION を、既定の小数点以下桁数を指定するには DEFAULTSCALE を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e062b-140">You can use DEFAULTPRECISION to specify a default precision, and DEFAULTSCALE to specify a default scale.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="e062b-141">戻り値</span><span class="sxs-lookup"><span data-stu-id="e062b-141">Returns</span></span>  
 <span data-ttu-id="e062b-142">記述された列の番号を返します。</span><span class="sxs-lookup"><span data-stu-id="e062b-142">The number of the column described.</span></span> <span data-ttu-id="e062b-143">最初の列は列 1 です。</span><span class="sxs-lookup"><span data-stu-id="e062b-143">The first column is column 1.</span></span> <span data-ttu-id="e062b-144">エラーが発生すると 0 を返します。</span><span class="sxs-lookup"><span data-stu-id="e062b-144">If an error occurs, returns 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e062b-145">解説</span><span class="sxs-lookup"><span data-stu-id="e062b-145">Remarks</span></span>  
 <span data-ttu-id="e062b-146">**srv_sendrow** を初めて呼び出す前に、行内の各列に対して 1 回ずつ **srv_describe** 関数を呼び出しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="e062b-146">The **srv_describe** function must be called once for each column in the row before the first call to **srv_sendrow**.</span></span> <span data-ttu-id="e062b-147">行内の列は任意の順で記述できます。</span><span class="sxs-lookup"><span data-stu-id="e062b-147">The columns of a row can be described in any order.</span></span>  
  
 <span data-ttu-id="e062b-148">完全な結果セットの送信が完了する前に行内の各列のソース データの位置および長さを変更するには、それぞれ **srv_setcoldata** と **srv_setcollen** を使用します。</span><span class="sxs-lookup"><span data-stu-id="e062b-148">To change the location and length of the source data in column rows before the complete result set has been sent, use **srv_setcoldata** and **srv_setcollen**, respectively.</span></span>  
  
 <span data-ttu-id="e062b-149">データ型および拡張ストアド プロシージャ API のデータ型変換について詳しくは、「[データ型 &#40;拡張ストアド プロシージャ API&#41;](data-types-extended-stored-procedure-api.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e062b-149">For a description of data types and Extended Store Procedure API data type conversions, see[Data Types &#40;Extended Stored Procedure API&#41;](data-types-extended-stored-procedure-api.md).</span></span>  
  
 <span data-ttu-id="e062b-150">アプリケーションで使用する列名が Unicode である場合は、**srv_describe** を呼び出す前に、列名をサーバーのマルチバイト コード ページに変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e062b-150">If the column name in your application is in Unicode, you need to convert it to the multibyte code page of the server before calling **srv_describe**.</span></span> <span data-ttu-id="e062b-151">詳細については、「 [Unicode データおよびサーバーコードページ](../extended-stored-procedures-programming/unicode-data-and-server-code-pages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e062b-151">For more information, see [Unicode Data and Server Code Pages](../extended-stored-procedures-programming/unicode-data-and-server-code-pages.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e062b-152">拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e062b-152">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="e062b-153">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e062b-153">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e062b-154">参照</span><span class="sxs-lookup"><span data-stu-id="e062b-154">See Also</span></span>  
 <span data-ttu-id="e062b-155">[srv_sendrow &#40;拡張ストアドプロシージャ API&#41;](srv-sendrow-extended-stored-procedure-api.md) </span><span class="sxs-lookup"><span data-stu-id="e062b-155">[srv_sendrow &#40;Extended Stored Procedure API&#41;](srv-sendrow-extended-stored-procedure-api.md) </span></span>  
 <span data-ttu-id="e062b-156">[srv_setutype &#40;拡張ストアドプロシージャ API&#41;](srv-setutype-extended-stored-procedure-api.md) </span><span class="sxs-lookup"><span data-stu-id="e062b-156">[srv_setutype &#40;Extended Stored Procedure API&#41;](srv-setutype-extended-stored-procedure-api.md) </span></span>  
 [<span data-ttu-id="e062b-157">srv_setcoldata &#40;拡張ストアド プロシージャ API&#41;</span><span class="sxs-lookup"><span data-stu-id="e062b-157">srv_setcoldata &#40;Extended Stored Procedure API&#41;</span></span>](srv-setcoldata-extended-stored-procedure-api.md)  
  
  
