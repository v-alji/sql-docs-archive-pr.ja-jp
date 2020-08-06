---
title: キューブの参照 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 3819946e-d3fa-4c1d-afe3-599c938b1b2e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7cbf35866bb0a1f65074a7e106ecf556e98aa30b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631276"
---
# <a name="browsing-the-cube"></a><span data-ttu-id="86773-102">キューブの表示</span><span class="sxs-lookup"><span data-stu-id="86773-102">Browsing the Cube</span></span>
  <span data-ttu-id="86773-103">キューブを配置すると、キューブ デザイナーの **[ブラウザー]** タブにキューブ データが表示され、ディメンション デザイナーの **[ブラウザー]** タブにディメンション データが表示されます。</span><span class="sxs-lookup"><span data-stu-id="86773-103">After you deploy a cube, the cube data is viewable on the **Browser** tab in Cube Designer, and the dimension data is viewable on the **Browser** tab in Dimension Designer.</span></span> <span data-ttu-id="86773-104">キューブ データとディメンション データを参照すると、作業を段階的に確認できます。</span><span class="sxs-lookup"><span data-stu-id="86773-104">Browsing cube and dimension data is way to check your work incrementally.</span></span> <span data-ttu-id="86773-105">プロパティ、リレーションシップ、およびその他のオブジェクトに対する細かい変更が、それらのオブジェクトの処理後に期待どおりの効果をもたらしていることを検証できます。</span><span class="sxs-lookup"><span data-stu-id="86773-105">You can verify that small changes to properties, relationships, and other objects have the desired effect once the object is processed.</span></span> <span data-ttu-id="86773-106">[ブラウザー] タブはキューブ データとディメンション データの両方を表示するために使用されますが、参照するオブジェクトに応じて異なる機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="86773-106">While the Browser tab is used to view both cube and dimension data, the tab provides different capabilities based on the object you are browsing.</span></span>  
  
 <span data-ttu-id="86773-107">ディメンションの場合は、メンバーを表示したり、階層内をリーフ ノードまで移動したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="86773-107">For dimensions, the Browser tab provides a way to view members or navigate a hierarchy all the way down to the leaf node.</span></span> <span data-ttu-id="86773-108">モデルに翻訳を追加すると、ディメンション データを別の言語で参照できます。</span><span class="sxs-lookup"><span data-stu-id="86773-108">You can browse dimension data in different languages, assuming you have added the translations to your model.</span></span>  
  
 <span data-ttu-id="86773-109">キューブの場合は、データを探索するための 2 つの方法が [ブラウザー] タブに用意されています。</span><span class="sxs-lookup"><span data-stu-id="86773-109">For cubes, the Browser tab provides two approaches for exploring data.</span></span> <span data-ttu-id="86773-110">組み込みの MDX クエリ デザイナーを使用して、多次元データベースからフラット化行セットを返すクエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="86773-110">You can use the built-in MDX Query Designer to build queries that return a flattened rowset from a multidimensional database.</span></span> <span data-ttu-id="86773-111">または、Excel のショートカットを使用してもかまいません。</span><span class="sxs-lookup"><span data-stu-id="86773-111">Alternatively, you can use an Excel shortcut.</span></span> <span data-ttu-id="86773-112">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]内から Excel を起動する場合、既にピボットテーブルがあるワークシートと、モデル ワークスペース データベースへの定義済みの接続が含まれている状態で Excel が開かれます。</span><span class="sxs-lookup"><span data-stu-id="86773-112">When you start Excel from within [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], Excel opens with a PivotTable already in the worksheet and a predefined connection to the model workspace database.</span></span>  
  
 <span data-ttu-id="86773-113">横軸と縦軸を使用して対話的にキューブ データを探索し、データのリレーションシップを分析できるため、通常は Excel での参照の方が便利です。</span><span class="sxs-lookup"><span data-stu-id="86773-113">Excel generally offers a better browsing experience because you can explore cube data interactively, using horizontal and vertical axes to analyze the relationships in your data.</span></span> <span data-ttu-id="86773-114">一方、MDX クエリ デザイナーは、1 つの軸に制限されます。</span><span class="sxs-lookup"><span data-stu-id="86773-114">In contrast, the MDX Query Designer is limited to a single axis.</span></span> <span data-ttu-id="86773-115">また、行セットがフラット化されるため、Excel のピボットテーブルでは可能なドリルダウンができません。</span><span class="sxs-lookup"><span data-stu-id="86773-115">Moreover, because the rowset is flattened, you do not get the drilldown that an Excel PivotTable provides.</span></span> <span data-ttu-id="86773-116">この後のレッスンで行うように、キューブにディメンションや階層を追加する場合は、データを参照するためのソリューションとしては Excel の方が適しています。</span><span class="sxs-lookup"><span data-stu-id="86773-116">As you add more dimensions and hierarchies to your cube, which you will do in subsequent lessons, Excel will be the preferred solution for browsing data.</span></span>  
  
