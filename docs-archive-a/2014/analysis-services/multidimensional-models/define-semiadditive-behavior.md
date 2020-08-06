---
title: 準加法の動作を定義する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- semiadditive
- Business Intelligence enhancements [Analysis Services], semiadditive behavior
- measures [Analysis Services], semiadditive
ms.assetid: b25726bc-728b-4601-ad87-9015c39dc615
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9c2028c350046fdcc9f98bcd0f0612d6a91ccabb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641345"
---
# <a name="define-semiadditive-behavior"></a><span data-ttu-id="71a19-102">準加法の動作の定義</span><span class="sxs-lookup"><span data-stu-id="71a19-102">Define Semiadditive Behavior</span></span>
  <span data-ttu-id="71a19-103">すべてのディメンションで一様に集計しない準加法メジャーは、多くのビジネス シナリオでよく見られます。</span><span class="sxs-lookup"><span data-stu-id="71a19-103">Semiadditive measures, which do not uniformly aggregate across all dimensions, are very common in many business scenarios.</span></span> <span data-ttu-id="71a19-104">この問題は、一定期間の残高のスナップショットに基づくすべてのキューブで明らかです。</span><span class="sxs-lookup"><span data-stu-id="71a19-104">Every cube that is based on snapshots of balances over time exhibits this problem.</span></span> <span data-ttu-id="71a19-105">これらのスナップショットは、証券、口座残高、予算、人事、保険契約と保険金請求、およびその他多くのビジネス ドメインを扱うアプリケーションで見られます。</span><span class="sxs-lookup"><span data-stu-id="71a19-105">You can find these snapshots in applications dealing with securities, account balances, budgeting, human resources, insurance policies and claims, and many other business domains.</span></span>  
  
 <span data-ttu-id="71a19-106">準加法の動作をキューブに追加すると、勘定科目の種類の属性の個々のメジャーまたはメンバーの集計方法を定義できます。</span><span class="sxs-lookup"><span data-stu-id="71a19-106">Add semiadditive behavior to a cube to define an aggregation method for individual measures or members of the account type attribute.</span></span> <span data-ttu-id="71a19-107">キューブに勘定科目ディメンションが含まれる場合は、勘定科目の種類に基づき、準加法の動作を自動的に設定できます。</span><span class="sxs-lookup"><span data-stu-id="71a19-107">If the cube contains an account dimension, you can automatically set semiadditive behavior based on the account type.</span></span>  
  
 <span data-ttu-id="71a19-108">準加法の動作を追加するには、キューブ デザイナーでキューブを開き、[キューブ] メニューの **[ビジネス インテリジェンスの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="71a19-108">To add semiadditive behavior, open a cube in Cube Designer and choose **Add Business Intelligence** from the Cube menu.</span></span> <span data-ttu-id="71a19-109">ビジネス インテリジェンス ウィザードで、 **[拡張機能の選択]** ページの **[準加法の動作の定義]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="71a19-109">In the Business Intelligence Wizard, select the **Define semiadditive behavior** option on the **Choose Enhancement** page.</span></span> <span data-ttu-id="71a19-110">その後、このウィザードに従って、準加法の動作のあるメジャーを識別します。</span><span class="sxs-lookup"><span data-stu-id="71a19-110">This wizard then guides you through the steps of identifying which measures have semiadditive behavior.</span></span>  
  
 <span data-ttu-id="71a19-111">Standard Edition で使用できる LastChild を除き、準加法の動作を使用できるのは、Business Intelligence または Enterprise Edition のみです。</span><span class="sxs-lookup"><span data-stu-id="71a19-111">With the exception of LastChild which is available in the standard edition, semi-additive behaviors are only available in the business intelligence or enterprise editions.</span></span>  
  
## <a name="define-semiadditive-behavior"></a><span data-ttu-id="71a19-112">準加法の動作の定義</span><span class="sxs-lookup"><span data-stu-id="71a19-112">Define Semiadditive Behavior</span></span>  
 <span data-ttu-id="71a19-113">ウィザードの **[準加法の動作の定義]** ページで、次のいずれかのオプションを選択して、準加法の定義方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="71a19-113">On the **Define Semiadditive Behavior** page of the wizard, you select how to define semiadditivity by selecting one of the following options:</span></span>  
  
 <span data-ttu-id="71a19-114">**[準加法の動作を無効にする]**</span><span class="sxs-lookup"><span data-stu-id="71a19-114">**Turn off semiadditive behavior**</span></span>  
 <span data-ttu-id="71a19-115">準加法の動作が定義済みのキューブから準加法の動作を削除します。</span><span class="sxs-lookup"><span data-stu-id="71a19-115">Removes semiadditive behavior from a cube in which semiadditive behavior was previously defined.</span></span> <span data-ttu-id="71a19-116">メジャーが次のいずれかの種類の集計関数に設定されている場合にこのオプションを選択すると、メジャーは `SUM` にリセットされます。</span><span class="sxs-lookup"><span data-stu-id="71a19-116">This selection resets a measure to `SUM` if it is set to any of the following aggregation function types:</span></span>  
  
-   <span data-ttu-id="71a19-117">By Account</span><span class="sxs-lookup"><span data-stu-id="71a19-117">By Account</span></span>  
  
-   <span data-ttu-id="71a19-118">Average of Children</span><span class="sxs-lookup"><span data-stu-id="71a19-118">Average of Children</span></span>  
  
-   <span data-ttu-id="71a19-119">First Child</span><span class="sxs-lookup"><span data-stu-id="71a19-119">First Child</span></span>  
  
-   <span data-ttu-id="71a19-120">Last Child</span><span class="sxs-lookup"><span data-stu-id="71a19-120">Last Child</span></span>  
  
-   <span data-ttu-id="71a19-121">Last Nonempty Child</span><span class="sxs-lookup"><span data-stu-id="71a19-121">Last Nonempty Child</span></span>  
  
-   <span data-ttu-id="71a19-122">First Nonempty Child</span><span class="sxs-lookup"><span data-stu-id="71a19-122">First Nonempty Child</span></span>  
  
-   <span data-ttu-id="71a19-123">なし</span><span class="sxs-lookup"><span data-stu-id="71a19-123">None</span></span>  
  
 <span data-ttu-id="71a19-124">このオプションでは、標準の集計関数である、 `Sum` 、 `Min` `Max` 、 `Count` 、または `Distinct``Count` のメジャーは変更されません。</span><span class="sxs-lookup"><span data-stu-id="71a19-124">This option does not change measures with a regular aggregation function: `Sum`, `Min`, `Max`, `Count`, or `Distinct``Count`.</span></span>  
  
 <span data-ttu-id="71a19-125">**準加法メンバーを含む ' Account ' 勘定科目ディメンションが検出されました。サーバーは、勘定科目の種類ごとに指定された準加法の動作に従って、このディメンションのメンバーを集計します。**</span><span class="sxs-lookup"><span data-stu-id="71a19-125">**The wizard has detected the 'Account" account dimension, which contains semiadditive members. The server will aggregate members of this dimension according to the semiadditive behavior specified for each account type.**</span></span>  
 <span data-ttu-id="71a19-126">Account 型のディメンションにより次元設定されたメジャー グループのすべてのメジャーが By Account 集計関数に設定され、このディメンションのメンバーは、勘定科目の種類ごとに指定されている準加法動作に従って集計されます。</span><span class="sxs-lookup"><span data-stu-id="71a19-126">Causes the system to set all measures from a measure group dimensioned by an Account type dimension to the By Account aggregation function and the server will aggregate members of the dimension according to the semiadditive behavior specified for each account type.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="71a19-127">ウィザードで Account 型のディメンションが検出された場合は、既定でこのオプションが選択されます。</span><span class="sxs-lookup"><span data-stu-id="71a19-127">This option is selected by default if the wizard detects an Account type dimension.</span></span>  
  
 <span data-ttu-id="71a19-128">**[個別のメジャーに準加法の動作を定義する]**</span><span class="sxs-lookup"><span data-stu-id="71a19-128">**Define semiadditive behavior for individual measures**</span></span>  
 <span data-ttu-id="71a19-129">各メジャーの準加法の動作を個別に選択します。</span><span class="sxs-lookup"><span data-stu-id="71a19-129">Selects the semiadditive behavior of each measure individually.</span></span> <span data-ttu-id="71a19-130">既定の設定は、`SUM` (完全加法) です。</span><span class="sxs-lookup"><span data-stu-id="71a19-130">The default setting is `SUM` (fully additive).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="71a19-131">ウィザードで Account 型のディメンションが検出されない場合は、既定でこのオプションが選択されます。</span><span class="sxs-lookup"><span data-stu-id="71a19-131">This option is selected by default if the wizard does not detect an Account type dimension.</span></span>  
  
 <span data-ttu-id="71a19-132">各メジャーに対して、次の表に示した種類から準加法の機能を選択できます。</span><span class="sxs-lookup"><span data-stu-id="71a19-132">For each measure, you can select from the types of semiadditive functionality described in the following table.</span></span>  
  
|<span data-ttu-id="71a19-133">準加法関数</span><span class="sxs-lookup"><span data-stu-id="71a19-133">Semiadditive function</span></span>|<span data-ttu-id="71a19-134">説明</span><span class="sxs-lookup"><span data-stu-id="71a19-134">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="71a19-135">Average of Children</span><span class="sxs-lookup"><span data-stu-id="71a19-135">Average of Children</span></span>|<span data-ttu-id="71a19-136">子の平均がメンバーの集計です。</span><span class="sxs-lookup"><span data-stu-id="71a19-136">The aggregation of a member is the average of its children.</span></span>|  
|<span data-ttu-id="71a19-137">[ByAccount]</span><span class="sxs-lookup"><span data-stu-id="71a19-137">ByAccount</span></span>|<span data-ttu-id="71a19-138">勘定科目の種類に対して指定された準加法を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="71a19-138">The system reads the semiadditive behavior specified for the account type.</span></span>|  
|<span data-ttu-id="71a19-139">Count</span><span class="sxs-lookup"><span data-stu-id="71a19-139">Count</span></span>|<span data-ttu-id="71a19-140">メンバーの数が集計です。</span><span class="sxs-lookup"><span data-stu-id="71a19-140">The aggregation is a count of members.</span></span>|  
|<span data-ttu-id="71a19-141">Distinct Count</span><span class="sxs-lookup"><span data-stu-id="71a19-141">Distinct Count</span></span>|<span data-ttu-id="71a19-142">一意のメンバーの数が集計です。</span><span class="sxs-lookup"><span data-stu-id="71a19-142">The aggregation is a count of unique members.</span></span>|  
|<span data-ttu-id="71a19-143">First Child</span><span class="sxs-lookup"><span data-stu-id="71a19-143">First Child</span></span>|<span data-ttu-id="71a19-144">メンバー値は時間ディメンションに従って最初の子の値として評価されます。</span><span class="sxs-lookup"><span data-stu-id="71a19-144">The member value is evaluated as the value of its first child along the time dimension.</span></span>|  
|<span data-ttu-id="71a19-145">FirstNonEmpty</span><span class="sxs-lookup"><span data-stu-id="71a19-145">FirstNonEmpty</span></span>|<span data-ttu-id="71a19-146">メンバー値はデータを格納する時間ディメンションに従って最初の子の値として評価されます。</span><span class="sxs-lookup"><span data-stu-id="71a19-146">The member value is evaluated as the value of its first child along the time dimension that contains data.</span></span>|  
|<span data-ttu-id="71a19-147">LastChild</span><span class="sxs-lookup"><span data-stu-id="71a19-147">LastChild</span></span>|<span data-ttu-id="71a19-148">メンバー値は時間ディメンションに従って最後の子の値として評価されます。</span><span class="sxs-lookup"><span data-stu-id="71a19-148">The member value is evaluated as the value of its last child along the time dimension.</span></span>|  
|<span data-ttu-id="71a19-149">LastNonEmpty</span><span class="sxs-lookup"><span data-stu-id="71a19-149">LastNonEmpty</span></span>|<span data-ttu-id="71a19-150">メンバー値はデータを格納する時間ディメンションに従って最後の子の値として評価されます。</span><span class="sxs-lookup"><span data-stu-id="71a19-150">The member value is evaluated as the value of its last child along the time dimension that contains data.</span></span>|  
|<span data-ttu-id="71a19-151">Max</span><span class="sxs-lookup"><span data-stu-id="71a19-151">Max</span></span>|<span data-ttu-id="71a19-152">標準最大集計関数が適用されます。</span><span class="sxs-lookup"><span data-stu-id="71a19-152">The standard maximum aggregation function is applied.</span></span>|  
|<span data-ttu-id="71a19-153">最小</span><span class="sxs-lookup"><span data-stu-id="71a19-153">Min</span></span>|<span data-ttu-id="71a19-154">標準最小集計関数が適用されます。</span><span class="sxs-lookup"><span data-stu-id="71a19-154">The standard minimum aggregation function is applied.</span></span>|  
|<span data-ttu-id="71a19-155">なし</span><span class="sxs-lookup"><span data-stu-id="71a19-155">None</span></span>|<span data-ttu-id="71a19-156">集計は適用されません。</span><span class="sxs-lookup"><span data-stu-id="71a19-156">No aggregation is applied.</span></span>|  
|<span data-ttu-id="71a19-157">SUM</span><span class="sxs-lookup"><span data-stu-id="71a19-157">Sum</span></span>|<span data-ttu-id="71a19-158">標準の合計関数が適用されます。</span><span class="sxs-lookup"><span data-stu-id="71a19-158">The standard summation function is applied.</span></span>|  
  
 <span data-ttu-id="71a19-159">ウィザードを完了すると、既存の準加法の動作は上書きされます。</span><span class="sxs-lookup"><span data-stu-id="71a19-159">Any existing semiadditive behavior is overwritten when you complete the wizard.</span></span>  
  
  
