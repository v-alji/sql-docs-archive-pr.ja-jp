---
title: ソースキューブのスライス (データマイニングウィザード)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.slicesourcecube.f1
ms.assetid: 16485608-d3b9-49ee-8baa-948038cdd7ec
author: minewiskan
ms.author: owend
ms.openlocfilehash: 762248d4c2a268ac36b0dfa3ffeba20123017017
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736859"
---
# <a name="slice-source-cube-data-mining-wizard"></a><span data-ttu-id="9c5c5-102">Slice Source Cube (Data Mining Wizard)</span><span class="sxs-lookup"><span data-stu-id="9c5c5-102">Slice Source Cube (Data Mining Wizard)</span></span>
  <span data-ttu-id="9c5c5-103">**[ソース キューブのスライス]** ダイアログ ボックスを使用すると、モデルのトレーニング用に使用するデータを制限できます。</span><span class="sxs-lookup"><span data-stu-id="9c5c5-103">You can use the **Slice Source Cube** dialog box to restrict the data used to train the model.</span></span> <span data-ttu-id="9c5c5-104">通常、キューブには、すべての店舗、すべての地域、すべての製品など、多くの異なるディメンションと属性に関連するデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="9c5c5-104">Typically a cube contains data related to many different dimensions and attributes, such as all stores, all regions, and all products.</span></span> <span data-ttu-id="9c5c5-105">属性の無限の組み合わせに対してモデルのトレーニングを実行することは実用的ではないため、このダイアログ ボックスを使用して、モデルのトレーニングで利用する特定のセットを選択します。</span><span class="sxs-lookup"><span data-stu-id="9c5c5-105">It is not practical to train a model on unlimited combinations of attributes, so you use this dialog box to choose a specific set to use in training a model.</span></span>  
  
 <span data-ttu-id="9c5c5-106">たとえば、AdventureWorks キューブで、特定の製品ライン、地域、または年でスライスを実行し、データの一部を取得することができます。</span><span class="sxs-lookup"><span data-stu-id="9c5c5-106">For example, in the AdventureWorks cube, you might slice by a particular product line, region, or year, to get a portion of the data.</span></span>  
  
 <span data-ttu-id="9c5c5-107">スライスおよびキューブについて詳しく理解していない場合は、次の記事を確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9c5c5-107">If you are unfamiliar with slices and cubes, we recommend that you review these articles:</span></span>  
  