### <a name="to-browse-the-deployed-cube"></a><span data-ttu-id="86773-117">配置したキューブを表示するには</span><span class="sxs-lookup"><span data-stu-id="86773-117">To browse the deployed cube</span></span>  
  
1.  <span data-ttu-id="86773-118">**で、Product ディメンションの** ディメンション デザイナー [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="86773-118">Switch to **Dimension Designer** for the Product dimension in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="86773-119">これを行うには、ソリューション エクスプローラーの **[ディメンション]** ノードで **[Product]** ディメンションをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="86773-119">To do this, double-click the **Product** dimension in the **Dimensions** node of Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="86773-120">[**ブラウザー** ] タブをクリックして、属性階層の**All**メンバーを表示し `Product Key` ます。</span><span class="sxs-lookup"><span data-stu-id="86773-120">Click the **Browser** tab to display the **All** member of the `Product Key` attribute hierarchy.</span></span> <span data-ttu-id="86773-121">レッスン 3 では、Product ディメンションのユーザー階層を定義し、ディメンションを参照できるようにします。</span><span class="sxs-lookup"><span data-stu-id="86773-121">In lesson three, you will define a user hierarchy for the Product dimension that will let you browse the dimension.</span></span>  
  
3.  <span data-ttu-id="86773-122">**で** キューブ デザイナー [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="86773-122">Switch to **Cube Designer** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="86773-123">これを行うには、ソリューション エクスプローラーの **[キューブ]** ノードで **[Analysis Services Tutorial]** キューブをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="86773-123">To do this, double-click the **Analysis Services Tutorial** cube in the **Cubes** node of Solution Explorer.</span></span>  
  
4.  <span data-ttu-id="86773-124">**[ブラウザー]** タブをクリックし、キューブ デザイナーのツール バーにある **[再接続]** アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="86773-124">Select the **Browser** tab, and then click the **Reconnect** icon on the toolbar of the designer.</span></span>  
  
     <span data-ttu-id="86773-125">キューブ デザイナーの左側のペインには、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブのオブジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="86773-125">The left pane of the designer shows the objects in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span> <span data-ttu-id="86773-126">**[ブラウザー]** タブの右側には、2 つのペインが表示されます。上は **フィルター** ペイン、下は **データ** ペインです。</span><span class="sxs-lookup"><span data-stu-id="86773-126">On the right side of the **Browser** tab, there are two panes: the upper pane is the **Filter** pane, and the lower pane is the **Data** pane.</span></span> <span data-ttu-id="86773-127">次のレッスンでは、キューブ ブラウザーを使用して分析を行います。</span><span class="sxs-lookup"><span data-stu-id="86773-127">In an upcoming lesson, you will use the cube browser to do analysis.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="86773-128">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="86773-128">Next Lesson</span></span>  
 [<span data-ttu-id="86773-129">レッスン 3:メジャー、属性、および階層の修正</span><span class="sxs-lookup"><span data-stu-id="86773-129">Lesson 3: Modifying Measures, Attributes and Hierarchies</span></span>](lesson-3-modifying-measures-attributes-and-hierarchies.md)  
  
## <a name="see-also"></a><span data-ttu-id="86773-130">参照</span><span class="sxs-lookup"><span data-stu-id="86773-130">See Also</span></span>  
 [<span data-ttu-id="86773-131">MDX クエリ エディター &#40;Analysis Services - 多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="86773-131">MDX Query Editor &#40;Analysis Services - Multidimensional Data&#41;</span></span>](mdx-query-editor-analysis-services-multidimensional-data.md)  
  
  
