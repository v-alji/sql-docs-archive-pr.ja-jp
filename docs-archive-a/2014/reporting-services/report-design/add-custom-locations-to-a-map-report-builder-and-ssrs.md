---
title: カスタムの場所のマップへの追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- MICROSOFT.REPORTDESIGNER.MAPPOINT.POINTTEMPLATE
ms.assetid: 7d36faae-5bcc-446a-9eba-f42349cafacb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 167558534280f08d576205b5ff1b94d0588fcb78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738004"
---
# <a name="add-custom-locations-to-a-map-report-builder-and-ssrs"></a><span data-ttu-id="bc975-102">カスタムの場所のマップへの追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="bc975-102">Add Custom Locations to a Map (Report Builder and SSRS)</span></span>
  <span data-ttu-id="bc975-103">マップをレポートに追加した後、ポイントの場所を独自に追加できます。</span><span class="sxs-lookup"><span data-stu-id="bc975-103">After you add a map to a report, you can add your own point locations.</span></span>  
  
 <span data-ttu-id="bc975-104">レイヤー上のすべてのポイントの表示プロパティは、レイヤーのポイント プロパティのオプションを設定することで制御できます。</span><span class="sxs-lookup"><span data-stu-id="bc975-104">Display properties for all points on a layer are controlled by setting options for the point properties for the layer.</span></span> <span data-ttu-id="bc975-105">選択した埋め込みポイントの表示プロパティをオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="bc975-105">For a selected embedded point, you can override the display properties.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bc975-106">埋め込みポイントのレイヤー表示プロパティをオーバーライドした場合、加えた変更を元に戻すことはできません。</span><span class="sxs-lookup"><span data-stu-id="bc975-106">When you override the layer display properties for the embedded point, the changes that you make are not reversible.</span></span>  
  
 <span data-ttu-id="bc975-107">詳細については、「 [ルールおよび分析データを使用した多角形、線、およびポイントの表示の変更 &#40;レポート ビルダーおよび SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc975-107">For more information, see [Vary Polygon, Line, and Point Display by Rules and Analytical Data &#40;Report Builder and SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-point-layer"></a><span data-ttu-id="bc975-108">ポイント レイヤーを追加するには</span><span class="sxs-lookup"><span data-stu-id="bc975-108">To add a point layer</span></span>  
  
1.  <span data-ttu-id="bc975-109">レポート デザイン画面で、マップをクリックして選択し、マップ ペインを表示します。</span><span class="sxs-lookup"><span data-stu-id="bc975-109">On the report design surface, click the map to select it and display the Map pane.</span></span>  
  
2.  <span data-ttu-id="bc975-110">ツール バーの **[レイヤーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc975-110">On the toolbar, click **Add Layer**.</span></span>  
  
3.  <span data-ttu-id="bc975-111">ボックスの一覧から、 **[ポイント レイヤーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc975-111">From the drop-down list, click **Add Point Layer**.</span></span> <span data-ttu-id="bc975-112">ポイントが定義されていないポイント レイヤーがマップに追加されます。</span><span class="sxs-lookup"><span data-stu-id="bc975-112">A point layer with no points is added to the map.</span></span> <span data-ttu-id="bc975-113">既定では、ポイント レイヤーは埋め込みポイントに対応します。</span><span class="sxs-lookup"><span data-stu-id="bc975-113">By default, the point layer is ready for embedded points.</span></span>  
  
### <a name="to-add-a-custom-point"></a><span data-ttu-id="bc975-114">カスタム ポイントを追加するには</span><span class="sxs-lookup"><span data-stu-id="bc975-114">To add a custom point</span></span>  
  
1.  <span data-ttu-id="bc975-115">レポート デザイン画面で、マップをクリックして選択し、マップ ペインを表示します。</span><span class="sxs-lookup"><span data-stu-id="bc975-115">On the report design surface, click the map to select it and display the Map pane.</span></span>  
  
2.  <span data-ttu-id="bc975-116">マップ ペインで、種類が **[埋め込み]** のポイント レイヤーを右クリックし、 **[ポイントの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc975-116">In the Map pane, right-click a point layer that has type **Embedded**, and then click **Add Point**.</span></span> <span data-ttu-id="bc975-117">カーソルが十字に変化します。</span><span class="sxs-lookup"><span data-stu-id="bc975-117">The cursor changes to crosshairs.</span></span>  
  
3.  <span data-ttu-id="bc975-118">ポイントの追加先として、マップ上の場所をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc975-118">To add a point, click a location on the map.</span></span> <span data-ttu-id="bc975-119">選択したレイヤー上のクリックした場所に、埋め込みポイントが追加されます。</span><span class="sxs-lookup"><span data-stu-id="bc975-119">An embedded point is added to the selected layer at the location where you click.</span></span>  
  
### <a name="to-customize-the-display-for-an-embedded-point"></a><span data-ttu-id="bc975-120">埋め込みポイントの表示をカスタマイズするには</span><span class="sxs-lookup"><span data-stu-id="bc975-120">To customize the display for an embedded point</span></span>  
  
1.  <span data-ttu-id="bc975-121">ポイントを右クリックし、 **[ポイントのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc975-121">Right-click the point, and then click **Point Properties**.</span></span> <span data-ttu-id="bc975-122">**[マップの埋め込みポイントのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc975-122">The **Map Embedded Point Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="bc975-123">**[このレイヤーのポイント オプションをオーバーライドする]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc975-123">Click **Override point options for this layer**.</span></span> <span data-ttu-id="bc975-124">左ペインに複数のプロパティ ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc975-124">Multiple property pages appear in the left pane.</span></span>  
  
3.  <span data-ttu-id="bc975-125">ページをクリックし、このポイントに適用する表示プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="bc975-125">Click the pages and set the display properties that you want to apply to this point.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc975-126">参照</span><span class="sxs-lookup"><span data-stu-id="bc975-126">See Also</span></span>  
 <span data-ttu-id="bc975-127">[マップ &#40;レポート ビルダーおよび SSRS&#41;](maps-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="bc975-127">[Maps &#40;Report Builder and SSRS&#41;](maps-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="bc975-128">ルールおよび分析データを使用した多角形、線、およびポイントの表示の変更 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="bc975-128">Vary Polygon, Line, and Point Display by Rules and Analytical Data &#40;Report Builder and SSRS&#41;</span></span>](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)  
  
  
