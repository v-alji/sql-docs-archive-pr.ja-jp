---
title: srv_paramstatus (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramstatus
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramstatus
ms.assetid: 86cecd45-0b09-42e9-8152-32a12a1c2b7a
author: rothja
ms.author: jroth
ms.openlocfilehash: d89d4ccbb6a97ff47669ad4ed9c0b4c22ac934eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711921"
---
# <a name="srv_paramstatus-extended-stored-procedure-api"></a><span data-ttu-id="ccfde-102">srv_paramstatus (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="ccfde-102">srv_paramstatus (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="ccfde-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="ccfde-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="ccfde-104">特定のリモート ストアド プロシージャ呼び出しのパラメーターの状態を返します。</span><span class="sxs-lookup"><span data-stu-id="ccfde-104">Returns the status of a particular remote stored procedure call parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccfde-105">構文</span><span class="sxs-lookup"><span data-stu-id="ccfde-105">Syntax</span></span>  
  
```  
  
int srv_paramstatus (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="ccfde-106">引数</span><span class="sxs-lookup"><span data-stu-id="ccfde-106">Arguments</span></span>  
 <span data-ttu-id="ccfde-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="ccfde-107">*srvproc*</span></span>  
 <span data-ttu-id="ccfde-108">特定のクライアント接続のためのハンドル (この場合は、リモート ストアド プロシージャ呼び出しを受け取るハンドル) である SRV_PROC 構造体を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="ccfde-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="ccfde-109">この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="ccfde-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="ccfde-110">*n*</span><span class="sxs-lookup"><span data-stu-id="ccfde-110">*n*</span></span>  
 <span data-ttu-id="ccfde-111">パラメーターの番号を示します。</span><span class="sxs-lookup"><span data-stu-id="ccfde-111">Indicates the number of the parameter.</span></span> <span data-ttu-id="ccfde-112">最初のパラメーターは 1 です。</span><span class="sxs-lookup"><span data-stu-id="ccfde-112">The first parameter is number 1.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="ccfde-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="ccfde-113">Returns</span></span>  
 <span data-ttu-id="ccfde-114">このパラメーターの状態フラグを示す `int` 値を返します。</span><span class="sxs-lookup"><span data-stu-id="ccfde-114">An `int` that contains status flags for the parameter.</span></span> <span data-ttu-id="ccfde-115">現在、フラグは 1 つだけあります。ビット 0 が 1 に設定されている場合、パラメーターは戻りパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="ccfde-115">Currently, there is only one flag: If bit 0 is set to 1, the parameter is a return parameter.</span></span> <span data-ttu-id="ccfde-116">*n* 番目のパラメーターがない場合、またはリモート ストアド プロシージャがない場合は、-1 を返します。</span><span class="sxs-lookup"><span data-stu-id="ccfde-116">If there is no *n*th parameter or if there is no remote stored procedure, it returns -1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ccfde-117">解説</span><span class="sxs-lookup"><span data-stu-id="ccfde-117">Remarks</span></span>  
 <span data-ttu-id="ccfde-118">このルーチンは、リモート ストアド プロシージャ呼び出しのパラメーターに関する状態フラグを返します。</span><span class="sxs-lookup"><span data-stu-id="ccfde-118">This routine returns the status flags for a remote stored procedure call parameter.</span></span>  
  
 <span data-ttu-id="ccfde-119">パラメーターには、リモート ストアド プロシージャを使用してクライアントとアプリケーションとの間で受け渡しされるデータが格納されます。</span><span class="sxs-lookup"><span data-stu-id="ccfde-119">Parameters contain data passed between clients and the application with remote stored procedures.</span></span> <span data-ttu-id="ccfde-120">クライアントは戻りパラメーターとして特定のパラメーターを指定できます。</span><span class="sxs-lookup"><span data-stu-id="ccfde-120">The client can specify certain parameters as return parameters.</span></span> <span data-ttu-id="ccfde-121">この戻りパラメーターには、アプリケーションからクライアントに返す値を格納できます。</span><span class="sxs-lookup"><span data-stu-id="ccfde-121">These return parameters can contain values that the application passes back to the client.</span></span>  
  
 <span data-ttu-id="ccfde-122">現在使用されている唯一の状態フラグは、パラメーターが戻りパラメーターかどうかを示すものです。</span><span class="sxs-lookup"><span data-stu-id="ccfde-122">Currently, the only status flag is one that indicates whether the parameter is a return parameter.</span></span>  
  
 <span data-ttu-id="ccfde-123">パラメーターを指定してリモート ストアド プロシージャを呼び出す場合、パラメーターは名前で指定することも、名前を使用せずにその位置を指定して渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="ccfde-123">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="ccfde-124">名前によるパラメーター指定と位置によるパラメーター指定を混合してリモート ストアド プロシージャを呼び出すと、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="ccfde-124">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="ccfde-125">エラーが発生した場合でも、SRV_RPC ハンドラーは呼び出されますが、パラメーターがないかのように表示され、 **srv_rpcparams**は0を返します。</span><span class="sxs-lookup"><span data-stu-id="ccfde-125">If an error occurs, the SRV_RPC handler is still called, but it appears as if there were no parameters, and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ccfde-126">拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ccfde-126">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="ccfde-127">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ccfde-127">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccfde-128">参照</span><span class="sxs-lookup"><span data-stu-id="ccfde-128">See Also</span></span>  
 [<span data-ttu-id="ccfde-129">srv_rpcparams &#40;拡張ストアド プロシージャ API&#41;</span><span class="sxs-lookup"><span data-stu-id="ccfde-129">srv_rpcparams &#40;Extended Stored Procedure API&#41;</span></span>](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
