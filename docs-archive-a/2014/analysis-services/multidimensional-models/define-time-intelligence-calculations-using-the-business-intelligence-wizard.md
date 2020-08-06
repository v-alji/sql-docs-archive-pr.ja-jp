---
title: ビジネスインテリジェンスウィザードを使用したタイムインテリジェンス計算の定義 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- period over period growth [Analysis Services]
- parallel period comparisons [Analysis Services]
- Business Intelligence enhancements [Analysis Services], time intelligence
- time views [Analysis Services]
- hierarchies [Analysis Services], time
- time periods [Analysis Services]
- moving averages
- time [Analysis Services]
- period to date [Analysis Services]
- calculations [Analysis Services], time
- time hierarchies [Analysis Services]
- time intelligence [Analysis Services]
ms.assetid: be36e8fc-f46e-4553-8623-b27d695c330b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 222efb572c227e6a8ca3d1e2295b662cb586184a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632760"
---
# <a name="define-time-intelligence-calculations-using-the-business-intelligence-wizard"></a><span data-ttu-id="d0dae-102">ビジネス インテリジェンス ウィザードを使用したタイム インテリジェンス計算の定義</span><span class="sxs-lookup"><span data-stu-id="d0dae-102">Define Time Intelligence Calculations using the Business Intelligence Wizard</span></span>
  <span data-ttu-id="d0dae-103">タイム インテリジェンス拡張機能は、選択した階層に時間計算 (または時間ビュー) を追加するキューブ拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="d0dae-103">The time intelligence enhancement is a cube enhancement that adds time calculations (or time views) to a selected hierarchy.</span></span> <span data-ttu-id="d0dae-104">この拡張機能では、次の計算のカテゴリがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d0dae-104">This enhancement supports the following categories of calculations:</span></span>  
  
-   <span data-ttu-id="d0dae-105">期間累計</span><span class="sxs-lookup"><span data-stu-id="d0dae-105">Period to date.</span></span>  
  
-   <span data-ttu-id="d0dae-106">前期比成長率</span><span class="sxs-lookup"><span data-stu-id="d0dae-106">Period over period growth.</span></span>  
  
-   <span data-ttu-id="d0dae-107">移動平均</span><span class="sxs-lookup"><span data-stu-id="d0dae-107">Moving averages.</span></span>  
  
-   <span data-ttu-id="d0dae-108">並列期間比較</span><span class="sxs-lookup"><span data-stu-id="d0dae-108">Parallel period comparisons.</span></span>  
  
 <span data-ttu-id="d0dae-109">時間ディメンションを持つキューブにタイム インテリジェンスを適用します</span><span class="sxs-lookup"><span data-stu-id="d0dae-109">You apply time intelligence to cubes that have a time dimension.</span></span> <span data-ttu-id="d0dae-110">(時間ディメンションは、`Type` プロパティが `Time` に設定されているディメンションです)。</span><span class="sxs-lookup"><span data-stu-id="d0dae-110">(A time dimension is a dimension whose `Type` property is set to `Time`).</span></span> <span data-ttu-id="d0dae-111">また、そのディメンションの時間属性には、`Type` プロパティの適切な設定 (Years や Months など) も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0dae-111">Additionally, the time attributes of that dimension must also have the appropriate setting (such as, Years or Months) for their `Type` property.</span></span> <span data-ttu-id="d0dae-112">ディメンション ウィザードを使用して時間ディメンションを作成すると、ディメンションとその属性の両方の `Type` プロパティが正しく設定されます。</span><span class="sxs-lookup"><span data-stu-id="d0dae-112">The `Type` property of both the dimension and its attributes will be set correctly if you use the Dimension Wizard to create the time dimension.</span></span>  
  
 <span data-ttu-id="d0dae-113">タイム インテリジェンスをキューブに追加するには、ビジネス インテリジェンス ウィザードを使用して、 **[拡張機能の選択]** ページの **[タイム インテリジェンスの定義]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="d0dae-113">To add time intelligence to a cube, you use the Business Intelligence Wizard, and select the **Define time intelligence** option on the **Choose Enhancement** page.</span></span> <span data-ttu-id="d0dae-114">このウィザードでは、タイム インテリジェンスの追加先となる階層を選択し、その階層内でタイム インテリジェンスを適用するメンバーを指定する手順が示されます。</span><span class="sxs-lookup"><span data-stu-id="d0dae-114">This wizard then guides you through the steps of selecting a hierarchy to which you are adding time intelligence and specifying which members in the hierarchy will have time intelligence applied to them.</span></span> <span data-ttu-id="d0dae-115">ウィザードの最後のページでは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 選択したタイムインテリジェンスを追加するために、データベースに対して行われる変更を確認できます。</span><span class="sxs-lookup"><span data-stu-id="d0dae-115">On the last page of the wizard, you can see the changes that will be made to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database to add the selected time intelligence.</span></span>  
  
