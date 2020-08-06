---
title: 多次元モデルの計算 |Microsoft Docs
ms.custom: ''
ms.date: 12/10/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- calculations [Analysis Services], creating
- deleting calculations
- calculations [Analysis Services], scripts
- Cube Designer
- modifying scripts
- removing calculations
- calculations [Analysis Services], deleting
- scripts [Analysis Services], calculations
- cubes [Analysis Services], calculations
- solve orders [Analysis Services]
ms.assetid: c21b3459-9bef-45a2-aba5-c992eba5b66e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 64a9733c4fd198a9906e28c437f7ba4fb10dd39a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737158"
---
# <a name="calculations-in-multidimensional-models"></a><span data-ttu-id="8d98f-102">多次元モデルの計算</span><span class="sxs-lookup"><span data-stu-id="8d98f-102">Calculations in Multidimensional Models</span></span>
  <span data-ttu-id="8d98f-103">キューブ デザイナーの **[計算]** タブを使用して、計算されるメンバー、名前付きセット、およびその他の多次元式 (MDX) 計算を作成します。</span><span class="sxs-lookup"><span data-stu-id="8d98f-103">Use the **Calculations** tab of Cube Designer to create calculated members, named sets, and other Multidimensional Expressions (MDX) calculations.</span></span>  
  
 <span data-ttu-id="8d98f-104">**[計算]** タブには、次の 3 つのペインがあります。</span><span class="sxs-lookup"><span data-stu-id="8d98f-104">The **Calculations** tab has the following three panes:</span></span>  
  
-   <span data-ttu-id="8d98f-105">**[スクリプト オーガナイザー]** ペインには、キューブ内の計算が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="8d98f-105">The **Script Organizer** pane lists the calculations in a cube.</span></span> <span data-ttu-id="8d98f-106">このペインを使用して、編集する計算を作成、整理、および選択します。</span><span class="sxs-lookup"><span data-stu-id="8d98f-106">Use this pane to create, organize, and select calculations for editing.</span></span>  
  
-   <span data-ttu-id="8d98f-107">**[計算ツール]** ペインには、計算を作成するためのメタデータ、関数、およびテンプレートが用意されています。</span><span class="sxs-lookup"><span data-stu-id="8d98f-107">The **Calculation Tools** pane provides metadata, functions, and templates with which to create calculations.</span></span>  
  
