---
title: 親子階層内の親属性プロパティの定義 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2d78fa73-a13b-4e12-bbd0-43e5307f760c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1dfa4340bdc161809cf3821e5cb1f0609399e1d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642384"
---
# <a name="defining-parent-attribute-properties-in-a-parent-child-hierarchy"></a><span data-ttu-id="99da0-102">親子階層の親属性プロパティの定義</span><span class="sxs-lookup"><span data-stu-id="99da0-102">Defining Parent Attribute Properties in a Parent-Child Hierarchy</span></span>
  <span data-ttu-id="99da0-103">親子階層とは、2 つのテーブル列に基づいたディメンション内の階層です。</span><span class="sxs-lookup"><span data-stu-id="99da0-103">A parent-child hierarchy is a hierarchy in a dimension that is based on two table columns.</span></span> <span data-ttu-id="99da0-104">この 2 つのテーブル列により、ディメンションのメンバー間の階層リレーションシップが定義されます。</span><span class="sxs-lookup"><span data-stu-id="99da0-104">Together, these columns define the hierarchical relationships among the members of the dimension.</span></span> <span data-ttu-id="99da0-105">一方の列は *メンバー キー列*と呼ばれ、各ディメンション メンバーを識別します。</span><span class="sxs-lookup"><span data-stu-id="99da0-105">The first column, called the *member key column*, identifies each dimension member.</span></span> <span data-ttu-id="99da0-106">もう一方の列は *親列*と呼ばれ、各ディメンション メンバーの親を識別します。</span><span class="sxs-lookup"><span data-stu-id="99da0-106">The other column, called the *parent column*, identifies the parent of each dimension member.</span></span> <span data-ttu-id="99da0-107">親属性の **NamingTemplate** プロパティは、親子階層の各レベルの名前を指定します。 **MembersWithData** プロパティは、親メンバーのデータを表示するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="99da0-107">The **NamingTemplate** property of a parent attribute determines the name of each level in the parent-child hierarchy, and the **MembersWithData** property determines whether data for parent members should be displayed.</span></span>

 <span data-ttu-id="99da0-108">詳細については、「親子[階層](multidimensional-models/parent-child-dimension.md)」、「[親子階層の属性](multidimensional-models/parent-child-dimension-attributes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99da0-108">For more information, see [Parent-Child Hierarchy](multidimensional-models/parent-child-dimension.md), [Attributes in Parent-Child Hierarchies](multidimensional-models/parent-child-dimension-attributes.md)</span></span>

> [!NOTE]
>  <span data-ttu-id="99da0-109">ディメンション ウィザードを使用してディメンションを作成すると、親子リレーションシップを持つテーブルがウィザードによって認識され、親子階層が自動的に定義されます。</span><span class="sxs-lookup"><span data-stu-id="99da0-109">When you use the Dimension Wizard to create a dimension, the wizard recognizes the tables that have parent-child relationships and automatically defines the parent-child hierarchy for you.</span></span>

 <span data-ttu-id="99da0-110">このトピックの実習では、名前付けテンプレートを使用して、 **Employee** ディメンションの親子階層の各レベルに名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="99da0-110">In the tasks in this topic, you will create a naming template that defines the name for each level in the parent-child hierarchy in the **Employee** dimension.</span></span> <span data-ttu-id="99da0-111">次に、すべての親データが非表示になるように親属性を構成します。これにより、リーフレベルのメンバーの売上高のみが表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="99da0-111">You will then configure the parent attribute to hide all parent data, so that only the sales for leaf-level members are displayed.</span></span>

## <a name="browsing-the-employee-dimension"></a><span data-ttu-id="99da0-112">Employee ディメンションの表示</span><span class="sxs-lookup"><span data-stu-id="99da0-112">Browsing the Employee Dimension</span></span>

1.  <span data-ttu-id="99da0-113">ソリューション エクスプローラーで、 **[ディメンション]** フォルダーの **Employee.dim** をダブルクリックし、Employee ディメンションのディメンション デザイナーを開きます。</span><span class="sxs-lookup"><span data-stu-id="99da0-113">In Solution Explorer, double-click **Employee.dim** in the **Dimensions** folder to open Dimension Designer for the Employee dimension.</span></span>

2.  <span data-ttu-id="99da0-114">**[ブラウザー]** タブをクリックし、 **[階層]** ボックスの一覧で **[Employees]** が選択されていることを確認します。次に、 **[All Employees]** メンバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="99da0-114">Click the **Browser** tab, verify that **Employees** is selected in the **Hierarchy** list, and then expand the **All Employees** member.</span></span>

     <span data-ttu-id="99da0-115">この親子階層では、 **Ken J. Sánchez** が最上位の管理者です。</span><span class="sxs-lookup"><span data-stu-id="99da0-115">Notice that **Ken J. Sánchez** is the top-level manager in this parent-child hierarchy.</span></span>

3.  <span data-ttu-id="99da0-116">**[Ken J. Sánchez]** メンバーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="99da0-116">Select the **Ken J. Sánchez** member.</span></span>

     <span data-ttu-id="99da0-117">このメンバーのレベル名は **Level 02**です。</span><span class="sxs-lookup"><span data-stu-id="99da0-117">Notice that the level name for this member is **Level 02**.</span></span> <span data-ttu-id="99da0-118">(レベル名は、 **[現在のレベル:]** の後、つまり、 **[All Employees]** メンバーのすぐ上に表示されます)。次の実習では、さらにわかりやすい名前を各レベルに定義します。</span><span class="sxs-lookup"><span data-stu-id="99da0-118">(The level name appears after **Current level:** immediately above the **All Employees** member.) In the next task, you will define more descriptive names for each level.</span></span>

4.  <span data-ttu-id="99da0-119">**[Ken J. Sánchez]** を展開し、この管理者の監督下にある従業員の名前を表示します。次に、 **[Brian S. Welcker]** をクリックし、このレベルの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="99da0-119">Expand **Ken J. Sánchez** to view the names of the employees who report to this manager, and then select **Brian S. Welcker** to view the name of this level.</span></span>

     <span data-ttu-id="99da0-120">このメンバーのレベル名は **Level 03**です。</span><span class="sxs-lookup"><span data-stu-id="99da0-120">Notice that the level name for this member is **Level 03**.</span></span>

5.  <span data-ttu-id="99da0-121">ソリューション エクスプローラーで、 **[キューブ]** フォルダー内の **Analysis Services Tutorial.cube** をダブルクリックして、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブのキューブ デザイナーを開きます。</span><span class="sxs-lookup"><span data-stu-id="99da0-121">In Solution Explorer, double-click **Analysis Services Tutorial.cube** in the **Cubes** folder to open Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span>

6.  <span data-ttu-id="99da0-122">**[ブラウザー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="99da0-122">Click the **Browser** tab.</span></span>

7.  <span data-ttu-id="99da0-123">Excel アイコンをクリックし、接続の有効化を確認するメッセージが表示されたら **[有効化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99da0-123">Click the Excel icon, and then click **Enable** when prompted to enable connections.</span></span>

8.  <span data-ttu-id="99da0-124">ピボットテーブルのフィールド リストで **Reseller Sales**を展開します。</span><span class="sxs-lookup"><span data-stu-id="99da0-124">In the PivotTable Field List, expand **Reseller Sales**.</span></span> <span data-ttu-id="99da0-125">**Reseller Sales-Sales Amount** を値領域にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="99da0-125">Drag **Reseller Sales-Sales Amount** to the Values area.</span></span>

9. <span data-ttu-id="99da0-126">ピボットテーブルのフィールド リストで **Employee**を展開し、 **Employees** 階層を **行** 領域にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="99da0-126">In the PivotTable Field List, expand **Employee**, and then drag the **Employees** hierarchy to the **Rows** area.</span></span>

     <span data-ttu-id="99da0-127">Employees 階層のすべてのメンバーがピボットテーブル レポートの列 A に追加されます。</span><span class="sxs-lookup"><span data-stu-id="99da0-127">All the members of the Employees hierarchy are added to column A of the PivotTable report.</span></span>

     <span data-ttu-id="99da0-128">次の図は、展開された Employees 階層を示しています。</span><span class="sxs-lookup"><span data-stu-id="99da0-128">The following image shows the Employees hierarchy expanded.</span></span>

10. <span data-ttu-id="99da0-129">![Employees 階層を示すピボットテーブル](../../2014/tutorials/media/l4-employee-1.gif "Employees 階層を示すピボットテーブル")</span><span class="sxs-lookup"><span data-stu-id="99da0-129">![PivotTable showing Employees hierarchy](../../2014/tutorials/media/l4-employee-1.gif "PivotTable showing Employees hierarchy")</span></span>

     <span data-ttu-id="99da0-130">Level 03 の各管理者の売上は Level 04 にも表示されます。</span><span class="sxs-lookup"><span data-stu-id="99da0-130">Notice that the sales made by each manager in Level 03 are also displayed in Level 04.</span></span> <span data-ttu-id="99da0-131">各管理者は、他の管理者の部下でもあるからです。</span><span class="sxs-lookup"><span data-stu-id="99da0-131">This is because each manager is also an employee of another manager.</span></span> <span data-ttu-id="99da0-132">次の実習では、これらの売上高を非表示にします。</span><span class="sxs-lookup"><span data-stu-id="99da0-132">In the next task, you will hide these sale amounts.</span></span>

## <a name="modifying-parent-attribute-properties-in-the-employee-dimension"></a><span data-ttu-id="99da0-133">Employee ディメンションの親属性プロパティの変更</span><span class="sxs-lookup"><span data-stu-id="99da0-133">Modifying Parent Attribute Properties in the Employee Dimension</span></span>

1.  <span data-ttu-id="99da0-134">**Employee** ディメンションのディメンション デザイナーに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="99da0-134">Switch to Dimension Designer for the **Employee** dimension.</span></span>

2.  <span data-ttu-id="99da0-135">**[ディメンション構造]** タブをクリックし、 **[属性]** ペインで **[Employees]** 属性階層をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99da0-135">Click the **Dimension Structure** tab, and then select the **Employees** attribute hierarchy in the **Attributes** pane.</span></span>

     <span data-ttu-id="99da0-136">この属性だけ、他とは異なるアイコンが表示されています。</span><span class="sxs-lookup"><span data-stu-id="99da0-136">Notice the unique icon for this attribute.</span></span> <span data-ttu-id="99da0-137">このアイコンは、Employees 属性が親子階層の親キーであることを示しています。</span><span class="sxs-lookup"><span data-stu-id="99da0-137">This icon signifies that the attribute is the parent key in a parent-child hierarchy.</span></span> <span data-ttu-id="99da0-138">また、[プロパティ] ウィンドウを見ると、この属性の **Usage** プロパティが **Parent**として定義されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="99da0-138">Notice also, in the Properties window, that the **Usage** property for the attribute is defined as **Parent**.</span></span> <span data-ttu-id="99da0-139">このプロパティは、ディメンションを設計した際にディメンション ウィザードによって設定されたものです。</span><span class="sxs-lookup"><span data-stu-id="99da0-139">This property was set by the Dimension Wizard when the dimension was designed.</span></span> <span data-ttu-id="99da0-140">親子リレーションシップは、ウィザードによって自動的に検出されています。</span><span class="sxs-lookup"><span data-stu-id="99da0-140">The wizard automatically detected the parent-child relationship.</span></span>

3.  <span data-ttu-id="99da0-141">[プロパティ] ウィンドウで、**NamingTemplate**プロパティ セルの参照ボタン ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99da0-141">In the Properties window, click the ellipsis button (**...**) in the **NamingTemplate** property cell.</span></span>

     <span data-ttu-id="99da0-142">**[レベル名前付けテンプレート]** ダイアログ ボックスでレベル名前付けテンプレートを定義します。このテンプレートは、キューブを表示するときに表示される親子階層のレベル名を決定します。</span><span class="sxs-lookup"><span data-stu-id="99da0-142">In the **Level Naming Template** dialog box, you define the level naming template that determines the level names in the parent-child hierarchy that are displayed to users as they browse cubes.</span></span>

4.  <span data-ttu-id="99da0-143">2行目の行の [ **\*** **名前**] 列に「 \*\*Employee Level \* \*\* 」と入力し、3番目の行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99da0-143">In the second row, the **\*** row, type **Employee Level \*** in the **Name** column, and then click the third row.</span></span>

     <span data-ttu-id="99da0-144">**[結果]** の下を確認すると、各レベルには、"Employee Level" の後ろに連番を追加した名前が付いています。</span><span class="sxs-lookup"><span data-stu-id="99da0-144">Notice under **Result** that each level will now be named "Employee Level" followed by a sequentially increasing number.</span></span>

     <span data-ttu-id="99da0-145">次の図は、 **[レベル名前付けテンプレート]** ダイアログ ボックスで定義を変更するようすを示しています。</span><span class="sxs-lookup"><span data-stu-id="99da0-145">The following image shows the changes in the **Level Naming Template** dialog box.</span></span>

     <span data-ttu-id="99da0-146">![[レベル名前付けテンプレート] ダイアログボックス](../../2014/tutorials/media/l4-namingtemplate.gif "[レベル名前付けテンプレート] ダイアログ ボックス")</span><span class="sxs-lookup"><span data-stu-id="99da0-146">![Level Naming Template dialog box](../../2014/tutorials/media/l4-namingtemplate.gif "Level Naming Template dialog box")</span></span>

5.  <span data-ttu-id="99da0-147">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99da0-147">Click **OK**.</span></span>

6.  <span data-ttu-id="99da0-148">**Employees** 属性の[プロパティ] ウィンドウの **MembersWithData** プロパティ セルで、 **[NonLeafDataHidden]** を選択して **Employees** 属性の値を変更します。</span><span class="sxs-lookup"><span data-stu-id="99da0-148">In the Properties window for the **Employees** attribute, in the **MembersWithData** property cell, select **NonLeafDataHidden** to change this value for the **Employees** attribute.</span></span>

     <span data-ttu-id="99da0-149">この操作により、親子階層内の非リーフレベル メンバーに関連付けられているデータが非表示になります。</span><span class="sxs-lookup"><span data-stu-id="99da0-149">This will cause data that is related to non-leaf level members in the parent-child hierarchy to be hidden.</span></span>

## <a name="browsing-the-employee-dimension-with-the-modified-attributes"></a><span data-ttu-id="99da0-150">属性を変更した Employee ディメンションの表示</span><span class="sxs-lookup"><span data-stu-id="99da0-150">Browsing the Employee Dimension with the Modified Attributes</span></span>

1.  <span data-ttu-id="99da0-151">**で、** [ビルド] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]メニューの **[Analysis Services Tutorial の配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99da0-151">On the **Build** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>

2.  <span data-ttu-id="99da0-152">チュートリアルが正常に配置されたら、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブのキューブ デザイナーに切り替え、 **[ブラウザー]** タブのツール バーで **[再接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99da0-152">When deployment has successfully completed, switch to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click **Reconnect** on the toolbar of the **Browser** tab.</span></span>

3.  <span data-ttu-id="99da0-153">Excel アイコンをクリックし、 **[有効化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99da0-153">Click the Excel icon, and then click **Enable**.</span></span>

4.  <span data-ttu-id="99da0-154">**Reseller Sales-Sales Amount** を値領域にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="99da0-154">Drag **Reseller Sales-Sales Amount** to the Values area.</span></span>

5.  <span data-ttu-id="99da0-155">**Employees** 階層を行ラベル領域にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="99da0-155">Drag the **Employees** hierarchy to the Row Labels area.</span></span>

     <span data-ttu-id="99da0-156">次の図は、Employees 階層を変更したようすを示しています。</span><span class="sxs-lookup"><span data-stu-id="99da0-156">The following image shows the changes that you made to the Employees hierarchy.</span></span> <span data-ttu-id="99da0-157">Stephen Y. Jiang は、本人自身の部下として表示されなくなっています。</span><span class="sxs-lookup"><span data-stu-id="99da0-157">Notice that Stephen Y. Jiang no longer appears as an employee of himself.</span></span>

     <span data-ttu-id="99da0-158">![変更した Employees 階層](../../2014/tutorials/media/l4-employee-2.png "変更した Employees 階層")</span><span class="sxs-lookup"><span data-stu-id="99da0-158">![Modified Employees hierarchy](../../2014/tutorials/media/l4-employee-2.png "Modified Employees hierarchy")</span></span>

## <a name="next-task-in-lesson"></a><span data-ttu-id="99da0-159">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="99da0-159">Next Task in Lesson</span></span>
 [<span data-ttu-id="99da0-160">属性メンバーの自動的なグループ化</span><span class="sxs-lookup"><span data-stu-id="99da0-160">Automatically Grouping Attribute Members</span></span>](lesson-4-3-automatically-grouping-attribute-members.md)

## <a name="see-also"></a><span data-ttu-id="99da0-161">参照</span><span class="sxs-lookup"><span data-stu-id="99da0-161">See Also</span></span>
 <span data-ttu-id="99da0-162">親子階層の親子[階層](multidimensional-models/parent-child-dimension.md)[属性](multidimensional-models/parent-child-dimension-attributes.md)</span><span class="sxs-lookup"><span data-stu-id="99da0-162">[Parent-Child Hierarchy](multidimensional-models/parent-child-dimension.md) [Attributes in Parent-Child Hierarchies](multidimensional-models/parent-child-dimension-attributes.md)</span></span>


