---
title: リモートパーティション |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- storage [Analysis Services], partitions
- archiving remote partitions [Analysis Services]
- partitions [Analysis Services], remote
- restoring remote partitions [Analysis Services]
- backing up remote partitions [Analysis Services]
- partitions [Analysis Services], storage
- storing data [Analysis Services], partitions
- remote partitions [Analysis Services]
ms.assetid: 63f5d9f5-c6b6-4ceb-94fe-7b6c396d10bb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 32fdf05d061d4e1c1da6ec0ef9179ecd12bda172
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716918"
---
# <a name="remote-partitions"></a><span data-ttu-id="47604-102">リモート パーティション</span><span class="sxs-lookup"><span data-stu-id="47604-102">Remote Partitions</span></span>
  <span data-ttu-id="47604-103">リモートパーティションのデータは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] パーティションとその親キューブの定義 (メタデータ) が格納されているインスタンスとは異なる Microsoft のインスタンスに格納されます。</span><span class="sxs-lookup"><span data-stu-id="47604-103">The data of a remote partition is stored on a different instance of Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] than the instance that contains the definitions (metadata) of the partition and its parent cube.</span></span> <span data-ttu-id="47604-104">リモート パーティションは、パーティションとその親キューブが定義されているインスタンスと同じ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスで管理されます。</span><span class="sxs-lookup"><span data-stu-id="47604-104">A remote partition is administered on the same instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] where the partition and its parent cube are defined.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="47604-105">リモートパーティションを格納するには、コンピューターにのインスタンスが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インストールされており、パーティションが定義されているインスタンスと同じ Service Pack レベルが実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="47604-105">To store a remote partition, the computer must have an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] installed and be running the same service pack level as the instance where the partition was defined.</span></span> <span data-ttu-id="47604-106">以前のバージョンの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンス上でのリモート パーティションはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="47604-106">Remote partitions on instances of an earlier version of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] are not supported.</span></span>  
  
 <span data-ttu-id="47604-107">リモート パーティションがメジャー グループに含まれている場合、キューブのメモリおよび CPU 使用率は、メジャー グループ内のすべてのパーティション間で分散されます。</span><span class="sxs-lookup"><span data-stu-id="47604-107">When remote partitions are included in a measure group, the memory and CPU utilization of the cube is distributed across all the partitions in the measure group.</span></span> <span data-ttu-id="47604-108">たとえば、リモート パーティションが単独で、または親キューブの処理の一部として処理される場合、そのパーティションのメモリおよび CPU 使用率の大部分は [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のリモート インスタンスで発生します。</span><span class="sxs-lookup"><span data-stu-id="47604-108">For example, when a remote partition is processed, either alone or as part of parent cube processing, most of the memory and CPU utilization for that partition occurs on the remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="47604-109">リモート パーティションを含んでいるキューブには、書き込み許可ディメンションを含めることができます。ただし、これはキューブのパフォーマンスに影響を及ぼす可能性があります。</span><span class="sxs-lookup"><span data-stu-id="47604-109">A cube that contains remote partitions can contain write-enabled dimensions; however, this may affect performance for the cube.</span></span> <span data-ttu-id="47604-110">書き込み許可ディメンションの詳細については、「[書き込み許可ディメンション](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47604-110">For more information about write-enabled dimensions, see [Write-Enabled Dimensions](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md).</span></span>  
  
## <a name="storage-modes-for-remote-partitions"></a><span data-ttu-id="47604-111">リモート パーティションのストレージ モード</span><span class="sxs-lookup"><span data-stu-id="47604-111">Storage Modes for Remote Partitions</span></span>  
 <span data-ttu-id="47604-112">リモート パーティションでは、ローカル パーティションで使用する多次元 OLAP (MOLAP)、ハイブリッド OLAP (HOLAP)、リレーショナル OLAP (ROLAP) のストレージ型のいずれかを使用できます。</span><span class="sxs-lookup"><span data-stu-id="47604-112">Remote partitions may use any of the storage types used by local partitions: multidimensional OLAP (MOLAP), hybrid OLAP (HOLAP), or relational OLAP (ROLAP).</span></span> <span data-ttu-id="47604-113">リモート パーティションでは、プロアクティブ キャッシュも使用できます。</span><span class="sxs-lookup"><span data-stu-id="47604-113">Remote partitions may also use proactive caching.</span></span> <span data-ttu-id="47604-114">リモート パーティションのストレージ モードに応じて、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のリモート インスタンスに次のデータが格納されます。</span><span class="sxs-lookup"><span data-stu-id="47604-114">Depending on the storage mode of a remote partition, the following data is stored on the remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="47604-115">ストレージ型</span><span class="sxs-lookup"><span data-stu-id="47604-115">Storage Type</span></span>|<span data-ttu-id="47604-116">Data</span><span class="sxs-lookup"><span data-stu-id="47604-116">Data</span></span>|  
|<span data-ttu-id="47604-117">[MOLAP]</span><span class="sxs-lookup"><span data-stu-id="47604-117">MOLAP</span></span>|<span data-ttu-id="47604-118">パーティションの集計と、パーティションのソース データのコピー</span><span class="sxs-lookup"><span data-stu-id="47604-118">The partition's aggregations and a copy of the partition's source data</span></span>|  
|<span data-ttu-id="47604-119">HOLAP</span><span class="sxs-lookup"><span data-stu-id="47604-119">HOLAP</span></span>|<span data-ttu-id="47604-120">パーティションの集計</span><span class="sxs-lookup"><span data-stu-id="47604-120">The partitions aggregations</span></span>|  
|<span data-ttu-id="47604-121">[ROLAP]</span><span class="sxs-lookup"><span data-stu-id="47604-121">ROLAP</span></span>|<span data-ttu-id="47604-122">パーティション データなし</span><span class="sxs-lookup"><span data-stu-id="47604-122">No partition data</span></span>|  
  
 <span data-ttu-id="47604-123">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の複数のインスタンスに格納された複数の MOLAP パーティションまたは HOLAP パーティションがメジャー グループに含まれる場合、キューブでは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のそれらのインスタンス間でメジャー グループのデータを分散します。</span><span class="sxs-lookup"><span data-stu-id="47604-123">If a measure group contains multiple MOLAP or HOLAP partitions stored on multiple instances of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the cube distributes the data in the measure group data among those instances of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="merging-remote-partitions"></a><span data-ttu-id="47604-124">リモート パーティションのマージ</span><span class="sxs-lookup"><span data-stu-id="47604-124">Merging Remote Partitions</span></span>  
 <span data-ttu-id="47604-125">リモート パーティションは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の同一のリモート インスタンスに格納されている他のリモート パーティションとのみマージできます。</span><span class="sxs-lookup"><span data-stu-id="47604-125">Remote partitions can be merged only with other remote partitions that are stored on the same remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="47604-126">パーティションのマージの詳細については、「 [Analysis Services &#40;SSAS-多次元&#41;でのパーティションのマージ](../multidimensional-models/merge-partitions-in-analysis-services-ssas-multidimensional.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47604-126">For more information about merging partitions, see [Merge Partitions in Analysis Services &#40;SSAS - Multidimensional&#41;](../multidimensional-models/merge-partitions-in-analysis-services-ssas-multidimensional.md).</span></span>  
  
## <a name="archiving-and-restoring-remote-partitions"></a><span data-ttu-id="47604-127">リモート パーティションのアーカイブと復元</span><span class="sxs-lookup"><span data-stu-id="47604-127">Archiving and Restoring Remote Partitions</span></span>  
 <span data-ttu-id="47604-128">リモート パーティションのデータのアーカイブまたは復元は、リモート パーティションを格納するデータベースをアーカイブまたは復元するときに行えます。</span><span class="sxs-lookup"><span data-stu-id="47604-128">Data in remote partitions can be archived or restored when the database that stores the remote partition is archived or restored.</span></span> <span data-ttu-id="47604-129">リモート パーティションを復元せずにデータベースを復元する場合、リモート パーティションを処理しないとパーティションのデータを使用できません。</span><span class="sxs-lookup"><span data-stu-id="47604-129">If you restore a database without restoring a remote partition, you must process the remote partition before you can use the data in the partition.</span></span> <span data-ttu-id="47604-130">データベースのアーカイブと復元の詳細については、「 [Analysis Services データベースのバックアップと復元](../multidimensional-models/backup-and-restore-of-analysis-services-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47604-130">For more information about archiving and restoring databases, see [Backup and Restore of Analysis Services Databases](../multidimensional-models/backup-and-restore-of-analysis-services-databases.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47604-131">参照</span><span class="sxs-lookup"><span data-stu-id="47604-131">See Also</span></span>  
 <span data-ttu-id="47604-132">[リモートパーティション &#40;Analysis Services の作成と管理&#41;](../multidimensional-models/create-and-manage-a-remote-partition-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="47604-132">[Create and Manage a Remote Partition &#40;Analysis Services&#41;](../multidimensional-models/create-and-manage-a-remote-partition-analysis-services.md) </span></span>  
 [<span data-ttu-id="47604-133">Analysis Services オブジェクトの処理</span><span class="sxs-lookup"><span data-stu-id="47604-133">Processing Analysis Services Objects</span></span>](../multidimensional-models/processing-analysis-services-objects.md)  
  
  
