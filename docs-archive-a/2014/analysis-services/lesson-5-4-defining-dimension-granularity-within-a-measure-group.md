---
title: メジャーグループ内でのディメンション粒度の定義 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4f079485-9eb4-405c-9a20-81258298b810
author: minewiskan
ms.author: owend
ms.openlocfilehash: dd1119da70631d66debdf79ecf8c911eedd06d44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639767"
---
# <a name="defining-dimension-granularity-within-a-measure-group"></a><span data-ttu-id="8ede2-102">メジャー グループでのディメンション粒度の定義</span><span class="sxs-lookup"><span data-stu-id="8ede2-102">Defining Dimension Granularity within a Measure Group</span></span>
  <span data-ttu-id="8ede2-103">ファクト データは、利用目的ごとに異なる粒度でディメンションを作成しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="8ede2-103">Users will want to dimension fact data at different granularity or specificity for different purposes.</span></span> <span data-ttu-id="8ede2-104">たとえば、販売店やインターネットでの売上データを日ごとに記録する一方で、販売量は月ごとまたは四半期ごとに記録することが考えられます。</span><span class="sxs-lookup"><span data-stu-id="8ede2-104">For example, sales data for reseller or internet sales may be recorded for each day, whereas sales quota information may only exist at the month or quarter level.</span></span> <span data-ttu-id="8ede2-105">このようなシナリオでは、ファクト テーブルごとに異なる詳細度を、時間のディメンションに設定します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-105">In these scenarios, users will want a time dimension with a different grain or level of detail for each of these different fact tables.</span></span> <span data-ttu-id="8ede2-106">新しいデータベース ディメンションを定義する場合、このようにさまざまに異なる詳細度を設定して時間のディメンションを定義することもできますが、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]を使用すると、さらに容易にディメンションを定義できます。</span><span class="sxs-lookup"><span data-stu-id="8ede2-106">While you could define a new database dimension as a time dimension with this different grain, there is an easier way with [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="8ede2-107">メジャー グループでディメンションを使用する場合、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]の既定では、ディメンションのキー属性に基づいてディメンションの詳細度が決定されます。</span><span class="sxs-lookup"><span data-stu-id="8ede2-107">By default in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], when a dimension is used within a measure group, the grain of the data within that dimension is based on the key attribute of the dimension.</span></span> <span data-ttu-id="8ede2-108">たとえば、あるメジャー グループに時間のディメンションが存在し、その時間ディメンションの既定の詳細度が日単位である場合は、メジャー グループ内のそのディメンションの既定の詳細度が日単位になります。</span><span class="sxs-lookup"><span data-stu-id="8ede2-108">For example, when a time dimension is included within a measure group and the default grain of the time dimension is daily, the default grain of that dimension within the measure group is daily.</span></span> <span data-ttu-id="8ede2-109">このチュートリアルで使用する **Internet Sales** (インターネット売上) や **Reseller Sales** (販売店売上) メジャー グループなどのように、既定の詳細度が適切である場合は数多くあります。</span><span class="sxs-lookup"><span data-stu-id="8ede2-109">Many times this is appropriate, such as for the **Internet Sales** and **Reseller Sales** measure groups in this tutorial.</span></span> <span data-ttu-id="8ede2-110">しかし、販売量や予算などのメジャー グループに存在するディメンションには、月単位、または四半期単位の詳細度がより適切です。</span><span class="sxs-lookup"><span data-stu-id="8ede2-110">However, when such a dimension is included in other types of measure groups, such as in a sales quota or budget measure group, a monthly or quarterly grain is generally more appropriate.</span></span>  
  
 <span data-ttu-id="8ede2-111">キューブ ディメンションに既定値以外の詳細度を指定するには、具体的なメジャー グループ内で使用するキューブ ディメンションの "粒度" 属性を変更します。この操作は、キューブ デザイナーの **[ディメンションの使用法]** タブで行います。</span><span class="sxs-lookup"><span data-stu-id="8ede2-111">To specify a grain for a cube dimension other than the default grain, you modify the granularity attribute for a cube dimension as used within a particular measure group on the **Dimension Usage** tab of Cube Designer.</span></span> <span data-ttu-id="8ede2-112">指定のメジャー グループのディメンションの詳細度を、そのディメンションのキー属性以外の属性に変更する場合は、メジャー グループ内の他のすべての属性を、新しい "粒度" 属性に関連付ける必要があります (間接的な関連付けも有効です)。</span><span class="sxs-lookup"><span data-stu-id="8ede2-112">When you change the grain of a dimension within a specific measure group to an attribute other than the key attribute for that dimension, you must guarantee that all other attributes in the measure group are directly or indirectly related to new granularity attribute.</span></span> <span data-ttu-id="8ede2-113">関連付けを行うには、"粒度" 属性として指定した属性と、その他のすべての属性との間に、属性リレーションシップを指定します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-113">You do this by specifying attribute relationships between all other attributes and the attribute that is specified as the granularity attribute in the measure group.</span></span> <span data-ttu-id="8ede2-114">この場合、属性リレーションシップを移動するのではなく、追加の属性リレーションシップを定義します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-114">In this case, you define additional attribute relationships rather than move attribute relationships.</span></span> <span data-ttu-id="8ede2-115">"粒度" 属性として指定した属性は、メジャー グループ内のディメンションの残りの属性のキー属性になります。</span><span class="sxs-lookup"><span data-stu-id="8ede2-115">The attribute that is specified as the granularity attribute effectively becomes the key attribute within the measure group for the remaining attributes in the dimension.</span></span> <span data-ttu-id="8ede2-116">属性リレーションシップを適切に指定しないと、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] は値を正しく集計できません。これについては、このトピックの実習で確認します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-116">If you do not specify attribute relationships appropriately, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] will not be able to aggregate values correctly, as you will see in the tasks in this topic.</span></span>  
  
 <span data-ttu-id="8ede2-117">詳細については、「 [ディメンション リレーションシップ](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)」および「 [ファクト リレーションシップとファクト リレーションシップのプロパティの定義](multidimensional-models/define-a-regular-relationship-and-regular-relationship-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ede2-117">For more information, see [Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md), [Define a Regular Relationship and Regular Relationship Properties](multidimensional-models/define-a-regular-relationship-and-regular-relationship-properties.md).</span></span>  
  
 <span data-ttu-id="8ede2-118">このトピックの実習では、Sales Quotas メジャー グループを追加し、このメジャー グループの Date ディメンションの粒度を月単位 (Month) に設定します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-118">In the tasks in this topic, you add a Sales Quotas measure group and define the granularity of the Date dimension in this measure group to be monthly.</span></span> <span data-ttu-id="8ede2-119">次に、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] が値を適切に集計できるよう、Month 属性とその他の属性との間に属性リレーションシップを定義します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-119">You then define attribute relationships between the month attribute and other dimension attributes to ensure that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] aggregates values correctly.</span></span>  
  