-   <span data-ttu-id="8d98f-108">計算式ペインでは、フォーム ビューおよびスクリプト ビューがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="8d98f-108">The Calculation Expressions pane supports a form view and a script view.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8d98f-109">MDX スクリプティングの詳細については、「 [Microsoft SQL Server 2005 での Mdx スクリプトの概要](https://go.microsoft.com/fwlink/?LinkId=81892)」を参照してください。また、Microsoft TechNet Web サイトの[SQL Server 2005-Analysis Services](https://go.microsoft.com/fwlink/?LinkId=80853)のページにある「その他のリソース」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d98f-109">For more information about MDX scripting, see [Introduction to MDX Scripting in Microsoft SQL Server 2005](https://go.microsoft.com/fwlink/?LinkId=81892), and see the Additional Resources section on the [SQL Server 2005 - Analysis Services](https://go.microsoft.com/fwlink/?LinkId=80853) page on the Microsoft TechNet Web site.</span></span> <span data-ttu-id="8d98f-110">キューブ デザインに関連するパフォーマンスの問題の詳細については、「 [SQL Server 2005 Analysis Services パフォーマンス ガイド](https://download.microsoft.com/download/8/5/e/85eea4fa-b3bb-4426-97d0-7f7151b2011c/ssas2005perfguide.doc)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d98f-110">For more information about performance issues related to cube design, see the [SQL Server 2005 Analysis Services Performance Guide](https://download.microsoft.com/download/8/5/e/85eea4fa-b3bb-4426-97d0-7f7151b2011c/ssas2005perfguide.doc).</span></span>  
  
## <a name="creating-a-new-calculation"></a><span data-ttu-id="8d98f-111">新しい計算の作成</span><span class="sxs-lookup"><span data-stu-id="8d98f-111">Creating a New Calculation</span></span>  
 <span data-ttu-id="8d98f-112">新しい計算を作成するには、キューブ デザイナーの **[計算]** タブの **[キューブ]** メニューで、作成する計算の種類に応じて、 **[新しい計算されるメンバー]**、 **[新しい名前付きセット]**、または **[新しいスクリプト コマンド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8d98f-112">To create a new calculation, on the **Calculations** tab of Cube Designer, on the **Cube** menu, click either **New Calculated Member**, **New Named Set**, or **New Script Command**, depending on the type of calculation you want to create.</span></span> <span data-ttu-id="8d98f-113">また、ツール バーで対応するいずれかのボタンをクリックするか、 **[スクリプト オーガナイザー]** ペイン内を右クリックし、ショートカット メニューのいずれかのコマンドをクリックすることもできます。</span><span class="sxs-lookup"><span data-stu-id="8d98f-113">You can also click any of the corresponding buttons on the toolbar, or right-click anywhere in the **Script Organizer** pane and then click one of the commands on the shortcut menu.</span></span> <span data-ttu-id="8d98f-114">この操作により、新しい計算が **[スクリプト オーガナイザー]** ペインに追加され、計算式ペインの計算フォームにそのフィールドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8d98f-114">This action adds a new calculation to the **Script Organizer** pane and displays fields for it in the calculations form in the Calculations Expressions pane.</span></span> <span data-ttu-id="8d98f-115">新しいスクリプトを作成すると、この操作により計算式ペインに [スクリプト ビュー] が開きます。</span><span class="sxs-lookup"><span data-stu-id="8d98f-115">If you create a new script, this action opens the Script view in the Calculation Expressions pane.</span></span> <span data-ttu-id="8d98f-116">3 種類の計算を作成する方法の詳細については、「 [計算されるメンバーの作成](create-calculated-members.md)」、「 [名前付きセットの作成](create-named-sets.md)」、および「 [割り当てとその他のスクリプト コマンドの定義](define-assignments-and-other-script-commands.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d98f-116">For more information about building the three types of calculations, see [Create Calculated Members](create-calculated-members.md), [Create Named Sets](create-named-sets.md), and [Define Assignments and Other Script Commands](define-assignments-and-other-script-commands.md).</span></span>  
  
## <a name="editing-scripts"></a><span data-ttu-id="8d98f-117">スクリプトの編集</span><span class="sxs-lookup"><span data-stu-id="8d98f-117">Editing Scripts</span></span>  
 <span data-ttu-id="8d98f-118">[**計算**] タブの計算式ペインでスクリプトを編集します。計算式ペインには、スクリプトビューとフォームビューの2つのビューがあります。</span><span class="sxs-lookup"><span data-stu-id="8d98f-118">Edit scripts in the Calculation Expressions pane of the **Calculations** tab. The Calculation Expressions pane has two views, Script view and Form view.</span></span> <span data-ttu-id="8d98f-119">フォーム ビューには、1 つのコマンドの式およびプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8d98f-119">The Form view shows the expressions and properties for a single command.</span></span> <span data-ttu-id="8d98f-120">MDX スクリプトを編集する場合、式ボックスがフォーム ビュー全体に表示されます。</span><span class="sxs-lookup"><span data-stu-id="8d98f-120">When you edit an MDX script, an expression box fills the entire Form view.</span></span>  
  
 <span data-ttu-id="8d98f-121">スクリプト ビューには、スクリプトを編集するためのコード エディターが用意されています。</span><span class="sxs-lookup"><span data-stu-id="8d98f-121">The Script view provides a code editor in which to edit the scripts.</span></span> <span data-ttu-id="8d98f-122">計算式ペインがスクリプト ビューにある場合、 **[スクリプト オーガナイザー]** ペインは表示されません。</span><span class="sxs-lookup"><span data-stu-id="8d98f-122">While the Calculation Expressions pane is in Script view, the **Script Organizer** pane is hidden.</span></span> <span data-ttu-id="8d98f-123">スクリプト ビューには、色分け表示、かっこの対応、オートコンプリート、MDX コード領域などの機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="8d98f-123">The Script view provides color coding, parenthesis matching, auto-complete, and MDX code regions.</span></span> <span data-ttu-id="8d98f-124">MDX コード領域は、編集しやすいように折りたたんだり展開したりできます。</span><span class="sxs-lookup"><span data-stu-id="8d98f-124">The MDX code regions can be collapsed or expanded to facilitate editing.</span></span>  
  
 <span data-ttu-id="8d98f-125">**[キューブ]** メニューをクリックし、 **[計算を表示]** をポイントして、 **[スクリプト]** または **[フォーム]** をクリックして、フォーム ビューとスクリプト ビューを切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="8d98f-125">You can switch between the Form view and the Script view by clicking the **Cube** menu, pointing to **Show Calculations in**, and then clicking **Script** or **Form**.</span></span> <span data-ttu-id="8d98f-126">また、ツール バーの **[フォーム ビュー]** または **[スクリプト ビュー]** をクリックすることもできます。</span><span class="sxs-lookup"><span data-stu-id="8d98f-126">You can also click either **Form view** or **Script view** on the toolbar.</span></span>  
  
## <a name="changing-solve-order"></a><span data-ttu-id="8d98f-127">解決順序の変更</span><span class="sxs-lookup"><span data-stu-id="8d98f-127">Changing Solve Order</span></span>  
 <span data-ttu-id="8d98f-128">計算は、 **[スクリプト オーガナイザー]** ペインに一覧表示されている順序で解決されます。</span><span class="sxs-lookup"><span data-stu-id="8d98f-128">Calculations are solved in the order listed in the **Script Organizer** pane.</span></span> <span data-ttu-id="8d98f-129">計算を右クリックし、ショートカット メニューの **[上へ移動]** または **[下へ移動]** をクリックして、計算の順序を変更できます。</span><span class="sxs-lookup"><span data-stu-id="8d98f-129">You can reorder the calculations by right-clicking any calculation and then clicking **Move Up** or **Move Down** on the shortcut menu.</span></span> <span data-ttu-id="8d98f-130">また、計算をクリックし、ツール バーの **[上へ移動]** ボタンまたは **[下へ移動]** ボタンをクリックすることもできます。</span><span class="sxs-lookup"><span data-stu-id="8d98f-130">You can also click a calculation and then click the **Move Up** or **Move Down** button on the toolbar.</span></span>  
  
 <span data-ttu-id="8d98f-131">計算されるセルおよび計算されるメンバーについて、この順序を手動でオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="8d98f-131">You can override this order manually for calculated cells and calculated members.</span></span> <span data-ttu-id="8d98f-132">パス順序と解決順序の詳細については、「[パス順序と解決順序の概要 (MDX)](mdx/mdx-data-manipulation-understanding-pass-order-and-solve-order.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d98f-132">For more information about pass order and solve order, see [Understanding Pass Order and Solve Order &#40;MDX&#41;](mdx/mdx-data-manipulation-understanding-pass-order-and-solve-order.md).</span></span>  
  
## <a name="deleting-a-calculation"></a><span data-ttu-id="8d98f-133">計算の削除</span><span class="sxs-lookup"><span data-stu-id="8d98f-133">Deleting a Calculation</span></span>  
 <span data-ttu-id="8d98f-134">既存の計算を削除するには、 **[スクリプト オーガナイザー]** ペインの **[計算]** タブで、削除する計算を選択し、 **[編集]** メニューの **[削除]** をクリックするか、ツール バーの **[削除]** アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8d98f-134">To delete an existing calculation, on the **Calculations** tab, in the **Script Organizer** pane, select the calculation to be deleted, and then click **Delete** on the **Edit** menu or click the **Delete** icon on the toolbar.</span></span> <span data-ttu-id="8d98f-135">また、 **[スクリプト オーガナイザー]** ペインで計算を右クリックし、ショートカット メニューから **[削除]** を選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="8d98f-135">You can also right-click the calculation in the **Script Organizer** pane and select **Delete** from the short-cut menu.</span></span>  
  
  
