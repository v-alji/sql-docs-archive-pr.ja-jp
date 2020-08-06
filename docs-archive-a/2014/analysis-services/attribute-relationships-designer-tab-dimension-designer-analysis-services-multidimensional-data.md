---
title: 属性リレーションシップ ([属性リレーションシップ] タブ、ディメンションデザイナー) (Analysis Services 多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.ardesigner.attributerelationships.f1
ms.assetid: abc8af00-5389-456d-b0f1-ec3e7403d4f9
author: minewiskan
ms.author: owend
ms.openlocfilehash: a0d3b9beb03b060b0ca6d334f23c490e6aea90a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633622"
---
# <a name="attribute-relationships-attribute-relationship-designer-tab-dimension-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="c9a0f-102">[属性リレーションシップ] ([属性リレーションシップ] タブ、ディメンション デザイナー) (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="c9a0f-102">Attribute Relationships (Attribute Relationship Designer Tab, Dimension Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="c9a0f-103">**[属性リレーションシップ]** の一覧を使用すると、属性リレーションシップ ダイアグラム内の特定の属性リレーションシップを探したり、そのリレーションシップを管理したりできます。</span><span class="sxs-lookup"><span data-stu-id="c9a0f-103">Use the **Attribute Relationship** list to locate a specific attribute relationship in the attribute relationship diagram and to manage that relationship.</span></span> <span data-ttu-id="c9a0f-104">このペインは、属性リレーションシップ ダイアグラムを含むペインのすぐ下に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c9a0f-104">This pane appears immediately under the pane that contains the attribute relationship diagram.</span></span>  
  
 <span data-ttu-id="c9a0f-105">**[属性リレーションシップ] ペインを表示するには**</span><span class="sxs-lookup"><span data-stu-id="c9a0f-105">**To view the Attribute Relationships pane**</span></span>  
  
1.  <span data-ttu-id="c9a0f-106">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]のソリューション エクスプローラーで、ディメンションをダブルクリックしてディメンション デザイナーを開き、 **[属性リレーションシップ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c9a0f-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in Solution Explorer, double-click a dimension to open the Dimension Designer, and then click the **Attribute Relationship** tab.</span></span>  
  
2.  <span data-ttu-id="c9a0f-107">ツール バーの **[リスト ビューの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c9a0f-107">On the toolbar, click the **Show List Views** icon.</span></span>  
  
## <a name="using-the-attribute-relationships-list"></a><span data-ttu-id="c9a0f-108">[属性リレーションシップ] の一覧の使用</span><span class="sxs-lookup"><span data-stu-id="c9a0f-108">Using the Attribute Relationships List</span></span>  
 <span data-ttu-id="c9a0f-109">**[属性リレーションシップ]** の一覧には、ディメンション内のすべての属性リレーションシップが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c9a0f-109">The **Attribute Relationships** list displays all the attribute relationships in the dimension.</span></span>  
  
 <span data-ttu-id="c9a0f-110">属性リレーションシップ ダイアグラム内の特定の属性リレーションシップを探すには、一覧にある属性をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="c9a0f-110">To locate a specific attribute relationship in the attribute relationship diagram, double-click the attribute in the list.</span></span> <span data-ttu-id="c9a0f-111">属性リレーションシップは属性リレーションシップ ダイアグラムで強調表示され、そのプロパティは [プロパティ] ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c9a0f-111">The attribute relationship will be highlighted in the attribute relationship diagram and its properties will appear in the Properties window.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c9a0f-112">この一覧では、複数の属性リレーションシップを選択して変更できます。</span><span class="sxs-lookup"><span data-stu-id="c9a0f-112">You can select multiple attribute relationships in the list and make changes.</span></span>  
  
 <span data-ttu-id="c9a0f-113">属性リレーションシップが正しくない場合は、2 つの属性を接続する矢印にアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c9a0f-113">If an attribute relationship is incorrect, an icon appears on the arrow connecting to the two attributes.</span></span> <span data-ttu-id="c9a0f-114">リレーションシップが正しくない理由を特定するには、アイコン上にポインターを合わせ、ツールヒントに表示される説明を確認します。</span><span class="sxs-lookup"><span data-stu-id="c9a0f-114">To determine why the relationship is not correct, pause on the icon and read the description provided in the tooltip.</span></span>  
  
 <span data-ttu-id="c9a0f-115">属性リレーションシップを管理するには、属性リレーションシップを右クリックし、ショートカット メニューの適切なコマンドをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c9a0f-115">To manage the attribute relationship, right-click the attribute relationship and click the appropriate command in the shortcut menu.</span></span>  
  
### <a name="shortcut-menu-options"></a><span data-ttu-id="c9a0f-116">ショートカット メニューのオプション</span><span class="sxs-lookup"><span data-stu-id="c9a0f-116">Shortcut Menu Options</span></span>  
 <span data-ttu-id="c9a0f-117">**[属性リレーションシップの編集]**</span><span class="sxs-lookup"><span data-stu-id="c9a0f-117">**Edit Attribute Relationship**</span></span>  
 <span data-ttu-id="c9a0f-118">属性リレーションシップを変更できる、**[属性リレーションシップの編集]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="c9a0f-118">Opens the **Edit Attribute Relationship** dialog box in which you can modify the attribute relationship.</span></span>  
  
 <span data-ttu-id="c9a0f-119">詳細については、[[属性リレーションシップの作成] ダイアログ ボックスと [属性リレーションシップの編集] ダイアログ ボックス &#40;[属性リレーションシップ] タブ、ディメンション デザイナー&#41; &#40;Analysis Services - 多次元データ&#41;](create-edit-attribute-relationships-dialog-boxes-analysis-services-multidimensional-data.md) と [属性リレーションシップの定義](multidimensional-models/attribute-relationships-define.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c9a0f-119">For more information, see [Create Attribute Relationship and Edit Attribute Relationship Dialog Boxes &#40;Attribute Relationship Designer Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](create-edit-attribute-relationships-dialog-boxes-analysis-services-multidimensional-data.md) and [Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md).</span></span>  
  
 <span data-ttu-id="c9a0f-120">**[リレーションシップの種類]**</span><span class="sxs-lookup"><span data-stu-id="c9a0f-120">**Relationship Type**</span></span>  
 <span data-ttu-id="c9a0f-121">リレーションシップの種類を **[可変]** または **[固定]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="c9a0f-121">Sets the relationship type to either **Flexible** or **Rigid**.</span></span> <span data-ttu-id="c9a0f-122">可変のリレーションシップでは、メンバー間のリレーションシップが時間の経過と共に変化します。</span><span class="sxs-lookup"><span data-stu-id="c9a0f-122">In a flexible relationship, relationships between members change over time.</span></span> <span data-ttu-id="c9a0f-123">固定のリレーションシップでは、メンバー間のリレーションシップが時間の経過と共に変化しません。</span><span class="sxs-lookup"><span data-stu-id="c9a0f-123">In a rigid relationship, relationships between members do not change over time.</span></span>  
  
 <span data-ttu-id="c9a0f-124">**削除**</span><span class="sxs-lookup"><span data-stu-id="c9a0f-124">**Delete**</span></span>  
 <span data-ttu-id="c9a0f-125">選択した属性リレーションシップを削除します。</span><span class="sxs-lookup"><span data-stu-id="c9a0f-125">Deletes the selected attribute relationship.</span></span>  
  
 <span data-ttu-id="c9a0f-126">**プロパティ**</span><span class="sxs-lookup"><span data-stu-id="c9a0f-126">**Properties**</span></span>  
 <span data-ttu-id="c9a0f-127">属性のプロパティを **[プロパティ]** ウィンドウに表示します。</span><span class="sxs-lookup"><span data-stu-id="c9a0f-127">Displays the attribute's properties in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9a0f-128">参照</span><span class="sxs-lookup"><span data-stu-id="c9a0f-128">See Also</span></span>  
 <span data-ttu-id="c9a0f-129">[ディメンションデザイナー &#40;の属性リレーションシップ&#41; &#40;Analysis Services-多次元データ&#41;](attribute-relationships-dimension-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="c9a0f-129">[Attribute Relationships &#40;Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](attribute-relationships-dimension-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="c9a0f-130">[ツールバー &#40;[属性リレーションシップ] デザイナータブ、ディメンションデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](toolbar-attribute-relationship-dimension-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="c9a0f-130">[Toolbar &#40;Attribute Relationship Designer Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-attribute-relationship-dimension-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="c9a0f-131">[属性 &#40;属性リレーションシップデザイナー] タブ、ディメンションデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](attributes-designer-tab-dimension-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="c9a0f-131">[Attributes &#40;Attribute Relationship Designer Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](attributes-designer-tab-dimension-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="c9a0f-132">[属性リレーションシップダイアグラム &#40;[属性リレーションシップ] デザイナータブ、ディメンションデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](attribute-relationship-diagram-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="c9a0f-132">[Attribute Relationship Diagram &#40;Attribute Relationship Designer Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](attribute-relationship-diagram-analysis-services-multidimensional-data.md)</span></span>  
  
  
