---
title: srv_paramset (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramset
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramset
ms.assetid: 2a509206-a1b8-4b20-b0a2-ef680cef7bd8
author: rothja
ms.author: jroth
ms.openlocfilehash: 9ebe308e5e0c8fc24382582fb71db2f48c77541e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632475"
---
# <a name="srv_paramset-extended-stored-procedure-api"></a><span data-ttu-id="6117e-102">srv_paramset (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="6117e-102">srv_paramset (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="6117e-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="6117e-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="6117e-104">リモート ストアド プロシージャ呼び出しの戻りパラメーターの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="6117e-104">Sets the value of a remote stored procedure call return parameter.</span></span> <span data-ttu-id="6117e-105">この関数に代わって **srv_paramsetoutput** 関数が使用されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="6117e-105">This function has been superseded by the **srv_paramsetoutput** function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6117e-106">構文</span><span class="sxs-lookup"><span data-stu-id="6117e-106">Syntax</span></span>  
  
```  
  
int srv_paramset (  
SRV_PROC *  
srvproc  
,  
int  
n  
,   
void *  
data  
,  
int  
len   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="6117e-107">引数</span><span class="sxs-lookup"><span data-stu-id="6117e-107">Arguments</span></span>  
 <span data-ttu-id="6117e-108">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="6117e-108">*srvproc*</span></span>  
 <span data-ttu-id="6117e-109">特定のクライアント接続のためのハンドル (この場合は、リモート ストアド プロシージャ呼び出しを受け取るハンドル) である SRV_PROC 構造体を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="6117e-109">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="6117e-110">この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="6117e-110">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="6117e-111">*n*</span><span class="sxs-lookup"><span data-stu-id="6117e-111">*n*</span></span>  
 <span data-ttu-id="6117e-112">設定するパラメーターの番号を示します。</span><span class="sxs-lookup"><span data-stu-id="6117e-112">Indicates the number of the parameter to set.</span></span> <span data-ttu-id="6117e-113">最初のパラメーターは 1 です。</span><span class="sxs-lookup"><span data-stu-id="6117e-113">The first parameter is 1.</span></span>  
  
 <span data-ttu-id="6117e-114">*data*</span><span class="sxs-lookup"><span data-stu-id="6117e-114">*data*</span></span>  
 <span data-ttu-id="6117e-115">リモート ストアド プロシージャの戻りパラメーターとしてクライアントに返されるデータ値を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="6117e-115">Is a pointer to the data value to be sent back to the client as the remote stored procedure return parameter.</span></span>  
  
 <span data-ttu-id="6117e-116">*len*</span><span class="sxs-lookup"><span data-stu-id="6117e-116">*len*</span></span>  
 <span data-ttu-id="6117e-117">返されるデータの実際の長さを指定します。</span><span class="sxs-lookup"><span data-stu-id="6117e-117">Specifies the actual length of the data to be returned.</span></span> <span data-ttu-id="6117e-118">パラメーターのデータ型が固定長であり、NULL 値を許容しない型 (*srvbit* や *srvint1* など) である場合、*len* は無視されます。</span><span class="sxs-lookup"><span data-stu-id="6117e-118">If the data type of the parameter is of a constant length and does not allow null values (for example, *srvbit* or *srvint1*), *len* is ignored.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="6117e-119">戻り値</span><span class="sxs-lookup"><span data-stu-id="6117e-119">Returns</span></span>  
 <span data-ttu-id="6117e-120">パラメーター値が正しく設定された場合は SUCCEED を返し、それ以外の場合は FAIL を返します。</span><span class="sxs-lookup"><span data-stu-id="6117e-120">SUCCEED if the parameter value was successfully set; otherwise, FAIL.</span></span> <span data-ttu-id="6117e-121">FAIL を返すのは、現在のリモート ストアド プロシージャがない場合、*n* 番目のリモート ストアド プロシージャ パラメーターがない場合、パラメーターが戻りパラメーターでない場合、*len* 引数が無効である場合です。</span><span class="sxs-lookup"><span data-stu-id="6117e-121">FAIL is returned when there is no current remote stored procedure, when there is no *n*th remote stored procedure parameter, when the parameter is not a return parameter, and when the *len* argument is not legal.</span></span>  
  
 <span data-ttu-id="6117e-122">*len* が 0 である場合は、NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="6117e-122">If *len*is 0, it returns NULL.</span></span> <span data-ttu-id="6117e-123">*len* を 0 に設定する以外に、クライアントに NULL を返す方法はありません。</span><span class="sxs-lookup"><span data-stu-id="6117e-123">Setting *len* to 0 is the only way to return NULL to the client.</span></span>  
  
 <span data-ttu-id="6117e-124">パラメーターがデータ型の1つである場合、この関数は次の値を返し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="6117e-124">This function returns the following values, if the parameter is one of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] data types.</span></span>  
  
|<span data-ttu-id="6117e-125">新しいデータ型</span><span class="sxs-lookup"><span data-stu-id="6117e-125">New data types</span></span>|<span data-ttu-id="6117e-126">戻り値のデータ長</span><span class="sxs-lookup"><span data-stu-id="6117e-126">Return data length</span></span>|  
|--------------------|------------------------|  
|`BITN`|<span data-ttu-id="6117e-127">**NULL:** *len* = 0、data = IG、RET = 0</span><span class="sxs-lookup"><span data-stu-id="6117e-127">**NULL:** *len* = 0, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="6117e-128">**ZERO:** N/A</span><span class="sxs-lookup"><span data-stu-id="6117e-128">**ZERO:** N/A</span></span><br /><br /> <span data-ttu-id="6117e-129">**>= 255:** 該当なし</span><span class="sxs-lookup"><span data-stu-id="6117e-129">**>=255:** N/A</span></span><br /><br /> <span data-ttu-id="6117e-130">**<255:** 該当なし</span><span class="sxs-lookup"><span data-stu-id="6117e-130">**<255:** N/A</span></span>|  
|`BIGVARCHAR`|<span data-ttu-id="6117e-131">**NULL:** *len* = 0、data = IG、RET = 1</span><span class="sxs-lookup"><span data-stu-id="6117e-131">**NULL:** *len* = 0, data = IG, RET = 1</span></span><br /><br /> <span data-ttu-id="6117e-132">**ZERO:** *len* = IG、data = IG、RET = 0</span><span class="sxs-lookup"><span data-stu-id="6117e-132">**ZERO:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="6117e-133">**>=255:** *len* = max8k、data = valid、RET = 0</span><span class="sxs-lookup"><span data-stu-id="6117e-133">**>=255:** *len* = max8k, data = valid, RET = 0</span></span><br /><br /> <span data-ttu-id="6117e-134">**<255:** *len* = <8k、data = valid、RET = 1</span><span class="sxs-lookup"><span data-stu-id="6117e-134">**<255:** *len* = <8k, data = valid, RET = 1</span></span>|  
|`BIGCHAR`|<span data-ttu-id="6117e-135">**NULL:** *len* = 0、data = IG、RET = 1</span><span class="sxs-lookup"><span data-stu-id="6117e-135">**NULL:** *len* = 0, data = IG, RET = 1</span></span><br /><br /> <span data-ttu-id="6117e-136">**ZERO:** *len* = IG、data = IG、RET = 0</span><span class="sxs-lookup"><span data-stu-id="6117e-136">**ZERO:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="6117e-137">**>=255:** *len* = max8k、data = valid、RET = 0</span><span class="sxs-lookup"><span data-stu-id="6117e-137">**>=255:** *len* = max8k, data = valid, RET = 0</span></span><br /><br /> <span data-ttu-id="6117e-138">**<255:** *len* = <8k、data = valid、RET = 1</span><span class="sxs-lookup"><span data-stu-id="6117e-138">**<255:** *len* = <8k, data = valid, RET = 1</span></span>|  
|`BIGBINARY`|<span data-ttu-id="6117e-139">**NULL:** *len* = 0、data = IG、RET = 1</span><span class="sxs-lookup"><span data-stu-id="6117e-139">**NULL:** *len* = 0, data = IG, RET = 1</span></span><br /><br /> <span data-ttu-id="6117e-140">**ZERO:** *len* = IG、data = IG、RET = 0</span><span class="sxs-lookup"><span data-stu-id="6117e-140">**ZERO:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="6117e-141">**>=255:** *len* = max8k、data = valid、RET = 0</span><span class="sxs-lookup"><span data-stu-id="6117e-141">**>=255:** *len* = max8k, data = valid, RET = 0</span></span><br /><br /> <span data-ttu-id="6117e-142">**<255:** *len* = <8k、data = valid、RET = 1</span><span class="sxs-lookup"><span data-stu-id="6117e-142">**<255:** *len* = <8k, data = valid, RET = 1</span></span>|  
|`BIGVARBINARY`|<span data-ttu-id="6117e-143">**NULL:** *len* = 0、data = IG、RET = 1</span><span class="sxs-lookup"><span data-stu-id="6117e-143">**NULL:** *len* = 0, data = IG, RET = 1</span></span><br /><br /> <span data-ttu-id="6117e-144">**ZERO:** *len* = IG、data = IG、RET = 0</span><span class="sxs-lookup"><span data-stu-id="6117e-144">**ZERO:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="6117e-145">**>=255:** *len* = max8k、data = valid、RET = 0</span><span class="sxs-lookup"><span data-stu-id="6117e-145">**>=255:** *len* = max8k, data = valid, RET = 0</span></span><br /><br /> <span data-ttu-id="6117e-146">**<255:** *len* = <8k、data = valid、RET = 1</span><span class="sxs-lookup"><span data-stu-id="6117e-146">**<255:** *len* = <8k, data = valid, RET = 1</span></span>|  
|<span data-ttu-id="6117e-147">NCHAR</span><span class="sxs-lookup"><span data-stu-id="6117e-147">NCHAR</span></span>|<span data-ttu-id="6117e-148">**NULL:** *len* = 0、data = IG、RET = 1</span><span class="sxs-lookup"><span data-stu-id="6117e-148">**NULL:** *len* = 0, data = IG, RET = 1</span></span><br /><br /> <span data-ttu-id="6117e-149">**ZERO:** *len* = IG、data = IG、RET = 0</span><span class="sxs-lookup"><span data-stu-id="6117e-149">**ZERO:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="6117e-150">**>=255:** *len* = max8k、data = valid、RET = 0</span><span class="sxs-lookup"><span data-stu-id="6117e-150">**>=255:** *len* = max8k, data = valid, RET = 0</span></span><br /><br /> <span data-ttu-id="6117e-151">**<255:** *len* = <8k、data = valid、RET = 1</span><span class="sxs-lookup"><span data-stu-id="6117e-151">**<255:** *len* = <8k, data = valid, RET = 1</span></span>|  
|<span data-ttu-id="6117e-152">NVARCHAR</span><span class="sxs-lookup"><span data-stu-id="6117e-152">NVARCHAR</span></span>|<span data-ttu-id="6117e-153">**NULL:** *len* = 0、data = IG、RET = 1</span><span class="sxs-lookup"><span data-stu-id="6117e-153">**NULL:** *len* = 0, data = IG, RET = 1</span></span><br /><br /> <span data-ttu-id="6117e-154">**ZERO:** *len* = IG、data = IG、RET = 0</span><span class="sxs-lookup"><span data-stu-id="6117e-154">**ZERO:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="6117e-155">**>=255:** *len* = max8k、data = valid、RET = 0</span><span class="sxs-lookup"><span data-stu-id="6117e-155">**>=255:** *len* = max8k, data = valid, RET = 0</span></span><br /><br /> <span data-ttu-id="6117e-156">**<255:** *len* = <8k、data = valid、RET = 1</span><span class="sxs-lookup"><span data-stu-id="6117e-156">**<255:** *len* = <8k, data = valid, RET = 1</span></span>|  
|`NTEXT`|<span data-ttu-id="6117e-157">**NULL:** *len* = IG、data = IG、RET = 0</span><span class="sxs-lookup"><span data-stu-id="6117e-157">**NULL:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="6117e-158">**ZERO:** *len* = IG、data = IG、RET = 0</span><span class="sxs-lookup"><span data-stu-id="6117e-158">**ZERO:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="6117e-159">**>=255:** *len* = IG、data = IG、RET = 0</span><span class="sxs-lookup"><span data-stu-id="6117e-159">**>=255:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="6117e-160">\*\* \< 255:\*\* *len* = ig、data = ig、RET = 0</span><span class="sxs-lookup"><span data-stu-id="6117e-160">**\<255:** *len* = IG, data = IG, RET = 0</span></span>|  
|<span data-ttu-id="6117e-161">RET は srv_paramset の戻り値です。</span><span class="sxs-lookup"><span data-stu-id="6117e-161">RET = Return value of srv_paramset</span></span>||  
|<span data-ttu-id="6117e-162">IG は値が無視されることを示します。</span><span class="sxs-lookup"><span data-stu-id="6117e-162">IG = Value will be ignored</span></span>||  
|<span data-ttu-id="6117e-163">valid はデータを指す任意の有効なポインターを示します。</span><span class="sxs-lookup"><span data-stu-id="6117e-163">valid = Any valid pointer to data</span></span>||  
  
## <a name="remarks"></a><span data-ttu-id="6117e-164">解説</span><span class="sxs-lookup"><span data-stu-id="6117e-164">Remarks</span></span>  
 <span data-ttu-id="6117e-165">パラメーターには、リモート ストアド プロシージャを使用してクライアントとアプリケーションとの間で受け渡しされるデータが格納されます。</span><span class="sxs-lookup"><span data-stu-id="6117e-165">Parameters contain data passed between clients and the application with remote stored procedures.</span></span> <span data-ttu-id="6117e-166">クライアントは戻りパラメーターとして特定のパラメーターを指定できます。</span><span class="sxs-lookup"><span data-stu-id="6117e-166">The client can specify certain parameters as return parameters.</span></span> <span data-ttu-id="6117e-167">この戻りパラメーターには、Open Data Services サーバー アプリケーションがクライアントに返す値を格納することができます。</span><span class="sxs-lookup"><span data-stu-id="6117e-167">These return parameters can contain values that the Open Data Services server application passes back to the client.</span></span> <span data-ttu-id="6117e-168">戻りパラメーターの使用は、パラメーターの参照渡しに類似しています。</span><span class="sxs-lookup"><span data-stu-id="6117e-168">Using return parameters is analogous to passing parameters by reference.</span></span>  
  
 <span data-ttu-id="6117e-169">戻りパラメーターとして呼び出されていないパラメーターには、戻り値を設定できません。</span><span class="sxs-lookup"><span data-stu-id="6117e-169">You cannot set the return value for a parameter that wasn't invoked as a return parameter.</span></span> <span data-ttu-id="6117e-170">パラメーターがどのように呼び出されたかを判別するには **srv_paramstatus** を使用します。</span><span class="sxs-lookup"><span data-stu-id="6117e-170">You can use **srv_paramstatus** to determine how the parameter was invoked.</span></span>  
  
 <span data-ttu-id="6117e-171">この関数は、パラメーターの戻り値を設定するものであり、戻り値を実際にクライアントに返す役割はありません。</span><span class="sxs-lookup"><span data-stu-id="6117e-171">This function sets the return value for a parameter but it does not actually send the return value to the client.</span></span> <span data-ttu-id="6117e-172">**srv_paramset** に設定されているかどうかにかかわらず、すべての戻りパラメーターは、ステータス フラグ SRV_DONE_FINAL が設定された状態で **srv_senddone** が呼び出されると、自動的にクライアントに送信されます。</span><span class="sxs-lookup"><span data-stu-id="6117e-172">All return parameters, whether their return values have been set with **srv_paramset** or not, are automatically sent to the client when **srv_senddone** is called with the status flag SRV_DONE_FINAL set.</span></span>  
  
 <span data-ttu-id="6117e-173">パラメーターを指定してリモート ストアド プロシージャを呼び出す場合、パラメーターは名前で指定することも、名前を使用せずにその位置を指定して渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="6117e-173">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="6117e-174">名前によるパラメーター指定と位置によるパラメーター指定を混合してリモート ストアド プロシージャを呼び出すと、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="6117e-174">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="6117e-175">エラーが発生しても SRV_RPC ハンドラーは呼び出されますが、パラメーターが存在しないと見なされ、**srv_rpcparams** は 0 を返します。</span><span class="sxs-lookup"><span data-stu-id="6117e-175">The SRV_RPC handler is still called, but it appears as if there were no parameters, and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6117e-176">拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6117e-176">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="6117e-177">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6117e-177">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6117e-178">参照</span><span class="sxs-lookup"><span data-stu-id="6117e-178">See Also</span></span>  
 [<span data-ttu-id="6117e-179">srv_paramsetoutput &#40;拡張ストアド プロシージャ API&#41;</span><span class="sxs-lookup"><span data-stu-id="6117e-179">srv_paramsetoutput &#40;Extended Stored Procedure API&#41;</span></span>](srv-paramsetoutput-extended-stored-procedure-api.md)  
  
  
