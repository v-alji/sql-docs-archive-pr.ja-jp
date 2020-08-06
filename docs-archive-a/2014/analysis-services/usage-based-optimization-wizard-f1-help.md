---
title: 使用法に基づく最適化ウィザードの F1 ヘルプ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.usagebasedoptimizationwizard.f1
helpviewer_keywords:
- Usage-Based Optimization Wizard
ms.assetid: e5f5a938-ae7c-4f4e-9416-a7f94ac82763
author: minewiskan
ms.author: owend
ms.openlocfilehash: 517c122f79421294e1dfa562665948c4dc7bf95f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720354"
---
# <a name="usage-based-optimization-wizard-f1-help"></a><span data-ttu-id="27c5d-102">使用法に基づく最適化ウィザードの F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="27c5d-102">Usage-Based Optimization Wizard F1 Help</span></span>
  <span data-ttu-id="27c5d-103">使用法に基づく最適化ウィザードを使用するとパーティションの集計をデザインすることができ、その出力は集計のデザイン ウィザードに似ています。</span><span class="sxs-lookup"><span data-stu-id="27c5d-103">The Usage-Based Optimization Wizard is similar in output to the Aggregation Design Wizard, and is used to design aggregations for a partition.</span></span> <span data-ttu-id="27c5d-104">ただし、使用法に基づく最適化ウィザードでは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスのクエリ ログに記録されているクエリの特定の使用パターンに基づいて集計をデザインします。</span><span class="sxs-lookup"><span data-stu-id="27c5d-104">However, the Usage-Based Optimization Wizard designs aggregations based on the specific usage patterns of queries recorded in the query log of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="27c5d-105">集計を使用すると、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] クエリごとに基になるデータソースのデータを再計算するのではなく、キューブストレージから事前計算済みの合計を直接取得できるため、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="27c5d-105">Aggregations provide performance improvements by allowing [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to retrieve pre-calculated totals directly from cube storage instead of having to recalculate data from an underlying data source for each query.</span></span>  
  
 <span data-ttu-id="27c5d-106">内から使用法に基づく最適化ウィザードを開くには、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] プロジェクトのキューブデザイナーを開き、[ [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] **集計**] タブをクリックします。ツールバーの [**使用法に基づく最適化**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="27c5d-106">To open the Usage-Based Optimization Wizard from within [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the cube designer for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, and then click the **Aggregations** tab. Click the **Usage Based Optimization** button in the toolbar.</span></span>  
  
 <span data-ttu-id="27c5d-107">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]内から使用法に基づく最適化ウィザードを開くには、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースに接続し、 **[キューブ]** フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="27c5d-107">To open the Usage-Based Optimization Wizard from within [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], connect to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database and then open the **Cubes** folder.</span></span> <span data-ttu-id="27c5d-108">キューブを選択して **[メジャー グループ]** フォルダーを開き、変更するメジャー グループを展開します。</span><span class="sxs-lookup"><span data-stu-id="27c5d-108">Select a cube and then open the **Measure Groups** folder and expand the measure group that you want to modify.</span></span> <span data-ttu-id="27c5d-109">**[パーティション]** フォルダーを右クリックし、 **[使用法に基づく最適化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="27c5d-109">Right-click the **Partitions** folder and then select **Usage Based Optimization**.</span></span>  
  
 <span data-ttu-id="27c5d-110">こうした集計のデザインは、集計のデザイン ウィザードを使用して行います。</span><span class="sxs-lookup"><span data-stu-id="27c5d-110">To design these aggregations, you can use the Aggregation Design Wizard.</span></span> <span data-ttu-id="27c5d-111">このウィザードでは、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="27c5d-111">This wizard guides you through the following steps:</span></span>  
  
-   <span data-ttu-id="27c5d-112">パーティション、メジャー グループ、またはキューブのストレージとキャッシュのオプションに対して、標準またはカスタムの設定を選択します。</span><span class="sxs-lookup"><span data-stu-id="27c5d-112">Selecting standard or custom settings for the storage and caching options of a partition, measure group, or cube.</span></span>  
  
-   <span data-ttu-id="27c5d-113">パーティション、メジャー グループ、またはキューブによって参照されるオブジェクトの推定カウントまたは実際のカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="27c5d-113">Providing estimated or actual counts for objects referenced by the partition, measure group, or cube.</span></span>  
  
-   <span data-ttu-id="27c5d-114">集計オプションと制限を指定して、デザインされた集計によって配信されるストレージとクエリのパフォーマンスを最適化します。</span><span class="sxs-lookup"><span data-stu-id="27c5d-114">Specifying aggregation options and limits to optimize the storage and query performance delivered by designed aggregations.</span></span>  
  
-   <span data-ttu-id="27c5d-115">パーティション、メジャー グループ、またはキューブの保存と処理 (省略可) を行い、定義された集計を生成します。</span><span class="sxs-lookup"><span data-stu-id="27c5d-115">Saving and optionally processing the partition, measure group, or cube to generate the defined aggregations.</span></span>  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="27c5d-116">の集計のデザイン ウィザードでは、集計デザインを提供するパーティション構造の統計分析に基づいて集計をデザインします。集計をデザインする際には、ストレージ サイズまたはパフォーマンスの推定向上度を制限できます。</span><span class="sxs-lookup"><span data-stu-id="27c5d-116">provides the Aggregation Design Wizard to design aggregations based on statistical analysis of the structure of the partition to deliver an aggregation design that can be limited by storage size or estimated performance gain.</span></span> <span data-ttu-id="27c5d-117">集計のデザイン ウィザードを使用するとパーティションの全体的なパフォーマンスを向上させることができますが、このウィザードの集計デザインはビジネス ユーザーの特定のニーズに合致したものではありません。</span><span class="sxs-lookup"><span data-stu-id="27c5d-117">You can use the Aggregation Design Wizard to improve the overall performance of a partition, but the aggregation design is not targeted to the specific needs of your business users.</span></span> <span data-ttu-id="27c5d-118">使用法に基づく最適化ウィザードでは、こうした特定のニーズに合致した集計デザインが可能ですが、このためには [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスのクエリ ログに、こうしたクエリを構築するための十分な情報が記録されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="27c5d-118">The Usage-Based Optimization Wizard can provide an aggregation design targeted to these specific needs, but the wizard can do so only if the query log for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance contains enough information to construct such queries.</span></span>  
  
 <span data-ttu-id="27c5d-119">通常、両方のウィザードを併用することで、配置後のパフォーマンスと長期的なパフォーマンスを向上させます。</span><span class="sxs-lookup"><span data-stu-id="27c5d-119">Typically, both wizards are used together to improve performance both upon deployment and over time.</span></span> <span data-ttu-id="27c5d-120">パーティション (または、パーティションを含むキューブやメジャー グループ) を最初に配置するときに、まず集計のデザイン ウィザードを使用して全体的なパフォーマンスを向上させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="27c5d-120">The Aggregation Design Wizard should be used first, when the partition (or the cube or measure group containing the partition) is initially deployed, to provide an overall performance benefit.</span></span> <span data-ttu-id="27c5d-121">その後、一定期間が経過してパーティションに対するビジネス ユーザーのクエリがクエリ ログに記録されたら、使用法に基づく最適化ウィザードを使用します。これにより、ビジネス ユーザーのクエリ要件に適応した、よりパフォーマンスの高い集計デザインを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="27c5d-121">After a period of time during which you have recorded the queries of business users for the partition in the query log, you can then use the Usage-Based Optimization Wizard to further focus the aggregation design to better serve the performance and query requirements of your business users.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="27c5d-122">クエリ ログの構成については、「 [Analysis Services クエリ ログの構成](instances/log-operations-in-analysis-services.md?view=sql-server-2014#bkmk_querylog)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="27c5d-122">For information about configuring the query log, see [Configuring the Analysis Services Query Log](instances/log-operations-in-analysis-services.md?view=sql-server-2014#bkmk_querylog).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="27c5d-123">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="27c5d-123">In This Section</span></span>  
  
-   [<span data-ttu-id="27c5d-124">使用法に基づく最適化ウィザード &#40;変更するパーティションの選択&#41;</span><span class="sxs-lookup"><span data-stu-id="27c5d-124">Select Partitions to Modify &#40;Usage-Based Optimization Wizard&#41;</span></span>](select-partitions-to-modify-usage-based-optimization-wizard.md)  
  
-   [<span data-ttu-id="27c5d-125">使用法に基づく最適化ウィザードを &#40;クエリ条件を指定し&#41;</span><span class="sxs-lookup"><span data-stu-id="27c5d-125">Specify Query Criteria &#40;Usage-Based Optimization Wizard&#41;</span></span>](specify-query-criteria-usage-based-optimization-wizard.md)  
  
-   [<span data-ttu-id="27c5d-126">使用法に基づく最適化ウィザード &#40;最適化されるクエリを確認し&#41;</span><span class="sxs-lookup"><span data-stu-id="27c5d-126">Review the Queries that will be Optimized &#40;Usage-Based Optimization Wizard&#41;</span></span>](review-the-queries-that-will-be-optimized-usage-based-optimization-wizard.md)  
  
-   [<span data-ttu-id="27c5d-127">使用法に基づく最適化ウィザードを &#40;集計使用率を確認する&#41;</span><span class="sxs-lookup"><span data-stu-id="27c5d-127">Review Aggregation Usage &#40;Usage-Based Optimiation Wizard&#41;</span></span>](review-aggregation-usage-usage-based-optimiation-wizard.md)  
  
-   [<span data-ttu-id="27c5d-128">&#40;使用法に基づく最適化ウィザードを使用してオブジェクト数を指定&#41;</span><span class="sxs-lookup"><span data-stu-id="27c5d-128">Specify Object Counts &#40;Usage-Based Optimization Wizard&#41;</span></span>](specify-object-counts-usage-based-optimization-wizard.md)  
  
-   [<span data-ttu-id="27c5d-129">集計オプションの設定 &#40;使用法に基づく最適化ウィザード&#41;</span><span class="sxs-lookup"><span data-stu-id="27c5d-129">Set Aggregation Options &#40;Usage-Based Optimization Wizard&#41;</span></span>](set-aggregation-options-usage-based-optimization-wizard.md)  
  
-   [<span data-ttu-id="27c5d-130">ウィザードの完了 &#40;使用法に基づく最適化ウィザード&#41;</span><span class="sxs-lookup"><span data-stu-id="27c5d-130">Completing the Wizard &#40;Usage-Based Optimization Wizard&#41;</span></span>](completing-the-wizard-usage-based-optimization-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="27c5d-131">参照</span><span class="sxs-lookup"><span data-stu-id="27c5d-131">See Also</span></span>  
 <span data-ttu-id="27c5d-132">[集計と集計のデザイン](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md) </span><span class="sxs-lookup"><span data-stu-id="27c5d-132">[Aggregations and Aggregation Designs](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md) </span></span>  
 <span data-ttu-id="27c5d-133">[多次元モデルのキューブ](multidimensional-models/cubes-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="27c5d-133">[Cubes in Multidimensional Models](multidimensional-models/cubes-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="27c5d-134">[集計のデザインウィザードの F1 ヘルプ](aggregation-design-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="27c5d-134">[Aggregation Design Wizard F1 Help](aggregation-design-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="27c5d-135">Analysis Services のウィザード &#40;多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="27c5d-135">Analysis Services Wizards &#40;Multidimensional Data&#41;</span></span>](analysis-services-wizards-multidimensional-data.md)  
  
  
