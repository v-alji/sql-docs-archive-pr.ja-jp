---
title: 属性階層の非表示と無効化 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 095039c2-7104-414c-a9a6-327b03ce79df
author: minewiskan
ms.author: owend
ms.openlocfilehash: cc043c68d2a83424a14707799fd90bf893abc12d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742633"
---
# <a name="hiding-and-disabling-attribute-hierarchies"></a><span data-ttu-id="5b661-102">属性階層の非表示化と無効化</span><span class="sxs-lookup"><span data-stu-id="5b661-102">Hiding and Disabling Attribute Hierarchies</span></span>
  <span data-ttu-id="5b661-103">既定では、ディメンションの属性ごとに属性階層が 1 つ作成されます。また、それぞれの階層はディメンションのファクト データで使用できます。</span><span class="sxs-lookup"><span data-stu-id="5b661-103">By default, an attribute hierarchy is created for every attribute in a dimension, and each hierarchy is available for dimensioning fact data.</span></span> <span data-ttu-id="5b661-104">属性階層は、"All" レベルと、その階層のすべてのメンバーを含む詳細レベルで構成されます。</span><span class="sxs-lookup"><span data-stu-id="5b661-104">This hierarchy consists of an "All" level and a detail level containing all members of the hierarchy.</span></span> <span data-ttu-id="5b661-105">既に学習したように、これらの属性をユーザー定義階層として整理し、キューブ内にナビゲーション パスを設けることができます。</span><span class="sxs-lookup"><span data-stu-id="5b661-105">As you have already learned, you can organize attributes into user-defined hierarchies to provide navigation paths in a cube.</span></span> <span data-ttu-id="5b661-106">状況によっては、一部の属性とその階層を無効にしたり、非表示にしたりする必要が生じます。</span><span class="sxs-lookup"><span data-stu-id="5b661-106">Under certain circumstances, you may want to disable or hide some attributes and their hierarchies.</span></span> <span data-ttu-id="5b661-107">たとえば、社会保障番号 (身分登録番号)、給与、誕生日、ログイン情報などは、キューブ情報の生成には必要のない属性です。</span><span class="sxs-lookup"><span data-stu-id="5b661-107">For example, certain attributes such as social security numbers or national identification numbers, pay rates, birth dates, and login information are not attributes by which users will dimension cube information.</span></span> <span data-ttu-id="5b661-108">一般に、これらの情報は、特定の属性メンバーの詳細情報としてのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="5b661-108">Instead, this information is generally only viewed as details of a particular attribute member.</span></span> <span data-ttu-id="5b661-109">したがって、これらの属性階層を非表示にして、各属性のメンバー プロパティとしてのみ表示されるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b661-109">You may want to hide these attribute hierarchies, leaving the attributes visible only as member properties of a specific attribute.</span></span> <span data-ttu-id="5b661-110">また、顧客名、郵便番号など他の属性メンバーは、属性階層に個別に表示するのではなく、ユーザー階層からのみ表示されるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b661-110">You may also want to make members of other attributes, such as customer names or postal codes, visible only when they are viewed through a user hierarchy instead of independently through an attribute hierarchy.</span></span> <span data-ttu-id="5b661-111">このような処理をするのは、属性階層内の独立したメンバーが非常に多いためです。</span><span class="sxs-lookup"><span data-stu-id="5b661-111">One reason to do so may be the sheer number of distinct members in the attribute hierarchy.</span></span> <span data-ttu-id="5b661-112">処理パフォーマンスを向上させるため、ユーザーが参照しない属性階層を無効にしてください。</span><span class="sxs-lookup"><span data-stu-id="5b661-112">Finally, to improve processing performance, you should disable attribute hierarchies that users will not use for browsing.</span></span>

 <span data-ttu-id="5b661-113">**AttributeHierarchyEnabled** プロパティは、属性階層を作成するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5b661-113">The value of the **AttributeHierarchyEnabled** property determines whether an attribute hierarchy is created.</span></span> <span data-ttu-id="5b661-114">このプロパティを **False**に設定すると、属性階層は作成されず、その属性はユーザー階層のレベルとして使用できなくなります。つまり、属性階層がメンバー プロパティとしてのみ存在するようになります。</span><span class="sxs-lookup"><span data-stu-id="5b661-114">If this property is set to **False**, the attribute hierarchy is not created and the attribute cannot be used as a level in a user hierarchy; the attribute hierarchy exists as a member property only.</span></span> <span data-ttu-id="5b661-115">ただし、属性階層を無効にしても、その属性階層を使用して別の属性のメンバーを整理することはできます。</span><span class="sxs-lookup"><span data-stu-id="5b661-115">However, a disabled attribute hierarchy can still be used to order the members of another attribute.</span></span> <span data-ttu-id="5b661-116">**AttributeHierarchyEnabled** プロパティを **True**に設定している場合は、ユーザー定義階層で属性階層が使用されているかどうかに関係なく、 **AttributeHierarchyVisible** プロパティの値によりその属性階層の表示、非表示が決定されます。</span><span class="sxs-lookup"><span data-stu-id="5b661-116">If the value of the **AttributeHierarchyEnabled** property is set to **True**, the value of the **AttributeHierarchyVisible** property determines whether the attribute hierarchy is visible independent of its use in a user-defined hierarchy.</span></span>

 <span data-ttu-id="5b661-117">属性階層を有効にしている場合は、さらに次の 3 つのプロパティに値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5b661-117">When an attribute hierarchy is enabled, you may want to specify values for the following three additional properties:</span></span>

