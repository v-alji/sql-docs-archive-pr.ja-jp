---
title: メジャーの変更 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7bd48810-15ce-45ff-862b-372d08606995
author: minewiskan
ms.author: owend
ms.openlocfilehash: fd352cbca1d21f5842e075d9cb8e5e766aa369b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643598"
---
# <a name="modifying-measures"></a><span data-ttu-id="2f17e-102">メジャーの変更</span><span class="sxs-lookup"><span data-stu-id="2f17e-102">Modifying Measures</span></span>
  <span data-ttu-id="2f17e-103">**FormatString** プロパティを使用して書式設定を定義することによって、メジャーの表示方法を調整できます。</span><span class="sxs-lookup"><span data-stu-id="2f17e-103">You can use the **FormatString** property to define formatting settings that control how measures are displayed to users.</span></span> <span data-ttu-id="2f17e-104">この実習では、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブの通貨メジャーと比率メジャーの書式プロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="2f17e-104">In this task, you specify formatting properties for the currency and percentage measures in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span>  
  
### <a name="to-modify-the-measures-of-the-cube"></a><span data-ttu-id="2f17e-105">キューブのメジャーを変更するには</span><span class="sxs-lookup"><span data-stu-id="2f17e-105">To modify the measures of the cube</span></span>  
  
1.  <span data-ttu-id="2f17e-106">**Tutorial キューブのキューブ デザイナーで、** [キューブ構造] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] タブに切り替えます。次に、 **[メジャー]** ペインの **[Internet Sales]** メジャー グループを展開し、 **[Order Quantity]** を右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f17e-106">Switch to the **Cube Structure** tab of Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, expand the **Internet Sales** measure group in the **Measures** pane, right-click **Order Quantity**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="2f17e-107">[プロパティ] ウィンドウの **[自動的に隠す]** 押しピン アイコンをクリックし、[プロパティ] ウィンドウを開いたまま固定します。</span><span class="sxs-lookup"><span data-stu-id="2f17e-107">In the Properties window, click the **Auto Hide** pushpin icon to pin the Properties window open.</span></span>  
  
     <span data-ttu-id="2f17e-108">[プロパティ] ウィンドウを開いたままにしておくと、キューブ内のアイテムごとにプロパティを変更する操作が容易になります。</span><span class="sxs-lookup"><span data-stu-id="2f17e-108">It is easier to change properties for several items in the cube when the Properties window remains open.</span></span>  
  
3.  <span data-ttu-id="2f17e-109">[プロパティ] ウィンドウで、 **[FormatString]** ボックスの一覧をクリックし、「 **#,#**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="2f17e-109">In the Properties window, click the **FormatString** list, and then type **#,#**.</span></span>  
  
4.  <span data-ttu-id="2f17e-110">**[キューブ構造]** タブのツール バーで、左側の **[メジャー グリッドの表示]** アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f17e-110">On the toolbar of the **Cube Structure** tab, click the **Show Measures Grid** icon on the left.</span></span>  
  
     <span data-ttu-id="2f17e-111">グリッド ビューで複数のメジャーを同時に選択できます。</span><span class="sxs-lookup"><span data-stu-id="2f17e-111">The grid view lets you select multiple measures at the same time.</span></span>  
  
