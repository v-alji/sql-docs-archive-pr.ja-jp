---
title: 拡張ストアド プロシージャのプログラマーズ リファレンス | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
topic_type:
- apiref
- apinav
helpviewer_keywords:
- extended stored procedures [SQL Server], listed
ms.assetid: 4e9d0374-0927-4f17-bab9-2215b1b8fea8
author: rothja
ms.author: jroth
ms.openlocfilehash: f3b1beade751cd7a7407f3c33eb7f8ae58c9fd4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645076"
---
# <a name="extended-stored-procedures-programmer39s-reference"></a><span data-ttu-id="96691-102">拡張ストアドプロシージャプログラマー&#39;s リファレンス</span><span class="sxs-lookup"><span data-stu-id="96691-102">Extended Stored Procedures Programmer&#39;s Reference</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="96691-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="96691-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="96691-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)]拡張ストアドプロシージャ api は、既に Open Data Services に含まれており、機能を拡張するためのサーバーベースのアプリケーションプログラミングインターフェイス (API) を提供し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="96691-104">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Extended Stored Procedure API, previously part of Open Data Services, provides a server-based application programming interface (API) for extending [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] functionality.</span></span> <span data-ttu-id="96691-105">この API は、アプリケーションの構築に使用する C および C++ の関数とマクロで構成されています。</span><span class="sxs-lookup"><span data-stu-id="96691-105">The API consists of C and C++ functions and macros used to build applications.</span></span>  
  
 <span data-ttu-id="96691-106">拡張ストアド プロシージャへのニーズは、現在は CLR 統合などの強力な新しいテクノロジにほとんど移行しています。</span><span class="sxs-lookup"><span data-stu-id="96691-106">With the emergence of newer and more powerful technologies such as CLR integration, the need for extended stored procedures has largely been replaced.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="96691-107">拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="96691-107">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="96691-108">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="96691-108">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="96691-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="96691-109">In This Section</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="96691-110">Data Types (データ型)</span><span class="sxs-lookup"><span data-stu-id="96691-110">Data Types</span></span>](srv-pfield-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="96691-111">srv_alloc</span><span class="sxs-lookup"><span data-stu-id="96691-111">srv_alloc</span></span>](srv-alloc-extended-stored-procedure-api.md)||  
|[<span data-ttu-id="96691-112">srv_convert</span><span class="sxs-lookup"><span data-stu-id="96691-112">srv_convert</span></span>](srv-pfieldex-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="96691-113">srv_describe</span><span class="sxs-lookup"><span data-stu-id="96691-113">srv_describe</span></span>](srv-rpcdb-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="96691-114">srv_getbindtoken</span><span class="sxs-lookup"><span data-stu-id="96691-114">srv_getbindtoken</span></span>](srv-rpcname-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="96691-115">srv_got_attention</span><span class="sxs-lookup"><span data-stu-id="96691-115">srv_got_attention</span></span>](srv-rpcnumber-extended-stored-procedure-api.md)|  
||[<span data-ttu-id="96691-116">srv_rpcoptions</span><span class="sxs-lookup"><span data-stu-id="96691-116">srv_rpcoptions</span></span>](srv-rpcoptions-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="96691-117">srv_message_handler</span><span class="sxs-lookup"><span data-stu-id="96691-117">srv_message_handler</span></span>](srv-rpcowner-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="96691-118">srv_paramdata</span><span class="sxs-lookup"><span data-stu-id="96691-118">srv_paramdata</span></span>](srv-rpcparams-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="96691-119">srv_paraminfo</span><span class="sxs-lookup"><span data-stu-id="96691-119">srv_paraminfo</span></span>](srv-senddone-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="96691-120">srv_paramlen</span><span class="sxs-lookup"><span data-stu-id="96691-120">srv_paramlen</span></span>](srv-sendmsg-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="96691-121">srv_parammaxlen</span><span class="sxs-lookup"><span data-stu-id="96691-121">srv_parammaxlen</span></span>](srv-sendrow-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="96691-122">srv_paramname</span><span class="sxs-lookup"><span data-stu-id="96691-122">srv_paramname</span></span>](srv-setcoldata-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="96691-123">srv_paramnumber</span><span class="sxs-lookup"><span data-stu-id="96691-123">srv_paramnumber</span></span>](srv-setcollen-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="96691-124">srv_paramset</span><span class="sxs-lookup"><span data-stu-id="96691-124">srv_paramset</span></span>](srv-setutype-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="96691-125">srv_paramsetoutput</span><span class="sxs-lookup"><span data-stu-id="96691-125">srv_paramsetoutput</span></span>](srv-willconvert-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="96691-126">srv_paramstatus</span><span class="sxs-lookup"><span data-stu-id="96691-126">srv_paramstatus</span></span>](srv-wsendmsg-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="96691-127">srv_paramtype</span><span class="sxs-lookup"><span data-stu-id="96691-127">srv_paramtype</span></span>](srv-paramtype-extended-stored-procedure-api.md)||  
  
  
