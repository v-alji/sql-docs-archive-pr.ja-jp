---
title: ユーザー定義階層の属性間の属性リレーションシップの指定 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 456c2a47-d395-45f9-9efa-89f3fa2ac621
author: minewiskan
ms.author: owend
ms.openlocfilehash: dc2fa03f72039aedd16c82b86ce0dd41b8f59702
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632815"
---
# <a name="specifying-attribute-relationships-between-attributes-in-a-user-defined-hierarchy"></a><span data-ttu-id="ad892-102">ユーザー定義階層の属性間での属性リレーションシップの指定</span><span class="sxs-lookup"><span data-stu-id="ad892-102">Specifying Attribute Relationships Between Attributes in a User-Defined Hierarchy</span></span>
  <span data-ttu-id="ad892-103">このチュートリアルで既に学習したように、ユーザー階層に属性階層を配置し、キューブ内を移動するためのパスを作ることができます。</span><span class="sxs-lookup"><span data-stu-id="ad892-103">As you have already learned in this tutorial, you can organize attribute hierarchies into levels within user hierarchies to provide navigation paths for users in a cube.</span></span> <span data-ttu-id="ad892-104">ユーザー階層は、市区町村、州、国などの一般階層を表せるほか、従業員名、役職、部署名のように操作パスのみを表すこともできます。</span><span class="sxs-lookup"><span data-stu-id="ad892-104">A user hierarchy can represent a natural hierarchy, such as city, state, and country, or can just represent a navigation path, such as employee name, title, and department name.</span></span> <span data-ttu-id="ad892-105">階層内を移動するユーザーにとっては、どちらのユーザー階層も変わりません。</span><span class="sxs-lookup"><span data-stu-id="ad892-105">To the user navigating a hierarchy, these two types of user hierarchies are the same.</span></span>  
  
 <span data-ttu-id="ad892-106">一般階層で、各層を構成する属性間に属性リレーションシップが定義されている場合、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] は、1 つの階層の集計結果を使用して、その階層に関連付けられている別の階層の結果を取得することができます。</span><span class="sxs-lookup"><span data-stu-id="ad892-106">With a natural hierarchy, if you define attribute relationships between the attributes that make up the levels, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] can use an aggregation from one attribute to obtain the results from a related attribute.</span></span> <span data-ttu-id="ad892-107">属性間にリレーションシップを定義していない場合は、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] によってキー属性からすべての非キー属性が集計されます。</span><span class="sxs-lookup"><span data-stu-id="ad892-107">If there are no defined relationships between attributes, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] will aggregate all non-key attributes from the key attribute.</span></span> <span data-ttu-id="ad892-108">そのため、基になるデータで属性リレーションシップがサポートされる場合、属性間の属性リレーションシップを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad892-108">Therefore, if the underlying data supports it, you should define attribute relationships between attributes.</span></span> <span data-ttu-id="ad892-109">属性リレーションシップを定義すると、ディメンション、パーティション、およびクエリの処理パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="ad892-109">Defining attribute relationships improves dimension, partition, and query processing performance.</span></span> <span data-ttu-id="ad892-110">詳細については、「 [属性リレーションシップの定義](multidimensional-models/attribute-relationships-define.md) 」および「 [属性リレーションシップ](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad892-110">For more information, see [Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md) and [Attribute Relationships](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).</span></span>  
  
 <span data-ttu-id="ad892-111">属性リレーションシップを定義する際、リレーションシップを変更できるようにするのか、または固定するのかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="ad892-111">When you define attribute relationships, you can specify that the relationship is either flexible or rigid.</span></span> <span data-ttu-id="ad892-112">固定のリレーションシップを定義した場合、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] によってディメンションの更新時の集計が保持されます。</span><span class="sxs-lookup"><span data-stu-id="ad892-112">If you define a relationship as rigid, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] retains aggregations when the dimension is updated.</span></span> <span data-ttu-id="ad892-113">固定のリレーションシップを変更すると、ディメンションが完全に処理されない限り、処理の途中で [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] によってエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="ad892-113">If a relationship that is defined as rigid actually changes, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] generates an error during processing unless the dimension is fully processed.</span></span> <span data-ttu-id="ad892-114">適切なリレーションシップとリレーションシップのプロパティを指定すると、クエリ パフォーマンスと処理パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="ad892-114">Specifying the appropriate relationships and relationship properties increases query and processing performance.</span></span> <span data-ttu-id="ad892-115">詳細については、「 [属性リレーションシップの定義](multidimensional-models/attribute-relationships-define.md)」および「 [ユーザー階層プロパティ](multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad892-115">For more information, see [Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md), and [User Hierarchy Properties](multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md).</span></span>  
  
 <span data-ttu-id="ad892-116">このトピックの実習では、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial プロジェクトの一般ユーザー階層の属性に属性リレーションシップを定義します。</span><span class="sxs-lookup"><span data-stu-id="ad892-116">In the tasks in this topic, you define attribute relationships for the attributes in the natural user hierarchies in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project.</span></span> <span data-ttu-id="ad892-117">対象となるのは、 **Customer** ディメンションの **Customer Geography**階層、 **Sales Territory** ディメンションの **Sales Territory** 階層、 **Product** ディメンションの **Product Model Lines** 階層、 **Date** ディメンションの **Fiscal Date** 階層と **Calendar Date** 階層です。</span><span class="sxs-lookup"><span data-stu-id="ad892-117">These include the **Customer Geography** hierarchy in the **Custome**r dimension, the **Sales Territory** hierarchy in the **Sales Territory** dimension, the **Product Model** Lines hierarchy in the **Product** dimension, and the **Fiscal Date** and **Calendar Date** hierarchies in the **Date** dimension.</span></span> <span data-ttu-id="ad892-118">これらのユーザー階層は、すべて一般階層です。</span><span class="sxs-lookup"><span data-stu-id="ad892-118">These user hierarchies are all natural hierarchies.</span></span>  
  
## <a name="defining-attribute-relationships-for-attributes-in-the-customer-geography-hierarchy"></a><span data-ttu-id="ad892-119">Customer Geography 階層の属性に対する属性リレーションシップの定義</span><span class="sxs-lookup"><span data-stu-id="ad892-119">Defining Attribute Relationships for Attributes in the Customer Geography Hierarchy</span></span>  
  
1.  <span data-ttu-id="ad892-120">Customer ディメンションのディメンション デザイナーに切り替え、 **[ディメンション構造]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-120">Switch to Dimension Designer for the Customer dimension, and then click the **Dimension Structure** tab.</span></span>  
  
     <span data-ttu-id="ad892-121">**[階層]** ペインを見ると、 **Customer Geography** ユーザー定義階層に複数のレベルがあることがわかります。</span><span class="sxs-lookup"><span data-stu-id="ad892-121">In the **Hierarchies** pane, notice the levels in the **Customer Geography** user-defined hierarchy.</span></span> <span data-ttu-id="ad892-122">レベル間または属性間のリレーションシップが定義されていないため、この階層は、現時点ではまだユーザー用ドリルダウン パスにすぎません。</span><span class="sxs-lookup"><span data-stu-id="ad892-122">This hierarchy is currently just a drill-down path for users, as no relationship between levels or attributes have been defined.</span></span>  
  
2.  <span data-ttu-id="ad892-123">**[属性リレーションシップ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-123">Click the **Attribute Relationships** tab.</span></span>  
  
     <span data-ttu-id="ad892-124">**Geography** テーブルの非キー属性を **Geography** テーブルのキー属性にリンクする 4 つの属性リレーションシップがあります。</span><span class="sxs-lookup"><span data-stu-id="ad892-124">Notice the four attribute relationships that link the non-key attributes from the **Geography** table to the key attribute from the **Geography** table.</span></span> <span data-ttu-id="ad892-125">**Geography** 属性が **Full Name** 属性に関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="ad892-125">The **Geography** attribute is related to the **Full Name** attribute.</span></span> <span data-ttu-id="ad892-126">**Geography** 属性を介して、 **Postal Code** 属性が **Full Name** 属性に間接的にリンクしています。 **Postal Code** 属性は **Geography** 属性にリンクし、 **Geography** 属性は **Full Name** 属性にリンクしているためです。</span><span class="sxs-lookup"><span data-stu-id="ad892-126">The **Postal Code** attribute is indirectly linked to the **Full Name** attribute through the **Geography** attribute, because the **Postal Code** is linked to the **Geography** attribute and the **Geography** attribute is linked to the **Full Name** attribute.</span></span> <span data-ttu-id="ad892-127">次に、属性リレーションシップを変更して、 **Geography** 属性を使用できないようにします。</span><span class="sxs-lookup"><span data-stu-id="ad892-127">Next, we will change the attribute relationships so that they do not use the **Geography** attribute.</span></span>  
  
3.  <span data-ttu-id="ad892-128">ダイアグラムで、 **[Full Name]** 属性を右クリックし、 **[新しい属性リレーションシップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-128">In the diagram, right-click the **Full Name** attribute and then select **New Attribute Relationship**.</span></span>  
  
4.  <span data-ttu-id="ad892-129">**[属性リレーションシップの作成]** ダイアログ ボックスで、 **[基になる属性]** を **[Full Name]** にします。</span><span class="sxs-lookup"><span data-stu-id="ad892-129">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Full Name**.</span></span> <span data-ttu-id="ad892-130">**[関連属性]** を **[Postal Code]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-130">Set the **Related Attribute** to **Postal Code**.</span></span> <span data-ttu-id="ad892-131">時間が経過するとメンバー間のリレーションシップが変化する可能性があるため、 **[リレーションシップの種類]** ボックスの一覧で、リレーションシップの種類の設定は **[可変]** のままにします。</span><span class="sxs-lookup"><span data-stu-id="ad892-131">In the **Relationship type** list, leave the relationship type set to **Flexible** because relationships between the members might change over time.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="ad892-132">リレーションシップが重複しているため、ダイアグラムに警告アイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ad892-132">A warning icon appears in the diagram because the relationship is redundant.</span></span> <span data-ttu-id="ad892-133">リレーションシップの**完全名**  ->  **Geography** ->  **郵便**番号は既に存在しています。また、リレーションシップの**完全な名前**の  ->  **郵便**番号を作成しました。</span><span class="sxs-lookup"><span data-stu-id="ad892-133">The relationship **Full Name** -> **Geography**-> **Postal Code** already existed, and you just created the relationship **Full Name** -> **Postal Code**.</span></span> <span data-ttu-id="ad892-134">リレーションシップの**地理**郵便番号は重複しているので、 ->  **Postal Code**削除します。</span><span class="sxs-lookup"><span data-stu-id="ad892-134">The relationship **Geography**-> **Postal Code** is now redundant, so we will remove it.</span></span>  
  
6.  <span data-ttu-id="ad892-135">**[属性リレーションシップ]** ペインで、 **[Geography**-> **Postal Code]** を右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-135">In the **Attribute Relationships** pane, right-click **Geography**-> **Postal Code** and then click **Delete**.</span></span>  
  
7.  <span data-ttu-id="ad892-136">**[オブジェクトの削除]** ダイアログ ボックスが表示されたら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-136">When the **Delete Objects** dialog box appears, click **OK**.</span></span>  
  
8.  <span data-ttu-id="ad892-137">ダイアグラムで、 **[Postal Code]** 属性を右クリックし、 **[新しい属性リレーションシップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-137">In the diagram, right-click the **Postal Code** attribute and then select **New Attribute Relationship**.</span></span>  
  
9. <span data-ttu-id="ad892-138">**[属性リレーションシップの作成]** ダイアログ ボックスで、 **[基になる属性]** に **[Postal Code]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-138">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Postal Code**.</span></span> <span data-ttu-id="ad892-139">**[関連属性]** を **[City]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-139">Set the **Related Attribute** to **City**.</span></span> <span data-ttu-id="ad892-140">**[リレーションシップの種類]** ボックスの一覧で、リレーションシップの種類の設定を **[可変]** のままにします。</span><span class="sxs-lookup"><span data-stu-id="ad892-140">In the **Relationship type** list, leave the relationship type set to **Flexible**.</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="ad892-141">リレーションシップ**Geography** ->  **City**が冗長になり、削除されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ad892-141">The relationship **Geography**-> **City** is now redundant so we will delete it.</span></span>  
  
11. <span data-ttu-id="ad892-142">[属性リレーションシップ] ペインで、[ **Geography**City] を右クリックし、 ->  **City** [**削除**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-142">In the Attribute Relationships pane, right-click **Geography**-> **City** and then click **Delete**.</span></span>  
  
12. <span data-ttu-id="ad892-143">**[オブジェクトの削除]** ダイアログ ボックスが表示されたら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-143">When the **Delete Objects** dialog box appears, click **OK**.</span></span>  
  
13. <span data-ttu-id="ad892-144">ダイアグラムで、 **[City]** 属性を右クリックし、 **[新しい属性リレーションシップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-144">In the diagram, right-click the **City** attribute and then select **New Attribute Relationship**.</span></span>  
  
14. <span data-ttu-id="ad892-145">**[属性リレーションシップの作成]** ダイアログ ボックスで、 **[基になる属性]** に **[City]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-145">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **City**.</span></span> <span data-ttu-id="ad892-146">**[関連属性]** を **[State-Province]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-146">Set the **Related Attribute** to **State-Province**.</span></span> <span data-ttu-id="ad892-147">市区町村と都道府県のリレーションシップは時間が経過しても変化しないので、 **[リレーションシップの種類]** ボックスの一覧で、リレーションシップの種類を **[固定]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-147">In the **Relationship type** list, set the relationship type to **Rigid** because the relationship between a city and a state will not change over time.</span></span>  
  
15. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
16. <span data-ttu-id="ad892-148">**[Geography]** と **[State-Province]** の間の矢印を右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-148">Right-click the arrow between **Geography** and **State-Province** and then click **Delete**.</span></span>  
  
17. <span data-ttu-id="ad892-149">**[オブジェクトの削除]** ダイアログ ボックスが表示されたら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-149">When the **Delete Objects** dialog box appears, click **OK**.</span></span>  
  
18. <span data-ttu-id="ad892-150">ダイアグラムで、 **[State-Province]** 属性を右クリックし、 **[新しい属性リレーションシップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-150">In the diagram, right-click the **State-Province** attribute and then select **New Attribute Relationship**.</span></span>  
  
19. <span data-ttu-id="ad892-151">**[属性リレーションシップの作成]** ダイアログ ボックスで、 **[基になる属性]** に **[State-Province]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-151">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **State-Province**.</span></span> <span data-ttu-id="ad892-152">**[関連属性]** を **[Country-Region]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-152">Set the **Related Attribute** to **Country-Region**.</span></span> <span data-ttu-id="ad892-153">都道府県と国/地域のリレーションシップは時間が経過しても変化しないので、 **[リレーションシップの種類]** ボックスの一覧で、リレーションシップの種類を **[固定]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-153">In the **Relationship type** list, set the relationship type to **Rigid** because the relationship between a state-province and a country-region will not change over time.</span></span>  
  
20. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
21. <span data-ttu-id="ad892-154">[属性リレーションシップ] ペインで、[ **Geography** ->  **Country-Region** ] を右クリックし、[**削除**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-154">In the Attribute Relationships pane, right-click **Geography**-> **Country-Region** and then click **Delete**.</span></span>  
  
22. <span data-ttu-id="ad892-155">**[オブジェクトの削除]** ダイアログ ボックスが表示されたら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-155">When the **Delete Objects** dialog box appears, click **OK**.</span></span>  
  
23. <span data-ttu-id="ad892-156">**[ディメンション構造]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-156">Click the **Dimension Structure** tab.</span></span>  
  
     <span data-ttu-id="ad892-157">**Geography** と他の属性との最後の属性リレーションシップを削除すると、その **Geography** 自体が削除されます。</span><span class="sxs-lookup"><span data-stu-id="ad892-157">Notice that when you delete the last attribute relationship between **Geography** and other attributes, that **Geography** itself is deleted.</span></span> <span data-ttu-id="ad892-158">その後は属性が使用されなくなるためです。</span><span class="sxs-lookup"><span data-stu-id="ad892-158">This is because the attribute is no longer used.</span></span>  
  
24. <span data-ttu-id="ad892-159">[File]\(ファイル\) メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-159">On the File menu, click **Save All**.</span></span>  
  
## <a name="defining-attribute-relationships-for-attributes-in-the-sales-territory-hierarchy"></a><span data-ttu-id="ad892-160">Sales Territory 階層の属性に対する属性リレーションシップの定義</span><span class="sxs-lookup"><span data-stu-id="ad892-160">Defining Attribute Relationships for Attributes in the Sales Territory Hierarchy</span></span>  
  
1.  <span data-ttu-id="ad892-161">**Sales Territory** ディメンションのディメンション デザイナーを開き、 **[属性リレーションシップ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-161">Open Dimension Designer for the **Sales Territory** dimension, and then click the **Attribute Relationships** tab.</span></span>  
  
2.  <span data-ttu-id="ad892-162">ダイアグラムで、 **[Sales Territory Country]** 属性を右クリックし、 **[新しい属性リレーションシップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-162">In the diagram, right-click the **Sales Territory Country** attribute and then select **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="ad892-163">**[属性リレーションシップの作成]** ダイアログ ボックスで、 **[基になる属性]** に **[Sales Territory Country]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-163">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Sales Territory Country**.</span></span> <span data-ttu-id="ad892-164">**[関連属性]** を **[Sales Territory Group]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-164">Set the **Related Attribute** to **Sales Territory Group**.</span></span> <span data-ttu-id="ad892-165">**[リレーションシップの種類]** ボックスの一覧で、リレーションシップの種類の設定を **[可変]** のままにします。</span><span class="sxs-lookup"><span data-stu-id="ad892-165">In the **Relationship type** list, leave the relationship type set to **Flexible**.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="ad892-166">**Sales Territory Group** が **Sales Territory Country**にリンクされ、 **Sales Territory Country** が **Sales Territory Region**にリンクされました。</span><span class="sxs-lookup"><span data-stu-id="ad892-166">**Sales Territory Group** is now linked to **Sales Territory Country**, and **Sales Territory Country** is now linked to **Sales Territory Region**.</span></span> <span data-ttu-id="ad892-167">国内の販売グループや販売区域は時間と共に変わることがあり、各国の販売グループの編成も時間と共に変わる可能性があるので、これらのリレーションシップの **RelationshipType** プロパティは **Flexible** に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-167">The **RelationshipType** property for each of these relationships is set to **Flexible** because the groupings of regions within a country might change over time and because the groupings of countries into groups might change over time.</span></span>  
  
## <a name="defining-attribute-relationships-for-attributes-in-the-product-model-lines-hierarchy"></a><span data-ttu-id="ad892-168">Product Model Lines 階層の属性に対する属性リレーションシップの定義</span><span class="sxs-lookup"><span data-stu-id="ad892-168">Defining Attribute Relationships for Attributes in the Product Model Lines Hierarchy</span></span>  
  
1.  <span data-ttu-id="ad892-169">**Product** ディメンションのディメンション デザイナーを開き、 **[属性リレーションシップ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-169">Open Dimension Designer for the **Product** dimension, and then click the **Attribute Relationships** tab.</span></span>  
  
2.  <span data-ttu-id="ad892-170">ダイアグラムで、 **[Model Name]** 属性を右クリックし、 **[新しい属性リレーションシップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-170">In the diagram, right-click the **Model Name** attribute and then select **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="ad892-171">**[属性リレーションシップの作成]** ダイアログ ボックスで、 **[基になる属性]** に **[Model Name]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-171">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Model Name**.</span></span> <span data-ttu-id="ad892-172">**[関連属性]** を **[Product Line]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-172">Set the **Related Attribute** to **Product Line**.</span></span> <span data-ttu-id="ad892-173">**[リレーションシップの種類]** ボックスの一覧で、リレーションシップの種類の設定を **[可変]** のままにします。</span><span class="sxs-lookup"><span data-stu-id="ad892-173">In the **Relationship type** list, leave the relationship type set to **Flexible**.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="defining-attribute-relationships-for-attributes-in-the-fiscal-date-hierarchy"></a><span data-ttu-id="ad892-174">Fiscal Date 階層の属性に対する属性リレーションシップの定義</span><span class="sxs-lookup"><span data-stu-id="ad892-174">Defining Attribute Relationships for Attributes in the Fiscal Date Hierarchy</span></span>  
  
1.  <span data-ttu-id="ad892-175">**Date** ディメンションのディメンション デザイナーに切り替えて、 **[属性リレーションシップ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-175">Switch to Dimension Designer for the **Date** dimension, and then click the **Attribute Relationships** tab.</span></span>  
  
2.  <span data-ttu-id="ad892-176">ダイアグラムで、 **[Month Name]** 属性を右クリックし、 **[新しい属性リレーションシップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-176">In the diagram, right-click the **Month Name** attribute and then select **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="ad892-177">**[属性リレーションシップの作成]** ダイアログ ボックスで、 **[基になる属性]** に **[Month Name]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-177">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Month Name**.</span></span> <span data-ttu-id="ad892-178">**[関連属性]** を **[Fiscal Quarter]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-178">Set the **Related Attribute** to **Fiscal Quarter**.</span></span> <span data-ttu-id="ad892-179">**[リレーションシップの種類]** ボックスの一覧で、リレーションシップの種類を **[固定]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-179">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="ad892-180">ダイアグラムで、 **[Fiscal Quarter]** 属性を右クリックし、 **[新しい属性リレーションシップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-180">In the diagram, right-click the **Fiscal Quarter** attribute and then select **New Attribute Relationship**.</span></span>  
  
6.  <span data-ttu-id="ad892-181">**[属性リレーションシップの作成]** ダイアログ ボックスで、 **[基になる属性]** に **[Fiscal Quarter]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-181">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Fiscal Quarter**.</span></span> <span data-ttu-id="ad892-182">**[関連属性]** を **[Fiscal Semester]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-182">Set the **Related Attribute** to **Fiscal Semester**.</span></span> <span data-ttu-id="ad892-183">**[リレーションシップの種類]** ボックスの一覧で、リレーションシップの種類を **[固定]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-183">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="ad892-184">ダイアグラムで、 **[Fiscal Semester]** 属性を右クリックし、 **[新しい属性リレーションシップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-184">In the diagram, right-click the **Fiscal Semester** attribute and then select **New Attribute Relationship**.</span></span>  
  
9. <span data-ttu-id="ad892-185">**[属性リレーションシップの作成]** ダイアログ ボックスで、 **[基になる属性]** に **[Fiscal Semester]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-185">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Fiscal Semester**.</span></span> <span data-ttu-id="ad892-186">**[関連属性]** を **[Fiscal Year]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-186">Set the **Related Attribute** to **Fiscal Year**.</span></span> <span data-ttu-id="ad892-187">**[リレーションシップの種類]** ボックスの一覧で、リレーションシップの種類を **[固定]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-187">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="defining-attribute-relationships-for-attributes-in-the-calendar-date-hierarchy"></a><span data-ttu-id="ad892-188">Calendar Date 階層の属性に対する属性リレーションシップの定義</span><span class="sxs-lookup"><span data-stu-id="ad892-188">Defining Attribute Relationships for Attributes in the Calendar Date Hierarchy</span></span>  
  
1.  <span data-ttu-id="ad892-189">ダイアグラムで、 **[Month Name]** 属性を右クリックし、 **[新しい属性リレーションシップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-189">In the diagram, right-click the **Month Name** attribute and then select **New Attribute Relationship**.</span></span>  
  
2.  <span data-ttu-id="ad892-190">**[属性リレーションシップの作成]** ダイアログ ボックスで、 **[基になる属性]** に **[Month Name]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-190">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Month Name**.</span></span> <span data-ttu-id="ad892-191">**[関連属性]** を **[Calendar Quarter]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-191">Set the **Related Attribute** to **Calendar Quarter**.</span></span> <span data-ttu-id="ad892-192">**[リレーションシップの種類]** ボックスの一覧で、リレーションシップの種類を **[固定]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-192">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
4.  <span data-ttu-id="ad892-193">ダイアグラムで、 **[Calendar Quarter]** 属性を右クリックし、 **[新しい属性リレーションシップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-193">In the diagram, right-click the **Calendar Quarter** attribute and then select **New Attribute Relationship**.</span></span>  
  
5.  <span data-ttu-id="ad892-194">**[属性リレーションシップの作成]** ダイアログ ボックスで、 **[基になる属性]** に **[Calendar Quarter]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-194">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Calendar Quarter**.</span></span> <span data-ttu-id="ad892-195">**[関連属性]** を **[Calendar Semester]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-195">Set the **Related Attribute** to **Calendar Semester**.</span></span> <span data-ttu-id="ad892-196">**[リレーションシップの種類]** ボックスの一覧で、リレーションシップの種類を **[固定]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-196">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="ad892-197">ダイアグラムで、 **[Calendar Semester]** 属性を右クリックし、 **[新しい属性リレーションシップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-197">In the diagram, right-click the **Calendar Semester** attribute and then select **New Attribute Relationship**.</span></span>  
  
8.  <span data-ttu-id="ad892-198">**[属性リレーションシップの作成]** ダイアログ ボックスで、 **[基になる属性]** に **[Calendar Semester]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-198">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Calendar Semester**.</span></span> <span data-ttu-id="ad892-199">**[関連属性]** を **[Calendar Year]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-199">Set the **Related Attribute** to **Calendar Year**.</span></span> <span data-ttu-id="ad892-200">**[リレーションシップの種類]** ボックスの一覧で、リレーションシップの種類を **[固定]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-200">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="defining-attribute-relationships-for-attributes-in-the-geography-hierarchy"></a><span data-ttu-id="ad892-201">Geography 階層の属性に対する属性リレーションシップの定義</span><span class="sxs-lookup"><span data-stu-id="ad892-201">Defining Attribute Relationships for Attributes in the Geography Hierarchy</span></span>  
  
1.  <span data-ttu-id="ad892-202">Geography ディメンションのディメンション デザイナーを開き、 **[属性リレーションシップ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-202">Open Dimension Designer for the Geography dimension, and then click the **Attribute Relationships** tab.</span></span>  
  
2.  <span data-ttu-id="ad892-203">ダイアグラムで、 **[Postal Code]** 属性を右クリックし、 **[新しい属性リレーションシップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-203">In the diagram, right-click the **Postal Code** attribute and then select **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="ad892-204">**[属性リレーションシップの作成]** ダイアログ ボックスで、 **[基になる属性]** に **[Postal Code]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-204">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Postal Code**.</span></span> <span data-ttu-id="ad892-205">**[関連属性]** を **[City]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-205">Set the **Related Attribute** to **City**.</span></span> <span data-ttu-id="ad892-206">**[リレーションシップの種類]** ボックスの一覧で、リレーションシップの種類を **[可変]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-206">In the **Relationship type** list, set the relationship type to **Flexible**.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="ad892-207">ダイアグラムで、 **[City]** 属性を右クリックし、 **[新しい属性リレーションシップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-207">In the diagram, right-click the **City** attribute and then select **New Attribute Relationship**.</span></span>  
  
6.  <span data-ttu-id="ad892-208">**[属性リレーションシップの作成]** ダイアログ ボックスで、 **[基になる属性]** に **[City]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-208">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **City**.</span></span> <span data-ttu-id="ad892-209">**[関連属性]** を **[State-Province]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-209">Set the **Related Attribute** to **State-Province**.</span></span> <span data-ttu-id="ad892-210">**[リレーションシップの種類]** ボックスの一覧で、リレーションシップの種類を **[固定]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-210">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="ad892-211">ダイアグラムで、 **[State-Province]** 属性を右クリックし、 **[新しい属性リレーションシップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-211">In the diagram, right-click the **State-Province** attribute and then select **New Attribute Relationship**.</span></span>  
  
9. <span data-ttu-id="ad892-212">**[属性リレーションシップの作成]** ダイアログ ボックスで、 **[基になる属性]** に **[State-Province]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-212">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **State-Province**.</span></span> <span data-ttu-id="ad892-213">**[関連属性]** を **[Country-Region]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-213">Set the **Related Attribute** to **Country-Region**.</span></span> <span data-ttu-id="ad892-214">**[リレーションシップの種類]** ボックスの一覧で、リレーションシップの種類を **[固定]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-214">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. <span data-ttu-id="ad892-215">ダイアグラムで、 **[Geography Key]** 属性を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-215">In the diagram, right-click the **Geography Key** attribute and then select **Properties**.</span></span>  
  
12. <span data-ttu-id="ad892-216">**AttributeHierarchyOptimizedState** プロパティを **NotOptimized**に設定し、 **AttributeHierarchyOrdered** プロパティを **False**に設定し、 **AttributeHierarchyVisible** プロパティを **False**に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad892-216">Set the **AttributeHierarchyOptimizedState** property to **NotOptimized**, set the **AttributeHierarchyOrdered** property to **False**, and set the **AttributeHierarchyVisible** property to **False**.</span></span>  
  
13. <span data-ttu-id="ad892-217">**[File]\(ファイル\)** メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-217">On the **File** menu, click **Save All**.</span></span>  
  
14. <span data-ttu-id="ad892-218">**で、** [ビルド] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]メニューの **[Analysis Services Tutorial の配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad892-218">On the **Build** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="ad892-219">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="ad892-219">Next Task in Lesson</span></span>  
 [<span data-ttu-id="ad892-220">不明なメンバーと NULL 処理のプロパティの定義</span><span class="sxs-lookup"><span data-stu-id="ad892-220">Defining the Unknown Member and Null Processing Properties</span></span>](lesson-4-7-defining-the-unknown-member-and-null-processing-properties.md)  
  
## <a name="see-also"></a><span data-ttu-id="ad892-221">参照</span><span class="sxs-lookup"><span data-stu-id="ad892-221">See Also</span></span>  
 <span data-ttu-id="ad892-222">[属性リレーションシップの定義](multidimensional-models/attribute-relationships-define.md) </span><span class="sxs-lookup"><span data-stu-id="ad892-222">[Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md) </span></span>  
 [<span data-ttu-id="ad892-223">ユーザー階層プロパティ</span><span class="sxs-lookup"><span data-stu-id="ad892-223">User Hierarchy Properties</span></span>](multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)  
  
  
