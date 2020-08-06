---
title: サーバーのプロパティ ([プロセッサ] ページ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.processor.f1
ms.assetid: cc1581a2-492b-41f0-bda5-17909b65c4f7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c4d241f01de7ac961832e77bb09483cff275deb6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641849"
---
# <a name="server-properties-processors-page"></a><span data-ttu-id="ec672-102">[サーバーのプロパティ] ([プロセッサ] ページ)</span><span class="sxs-lookup"><span data-stu-id="ec672-102">Server Properties (Processors Page)</span></span>
  <span data-ttu-id="ec672-103">このページを使用すると、プロセッサ オプションを表示または変更できます。</span><span class="sxs-lookup"><span data-stu-id="ec672-103">Use this page to view or modify your processor options.</span></span> <span data-ttu-id="ec672-104">プロセッサの関係の設定は、複数のプロセッサが実装されている場合のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="ec672-104">Processor affinity settings are only enabled when more than one processor is installed.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ec672-105">Options</span><span class="sxs-lookup"><span data-stu-id="ec672-105">Options</span></span>  
 <span data-ttu-id="ec672-106">**[プロセッサの関係]**</span><span class="sxs-lookup"><span data-stu-id="ec672-106">**Processor Affinity**</span></span>  
 <span data-ttu-id="ec672-107">プロセッサの再読み込みを防ぎ、プロセッサ間のスレッドの移行を少なくするために、プロセッサを特定のスレッドに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="ec672-107">Assigns processors to specific threads to eliminating processor reloads and reduce thread migration across processors.</span></span> <span data-ttu-id="ec672-108">詳細については、「 [affinity mask サーバー構成オプション](affinity-mask-server-configuration-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec672-108">For more information, see [affinity mask Server Configuration Option](affinity-mask-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="ec672-109">**[I/O 関係]**</span><span class="sxs-lookup"><span data-stu-id="ec672-109">**I/O Affinity**</span></span>  
 <span data-ttu-id="ec672-110">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ディスク I/O を特定の CPU のサブセットにバインドします。</span><span class="sxs-lookup"><span data-stu-id="ec672-110">Binds [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] disk I/Os to a specified subset of CPUs.</span></span> <span data-ttu-id="ec672-111">詳細については、「 [affinity Input-Output mask サーバー構成オプション](affinity-input-output-mask-server-configuration-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec672-111">For more information, see [affinity Input-Output mask Server Configuration Option](affinity-input-output-mask-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="ec672-112">**[すべてのプロセッサに対して自動的にプロセッサ関係マスクを設定する]**</span><span class="sxs-lookup"><span data-stu-id="ec672-112">**Automatically set processor affinity mask for all processors**</span></span>  
 <span data-ttu-id="ec672-113">プロセッサの関係が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって設定されます。</span><span class="sxs-lookup"><span data-stu-id="ec672-113">Allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to set the processor affinity.</span></span>  
  
 <span data-ttu-id="ec672-114">**[すべてのプロセッサに対して自動的に I/O 関係マスクを設定する]**</span><span class="sxs-lookup"><span data-stu-id="ec672-114">**Automatically set I/O affinity mask for all processors**</span></span>  
 <span data-ttu-id="ec672-115">I/O 関係が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって設定されます。</span><span class="sxs-lookup"><span data-stu-id="ec672-115">Allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to set the I/O affinity.</span></span>  
  
 <span data-ttu-id="ec672-116">**[ワーカー スレッドの最大数]**</span><span class="sxs-lookup"><span data-stu-id="ec672-116">**Maximum worker threads**</span></span>  
 <span data-ttu-id="ec672-117">0 を指定すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はワーカー スレッドの数を動的に設定します。</span><span class="sxs-lookup"><span data-stu-id="ec672-117">0 allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to dynamically set the number of worker threads.</span></span> <span data-ttu-id="ec672-118">この設定は、ほとんどのシステムで最適な設定です。</span><span class="sxs-lookup"><span data-stu-id="ec672-118">This setting is best for most systems.</span></span> <span data-ttu-id="ec672-119">ただし、システム構成によっては、このオプションに特定の値を設定した方がパフォーマンスが向上することがあります。</span><span class="sxs-lookup"><span data-stu-id="ec672-119">However, depending on your system configuration, setting this option to a specific value sometimes improves performance.</span></span> <span data-ttu-id="ec672-120">詳細については、「 [max worker threads サーバー構成オプションの構成](configure-the-max-worker-threads-server-configuration-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec672-120">For more information, see [Configure the max worker threads Server Configuration Option](configure-the-max-worker-threads-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="ec672-121">**SQL Server の優先度を上げる**</span><span class="sxs-lookup"><span data-stu-id="ec672-121">**Boost SQL Server priority**</span></span>  
 <span data-ttu-id="ec672-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows スケジュールでの [!INCLUDE[msCoName](../../includes/msconame-md.md)] の優先度を、同じコンピューター内の他のプロセスよりも高くして実行するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ec672-122">Specifies whether [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should run at a higher [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows scheduling priority than other processes on the same computer.</span></span> <span data-ttu-id="ec672-123">詳細については、「 [priority boost サーバー構成オプションの構成](configure-the-priority-boost-server-configuration-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec672-123">For more information, see [Configure the priority boost Server Configuration Option](configure-the-priority-boost-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="ec672-124">**[Windows ファイバーを使用する (簡易プーリング)]**</span><span class="sxs-lookup"><span data-stu-id="ec672-124">**Use Windows fibers (lightweight pooling)**</span></span>  
 <span data-ttu-id="ec672-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスに対して、スレッドの代わりに Windows ファイバーを使用します。</span><span class="sxs-lookup"><span data-stu-id="ec672-125">Use Windows fibers instead of threads for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="ec672-126">このオプションは、Windows 2003 Server Edition でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="ec672-126">Note that this is only available in Windows 2003 Server Edition.</span></span> <span data-ttu-id="ec672-127">詳細については、「 [lightweight pooling Server Configuration Option](lightweight-pooling-server-configuration-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec672-127">For more information, see [lightweight pooling Server Configuration Option](lightweight-pooling-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="ec672-128">**[構成した値]**</span><span class="sxs-lookup"><span data-stu-id="ec672-128">**Configured Values**</span></span>  
 <span data-ttu-id="ec672-129">このペインの各オプションに構成されている値を表示します。</span><span class="sxs-lookup"><span data-stu-id="ec672-129">Displays the configured values for the options on this pane.</span></span> <span data-ttu-id="ec672-130">これらの値を変更した場合は、 **[実行中の値]** をクリックして、変更後の値が反映されているかどうかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="ec672-130">If you change these values, click **Running Values** to see whether the changes have taken effect.</span></span> <span data-ttu-id="ec672-131">値が反映されていない場合は、最初に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec672-131">If they have not, the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be restarted first.</span></span>  
  
 <span data-ttu-id="ec672-132">**[実行中の値]**</span><span class="sxs-lookup"><span data-stu-id="ec672-132">**Running Values**</span></span>  
 <span data-ttu-id="ec672-133">このペイン上のオプションの、現在実行中の値を表示します。</span><span class="sxs-lookup"><span data-stu-id="ec672-133">View the currently running values for the options on this pane.</span></span> <span data-ttu-id="ec672-134">これらの値は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="ec672-134">These values are read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec672-135">参照</span><span class="sxs-lookup"><span data-stu-id="ec672-135">See Also</span></span>  
 [<span data-ttu-id="ec672-136">サーバー構成オプション &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ec672-136">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