-   <span data-ttu-id="5b661-118">**IsAggregatable**</span><span class="sxs-lookup"><span data-stu-id="5b661-118">**IsAggregatable**</span></span>

     <span data-ttu-id="5b661-119">既定では、すべての属性階層に (All) レベルが定義されます。</span><span class="sxs-lookup"><span data-stu-id="5b661-119">By default, an (All) level is defined for all attribute hierarchies.</span></span> <span data-ttu-id="5b661-120">有効な属性階層の (All) レベルを無効にするには、このプロパティを **False**に設定します。</span><span class="sxs-lookup"><span data-stu-id="5b661-120">To disable the (All) level for an enabled attribute hierarchy, set the value for this property to **False**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="5b661-121">**IsAggregatable** プロパティが False に設定された属性は、ユーザー定義階層のルートとしてのみ使用できます。また、この属性には、指定された既定メンバーを割り当てる必要があります (これを行わなかった場合は、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] エンジンによって既定メンバーが選択されます)。</span><span class="sxs-lookup"><span data-stu-id="5b661-121">An attribute that has its **IsAggregatable** property set to false can only be used as the root of a user-defined hierarchy and must have a default member specified (otherwise, one will be chosen for you by the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] engine).</span></span>

-   <span data-ttu-id="5b661-122">**AttributeHierarchyOrdered**</span><span class="sxs-lookup"><span data-stu-id="5b661-122">**AttributeHierarchyOrdered**</span></span>

     <span data-ttu-id="5b661-123">既定では、処理中に \*\* が有効な属性階層のメンバーを整理し、Name や Key などの [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]OrderBy\*\* プロパティの値に基づいてメンバーを格納します。</span><span class="sxs-lookup"><span data-stu-id="5b661-123">By default, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] orders the members of enabled attribute hierarchies during processing, and then stores the members by the value of the **OrderBy** property, such as by Name or Key.</span></span> <span data-ttu-id="5b661-124">メンバーが順不同でもよい場合は、このプロパティの値を **False** に設定することにより、パフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="5b661-124">If you do not care about ordering, you can increase processing performance by setting the value of this property to **False**.</span></span>

