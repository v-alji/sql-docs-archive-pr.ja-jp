---
title: srv_parammaxlen (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_parammaxlen
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_parammaxlen
ms.assetid: 49bfc29d-f76a-4963-b0e6-b8532dfda850
author: rothja
ms.author: jroth
ms.openlocfilehash: b289743b3de4b115a67a029dcc0261854ee3a40b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742126"
---
# <a name="srv_parammaxlen-extended-stored-procedure-api"></a><span data-ttu-id="060bb-102">srv_parammaxlen (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="060bb-102">srv_parammaxlen (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="060bb-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="060bb-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="060bb-104">リモート ストアド プロシージャ呼び出しのパラメーターの最大データ長を返します。</span><span class="sxs-lookup"><span data-stu-id="060bb-104">Returns the maximum data length of a remote stored procedure call parameter.</span></span> <span data-ttu-id="060bb-105">この関数に代わって **srv_paraminfo** 関数が使用されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="060bb-105">This function has been superseded by the **srv_paraminfo** function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="060bb-106">構文</span><span class="sxs-lookup"><span data-stu-id="060bb-106">Syntax</span></span>  
  
```  
  
int srv_parammaxlen (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="060bb-107">引数</span><span class="sxs-lookup"><span data-stu-id="060bb-107">Arguments</span></span>  
 <span data-ttu-id="060bb-108">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="060bb-108">*srvproc*</span></span>  
 <span data-ttu-id="060bb-109">特定のクライアント接続のためのハンドル (この場合は、リモート ストアド プロシージャ呼び出しを受け取るハンドル) である SRV_PROC 構造体を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="060bb-109">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="060bb-110">この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="060bb-110">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="060bb-111">*n*</span><span class="sxs-lookup"><span data-stu-id="060bb-111">*n*</span></span>  
 <span data-ttu-id="060bb-112">パラメーターの番号を示します。</span><span class="sxs-lookup"><span data-stu-id="060bb-112">Indicates the number of the parameter.</span></span> <span data-ttu-id="060bb-113">最初のパラメーターは 1 です。</span><span class="sxs-lookup"><span data-stu-id="060bb-113">The first parameter is 1.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="060bb-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="060bb-114">Returns</span></span>  
 <span data-ttu-id="060bb-115">パラメーター データの最大長をバイト数で返します。</span><span class="sxs-lookup"><span data-stu-id="060bb-115">The maximum length, in bytes, of the parameter data.</span></span> <span data-ttu-id="060bb-116">*n* 番目のパラメーターがない場合、またはリモート ストアド プロシージャがない場合は、-1 を返します。</span><span class="sxs-lookup"><span data-stu-id="060bb-116">If there is no *n*th parameter or if there is no remote stored procedure, it returns -1.</span></span>  
  
 <span data-ttu-id="060bb-117">パラメーターが次のいずれかのデータ型である場合、この関数は次の値を返し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="060bb-117">This function returns the following values, if the parameter is one of the following [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types.</span></span>  
  
|<span data-ttu-id="060bb-118">新しいデータ型</span><span class="sxs-lookup"><span data-stu-id="060bb-118">New data types</span></span>|<span data-ttu-id="060bb-119">入力データ長</span><span class="sxs-lookup"><span data-stu-id="060bb-119">Input data length</span></span>|  
|--------------------|-----------------------|  
|`BITN`|<span data-ttu-id="060bb-120">**NULL:** 1</span><span class="sxs-lookup"><span data-stu-id="060bb-120">**NULL:** 1</span></span><br /><br /> <span data-ttu-id="060bb-121">**0:** 1</span><span class="sxs-lookup"><span data-stu-id="060bb-121">**ZERO:** 1</span></span><br /><br /> <span data-ttu-id="060bb-122">**>= 255:** 該当なし</span><span class="sxs-lookup"><span data-stu-id="060bb-122">**>=255:** N/A</span></span><br /><br /> <span data-ttu-id="060bb-123">**<255:** 該当なし</span><span class="sxs-lookup"><span data-stu-id="060bb-123">**<255:** N/A</span></span>|  
|`BIGVARCHAR`|<span data-ttu-id="060bb-124">**NULL:** 255</span><span class="sxs-lookup"><span data-stu-id="060bb-124">**NULL:** 255</span></span><br /><br /> <span data-ttu-id="060bb-125">**ZERO:** 255</span><span class="sxs-lookup"><span data-stu-id="060bb-125">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="060bb-126">**>= 255:** 255</span><span class="sxs-lookup"><span data-stu-id="060bb-126">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="060bb-127">**<255:** 255</span><span class="sxs-lookup"><span data-stu-id="060bb-127">**<255:** 255</span></span>|  
|`BIGCHAR`|<span data-ttu-id="060bb-128">**NULL:** 255</span><span class="sxs-lookup"><span data-stu-id="060bb-128">**NULL:** 255</span></span><br /><br /> <span data-ttu-id="060bb-129">**ZERO:** 255</span><span class="sxs-lookup"><span data-stu-id="060bb-129">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="060bb-130">**>= 255:** 255</span><span class="sxs-lookup"><span data-stu-id="060bb-130">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="060bb-131">**<255:** 255</span><span class="sxs-lookup"><span data-stu-id="060bb-131">**<255:** 255</span></span>|  
|`BIGBINARY`|<span data-ttu-id="060bb-132">**NULL:** 255</span><span class="sxs-lookup"><span data-stu-id="060bb-132">**NULL:** 255</span></span><br /><br /> <span data-ttu-id="060bb-133">**ZERO:** 255</span><span class="sxs-lookup"><span data-stu-id="060bb-133">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="060bb-134">**>= 255:** 255</span><span class="sxs-lookup"><span data-stu-id="060bb-134">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="060bb-135">**<255:** 255</span><span class="sxs-lookup"><span data-stu-id="060bb-135">**<255:** 255</span></span>|  
|`BIGVARBINARY`|<span data-ttu-id="060bb-136">**NULL:** 255</span><span class="sxs-lookup"><span data-stu-id="060bb-136">**NULL:** 255</span></span><br /><br /> <span data-ttu-id="060bb-137">**ZERO:** 255</span><span class="sxs-lookup"><span data-stu-id="060bb-137">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="060bb-138">**>= 255:** 255</span><span class="sxs-lookup"><span data-stu-id="060bb-138">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="060bb-139">**<255:** 255</span><span class="sxs-lookup"><span data-stu-id="060bb-139">**<255:** 255</span></span>|  
|`NCHAR`|<span data-ttu-id="060bb-140">**NULL:** 255</span><span class="sxs-lookup"><span data-stu-id="060bb-140">**NULL:** 255</span></span><br /><br /> <span data-ttu-id="060bb-141">**ZERO:** 255</span><span class="sxs-lookup"><span data-stu-id="060bb-141">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="060bb-142">**>= 255:** 255</span><span class="sxs-lookup"><span data-stu-id="060bb-142">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="060bb-143">**<255:** 255</span><span class="sxs-lookup"><span data-stu-id="060bb-143">**<255:** 255</span></span>|  
|`NVARCHAR`|<span data-ttu-id="060bb-144">**NULL:** 255</span><span class="sxs-lookup"><span data-stu-id="060bb-144">**NULL:** 255</span></span><br /><br /> <span data-ttu-id="060bb-145">**ZERO:** 255</span><span class="sxs-lookup"><span data-stu-id="060bb-145">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="060bb-146">**>= 255:** 255</span><span class="sxs-lookup"><span data-stu-id="060bb-146">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="060bb-147">**<255:** 255</span><span class="sxs-lookup"><span data-stu-id="060bb-147">**<255:** 255</span></span>|  
|`NTEXT`|<span data-ttu-id="060bb-148">**NULL:** -1</span><span class="sxs-lookup"><span data-stu-id="060bb-148">**NULL:** -1</span></span><br /><br /> <span data-ttu-id="060bb-149">**ZERO:** -1</span><span class="sxs-lookup"><span data-stu-id="060bb-149">**ZERO:** -1</span></span><br /><br /> <span data-ttu-id="060bb-150">**>= 255:** -1</span><span class="sxs-lookup"><span data-stu-id="060bb-150">**>=255:** -1</span></span><br /><br /> <span data-ttu-id="060bb-151">\*\* \< 255:\*\* -1</span><span class="sxs-lookup"><span data-stu-id="060bb-151">**\<255:** -1</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="060bb-152">解説</span><span class="sxs-lookup"><span data-stu-id="060bb-152">Remarks</span></span>  
 <span data-ttu-id="060bb-153">リモート ストアド プロシージャ パラメーターのデータ長には、それぞれ実際値および最大値があります。</span><span class="sxs-lookup"><span data-stu-id="060bb-153">Each remote stored procedure parameter has an actual and a maximum data length.</span></span> <span data-ttu-id="060bb-154">NULL 値を許容しない標準固定長データ型では、長さの実際値と最大値は等しくなります。</span><span class="sxs-lookup"><span data-stu-id="060bb-154">For standard fixed-length data types that do not allow null values, the actual and maximum lengths are the same.</span></span> <span data-ttu-id="060bb-155">可変長データ型では、この 2 つの値が異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="060bb-155">For variable-length data types, the lengths can vary.</span></span> <span data-ttu-id="060bb-156">たとえば、**varchar(30)** として宣言したパラメーターには、長さが 10 バイトしかないデータを格納することが可能です。</span><span class="sxs-lookup"><span data-stu-id="060bb-156">For example, a parameter declared as **varchar(30)** can have data that is only 10 bytes long.</span></span> <span data-ttu-id="060bb-157">このパラメーターは実際の長さが 10 で、最大の長さが 30 です。</span><span class="sxs-lookup"><span data-stu-id="060bb-157">The parameter's actual length is 10 and its maximum length is 30.</span></span> <span data-ttu-id="060bb-158">**srv_parammaxlen** 関数は、リモート ストアド プロシージャの最大データ長を取得します。</span><span class="sxs-lookup"><span data-stu-id="060bb-158">The **srv_parammaxlen** function gets the maximum data length of a remote stored procedure.</span></span> <span data-ttu-id="060bb-159">パラメーターの実際のデータ長を取得するには、**srv_paramlen** を使用します。</span><span class="sxs-lookup"><span data-stu-id="060bb-159">To obtain the actual length of a parameter, use **srv_paramlen**.</span></span>  
  
 <span data-ttu-id="060bb-160">パラメーターを指定してリモート ストアド プロシージャを呼び出す場合、パラメーターは名前で指定することも、名前を使用せずにその位置を指定して渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="060bb-160">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="060bb-161">名前によるパラメーター指定と位置によるパラメーター指定を混合してリモート ストアド プロシージャを呼び出すと、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="060bb-161">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="060bb-162">エラーが発生しても SRV_RPC ハンドラーは呼び出されますが、パラメーターが存在しないと見なされ、**srv_rpcparams** は 0 を返します。</span><span class="sxs-lookup"><span data-stu-id="060bb-162">The SRV_RPC handler is still called, but it appears as if there were no parameters, and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="060bb-163">拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="060bb-163">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="060bb-164">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="060bb-164">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="060bb-165">参照</span><span class="sxs-lookup"><span data-stu-id="060bb-165">See Also</span></span>  
 <span data-ttu-id="060bb-166">[srv_paraminfo &#40;拡張ストアドプロシージャ API&#41;](srv-paraminfo-extended-stored-procedure-api.md) </span><span class="sxs-lookup"><span data-stu-id="060bb-166">[srv_paraminfo &#40;Extended Stored Procedure API&#41;](srv-paraminfo-extended-stored-procedure-api.md) </span></span>  
 [<span data-ttu-id="060bb-167">srv_rpcparams &#40;拡張ストアド プロシージャ API&#41;</span><span class="sxs-lookup"><span data-stu-id="060bb-167">srv_rpcparams &#40;Extended Stored Procedure API&#41;</span></span>](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
