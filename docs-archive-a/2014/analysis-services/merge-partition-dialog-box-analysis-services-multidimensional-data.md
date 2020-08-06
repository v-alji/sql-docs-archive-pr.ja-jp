---
title: '[パーティションのマージ] ダイアログボックス (Analysis Services 多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.mergepartition.f1
ms.assetid: 1c94e250-ee18-4f98-b112-985f6346102a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1978c187bfb5097d286f78650b5bda6645c7a054
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644203"
---
# <a name="merge-partition-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="592b9-102">[パーティションのマージ] ダイアログ ボックス (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="592b9-102">Merge Partition Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="592b9-103">**SQL Server Management Studio** の **[パーティションのマージ]** ダイアログ ボックスを使用すると、キューブ内のメジャー グループのパーティションをマージできます。</span><span class="sxs-lookup"><span data-stu-id="592b9-103">Use the **Merge Partition** dialog box in **SQL Server Management Studio** to merge partitions for a measure group in a cube.</span></span> <span data-ttu-id="592b9-104">**[パーティションのマージ]** ダイアログ ボックスを表示するには、 **オブジェクト エクスプローラー** で [パーティション] フォルダーまたはパーティションを右クリックし、ショートカット メニューの **[パーティションのマージ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="592b9-104">You can display the **Merge Partition** dialog box by right-clicking the Partitions folder or a partition in **Object Explorer** and selecting **Merge Partitions** from the context menu.</span></span>  
  
## <a name="options"></a><span data-ttu-id="592b9-105">Options</span><span class="sxs-lookup"><span data-stu-id="592b9-105">Options</span></span>  
 <span data-ttu-id="592b9-106">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="592b9-106">**Server**</span></span>  
 <span data-ttu-id="592b9-107">対象パーティションを含む Analysis Services インスタンスの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="592b9-107">Select the name of the Analysis Services instance that contains the target partition.</span></span>  
  
 <span data-ttu-id="592b9-108">**名前**</span><span class="sxs-lookup"><span data-stu-id="592b9-108">**Name**</span></span>  
 <span data-ttu-id="592b9-109">対象パーティションとして使用する既存のパーティションの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="592b9-109">Select the name of an existing partition to use as the target partition.</span></span>  
  
 <span data-ttu-id="592b9-110">**フォルダー**</span><span class="sxs-lookup"><span data-stu-id="592b9-110">**Folder**</span></span>  
 <span data-ttu-id="592b9-111">[名前] で選択されたパーティションで Analysis Services インスタンスの既定のフォルダーが使用されていない場合は、ターゲット パーティションが含まれるフォルダーの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="592b9-111">Displays the name of the folder that contains the target partition, if the partition selected in Name does not use the default folder for the Analysis Services instance.</span></span>  
  
 <span data-ttu-id="592b9-112">**[基になるパーティション]**</span><span class="sxs-lookup"><span data-stu-id="592b9-112">**Source Partitions**</span></span>  
 <span data-ttu-id="592b9-113">対象パーティションにマージ可能な、基になるパーティションが含まれているグリッドを表示します。</span><span class="sxs-lookup"><span data-stu-id="592b9-113">Displays a grind containing the source partitions that can be merged into the target partition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="592b9-114">マージできるパーティションは、同じメジャー グループに属し同じ集計デザインを共有するパーティションだけです。</span><span class="sxs-lookup"><span data-stu-id="592b9-114">Only partitions in the same measure group that share the same aggregation design can be merged.</span></span>  
  
 <span data-ttu-id="592b9-115">このグリッドには次の列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="592b9-115">The grid contains the following columns:</span></span>  
  
|<span data-ttu-id="592b9-116">列</span><span class="sxs-lookup"><span data-stu-id="592b9-116">Column</span></span>|<span data-ttu-id="592b9-117">説明</span><span class="sxs-lookup"><span data-stu-id="592b9-117">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="592b9-118">**[マージ]**</span><span class="sxs-lookup"><span data-stu-id="592b9-118">**Merge**</span></span>|<span data-ttu-id="592b9-119">選択すると、基になるパーティションを対象パーティションにマージできます。</span><span class="sxs-lookup"><span data-stu-id="592b9-119">Select to merge the source partition into the target partition.</span></span>|  
|<span data-ttu-id="592b9-120">**[パーティション名]**</span><span class="sxs-lookup"><span data-stu-id="592b9-120">**Partition Name**</span></span>|<span data-ttu-id="592b9-121">基になるパーティションの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="592b9-121">Displays the name of the source partition.</span></span>|  
|<span data-ttu-id="592b9-122">**[最終処理]**</span><span class="sxs-lookup"><span data-stu-id="592b9-122">**Last Processed**</span></span>|<span data-ttu-id="592b9-123">基になるパーティションが最後に処理された日時を表示します。</span><span class="sxs-lookup"><span data-stu-id="592b9-123">Displays the date and time at which the source partition was last processed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="592b9-124">参照</span><span class="sxs-lookup"><span data-stu-id="592b9-124">See Also</span></span>  
 <span data-ttu-id="592b9-125">[パーティション &#40;Analysis Services-多次元データ&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="592b9-125">[Partitions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="592b9-126">Analysis Services でのパーティションのマージ (SSAS - 多次元)</span><span class="sxs-lookup"><span data-stu-id="592b9-126">Merge Partitions in Analysis Services &#40;SSAS - Multidimensional&#41;</span></span>](multidimensional-models/merge-partitions-in-analysis-services-ssas-multidimensional.md)  
  
  