-   <span data-ttu-id="5b661-125">**AttributeHierarchyOptimizedState**</span><span class="sxs-lookup"><span data-stu-id="5b661-125">**AttributeHierarchyOptimizedState**</span></span>

     <span data-ttu-id="5b661-126">既定では、処理中に [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] が有効な各属性階層のインデックスを作成します。これにより、クエリのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="5b661-126">By default, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] creates an index for each enabled attribute hierarchy during processing, to improve query performance.</span></span> <span data-ttu-id="5b661-127">属性階層を表示する予定がない場合は、このプロパティの値を **NotOptimized**に設定することにより、パフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="5b661-127">If you do not plan to use an attribute hierarchy for browsing, you can increase processing performance by setting the value of this property to **NotOptimized**.</span></span> <span data-ttu-id="5b661-128">ただし、非表示の属性をディメンションのキー属性として使用する場合は、属性メンバーのインデックスを作成することでパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="5b661-128">However, if you use a hidden hierarchy as the key attribute for the dimension, creating an index of the attribute members will still improve performance.</span></span>

 <span data-ttu-id="5b661-129">属性階層が無効になっている場合は、これらのプロパティが適用されません。</span><span class="sxs-lookup"><span data-stu-id="5b661-129">These properties do not apply if an attribute hierarchy is disabled.</span></span>

 <span data-ttu-id="5b661-130">このトピックの実習では、Employee ディメンションの社会保障番号のほか、表示する必要のない他の属性を無効にします。</span><span class="sxs-lookup"><span data-stu-id="5b661-130">In the tasks in this topic, you will disable social security numbers and other attributes in the Employee dimension that will not be used for browsing.</span></span> <span data-ttu-id="5b661-131">次に、Customer ディメンションの顧客名と郵便番号の属性階層を非表示にします。</span><span class="sxs-lookup"><span data-stu-id="5b661-131">You will then hide the customer name and postal code attribute hierarchies in the Customer dimension.</span></span> <span data-ttu-id="5b661-132">ユーザー階層とは関係なく、これらの階層の属性メンバーが多いと、階層の表示が非常に遅くなります。</span><span class="sxs-lookup"><span data-stu-id="5b661-132">The large number of attribute members in these hierarchies will make browsing these hierarchies very slow independent of a user hierarchy.</span></span>

## <a name="setting-attribute-hierarchy-properties-in-the-employee-dimension"></a><span data-ttu-id="5b661-133">Employee ディメンションの属性階層プロパティの設定</span><span class="sxs-lookup"><span data-stu-id="5b661-133">Setting Attribute Hierarchy Properties in the Employee Dimension</span></span>