5.  <span data-ttu-id="2f17e-112">次のメジャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="2f17e-112">Select the following measures.</span></span> <span data-ttu-id="2f17e-113">Ctrl キーを押しながらクリックすると、複数のメジャーを選択できます。</span><span class="sxs-lookup"><span data-stu-id="2f17e-113">You can select multiple measures by clicking each while holding down the CTRL key:</span></span>  
  
    -   <span data-ttu-id="2f17e-114">**Unit Price**</span><span class="sxs-lookup"><span data-stu-id="2f17e-114">**Unit Price**</span></span>  
  
    -   <span data-ttu-id="2f17e-115">**Extended Amount**</span><span class="sxs-lookup"><span data-stu-id="2f17e-115">**Extended Amount**</span></span>  
  
    -   <span data-ttu-id="2f17e-116">**Discount Amount**</span><span class="sxs-lookup"><span data-stu-id="2f17e-116">**Discount Amount**</span></span>  
  
    -   <span data-ttu-id="2f17e-117">**Product Standard Cost**</span><span class="sxs-lookup"><span data-stu-id="2f17e-117">**Product Standard Cost**</span></span>  
  
    -   <span data-ttu-id="2f17e-118">**Total Product Cost**</span><span class="sxs-lookup"><span data-stu-id="2f17e-118">**Total Product Cost**</span></span>  
  
    -   <span data-ttu-id="2f17e-119">**Sales Amount**</span><span class="sxs-lookup"><span data-stu-id="2f17e-119">**Sales Amount**</span></span>  
  
    -   <span data-ttu-id="2f17e-120">**Tax Amt**</span><span class="sxs-lookup"><span data-stu-id="2f17e-120">**Tax Amt**</span></span>  
  
    -   <span data-ttu-id="2f17e-121">**運送料**</span><span class="sxs-lookup"><span data-stu-id="2f17e-121">**Freight**</span></span>  
  
6.  <span data-ttu-id="2f17e-122">[プロパティ] ウィンドウで、 **FormatString** プロパティのセルをクリックして、 **[Currency]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2f17e-122">In the Properties window, in the **FormatString** list, select **Currency**.</span></span>  
  
7.  <span data-ttu-id="2f17e-123">[プロパティ] ウィンドウの一番上 (タイトル バーのすぐ下) にあるドロップダウン リストで、 **[Unit Price Discount Pct]** メジャーを選択します。次に、 **FormatString** プロパティのセルをクリックして **[Percent]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2f17e-123">In the drop-down list at the top of the Properties window (right below the title bar), select the measure **Unit Price Discount Pct**, and then select **Percent** in the **FormatString** list.</span></span>  
  
8.  <span data-ttu-id="2f17e-124">プロパティウィンドウで、 **Unit Price 割引率**メジャーの**Name**プロパティをに変更し `Unit Price Discount Percentage` ます。</span><span class="sxs-lookup"><span data-stu-id="2f17e-124">In the Properties window, change the **Name** property for the **Unit Price Discount Pct** measure to `Unit Price Discount Percentage`.</span></span>  
  
9. <span data-ttu-id="2f17e-125">[**メジャー** ] ペインで [ **Tax Amt** ] をクリックし、このメジャーの名前をに変更し `Tax Amount` ます。</span><span class="sxs-lookup"><span data-stu-id="2f17e-125">In the **Measures** pane, click **Tax Amt** and change the name of this measure to `Tax Amount`.</span></span>  
  
10. <span data-ttu-id="2f17e-126">[プロパティ] ウィンドウの **[自動的に隠す]** アイコンをクリックし、[プロパティ] ウィンドウを非表示にします。次に、 **[キューブ構造]** タブのツール バーで、 **[メジャー ツリーの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f17e-126">In the Properties window, click the **Auto Hide** icon to hide the Properties window, and then click **Show Measures Tree** on the toolbar of the **Cube Structure** tab.</span></span>  
  
11. <span data-ttu-id="2f17e-127">**[File]\(ファイル\)** メニューの **[Save All]\(すべて保存\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f17e-127">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="2f17e-128">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="2f17e-128">Next Task in Lesson</span></span>  
 [<span data-ttu-id="2f17e-129">Customer ディメンションの変更</span><span class="sxs-lookup"><span data-stu-id="2f17e-129">Modifying the Customer Dimension</span></span>](lesson-3-2-modifying-the-customer-dimension.md)  
  
## <a name="see-also"></a><span data-ttu-id="2f17e-130">参照</span><span class="sxs-lookup"><span data-stu-id="2f17e-130">See Also</span></span>  
 <span data-ttu-id="2f17e-131">[データベースディメンションの定義](multidimensional-models/define-database-dimensions.md) </span><span class="sxs-lookup"><span data-stu-id="2f17e-131">[Define Database Dimensions](multidimensional-models/define-database-dimensions.md) </span></span>  
 [<span data-ttu-id="2f17e-132">メジャーのプロパティの構成</span><span class="sxs-lookup"><span data-stu-id="2f17e-132">Configure Measure Properties</span></span>](multidimensional-models/configure-measure-properties.md)  
  
  
