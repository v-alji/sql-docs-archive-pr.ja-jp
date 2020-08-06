---
title: srv_paramnumber (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramnumber
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramnumber
ms.assetid: d7a6dbff-71d9-4297-8a4f-bfd2876fe204
author: rothja
ms.author: jroth
ms.openlocfilehash: 1e621101c909ef251c40f38713e438d8e40d08a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643351"
---
# <a name="srv_paramnumber-extended-stored-procedure-api"></a><span data-ttu-id="f6627-102">srv_paramnumber (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="f6627-102">srv_paramnumber (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="f6627-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="f6627-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="f6627-104">リモート ストアド プロシージャ呼び出しのパラメーターの番号を返します。</span><span class="sxs-lookup"><span data-stu-id="f6627-104">Returns the number of a remote stored procedure call parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6627-105">構文</span><span class="sxs-lookup"><span data-stu-id="f6627-105">Syntax</span></span>  
  
```  
  
int srv_paramnumber (  
SRV_PROC *  
srvproc  
,  
DBCHAR *  
name  
,   
int  
namelen   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="f6627-106">引数</span><span class="sxs-lookup"><span data-stu-id="f6627-106">Arguments</span></span>  
 <span data-ttu-id="f6627-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="f6627-107">*srvproc*</span></span>  
 <span data-ttu-id="f6627-108">特定のクライアント接続のためのハンドル (この場合は、リモート ストアド プロシージャ呼び出しを受け取るハンドル) である SRV_PROC 構造体を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="f6627-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="f6627-109">この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="f6627-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="f6627-110">*name*</span><span class="sxs-lookup"><span data-stu-id="f6627-110">*name*</span></span>  
 <span data-ttu-id="f6627-111">パラメーターの *name* を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="f6627-111">Is a pointer to the parameter *name*.</span></span>  
  
 <span data-ttu-id="f6627-112">*namelen*</span><span class="sxs-lookup"><span data-stu-id="f6627-112">*namelen*</span></span>  
 <span data-ttu-id="f6627-113">*name* の長さです。</span><span class="sxs-lookup"><span data-stu-id="f6627-113">Is the length of *name*.</span></span> <span data-ttu-id="f6627-114">*name* が NULL 終端である場合は、*namelen* を SRV_NULLTERM に設定します。</span><span class="sxs-lookup"><span data-stu-id="f6627-114">If *name* is null-terminated, set *namelen* to SRV_NULLTERM.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="f6627-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="f6627-115">Returns</span></span>  
 <span data-ttu-id="f6627-116">指定されたパラメーターのパラメーター番号を返します。</span><span class="sxs-lookup"><span data-stu-id="f6627-116">The parameter number of the named parameter.</span></span> <span data-ttu-id="f6627-117">最初のパラメーターは 1 です。</span><span class="sxs-lookup"><span data-stu-id="f6627-117">The first parameter is 1.</span></span> <span data-ttu-id="f6627-118">*name* という名前のパラメーターがない場合、またはリモート ストアド プロシージャがない場合は、0 を返し、メッセージを生成します。</span><span class="sxs-lookup"><span data-stu-id="f6627-118">If there is no parameter named *name* or no remote stored procedure, 0 is returned and a message is generated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6627-119">解説</span><span class="sxs-lookup"><span data-stu-id="f6627-119">Remarks</span></span>  
 <span data-ttu-id="f6627-120">パラメーターを指定してリモート ストアド プロシージャを呼び出す場合、パラメーターは名前で指定することも、名前を使用せずにその位置を指定して渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="f6627-120">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="f6627-121">名前によるパラメーター指定と位置によるパラメーター指定を混合してリモート ストアド プロシージャを呼び出すと、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="f6627-121">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="f6627-122">エラーが発生しても SRV_RPC ハンドラーは呼び出されますが、パラメーターが存在しないと見なされ、**srv_rpcparams** は 0 を返します。</span><span class="sxs-lookup"><span data-stu-id="f6627-122">The SRV_RPC handler is still called, but it appears as if there were no parameters, and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f6627-123">拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6627-123">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="f6627-124">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f6627-124">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6627-125">参照</span><span class="sxs-lookup"><span data-stu-id="f6627-125">See Also</span></span>  
 [<span data-ttu-id="f6627-126">srv_rpcparams &#40;拡張ストアド プロシージャ API&#41;</span><span class="sxs-lookup"><span data-stu-id="f6627-126">srv_rpcparams &#40;Extended Stored Procedure API&#41;</span></span>](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