1.  <span data-ttu-id="5b661-134">Employee ディメンションのディメンション デザイナーに切り替え、 **[ブラウザー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5b661-134">Switch to Dimension Designer for the Employee dimension, and then click the **Browser** tab.</span></span>

2.  <span data-ttu-id="5b661-135">**[階層]** ボックスの一覧に、次の属性階層が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5b661-135">Verify that the following attribute hierarchies appear in the **Hierarchy** list:</span></span>

    -   <span data-ttu-id="5b661-136">**Base Rate**</span><span class="sxs-lookup"><span data-stu-id="5b661-136">**Base Rate**</span></span>

    -   <span data-ttu-id="5b661-137">**生年月日**</span><span class="sxs-lookup"><span data-stu-id="5b661-137">**Birth Date**</span></span>

    -   <span data-ttu-id="5b661-138">**Login ID**</span><span class="sxs-lookup"><span data-stu-id="5b661-138">**Login ID**</span></span>

    -   <span data-ttu-id="5b661-139">**Manager SSN**</span><span class="sxs-lookup"><span data-stu-id="5b661-139">**Manager SSN**</span></span>

    -   <span data-ttu-id="5b661-140">**保障**</span><span class="sxs-lookup"><span data-stu-id="5b661-140">**SSN**</span></span>

3.  <span data-ttu-id="5b661-141">**[ディメンション構造]** タブに切り替え、 **[属性]** ペインで次の属性を選択します。</span><span class="sxs-lookup"><span data-stu-id="5b661-141">Switch to the **Dimension Structure** tab, and then select the following attributes in the **Attributes** pane.</span></span> <span data-ttu-id="5b661-142">Ctrl キーを押しながらクリックすると、複数のメジャーを選択できます。</span><span class="sxs-lookup"><span data-stu-id="5b661-142">You can select multiple measures by clicking each while holding down the CTRL key:</span></span>

    -   <span data-ttu-id="5b661-143">**Base Rate**</span><span class="sxs-lookup"><span data-stu-id="5b661-143">**Base Rate**</span></span>

    -   <span data-ttu-id="5b661-144">**生年月日**</span><span class="sxs-lookup"><span data-stu-id="5b661-144">**Birth Date**</span></span>

    -   <span data-ttu-id="5b661-145">**Login ID**</span><span class="sxs-lookup"><span data-stu-id="5b661-145">**Login ID**</span></span>

    -   <span data-ttu-id="5b661-146">**Manager SSN**</span><span class="sxs-lookup"><span data-stu-id="5b661-146">**Manager SSN**</span></span>

    -   <span data-ttu-id="5b661-147">**保障**</span><span class="sxs-lookup"><span data-stu-id="5b661-147">**SSN**</span></span>

4.  <span data-ttu-id="5b661-148">[プロパティ] ウィンドウで、選択した属性の **AttributeHierarchyEnabled** プロパティの値を **False** に設定します。</span><span class="sxs-lookup"><span data-stu-id="5b661-148">In the Properties window, set the value of the **AttributeHierarchyEnabled** property to **False** for the selected attributes.</span></span>

     <span data-ttu-id="5b661-149">**[属性]** ペインを見ると、各属性のアイコンが変わり、無効になっていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="5b661-149">Notice in the **Attributes** pane that the icon for each attribute has changed to indicate that the attribute is not enabled.</span></span>

     <span data-ttu-id="5b661-150">次の図では、選択した属性の **AttributeHierarchyEnabled** プロパティが False に設定されています。</span><span class="sxs-lookup"><span data-stu-id="5b661-150">The following image shows the **AttributeHierarchyEnabled** property set to False for the selected attributes.</span></span>

     <span data-ttu-id="5b661-151">![False に設定された AttributeHierarchyEnabled プロパティ](../../2014/tutorials/media/l4-hierarchyenabled-1.gif "False に設定された AttributeHierarchyEnabled プロパティ")</span><span class="sxs-lookup"><span data-stu-id="5b661-151">![AttributeHierarchyEnabled property set to False](../../2014/tutorials/media/l4-hierarchyenabled-1.gif "AttributeHierarchyEnabled property set to False")</span></span>

5.  <span data-ttu-id="5b661-152">**[ビルド]** メニューの **[Analysis Services Tutorial の配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5b661-152">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>

6.  <span data-ttu-id="5b661-153">処理が完了したら **[ブラウザー]** タブに切り替え、 **[再接続]** をクリックします。その後、変更後の属性階層を表示してみてください。</span><span class="sxs-lookup"><span data-stu-id="5b661-153">When processing has successfully completed, switch to the **Browser** tab, click **Reconnect**, and then try to browse the modified attribute hierarchies.</span></span>

     <span data-ttu-id="5b661-154">変更した属性のメンバーは、 **[階層]** ボックスの一覧に属性階層として表示されません。</span><span class="sxs-lookup"><span data-stu-id="5b661-154">Notice that the members of the modified attributes are not available for browsing as attribute hierarchies in the **Hierarchy** list.</span></span> <span data-ttu-id="5b661-155">無効にしたいずれかの階層属性をユーザー階層のレベルとして追加しようとすると、ユーザー定義階層に追加するには、その属性階層を有効にしなければならないことを知らせるエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5b661-155">If you try to add one of the disabled attribute hierarchies as a level in a user hierarchy, you will receive an error notifying you that the attribute hierarchy must be enabled to participate in a user-defined hierarchy.</span></span>

## <a name="setting-attribute-hierarchy-properties-in-the-customer-dimension"></a><span data-ttu-id="5b661-156">Customer ディメンションの属性階層プロパティの設定</span><span class="sxs-lookup"><span data-stu-id="5b661-156">Setting Attribute Hierarchy Properties in the Customer Dimension</span></span>

1.  <span data-ttu-id="5b661-157">Customer ディメンションのディメンション デザイナーに切り替え、 **[ブラウザー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5b661-157">Switch to Dimension Designer for the Customer dimension, and then click the **Browser** tab.</span></span>

2.  <span data-ttu-id="5b661-158">**[階層]** ボックスの一覧に、次の属性階層が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5b661-158">Verify that the following attribute hierarchies appear in the **Hierarchy** list:</span></span>

    -   <span data-ttu-id="5b661-159">**フルネーム**</span><span class="sxs-lookup"><span data-stu-id="5b661-159">**Full Name**</span></span>

    -   <span data-ttu-id="5b661-160">**Postal Code**</span><span class="sxs-lookup"><span data-stu-id="5b661-160">**Postal Code**</span></span>

3.  <span data-ttu-id="5b661-161">**[ディメンション構造]** タブに切り替え、 **[属性]** ペインで次の属性を選択します。複数の属性を選択するときは、Ctrl キーを押しながら各属性をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5b661-161">Switch to the **Dimension Structure** tab, and then select the following attributes in the **Attributes** pane by using the CTRL key to select multiple attributes at the same time:</span></span>

    -   <span data-ttu-id="5b661-162">**フルネーム**</span><span class="sxs-lookup"><span data-stu-id="5b661-162">**Full Name**</span></span>

    -   <span data-ttu-id="5b661-163">**Postal Code**</span><span class="sxs-lookup"><span data-stu-id="5b661-163">**Postal Code**</span></span>

4.  <span data-ttu-id="5b661-164">[プロパティ] ウィンドウで、選択した属性の **AttributeHierarchyVisible** プロパティの値を **False** に設定します。</span><span class="sxs-lookup"><span data-stu-id="5b661-164">In the Properties window, set the value of the **AttributeHierarchyVisible** property to **False** for the selected attributes.</span></span>

     <span data-ttu-id="5b661-165">これらの属性階層のメンバーはファクト データの多次元化に使用されるため、メンバーを整理して最適化することによりパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="5b661-165">Because the members of these attribute hierarchies will be used for dimensioning fact data, ordering and optimizing the members of these attribute hierarchies will improve performance.</span></span> <span data-ttu-id="5b661-166">このため、これらの属性のプロパティは変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="5b661-166">Therefore, the properties of these attributes should not be changed.</span></span>

     <span data-ttu-id="5b661-167">次の図では、 **AttributeHierarchyVisible** プロパティが False に設定されています。</span><span class="sxs-lookup"><span data-stu-id="5b661-167">The following image shows the **AttributeHierarchyVisible** property set to False.</span></span>

     <span data-ttu-id="5b661-168">![False に設定された AttributeHierarchyVisible プロパティ](../../2014/tutorials/media/l4-hierarchyvisible-1.gif "False に設定された AttributeHierarchyVisible プロパティ")</span><span class="sxs-lookup"><span data-stu-id="5b661-168">![AttributeHierarchyVisible property set to False](../../2014/tutorials/media/l4-hierarchyvisible-1.gif "AttributeHierarchyVisible property set to False")</span></span>

5.  <span data-ttu-id="5b661-169">**[属性]** ペインの **Postal Code** 属性を、 **[階層とレベル]** ペインの **Customer Geography** ユーザー階層 ( **City** レベルのすぐ下) にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="5b661-169">Drag the **Postal Code** attribute from the **Attributes** pane into the **Customer Geography** user hierarchy in the **Hierarchies and Levels** pane, immediately under the **City** level.</span></span>

     <span data-ttu-id="5b661-170">属性が非表示に設定されていても、ユーザー階層にレベルとして追加することができます。</span><span class="sxs-lookup"><span data-stu-id="5b661-170">Notice that a hidden attribute can still become a level in a user hierarchy.</span></span>

6.  <span data-ttu-id="5b661-171">**[ビルド]** メニューの **[Analysis Services Tutorial の配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5b661-171">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>

7.  <span data-ttu-id="5b661-172">配置が正常に完了したら、Customer ディメンションの **[ブラウザー]** タブに切り替え、 **[再接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5b661-172">When deployment has successfully completed, switch to the **Browser** tab for the Customer dimension, and then click **Reconnect**.</span></span>

8.  <span data-ttu-id="5b661-173">**[階層]** ボックスの一覧から、変更した属性階層のいずれかを選択してみます。</span><span class="sxs-lookup"><span data-stu-id="5b661-173">Try to select either of the modified attribute hierarchies from the **Hierarchy** list.</span></span>

     <span data-ttu-id="5b661-174">**[階層]** ボックスの一覧には、変更した属性階層は何も表示されないはずです。</span><span class="sxs-lookup"><span data-stu-id="5b661-174">Notice that neither of the modified attribute hierarchies appears in the **Hierarchy** list.</span></span>

9. <span data-ttu-id="5b661-175">**[階層]** ボックスの一覧で **[Customer Geography]** をクリックし、ブラウザー ペインに各レベルを表示します。</span><span class="sxs-lookup"><span data-stu-id="5b661-175">In the **Hierarchy** list, select **Customer Geography**, and then browse each level in the browser pane.</span></span>

     <span data-ttu-id="5b661-176">ユーザー定義階層には、非表示にした **Postal Code** レベルと **Full Name**レベルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5b661-176">Notice that the hidden levels, **Postal Code** and **Full Name**, are visible in the user-defined hierarchy.</span></span>

## <a name="next-task-in-lesson"></a><span data-ttu-id="5b661-177">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="5b661-177">Next Task in Lesson</span></span>
 [<span data-ttu-id="5b661-178">2 次属性に基づく属性メンバーの並べ替え</span><span class="sxs-lookup"><span data-stu-id="5b661-178">Sorting Attribute Members Based on a Secondary Attribute</span></span>](lesson-4-5-sorting-attribute-members-based-on-a-secondary-attribute.md)


