---
title: インジケーターの追加または削除 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a8b1aac1-53ef-47a4-afc0-8fa866c6c480
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 186ed4f5b6cf7cb239dc7c33a11089c11bccae14
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719599"
---
# <a name="add-or-delete-an-indicator-report-builder-and-ssrs"></a><span data-ttu-id="54b41-102">インジケーターの追加または削除 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="54b41-102">Add or Delete an Indicator (Report Builder and SSRS)</span></span>
  <span data-ttu-id="54b41-103">インジケーターは、1 つのデータ値の状態をひとめでわかるようにするための小さなゲージです。</span><span class="sxs-lookup"><span data-stu-id="54b41-103">Indicators are minimal gauges that convey the state of a single data value at a glance.</span></span> <span data-ttu-id="54b41-104">詳細については、「 [インジケーター (レポート ビルダーおよび SSRS)](indicators-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54b41-104">For more information about them, see [Indicators &#40;Report Builder and SSRS&#41;](indicators-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="54b41-105">通常、インジケーターはテーブルまたはマトリックス内のセルに置かれますが、単独で使用したり、ゲージと並べて使用したり、ゲージに埋め込むこともできます。</span><span class="sxs-lookup"><span data-stu-id="54b41-105">Indicators are commonly placed in cells in a table or matrix, but you can also use indicators by themselves, side-by-side with gauges, or embedded in gauges.</span></span>  
  
 <span data-ttu-id="54b41-106">インジケーターを最初に追加すると、既定では測定単位としてパーセンテージを使用するように構成されます。</span><span class="sxs-lookup"><span data-stu-id="54b41-106">When you first add an indicator, it is by default configured to use percentages as measurement units.</span></span> <span data-ttu-id="54b41-107">パーセンテージの範囲は、インジケーター セットのメンバー間に均等に配分されます。テーブルやマトリックスなど、インジケーターの親が、インジケーターによって表示される値のスコープです。</span><span class="sxs-lookup"><span data-stu-id="54b41-107">The percentage ranges are evenly distributed across members of the indicator set, and the scope of values shown by the indicator is the parent of the indicator such as a table or matrix.</span></span>  
  
 <span data-ttu-id="54b41-108">インジケーターの値および状態は、更新することができます。</span><span class="sxs-lookup"><span data-stu-id="54b41-108">You can update the values and states of indicators.</span></span> <span data-ttu-id="54b41-109">詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="54b41-109">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="54b41-110">インジケーター アイコンとインジケーター セットの変更 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="54b41-110">Change Indicator Icons and Indicator Sets &#40;Report Builder and SSRS&#41;</span></span>](change-indicator-icons-and-indicator-sets-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="54b41-111">測定単位の設定および構成 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="54b41-111">Set and Configure Measurement Units &#40;Report Builder and SSRS&#41;</span></span>](set-and-configure-measurement-units-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="54b41-112">同期スコープの設定 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="54b41-112">Set Synchronization Scope &#40;Report Builder and SSRS&#41;</span></span>](set-synchronization-scope-report-builder-and-ssrs.md)  
  
 <span data-ttu-id="54b41-113">インジケーターは、ゲージ パネル内に配置されるため、 **[インジケーターのプロパティ]** ダイアログ ボックスまたは **プロパティ** ペインを使用してインジケーターを構成するには、パネルの代わりにインジケーターを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="54b41-113">Because an indicator is positioned inside the gauge panel, you need to select the indicator instead of the panel when you want to configure the indicator by using the **Indicators Properties** dialog box or the **Properties** pane.</span></span> <span data-ttu-id="54b41-114">次の図は、ゲージ パネルで選択されたインジケーターを示します。</span><span class="sxs-lookup"><span data-stu-id="54b41-114">The following picture shows a selected indicator in its gauge panel.</span></span>  
  
 <span data-ttu-id="54b41-115">![rs_GaugePanelWithIndicator](../media/rs-gaugepanelwithindicator.gif "rs_GaugePanelWithIndicator")</span><span class="sxs-lookup"><span data-stu-id="54b41-115">![rs_GaugePanelWithIndicator](../media/rs-gaugepanelwithindicator.gif "rs_GaugePanelWithIndicator")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="54b41-116">列の幅とデータ値の長さにより、テーブル内またはマトリックス セル内のテキストは、折り返されて複数行に表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="54b41-116">Depending on column width and the length of data values, the text in table or matrix cells might wrap and display text on multiple lines.</span></span> <span data-ttu-id="54b41-117">そのような場合、インジケーター アイコンが引き伸ばされて形が変わる場合があります。</span><span class="sxs-lookup"><span data-stu-id="54b41-117">When this occurs, the indicator icon might be stretched and change shape.</span></span> <span data-ttu-id="54b41-118">これにより、インジケーター アイコンが読みにくくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="54b41-118">This can make the indicator icon less readable.</span></span> <span data-ttu-id="54b41-119">インジケーターは、四角形の中に配置し、アイコンが引き伸ばされないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="54b41-119">Place the indicator inside a rectangle to ensure that the icon is never stretched.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-an-indicator-to-a-table-or-matrix"></a><span data-ttu-id="54b41-120">テーブルまたはマトリックスにインジケーターを追加するには</span><span class="sxs-lookup"><span data-stu-id="54b41-120">To add an indicator to a table or matrix</span></span>  
  
1.  <span data-ttu-id="54b41-121">表示するデータのテーブルおよびマトリックスが含まれる既存のレポートを開くか、新しいレポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="54b41-121">Open an existing report or create a new report that contains a table and matrix with the data you want to display.</span></span> <span data-ttu-id="54b41-122">詳細については、「[(レポート ビルダーおよび SSRS)](tables-report-builder-and-ssrs.md)」または「[マトリックス (レポート ビルダーおよび SSRS)](create-a-matrix-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54b41-122">For more information, see [Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) or [Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="54b41-123">テーブルまたはマトリックスに列を挿入します。</span><span class="sxs-lookup"><span data-stu-id="54b41-123">Insert a column in your table or matrix.</span></span> <span data-ttu-id="54b41-124">詳細については、「[列の挿入または削除 &#40;レポート ビルダーおよび SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54b41-124">For more information, see [Insert or Delete a Column &#40;Report Builder and SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md).</span></span>  
  
3.  <span data-ttu-id="54b41-125">必要に応じて、 **[挿入]** タブで **[四角形]** をクリックし、新しい列のセルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="54b41-125">Optionally, on the **Insert** tab, click **Rectangle**, and then click a cell in the new column.</span></span>  
  
4.  <span data-ttu-id="54b41-126">**[挿入]** タブで、 **[インジケーター]** をクリックし、新しい列のセルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="54b41-126">On the **Insert** tab, click **Indicator**, and then click a cell in the new column.</span></span>  
  
     <span data-ttu-id="54b41-127">セルに四角形を追加した場合は、そのセルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="54b41-127">If you added a rectangle to a cell, click that cell.</span></span>  
  
5.  <span data-ttu-id="54b41-128">左側のペインの **[インジケーター スタイルの選択]** ダイアログ ボックスで、目的のインジケーター タイプをクリックし、インジケーター セットをクリックします。</span><span class="sxs-lookup"><span data-stu-id="54b41-128">In the **Select Indicator Style** dialog box, in the left pane, click the indicator type you want, and then click the indicator set.</span></span>  
  
6.  <span data-ttu-id="54b41-129">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="54b41-129">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="54b41-130">インジケーターをクリックします。</span><span class="sxs-lookup"><span data-stu-id="54b41-130">Click the indicator.</span></span> <span data-ttu-id="54b41-131">**ゲージ データ** ペインが開きます。</span><span class="sxs-lookup"><span data-stu-id="54b41-131">The **Gauge Data** pane opens.</span></span>  
  
8.  <span data-ttu-id="54b41-132">**[値]** 領域の **[(未指定)]** ドロップダウン リストで、インジケーターとして値を表示するフィールドをクリックします。</span><span class="sxs-lookup"><span data-stu-id="54b41-132">In the **Values** area, in the **(Unspecified)** drop-down list, click the field whose values you want to display as an indicator.</span></span>  
  
     <span data-ttu-id="54b41-133">インジケーターは既定値を使用するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="54b41-133">The indicator is configured to use default values.</span></span> <span data-ttu-id="54b41-134">既定では、インジケーターは測定単位としてパーセンテージを使用するように構成されており、パーセンテージの範囲は、インジケーターのメンバー間に均等に配分されます。インジケーターが示す値には、最も近いグループのスコープが使用されます。</span><span class="sxs-lookup"><span data-stu-id="54b41-134">By default, indicators are configured use percentages as measurement units and the percentage ranges are evenly distributed across the members of the indicator and the value that the indicator conveys uses the scope of the nearest group.</span></span>  
  
### <a name="to-delete-an-indicator-to-a-table-or-matrix"></a><span data-ttu-id="54b41-135">テーブルまたはマトリックスからインジケーターを削除するには</span><span class="sxs-lookup"><span data-stu-id="54b41-135">To delete an indicator to a table or matrix</span></span>  
  
1.  <span data-ttu-id="54b41-136">削除するインジケーターを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="54b41-136">Right-click the indicator to delete and click **Delete**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="54b41-137">インジケーターは、他のインジケーターまたはゲージを含むゲージ パネル内に配置されている場合があります。</span><span class="sxs-lookup"><span data-stu-id="54b41-137">An indicator might be positioned inside a gauge panel that contains other indicators or gauges.</span></span> <span data-ttu-id="54b41-138">ゲージ パネルに複数の項目が含まれている場合は、ゲージ パネルではなく、削除するインジケーターをクリックするよう注意してください。</span><span class="sxs-lookup"><span data-stu-id="54b41-138">If the gauge panels contain multiple items, be sure to click the indicator to delete it, not the gauge panel.</span></span> <span data-ttu-id="54b41-139">ゲージ パネルをクリックして削除すると、ゲージ パネルだけでなく、その中の項目がすべて削除されます。</span><span class="sxs-lookup"><span data-stu-id="54b41-139">If you click and then delete the gauge panel, the gauge panels and all the items in it are deleted.</span></span>  
  
2.  <span data-ttu-id="54b41-140">**[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="54b41-140">Click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54b41-141">参照</span><span class="sxs-lookup"><span data-stu-id="54b41-141">See Also</span></span>  
 [<span data-ttu-id="54b41-142">インジケーター &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="54b41-142">Indicators &#40;Report Builder and SSRS&#41;</span></span>](indicators-report-builder-and-ssrs.md)  
  
  