## <a name="selecting-a-time-hierarchy"></a><span data-ttu-id="d0dae-116">時間階層の選択</span><span class="sxs-lookup"><span data-stu-id="d0dae-116">Selecting a Time Hierarchy</span></span>  
 <span data-ttu-id="d0dae-117">**[対象となる階層と計算の選択]** ページで、タイム インテリジェンス拡張機能の適用先となる時間階層を選択します。</span><span class="sxs-lookup"><span data-stu-id="d0dae-117">On the **Choose Target Hierarchy and Calculations** page, you select the time hierarchy to which the time enhancement applies.</span></span> <span data-ttu-id="d0dae-118">タイム インテリジェンス拡張機能は、ビジネス インテリジェンス ウィザードを実行するたびに 1 つの時間階層にのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="d0dae-118">You can apply the time enhancement to only one time hierarchy every time that you run the Business Intelligence Wizard.</span></span> <span data-ttu-id="d0dae-119">複数の時間階層に拡張機能を適用する場合は、ウィザードをもう一度実行します。</span><span class="sxs-lookup"><span data-stu-id="d0dae-119">If you want to apply the enhancement to more than one time hierarchy, you run the wizard again.</span></span>  
  
 <span data-ttu-id="d0dae-120">時間階層を選択したら、 **[使用できる時間の計算]** の一覧で、階層に適用する計算を選択します。</span><span class="sxs-lookup"><span data-stu-id="d0dae-120">After you select a time hierarchy, in the **Available time calculations** list, you select the calculations that apply to the hierarchy.</span></span> <span data-ttu-id="d0dae-121">一覧表示される計算は、階層内のレベルと、各レベルの属性の `Type` プロパティ設定によって異なります。</span><span class="sxs-lookup"><span data-stu-id="d0dae-121">The calculations that are listed depend on the levels in the hierarchy, and on the `Type` property setting for the attribute for each level.</span></span> <span data-ttu-id="d0dae-122">たとえば、Years 階層では年度累計と前年比成長率がサポートされますが、Quarters 階層ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="d0dae-122">For example, a Years hierarchy supports Year to Date and Year Over Year Growth, but a Quarters hierarchy does not.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d0dae-123">Timeintelligence.xml テンプレート ファイルでは、 **[使用できる時間の計算]** に一覧表示される時間計算を定義します。</span><span class="sxs-lookup"><span data-stu-id="d0dae-123">The Timeintelligence.xml template file defines the time calculations that are listed in **Available time calculations**.</span></span> <span data-ttu-id="d0dae-124">一覧表示された計算がニーズに合わない場合は、既存の計算を変更するか、Timeintelligence.xml ファイルに新しい計算を追加できます。</span><span class="sxs-lookup"><span data-stu-id="d0dae-124">If the listed calculations do not meet your needs, you can either change the existing calculations or add new calculations to the Timeintelligence.xml file.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="d0dae-125">計算の説明を表示するには、上矢印と下矢印を使用して、その計算を強調表示します。</span><span class="sxs-lookup"><span data-stu-id="d0dae-125">To view a description for a calculation, use the up and down arrows to highlight that calculation.</span></span>  
  
## <a name="apply-time-views-to-members"></a><span data-ttu-id="d0dae-126">メンバーへの時間ビューの適用</span><span class="sxs-lookup"><span data-stu-id="d0dae-126">Apply Time Views to Members</span></span>  
 <span data-ttu-id="d0dae-127">**[計算範囲の定義]** ページで、新しい時間ビューを適用するメンバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="d0dae-127">On the **Define Scope of Calculations** page, you specify the members to which the new time views apply.</span></span> <span data-ttu-id="d0dae-128">新しい時間ビューは、次のいずれかのオブジェクトに適用できます。</span><span class="sxs-lookup"><span data-stu-id="d0dae-128">You can apply the new time views to one of the following objects:</span></span>  
  
