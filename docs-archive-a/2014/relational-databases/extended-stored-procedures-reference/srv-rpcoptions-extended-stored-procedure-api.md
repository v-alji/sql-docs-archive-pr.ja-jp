---
title: srv_rpcoptions (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcoptions
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcoptions
ms.assetid: dbcce5d1-d5a1-4379-9597-04e43af5923d
author: rothja
ms.author: jroth
ms.openlocfilehash: f5ebe4ab48721002e679ce149293b474a934e348
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743249"
---
# <a name="srv_rpcoptions-extended-stored-procedure-api"></a><span data-ttu-id="d204d-102">srv_rpcoptions (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="d204d-102">srv_rpcoptions (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="d204d-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="d204d-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="d204d-104">現在のリモート ストアド プロシージャの実行時オプションを返します。</span><span class="sxs-lookup"><span data-stu-id="d204d-104">Returns run-time options for the current remote stored procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d204d-105">構文</span><span class="sxs-lookup"><span data-stu-id="d204d-105">Syntax</span></span>  
  
```  
  
DBUSMALLINT srv_rpcoptions ( SRV_PROC *  
srvproc   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="d204d-106">引数</span><span class="sxs-lookup"><span data-stu-id="d204d-106">Arguments</span></span>  
 <span data-ttu-id="d204d-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="d204d-107">*srvproc*</span></span>  
 <span data-ttu-id="d204d-108">特定のクライアント接続のためのハンドル (この場合は、リモート ストアド プロシージャを受け取るハンドル) である SRV_PROC 構造体を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="d204d-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure).</span></span> <span data-ttu-id="d204d-109">この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="d204d-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="d204d-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="d204d-110">Returns</span></span>  
 <span data-ttu-id="d204d-111">現在のリモート ストアド プロシージャの実行時フラグを論理 OR で結合して格納したビットマップを返します。</span><span class="sxs-lookup"><span data-stu-id="d204d-111">A bitmap that contains the run-time flags joined in a logical OR for the current remote stored procedure.</span></span> <span data-ttu-id="d204d-112">リモート ストアド プロシージャがない場合は、0 を返し、メッセージを生成します。</span><span class="sxs-lookup"><span data-stu-id="d204d-112">If there is not a current remote stored procedure, 0 is returned and a message is generated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d204d-113">解説</span><span class="sxs-lookup"><span data-stu-id="d204d-113">Remarks</span></span>  
 <span data-ttu-id="d204d-114">次の表では、各実行時フラグについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d204d-114">The following table describes each run-time flag.</span></span>  
  
|<span data-ttu-id="d204d-115">実行時フラグ</span><span class="sxs-lookup"><span data-stu-id="d204d-115">Run-time flag</span></span>|<span data-ttu-id="d204d-116">説明</span><span class="sxs-lookup"><span data-stu-id="d204d-116">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="d204d-117">SRV_NOMETADATA</span><span class="sxs-lookup"><span data-stu-id="d204d-117">SRV_NOMETADATA</span></span>|<span data-ttu-id="d204d-118">クライアントがメタデータ情報なしの結果を要求したことを示します。</span><span class="sxs-lookup"><span data-stu-id="d204d-118">The client has requested results without metadata information.</span></span> <span data-ttu-id="d204d-119">このフラグは、クライアントがのインスタンスと通信している場合にのみ使用され [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="d204d-119">This flag is only used when the client is communicating with an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d204d-120">拡張ストアド プロシージャ API アプリケーションではメタデータ情報を省略できません。</span><span class="sxs-lookup"><span data-stu-id="d204d-120">An Extended Stored Procedure API application cannot omit metadata information.</span></span>|  
|<span data-ttu-id="d204d-121">SRV_RECOMPILE</span><span class="sxs-lookup"><span data-stu-id="d204d-121">SRV_RECOMPILE</span></span>|<span data-ttu-id="d204d-122">クライアントがリモート ストアド プロシージャの実行前に再コンパイルを要求していることを示します。</span><span class="sxs-lookup"><span data-stu-id="d204d-122">The client has requested to recompile the remote stored procedure before executing it.</span></span> <span data-ttu-id="d204d-123">このフラグは、拡張ストアド プロシージャ API アプリケーションには適用できません。</span><span class="sxs-lookup"><span data-stu-id="d204d-123">This flag may not apply to an Extended Stored Procedure API application.</span></span>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d204d-124">拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d204d-124">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="d204d-125">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d204d-125">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