-   [<span data-ttu-id="9c5c5-108">パーティションスライスプロパティ &#40;Analysis Services に設定し&#41;</span><span class="sxs-lookup"><span data-stu-id="9c5c5-108">Set the Partition Slice Property &#40;Analysis Services&#41;</span></span>](multidimensional-models/set-the-partition-slice-property-analysis-services.md)  
  
-   [<span data-ttu-id="9c5c5-109">ローカル パーティションの作成と管理 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="9c5c5-109">Create and Manage a Local Partition &#40;Analysis Services&#41;</span></span>](multidimensional-models/create-and-manage-a-local-partition-analysis-services.md)  
  
> [!NOTE]  
>  <span data-ttu-id="9c5c5-110">動的 MDX 関数 ([Generate (MDX)](/sql/mdx/generate-mdx) または [Except (MDX)](/sql/mdx/except-mdx-function) など) はパーティションの Slice プロパティでサポートされていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9c5c5-110">Note that dynamic MDX functions (such as [Generate &#40;MDX&#41;](/sql/mdx/generate-mdx) or [Except &#40;MDX&#41;](/sql/mdx/except-mdx-function)) are not supported in the Slice property for partitions.</span></span> <span data-ttu-id="9c5c5-111">明示的な組またはメンバー参照を使用して、スライスを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c5c5-111">You must define the slice by using explicit tuples or member references.</span></span>  
>   
>  <span data-ttu-id="9c5c5-112">たとえば、範囲を定義するために[&#40;範囲&#41; &#40;MDX&#41;](/sql/mdx/range-mdx)を使用するのではなく、特定の年で各メンバーを列挙する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c5c5-112">For example, rather than using  [: &#40;Range&#41; &#40;MDX&#41;](/sql/mdx/range-mdx) to define a range, you would need to enumerate each member by the specific years.</span></span>  
>   
>  <span data-ttu-id="9c5c5-113">複雑なスライスを定義する必要がある場合は、XMLA Alter スクリプトを使用して、スライスで組を定義することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9c5c5-113">If you need to define a complex slice, we recommend that you define the tuples in the slice by using an XMLA Alter script.</span></span> <span data-ttu-id="9c5c5-114">続けて、ascmd コマンド ライン ツールまたは SSIS [Analysis Services Execute DDL Task](../integration-services/control-flow/analysis-services-execute-ddl-task.md) を使用してスクリプトを実行し、指定したメンバーのセットをパーティション処理の直前に作成します。</span><span class="sxs-lookup"><span data-stu-id="9c5c5-114">Then, you can use either the ascmd command-line tool or the SSIS [Analysis Services Execute DDL Task](../integration-services/control-flow/analysis-services-execute-ddl-task.md) to run the script and create the specified set of members immediately before you process the partition.</span></span>  
  
 <span data-ttu-id="9c5c5-115">**詳細情報:** [データ マイニング ウィザード &#40;Analysis Services - データ マイニング&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md)、[リレーショナル マイニング構造の作成](data-mining/create-a-relational-mining-structure.md)</span><span class="sxs-lookup"><span data-stu-id="9c5c5-115">**For More Information:** [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Create a Relational Mining Structure](data-mining/create-a-relational-mining-structure.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="9c5c5-116">Options</span><span class="sxs-lookup"><span data-stu-id="9c5c5-116">Options</span></span>  
 <span data-ttu-id="9c5c5-117">**ディメンション**</span><span class="sxs-lookup"><span data-stu-id="9c5c5-117">**Dimension**</span></span>  
 <span data-ttu-id="9c5c5-118">スライスするディメンションを選択します。</span><span class="sxs-lookup"><span data-stu-id="9c5c5-118">Select the dimension that you want to slice.</span></span>  
  
 <span data-ttu-id="9c5c5-119">**Hierarchy**</span><span class="sxs-lookup"><span data-stu-id="9c5c5-119">**Hierarchy**</span></span>  
 <span data-ttu-id="9c5c5-120">スライスする階層を選択します。</span><span class="sxs-lookup"><span data-stu-id="9c5c5-120">Select the hierarchy that you want to slice.</span></span> <span data-ttu-id="9c5c5-121">任意の階層レベルを選択できますが、モデルで使用される属性は、選択したレベルに存在する属性のみです。</span><span class="sxs-lookup"><span data-stu-id="9c5c5-121">You can choose any level of a hierarchy, but the attributes used in the model will be only at the level that you choose.</span></span>  
  
 <span data-ttu-id="9c5c5-122">たとえば、地理階層を選択し、レベルとして国を選択する場合は、属性として市を使用するモデルを構築することはできません。</span><span class="sxs-lookup"><span data-stu-id="9c5c5-122">For example, if you choose the Geography hierarchy, and select Country as the level, you cannot build a model that uses City as the attributes.</span></span> <span data-ttu-id="9c5c5-123">逆に、スライスする階層レベルとして市を選択すると、国に基づくマイニング モデルを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="9c5c5-123">Conversely, if you choose City as the level of the hierarchy on which to slice, you cannot create a mining model based on Country.</span></span>  
  
 <span data-ttu-id="9c5c5-124">**[オペレーター]**</span><span class="sxs-lookup"><span data-stu-id="9c5c5-124">**Operator**</span></span>  
 <span data-ttu-id="9c5c5-125">スライス式の作成に使用する演算子を選択します。</span><span class="sxs-lookup"><span data-stu-id="9c5c5-125">Select the operator to use in building a slice expression.</span></span>  
  
 <span data-ttu-id="9c5c5-126">たとえば、階層として [Geography] を選択した場合は、演算子 = を選択し、フィルターとして「ヨーロッパ」と入力すると、ヨーロッパのキューブデータだけを取得できます。</span><span class="sxs-lookup"><span data-stu-id="9c5c5-126">For example, if you chose Geography as the hierarchy, you could select the operator = and then type "Europe" as the filter, to get cube data for Europe only.</span></span>  
  
 <span data-ttu-id="9c5c5-127">**[フィルター式]**</span><span class="sxs-lookup"><span data-stu-id="9c5c5-127">**Filter Expression**</span></span>  
 <span data-ttu-id="9c5c5-128">選択したディメンションでキューブをフィルター処理するときに条件として使用する式を入力します。</span><span class="sxs-lookup"><span data-stu-id="9c5c5-128">Type an expression to use as a criterion when filtering the cube on the selected dimension.</span></span>  
  
 <span data-ttu-id="9c5c5-129">**パラメーター**</span><span class="sxs-lookup"><span data-stu-id="9c5c5-129">**Parameters**</span></span>  
 <span data-ttu-id="9c5c5-130">このオプションは、データ マイニング モデルでは使用されません。</span><span class="sxs-lookup"><span data-stu-id="9c5c5-130">This option is not used for data mining models.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c5c5-131">参照</span><span class="sxs-lookup"><span data-stu-id="9c5c5-131">See Also</span></span>  
 <span data-ttu-id="9c5c5-132">[[ウィザードの完了] &#40;データマイニングウィザード&#41;](completing-the-wizard-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="9c5c5-132">[Completing the Wizard &#40;Data Mining Wizard&#41;](completing-the-wizard-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="9c5c5-133">[データマイニングウィザードの F1 ヘルプ &#40;Analysis Services データマイニング&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="9c5c5-133">[Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="9c5c5-134">データマイニングウィザードの &#40;マイニングモデル列の使用法の指定&#41;</span><span class="sxs-lookup"><span data-stu-id="9c5c5-134">Specify Mining Model Column Usage &#40;Data Mining Wizard&#41;</span></span>](specify-mining-model-column-usage-data-mining-wizard.md)  
  
  
