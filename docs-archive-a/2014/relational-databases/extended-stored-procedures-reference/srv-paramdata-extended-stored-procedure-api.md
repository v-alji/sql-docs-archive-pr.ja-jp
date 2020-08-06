---
title: srv_paramdata (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramdata
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramdata
ms.assetid: 3104514d-b404-47c9-b6d7-928106384874
author: rothja
ms.author: jroth
ms.openlocfilehash: 092ca5b811a12c3e6b199a6041ce6e4f8e02f4b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643354"
---
# <a name="srv_paramdata-extended-stored-procedure-api"></a><span data-ttu-id="1a1f8-102">srv_paramdata (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="1a1f8-102">srv_paramdata (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="1a1f8-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="1a1f8-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="1a1f8-104">リモート ストアド プロシージャ呼び出しのパラメーターの値を返します。</span><span class="sxs-lookup"><span data-stu-id="1a1f8-104">Returns the value of a remote stored procedure call parameter.</span></span> <span data-ttu-id="1a1f8-105">この関数に代わって **srv_paraminfo** 関数が使用されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="1a1f8-105">This function has been superseded by the **srv_paraminfo** function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a1f8-106">構文</span><span class="sxs-lookup"><span data-stu-id="1a1f8-106">Syntax</span></span>  
  
```  
  
void * srv_paramdata (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="1a1f8-107">引数</span><span class="sxs-lookup"><span data-stu-id="1a1f8-107">Arguments</span></span>  
 <span data-ttu-id="1a1f8-108">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="1a1f8-108">*srvproc*</span></span>  
 <span data-ttu-id="1a1f8-109">特定のクライアント接続のためのハンドル (この場合は、リモート ストアド プロシージャ呼び出しを受け取るハンドル) である SRV_PROC 構造体を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="1a1f8-109">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="1a1f8-110">この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ ライブラリで使用する情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="1a1f8-110">The structure contains information the Extended Stored Procedure library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="1a1f8-111">*n*</span><span class="sxs-lookup"><span data-stu-id="1a1f8-111">*n*</span></span>  
 <span data-ttu-id="1a1f8-112">パラメーターの番号です。</span><span class="sxs-lookup"><span data-stu-id="1a1f8-112">Is the number of the parameter.</span></span> <span data-ttu-id="1a1f8-113">最初のパラメーターは 1 です。</span><span class="sxs-lookup"><span data-stu-id="1a1f8-113">The first parameter is number 1.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="1a1f8-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="1a1f8-114">Returns</span></span>  
 <span data-ttu-id="1a1f8-115">パラメーター値を指すポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="1a1f8-115">A pointer to the parameter value.</span></span> <span data-ttu-id="1a1f8-116">*n* 番目のパラメーターが NULL である場合、*n* 番目のパラメーターがない場合、またはリモート ストアド プロシージャがない場合には、NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="1a1f8-116">If the *n*th parameter is NULL, there is no *n*th parameter, or there is no remote stored procedure, returns NULL.</span></span> <span data-ttu-id="1a1f8-117">パラメーター値が文字列である場合、NULL 終端ではないこともあります。</span><span class="sxs-lookup"><span data-stu-id="1a1f8-117">If the parameter value is a string, it might not be null-terminated.</span></span> <span data-ttu-id="1a1f8-118">文字列の長さを判断するには、**srv_paramlen** を使用します。</span><span class="sxs-lookup"><span data-stu-id="1a1f8-118">Use **srv_paramlen** to determine the length of the string.</span></span>  
  
 <span data-ttu-id="1a1f8-119">パラメーターがデータ型の1つである場合、この関数は次の値を返し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="1a1f8-119">This function returns the following values, if the parameter is one of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types.</span></span> <span data-ttu-id="1a1f8-120">ポインター データには、データ型に対する有効なポインター (VP) か、NULL か、該当なし (N/A) かを示す情報と、ポインターが指すデータの内容が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1a1f8-120">Pointer data includes whether the pointer for the data type is valid (VP), NULL, or not applicable (N/A), and the contents of the data pointed to.</span></span>  
  
|<span data-ttu-id="1a1f8-121">新しいデータ型</span><span class="sxs-lookup"><span data-stu-id="1a1f8-121">New data types</span></span>|<span data-ttu-id="1a1f8-122">入力データ長</span><span class="sxs-lookup"><span data-stu-id="1a1f8-122">Input data length</span></span>|  
|--------------------|-----------------------|  
|<span data-ttu-id="1a1f8-123">BITN</span><span class="sxs-lookup"><span data-stu-id="1a1f8-123">BITN</span></span>|<span data-ttu-id="1a1f8-124">**NULL:** VP、NULL</span><span class="sxs-lookup"><span data-stu-id="1a1f8-124">**NULL:** VP, NULL</span></span><br /><br /> <span data-ttu-id="1a1f8-125">**ZERO:** VP、NULL</span><span class="sxs-lookup"><span data-stu-id="1a1f8-125">**ZERO:** VP, NULL</span></span><br /><br /> <span data-ttu-id="1a1f8-126">**>= 255:** 該当なし</span><span class="sxs-lookup"><span data-stu-id="1a1f8-126">**>=255:** N/A</span></span><br /><br /> <span data-ttu-id="1a1f8-127">**<255:** 該当なし</span><span class="sxs-lookup"><span data-stu-id="1a1f8-127">**<255:** N/A</span></span>|  
|<span data-ttu-id="1a1f8-128">BIGVARCHAR</span><span class="sxs-lookup"><span data-stu-id="1a1f8-128">BIGVARCHAR</span></span>|<span data-ttu-id="1a1f8-129">**NULL:** NULL、N/A</span><span class="sxs-lookup"><span data-stu-id="1a1f8-129">**NULL:** NULL, N/A</span></span><br /><br /> <span data-ttu-id="1a1f8-130">**ZERO:** VP、NULL</span><span class="sxs-lookup"><span data-stu-id="1a1f8-130">**ZERO:** VP, NULL</span></span><br /><br /> <span data-ttu-id="1a1f8-131">**>=255:** VP、255 文字</span><span class="sxs-lookup"><span data-stu-id="1a1f8-131">**>=255:** VP, 255 chars</span></span><br /><br /> <span data-ttu-id="1a1f8-132">**<255:** VP、実際のデータ</span><span class="sxs-lookup"><span data-stu-id="1a1f8-132">**<255:** VP, actual data</span></span>|  
|<span data-ttu-id="1a1f8-133">BIGCHAR</span><span class="sxs-lookup"><span data-stu-id="1a1f8-133">BIGCHAR</span></span>|<span data-ttu-id="1a1f8-134">**NULL:** NULL、N/A</span><span class="sxs-lookup"><span data-stu-id="1a1f8-134">**NULL:** NULL, N/A</span></span><br /><br /> <span data-ttu-id="1a1f8-135">**ZERO:** VP、255 個のスペース</span><span class="sxs-lookup"><span data-stu-id="1a1f8-135">**ZERO:** VP, 255 spaces</span></span><br /><br /> <span data-ttu-id="1a1f8-136">**>=255:** VP、255 文字</span><span class="sxs-lookup"><span data-stu-id="1a1f8-136">**>=255:** VP, 255 chars</span></span><br /><br /> <span data-ttu-id="1a1f8-137">**<255:** VP、実際のデータ + パディング (最大 255 文字)</span><span class="sxs-lookup"><span data-stu-id="1a1f8-137">**<255:** VP, actual data + padding (up to 255)</span></span>|  
|<span data-ttu-id="1a1f8-138">BIGBINARY</span><span class="sxs-lookup"><span data-stu-id="1a1f8-138">BIGBINARY</span></span>|<span data-ttu-id="1a1f8-139">**NULL:** NULL、N/A</span><span class="sxs-lookup"><span data-stu-id="1a1f8-139">**NULL:** NULL, N/A</span></span><br /><br /> <span data-ttu-id="1a1f8-140">**ZERO:** VP、255 0x00</span><span class="sxs-lookup"><span data-stu-id="1a1f8-140">**ZERO:** VP, 255 0x00</span></span><br /><br /> <span data-ttu-id="1a1f8-141">**>=255:** VP、255 バイト</span><span class="sxs-lookup"><span data-stu-id="1a1f8-141">**>=255:** VP, 255 bytes</span></span><br /><br /> <span data-ttu-id="1a1f8-142">**<255:** VP、実際のデータ + パディング (最大 255 文字)</span><span class="sxs-lookup"><span data-stu-id="1a1f8-142">**<255:** VP, actual data + padding (up to 255)</span></span>|  
|<span data-ttu-id="1a1f8-143">BIGVARBINARY</span><span class="sxs-lookup"><span data-stu-id="1a1f8-143">BIGVARBINARY</span></span>|<span data-ttu-id="1a1f8-144">**NULL:** NULL、N/A</span><span class="sxs-lookup"><span data-stu-id="1a1f8-144">**NULL:** NULL, N/A</span></span><br /><br /> <span data-ttu-id="1a1f8-145">**ZERO:** VP、0x00</span><span class="sxs-lookup"><span data-stu-id="1a1f8-145">**ZERO:** VP, 0x00</span></span><br /><br /> <span data-ttu-id="1a1f8-146">**>=255:** VP、255 バイト</span><span class="sxs-lookup"><span data-stu-id="1a1f8-146">**>=255:** VP, 255 bytes</span></span><br /><br /> <span data-ttu-id="1a1f8-147">**<255:** VP、実際のデータ</span><span class="sxs-lookup"><span data-stu-id="1a1f8-147">**<255:** VP, actual data</span></span>|  
|<span data-ttu-id="1a1f8-148">NCHAR</span><span class="sxs-lookup"><span data-stu-id="1a1f8-148">NCHAR</span></span>|<span data-ttu-id="1a1f8-149">**NULL:** NULL、N/A</span><span class="sxs-lookup"><span data-stu-id="1a1f8-149">**NULL:** NULL, N/A</span></span><br /><br /> <span data-ttu-id="1a1f8-150">**ZERO:** VP、255 個のスペース</span><span class="sxs-lookup"><span data-stu-id="1a1f8-150">**ZERO:** VP, 255 spaces</span></span><br /><br /> <span data-ttu-id="1a1f8-151">**>=255:** VP、255 文字</span><span class="sxs-lookup"><span data-stu-id="1a1f8-151">**>=255:** VP, 255 chars</span></span><br /><br /> <span data-ttu-id="1a1f8-152">**<255:** VP、実際のデータ + パディング (最大 255 文字)</span><span class="sxs-lookup"><span data-stu-id="1a1f8-152">**<255:** VP, actual data + padding (up to 255)</span></span>|  
|<span data-ttu-id="1a1f8-153">NVARCHAR</span><span class="sxs-lookup"><span data-stu-id="1a1f8-153">NVARCHAR</span></span>|<span data-ttu-id="1a1f8-154">**NULL:** NULL、N/A</span><span class="sxs-lookup"><span data-stu-id="1a1f8-154">**NULL:** NULL, N/A</span></span><br /><br /> <span data-ttu-id="1a1f8-155">**ZERO:** VP、NULL</span><span class="sxs-lookup"><span data-stu-id="1a1f8-155">**ZERO:** VP, NULL</span></span><br /><br /> <span data-ttu-id="1a1f8-156">**>=255:** VP、255 文字</span><span class="sxs-lookup"><span data-stu-id="1a1f8-156">**>=255:** VP, 255 chars</span></span><br /><br /> <span data-ttu-id="1a1f8-157">**<255:** VP、実際のデータ</span><span class="sxs-lookup"><span data-stu-id="1a1f8-157">**<255:** VP, actual data</span></span>|  
|<span data-ttu-id="1a1f8-158">NTEXT</span><span class="sxs-lookup"><span data-stu-id="1a1f8-158">NTEXT</span></span>|<span data-ttu-id="1a1f8-159">**NULL:** N/A</span><span class="sxs-lookup"><span data-stu-id="1a1f8-159">**NULL:** N/A</span></span><br /><br /> <span data-ttu-id="1a1f8-160">**ZERO:** N/A</span><span class="sxs-lookup"><span data-stu-id="1a1f8-160">**ZERO:** N/A</span></span><br /><br /> <span data-ttu-id="1a1f8-161">**>= 255:** 該当なし</span><span class="sxs-lookup"><span data-stu-id="1a1f8-161">**>=255:** N/A</span></span><br /><br /> <span data-ttu-id="1a1f8-162">\*\* \< 255:\*\* 該当なし</span><span class="sxs-lookup"><span data-stu-id="1a1f8-162">**\<255:** N/A</span></span>|  
  
 <span data-ttu-id="1a1f8-163">\*   データが NULL 終端ではないため、255 文字を超えるデータが切り捨てられても警告は発生しません。</span><span class="sxs-lookup"><span data-stu-id="1a1f8-163">\*   data is not null-terminated; no warning is issued on truncation for data >255 characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a1f8-164">解説</span><span class="sxs-lookup"><span data-stu-id="1a1f8-164">Remarks</span></span>  
 <span data-ttu-id="1a1f8-165">パラメーター名がわかっている場合は、**srv_paramnumber** でパラメーター番号を取得できます。</span><span class="sxs-lookup"><span data-stu-id="1a1f8-165">If you know the parameter name, you can use **srv_paramnumber** to get the parameter number.</span></span> <span data-ttu-id="1a1f8-166">パラメーターが NULL かどうかを判断する場合は、**srv_paramlen** を使用します。</span><span class="sxs-lookup"><span data-stu-id="1a1f8-166">To determine whether a parameter is NULL, use **srv_paramlen**.</span></span>  
  
 <span data-ttu-id="1a1f8-167">パラメーターを指定してリモート ストアド プロシージャを呼び出す場合、パラメーターは名前で指定することも、名前を使用せずにその位置を指定して渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="1a1f8-167">When a remote stored procedure call is made with parameters, the parameters can be passed by name or by position (unnamed).</span></span> <span data-ttu-id="1a1f8-168">名前によるパラメーター指定と位置によるパラメーター指定を混合してリモート ストアド プロシージャを呼び出すと、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="1a1f8-168">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="1a1f8-169">エラーが発生しても SRV_RPC ハンドラーは呼び出されますが、パラメーターが存在しないと見なされ、**srv_rpcparams** は 0 を返します。</span><span class="sxs-lookup"><span data-stu-id="1a1f8-169">If an error occurs, the SRV_RPC handler is still called, but it appears as if there were no parameters and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1a1f8-170">拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a1f8-170">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="1a1f8-171">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1a1f8-171">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a1f8-172">参照</span><span class="sxs-lookup"><span data-stu-id="1a1f8-172">See Also</span></span>  
 [<span data-ttu-id="1a1f8-173">srv_rpcparams &#40;拡張ストアド プロシージャ API&#41;</span><span class="sxs-lookup"><span data-stu-id="1a1f8-173">srv_rpcparams &#40;Extended Stored Procedure API&#41;</span></span>](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
