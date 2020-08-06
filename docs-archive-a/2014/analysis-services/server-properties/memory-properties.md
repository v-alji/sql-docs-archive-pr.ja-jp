---
title: メモリのプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- LowMemoryLimit property
- MinimumAllocatedMemory property
- MidMemoryPrice property
- MemoryHeapType property
- memory [Analysis Services]
- DefaultPagesCountToReuse property
- TotalMemoryLimit property
- SessionMemoryLimit property
- VirtualMemoryLimit property
- WaitCountIfHighMemory property
- HighMemoryPrice property
- HeapTypeForObjects property
ms.assetid: 085f5195-7b2c-411a-9813-0ff5c6066d13
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6f2d2e56c9a951cee27752bd57d55d185a9b6618
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743482"
---
# <a name="memory-properties"></a><span data-ttu-id="3993d-102">メモリのプロパティ</span><span class="sxs-lookup"><span data-stu-id="3993d-102">Memory Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="3993d-103">では、次の表に示すサーバー メモリ プロパティがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="3993d-103">supports the server memory properties listed in the following table.</span></span> <span data-ttu-id="3993d-104">これらのプロパティの設定方法については、「 [SQL Server 2008 R2 Analysis Services 操作ガイド](https://go.microsoft.com/fwlink/?LinkID=225539)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3993d-104">For guidance in setting these properties, see [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>  
  
 <span data-ttu-id="3993d-105">1 ～ 100 の値は、 **[物理メモリの合計]** または **[仮想アドレス領域]** のどちらか少ない方に対する割合を示します。</span><span class="sxs-lookup"><span data-stu-id="3993d-105">Values between 1 and 100 represent percentages of **Total Physical Memory** or **Virtual Address Space**, whichever is less.</span></span> <span data-ttu-id="3993d-106">100 を超える値はメモリ制限を示します (単位: バイト)。</span><span class="sxs-lookup"><span data-stu-id="3993d-106">Values over 100 represent memory limits in bytes.</span></span>  
  
 <span data-ttu-id="3993d-107">**適用対象:** 多次元および表形式サーバーモード (特に明記されていない場合)。</span><span class="sxs-lookup"><span data-stu-id="3993d-107">**Applies to:** Multidimensional and Tabular server mode, unless noted otherwise.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3993d-108">Properties</span><span class="sxs-lookup"><span data-stu-id="3993d-108">Properties</span></span>  
 `LowMemoryLimit`  
 <span data-ttu-id="3993d-109">サーバーがメモリ不足になる時点を定義する、符号付き 64 ビット倍精度浮動小数点数のプロパティ。合計物理メモリの比率として表されます。</span><span class="sxs-lookup"><span data-stu-id="3993d-109">A signed 64-bit double-precision floating-point number property that defines the point at which the server is low on memory, expressed as percentage of total physical memory.</span></span> <span data-ttu-id="3993d-110">この制限に達すると、インスタンスは、期限切れのセッションを終了したり、使用されていない計算をアンロードしたりすることによって、徐々にキャッシュ内のメモリを解放し始めます。</span><span class="sxs-lookup"><span data-stu-id="3993d-110">When this limit is reached, the instance will start to slowly clear memory out of caches by closing expired sessions and unloading unused calculations.</span></span> <span data-ttu-id="3993d-111">この制限を下回っている間は、メモリは解放されません。</span><span class="sxs-lookup"><span data-stu-id="3993d-111">The server will not release memory below this limit.</span></span> <span data-ttu-id="3993d-112">既定値は 65 です。これは、物理メモリまたは仮想アドレス空間の 65% (どちらか少ない方) を超えたらメモリ不足とすることを示します。</span><span class="sxs-lookup"><span data-stu-id="3993d-112">The default value is 65; which indicates the low memory limit is 65% of physical memory or the virtual address space, whichever is less.</span></span>  
  
 `TotalMemoryLimit`  
 <span data-ttu-id="3993d-113">サーバーが、より積極的にメモリを解放し始めるしきい値を定義します。</span><span class="sxs-lookup"><span data-stu-id="3993d-113">Defines a threshold that when reached, causes the server to deallocate memory more aggressively.</span></span> <span data-ttu-id="3993d-114">既定値は、物理メモリまたは仮想アドレス空間の 80% です (どちらか少ない方)。</span><span class="sxs-lookup"><span data-stu-id="3993d-114">The default value 80% of physical memory or the virtual address space, whichever is less.</span></span>  
  
 <span data-ttu-id="3993d-115">`TotalMemoryLimit` は常に、`HardMemoryLimit` より小さくする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3993d-115">Note that `TotalMemoryLimit` must always be less than `HardMemoryLimit`</span></span>  
  
 `HardMemoryLimit`  
 <span data-ttu-id="3993d-116">インスタンスが、メモリ使用量を減らすために、アクティブなユーザー セッションを積極的に終了し始めるメモリのしきい値を指定します。</span><span class="sxs-lookup"><span data-stu-id="3993d-116">Specifies a memory threshold after which the instance aggressively terminates active user sessions to reduce memory usage.</span></span> <span data-ttu-id="3993d-117">終了されたすべてのセッションには、メモリ不足によって使用中止となった旨のエラーが送信されます。</span><span class="sxs-lookup"><span data-stu-id="3993d-117">All terminated sessions will receive an error about being cancelled by memory pressure.</span></span> <span data-ttu-id="3993d-118">既定値 (0) は、`HardMemoryLimit` が `TotalMemoryLimit` とシステムの物理メモリ合計の間の値に設定されることを意味します。システムの物理メモリがプロセスの仮想アドレス領域を超える場合は、`HardMemoryLimit` を計算せずに、仮想アドレス空間が使用されます。</span><span class="sxs-lookup"><span data-stu-id="3993d-118">The default value, zero (0), means the `HardMemoryLimit` will be set to a midway value between `TotalMemoryLimit` and the total physical memory of the system; if the physical memory of the system is larger than the virtual address space of the process, then virtual address space will be used instead to calculate `HardMemoryLimit`.</span></span>  
  
 `VirtualMemoryLimit`  
 <span data-ttu-id="3993d-119">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="3993d-119">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `VertiPaqPagingPolicy`  
 <span data-ttu-id="3993d-120">サーバーのメモリが不足したときのページングの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="3993d-120">Specifies the paging behavior in the event the server runs low on memory.</span></span> <span data-ttu-id="3993d-121">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3993d-121">Valid values are as follows:</span></span>  
  
 <span data-ttu-id="3993d-122">ゼロ (**0**) ページングを無効にします。</span><span class="sxs-lookup"><span data-stu-id="3993d-122">Zero (**0**) disables paging.</span></span> <span data-ttu-id="3993d-123">メモリが足りなくなると、メモリ不足エラーが発生し、処理は失敗します。</span><span class="sxs-lookup"><span data-stu-id="3993d-123">If memory is insufficient, processing fails with an out-of-memory error.</span></span> <span data-ttu-id="3993d-124">ページングを無効にする場合は、サービス アカウントに Windows 特権を付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3993d-124">If you disable paging, you must grant Windows privileges to the service account.</span></span> <span data-ttu-id="3993d-125">手順については、「[サービス アカウントの構成 (Analysis Services)](../instances/configure-service-accounts-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3993d-125">See [Configure Service Accounts &#40;Analysis Services&#41;](../instances/configure-service-accounts-analysis-services.md) for instructions.</span></span>  
  
 <span data-ttu-id="3993d-126">**1** が既定値です。</span><span class="sxs-lookup"><span data-stu-id="3993d-126">**1** is the default.</span></span> <span data-ttu-id="3993d-127">このプロパティを指定した場合、オペレーティング システムのページング ファイル (pagefile.sys) を使用してディスクへのページングが行われます。</span><span class="sxs-lookup"><span data-stu-id="3993d-127">This property enables paging to disk using the operating system page file (pagefile.sys).</span></span>  
  
 <span data-ttu-id="3993d-128">`VertiPaqPagingPolicy` が 1 に設定された場合、指定された方法を使用してサーバーがディスクへのページングを試行するので、メモリ制約によって処理が失敗する可能性は低くなります。</span><span class="sxs-lookup"><span data-stu-id="3993d-128">When `VertiPaqPagingPolicy` is set to 1, processing is less likely to fail due to memory constraints because the server will try to page to disk using the method that you specified.</span></span> <span data-ttu-id="3993d-129">`VertiPaqPagingPolicy` プロパティを設定しても、メモリ エラーが発生しないことが保証されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="3993d-129">Setting the `VertiPaqPagingPolicy` property does not guarantee that memory errors will never happen.</span></span> <span data-ttu-id="3993d-130">以下の状況では、メモリ不足エラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3993d-130">Out of memory errors can still occur under the following conditions:</span></span>  
  
-   <span data-ttu-id="3993d-131">すべての辞書のための十分なメモリがない。</span><span class="sxs-lookup"><span data-stu-id="3993d-131">There is not enough memory for all dictionaries.</span></span> <span data-ttu-id="3993d-132">処理中に、Analysis Services は各列の辞書をメモリにロックします。それらすべての合計が、`VertiPaqMemoryLimit` で指定されている値を超えることはできません。</span><span class="sxs-lookup"><span data-stu-id="3993d-132">During processing, Analysis Services locks the dictionaries for each column in memory, and all of these together cannot be more than the value specified for `VertiPaqMemoryLimit`.</span></span>  
  
-   <span data-ttu-id="3993d-133">処理に対応するための十分な仮想アドレス空間がない。</span><span class="sxs-lookup"><span data-stu-id="3993d-133">There is insufficient virtual address space to accommodate the process.</span></span>  
  
 <span data-ttu-id="3993d-134">繰り返し発生するメモリ不足エラーを解決するには、処理を要するデータの量を減らすようにモデルを設計し直すか、コンピューターに物理メモリを追加します。</span><span class="sxs-lookup"><span data-stu-id="3993d-134">To resolve persistent out of memory errors, you can either try to redesign the model to reduce the amount of data that needs processing, or you can add more physical memory to the computer.</span></span>  
  
 <span data-ttu-id="3993d-135">テーブル サーバー モードにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="3993d-135">Applies to tabular server mode only.</span></span>  
  
 `VertiPaqMemoryLimit`  
 <span data-ttu-id="3993d-136">ディスクへのページングを許可した場合に、ページングが開始されるメモリ消費レベル (メモリの合計に対する割合) をこのプロパティで指定します。</span><span class="sxs-lookup"><span data-stu-id="3993d-136">If paging to disk is allowed, this property specifies the level of memory consumption (as a percentage of total memory) at which paging starts.</span></span> <span data-ttu-id="3993d-137">既定値は 60 です。</span><span class="sxs-lookup"><span data-stu-id="3993d-137">The default is 60.</span></span> <span data-ttu-id="3993d-138">メモリ消費量が 60% 未満の場合、ディスクへのページングは実行されません。</span><span class="sxs-lookup"><span data-stu-id="3993d-138">If memory consumption is less than 60 percent, the server will not page to disk.</span></span>  
  
 <span data-ttu-id="3993d-139">このプロパティは、`VertiPaqPagingPolicyProperty` に依存します (ページングを有効にするには 1 に設定する必要があります)。</span><span class="sxs-lookup"><span data-stu-id="3993d-139">This property depends on the `VertiPaqPagingPolicyProperty`, which must be set to 1 in order for paging to occur.</span></span>  
  
 <span data-ttu-id="3993d-140">テーブル サーバー モードにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="3993d-140">Applies to tabular server mode only.</span></span>  
  
 `HighMemoryPrice`  
 <span data-ttu-id="3993d-141">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="3993d-141">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MemoryHeapType`  
 <span data-ttu-id="3993d-142">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="3993d-142">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="3993d-143">多次元サーバー モードにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="3993d-143">Applies to multidimensional server mode only.</span></span>  
  
 `HeapTypeForObjects`  
 <span data-ttu-id="3993d-144">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="3993d-144">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="3993d-145">多次元サーバー モードにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="3993d-145">Applies to multidimensional server mode only.</span></span>  
  
 `DefaultPagesCountToReuse`  
 <span data-ttu-id="3993d-146">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="3993d-146">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `HandleIA64AlignmentFaults`  
 <span data-ttu-id="3993d-147">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="3993d-147">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MidMemoryPrice`  
 <span data-ttu-id="3993d-148">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="3993d-148">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MinimumAllocatedMemory`  
 <span data-ttu-id="3993d-149">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="3993d-149">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `PreAllocate`  
 <span data-ttu-id="3993d-150">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="3993d-150">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `SessionMemoryLimit`  
 <span data-ttu-id="3993d-151">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="3993d-151">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `WaitCountIfHighMemory`  
 <span data-ttu-id="3993d-152">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="3993d-152">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3993d-153">参照</span><span class="sxs-lookup"><span data-stu-id="3993d-153">See Also</span></span>  
 <span data-ttu-id="3993d-154">[Analysis Services でのサーバープロパティの構成](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="3993d-154">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="3993d-155">Analysis Services インスタンスのサーバー モードの決定</span><span class="sxs-lookup"><span data-stu-id="3993d-155">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
