---
title: パーティションスライスプロパティの設定 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 08/05/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- partitions [Analysis Services], data slices
- data slices [Analysis Services]
ms.assetid: 507b91e5-7f85-4c22-be97-4d7a676e6667
author: minewiskan
ms.author: owend
ms.openlocfilehash: f42c4536b99ba3fecf9b947942b881a3be72784f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642979"
---
# <a name="set-the-partition-slice-property-analysis-services"></a><span data-ttu-id="7b388-102">パーティション スライス プロパティの設定 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="7b388-102">Set the Partition Slice Property (Analysis Services)</span></span>
  <span data-ttu-id="7b388-103">データ スライスとは、該当するパーティションのデータに対する直接的なクエリを円滑に行うための重要な最適化機能です。</span><span class="sxs-lookup"><span data-stu-id="7b388-103">A data slice is an important optimization feature that helps direct queries to the data of the appropriate partitions.</span></span> <span data-ttu-id="7b388-104">Slice プロパティを明示的に設定すると、MOLAP パーティションと HOLAP パーティションに対して生成される既定のスライスがオーバーライドされるため、クエリのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="7b388-104">Explicitly setting the Slice property can improve query performance by overriding default slices generated for MOLAP and HOLAP partitions.</span></span> <span data-ttu-id="7b388-105">また、Slice プロパティによって、パーティションの処理時に追加の検証チェックが提供されます。</span><span class="sxs-lookup"><span data-stu-id="7b388-105">Additionally, the Slice property provides an extra validation check when processing the partition.</span></span>  
  
 <span data-ttu-id="7b388-106">パーティションを作成してから処理するまでに、Slice プロパティを使用してデータ スライスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7b388-106">You can specify a data slice after you create a partition, but before processing it, using the Slice property.</span></span> <span data-ttu-id="7b388-107">[パーティション] タブで、メジャー グループを展開し、パーティションを右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b388-107">On the Partitions tab, expand a measure group, right-click a partition, and select **Properties**.</span></span>  
  
## <a name="defining-a-slice"></a><span data-ttu-id="7b388-108">スライスの定義</span><span class="sxs-lookup"><span data-stu-id="7b388-108">Defining a Slice</span></span>  
 <span data-ttu-id="7b388-109">Slice プロパティに有効な値には、MDX メンバー、セット、または組があります。</span><span class="sxs-lookup"><span data-stu-id="7b388-109">Valid values for a slice property are an MDX member, set, or tuple.</span></span> <span data-ttu-id="7b388-110">有効なスライス構文の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7b388-110">The following examples illustrate valid slice syntax:</span></span>  
  
