---
title: ゲージ パネルへのインジケーターとゲージの配置 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4dff9b67-b483-4c51-a822-6dbe706a6840
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b1107745f54cd94abd7507a3e9b5a706ca5402de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739367"
---
# <a name="include-indicators-and-gauges-in-a-gauge-panel-report-builder-and-ssrs"></a><span data-ttu-id="9a1f3-102">ゲージ パネルへのインジケーターとゲージの配置 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="9a1f3-102">Include Indicators and Gauges in a Gauge Panel (Report Builder and SSRS)</span></span>
  <span data-ttu-id="9a1f3-103">ゲージ パネルは、1 つ以上のゲージとインジケーターを格納する最上位のコンテナーです。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-103">The gauge panel is the top-level container that holds one or more gauges and indicators.</span></span> <span data-ttu-id="9a1f3-104">インジケーターは、ゲージに埋め込んだり、ゲージ パネルのゲージの横に配置したりできます。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-104">Indicators can be embedded in gauges or placed next to them in the gauge panel.</span></span>  
  
 <span data-ttu-id="9a1f3-105">ゲージ パネルでインジケーターとゲージが隣接し、異なるフィールドのデータを表示している場合は、ゲージとインジケーターのデータを区別しやすいようにラベルを追加することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-105">If the indicator and gauge are adjacent in the gauge panel and show data from different fields, you might want to add labels to make it clear what data the gauge and indicator convey.</span></span>  
  
 <span data-ttu-id="9a1f3-106">ゲージとインジケーターのオプションは、式を使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-106">Gauge and indicator options can be set by using expressions.</span></span> <span data-ttu-id="9a1f3-107">詳細については、「[式 (レポート ビルダーおよび SSRS)](expressions-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-107">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-embed-an-indicator-in-a-gauge"></a><span data-ttu-id="9a1f3-108">ゲージにインジケーターを埋め込むには</span><span class="sxs-lookup"><span data-stu-id="9a1f3-108">To embed an indicator in a gauge</span></span>  
  