-   <span data-ttu-id="d0dae-129">**勘定科目ディメンションのメンバー** 。 **[計算範囲の定義]** ページの **[使用できるメジャー]** 一覧には、勘定科目ディメンションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d0dae-129">**Members of an account dimension** On the **Define Scope of Calculations** page, the **Available measures** list includes account dimensions.</span></span> <span data-ttu-id="d0dae-130">勘定科目ディメンションの `Type` プロパティは `Accounts` に設定されています。</span><span class="sxs-lookup"><span data-stu-id="d0dae-130">Account dimensions have their `Type` properties set to `Accounts`.</span></span> <span data-ttu-id="d0dae-131">勘定科目ディメンションがあるのに、そのディメンションが **[使用できるメジャー]** 一覧に表示されない場合は、ビジネス インテリジェンス ウィザードを使用して、そのディメンションに勘定科目インテリジェンスを適用できます。</span><span class="sxs-lookup"><span data-stu-id="d0dae-131">If you have an accounts dimension but that dimension does not appear in the **Available measures** list, you can use the Business Intelligence Wizard to apply the account intelligence to that dimension.</span></span> <span data-ttu-id="d0dae-132">詳細については、「 [ディメンションへの勘定科目インテリジェンスの追加](bi-wizard-add-account-intelligence-to-a-dimension.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d0dae-132">For more information, see [Add Account Intelligence to a Dimension](bi-wizard-add-account-intelligence-to-a-dimension.md).</span></span>  
  
-   <span data-ttu-id="d0dae-133">**メジャー** 。勘定科目ディメンションを指定する代わりに、時間ビューの適用先となるメジャーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="d0dae-133">**Measures** Instead of specifying an account dimension, you can specify the measures to which the time views apply.</span></span> <span data-ttu-id="d0dae-134">この場合、選択した時間計算の適用先となるビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="d0dae-134">In this case, select the views to which selected time calculations apply.</span></span> <span data-ttu-id="d0dae-135">たとえば、資産および負債は年度累計のデータであるため、年度累計の計算は資産または負債のメジャーに適用しません。</span><span class="sxs-lookup"><span data-stu-id="d0dae-135">For example, assets and liabilities are year-to-date data; therefore, you do not apply a Year-to-Date calculation to assets or liabilities measures.</span></span>  
  
## <a name="viewing-the-time-intelligence-enhancement"></a><span data-ttu-id="d0dae-136">タイム インテリジェンス拡張機能の表示</span><span class="sxs-lookup"><span data-stu-id="d0dae-136">Viewing the Time Intelligence Enhancement</span></span>  
 <span data-ttu-id="d0dae-137">ビジネス インテリジェンス ウィザードの最後のページで、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースに対して行われる変更内容を表示できます。</span><span class="sxs-lookup"><span data-stu-id="d0dae-137">On the final page of the Business Intelligence Wizard, you can view the changes that will be made to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="d0dae-138">タイム インテリジェンス拡張機能では、次の表で説明されているように、選択した時間ディメンション、関連付けられているデータ ソース ビュー、および関連付けられているキューブがウィザードによって変更されます。</span><span class="sxs-lookup"><span data-stu-id="d0dae-138">For a time intelligence enhancement, the wizard will change the selected time dimension, associated data source view, and associated cube as described in the following table.</span></span>  
  
|<span data-ttu-id="d0dae-139">Object</span><span class="sxs-lookup"><span data-stu-id="d0dae-139">Object</span></span>|<span data-ttu-id="d0dae-140">Change</span><span class="sxs-lookup"><span data-stu-id="d0dae-140">Change</span></span>|  
|------------|------------|  
|<span data-ttu-id="d0dae-141">時間ディメンション</span><span class="sxs-lookup"><span data-stu-id="d0dae-141">Time dimension</span></span>|<span data-ttu-id="d0dae-142">計算 (またはビュー) ごとに属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="d0dae-142">Adds an attribute for each calculation (or view).</span></span>|  
|<span data-ttu-id="d0dae-143">データ ソース ビュー</span><span class="sxs-lookup"><span data-stu-id="d0dae-143">Data source view</span></span>|<span data-ttu-id="d0dae-144">時間ディメンションの新しい属性ごとに、計算される列を時間テーブルに追加します。</span><span class="sxs-lookup"><span data-stu-id="d0dae-144">Adds a calculated column in the time table for each new attribute in the time dimension.</span></span>|  
|<span data-ttu-id="d0dae-145">キューブ</span><span class="sxs-lookup"><span data-stu-id="d0dae-145">Cube</span></span>|<span data-ttu-id="d0dae-146">計算を実行する多次元式 (MDX) コードを定義する、計算されるメンバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="d0dae-146">Adds a calculated member that defines the Multidimensional Expressions (MDX) code to perform the calculation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0dae-147">参照</span><span class="sxs-lookup"><span data-stu-id="d0dae-147">See Also</span></span>  
 [<span data-ttu-id="d0dae-148">計算されるメンバーの作成</span><span class="sxs-lookup"><span data-stu-id="d0dae-148">Create Calculated Members</span></span>](create-calculated-members.md)  
  
  