|<span data-ttu-id="7b388-111">スライス</span><span class="sxs-lookup"><span data-stu-id="7b388-111">Slice</span></span>|<span data-ttu-id="7b388-112">メンバー、セット、または組</span><span class="sxs-lookup"><span data-stu-id="7b388-112">Member, set or tuple</span></span>|  
|-----------|--------------------------|  
|<span data-ttu-id="7b388-113">[Date].[Calendar].[Calendar Year].&[2010]</span><span class="sxs-lookup"><span data-stu-id="7b388-113">[Date].[Calendar].[Calendar Year].&[2010]</span></span>|<span data-ttu-id="7b388-114">2010 年のファクトを含むパーティションにこのスライスを指定します (モデルに Calendar Year 階層の Date ディメンションが含まれていていることを前提。2010 はメンバー)。</span><span class="sxs-lookup"><span data-stu-id="7b388-114">Specify this slice on a partition containing facts from year 2010 (assuming the model includes a Date dimension with Calendar Year hierarchy, where 2010 is a member).</span></span> <span data-ttu-id="7b388-115">パーティション ソースの WHERE 句またはテーブルが既に 2010 でフィルター処理されている可能性がありますが、Slice を指定すると、処理中に追加のチェック、クエリの実行中に対象を絞ったスキャンが実行されます。</span><span class="sxs-lookup"><span data-stu-id="7b388-115">Although the partition source WHERE clause or table might already filter by 2010, specifying the Slice provides an additional check during processing, as well as more targeted scans during query execution.</span></span>|  
|<span data-ttu-id="7b388-116">{ [Sales Territory].[Sales Territory Country].&[Australia], [Sales Territory].[Sales Territory Country].&[Canada] }</span><span class="sxs-lookup"><span data-stu-id="7b388-116">{ [Sales Territory].[Sales Territory Country].&[Australia], [Sales Territory].[Sales Territory Country].&[Canada] }</span></span>|<span data-ttu-id="7b388-117">販売区域情報を含むファクトが含まれるパーティションにこのスライスを指定します。</span><span class="sxs-lookup"><span data-stu-id="7b388-117">Specify this slice on a partition containing facts that include sales territory information.</span></span> <span data-ttu-id="7b388-118">スライスには、複数のメンバーで構成される MDX セットを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7b388-118">A slice can be an MDX set consisting of two or more members.</span></span>|  
|<span data-ttu-id="7b388-119">[Measures].[Sales Amount Quota] > '5000'</span><span class="sxs-lookup"><span data-stu-id="7b388-119">[Measures].[Sales Amount Quota] > '5000'</span></span>|<span data-ttu-id="7b388-120">このスライスは MDX 式を表します。</span><span class="sxs-lookup"><span data-stu-id="7b388-120">This slice shows an MDX expression.</span></span>|  
  
 <span data-ttu-id="7b388-121">パーティションのデータ スライスは、そのパーティションに含まれるデータを可能な限り類似した形で反映します。</span><span class="sxs-lookup"><span data-stu-id="7b388-121">A data slice of a partition should reflect, as closely as possible, the data in the partition.</span></span> <span data-ttu-id="7b388-122">たとえば、パーティションが 2012 年のデータに限定されている場合、そのパーティションのデータ スライスは時間ディメンションの 2012 メンバーを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b388-122">For example, if a partition is limited to 2012 data, the partition's data slice should specify the 2012 member of the Time dimension.</span></span> <span data-ttu-id="7b388-123">常にパーティションの内容を正確に反映するデータ スライスを指定できるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="7b388-123">It is not always possible to specify a data slice that reflects the exact contents of a partition.</span></span> <span data-ttu-id="7b388-124">たとえば、パーティションに含まれるデータが January (1 月) と February (2 月) のデータだけであっても、時間ディメンションのレベルが Year、Quarter、および Month である場合、パーティション ウィザードでは January メンバーと February メンバーを選択できません。</span><span class="sxs-lookup"><span data-stu-id="7b388-124">For example, if a partition contains data for only January and February, but the levels of the Time dimension are Year, Quarter, and Month, the Partition Wizard cannot select both the January and February members.</span></span> <span data-ttu-id="7b388-125">このような場合は、パーティションの内容を反映するメンバーの親を選択します。</span><span class="sxs-lookup"><span data-stu-id="7b388-125">In such cases, select the parent of the members that reflect the partition's contents.</span></span> <span data-ttu-id="7b388-126">この例では、Quarter&#xA0;1 を選択します。</span><span class="sxs-lookup"><span data-stu-id="7b388-126">In this example, select Quarter 1.</span></span>  
  
 <span data-ttu-id="7b388-127">データ スライスの利点については、「 [SSAS キューブ パーティションにスライスを設定する](https://go.microsoft.com/fwlink/?LinkId=317783)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b388-127">For an explanation of data slice benefits, see [Set the Slice on your SSAS Cube Partition](https://go.microsoft.com/fwlink/?LinkId=317783).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7b388-128">動的 MDX 関数 ([Generate (MDX)](/sql/mdx/generate-mdx) または [Except (MDX)](/sql/mdx/except-mdx-function) など) はパーティションの Slice プロパティでサポートされていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7b388-128">Note that dynamic MDX functions (such as [Generate &#40;MDX&#41;](/sql/mdx/generate-mdx) or [Except &#40;MDX&#41;](/sql/mdx/except-mdx-function)) are not supported in the Slice property for partitions.</span></span> <span data-ttu-id="7b388-129">明示的な組またはメンバー参照を使用して、スライスを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b388-129">You must define the slice by using explicit tuples or member references.</span></span>  
>   
>  <span data-ttu-id="7b388-130">たとえば、範囲を定義するために、 [MDX&#41;関数&#41; &#40;: &#40;範囲](/sql/mdx/range-mdx)を使用するのではなく、特定の年で各メンバーを列挙する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b388-130">For example, rather than using the [: &#40;Range&#41; &#40;MDX&#41;](/sql/mdx/range-mdx) function to define a range, you would need to enumerate each member by the specific years.</span></span>  
>   
>  <span data-ttu-id="7b388-131">複雑なスライスを定義する必要がある場合は、XMLA Alter スクリプトを使用して、スライスで組を定義することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7b388-131">If you need to define a complex slice, we recommend that you define the tuples in the slice by using an XMLA Alter script.</span></span> <span data-ttu-id="7b388-132">続けて、ascmd コマンド ライン ツールまたは SSIS [Analysis Services Execute DDL Task](../../integration-services/control-flow/analysis-services-execute-ddl-task.md) タスクを使用してスクリプトを実行し、指定したメンバーのセットをパーティション処理の直前に作成します。</span><span class="sxs-lookup"><span data-stu-id="7b388-132">Then, you can use either the ascmd command-line tool or the SSIS [Analysis Services Execute DDL Task](../../integration-services/control-flow/analysis-services-execute-ddl-task.md) task to run the script and create the specified set of members immediately before you process the partition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b388-133">参照</span><span class="sxs-lookup"><span data-stu-id="7b388-133">See Also</span></span>  
 [<span data-ttu-id="7b388-134">ローカル パーティションの作成と管理 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="7b388-134">Create and Manage a Local Partition &#40;Analysis Services&#41;</span></span>](create-and-manage-a-local-partition-analysis-services.md)  
  
  
