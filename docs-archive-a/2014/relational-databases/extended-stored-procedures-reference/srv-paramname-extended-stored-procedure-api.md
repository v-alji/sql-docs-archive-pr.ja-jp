---
title: srv_paramname (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramname
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramname
ms.assetid: 1a53d707-7b06-49cc-a0df-ac727cfe953f
author: rothja
ms.author: jroth
ms.openlocfilehash: 2227ac3d46efe7d09abc05964248229f3533d42d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742125"
---
# <a name="srv_paramname-extended-stored-procedure-api"></a><span data-ttu-id="514b8-102">srv_paramname (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="514b8-102">srv_paramname (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="514b8-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="514b8-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="514b8-104">リモート ストアド プロシージャ呼び出しのパラメーターの名前を返します。</span><span class="sxs-lookup"><span data-stu-id="514b8-104">Returns the name of a remote stored procedure call parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="514b8-105">構文</span><span class="sxs-lookup"><span data-stu-id="514b8-105">Syntax</span></span>  
  
```  
  
DBCHAR * srv_paramname (  
SRV_PROC * srvproc,intn, int *len );  
```  
  
## <a name="arguments"></a><span data-ttu-id="514b8-106">引数</span><span class="sxs-lookup"><span data-stu-id="514b8-106">Arguments</span></span>  
 <span data-ttu-id="514b8-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="514b8-107">*srvproc*</span></span>  
 <span data-ttu-id="514b8-108">特定のクライアント接続のためのハンドル (この場合は、リモート ストアド プロシージャ呼び出しを受け取るハンドル) である SRV_PROC 構造体を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="514b8-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="514b8-109">この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="514b8-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="514b8-110">*n*</span><span class="sxs-lookup"><span data-stu-id="514b8-110">*n*</span></span>  
 <span data-ttu-id="514b8-111">パラメーターの番号を示します。</span><span class="sxs-lookup"><span data-stu-id="514b8-111">Indicates the number of the parameter.</span></span> <span data-ttu-id="514b8-112">最初のパラメーターは 1 です。</span><span class="sxs-lookup"><span data-stu-id="514b8-112">The first parameter is 1.</span></span>  
  
 <span data-ttu-id="514b8-113">*len*</span><span class="sxs-lookup"><span data-stu-id="514b8-113">*len*</span></span>  
 <span data-ttu-id="514b8-114">パラメーター名の長さ (バイト数) を格納した `int` 変数へのポインターです。</span><span class="sxs-lookup"><span data-stu-id="514b8-114">Provides a pointer to an `int` variable that contains the length, in bytes, of the parameter name.</span></span> <span data-ttu-id="514b8-115">*len* が NULL である場合、リモート ストアド プロシージャのパラメーター名の長さは返されていません。</span><span class="sxs-lookup"><span data-stu-id="514b8-115">If *len* is NULL, the length of the remote stored procedure parameter name is not returned.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="514b8-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="514b8-116">Returns</span></span>  
 <span data-ttu-id="514b8-117">パラメーター名を格納した NULL 終端文字列を指すポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="514b8-117">A pointer to a null-terminated character string that contains the parameter name.</span></span> <span data-ttu-id="514b8-118">パラメーター名の長さは、*len* に格納されます。</span><span class="sxs-lookup"><span data-stu-id="514b8-118">The length of the parameter name is stored in *len*.</span></span> <span data-ttu-id="514b8-119">*n* 番目のパラメーターがない場合、またはリモート ストアド プロシージャがない場合は NULL を返し、*len* が -1 に設定され、情報エラー メッセージが送信されます。</span><span class="sxs-lookup"><span data-stu-id="514b8-119">If there is no *n*th parameter or no remote stored procedure, it returns NULL, *len* is set to -1, and an informational error message is sent.</span></span> <span data-ttu-id="514b8-120">パラメーター名が NULL である場合、*len* は 0 に設定され、NULL 終端の空文字列が返されます。</span><span class="sxs-lookup"><span data-stu-id="514b8-120">If the parameter name is NULL, *len* is set to 0 and a null-terminated empty string is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="514b8-121">解説</span><span class="sxs-lookup"><span data-stu-id="514b8-121">Remarks</span></span>  
 <span data-ttu-id="514b8-122">この関数は、リモート ストアド プロシージャ呼び出しのパラメーターの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="514b8-122">This function gets the name of a remote stored procedure call parameter.</span></span> <span data-ttu-id="514b8-123">パラメーターを指定してリモート ストアド プロシージャを呼び出す場合、パラメーターは名前で指定することも、名前を使用せずにその位置を指定して渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="514b8-123">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="514b8-124">名前によるパラメーター指定と位置によるパラメーター指定を混合してリモート ストアド プロシージャを呼び出すと、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="514b8-124">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="514b8-125">エラーが発生しても SRV_RPC ハンドラーは呼び出されますが、パラメーターが存在しないと見なされ、**srv_rpcparams** は 0 を返します。</span><span class="sxs-lookup"><span data-stu-id="514b8-125">The SRV_RPC handler is still called, but it appears as if there were no parameters, and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="514b8-126">拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="514b8-126">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="514b8-127">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="514b8-127">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="514b8-128">参照</span><span class="sxs-lookup"><span data-stu-id="514b8-128">See Also</span></span>  
 [<span data-ttu-id="514b8-129">srv_rpcparams &#40;拡張ストアド プロシージャ API&#41;</span><span class="sxs-lookup"><span data-stu-id="514b8-129">srv_rpcparams &#40;Extended Stored Procedure API&#41;</span></span>](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
