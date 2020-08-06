---
title: 準加法の動作の定義 (ビジネスインテリジェンスウィザード) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.semiadditivememberdetection.f1
ms.assetid: e57080ba-ce96-40f8-bca7-6701d1725b3c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5a3c46de038a7e45dcb39805e324260676a03228
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712633"
---
# <a name="define-semiadditive-behavior-business-intelligence-wizard"></a><span data-ttu-id="91758-102">[準加法の動作の定義] (ビジネス インテリジェンス ウィザード)</span><span class="sxs-lookup"><span data-stu-id="91758-102">Define Semiadditive Behavior (Business Intelligence Wizard)</span></span>
  <span data-ttu-id="91758-103">**[準加法の動作の定義]** ページを使用すると、メジャーに対する準加法の動作を有効または無効にできます。</span><span class="sxs-lookup"><span data-stu-id="91758-103">Use the **Define Semiadditive Behavior** page to enable or disable semi-additive behavior on measures.</span></span> <span data-ttu-id="91758-104">準加法の動作によって、キューブに含まれるメジャーが時間ディメンションで集計される方法が決まります。</span><span class="sxs-lookup"><span data-stu-id="91758-104">Semi-additive behavior determines how measures that are contained by a cube are aggregated over a time dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="91758-105">Standard Edition で使用できる LastChild を除き、準加法の動作を使用できるのは、Business Intelligence または Enterprise Edition のみです。</span><span class="sxs-lookup"><span data-stu-id="91758-105">With the exception of LastChild which is available in the standard edition, semi-additive behaviors are only available in the business intelligence or enterprise editions.</span></span> <span data-ttu-id="91758-106">さらに、準加法の動作はメジャーのみを対象にして定義するものであり、ディメンションを対象にしていないため、ディメンション デザイナーからビジネス インテリジェンス ウィザードを起動した場合や、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]のソリューション エクスプローラー内にあるディメンションを右クリックした場合は、ウィザード内でこのページは表示されません。</span><span class="sxs-lookup"><span data-stu-id="91758-106">Furthermore, because semiadditive behavior is defined only on measures and not dimensions, you will not find this page in the Business Intelligence Wizard if it was started from Dimension Designer or by right-clicking a dimension in Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="91758-107">Options</span><span class="sxs-lookup"><span data-stu-id="91758-107">Options</span></span>  
 <span data-ttu-id="91758-108">**[準加法の動作を無効にする]**</span><span class="sxs-lookup"><span data-stu-id="91758-108">**Turn off semiadditive behavior**</span></span>  
 <span data-ttu-id="91758-109">キューブに含まれるすべてのメジャーで準加法の動作を無効にします。</span><span class="sxs-lookup"><span data-stu-id="91758-109">Disables semi-additive behavior in all measures contained by the cube.</span></span>  
  
 <span data-ttu-id="91758-110">**\<dimension name>準加法メンバーを含む勘定科目ディメンションが検出されました。サーバーは、勘定科目の種類ごとに指定された準加法の動作に従って、このディメンションのメンバーを集計します。**</span><span class="sxs-lookup"><span data-stu-id="91758-110">**The wizard has detected the \<dimension name> account dimension, which contains semiadditive members. The server will aggregate members of this dimension according to the semiadditive behavior specified for each account type.**</span></span>  
 <span data-ttu-id="91758-111">準加法メンバーを含む勘定科目ディメンションの準加法の動作を有効にします。</span><span class="sxs-lookup"><span data-stu-id="91758-111">Enables semi-additive behavior for account dimensions that contain semi-additive members.</span></span> <span data-ttu-id="91758-112">このオプションを選択して、`ByAccount` への勘定科目ディメンションを参照する、メジャー グループのすべてのメジャーの集計関数を設定します。</span><span class="sxs-lookup"><span data-stu-id="91758-112">Selecting this option sets the aggregation function of all measures in measure groups that reference the account dimension to `ByAccount`.</span></span>  
  
 <span data-ttu-id="91758-113">勘定科目ディメンションの詳細については、「 [親子型ディメンションの財務アカウントの作成](multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91758-113">For more information about account dimensions, see [Create a Finance Account of parent-child type Dimension](multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md).</span></span>  
  
 <span data-ttu-id="91758-114">**[個別のメジャーに準加法の動作を定義する]**</span><span class="sxs-lookup"><span data-stu-id="91758-114">**Define semiadditive behavior for individual members**</span></span>  
 <span data-ttu-id="91758-115">準加法の動作を有効にして、特定のメジャーに対して準加法集計関数を指定します。</span><span class="sxs-lookup"><span data-stu-id="91758-115">Enables semi-additive behavior and specifies the semi-additive aggregation function for specific measures.</span></span> <span data-ttu-id="91758-116">集計関数は、メジャーを含むメジャー グループによって参照されるすべてのディメンションに対して適用されます。</span><span class="sxs-lookup"><span data-stu-id="91758-116">The aggregation function applies to all dimensions that are referenced by the measure group that contains the measure.</span></span>  
  
 <span data-ttu-id="91758-117">**直径**</span><span class="sxs-lookup"><span data-stu-id="91758-117">**Measures**</span></span>  
 <span data-ttu-id="91758-118">キューブに含まれるメジャーの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="91758-118">Displays the name of a measure contained by the cube.</span></span>  
  
 <span data-ttu-id="91758-119">**[集計関数]**</span><span class="sxs-lookup"><span data-stu-id="91758-119">**Semiadditive Function**</span></span>  
 <span data-ttu-id="91758-120">選択されたメジャーの集計関数を選択します。</span><span class="sxs-lookup"><span data-stu-id="91758-120">Select the aggregation function for the selected measure.</span></span> <span data-ttu-id="91758-121">次の表は、使用できる集計関数の一覧を示しています。</span><span class="sxs-lookup"><span data-stu-id="91758-121">The following table lists the aggregation functions that are available.</span></span>  
  
|<span data-ttu-id="91758-122">値</span><span class="sxs-lookup"><span data-stu-id="91758-122">Value</span></span>|<span data-ttu-id="91758-123">説明</span><span class="sxs-lookup"><span data-stu-id="91758-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="91758-124">**AverageOfChildren**</span><span class="sxs-lookup"><span data-stu-id="91758-124">**AverageOfChildren**</span></span>|<span data-ttu-id="91758-125">メジャーの子の平均を返すことによって集計されます。</span><span class="sxs-lookup"><span data-stu-id="91758-125">Aggregated by returning the average of the measure's children.</span></span>|  
|`ByAccount`|<span data-ttu-id="91758-126">勘定科目ディメンションで指定された属性の勘定科目の種類に関連付けられた集計関数によって集計されます。</span><span class="sxs-lookup"><span data-stu-id="91758-126">Aggregated by the aggregation function associated with the specified account type of an attribute in an account dimension.</span></span>|  
|`Count`|<span data-ttu-id="91758-127">`Count` 関数を使用して集計されます。</span><span class="sxs-lookup"><span data-stu-id="91758-127">Aggregated using the `Count` function.</span></span>|  
|`DistinctCount`|<span data-ttu-id="91758-128">`DistinctCount` 関数を使用して集計されます。</span><span class="sxs-lookup"><span data-stu-id="91758-128">Aggregated using the `DistinctCount` function.</span></span>|  
|<span data-ttu-id="91758-129">**FirstChild**</span><span class="sxs-lookup"><span data-stu-id="91758-129">**FirstChild**</span></span>|<span data-ttu-id="91758-130">メジャーの最初の子メンバーを返すことによって時間ディメンションで集計されます。</span><span class="sxs-lookup"><span data-stu-id="91758-130">Aggregated by returning the measure's first child member over a time dimension.</span></span>|  
|<span data-ttu-id="91758-131">**FirstNonEmpty**</span><span class="sxs-lookup"><span data-stu-id="91758-131">**FirstNonEmpty**</span></span>|<span data-ttu-id="91758-132">メジャーの最初の空でないメンバーを返すことによって時間ディメンションで集計されます。</span><span class="sxs-lookup"><span data-stu-id="91758-132">Aggregated by returning the measure's first nonempty member over a time dimension.</span></span>|  
|<span data-ttu-id="91758-133">**LastChild**</span><span class="sxs-lookup"><span data-stu-id="91758-133">**LastChild**</span></span>|<span data-ttu-id="91758-134">メジャーの最後の子メンバーを返すことによって時間ディメンションで集計されます。</span><span class="sxs-lookup"><span data-stu-id="91758-134">Aggregated by returning the measure's last child member over a time dimension.</span></span>|  
|<span data-ttu-id="91758-135">**LastNonEmpty**</span><span class="sxs-lookup"><span data-stu-id="91758-135">**LastNonEmpty**</span></span>|<span data-ttu-id="91758-136">メジャーの最後の空でないメンバーを返すことによって時間ディメンションで集計されます。</span><span class="sxs-lookup"><span data-stu-id="91758-136">Aggregated by returning the measure's last nonempty member over a time dimension.</span></span>|  
|`Max`|<span data-ttu-id="91758-137">`Max` 関数を使用して集計されます。</span><span class="sxs-lookup"><span data-stu-id="91758-137">Aggregated using the `Max` function.</span></span>|  
|`Min`|<span data-ttu-id="91758-138">`Min` 関数を使用して集計されます。</span><span class="sxs-lookup"><span data-stu-id="91758-138">Aggregated using the `Min` function.</span></span>|  
|<span data-ttu-id="91758-139">**なし**</span><span class="sxs-lookup"><span data-stu-id="91758-139">**None**</span></span>|<span data-ttu-id="91758-140">集計は実行されません。</span><span class="sxs-lookup"><span data-stu-id="91758-140">No aggregation performed.</span></span>|  
|`Sum`|<span data-ttu-id="91758-141">`Sum` 関数を使用して集計されます。</span><span class="sxs-lookup"><span data-stu-id="91758-141">Aggregated using the `Sum` function.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="91758-142">このオプションの選択は、 **[個別のメジャーに準加法の動作を定義する]** が選択されている場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="91758-142">Selections made for this option apply only if **Define semiadditive behavior for individual members** is selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91758-143">参照</span><span class="sxs-lookup"><span data-stu-id="91758-143">See Also</span></span>  
 <span data-ttu-id="91758-144">[ビジネスインテリジェンスウィザードの F1 ヘルプ](business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="91758-144">[Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="91758-145">[キューブデザイナー &#40;Analysis Services-多次元データ&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="91758-145">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="91758-146">ディメンションデザイナー &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="91758-146">Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