## <a name="adding-tables-and-defining-the-sales-quotas-measure-group"></a><span data-ttu-id="8ede2-120">テーブルの追加と Sales Quotas メジャー グループの定義</span><span class="sxs-lookup"><span data-stu-id="8ede2-120">Adding Tables and Defining the Sales Quotas Measure Group</span></span>  
  
1.  <span data-ttu-id="8ede2-121">**Adventure Works DW 2012** データ ソース ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="8ede2-121">Switch to the **Adventure Works DW 2012** data source view.</span></span>  
  
2.  <span data-ttu-id="8ede2-122">[**ダイアグラムオーガナイザー** ] ペイン内の任意の場所を右クリックし、[**新しいダイアグラム**] をクリックして、ダイアグラムに名前を指定し `Sales Quotas` ます。</span><span class="sxs-lookup"><span data-stu-id="8ede2-122">Right-click anywhere in the **Diagram Organizer** pane, click **New Diagram**, and then name the diagram `Sales Quotas`.</span></span>  
  
3.  <span data-ttu-id="8ede2-123">[テーブル] ペインから [ **Employee**]、[ **Sales 区域**]、および [ `Date` テーブル] を**ダイアグラム**ペインにドラッグします。 **Tables**</span><span class="sxs-lookup"><span data-stu-id="8ede2-123">Drag the **Employee**, **Sales Territory**, and `Date` tables from the **Tables** pane to the **Diagram** pane.</span></span>  
  
4.  <span data-ttu-id="8ede2-124">**[ダイアグラム]** ペイン内を右クリックし、 **[テーブルの追加と削除]** をクリックして、 **FactSalesQuota** テーブルを **[ダイアグラム]** ペインに追加します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-124">Add the **FactSalesQuota** table to the **Diagram** pane by right-clicking anywhere in the **Diagram** pane and selecting **Add/Remove Tables**.</span></span>  
  
     <span data-ttu-id="8ede2-125">**Employee** テーブルを介して、 **SalesTerritory** テーブルが **FactSalesQuota** テーブルに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="8ede2-125">Notice that the **SalesTerritory** table is linked to the **FactSalesQuota** table through the **Employee** table.</span></span>  
  
5.  <span data-ttu-id="8ede2-126">**FactSalesQuota** テーブルの列を確認し、このテーブル内のデータを調べます。</span><span class="sxs-lookup"><span data-stu-id="8ede2-126">Review the columns in the **FactSalesQuota** table and then explore the data in this table.</span></span>  
  
     <span data-ttu-id="8ede2-127">このテーブルのデータの詳細度が四半期単位になっていることがわかります。FactSalesQuota の最も低い詳細レベルが四半期単位ということになります。</span><span class="sxs-lookup"><span data-stu-id="8ede2-127">Notice that the grain of the data within this table is the calendar quarter, which is the lowest level of detail in the FactSalesQuota table.</span></span>  
  
6.  <span data-ttu-id="8ede2-128">データソースビューデザイナーで、 **FactSalesQuota**テーブルの**FriendlyName**プロパティをに変更 `SalesQuotas` します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-128">In Data Source View Designer, change the **FriendlyName** property of the **FactSalesQuota** table to `SalesQuotas`.</span></span>  
  
7.  <span data-ttu-id="8ede2-129">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブに切り替え、 **[キューブ構造]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ede2-129">Switch to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Cube Structure** tab.</span></span>  
  
