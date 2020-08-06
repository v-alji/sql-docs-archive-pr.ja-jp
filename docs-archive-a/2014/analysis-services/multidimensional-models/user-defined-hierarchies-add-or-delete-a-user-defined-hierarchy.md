---
title: ユーザー定義階層を追加または削除する |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Analysis Services], adding
- removing hierarchies
- adding hierarchies
- deleting hierarchies
- hierarchies [Analysis Services], removing
ms.assetid: 953818b4-9543-4c01-bb20-1d45ec6dfb91
author: minewiskan
ms.author: owend
ms.openlocfilehash: d20404a1d93d57221eb830366392eb90600f26c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642355"
---
# <a name="add-or-delete-a-user-defined-hierarchy"></a><span data-ttu-id="7a820-102">ユーザー定義階層の追加または削除</span><span class="sxs-lookup"><span data-stu-id="7a820-102">Add or Delete a User-Defined Hierarchy</span></span>
  <span data-ttu-id="7a820-103">ディメンションでのユーザー定義階層の追加と削除は、 **のディメンション デザイナーにある** [ディメンション構造] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]タブで実行します。</span><span class="sxs-lookup"><span data-stu-id="7a820-103">You add a user-defined hierarchy to or remove a user-defined hierarchy from a dimension on the **Dimension Structure** tab in Dimension Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="7a820-104">ユーザー定義階層を追加した場合、この階層は [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスでインスタンス化され、ディメンションが処理されるまで、ユーザーが使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="7a820-104">When you add a user-defined hierarchy, it is not available to users until it is instantiated in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and the dimension is processed.</span></span> <span data-ttu-id="7a820-105">詳細については、「SSAS&#41;および[多次元モデルオブジェクト処理](processing-a-multidimensional-model-analysis-services.md)の[&#40;多次元モデルデータベース](multidimensional-model-databases-ssas.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a820-105">For more information, see [Multidimensional Model Databases &#40;SSAS&#41;](multidimensional-model-databases-ssas.md) and [Multidimensional Model Object Processing](processing-a-multidimensional-model-analysis-services.md).</span></span>  
  
### <a name="to-add-a-user-defined-hierarchy-to-a-dimension"></a><span data-ttu-id="7a820-106">ディメンションにユーザー定義階層を追加するには</span><span class="sxs-lookup"><span data-stu-id="7a820-106">To add a user-defined hierarchy to a dimension</span></span>  
  
1.  <span data-ttu-id="7a820-107">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、適切な [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを開き、作業するディメンションを開きます。</span><span class="sxs-lookup"><span data-stu-id="7a820-107">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the appropriate [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, and then open the dimension with which you want to work.</span></span>  
  
     <span data-ttu-id="7a820-108">ディメンションは、ディメンション デザイナーの **[ディメンション構造]** タブに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7a820-108">The dimension opens in Dimension Designer on the **Dimension Structure** tab.</span></span>  
  
2.  <span data-ttu-id="7a820-109">ユーザー定義階層で使用する属性を、 **[属性]** ペインから **[階層]** ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="7a820-109">From the **Attributes** pane, drag an attribute that you want to use in the user-defined hierarchy to the **Hierarchies** pane.</span></span>  
  
3.  <span data-ttu-id="7a820-110">追加の属性をドラッグして、ユーザー定義階層内にレベルを形成します。</span><span class="sxs-lookup"><span data-stu-id="7a820-110">Drag additional attributes to form levels in the user-defined hierarchy.</span></span>  
  
     <span data-ttu-id="7a820-111">階層内で属性が表示される順序は重要です。</span><span class="sxs-lookup"><span data-stu-id="7a820-111">The order in which attributes are listed in the hierarchy is important.</span></span> <span data-ttu-id="7a820-112">たとえば、時間階層では、階層の一覧で日よりも年が上に表示される必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a820-112">For example, in a time hierarchy, years should appear higher in the hierarchy list than days.</span></span>  
  
4.  <span data-ttu-id="7a820-113">必要に応じて、レベルを適切な位置にドラッグして、ユーザー定義階層内でレベルを再配置します。</span><span class="sxs-lookup"><span data-stu-id="7a820-113">Optionally, rearrange the levels in the user-defined hierarchy by dragging them to the correct positions.</span></span>  
  
5.  <span data-ttu-id="7a820-114">必要に応じて、ユーザー定義階層またはそのレベルのプロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="7a820-114">Optionally, modify properties of the user-defined hierarchy or its levels.</span></span>  
  
     <span data-ttu-id="7a820-115">たとえば、ユーザー定義階層の名前を指定したり、その階層の 1 つ以上のレベルの名前を変更したり、All レベルのカスタム名を定義したりできます。</span><span class="sxs-lookup"><span data-stu-id="7a820-115">For example, you might want to specify a name for the user-defined hierarchy, rename one or more of its levels, and define a custom name for the All level.</span></span> <span data-ttu-id="7a820-116">詳細については、「[ユーザー階層のプロパティ](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)」および「[レベルのプロパティ &#91;準備中 Over&#93;](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a820-116">For more information, see [User Hierarchy Properties](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md), and [Level Properties &#91;Paved Over&#93;](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7a820-117">既定では、ユーザー定義階層は単なるパスです。これにより、ユーザーは情報をドリル ダウンできます。</span><span class="sxs-lookup"><span data-stu-id="7a820-117">By default, a user-defined hierarchy is just a path that enables users to drill down for information.</span></span> <span data-ttu-id="7a820-118">ただし、レベル間にリレーションシップが存在する場合は、レベル間の属性リレーションシップを構成することにより、クエリ パフォーマンスを向上できます。</span><span class="sxs-lookup"><span data-stu-id="7a820-118">However, if relationships exist between levels, you can increase query performance by configuring attribute relationships between levels.</span></span> <span data-ttu-id="7a820-119">詳細については、「 [属性リレーションシップ](../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md) 」および「 [属性リレーションシップの定義](attribute-relationships-define.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a820-119">For more information, see [Attribute Relationships](../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md) and [Define Attribute Relationships](attribute-relationships-define.md).</span></span>  
  
### <a name="to-remove-a-user-defined-hierarchy-from-a-dimension"></a><span data-ttu-id="7a820-120">ディメンションからユーザー定義階層を削除するには</span><span class="sxs-lookup"><span data-stu-id="7a820-120">To remove a user-defined hierarchy from a dimension</span></span>  
  
-   <span data-ttu-id="7a820-121">**[ディメンション構造]** タブの **[階層]** ペインで、削除するユーザー定義階層をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a820-121">On the **Dimension Structure** tab, click the user-defined hierarchy that you want to remove in the **Hierarchies** pane.</span></span> <span data-ttu-id="7a820-122">ツール バーの **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a820-122">On the toolbar, click **Delete**.</span></span>  
  
     - <span data-ttu-id="7a820-123">または</span><span class="sxs-lookup"><span data-stu-id="7a820-123">or -</span></span>  
  
-   <span data-ttu-id="7a820-124">**[階層]** ペインで、削除するユーザー定義階層を右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a820-124">Right-click the user-defined hierarchy that you want to remove in the **Hierarchies** pane and then click **Delete**.</span></span>  
  
     - <span data-ttu-id="7a820-125">または</span><span class="sxs-lookup"><span data-stu-id="7a820-125">or -</span></span>  
  
-   <span data-ttu-id="7a820-126">ユーザー定義階層をデザイン画面外にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="7a820-126">Drag the user-defined hierarchy off of the design surface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a820-127">参照</span><span class="sxs-lookup"><span data-stu-id="7a820-127">See Also</span></span>  
 <span data-ttu-id="7a820-128">[ユーザー階層](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="7a820-128">[User Hierarchies](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md) </span></span>  
 [<span data-ttu-id="7a820-129">ユーザー定義階層の作成</span><span class="sxs-lookup"><span data-stu-id="7a820-129">Create User-Defined Hierarchies</span></span>](user-defined-hierarchies-create.md)  
  
  
