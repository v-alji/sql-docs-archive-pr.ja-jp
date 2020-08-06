---
title: 集計関数を使用する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- aggregate functions [Analysis Services]
ms.assetid: c42166ef-b75c-45f4-859c-09a3e9617664
author: minewiskan
ms.author: owend
ms.openlocfilehash: 83cdc571019cffd8ae99e00f119541736c6f503b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642365"
---
# <a name="use-aggregate-functions"></a><span data-ttu-id="6414f-102">集計関数の使用</span><span class="sxs-lookup"><span data-stu-id="6414f-102">Use Aggregate Functions</span></span>
  <span data-ttu-id="6414f-103">メジャーをスライスするためにディメンションを使用する場合、メジャーはそのディメンションに含まれる階層に沿って集約されます。</span><span class="sxs-lookup"><span data-stu-id="6414f-103">When a dimension is used to slice a measure, the measure is summarized along the hierarchies contained in that dimension.</span></span> <span data-ttu-id="6414f-104">この集約動作は、メジャーに指定される集計関数に依存します。</span><span class="sxs-lookup"><span data-stu-id="6414f-104">The summation behavior depends on the aggregate function specified for the measure.</span></span> <span data-ttu-id="6414f-105">数値データが含まれているほとんどのメジャーでは、集計関数は `Sum` になります。</span><span class="sxs-lookup"><span data-stu-id="6414f-105">For most measures containing numeric data, the aggregate function is `Sum`.</span></span> <span data-ttu-id="6414f-106">メジャーの値は、どの階層のレベルがアクティブかに応じて異なる量の合計になります。</span><span class="sxs-lookup"><span data-stu-id="6414f-106">The value of the measure will sum to different amounts depending on which level of the hierarchy is active.</span></span>  
  
 <span data-ttu-id="6414f-107">Analysis Services において作成するすべてのメジャーは、対応する集計関数によりその動作が決まります。</span><span class="sxs-lookup"><span data-stu-id="6414f-107">In Analysis Services, every measure that you create is backed by an aggregation function that determines the measure's operation.</span></span> <span data-ttu-id="6414f-108">定義済みの集計 `Sum` の種類には、、、 `Min` `Max` 、 `Count` 、 **Distinct Count**など、いくつかの特殊な関数が含まれます。</span><span class="sxs-lookup"><span data-stu-id="6414f-108">Predefined aggregation types include `Sum`, `Min`, `Max`, `Count`, **Distinct Count**, and several other more specialized functions.</span></span> <span data-ttu-id="6414f-109">または、複雑な数式やカスタムの数式に基づいて集計を必要とする場合は、構築済みの集計関数を代わりに使用して、MDX の計算を作成できます。</span><span class="sxs-lookup"><span data-stu-id="6414f-109">Alternatively, if you require aggregations based on complex or custom formulas, you can build an MDX calculation in lieu of using a prebuilt aggregation function.</span></span> <span data-ttu-id="6414f-110">たとえば、割合の値のためのメジャーを定義する場合、計算されるメジャーを使用して MDX でそれを実行します。</span><span class="sxs-lookup"><span data-stu-id="6414f-110">For example, if you want to define a measure for a percentage value, you would do that in MDX, using a calculated measure.</span></span> <span data-ttu-id="6414f-111">「[CREATE MEMBER ステートメント &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6414f-111">See [CREATE MEMBER Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member).</span></span>  
  
 <span data-ttu-id="6414f-112">キューブ ウィザードを使用して作成されるメジャーは、メジャーの定義の一部として、集計の種類に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="6414f-112">Measures that are created via the Cube Wizard are assigned an aggregation type as part of the measure definition.</span></span> <span data-ttu-id="6414f-113">ソース列に数値データが含まれることを前提として、集計の種類は常に `Sum` になります。</span><span class="sxs-lookup"><span data-stu-id="6414f-113">The aggregation type is always `Sum`, assuming the source column contains numeric data.</span></span> <span data-ttu-id="6414f-114">`Sum` は、ソース列のデータ型に関係なく割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="6414f-114">`Sum` is assigned regardless of the source column's data type.</span></span> <span data-ttu-id="6414f-115">たとえば、キューブ ウィザードを使用してメジャーを作成し、ファクト テーブルからすべての列を抜粋した場合、ソースが日付と時間の列であっても、結果として得られるメジャーのすべてに `Sum` の集計があることが分かります。</span><span class="sxs-lookup"><span data-stu-id="6414f-115">For example, if you used the Cube Wizard to create measures, and you pulled in all columns from a fact table, you will notice that all of the resulting measures have an aggregation of `Sum`, even if the source is a date time column.</span></span> <span data-ttu-id="6414f-116">集計関数が適切であることを確認するウィザードを介して作成されたメジャーの場合は、事前に割り当てられている集計メソッドを常に確認します。</span><span class="sxs-lookup"><span data-stu-id="6414f-116">Always review the pre-assigned aggregation methods for measures created via the wizard to make sure the aggregation function is suitable.</span></span>  
  
 <span data-ttu-id="6414f-117">[!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)]または MDX のいずれかを介したキューブの定義で、集計方法を割り当てたり、変更したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="6414f-117">You can assign or change the aggregation method in the either the cube definition, via [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)], or via MDX.</span></span> <span data-ttu-id="6414f-118">詳細については、「[多次元モデル内のメジャーおよびメジャー グループの作成](create-measures-and-measure-groups-in-multidimensional-models.md)」または「[Aggregate &#40;MDX&#41;](/sql/mdx/aggregate-mdx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6414f-118">See [Create Measures and Measure Groups in Multidimensional Models](create-measures-and-measure-groups-in-multidimensional-models.md) or [Aggregate &#40;MDX&#41;](/sql/mdx/aggregate-mdx) for further instructions.</span></span>  
  
##  <a name="aggregate-functions"></a><a name="AggFunction"></a><span data-ttu-id="6414f-119">集計関数</span><span class="sxs-lookup"><span data-stu-id="6414f-119">Aggregate Functions</span></span>  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] <span data-ttu-id="6414f-120">には、メジャー グループに含まれるディメンションに従ってメジャーを集計するための関数があります。</span><span class="sxs-lookup"><span data-stu-id="6414f-120">provides functions to aggregate measures along the dimensions that are contained in measure groups.</span></span> <span data-ttu-id="6414f-121">集計関数の " *加法性* " によって、キューブのすべてのディメンションにわたってメジャーがどのように集計されるかが決まります。</span><span class="sxs-lookup"><span data-stu-id="6414f-121">The *additivity* of an aggregation function determines how the measure is aggregated across all the dimensions in the cube.</span></span> <span data-ttu-id="6414f-122">集計関数の加法性は、3 つのレベルに分類されます。</span><span class="sxs-lookup"><span data-stu-id="6414f-122">Aggregation functions fall into three levels of additivity:</span></span>  
  
 <span data-ttu-id="6414f-123">加法</span><span class="sxs-lookup"><span data-stu-id="6414f-123">Additive</span></span>  
 <span data-ttu-id="6414f-124">加法メジャーは完全加法メジャーとも呼ばれ、メジャーが含まれているメジャー グループ内のすべてのディメンションに従って制限なく集計できます。</span><span class="sxs-lookup"><span data-stu-id="6414f-124">An additive measure, also called a fully additive measure, can be aggregated along all the dimensions that are included in the measure group that contains the measure, without restriction.</span></span>  
  
 <span data-ttu-id="6414f-125">準加法</span><span class="sxs-lookup"><span data-stu-id="6414f-125">Semiadditive</span></span>  
 <span data-ttu-id="6414f-126">準加法メジャーは、メジャーが含まれているメジャー グループ内のすべてではなく一部のディメンションに従って集計できます。</span><span class="sxs-lookup"><span data-stu-id="6414f-126">A semiadditive measure can be aggregated along some, but not all, dimensions that are included in the measure group that contains the measure.</span></span> <span data-ttu-id="6414f-127">たとえば、在庫の数量を表すメジャーは、地理ディメンションに従って集計してすべての倉庫の合計在庫数量を生成できますが、このメジャーは在庫数量の定期的なスナップショットを表しているため、時間ディメンションに従って集計できません。</span><span class="sxs-lookup"><span data-stu-id="6414f-127">For example, a measure that represents the quantity available for inventory can be aggregated along a geography dimension to produce a total quantity available for all warehouses, but the measure cannot be aggregated along a time dimension because the measure represents a periodic snapshot of quantities available.</span></span> <span data-ttu-id="6414f-128">そのようなメジャーを時間ディメンションに従って集計すると、間違った結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="6414f-128">Aggregating such a measure along a time dimension would produce incorrect results.</span></span> <span data-ttu-id="6414f-129">詳細については、「 [準加法の動作の定義](define-semiadditive-behavior.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6414f-129">See [Define Semiadditive Behavior](define-semiadditive-behavior.md) for details.</span></span>  
  
 <span data-ttu-id="6414f-130">非加法</span><span class="sxs-lookup"><span data-stu-id="6414f-130">Nonadditive</span></span>  
 <span data-ttu-id="6414f-131">非加法メジャーは、メジャーが含まれているメジャー グループ内のどのディメンションに従っても集計できません。</span><span class="sxs-lookup"><span data-stu-id="6414f-131">A nonadditive measure cannot be aggregated along any dimension in the measure group that contains the measure.</span></span> <span data-ttu-id="6414f-132">代わりに、このメジャーは、メジャーを表すキューブのセルごとに計算する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6414f-132">Instead, the measure must be individually calculated for each cell in the cube that represents the measure.</span></span> <span data-ttu-id="6414f-133">たとえば、利益率などの比率を返す計算されるメジャーは、どのディメンションの子メンバーのパーセンテージ値からも集計できません。</span><span class="sxs-lookup"><span data-stu-id="6414f-133">For example, a calculated measure that returns a percentage, such as profit margin, cannot be aggregated from the percentage values of child members in any dimension.</span></span>  
  
 <span data-ttu-id="6414f-134">次の表は [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]の集計関数を示しています。関数の加法性と予想される出力が記載されています。</span><span class="sxs-lookup"><span data-stu-id="6414f-134">The following table lists the aggregation functions in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], and describes both the additivity and expected output of the function.</span></span>  
  
|<span data-ttu-id="6414f-135">集計関数</span><span class="sxs-lookup"><span data-stu-id="6414f-135">Aggregation function</span></span>|<span data-ttu-id="6414f-136">加法性</span><span class="sxs-lookup"><span data-stu-id="6414f-136">Additivity</span></span>|<span data-ttu-id="6414f-137">戻り値</span><span class="sxs-lookup"><span data-stu-id="6414f-137">Returned value</span></span>|  
|--------------------------|----------------|--------------------|  
|`Sum`|<span data-ttu-id="6414f-138">加法</span><span class="sxs-lookup"><span data-stu-id="6414f-138">Additive</span></span>|<span data-ttu-id="6414f-139">すべての子メンバーの値の合計を計算します。</span><span class="sxs-lookup"><span data-stu-id="6414f-139">Calculates the sum of values for all child members.</span></span> <span data-ttu-id="6414f-140">これは既定の集計関数です。</span><span class="sxs-lookup"><span data-stu-id="6414f-140">This is the default aggregation function.</span></span>|  
|`Count`|<span data-ttu-id="6414f-141">加法</span><span class="sxs-lookup"><span data-stu-id="6414f-141">Additive</span></span>|<span data-ttu-id="6414f-142">すべての子メンバーの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="6414f-142">Retrieves the count of all child members.</span></span>|  
|`Min`|<span data-ttu-id="6414f-143">準加法</span><span class="sxs-lookup"><span data-stu-id="6414f-143">Semiadditive</span></span>|<span data-ttu-id="6414f-144">すべての子メンバーの最低値を取得します。</span><span class="sxs-lookup"><span data-stu-id="6414f-144">Retrieves the lowest value for all child members.</span></span>|  
|`Max`|<span data-ttu-id="6414f-145">準加法</span><span class="sxs-lookup"><span data-stu-id="6414f-145">Semiadditive</span></span>|<span data-ttu-id="6414f-146">すべての子メンバーの最高値を取得します。</span><span class="sxs-lookup"><span data-stu-id="6414f-146">Retrieves the highest value for all child members.</span></span>|  
|`DistinctCount`|<span data-ttu-id="6414f-147">非加法</span><span class="sxs-lookup"><span data-stu-id="6414f-147">Nonadditive</span></span>|<span data-ttu-id="6414f-148">すべての一意の子メンバーの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="6414f-148">Retrieves the count of all unique child members.</span></span> <span data-ttu-id="6414f-149">詳細については、次のセクションの「 [個別のカウント メジャーの概要](use-aggregate-functions.md#bkmk_distinct) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6414f-149">For more details, see [About Distinct Count Measures](use-aggregate-functions.md#bkmk_distinct) in the next section.</span></span>|  
|`None`|<span data-ttu-id="6414f-150">非加法</span><span class="sxs-lookup"><span data-stu-id="6414f-150">Nonadditive</span></span>|<span data-ttu-id="6414f-151">集計は行われず、ディメンションのリーフ メンバーおよび非リーフ メンバーのすべての値が、メジャーが含まれているメジャー グループのファクト テーブルから直接入力されます。</span><span class="sxs-lookup"><span data-stu-id="6414f-151">No aggregation is performed, and all values for leaf and nonleaf members in a dimension are supplied directly from the fact table for the measure group that contains the measure.</span></span> <span data-ttu-id="6414f-152">ファクト テーブルからメンバーの値を読み取ることができない場合は、そのメンバーの値は Null に設定されます。</span><span class="sxs-lookup"><span data-stu-id="6414f-152">If no value can be read from the fact table for a member, the value for that member is set to null.</span></span>|  
|`ByAccount`|<span data-ttu-id="6414f-153">準加法</span><span class="sxs-lookup"><span data-stu-id="6414f-153">Semiadditive</span></span>|<span data-ttu-id="6414f-154">勘定科目ディメンションのメンバーの勘定科目の種類に割り当てられている集計関数に従って集計します。</span><span class="sxs-lookup"><span data-stu-id="6414f-154">Calculates the aggregation according to the aggregation function assigned to the account type for a member in an account dimension.</span></span> <span data-ttu-id="6414f-155">勘定科目ディメンションがメジャー グループに存在しない場合は、`None` 集計関数として扱われます。</span><span class="sxs-lookup"><span data-stu-id="6414f-155">If no account type dimension exists in the measure group, treated as the `None` aggregation function.</span></span><br /><br /> <span data-ttu-id="6414f-156">勘定科目ディメンションの詳細については、「 [親子型ディメンションの財務アカウントの作成](database-dimensions-finance-account-of-parent-child-type.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6414f-156">For more information about account dimensions, see [Create a Finance Account of parent-child type Dimension](database-dimensions-finance-account-of-parent-child-type.md).</span></span>|  
|`AverageOfChildren`|<span data-ttu-id="6414f-157">準加法</span><span class="sxs-lookup"><span data-stu-id="6414f-157">Semiadditive</span></span>|<span data-ttu-id="6414f-158">空ではないすべての子メンバーの値の平均を計算します。</span><span class="sxs-lookup"><span data-stu-id="6414f-158">Calculates the average of values for all non-empty child members.</span></span>|  
|`FirstChild`|<span data-ttu-id="6414f-159">準加法</span><span class="sxs-lookup"><span data-stu-id="6414f-159">Semiadditive</span></span>|<span data-ttu-id="6414f-160">最初の子メンバーの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="6414f-160">Retrieves the value of the first child member.</span></span>|  
|`LastChild`|<span data-ttu-id="6414f-161">準加法</span><span class="sxs-lookup"><span data-stu-id="6414f-161">Semiadditive</span></span>|<span data-ttu-id="6414f-162">最後の子メンバーの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="6414f-162">Retrieves the value of the last child member.</span></span>|  
|`FirstNonEmpty`|<span data-ttu-id="6414f-163">準加法</span><span class="sxs-lookup"><span data-stu-id="6414f-163">Semiadditive</span></span>|<span data-ttu-id="6414f-164">空ではない最初の子メンバーの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="6414f-164">Retrieves the value of the first non-empty child member.</span></span>|  
|`LastNonEmpty`|<span data-ttu-id="6414f-165">準加法</span><span class="sxs-lookup"><span data-stu-id="6414f-165">Semiadditive</span></span>|<span data-ttu-id="6414f-166">空ではない最後の子メンバーの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="6414f-166">Retrieves the value of the last non-empty child member.</span></span>|  
  
##  <a name="about-distinct-count-measures"></a><a name="bkmk_distinct"></a> <span data-ttu-id="6414f-167">個別のカウント メジャーの概要</span><span class="sxs-lookup"><span data-stu-id="6414f-167">About Distinct Count Measures</span></span>  
 <span data-ttu-id="6414f-168">**Aggregate Function** プロパティの値が **Distinct Count** であるメジャーは、"個別のカウント メジャー" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="6414f-168">A measure with an **Aggregate Function** property value of **Distinct Count** is called a distinct count measure.</span></span> <span data-ttu-id="6414f-169">個別のカウント メジャーを使用すると、ファクト テーブルにおけるディメンションの最下位レベル メンバーの出現数をカウントできます。</span><span class="sxs-lookup"><span data-stu-id="6414f-169">A distinct count measure can be used to count occurrences of a dimension's lowest-level members in the fact table.</span></span> <span data-ttu-id="6414f-170">カウントは重複しないため、メンバーが複数回発生した場合も 1 つとしてカウントされます。</span><span class="sxs-lookup"><span data-stu-id="6414f-170">Because the count is distinct, if a member occurs multiple times, it is counted only once.</span></span> <span data-ttu-id="6414f-171">個別のカウント メジャーは、常に専用のメジャー グループに配置されています。</span><span class="sxs-lookup"><span data-stu-id="6414f-171">A distinct count measure is always placed in a dedicated measure group.</span></span> <span data-ttu-id="6414f-172">独自のメジャー グループに個別のカウント メジャーを配置することは、パフォーマンスの最適化の手法としてデザイナーに構築されたベスト プラクティスです。</span><span class="sxs-lookup"><span data-stu-id="6414f-172">Putting a distinct count measure into its own measure group is a best practice that has been built into the designer as a performance optimization technique.</span></span>  
  
 <span data-ttu-id="6414f-173">個別のカウント メジャーを使用するのは、あるディメンションの各メンバーについて、別のディメンションの重複しない最下位レベルのメンバーが、ファクト テーブル内で行をいくつ共有しているかを調べる場合です。</span><span class="sxs-lookup"><span data-stu-id="6414f-173">Distinct count measures are commonly used to determine for each member of a dimension how many distinct, lowest-level members of another dimension share rows in the fact table.</span></span> <span data-ttu-id="6414f-174">たとえば、Sales キューブの場合、顧客および顧客グループごとに、何種類の製品が購入されたかを調べます。</span><span class="sxs-lookup"><span data-stu-id="6414f-174">For example, in a Sales cube, for each customer and customer group, how many distinct products were purchased?</span></span> <span data-ttu-id="6414f-175">つまり、Customers ディメンションの各メンバーに対して、Products ディメンションの重複しない最下位レベル メンバーがファクト テーブル内でいくつの行を共有しているかを調べます。または、Internet Site Visits キューブの場合、サイト閲覧者や閲覧者グループごとに、インターネット サイト上で閲覧された重複しないページ数を調べる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="6414f-175">(That is, for each member of the Customers dimension, how many distinct, lowest-level members of the Products dimension share rows in the fact table?) Or, for example, in an Internet Site Visits cube, for each site visitor and site visitor group, how many distinct pages on the Internet site were visited?</span></span> <span data-ttu-id="6414f-176">つまり、Site Visitors ディメンションのメンバーごとに、Page ディメンションの重複しない最下位レベルのメンバーがファクト テーブル内の行をいくつ共有しているかを調べます。これらの各サンプルでは、2 番目のディメンションの最下位レベル メンバーが個別のカウント メジャーによってカウントされます。</span><span class="sxs-lookup"><span data-stu-id="6414f-176">(That is, for each member of the Site Visitors dimension, how many distinct, lowest-level members of the Pages dimension share rows in the fact table?) In each of these examples, the second dimension's lowest-level members are counted by a distinct count measure.</span></span>  
  
 <span data-ttu-id="6414f-177">このような分析では、ディメンションを 2 つに制限する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="6414f-177">This kind of analysis need not be limited to two dimensions.</span></span> <span data-ttu-id="6414f-178">実際、カウント対象となるメンバーを含んでいるディメンションなど、キューブ内のディメンションを自由に組み合わせることによって個別のカウント メジャーを分割およびスライスできます。</span><span class="sxs-lookup"><span data-stu-id="6414f-178">In fact, a distinct count measure can be separated and sliced by any combination of dimensions in the cube, including the dimension that contains the counted members.</span></span>  
  
 <span data-ttu-id="6414f-179">メンバーをカウントする個別のカウント メジャーは、ファクト テーブル内の外部キー列に基づきます</span><span class="sxs-lookup"><span data-stu-id="6414f-179">A distinct count measure that counts members is based on a foreign key column in the fact table.</span></span> <span data-ttu-id="6414f-180">(つまり、メジャーの **Source Column** プロパティでこの列を識別します)。この列は、個別のカウント メジャーによってカウントされたメンバーを識別するディメンション テーブル列と結合します。</span><span class="sxs-lookup"><span data-stu-id="6414f-180">(That is, the measure's **Source Column** property identifies this column.) This column joins the dimension table column that identifies the members counted by the distinct count measure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6414f-181">参照</span><span class="sxs-lookup"><span data-stu-id="6414f-181">See Also</span></span>  
 <span data-ttu-id="6414f-182">[メジャーとメジャーグループ](measures-and-measure-groups.md) </span><span class="sxs-lookup"><span data-stu-id="6414f-182">[Measures and Measure Groups](measures-and-measure-groups.md) </span></span>  
 <span data-ttu-id="6414f-183">[Mdx 関数リファレンス &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx) </span><span class="sxs-lookup"><span data-stu-id="6414f-183">[MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx) </span></span>  
 [<span data-ttu-id="6414f-184">準加法の動作の定義</span><span class="sxs-lookup"><span data-stu-id="6414f-184">Define Semiadditive Behavior</span></span>](define-semiadditive-behavior.md)  
  
  