8.  <span data-ttu-id="8ede2-130">[**メジャー** ] ペイン内の任意の場所を右クリックし、[**新しいメジャーグループ**] をクリックし `SalesQuotas` ます。次に、[**新しいメジャーグループ**] ダイアログボックス内をクリックし、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ede2-130">Right-click anywhere in the **Measures** pane, click **New Measure Group**, click `SalesQuotas` in the **New Measure Group** dialog box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="8ede2-131">`Sales Quotas`メジャーグループが [**メジャー** ] ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="8ede2-131">The `Sales Quotas` measure group appears in the **Measures** pane.</span></span> <span data-ttu-id="8ede2-132">[**ディメンション**] ペインで、 `Date` データベースディメンションに基づいて新しいキューブディメンションも定義されていることを確認し `Date` ます。</span><span class="sxs-lookup"><span data-stu-id="8ede2-132">In the **Dimensions** pane, notice that a new `Date` cube dimension is also defined, based on the `Date` database dimension.</span></span> <span data-ttu-id="8ede2-133">新しい時間キューブ ディメンションが定義されてしまうのは、Sales Quotas メジャー グループの基となる [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] FactSalesQuota **ファクト テーブルの** DateKey **列に関連付けられている時間キューブ ディメンションがどのディメンションなのかを、** に指定していないためです。</span><span class="sxs-lookup"><span data-stu-id="8ede2-133">A new time-related cube dimension is defined because [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] does not know which of the existing time-related cube dimensions to relate to the **DateKey** column in the **FactSalesQuota** fact table that underlies the Sales Quotas measure group.</span></span> <span data-ttu-id="8ede2-134">時間キューブ ディメンションの設定は、このトピックの別の実習で変更します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-134">You will change this later in another task in this topic.</span></span>  
  
9. <span data-ttu-id="8ede2-135">メジャーグループを展開し `Sales Quotas` ます。</span><span class="sxs-lookup"><span data-stu-id="8ede2-135">Expand the `Sales Quotas` measure group.</span></span>  
  
10. <span data-ttu-id="8ede2-136">**[メジャー]** ペインで、 **Sales Amount Quota**をクリックします。次に、[プロパティ] ウィンドウで、 **FormatString** プロパティの値を **Currency** に設定します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-136">In the **Measures** pane, select **Sales Amount Quota**, and then set the value for the **FormatString** property to **Currency** in the Properties window.</span></span>  
  
11. <span data-ttu-id="8ede2-137">**Sales Quota Count**メジャーを選択し、 `#,#` プロパティウィンドウで**FormatString**プロパティの値として「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-137">Select the **Sales Quotas Count** measure, and then type `#,#` as the value for the **FormatString** property in the Properties window.</span></span>  
  
