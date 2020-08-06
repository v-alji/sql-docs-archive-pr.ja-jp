---
title: srv_paramlen (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramlen
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramlen
ms.assetid: d1fe92ff-cad6-4396-8216-125e5642e81e
author: rothja
ms.author: jroth
ms.openlocfilehash: fc2a0fa7f8409767a2afaa9c4c621ea72732b701
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742130"
---
# <a name="srv_paramlen-extended-stored-procedure-api"></a><span data-ttu-id="95ec4-102">srv_paramlen (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="95ec4-102">srv_paramlen (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="95ec4-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="95ec4-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="95ec4-104">リモート ストアド プロシージャ呼び出しのパラメーターのデータ長を返します。</span><span class="sxs-lookup"><span data-stu-id="95ec4-104">Returns the data length of a remote stored procedure call parameter.</span></span> <span data-ttu-id="95ec4-105">この関数に代わって **srv_paraminfo** 関数が使用されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="95ec4-105">This function has been superseded by the **srv_paraminfo** function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95ec4-106">構文</span><span class="sxs-lookup"><span data-stu-id="95ec4-106">Syntax</span></span>  
  
```  
  
int srv_paramlen (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="95ec4-107">引数</span><span class="sxs-lookup"><span data-stu-id="95ec4-107">Arguments</span></span>  
 <span data-ttu-id="95ec4-108">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="95ec4-108">*srvproc*</span></span>  
 <span data-ttu-id="95ec4-109">特定のクライアント接続のためのハンドル (この場合は、リモート ストアド プロシージャ呼び出しを受け取るハンドル) である SRV_PROC 構造体を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="95ec4-109">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="95ec4-110">この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="95ec4-110">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="95ec4-111">*n*</span><span class="sxs-lookup"><span data-stu-id="95ec4-111">*n*</span></span>  
 <span data-ttu-id="95ec4-112">パラメーターの番号を示します。</span><span class="sxs-lookup"><span data-stu-id="95ec4-112">Indicates the number of the parameter.</span></span> <span data-ttu-id="95ec4-113">最初のパラメーターは 1 です。</span><span class="sxs-lookup"><span data-stu-id="95ec4-113">The first parameter is 1.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="95ec4-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="95ec4-114">Returns</span></span>  
 <span data-ttu-id="95ec4-115">パラメーター データの実際の長さをバイト数で返します。</span><span class="sxs-lookup"><span data-stu-id="95ec4-115">The actual length, in bytes, of the parameter data.</span></span> <span data-ttu-id="95ec4-116">*n* 番目のパラメーターがない場合、またはリモート ストアド プロシージャがない場合は、-1 を返します。</span><span class="sxs-lookup"><span data-stu-id="95ec4-116">If there is no *n*th parameter or there is no remote stored procedure, it returns -1.</span></span> <span data-ttu-id="95ec4-117">*n* 番目のパラメーターが NULL である場合は 0 を返します。</span><span class="sxs-lookup"><span data-stu-id="95ec4-117">If the *n*th parameter is NULL, it returns 0.</span></span>  
  
 <span data-ttu-id="95ec4-118">パラメーターが次のシステムデータ型のいずれかである場合、この関数は次の値を返し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="95ec4-118">This function returns the following values, if the parameter is one of the following [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] system data types.</span></span>  
  
|<span data-ttu-id="95ec4-119">新しいデータ型</span><span class="sxs-lookup"><span data-stu-id="95ec4-119">New data types</span></span>|<span data-ttu-id="95ec4-120">入力データ長</span><span class="sxs-lookup"><span data-stu-id="95ec4-120">Input data length</span></span>|  
|--------------------|-----------------------|  
|`BITN`|<span data-ttu-id="95ec4-121">**NULL:** 1</span><span class="sxs-lookup"><span data-stu-id="95ec4-121">**NULL:** 1</span></span><br /><br /> <span data-ttu-id="95ec4-122">**0:** 1</span><span class="sxs-lookup"><span data-stu-id="95ec4-122">**ZERO:** 1</span></span><br /><br /> <span data-ttu-id="95ec4-123">**>= 255:** 該当なし</span><span class="sxs-lookup"><span data-stu-id="95ec4-123">**>=255:** N/A</span></span><br /><br /> <span data-ttu-id="95ec4-124">**<255:** 該当なし</span><span class="sxs-lookup"><span data-stu-id="95ec4-124">**<255:** N/A</span></span>|  
|`BIGVARCHAR`|<span data-ttu-id="95ec4-125">**NULL:** 0</span><span class="sxs-lookup"><span data-stu-id="95ec4-125">**NULL:** 0</span></span><br /><br /> <span data-ttu-id="95ec4-126">**0:** 1</span><span class="sxs-lookup"><span data-stu-id="95ec4-126">**ZERO:** 1</span></span><br /><br /> <span data-ttu-id="95ec4-127">**>= 255:** 255</span><span class="sxs-lookup"><span data-stu-id="95ec4-127">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="95ec4-128">**<255:** 実際の *len*</span><span class="sxs-lookup"><span data-stu-id="95ec4-128">**<255:** actual *len*</span></span>|  
|`BIGCHAR`|<span data-ttu-id="95ec4-129">**NULL:** 0</span><span class="sxs-lookup"><span data-stu-id="95ec4-129">**NULL:** 0</span></span><br /><br /> <span data-ttu-id="95ec4-130">**ZERO:** 255</span><span class="sxs-lookup"><span data-stu-id="95ec4-130">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="95ec4-131">**>= 255:** 255</span><span class="sxs-lookup"><span data-stu-id="95ec4-131">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="95ec4-132">**<255:** 255</span><span class="sxs-lookup"><span data-stu-id="95ec4-132">**<255:** 255</span></span>|  
|`BIGBINARY`|<span data-ttu-id="95ec4-133">**NULL:** 0</span><span class="sxs-lookup"><span data-stu-id="95ec4-133">**NULL:** 0</span></span><br /><br /> <span data-ttu-id="95ec4-134">**ZERO:** 255</span><span class="sxs-lookup"><span data-stu-id="95ec4-134">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="95ec4-135">**>= 255:** 255</span><span class="sxs-lookup"><span data-stu-id="95ec4-135">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="95ec4-136">**<255:** 255</span><span class="sxs-lookup"><span data-stu-id="95ec4-136">**<255:** 255</span></span>|  
|`BIGVARBINARY`|<span data-ttu-id="95ec4-137">**NULL:** 0</span><span class="sxs-lookup"><span data-stu-id="95ec4-137">**NULL:** 0</span></span><br /><br /> <span data-ttu-id="95ec4-138">**0:** 1</span><span class="sxs-lookup"><span data-stu-id="95ec4-138">**ZERO:** 1</span></span><br /><br /> <span data-ttu-id="95ec4-139">**>= 255:** 255</span><span class="sxs-lookup"><span data-stu-id="95ec4-139">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="95ec4-140">**<255:** 実際の *len*</span><span class="sxs-lookup"><span data-stu-id="95ec4-140">**<255:** actual *len*</span></span>|  
|`NCHAR`|<span data-ttu-id="95ec4-141">**NULL:** 0</span><span class="sxs-lookup"><span data-stu-id="95ec4-141">**NULL:** 0</span></span><br /><br /> <span data-ttu-id="95ec4-142">**ZERO:** 255</span><span class="sxs-lookup"><span data-stu-id="95ec4-142">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="95ec4-143">**>= 255:** 255</span><span class="sxs-lookup"><span data-stu-id="95ec4-143">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="95ec4-144">**<255:** 255</span><span class="sxs-lookup"><span data-stu-id="95ec4-144">**<255:** 255</span></span>|  
|`NVARCHAR`|<span data-ttu-id="95ec4-145">**NULL:** 0</span><span class="sxs-lookup"><span data-stu-id="95ec4-145">**NULL:** 0</span></span><br /><br /> <span data-ttu-id="95ec4-146">**0:** 1</span><span class="sxs-lookup"><span data-stu-id="95ec4-146">**ZERO:** 1</span></span><br /><br /> <span data-ttu-id="95ec4-147">**>= 255:** 255</span><span class="sxs-lookup"><span data-stu-id="95ec4-147">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="95ec4-148">**<255:** 実際の *len*</span><span class="sxs-lookup"><span data-stu-id="95ec4-148">**<255:** actual *len*</span></span>|  
|`NTEXT`|<span data-ttu-id="95ec4-149">**NULL:** -1</span><span class="sxs-lookup"><span data-stu-id="95ec4-149">**NULL:** -1</span></span><br /><br /> <span data-ttu-id="95ec4-150">**ZERO:** -1</span><span class="sxs-lookup"><span data-stu-id="95ec4-150">**ZERO:** -1</span></span><br /><br /> <span data-ttu-id="95ec4-151">**>= 255:** -1</span><span class="sxs-lookup"><span data-stu-id="95ec4-151">**>=255:** -1</span></span><br /><br /> <span data-ttu-id="95ec4-152">**<255:** -1</span><span class="sxs-lookup"><span data-stu-id="95ec4-152">**<255:** -1</span></span>|  
  
 <span data-ttu-id="95ec4-153">\*   実際の *len* とは、マルチバイト文字列 (cch) の長さを示します</span><span class="sxs-lookup"><span data-stu-id="95ec4-153">\*   actual *len* = Length of multibyte character string (cch)</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95ec4-154">解説</span><span class="sxs-lookup"><span data-stu-id="95ec4-154">Remarks</span></span>  
 <span data-ttu-id="95ec4-155">リモート ストアド プロシージャ パラメーターのデータ長には、それぞれ実際値および最大値があります。</span><span class="sxs-lookup"><span data-stu-id="95ec4-155">Each remote stored procedure parameter has an actual and a maximum data length.</span></span> <span data-ttu-id="95ec4-156">NULL 値を許容しない標準固定長データ型では、長さの実際値と最大値は等しくなります。</span><span class="sxs-lookup"><span data-stu-id="95ec4-156">For standard fixed-length data types that do not allow null values, the actual and maximum lengths are the same.</span></span> <span data-ttu-id="95ec4-157">可変長データ型では、この 2 つの値が異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="95ec4-157">For variable-length data types, the lengths can vary.</span></span> <span data-ttu-id="95ec4-158">たとえば、`varchar(30)` として宣言したパラメーターには、長さが 10 バイトしかないデータを格納することが可能です。</span><span class="sxs-lookup"><span data-stu-id="95ec4-158">For example, a parameter declared as `varchar(30)` can have data that is only 10 bytes long.</span></span> <span data-ttu-id="95ec4-159">このパラメーターは実際の長さが 10 で、最大の長さが 30 です。</span><span class="sxs-lookup"><span data-stu-id="95ec4-159">The parameter's actual length is 10 and its maximum length is 30.</span></span> <span data-ttu-id="95ec4-160">**srv_paramlen** 関数は、リモート ストアド プロシージャの実際のデータ長をバイト数で取得します。</span><span class="sxs-lookup"><span data-stu-id="95ec4-160">The **srv_paramlen** function gets the actual data length, in bytes, of a remote stored procedure.</span></span> <span data-ttu-id="95ec4-161">パラメーターの最大のデータ長を取得するには、**srv_parammaxlen** を使用します。</span><span class="sxs-lookup"><span data-stu-id="95ec4-161">To obtain the maximum data length of a parameter, use **srv_parammaxlen**.</span></span>  
  
 <span data-ttu-id="95ec4-162">パラメーターを指定してリモート ストアド プロシージャを呼び出す場合、パラメーターは名前で指定することも、名前を使用せずにその位置を指定して渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="95ec4-162">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="95ec4-163">名前によるパラメーター指定と位置によるパラメーター指定を混合してリモート ストアド プロシージャを呼び出すと、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="95ec4-163">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="95ec4-164">SRV_RPC ハンドラーはまだ呼び出されていますが、パラメーターがなかったかのように見え、 **srv_rpcparams** 0 を返します。</span><span class="sxs-lookup"><span data-stu-id="95ec4-164">The SRV_RPC handler is still called, but it appears as if there were no parameters and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="95ec4-165">拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="95ec4-165">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="95ec4-166">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="95ec4-166">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95ec4-167">参照</span><span class="sxs-lookup"><span data-stu-id="95ec4-167">See Also</span></span>  
 <span data-ttu-id="95ec4-168">[srv_paraminfo &#40;拡張ストアドプロシージャ API&#41;](srv-paraminfo-extended-stored-procedure-api.md) </span><span class="sxs-lookup"><span data-stu-id="95ec4-168">[srv_paraminfo &#40;Extended Stored Procedure API&#41;](srv-paraminfo-extended-stored-procedure-api.md) </span></span>  
 [<span data-ttu-id="95ec4-169">srv_rpcparams &#40;拡張ストアド プロシージャ API&#41;</span><span class="sxs-lookup"><span data-stu-id="95ec4-169">srv_rpcparams &#40;Extended Stored Procedure API&#41;</span></span>](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
