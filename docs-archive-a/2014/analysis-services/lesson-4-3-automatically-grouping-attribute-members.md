---
title: 属性メンバーの自動的なグループ化 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9fb2cda3-a122-4a4c-82e0-3454865eef04
author: minewiskan
ms.author: owend
ms.openlocfilehash: 820231263362a92584a15556e999d69f286349b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742653"
---
# <a name="automatically-grouping-attribute-members"></a><span data-ttu-id="10600-102">属性メンバーの自動的なグループ化</span><span class="sxs-lookup"><span data-stu-id="10600-102">Automatically Grouping Attribute Members</span></span>
  <span data-ttu-id="10600-103">キューブを表示するとき、通常は、ある属性階層のメンバーと別の属性階層のメンバーとを多次元化します。</span><span class="sxs-lookup"><span data-stu-id="10600-103">When you browse a cube, you typically dimension the members of one attribute hierarchy by the members of another attribute hierarchy.</span></span> <span data-ttu-id="10600-104">たとえば、都市別、製品別、または性別ごとに顧客の売上をグループ化して表示します。</span><span class="sxs-lookup"><span data-stu-id="10600-104">For example, you might group customer sales by city, by product purchased, or by gender.</span></span> <span data-ttu-id="10600-105">ただし、属性の種類によっては、属性 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 階層内のメンバーの分布に基づいて、属性メンバーのグループを自動的に作成すると便利です。</span><span class="sxs-lookup"><span data-stu-id="10600-105">However, with certain types of attributes, it is useful to have [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] automatically create groupings of attribute members based on the distribution of the members within an attribute hierarchy.</span></span> <span data-ttu-id="10600-106">たとえば、顧客の年収に基づいてグループが作成されるように [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] を設定できます。</span><span class="sxs-lookup"><span data-stu-id="10600-106">For example, you can have [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] create groups of yearly income values for customers.</span></span> <span data-ttu-id="10600-107">このようにグループ化した場合、属性階層を表示したときには、メンバーそのものではなく、グループの名前と値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="10600-107">When you do this, users who browse the attribute hierarchy will see the names and values of the groups instead of the members themselves.</span></span> <span data-ttu-id="10600-108">ユーザーに提示されるレベル数が限定されるので、分析が容易になります。</span><span class="sxs-lookup"><span data-stu-id="10600-108">This limits the number of levels that are presented to users, which can be more useful for analysis.</span></span>

 <span data-ttu-id="10600-109">**DiscretizationMethod** プロパティは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] にグループを作成させるかどうか、どのような種類のグループ化を実行するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="10600-109">The **DiscretizationMethod** property determines whether [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] creates groupings, and determines the type of grouping that is performed.</span></span> <span data-ttu-id="10600-110">既定では、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] はグループ化を実行しません。</span><span class="sxs-lookup"><span data-stu-id="10600-110">By default, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] does not perform any groupings.</span></span> <span data-ttu-id="10600-111">自動グループ化を有効にすると、属性の構造に基づいて、最適なグループ化の方法が [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] によって自動的に判断されます。また、次の一覧からいずれかのグループ化アルゴリズムを選択してグループ化の方法を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="10600-111">When you enable automatic groupings, you can allow [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to automatically determine the best grouping method based on the structure of the attribute, or you can choose one of the grouping algorithms in the following list to specify the grouping method:</span></span>

 <span data-ttu-id="10600-112">**[Equalareas]** [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]ディメンションメンバーの母集団全体がグループ全体に均等に分散されるように、グループ範囲を作成します。</span><span class="sxs-lookup"><span data-stu-id="10600-112">**EqualAreas** [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] creates group ranges so that the total population of dimension members is distributed equally across the groups.</span></span>

 <span data-ttu-id="10600-113">**クラスター** [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]ガウス分布を使用して K を意味するクラスター化方法を使用して、入力値に対して1次元クラスタリングを実行することで、グループを作成します。</span><span class="sxs-lookup"><span data-stu-id="10600-113">**Clusters** [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] creates groups by performing single-dimensional clustering on the input values by using the K-Means clustering method with Gaussian distributions.</span></span> <span data-ttu-id="10600-114">このオプションは、数値列でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="10600-114">This option is valid only for numeric columns.</span></span>

 <span data-ttu-id="10600-115">グループ化方法を指定したら、 **DiscretizationBucketCount** プロパティでグループの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="10600-115">After you specify a grouping method, you must specify the number of groups, by using the **DiscretizationBucketCount** property.</span></span> <span data-ttu-id="10600-116">詳細については、「[グループ属性メンバー &#40;分離&#41;](multidimensional-models/attribute-properties-group-attribute-members.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10600-116">For more information, see [Group Attribute Members &#40;Discretization&#41;](multidimensional-models/attribute-properties-group-attribute-members.md)</span></span>

 <span data-ttu-id="10600-117">このトピックの実習では、 **Customer** ディメンションの年収値、 **Employees** ディメンションの病気休暇時間、および **Employees** ディメンションの休暇時間でグループ化を行います。</span><span class="sxs-lookup"><span data-stu-id="10600-117">In the tasks in this topic, you will enable different types of groupings for the following: the yearly income values in the **Customer** dimension; the number of employee sick leave hours in the **Employees** dimension; and the number of employee vacation hours in the **Employees** dimension.</span></span> <span data-ttu-id="10600-118">その後、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブを処理して表示し、メンバー グループの効果を確認します。</span><span class="sxs-lookup"><span data-stu-id="10600-118">You will then process and browse the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube to view the effect of the member groups.</span></span> <span data-ttu-id="10600-119">最後に、メンバー グループのプロパティを変更し、グループの種類を変更した場合の影響を確認します。</span><span class="sxs-lookup"><span data-stu-id="10600-119">Finally, you will modify the member group properties to see the effect of the change in grouping type.</span></span>

## <a name="grouping-attribute-hierarchy-members-in-the-customer-dimension"></a><span data-ttu-id="10600-120">Customer ディメンションにおける属性階層メンバーのグループ化</span><span class="sxs-lookup"><span data-stu-id="10600-120">Grouping Attribute Hierarchy Members in the Customer Dimension</span></span>

1.  <span data-ttu-id="10600-121">ソリューション エクスプローラーで、 **[ディメンション]** フォルダーの **Customer** をダブルクリックし、Customer ディメンションのディメンション デザイナーを開きます。</span><span class="sxs-lookup"><span data-stu-id="10600-121">In Solution Explorer, double-click **Customer** in the **Dimensions** folder to open Dimension Designer for the Customer dimension.</span></span>

2.  <span data-ttu-id="10600-122">**[データ ソース ビュー]** ペインで **Customer** テーブルを右クリックし、 **[データの探索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="10600-122">In the **Data Source View** pane, right-click the **Customer** table, and then click **Explore Data**.</span></span>

     <span data-ttu-id="10600-123">**YearlyIncome** 列の値の範囲に注目してください。</span><span class="sxs-lookup"><span data-stu-id="10600-123">Notice the range of values for the **YearlyIncome** column.</span></span> <span data-ttu-id="10600-124">メンバーをグループ化しない限り、これらの値は **Yearly Income** 属性階層のメンバーになります。</span><span class="sxs-lookup"><span data-stu-id="10600-124">These values become the members of the **Yearly Income** attribute hierarchy, unless you enable member grouping.</span></span>

3.  <span data-ttu-id="10600-125">**[Customer テーブルの探索]** タブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="10600-125">Close the **Explore Customer Table** tab.</span></span>

4.  <span data-ttu-id="10600-126">**[属性]** ペインで、 **[Yearly Income]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="10600-126">In the **Attributes** pane, select **Yearly Income**.</span></span>

5.  <span data-ttu-id="10600-127">プロパティウィンドウで、 **DiscretizationMethod**プロパティの値を**Automatic**に変更し、 **DiscretizationBucketCount**プロパティの値をに変更し `5` ます。</span><span class="sxs-lookup"><span data-stu-id="10600-127">In the Properties window, change the value for the **DiscretizationMethod** property to **Automatic** and change the value for the **DiscretizationBucketCount** property to `5`.</span></span>

     <span data-ttu-id="10600-128">次の図は、変更後の **Yearly Income**プロパティを示しています。</span><span class="sxs-lookup"><span data-stu-id="10600-128">The following image shows the modified properties for **Yearly Income**.</span></span>

     <span data-ttu-id="10600-129">![年収の変更されたプロパティ](../../2014/tutorials/media/l4-discretizationmethod-1.gif "年収の変更されたプロパティ")</span><span class="sxs-lookup"><span data-stu-id="10600-129">![Modified properties for Yearly Income](../../2014/tutorials/media/l4-discretizationmethod-1.gif "Modified properties for Yearly Income")</span></span>

## <a name="grouping-attribute-hierarchy-members-in-the-employee-dimension"></a><span data-ttu-id="10600-130">Employee ディメンションにおける属性階層メンバーのグループ化</span><span class="sxs-lookup"><span data-stu-id="10600-130">Grouping Attribute Hierarchy Members in the Employee Dimension</span></span>

1.  <span data-ttu-id="10600-131">Employee ディメンションのディメンション デザイナーに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="10600-131">Switch to Dimension Designer for the Employee dimension.</span></span>

2.  <span data-ttu-id="10600-132">**[データ ソース ビュー]** ペインで **Employee** テーブルを右クリックし、 **[データの探索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="10600-132">In the **Data Source View** pane, right-click the **Employee** table, and then click **Explore Data**.</span></span>

     <span data-ttu-id="10600-133">**SickLeaveHours** 列および **VacationHours** 列の値に注目してください。</span><span class="sxs-lookup"><span data-stu-id="10600-133">Notice the values for the **SickLeaveHours** column and the **VacationHours** column.</span></span>

3.  <span data-ttu-id="10600-134">**[Employee テーブルの探索]** タブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="10600-134">Close the **Explore Employee Table** tab.</span></span>

4.  <span data-ttu-id="10600-135">**[属性]** ペインで、 **[Sick Leave Hours]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="10600-135">In the **Attributes** pane, select **Sick Leave Hours**.</span></span>

5.  <span data-ttu-id="10600-136">プロパティウィンドウで、 **DiscretizationMethod**プロパティの値を**クラスター**に変更し、 **DiscretizationBucketCount**プロパティの値をに変更し `5` ます。</span><span class="sxs-lookup"><span data-stu-id="10600-136">In the Properties window, change the value for the **DiscretizationMethod** property to **Clusters** and change the value for the **DiscretizationBucketCount** property to `5`.</span></span>

6.  <span data-ttu-id="10600-137">**[属性]** ペインで、 **[Vacation Hours]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="10600-137">In the **Attributes** pane, select **Vacation Hours**.</span></span>

7.  <span data-ttu-id="10600-138">プロパティウィンドウで、 **DiscretizationMethod**プロパティの値を**Equal Areas**に変更し、 **DiscretizationBucketCount**プロパティの値をに変更し `5` ます。</span><span class="sxs-lookup"><span data-stu-id="10600-138">In the Properties window, change the value for the **DiscretizationMethod** property to **Equal Areas** and change the value for the **DiscretizationBucketCount** property to `5`.</span></span>

## <a name="browsing-the-modified-attribute-hierarchies"></a><span data-ttu-id="10600-139">変更した属性階層の表示</span><span class="sxs-lookup"><span data-stu-id="10600-139">Browsing the Modified Attribute Hierarchies</span></span>

1.  <span data-ttu-id="10600-140">**で、** [ビルド] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]メニューの **[Analysis Services Tutorial の配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="10600-140">On the **Build** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>

2.  <span data-ttu-id="10600-141">配置が正常に完了したら、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブのキューブ デザイナーに切り替え、 **[ブラウザー]** タブのツール バーで **[再接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="10600-141">When deployment has successfully completed, switch to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click **Reconnect** on the **Browser** tab.</span></span>

3.  <span data-ttu-id="10600-142">Excel アイコンをクリックし、 **[有効化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="10600-142">Click the Excel icon, and then click **Enable**.</span></span>

4.  <span data-ttu-id="10600-143">**Internet Sales-Sales Amount** メジャーをピボットテーブル フィールド リストの値領域にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="10600-143">Drag the **Internet Sales-Sales Amount** measure to the Values area of the PivotTable Field List.</span></span>

5.  <span data-ttu-id="10600-144">フィールド リストで **Product** ディメンションを展開します。次に、 **[Product Model Lines]** ユーザー階層をフィールド リストの **[行ラベル]** 領域にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="10600-144">In the field list, expand the **Product** dimension, and then drag the **Product Model Lines** user hierarchy to the **Row Labels** area of the field list.</span></span>

6.  <span data-ttu-id="10600-145">フィールド リストで **Customer** ディメンションを展開し、 **Demographic** 表示フォルダーを展開します。次に、 **Yearly Income** 属性階層を **[列ラベル]** 領域にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="10600-145">Expand the **Customer** dimension in the field list, expand the **Demographic** display folder, and then drag the **Yearly Income** attribute hierarchy to the **Column Labels** area.</span></span>

     <span data-ttu-id="10600-146">**Yearly Income** 属性階層のメンバーが 6 つのバケットにグループ化されました。この中には、年収が不明である顧客への売上のバケットも含まれています。</span><span class="sxs-lookup"><span data-stu-id="10600-146">The members of the **Yearly Income** attribute hierarchy are now grouped into six buckets, including a bucket for sales to customers whose yearly income is unknown.</span></span> <span data-ttu-id="10600-147">すべてのバケットが表示されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="10600-147">Not all buckets are displayed.</span></span>

7.  <span data-ttu-id="10600-148">列領域から **Yearly Income** 属性階層を削除し、 **[値]** 領域から **Internet Sales-Sales Amount** メジャーを削除します。</span><span class="sxs-lookup"><span data-stu-id="10600-148">Remove the **Yearly Income** attribute hierarchy from the columns area and remove the **Internet Sales-Sales Amount** measure from the **Values** area.</span></span>

8.  <span data-ttu-id="10600-149">**Reseller Sales-Sales Amount** メジャーをデータ領域に追加します。</span><span class="sxs-lookup"><span data-stu-id="10600-149">Add the **Reseller Sales-Sales Amount** measure to the data area.</span></span>

9. <span data-ttu-id="10600-150">フィールド リストで **Employee** ディメンションを展開し、 **Organization**を展開します。次に、 **[Sick Leave Hours]** を **[列ラベル]** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="10600-150">In the field list, expand the **Employee** dimension, expand **Organization**, then drag **Sick Leave Hours** to **Column Labels**.</span></span>

     <span data-ttu-id="10600-151">2 つのグループのうちの 1 つは、すべて従業員によって売り上げられた売上データです</span><span class="sxs-lookup"><span data-stu-id="10600-151">Notice that all sales are made by employees within one of two groups.</span></span> <span data-ttu-id="10600-152">病欠時間が 32 ～ 42 時間の従業員は、病欠時間が 20 ～ 31 時間の従業員よりも大幅に売り上げていることもわかります。</span><span class="sxs-lookup"><span data-stu-id="10600-152">Notice also that the employees with 32 - 42 sick leave hours made significantly more sales than employees with 20 - 31 sick leave hours.</span></span>

     <span data-ttu-id="10600-153">次の図は、従業員の病欠時間別の売上ディメンションを示します。</span><span class="sxs-lookup"><span data-stu-id="10600-153">The following image shows sales dimensioned by employee sick leave hours.</span></span>

     <span data-ttu-id="10600-154">![従業員の病欠時間数ごとに配列された売上高](../../2014/tutorials/media/l4-discretizationmethod-2.gif "従業員の病欠時間数ごとに配列された売上高")</span><span class="sxs-lookup"><span data-stu-id="10600-154">![Sales dimensioned by employee sick leave hours](../../2014/tutorials/media/l4-discretizationmethod-2.gif "Sales dimensioned by employee sick leave hours")</span></span>

10. <span data-ttu-id="10600-155">**データ** ペインの列領域から **Sick Leave Hours** 属性階層を削除します。</span><span class="sxs-lookup"><span data-stu-id="10600-155">Remove the **Sick Leave Hours** attribute hierarchy from the column area of the **Data** pane.</span></span>

11. <span data-ttu-id="10600-156">**Vacation Hours** を **データ** ペインの列領域に追加します。</span><span class="sxs-lookup"><span data-stu-id="10600-156">Add **Vacation Hours** to the column area of the **Data** pane.</span></span>

     <span data-ttu-id="10600-157">EqualAreas グループ化方法に基づいて、2 つのグループが表示されます。</span><span class="sxs-lookup"><span data-stu-id="10600-157">Notice that two groups appear, based on the equal areas grouping method.</span></span> <span data-ttu-id="10600-158">他の 3 つのグループはデータ値がないため、表示されません。</span><span class="sxs-lookup"><span data-stu-id="10600-158">Three other groups are hidden because they contain no data values.</span></span>

## <a name="modifying-grouping-properties-and-reviewing-the-effect-of-the-changes"></a><span data-ttu-id="10600-159">グループ化のプロパティの変更と、その影響の確認</span><span class="sxs-lookup"><span data-stu-id="10600-159">Modifying Grouping Properties and Reviewing the Effect of the Changes</span></span>

1.  <span data-ttu-id="10600-160">**Employee** ディメンションのディメンション デザイナーに切り替え、 **[属性]** ペインで **[Vacation Hours]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="10600-160">Switch to Dimension Designer for the **Employee** dimension, and then select **Vacation Hours** in the **Attributes** pane.</span></span>

2.  <span data-ttu-id="10600-161">[プロパティ] ウィンドウで、 **DiscretizationBucketCount** プロパティの値を **10**に変更します。</span><span class="sxs-lookup"><span data-stu-id="10600-161">In the Properties window, change the value of the **DiscretizationBucketCount** property to **10.**</span></span>

3.  <span data-ttu-id="10600-162">**で、** [ビルド] [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]メニューの **[Analysis Services Tutorial の配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="10600-162">On the **Build** menu of [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>

4.  <span data-ttu-id="10600-163">配置が正常に完了したら、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブのキューブ デザイナーに戻ります。</span><span class="sxs-lookup"><span data-stu-id="10600-163">When deployment has successfully completed, switch back to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span>

5.  <span data-ttu-id="10600-164">**[ブラウザー]** タブで **[再接続]** をクリックし、Excel アイコンをクリックします。グループ化の方法を変更した場合の影響を確認できるように、次のようにピボットテーブルを再構築します。</span><span class="sxs-lookup"><span data-stu-id="10600-164">Click **Reconnect** on the **Browser** tab, click the Excel icon, and then reconstruct the PivotTable so that you can view the effect of the change to the grouping method:</span></span>

    1.  <span data-ttu-id="10600-165">Reseller Sales-Sales Amount を [値] にドラッグする</span><span class="sxs-lookup"><span data-stu-id="10600-165">Drag Reseller Sales-Sales Amount to Values</span></span>

    2.  <span data-ttu-id="10600-166">Vacation Hours (Employees Organization フォルダー内) を [列] にドラッグする</span><span class="sxs-lookup"><span data-stu-id="10600-166">Drag Vacation Hours (in the Employees Organization folder) to Columns</span></span>

    3.  <span data-ttu-id="10600-167">Product Model Lines を [行] にドラッグする</span><span class="sxs-lookup"><span data-stu-id="10600-167">Drag Product Model Lines to Rows</span></span>

     <span data-ttu-id="10600-168">**Vacation Hours** 属性メンバーのグループが 3 つあります。各メンバーに製品の売上の値が含まれています</span><span class="sxs-lookup"><span data-stu-id="10600-168">Notice that there are now three groups of members of the **Vacation Hours** attribute that have sales values for products.</span></span> <span data-ttu-id="10600-169">(他の 7 つのグループには、売上データのあるメンバーが存在しません)。</span><span class="sxs-lookup"><span data-stu-id="10600-169">(The other seven groups contain members with no sales data.)</span></span>

## <a name="next-task-in-lesson"></a><span data-ttu-id="10600-170">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="10600-170">Next Task in Lesson</span></span>
 [<span data-ttu-id="10600-171">属性階層の非表示化と無効化</span><span class="sxs-lookup"><span data-stu-id="10600-171">Hiding and Disabling Attribute Hierarchies</span></span>](lesson-4-4-hiding-and-disabling-attribute-hierarchies.md)

## <a name="see-also"></a><span data-ttu-id="10600-172">参照</span><span class="sxs-lookup"><span data-stu-id="10600-172">See Also</span></span>
 [<span data-ttu-id="10600-173">属性メンバーのグループ化 (分離)</span><span class="sxs-lookup"><span data-stu-id="10600-173">Group Attribute Members &#40;Discretization&#41;</span></span>](multidimensional-models/attribute-properties-group-attribute-members.md)