12. <span data-ttu-id="8ede2-138">メジャーグループから**Calendar Quarter**メジャーを削除 `Sales Quotas` します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-138">Delete the **Calendar Quarter** measure from the `Sales Quotas` measure group.</span></span>  
  
     [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="8ede2-139">によって、Calendar Quarter メジャーの基となる列 (この列には他のメジャーも含まれている) が自動的に検出されました。</span><span class="sxs-lookup"><span data-stu-id="8ede2-139">detected the column that underlies the Calendar Quarter measure as a column that contains measures.</span></span> <span data-ttu-id="8ede2-140">しかし、このトピックの後の操作で Sales Quotas メジャー グループを Date ディメンションにリンクさせるときは、検出された列および CalendarYear 列の値を手動で割り当てます。</span><span class="sxs-lookup"><span data-stu-id="8ede2-140">However, this column and the CalendarYear column contain the values that you will use to link the Sales Quotas measure group to the Date dimension later in this topic.</span></span>  
  
13. <span data-ttu-id="8ede2-141">[**メジャー** ] ペインで、メジャーグループを右クリック `Sales Quotas` し、[**新しいメジャー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ede2-141">In the **Measures** pane, right-click the `Sales Quotas` measure group, and then click **New Measure**.</span></span>  
  
     <span data-ttu-id="8ede2-142">**[新しいメジャー]** ダイアログ ボックスが開き、メジャーの使用法が **[合計]** である場合に選択できる列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8ede2-142">The **New Measure** dialog box opens, containing the available source columns for a measure with a usage type of **Sum**.</span></span>  
  
14. <span data-ttu-id="8ede2-143">[**新しいメジャー** ] ダイアログボックスで、**使用法**の一覧から [**個別のカウント**] を選択し、[基になるテーブル] ボックスの一覧でが選択されていることを確認し `SalesQuotas` ます。次に、[基になる**列**] ボックスの一覧で [**従業員キー** ] を選択し、[ **OK**] をクリック**Source table**</span><span class="sxs-lookup"><span data-stu-id="8ede2-143">In the **New Measure** dialog box, select **Distinct count** in the **Usage** list, verify that `SalesQuotas` is selected in the **Source table** list, select **EmployeeKey** in the **Source column** list, and then click **OK**.</span></span>  
  
     <span data-ttu-id="8ede2-144">**Sales Quotas 1**という名前の新しいメジャー グループに、メジャーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="8ede2-144">Notice that the measure is created in a new measure group named **Sales Quotas 1**.</span></span> <span data-ttu-id="8ede2-145">処理速度を最大限に向上させるため、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の "個別のカウント" メジャーは専用のメジャー グループに作成されます。</span><span class="sxs-lookup"><span data-stu-id="8ede2-145">Distinct count measures in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] are created in their own measure groups to maximize processing performance.</span></span>  
  
15. <span data-ttu-id="8ede2-146">**Employee Key Distinct Count**メジャーの**Name**プロパティの値をに変更し、 `Sales Person Count` `#,#` **FormatString**プロパティの値として「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-146">Change the value for the **Name** property for the **Employee Key Distinct Count** measure to `Sales Person Count`, and then type `#,#` as the value for the **FormatString** property.</span></span>  
  
## <a name="browsing-the-measures-in-the-sales-quota-measure-group-by-date"></a><span data-ttu-id="8ede2-147">Sales Quota メジャー グループのメジャーの日付順での表示</span><span class="sxs-lookup"><span data-stu-id="8ede2-147">Browsing the Measures in the Sales Quota Measure Group by Date</span></span>  
  
1.  <span data-ttu-id="8ede2-148">**[ビルド]** メニューの **[Analysis Services Tutorial の配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ede2-148">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="8ede2-149">配置が正常に完了したら、 **Tutorial キューブのキューブ デザイナーで** [ブラウザー] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] タブをクリックし、 **[再接続]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ede2-149">When deployment has successfully completed, click the **Browser** tab in Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Reconnect** button.</span></span>  
  
3.  <span data-ttu-id="8ede2-150">Excel ショートカットをクリックし、 **[有効化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ede2-150">Click the Excel shortcut, and then click **Enable**.</span></span>  
  
4.  <span data-ttu-id="8ede2-151">ピボットテーブルのフィールドリストでメジャーグループを展開し、 `Sales Quotas` **Sales Amount Quota**メジャーを [値] 領域にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="8ede2-151">In the PivotTable Field List, expand the `Sales Quotas` measure group, and then drag the **Sales Amount Quota** measure to the Values area.</span></span>  
  
5.  <span data-ttu-id="8ede2-152">**Sales Territory** ディメンションを展開し、 **Sales Territories** ユーザー定義階層を行ラベルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="8ede2-152">Expand the **Sales Territory** dimension, and then drag the **Sales Territories** user-defined hierarchy to Row Labels.</span></span>  
  
     <span data-ttu-id="8ede2-153">次の図に示すように、Sales Territory キューブ ディメンションは、直接的にも間接的にも Fact Sales Quota テーブルには関連付けられていません。</span><span class="sxs-lookup"><span data-stu-id="8ede2-153">Notice that the Sales Territory cube dimension is not related, directly or indirectly, to the Fact Sales Quota table, as shown in the following image.</span></span>  
  
     <span data-ttu-id="8ede2-154">![販売区域キューブディメンション](../../2014/tutorials/media/l5-granularity-2.gif "Sales Territory キューブ ディメンション")</span><span class="sxs-lookup"><span data-stu-id="8ede2-154">![Sales Territory cube dimension](../../2014/tutorials/media/l5-granularity-2.gif "Sales Territory cube dimension")</span></span>  
  
     <span data-ttu-id="8ede2-155">このトピックの次の一連の手順では、Sales Territory キューブ ディメンションと Fact Sales Quota テーブルの間に参照ディメンションのリレーションシップを定義します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-155">In the next series of steps in this topic you will define a reference dimension relationship between this dimension and this fact table.</span></span>  
  
6.  <span data-ttu-id="8ede2-156">**Sales Territories** ユーザー階層を行ラベル領域から列ラベル領域に移動します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-156">Move the **Sales Territories** user hierarchy from the Rows Labels area to the Column Labels area.</span></span>  
  
7.  <span data-ttu-id="8ede2-157">ピボットテーブル フィールド リストで **Sales Territories** ユーザー定義階層を選択し、右側の下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ede2-157">In the PivotTable Field list, select the **Sales Territories** user-defined hierarchy, and then click the down arrow to the right.</span></span>  
  
     <span data-ttu-id="8ede2-158">![フィールドの一覧内の Sales Territories 階層](../../2014/tutorials/media/l5-granularity-1a.png "フィールドの一覧内の Sales Territories 階層")</span><span class="sxs-lookup"><span data-stu-id="8ede2-158">![Sales Territories hierarchy in the field list](../../2014/tutorials/media/l5-granularity-1a.png "Sales Territories hierarchy in the field list")</span></span>  
  
8.  <span data-ttu-id="8ede2-159">フィルターで [すべて選択] チェック ボックスをクリックしてすべての選択を解除してから、 **North America**だけを選択します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-159">In the filter, click the Select All checkbox to clear all the selections, and then choose just **North America**.</span></span>  
  
     <span data-ttu-id="8ede2-160">![North America を選択するためのフィルター ペイン](../../2014/tutorials/media/l5-granularity-1b.png "North America を選択するためのフィルター ペイン")</span><span class="sxs-lookup"><span data-stu-id="8ede2-160">![Filter pane for selecting North America](../../2014/tutorials/media/l5-granularity-1b.png "Filter pane for selecting North America")</span></span>  
  
9. <span data-ttu-id="8ede2-161">ピボットテーブルのフィールドリストで、を展開 `Date` します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-161">In the PivotTable Field List, expand `Date`.</span></span>  
  
10. <span data-ttu-id="8ede2-162">**Date.Fiscal Date** ユーザー階層を行ラベルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="8ede2-162">Drag the **Date.Fiscal Date** user hierarchy to Row Labels</span></span>  
  
11. <span data-ttu-id="8ede2-163">ピボットテーブルで、行ラベルの横にある下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ede2-163">On the PivotTable, click the down arrow next to Row Labels.</span></span> <span data-ttu-id="8ede2-164">**FY 2008**以外のすべての年をオフにします。</span><span class="sxs-lookup"><span data-stu-id="8ede2-164">Clear all of the years except for **FY 2008**.</span></span>  
  
     <span data-ttu-id="8ede2-165">**Month レベル**の**2007**年7月のメンバーだけが表示されます。これ**2007** **2007\*\*\*\*は、月レベルの** **2007**メンバーではなく、7月1日のうち、 **6 月 1**日のメンバーのみが31日ではなく、そのレベルの2007メンバーのみが表示されることに注意して `Date` ください。</span><span class="sxs-lookup"><span data-stu-id="8ede2-165">Notice that only the **July 2007** member of the **Month** level appears, instead of the **July, 2007**, **August, 2007**, and **September, 2007** members of **Month** level, and that only the **July 1, 2007** member of the `Date` level appears, instead of all 31 days.</span></span> <span data-ttu-id="8ede2-166">この動作が発生するのは、ファクトテーブル内のデータの粒度が quarter レベルで、ディメンションの粒度が日次レベルであるためです `Date` 。</span><span class="sxs-lookup"><span data-stu-id="8ede2-166">This behavior occurs because the grain of the data in the fact table is at the quarter level and the grain of the `Date` dimension is the daily level.</span></span> <span data-ttu-id="8ede2-167">この変更は、このトピックの別の実習で行います。</span><span class="sxs-lookup"><span data-stu-id="8ede2-167">You will change this behavior in the next task in this topic.</span></span>  
  
     <span data-ttu-id="8ede2-168">また、月単位および日単位の **Sales Amount Quota** の値が四半期のそれと同じである $13,733,000.00 になっています。</span><span class="sxs-lookup"><span data-stu-id="8ede2-168">Notice also that the **Sales Amount Quota** value for the month and day levels is the same value as for the quarter level, $13,733,000.00.</span></span> <span data-ttu-id="8ede2-169">これは、Sales Quotas メジャー グループのデータの最低詳細レベルが四半期単位になっているためです。</span><span class="sxs-lookup"><span data-stu-id="8ede2-169">This is because the lowest level of data in the Sales Quotas measure group is at the quarter level.</span></span> <span data-ttu-id="8ede2-170">この変更は、レッスン 6 で行います。</span><span class="sxs-lookup"><span data-stu-id="8ede2-170">You will change this behavior in Lesson 6.</span></span>  
  
     <span data-ttu-id="8ede2-171">次の図は、 **Sales Amount Quota**の値を示しています。</span><span class="sxs-lookup"><span data-stu-id="8ede2-171">The following image shows the values for **Sales Amount Quota**.</span></span>  
  
     <span data-ttu-id="8ede2-172">![Sales Amount Quota の値](../../2014/tutorials/media/l5-granularity-3.png "Sales Amount Quota の値")</span><span class="sxs-lookup"><span data-stu-id="8ede2-172">![Values for Sales Amount Quota](../../2014/tutorials/media/l5-granularity-3.png "Values for Sales Amount Quota")</span></span>  
  
## <a name="defining-dimension-usage-properties-for-the-sales-quotas-measure-group"></a><span data-ttu-id="8ede2-173">Sales Quotas メジャー グループにおけるディメンションの使用法の定義</span><span class="sxs-lookup"><span data-stu-id="8ede2-173">Defining Dimension Usage Properties for the Sales Quotas Measure Group</span></span>  
  
1.  <span data-ttu-id="8ede2-174">**Employee** ディメンションのディメンション デザイナーを開き、 **[データ ソース ビュー]** ペインで **[SalesTerritoryKey]** を右クリックし、 **[列から新しい属性を作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ede2-174">Open Dimension Designer for the **Employee** dimension, right-click **SalesTerritoryKey** in the **Data Source View** pane, and then click **New Attribute from Column**.</span></span>  
  
2.  <span data-ttu-id="8ede2-175">**[属性]** ペインで、 **[SalesTerritoryKey]** をクリックします。次に、[プロパティ] ウィンドウで **AttributeHierarchyVisible** プロパティを **False** に設定します。さらに、 **AttributeHierarchyOptimizedState** プロパティを **NotOptimized**に設定し、 **AttributeHierarchyOrdered** プロパティを **False**に設定します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-175">In the **Attributes** pane, select **SalesTerritoryKey**, and then set the **AttributeHierarchyVisible** property to **False** in the Properties window, set the **AttributeHierarchyOptimizedState** property to **NotOptimized**, and set the **AttributeHierarchyOrdered** property to **False**.</span></span>  
  
     <span data-ttu-id="8ede2-176">この属性は、**販売区域**ディメンションを、 `Sales Quotas` 参照ディメンションとしておよび**sales quota 1**メジャーグループにリンクするために必要です。</span><span class="sxs-lookup"><span data-stu-id="8ede2-176">This attribute is required to link the **Sales Territory** dimension to the `Sales Quotas` and **Sales Quotas 1** measure groups as a referenced dimension.</span></span>  
  
3.  <span data-ttu-id="8ede2-177">チュートリアルキューブのキューブデザイナーで、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] [ディメンションの**使用法**] タブをクリックし、[ `Sales Quotas` および**Sales quota 1** ] メジャーグループ内のディメンションの使用法を確認します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-177">In Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, click the **Dimension Usage** tab, and then review the dimension usage within the `Sales Quotas` and **Sales Quotas 1** measure groups.</span></span>  
  
     <span data-ttu-id="8ede2-178">**Employee** `Date` ディメンションと cube ディメンションが、通常のリレーションシップを通じて**sales Quotasand sales quota 1**メジャーグループにリンクされていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8ede2-178">Notice that the **Employee** and `Date` cube dimensions are linked to the **Sales Quotasand Sales Quotas 1** measure groups through regular relationships.</span></span> <span data-ttu-id="8ede2-179">また、 **Sales Territory** キューブ ディメンションはどちらのメジャー グループにもリンクしていません。</span><span class="sxs-lookup"><span data-stu-id="8ede2-179">Notice also that the **Sales Territory** cube dimension is not linked to either of these measure groups.</span></span>  
  
4.  <span data-ttu-id="8ede2-180">**販売区域**ディメンションとメジャーグループが交差する位置にあるセルをクリックし、 `Sales Quotas` 参照ボタン ([.**..**]) をクリックします。[**リレーションシップの定義**] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8ede2-180">Click the cell at the intersection of the **Sales Territory** dimension and the `Sales Quotas` measure group and then click the browse button (**...**). The **Define Relationship** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="8ede2-181">**[リレーションシップの種類の選択]** ボックスの一覧から **[参照対象]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ede2-181">In the **Select relationship type** list, select **Referenced**.</span></span>  
  
6.  <span data-ttu-id="8ede2-182">**[中間ディメンション]** ボックスの一覧から **[Employee]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-182">In the **Intermediate dimension** list, select **Employee**.</span></span>  
  
7.  <span data-ttu-id="8ede2-183">**[参照ディメンションの属性]** ボックスの一覧から **[Sales Territory Region]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-183">In the **Reference dimension attribute** list, select **Sales Territory Region.**</span></span>  
  
8.  <span data-ttu-id="8ede2-184">**[中間ディメンションの属性]** ボックスの一覧から **[Sales Territory Key]** を選択します</span><span class="sxs-lookup"><span data-stu-id="8ede2-184">In the **Intermediate dimension attribute** list, select **Sales Territory Key**.</span></span> <span data-ttu-id="8ede2-185">(Sales Territory Region 属性のキー列は、SalesTerritoryKey 列です)。</span><span class="sxs-lookup"><span data-stu-id="8ede2-185">(The key column for the Sales Territory Region attribute is the SalesTerritoryKey column.)</span></span>  
  
9. <span data-ttu-id="8ede2-186">**[具体化する]** チェック ボックスがオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-186">Verify that the **Materialize** check box is selected.</span></span>  
  
10. <span data-ttu-id="8ede2-187">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ede2-187">Click **OK**.</span></span>  
  
11. <span data-ttu-id="8ede2-188">**販売区域**ディメンションと**sales quota 1**メジャーグループが交差する位置にあるセルをクリックし、参照ボタン ([.**..**]) をクリックします。[**リレーションシップの定義**] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8ede2-188">Click the cell at the intersection of the **Sales Territory** dimension and the **Sales Quotas 1** measure group and then click the browse button (**...**). The **Define Relationship** dialog box opens.</span></span>  
  
12. <span data-ttu-id="8ede2-189">**[リレーションシップの種類の選択]** ボックスの一覧から **[参照対象]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ede2-189">In the **Select relationship type** list, select **Referenced**.</span></span>  
  
13. <span data-ttu-id="8ede2-190">**[中間ディメンション]** ボックスの一覧から **[Employee]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-190">In the **Intermediate dimension** list, select **Employee**.</span></span>  
  
14. <span data-ttu-id="8ede2-191">**[参照ディメンションの属性]** ボックスの一覧から **[Sales Territory Region]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-191">In the **Reference dimension attribute** list, select **Sales Territory Region.**</span></span>  
  
15. <span data-ttu-id="8ede2-192">**[中間ディメンションの属性]** ボックスの一覧から **[Sales Territory Key]** を選択します</span><span class="sxs-lookup"><span data-stu-id="8ede2-192">In the **Intermediate dimension attribute** list, select **Sales Territory Key**.</span></span> <span data-ttu-id="8ede2-193">(Sales Territory Region 属性のキー列は、SalesTerritoryKey 列です)。</span><span class="sxs-lookup"><span data-stu-id="8ede2-193">(The key column for the Sales Territory Region attribute is the SalesTerritoryKey column.)</span></span>  
  
16. <span data-ttu-id="8ede2-194">**[具体化する]** チェック ボックスがオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-194">Verify that the **Materialize** check box is selected.</span></span>  
  
17. <span data-ttu-id="8ede2-195">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ede2-195">Click **OK**.</span></span>  
  
18. <span data-ttu-id="8ede2-196">`Date`キューブディメンションを削除します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-196">Delete the `Date` cube dimension.</span></span>  
  
     <span data-ttu-id="8ede2-197">時間に関連する4つのキューブディメンションを用意する代わりに、メジャーグループの**Order Date**キューブディメンションを使用して、販売ノルマを測定する日付を使用し `Sales Quotas` ます。</span><span class="sxs-lookup"><span data-stu-id="8ede2-197">Instead of having four time-related cube dimensions, you will use the **Order Date** cube dimension in the `Sales Quotas` measure group as the date against which sales quotas will be dimensioned.</span></span> <span data-ttu-id="8ede2-198">また、このキューブ ディメンションはキューブ内のプライマリ日付ディメンションにもなります。</span><span class="sxs-lookup"><span data-stu-id="8ede2-198">You will also use this cube dimension as the primary date dimension in the cube.</span></span>  
  
19. <span data-ttu-id="8ede2-199">[**ディメンション**] ボックスの一覧で、 **Order Date**キューブディメンションの名前をに変更 `Date` します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-199">In the **Dimensions** list, rename the **Order Date** cube dimension to `Date`.</span></span>  
  
     <span data-ttu-id="8ede2-200">**Order Date**キューブディメンションの名前をに変更する `Date` と、ユーザーはそのロールをこのキューブのプライマリ日付ディメンションとして簡単に理解できるようになります。</span><span class="sxs-lookup"><span data-stu-id="8ede2-200">Renaming the **Order Date** cube dimension to `Date` makes it easier for users to understand its role as the primary date dimension in this cube.</span></span>  
  
20. <span data-ttu-id="8ede2-201">**...** `Sales Quotas` メジャーグループとディメンションが交差する位置にあるセルで、参照ボタン ([...]) をクリックします。 `Date`</span><span class="sxs-lookup"><span data-stu-id="8ede2-201">Click the browse button (**...**) in the cell at the intersection of the `Sales Quotas` measure group and the `Date` dimension.</span></span>  
  
21. <span data-ttu-id="8ede2-202">**[リレーションシップの定義]** ダイアログ ボックスで、 **[リレーションシップの種類の選択]** ボックスの一覧から **[標準]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-202">In the **Define Relationship** dialog box, select **Regular** in the **Select relationship type** list.</span></span>  
  
22. <span data-ttu-id="8ede2-203">**[粒度属性]** ボックスの一覧から **[Calendar Quarter]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-203">In the **Granularity attribute** list, select **Calendar Quarter**.</span></span>  
  
     <span data-ttu-id="8ede2-204">非キー属性を粒度属性として選択したため、警告が表示されます。他のすべての属性をメンバー プロパティとして指定し、直接または間接的に粒度属性に関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ede2-204">Notice that a warning appears to notify you that because you have selected a non-key attribute as the granularity attribute, you must make sure that all other attributes are directly or indirectly related to the granularity attribute by specifying them as member properties.</span></span>  
  
23. <span data-ttu-id="8ede2-205">**[リレーションシップの定義]** ダイアログ ボックスの **[リレーションシップ]** 領域で、Date キューブ ディメンションの基となるテーブルから **CalendarYear** および **CalendarQuarter** ディメンション列を、Sales Quota メジャー グループの基となるテーブルの **CalendarYear** および **CalendarQuarter** 列にそれぞれリンクし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ede2-205">In the **Relationship** area of the **Define Relationship** dialog box, link the **CalendarYear** and **CalendarQuarter** dimension columns from the table that underlies the Date cube dimension to the **CalendarYear** and **CalendarQuarter** columns in the table that underlies the Sales Quota measure group, and then click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8ede2-206">Calendar Quarter が、Sales Quotas メジャー グループの Date キューブ ディメンションの粒度属性として定義されます。しかし、Date 属性は依然として Internet Sales および Reseller Sales メジャー グループの粒度属性です。</span><span class="sxs-lookup"><span data-stu-id="8ede2-206">The Calendar Quarter is defined as the granularity attribute for the Date cube dimension in the Sales Quotas measure group, but the Date attribute continues to be the granularity attribute for the Internet Sales and Reseller Sales measure groups.</span></span>  
  
24. <span data-ttu-id="8ede2-207">前の 4 つの手順を **Sales Quotas 1** メジャー グループに対して繰り返します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-207">Repeat the previous four steps for the **Sales Quotas 1** measure group.</span></span>  
  
## <a name="defining-attribute-relationships-between-the-calendar-quarter-attribute-and-the-other-dimension-attributes-in-the-date-dimension"></a><span data-ttu-id="8ede2-208">Calendar Quarter 属性およびその他の属性間の属性リレーションシップの Date ディメンションへの定義</span><span class="sxs-lookup"><span data-stu-id="8ede2-208">Defining Attribute Relationships Between the Calendar Quarter Attribute and the Other Dimension Attributes in the Date Dimension</span></span>  
  
1.  <span data-ttu-id="8ede2-209">ディメンションの**ディメンションデザイナー**に切り替え `Date` 、[**属性リレーションシップ**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ede2-209">Switch to **Dimension Designer** for the `Date` dimension, and then click the **Attribute Relationships** tab.</span></span>  
  
     <span data-ttu-id="8ede2-210">Calendar **Year** **は calendar Quarter 属性を**介して calendar **Quarter**にリンクされていますが、会計カレンダーの属性は互いにリンクされています。**Calendar Quarter**属性にリンクされていないため、メジャーグループ内で正しく集計されません `Sales Quotas` 。</span><span class="sxs-lookup"><span data-stu-id="8ede2-210">Notice that although **Calendar Year** is linked to **Calendar Quarter** through the **Calendar Semester** attribute, the fiscal calendar attributes are linked only to one another; they are not linked to the **Calendar Quarter** attribute and therefore will not aggregate correctly in the `Sales Quotas` measure group.</span></span>  
  
2.  <span data-ttu-id="8ede2-211">ダイアグラムで、 **[Calendar Quarter]** 属性を右クリックし、 **[新しい属性リレーションシップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ede2-211">In the diagram, right-click the **Calendar Quarter** attribute and then select **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="8ede2-212">**[属性リレーションシップの作成]** ダイアログ ボックスで、 **[基になる属性]** に **[Calendar Quarter]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-212">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Calendar Quarter**.</span></span> <span data-ttu-id="8ede2-213">**[関連属性]** を **[Fiscal Quarter]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-213">Set the **Related Attribute** to **Fiscal Quarter**.</span></span>  
  
4.  <span data-ttu-id="8ede2-214">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ede2-214">Click **OK**.</span></span>  
  
     <span data-ttu-id="8ede2-215">`Date`非キー属性が粒度属性として使用されている場合にデータが集計されない可能性がある1つ以上の冗長属性リレーションシップがディメンションに含まれていることを示す警告メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8ede2-215">Notice that a warning message appears stating that the `Date` dimension contains one or more redundant attribute relationships that may prevent data from being aggregated when a non-key attribute is used as a granularity attribute.</span></span>  
  
5.  <span data-ttu-id="8ede2-216">**Month Name** 属性と **Fiscal Quarter** 属性との間の属性リレーションシップを削除します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-216">Delete the attribute relationship between the **Month Name** attribute and the **Fiscal Quarter** attribute.</span></span>  
  
6.  <span data-ttu-id="8ede2-217">**[File]\(ファイル\)** メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ede2-217">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="browsing-the-measures-in-the-sales-quota-measure-group-by-date"></a><span data-ttu-id="8ede2-218">Sales Quota メジャー グループのメジャーの日付順での表示</span><span class="sxs-lookup"><span data-stu-id="8ede2-218">Browsing the Measures in the Sales Quota Measure Group by Date</span></span>  
  
1.  <span data-ttu-id="8ede2-219">**[ビルド]** メニューの **[Analysis Services Tutorial の配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ede2-219">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="8ede2-220">配置が正常に完了したら、 **Tutorial キューブのキューブ デザイナーで** [ブラウザー] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] タブをクリックし、 **[再接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ede2-220">When deployment has successfully completed, click the **Browser** tab in Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click **Reconnect**.</span></span>  
  
3.  <span data-ttu-id="8ede2-221">Excel ショートカットをクリックし、 **[有効化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ede2-221">Click the Excel shortcut, and then click **Enable**.</span></span>  
  
4.  <span data-ttu-id="8ede2-222">**Sales Amount Quota** メジャーを値領域にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="8ede2-222">Drag the **Sales Amount Quota** measure to the Values area.</span></span>  
  
5.  <span data-ttu-id="8ede2-223">**Sales Territories** ユーザー階層を列ラベルにドラッグし、 **North America**でフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-223">Drag the **Sales Territories** user hierarchy to the Column Labels, and then filter on **North America**.</span></span>  
  
6.  <span data-ttu-id="8ede2-224">**Date.FiscalDate** ユーザー階層を行ラベルにドラッグし、ピボットテーブルの **[行ラベル]** の横の下矢印をクリックします。次に、 **[FY 2008]** 以外のすべてのチェック ボックスをオフにして、2008 年度 (会計年度) だけを表示します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-224">Drag the **Date.FiscalDate** user hierarchy to the Row Labels, and then click the down arrow next to **Row Labels** on the PivotTable, and clear all check boxes other than **FY 2008**, to display only fiscal year 2008.</span></span>  
  
7.  <span data-ttu-id="8ede2-225">[OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ede2-225">Click OK.</span></span>  
  
8.  <span data-ttu-id="8ede2-226">**FY 2008**、 **H1 FY 2008**、 **Q1 FY 2008**の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-226">Expand **FY 2008**, expand **H1 FY 2008**, and then expand **Q1 FY 2008**.</span></span>  
  
     <span data-ttu-id="8ede2-227">次の図は、Sales Quotas メジャー グループが適切に多次元化された、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブのピボットテーブルです。</span><span class="sxs-lookup"><span data-stu-id="8ede2-227">The following image shows a PivotTable for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, with the Sales Quota measure group dimensioned correctly.</span></span>  
  
     <span data-ttu-id="8ede2-228">会計四半期レベルの各メンバーが、四半期レベルと同じ値になっています。</span><span class="sxs-lookup"><span data-stu-id="8ede2-228">Notice that each member of the fiscal quarter level has the same value as the quarter level.</span></span> <span data-ttu-id="8ede2-229">たとえば、 **Q1 FY 2008** では、 **Q1 FY 2008** の分の $9,180,000.00 が、その各メンバーの値にもなっています。</span><span class="sxs-lookup"><span data-stu-id="8ede2-229">Using **Q1 FY 2008** as an example, the quota of $9,180,000.00 for **Q1 FY 2008** is also the value for each of its members.</span></span> <span data-ttu-id="8ede2-230">このように表示されるのは、ファクト テーブルの詳細度が四半期単位であり、同時に Date ディメンションの詳細レベルも四半期単位であるためです。</span><span class="sxs-lookup"><span data-stu-id="8ede2-230">This behavior occurs because the grain of the data in the fact table is at the quarter level and the grain of the Date dimension is also at the quarter level.</span></span> <span data-ttu-id="8ede2-231">レッスン 6 では、四半期ごとの販売量を各月に均等に割り振る方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-231">In Lesson 6, you will learn how to allocate the quarterly amount proportionally to each month.</span></span>  
  
     <span data-ttu-id="8ede2-232">![適切にディメンションが指定された Sales Quota メジャー グループ](../../2014/tutorials/media/l5-granularity-7.gif "適切にディメンションが指定された Sales Quota メジャー グループ")</span><span class="sxs-lookup"><span data-stu-id="8ede2-232">![Sales Quota measure group dimensioned correctly](../../2014/tutorials/media/l5-granularity-7.gif "Sales Quota measure group dimensioned correctly")</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="8ede2-233">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="8ede2-233">Next Lesson</span></span>  
 [<span data-ttu-id="8ede2-234">レッスン 6: 計算の定義</span><span class="sxs-lookup"><span data-stu-id="8ede2-234">Lesson 6: Defining Calculations</span></span>](lesson-6-defining-calculations.md)  
  
## <a name="see-also"></a><span data-ttu-id="8ede2-235">参照</span><span class="sxs-lookup"><span data-stu-id="8ede2-235">See Also</span></span>  
 <span data-ttu-id="8ede2-236">[ディメンションのリレーションシップ](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span><span class="sxs-lookup"><span data-stu-id="8ede2-236">[Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span></span>  
 <span data-ttu-id="8ede2-237">[標準リレーションシップおよび標準リレーションシッププロパティの定義](multidimensional-models/define-a-regular-relationship-and-regular-relationship-properties.md) </span><span class="sxs-lookup"><span data-stu-id="8ede2-237">[Define a Regular Relationship and Regular Relationship Properties](multidimensional-models/define-a-regular-relationship-and-regular-relationship-properties.md) </span></span>  
 [<span data-ttu-id="8ede2-238">データ ソース ビュー デザイナーでのダイアグラムの操作 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="8ede2-238">Work with Diagrams in Data Source View Designer &#40;Analysis Services&#41;</span></span>](multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md)  
  
  
