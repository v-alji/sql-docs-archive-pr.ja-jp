---
title: '[ウィザードの完了] (パーティションウィザード)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionwizard.finish.f1
ms.assetid: 68a4dd5d-94d9-4a02-be31-949a6da0ef51
author: minewiskan
ms.author: owend
ms.openlocfilehash: d60be28170e8f8ec156d1c37149ddbc04b64bf8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633504"
---
# <a name="completing-the-wizard-partition-wizard"></a><span data-ttu-id="845bd-102">[ウィザードの完了] (パーティション ウィザード)</span><span class="sxs-lookup"><span data-stu-id="845bd-102">Completing the Wizard (Partition Wizard)</span></span>
  <span data-ttu-id="845bd-103">**[ウィザードの完了]** ページを使用すると、パーティションの名前の設定とパーティションの集計のデザインを定義できます。必要であれば、パーティション ウィザードの完了後にパーティションを配置し、処理することもできます。</span><span class="sxs-lookup"><span data-stu-id="845bd-103">Use the **Completing the Wizard** page to name the partition, define the aggregation design for your partition, and optionally deploy and process the partition after completing the Partition Wizard.</span></span>  
  
## <a name="options"></a><span data-ttu-id="845bd-104">Options</span><span class="sxs-lookup"><span data-stu-id="845bd-104">Options</span></span>  
 <span data-ttu-id="845bd-105">**名前**</span><span class="sxs-lookup"><span data-stu-id="845bd-105">**Name**</span></span>  
 <span data-ttu-id="845bd-106">新しいパーティションの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="845bd-106">Type the name for the new partition.</span></span> <span data-ttu-id="845bd-107">複数のテーブルを使用する場合、プレフィックスを入力します。このプレフィックスとテーブル名を組み合わせて、各パーティションの名前が作成されます。</span><span class="sxs-lookup"><span data-stu-id="845bd-107">If you are working with multiple tables, enter the prefix that will be combined with the table name to create each partition name.</span></span>  
  
 <span data-ttu-id="845bd-108">**[集計オプション]**</span><span class="sxs-lookup"><span data-stu-id="845bd-108">**Aggregation options**</span></span>  
 <span data-ttu-id="845bd-109">パーティションの集計オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="845bd-109">Specifies the aggregation option for the partition.</span></span>  
  
 <span data-ttu-id="845bd-110">次の表に、選択できる集計オプションを示します。</span><span class="sxs-lookup"><span data-stu-id="845bd-110">The following table lists the aggregation options that are available.</span></span>  
  
|<span data-ttu-id="845bd-111">オプション</span><span class="sxs-lookup"><span data-stu-id="845bd-111">Option</span></span>|<span data-ttu-id="845bd-112">説明</span><span class="sxs-lookup"><span data-stu-id="845bd-112">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="845bd-113">**[ここでパーティションの集計をデザインする]**</span><span class="sxs-lookup"><span data-stu-id="845bd-113">**Design aggregations for the partition now**</span></span>|<span data-ttu-id="845bd-114">パーティション ウィザードで新しいパーティションを作成した後で、そのパーティションの集計をデザインします。</span><span class="sxs-lookup"><span data-stu-id="845bd-114">Designs aggregations for the new partition after the Partition Wizard creates the new partition.</span></span> <span data-ttu-id="845bd-115">このオプションを選択した場合、パーティション ウィザードで **[完了]** をクリックすると集計のデザイン ウィザードが起動します。</span><span class="sxs-lookup"><span data-stu-id="845bd-115">Selecting this option starts the Aggregation Design Wizard after you click **Finish** in the Partition Wizard.</span></span> <span data-ttu-id="845bd-116">集計のデザイン ウィザードの詳細については、「 [集計のデザイン ウィザードの F1 ヘルプ](aggregation-design-wizard-f1-help.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="845bd-116">For more information about the Aggregation Design Wizard, see [Aggregation Design Wizard F1 Help](aggregation-design-wizard-f1-help.md).</span></span>|  
|<span data-ttu-id="845bd-117">**[後で集計をデザインする]**</span><span class="sxs-lookup"><span data-stu-id="845bd-117">**Design the aggregations later**</span></span>|<span data-ttu-id="845bd-118">ここでは集計をデザインせずに、パーティションを作成します。</span><span class="sxs-lookup"><span data-stu-id="845bd-118">Creates the partition without designing aggregations at this time.</span></span>|  
|<span data-ttu-id="845bd-119">**[既存のパーティションから集計のデザインをコピーする]**</span><span class="sxs-lookup"><span data-stu-id="845bd-119">**Copy the aggregation design from an existing partition**</span></span>|<span data-ttu-id="845bd-120">メジャー グループの既存のパーティションから新しいパーティションに、集計のデザインをコピーします。</span><span class="sxs-lookup"><span data-stu-id="845bd-120">Copies the aggregation design from an existing partition in the measure group to the new partition.</span></span> <span data-ttu-id="845bd-121">このオプションをクリックすると、 **[コピー元]** オプションが有効になります。</span><span class="sxs-lookup"><span data-stu-id="845bd-121">Clicking this option makes the **Copy from** option available.</span></span> <span data-ttu-id="845bd-122">**[コピー元]** オプションを使用して、集計のデザインのコピー元パーティションを選択します。</span><span class="sxs-lookup"><span data-stu-id="845bd-122">Use the **Copy from** option to select the partition from which to copy the aggregation design.</span></span><br /><br /> <span data-ttu-id="845bd-123">将来マージされる可能性があるパーティションは、テーブル構造と集計デザインが同じであることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="845bd-123">Note that partitions that may be merged in the future must have the same table structure and aggregation design.</span></span> <span data-ttu-id="845bd-124">新しいパーティションをメジャー グループの既存のパーティションとマージする可能性がある場合、既存のパーティションから新しいパーティションに、集計のデザインをコピーしておきます。</span><span class="sxs-lookup"><span data-stu-id="845bd-124">If you might merge the new partition with an existing partition in the measure group, you should copy the aggregation design of the existing partition into the new partition.</span></span>|  
  
 <span data-ttu-id="845bd-125">**[今すぐ配置して処理する]**</span><span class="sxs-lookup"><span data-stu-id="845bd-125">**Deploy and Process Now**</span></span>  
 <span data-ttu-id="845bd-126">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]\*\*\*\* インスタンスにパーティションを配置し、処理します。</span><span class="sxs-lookup"><span data-stu-id="845bd-126">Deploys and processes the partition to the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance specified on the **Processing and Storage Locations** page.</span></span> <span data-ttu-id="845bd-127">このページの **[完了]** をクリックすると、パーティションが配置されて処理されます。</span><span class="sxs-lookup"><span data-stu-id="845bd-127">The wizard deploys and processes the partition after you click **Finish** on this page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="845bd-128">参照</span><span class="sxs-lookup"><span data-stu-id="845bd-128">See Also</span></span>  
 [<span data-ttu-id="845bd-129">パーティション (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="845bd-129">Partitions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  