1.  <span data-ttu-id="9a1f3-109">表示するデータのテーブルおよびマトリックスが含まれる既存のレポートを開くか、新しいレポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-109">Open an existing report or create a new report that contains a table and matrix with the data you want to display.</span></span> <span data-ttu-id="9a1f3-110">詳細については、「[(レポート ビルダーおよび SSRS)](tables-report-builder-and-ssrs.md)」または「[マトリックス (レポート ビルダーおよび SSRS)](create-a-matrix-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-110">For more information, see [Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) or [Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="9a1f3-111">テーブルまたはマトリックスに列を挿入します。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-111">Insert a column in your table or matrix.</span></span> <span data-ttu-id="9a1f3-112">詳細については、「[列の挿入または削除 &#40;レポート ビルダーおよび SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-112">For more information, see [Insert or Delete a Column &#40;Report Builder and SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md).</span></span>  
  
3.  <span data-ttu-id="9a1f3-113">**[挿入]** タブの **[データ領域]** グループで **[ゲージ]** をクリックし、次に新しい列のセルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-113">On the **Insert** tab, in the **Data Regions** group, click **Gauge**, and then, and then click a cell in the new column.</span></span> <span data-ttu-id="9a1f3-114">**[ゲージの種類の選択]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-114">The **Select Gauge Type** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="9a1f3-115">**[放射状]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-115">Click **Radial**.</span></span> <span data-ttu-id="9a1f3-116">最初の放射状ゲージが選択されます。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-116">The first radial gauge is selected.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="9a1f3-117">ゲージをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-117">Click the gauge.</span></span> <span data-ttu-id="9a1f3-118">**ゲージ データ** ペインが開きます。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-118">The **Gauge Data** pane opens.</span></span>  
  
7.  <span data-ttu-id="9a1f3-119">**[値]** 領域の **[(未指定)]** ボックスの一覧で、ゲージに値を表示するフィールドをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-119">In the **Values** area, in the **(Unspecified)** list box, click the field whose values you want to display in the gauge.</span></span> <span data-ttu-id="9a1f3-120">または、使用するフィールドをレポート データセットからドラッグします。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-120">Alternatively, drag the field to use from the report dataset.</span></span>  
  
8.  <span data-ttu-id="9a1f3-121">ゲージを右クリックし、 **[インジケーターの追加]** をクリックして、 **[子]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-121">Right-click the gauge, click **Add Indicator**, and then click **Child**.</span></span> <span data-ttu-id="9a1f3-122">**[インジケーター スタイルの選択]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-122">The **Select Indicator Style** dialog box opens.</span></span>  
  
9. <span data-ttu-id="9a1f3-123">左側のペインの **[インジケーター スタイルの選択]** ダイアログ ボックスで、目的のインジケーター タイプをクリックし、インジケーター セットをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-123">In the **Select Indicator Style** dialog box, in the left pane, click the indicator type you want, and then click the indicator set.</span></span>  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
11. <span data-ttu-id="9a1f3-124">インジケーターをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-124">Click the indicator.</span></span> <span data-ttu-id="9a1f3-125">**ゲージ データ** ペインが開きます。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-125">The **Gauge Data** pane opens.</span></span>  
  
12. <span data-ttu-id="9a1f3-126">**[値]** 領域の **[(未指定)]** ボックスの一覧で、インジケーターとして値を表示するフィールドをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-126">In the **Values** area, in the **(Unspecified)** list box, click the field whose values you want to display as an indicator.</span></span> <span data-ttu-id="9a1f3-127">または、使用するフィールドをレポート データセットからドラッグします。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-127">Alternatively, drag the field to use from the report dataset.</span></span>  
  
     <span data-ttu-id="9a1f3-128">このフィールドは、ゲージで使用するフィールドと同じでも別でもかまいません。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-128">The field can be the same or a different field from the one you use in the gauge.</span></span>  
  
13. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-show-an-indicator-and-gauge-side-by-side"></a><span data-ttu-id="9a1f3-129">インジケーターとゲージを並べて表示するには</span><span class="sxs-lookup"><span data-stu-id="9a1f3-129">To show an indicator and gauge side by side</span></span>  
  
1.  <span data-ttu-id="9a1f3-130">表示するデータのテーブルおよびマトリックスが含まれる既存のレポートを開くか、新しいレポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-130">Open an existing report or create a new report that contains a table and matrix with the data you want to display.</span></span> <span data-ttu-id="9a1f3-131">詳細については、「[(レポート ビルダーおよび SSRS)](tables-report-builder-and-ssrs.md)」または「[マトリックス (レポート ビルダーおよび SSRS)](create-a-matrix-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-131">For more information, see [Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) or [Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="9a1f3-132">テーブルまたはマトリックスに列を挿入します。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-132">Insert a column in your table or matrix.</span></span> <span data-ttu-id="9a1f3-133">詳細については、「[列の挿入または削除 &#40;レポート ビルダーおよび SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-133">For more information, see [Insert or Delete a Column &#40;Report Builder and SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md).</span></span>  
  
3.  <span data-ttu-id="9a1f3-134">**[挿入]** タブの **[データ領域]** グループで **[ゲージ]** をクリックし、挿入した列のセルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-134">On the **Insert** tab, in the **Data Regions** group, click **Gauge**, and then click a cell in the column you inserted.</span></span> <span data-ttu-id="9a1f3-135">**[ゲージの種類の選択]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-135">The **Select Gauge Type** dialog appears.</span></span>  
  
4.  <span data-ttu-id="9a1f3-136">**[放射状]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-136">Click **Radial**.</span></span> <span data-ttu-id="9a1f3-137">最初の放射状ゲージが選択されます。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-137">The first radial gauge is selected.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="9a1f3-138">ゲージをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-138">Click the gauge.</span></span> <span data-ttu-id="9a1f3-139">**ゲージ データ** ペインが開きます。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-139">The **Gauge Data** pane opens.</span></span>  
  
7.  <span data-ttu-id="9a1f3-140">**[値]** 領域の **[(未指定)]** ボックスの一覧で、ゲージに値を表示するフィールドをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-140">In the **Values** area, in the **(Unspecified)** list box, click the field whose values you want to display in the gauge.</span></span> <span data-ttu-id="9a1f3-141">または、使用するフィールドをレポート データセットからドラッグします。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-141">Alternatively, drag the field to use from the report dataset.</span></span>  
  
8.  <span data-ttu-id="9a1f3-142">ゲージを右クリックし、 **[インジケーターの追加]** をクリックして、 **[隣接]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-142">Right-click the gauge, click **Add Indicator**, and then click **Adjacent**.</span></span> <span data-ttu-id="9a1f3-143">**[インジケーター スタイルの選択]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-143">The **Select Indicator Style** dialog box opens.</span></span>  
  
9. <span data-ttu-id="9a1f3-144">左側のペインの **[インジケーター スタイルの選択]** ダイアログ ボックスで、目的のインジケーター タイプをクリックし、インジケーター セットをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-144">In the **Select Indicator Style** dialog box, in the left pane, click the indicator type you want, and then click the indicator set.</span></span>  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
11. <span data-ttu-id="9a1f3-145">インジケーターをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-145">Click the indicator.</span></span> <span data-ttu-id="9a1f3-146">**ゲージ データ** ペインが開きます。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-146">The **Gauge Data** pane opens.</span></span>  
  
12. <span data-ttu-id="9a1f3-147">**[値]** 領域の **[(未指定)]** ボックスの一覧で、インジケーターとして値を表示するフィールドをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-147">In the **Values** area, in the **(Unspecified)** list box, click the field whose values you want to display as an indicator.</span></span> <span data-ttu-id="9a1f3-148">または、使用するフィールドをレポート データセットからドラッグします。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-148">Alternatively, drag the field to use from the report dataset.</span></span>  
  
     <span data-ttu-id="9a1f3-149">このフィールドは、ゲージで使用するフィールドと同じでも別でもかまいません。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-149">The field can be the same or a different field from the one you use in the gauge.</span></span>  
  
13. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
14. <span data-ttu-id="9a1f3-150">ゲージ パネルを右クリックして、 **[ラベルの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-150">Right-click the gauge panel and click **Add Label**.</span></span> <span data-ttu-id="9a1f3-151">ラベルがゲージ パネルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-151">A label is added to the gauge panel.</span></span> <span data-ttu-id="9a1f3-152">もう一度繰り返します。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-152">Repeat one more time.</span></span>  
  
     <span data-ttu-id="9a1f3-153">ゲージ パネルに 2 つのラベルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-153">The gauge panel has two labels.</span></span>  
  
15. <span data-ttu-id="9a1f3-154">各ラベルをゲージまたはインジケーターの近くにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-154">Drag each label to a location near the gauge or indicator.</span></span>  
  
16. <span data-ttu-id="9a1f3-155">ゲージの近くのラベルを右クリックし、 **[ラベルのプロパティ]** をクリックして、 **[テキスト]** ボックスにテキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-155">Right-click the label near the gauge, click **Label Properties**,and type the text you want in the **Text** box.</span></span>  
  
17. <span data-ttu-id="9a1f3-156">インジケーターの近くのラベルを右クリックし、 **[ラベルのプロパティ]** をクリックして、 **[テキスト]** ボックスにテキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="9a1f3-156">Right-click the label near the indicator, click **Label Properties**,and type the text you want in the **Text** box.</span></span>  
  
18. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9a1f3-157">参照</span><span class="sxs-lookup"><span data-stu-id="9a1f3-157">See Also</span></span>  
 [<span data-ttu-id="9a1f3-158">インジケーター &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9a1f3-158">Indicators &#40;Report Builder and SSRS&#41;</span></span>](indicators-report-builder-and-ssrs.md)  
  
  
