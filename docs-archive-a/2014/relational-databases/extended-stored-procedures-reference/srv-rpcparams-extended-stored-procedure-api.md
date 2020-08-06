---
title: srv_rpcparams (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcparams
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcparams
ms.assetid: 96a5e6f6-d320-4623-b96e-0a856e3abebb
author: rothja
ms.author: jroth
ms.openlocfilehash: 443b9ea8a67341afdb92f0c384148c8b1b42f752
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743241"
---
# <a name="srv_rpcparams-extended-stored-procedure-api"></a><span data-ttu-id="c996a-102">srv_rpcparams (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="c996a-102">srv_rpcparams (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="c996a-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="c996a-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="c996a-104">現在のリモート ストアド プロシージャのパラメーター数を返します。</span><span class="sxs-lookup"><span data-stu-id="c996a-104">Returns the number of parameters for the current remote stored procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c996a-105">構文</span><span class="sxs-lookup"><span data-stu-id="c996a-105">Syntax</span></span>  
  
```  
  
int srv_rpcparams ( SRV_PROC *  
srvproc   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="c996a-106">引数</span><span class="sxs-lookup"><span data-stu-id="c996a-106">Arguments</span></span>  
 <span data-ttu-id="c996a-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="c996a-107">*srvproc*</span></span>  
 <span data-ttu-id="c996a-108">特定のクライアント接続のためのハンドル (この場合は、リモート ストアド プロシージャを受け取るハンドル) である SRV_PROC 構造体を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="c996a-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure).</span></span> <span data-ttu-id="c996a-109">この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="c996a-109">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="c996a-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="c996a-110">Returns</span></span>  
 <span data-ttu-id="c996a-111">リモート ストアド プロシージャ内のパラメーター数を返します。</span><span class="sxs-lookup"><span data-stu-id="c996a-111">The number of parameters in the remote stored procedure.</span></span> <span data-ttu-id="c996a-112">リモート ストアド プロシージャにパラメーターがない場合、または現在のリモート ストアド プロシージャがない場合は、-1 を返し、情報エラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="c996a-112">If there are no parameters in the remote stored procedure or if there is not a current remote stored procedure, -1 is returned and an information error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c996a-113">解説</span><span class="sxs-lookup"><span data-stu-id="c996a-113">Remarks</span></span>  
 <span data-ttu-id="c996a-114">この関数は現在のリモート ストアド プロシージャのパラメーター数を返します。</span><span class="sxs-lookup"><span data-stu-id="c996a-114">This function returns the number of parameters in the current remote stored procedure.</span></span> <span data-ttu-id="c996a-115">通常、この関数はリモート ストアド プロシージャから呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="c996a-115">It is usually called from the remote stored procedure.</span></span>  
  
 <span data-ttu-id="c996a-116">パラメーターを指定してリモート ストアド プロシージャを呼び出す場合、パラメーターは名前で指定することも、名前を使用せずにその位置を指定して渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="c996a-116">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="c996a-117">名前によるパラメーター指定と位置によるパラメーター指定を混合してリモート ストアド プロシージャを呼び出すと、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="c996a-117">If the remote stored procedure call was made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="c996a-118">このエラーが発生してもリモート ストアド プロシージャ ハンドラーは呼び出されますが、ハンドラーはパラメーターを受け取らず、**srv_rpcparams** は 0 を返します。</span><span class="sxs-lookup"><span data-stu-id="c996a-118">When this error occurs, the remote stored procedure handler is called, but it does not receive the parameters and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c996a-119">拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c996a-119">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="c996a-120">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c996a-120">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
