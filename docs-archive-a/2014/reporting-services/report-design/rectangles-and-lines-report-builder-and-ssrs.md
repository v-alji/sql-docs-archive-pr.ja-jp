---
title: 四角形と線 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d6226b0c-0398-4185-8565-96099876fc21
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 96b795c3edeabb938e836be3486e28e08737a8e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644313"
---
# <a name="rectangles-and-lines-report-builder-and-ssrs"></a><span data-ttu-id="195b3-102">四角形と線 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="195b3-102">Rectangles and Lines (Report Builder and SSRS)</span></span>
  <span data-ttu-id="195b3-103">四角形と線は、レポートに視覚効果を与えることができます。</span><span class="sxs-lookup"><span data-stu-id="195b3-103">Rectangles and lines can create visual effects within a report.</span></span> <span data-ttu-id="195b3-104">[ホーム] タブの [罫線] セクションでこれらのレポート アイテムの表示プロパティを設定し、プロパティ ペインを使用してその他のプロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="195b3-104">You can set display properties on these report items from the Border section of the Home tab, and set other properties by using the Properties pane.</span></span> <span data-ttu-id="195b3-105">背景色、背景画像、ツールヒント、ブックマークなどの機能を、四角形に追加できます。</span><span class="sxs-lookup"><span data-stu-id="195b3-105">You can add features like a background color or image, a tooltip, or a bookmark to a rectangle.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="rectangles-and-lines-as-report-parts"></a><a name="RectanglesLinesReportParts"></a> <span data-ttu-id="195b3-106">レポート パーツとしての四角形と線</span><span class="sxs-lookup"><span data-stu-id="195b3-106">Rectangles and Lines as Report Parts</span></span>  
 <span data-ttu-id="195b3-107">四角形はその中にあるアイテムと共に、レポート パーツとしてレポートとは別にパブリッシュできます。</span><span class="sxs-lookup"><span data-stu-id="195b3-107">You can publish rectangles with the items that they contain separately from the report as report parts.</span></span> [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
 <span data-ttu-id="195b3-108">四角形内のレポート アイテムをレポート パーツとしてパブリッシュすることはできません。</span><span class="sxs-lookup"><span data-stu-id="195b3-108">You cannot publish the report items within the rectangle as report parts.</span></span> <span data-ttu-id="195b3-109">レポートに四角形を追加すると、その四角形と内部のアイテムを取得できます。</span><span class="sxs-lookup"><span data-stu-id="195b3-109">When people add the rectangle to a report, they get the rectangle and the items it contains.</span></span>  
  

  
##  <a name="using-a-rectangle-as-a-container"></a><a name="RectangleAsContainer"></a> <span data-ttu-id="195b3-110">コンテナーとしての四角形の使用</span><span class="sxs-lookup"><span data-stu-id="195b3-110">Using a Rectangle as a Container</span></span>  
 <span data-ttu-id="195b3-111">四角形は、他のアイテムのコンテナーとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="195b3-111">You can use a rectangle as a container for other items.</span></span> <span data-ttu-id="195b3-112">四角形を移動すると、四角形の中にあるアイテムも合わせて移動します。</span><span class="sxs-lookup"><span data-stu-id="195b3-112">When you move the rectangle, the items that are contained within the rectangle move along with it.</span></span> <span data-ttu-id="195b3-113">四角形の中にあるアイテムの **Parent** プロパティには、四角形の名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="195b3-113">An item within the rectangle shows the name of the rectangle in its **Parent** property.</span></span> <span data-ttu-id="195b3-114">四角形をコンテナーとして使用する方法については、「[四角形またはコンテナーの追加 &#40;レポート ビルダーおよび SSRS&#41;](add-a-rectangle-or-container-report-builder-and-ssrs.md)」および「[マトリックスとグラフでの同じデータの表示 &#40;レポート ビルダー&#41;](display-the-same-data-on-a-matrix-and-a-chart-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="195b3-114">For more information about using a rectangle as a container, see [Add a Rectangle or Container &#40;Report Builder and SSRS&#41;](add-a-rectangle-or-container-report-builder-and-ssrs.md) and [Display the Same Data on a Matrix and a Chart &#40;Report Builder&#41;](display-the-same-data-on-a-matrix-and-a-chart-report-builder.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="195b3-115">四角形はアイテムの単なるコンテナーで、アイテムを四角形内で作成するか四角形にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="195b3-115">A rectangle is only a container for items that you either create in the rectangle or drag into the rectangle.</span></span> <span data-ttu-id="195b3-116">デザイン画面に既に存在するアイテムの周囲に四角形を描画した場合、四角形はコンテナーとして機能しません。</span><span class="sxs-lookup"><span data-stu-id="195b3-116">If you draw a rectangle around an item that already exists on the design surface, the rectangle will not act as its container.</span></span> <span data-ttu-id="195b3-117">この四角形はアイテムの Parent プロパティに表示されません。</span><span class="sxs-lookup"><span data-stu-id="195b3-117">The rectangle will not be listed in the item's Parent property.</span></span>  
  
 <span data-ttu-id="195b3-118">四角形をレポート アイテムの格納に使用する場合は、レポートの表示中にアイテムが全体としてどのような影響を受けるかを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="195b3-118">When using rectangles to contain report items, consider how the items will be affected as a whole during report rendering.</span></span> <span data-ttu-id="195b3-119">繰り返されるデータ行を含むレポート アイテム (たとえばテーブル) は、クエリから返されたデータに合わせて展開されるので、四角形内の他のアイテムの位置に影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="195b3-119">Report items that contain repeated rows of data (for example, tables) will expand to accommodate the data that is returned by a query, and this affects the positioning of other items in the rectangle.</span></span> <span data-ttu-id="195b3-120">アイテムがテーブルのデータ領域よりも下に配置されると、このテーブルによりアイテムは押し下げられます。</span><span class="sxs-lookup"><span data-stu-id="195b3-120">A table will push items down if they are positioned below the data region.</span></span> <span data-ttu-id="195b3-121">同じ位置にアイテムを配置するには、テーブルの下枠より上に上の枠が来るように配置された四角形の内部にレポート アイテムを配置します。</span><span class="sxs-lookup"><span data-stu-id="195b3-121">To anchor an item in place, you can place the report item inside of a rectangle that has an upper edge above the lower edge of the table.</span></span> <span data-ttu-id="195b3-122">詳しくは、「[レンダリングの動作 &#40;レポート ビルダーおよび SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="195b3-122">For more information, see [Rendering Behaviors &#40;Report Builder  and SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="adding-a-report-border"></a><a name="ReportBorder"></a><span data-ttu-id="195b3-123">レポートの罫線の追加</span><span class="sxs-lookup"><span data-stu-id="195b3-123">Adding a Report Border</span></span>  
 <span data-ttu-id="195b3-124">線や四角形を追加せずに、ヘッダー、フッター、およびレポート本文自体に罫線を追加することで、レポートに罫線を追加できます。</span><span class="sxs-lookup"><span data-stu-id="195b3-124">You can add a border to a report by adding borders to the headers, footers, and report body themselves, without adding lines or rectangles.</span></span> <span data-ttu-id="195b3-125">詳細については、「 [レポートへの罫線の追加 &#40;レポート ビルダーおよび SSRS&#41;](add-a-border-to-a-report-report-builder-and-ssrs.md)の詳細を参照してください。</span><span class="sxs-lookup"><span data-stu-id="195b3-125">For more information, see [Add a Border to a Report &#40;Report Builder and SSRS&#41;](add-a-border-to-a-report-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="195b3-126">操作方法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="195b3-126">How-To Topics</span></span>  
 [<span data-ttu-id="195b3-127">レポートへの罫線の追加 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="195b3-127">Add a Border to a Report &#40;Report Builder and SSRS&#41;</span></span>](add-a-border-to-a-report-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="195b3-128">四角形またはコンテナーの追加 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="195b3-128">Add a Rectangle or Container &#40;Report Builder and SSRS&#41;</span></span>](add-a-rectangle-or-container-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="195b3-129">罫線の追加および変更 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="195b3-129">Add and Modify a Line &#40;Report Builder and SSRS&#41;</span></span>](add-and-modify-a-line-report-builder-and-ssrs.md)  
  
## <a name="see-also"></a><span data-ttu-id="195b3-130">参照</span><span class="sxs-lookup"><span data-stu-id="195b3-130">See Also</span></span>  
 [<span data-ttu-id="195b3-131">四角形またはコンテナーの追加 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="195b3-131">Add a Rectangle or Container &#40;Report Builder and SSRS&#41;</span></span>](add-a-rectangle-or-container-report-builder-and-ssrs.md)  
  
  
