---
title: 機能のプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SQMSupportEnabled property
- ComUdfEnabled property
- LinkToOtherInstanceEnabled property
- ManagedCodeEnabled property
- ConnStringEncryptionEnabled property
- LinkFromOtherInstanceEnabled property
- LinkInsideInstanceEnabled property
- UseCachedPageAllocators property
ms.assetid: a34d046a-6562-4d98-b827-37cebc6d77b4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 08001a172c1b39fb912ef042ed85effd4f8ededa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743505"
---
# <a name="feature-properties"></a><span data-ttu-id="d3794-102">機能プロパティ</span><span class="sxs-lookup"><span data-stu-id="d3794-102">Feature Properties</span></span>
  <span data-ttu-id="d3794-103">機能プロパティは、製品の機能に関連しており、そのほとんどが詳細プロパティです。サーバー インスタンス間のリンクを制御するプロパティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d3794-103">Feature properties pertain to product features, most of them advanced, including properties that control links between server instances.</span></span>  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="d3794-104">では、次の表に示すサーバー プロパティがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d3794-104">supports the server properties listed in the following table.</span></span> <span data-ttu-id="d3794-105">その他のサーバー プロパティとその設定方法の詳細については、「 [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3794-105">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
 <span data-ttu-id="d3794-106">**適用対象:** 多次元サーバーモードのみ</span><span class="sxs-lookup"><span data-stu-id="d3794-106">**Applies to:** Multidimensional server mode only</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d3794-107">Properties</span><span class="sxs-lookup"><span data-stu-id="d3794-107">Properties</span></span>  
  
|<span data-ttu-id="d3794-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d3794-108">Property</span></span>|<span data-ttu-id="d3794-109">Default</span><span class="sxs-lookup"><span data-stu-id="d3794-109">Default</span></span>|<span data-ttu-id="d3794-110">説明</span><span class="sxs-lookup"><span data-stu-id="d3794-110">Description</span></span>|  
|--------------|-------------|-----------------|  
|`ManagedCodeEnabled`|<span data-ttu-id="d3794-111">1</span><span class="sxs-lookup"><span data-stu-id="d3794-111">1</span></span>|<span data-ttu-id="d3794-112">CLR ストレージ手順が有効かどうかを示す、ブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="d3794-112">A Boolean property that indicates whether CLR storage procedures are enabled.</span></span>|  
|`LinkInsideInstanceEnabled`|<span data-ttu-id="d3794-113">1</span><span class="sxs-lookup"><span data-stu-id="d3794-113">1</span></span>|<span data-ttu-id="d3794-114">リンク オブジェクトを同じサーバー インスタンス内で作成できるかどうかを示す、ブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="d3794-114">A Boolean property that indicates whether a linked object can be created inside the same server instance.</span></span>|  
|`LinkToOtherInstanceEnabled`|<span data-ttu-id="d3794-115">0</span><span class="sxs-lookup"><span data-stu-id="d3794-115">0</span></span>|<span data-ttu-id="d3794-116">リモート サーバー上のオブジェクトにリンクできるかどうかを示す、ブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="d3794-116">A Boolean property that indicates whether objects on remote servers can be linked to.</span></span>|  
|`LinkFromOtherInstanceEnabled`|<span data-ttu-id="d3794-117">0</span><span class="sxs-lookup"><span data-stu-id="d3794-117">0</span></span>|<span data-ttu-id="d3794-118">他のサーバー インスタンスからオブジェクトにリンクできるかどうかを示す、ブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="d3794-118">A Boolean property that indicates whether objects can be linked to from other server instances.</span></span>|  
|`ConnStringEncryptionEnabled`|<span data-ttu-id="d3794-119">1</span><span class="sxs-lookup"><span data-stu-id="d3794-119">1</span></span>|<span data-ttu-id="d3794-120">接続文字列がサーバー構成ファイル内で暗号化されているかどうかを示す、ブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="d3794-120">A Boolean property that indicates whether the connection string is encrypted in the server configuration file.</span></span>|  
|`UseCachedPageAllocators`|<span data-ttu-id="d3794-121">0</span><span class="sxs-lookup"><span data-stu-id="d3794-121">0</span></span>|<span data-ttu-id="d3794-122">キャッシュ ページ アロケーターが有効かどうかを示す、ブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="d3794-122">A Boolean property that indicates whether cached page allocators are enabled.</span></span>|  
|`ComUdfEnabled`|<span data-ttu-id="d3794-123">0</span><span class="sxs-lookup"><span data-stu-id="d3794-123">0</span></span>|<span data-ttu-id="d3794-124">COM オブジェクトとして定義されているユーザー定義関数が有効かどうかを示す、ブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="d3794-124">A Boolean property that indicates whether user-defined functions defined as COM objects are enabled.</span></span>|  
|`SQMSupportEnabled`|<span data-ttu-id="d3794-125">1</span><span class="sxs-lookup"><span data-stu-id="d3794-125">1</span></span>|<span data-ttu-id="d3794-126">エラー レポートおよび機能の使用状況レポートが [!INCLUDE[msCoName](../../includes/msconame-md.md)] に自動的に送信されるかどうかを示す、ブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="d3794-126">A Boolean property that indicates whether error and feature usage reports are sent to [!INCLUDE[msCoName](../../includes/msconame-md.md)] automatically.</span></span>|  
|`ResourceMonitoringEnabled`|<span data-ttu-id="d3794-127">1</span><span class="sxs-lookup"><span data-stu-id="d3794-127">1</span></span>|<span data-ttu-id="d3794-128">内部リソース監視カウンターが有効かどうかを示す、ブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="d3794-128">A Boolean property that indicates whether internal resource monitoring counters are enabled.</span></span> <span data-ttu-id="d3794-129">既定では、このプロパティは有効です。</span><span class="sxs-lookup"><span data-stu-id="d3794-129">This property is on by default.</span></span> <span data-ttu-id="d3794-130">有効である場合、このプロパティは、カウンターが CPU、メモリ、および I/O アクティビティに関する使用状況データを収集できるようにします。</span><span class="sxs-lookup"><span data-stu-id="d3794-130">When enabled, this property allows counters to collect usage data about CPU, memory, and I/O activity.</span></span><br /><br /> <span data-ttu-id="d3794-131">内部リソース監視カウンターは、リソース使用状況について報告する動的管理ビュー (DMV) によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="d3794-131">Internal resource monitoring counters are used by Dynamic Management Views (DMV) that report on resource utilization.</span></span> <span data-ttu-id="d3794-132">このプロパティを無効にすると、DMV クエリは引き続き実行されますが、結果セットは無効になります。</span><span class="sxs-lookup"><span data-stu-id="d3794-132">If you disable this property, the DMV queries will still run, but the result set will be invalid.</span></span> <span data-ttu-id="d3794-133">このプロパティに依存するのは、次のような DMV です。</span><span class="sxs-lookup"><span data-stu-id="d3794-133">DMVs that depend on this property include the following:</span></span><br /><span data-ttu-id="d3794-134">**DISCOVER_OBJECT_ACTIVITY**</span><span class="sxs-lookup"><span data-stu-id="d3794-134">**DISCOVER_OBJECT_ACTIVITY**</span></span><br /><span data-ttu-id="d3794-135">**DISCOVER_COMMAND_OBJECTS**</span><span class="sxs-lookup"><span data-stu-id="d3794-135">**DISCOVER_COMMAND_OBJECTS**</span></span><br /><span data-ttu-id="d3794-136">**DISCOVER_SESSIONS** (SESSION_READS、SESSION_WRITES、SESSION_CPU_TIME_MS の場合)</span><span class="sxs-lookup"><span data-stu-id="d3794-136">**DISCOVER_SESSIONS** (for SESSION_READS, SESSION_WRITES, SESSION_CPU_TIME_MS)</span></span><br /><br /> <br /><br /> <span data-ttu-id="d3794-137">NUMA アーキテクチャを使用するマルチコア システムでは、このプロパティを無効にすると、特にマルチユーザーのワークロードが高い場合に、クエリのパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="d3794-137">On a multi-core system that uses NUMA architecture, disabling this property can improve query performance, particularly for high multi-user workloads.</span></span> <span data-ttu-id="d3794-138">このプロパティを変更したためにクエリのパフォーマンスが向上したかどうかを判断するには、比較テストを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3794-138">You will need to run comparison tests to determine whether query performance is improved as the result of changing this property.</span></span> <span data-ttu-id="d3794-139">キャッシュの消去、一般的な間違いの回避など、比較テストの実行に関するベスト プラクティスについては、「 [SQL Server 2008 R2 Analysis Services 操作ガイド](https://go.microsoft.com/fwlink/?LinkID=225539)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3794-139">For best practices on running comparison tests, including clearing the cache and avoiding common mistakes, see the [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3794-140">参照</span><span class="sxs-lookup"><span data-stu-id="d3794-140">See Also</span></span>  
 <span data-ttu-id="d3794-141">[Analysis Services でのサーバープロパティの構成](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="d3794-141">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 <span data-ttu-id="d3794-142">[Analysis Services インスタンスのサーバーモードの決定](../instances/determine-the-server-mode-of-an-analysis-services-instance.md) </span><span class="sxs-lookup"><span data-stu-id="d3794-142">[Determine the Server Mode of an Analysis Services Instance](../instances/determine-the-server-mode-of-an-analysis-services-instance.md) </span></span>  
 [<span data-ttu-id="d3794-143">動的管理ビュー (DMV) を使用した Analysis Services の監視</span><span class="sxs-lookup"><span data-stu-id="d3794-143">Use Dynamic Management Views &#40;DMVs&#41; to Monitor Analysis Services</span></span>](../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  
