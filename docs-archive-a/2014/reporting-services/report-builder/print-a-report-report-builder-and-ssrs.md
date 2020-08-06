---
title: レポートの印刷 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b96936c9-c387-41a9-8c19-6eb325769ffd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fe029019cdf9739153256db399cfa1426d3ba632
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634288"
---
# <a name="print-a-report-report-builder-and-ssrs"></a><span data-ttu-id="2b98b-102">レポートの印刷 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="2b98b-102">Print a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="2b98b-103">レポートをレポート サーバーに保存した後は、ブラウザーやレポート マネージャーのほか、エクスポートされたレポートの表示に使用する任意のアプリケーションで、レポートを表示および印刷できます。</span><span class="sxs-lookup"><span data-stu-id="2b98b-103">After you save a report to a report server, you can view and print the report from a browser, Report Manager, or any application that you use to view an exported report.</span></span> <span data-ttu-id="2b98b-104">レポートを保存する前にプレビューする場合は、印刷することができます。</span><span class="sxs-lookup"><span data-stu-id="2b98b-104">Before saving a report, you can print it when you preview it.</span></span>  
  
 <span data-ttu-id="2b98b-105">レポートを印刷するときには、使用する用紙のサイズを指定できます。</span><span class="sxs-lookup"><span data-stu-id="2b98b-105">When you print a report, you can specify the size of the paper to use.</span></span> <span data-ttu-id="2b98b-106">用紙のサイズによって、レポート内のページ数や各ページに収まるレポート データが決定されます。</span><span class="sxs-lookup"><span data-stu-id="2b98b-106">The size of the paper determines the number of pages in a report and which report data fits on each page.</span></span> <span data-ttu-id="2b98b-107">用紙のサイズは、PDF、画像、および印刷などのハード改ページ レンダラーを使用して表示されるレポートのみに影響します。</span><span class="sxs-lookup"><span data-stu-id="2b98b-107">Paper size affects only reports that are rendered with hard page-break renders: PDF, Image, and Print.</span></span> <span data-ttu-id="2b98b-108">用紙サイズの設定はその他のレンダラーには影響しません。</span><span class="sxs-lookup"><span data-stu-id="2b98b-108">Setting the paper size has no effect on other renderers.</span></span> <span data-ttu-id="2b98b-109">詳しくは、「[レンダリングの動作 &#40;レポート ビルダーおよび SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2b98b-109">For more information, see [Rendering Behaviors &#40;Report Builder  and SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="2b98b-110">レポート マネージャーのレポート ビューアー ツール バー、またはレポート ビルダーのプレビューでは、レポートをハード改ページ レンダラーにエクスポートしたり、[印刷] ボタンをクリックしてレポートのコピーを印刷したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="2b98b-110">From the report viewer toolbar in Report Manager or in preview in Report Builder, you can export a report to a hard page-break renderer or click the Print button to print a copy of the report.</span></span> <span data-ttu-id="2b98b-111">用紙のサイズやその他のページ設定プロパティの設定が必要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="2b98b-111">You might need to set the paper size or other page setup properties.</span></span> <span data-ttu-id="2b98b-112">**[レポートのプロパティ]** ダイアログ ボックスを使用すると、用紙のサイズを含むページ設定プロパティを変更できます。</span><span class="sxs-lookup"><span data-stu-id="2b98b-112">Use the **Report Properties** dialog box to change page setup properties, including paper size.</span></span>  
  
 <span data-ttu-id="2b98b-113">印刷ページの余白は、デザイン モードと実行モードの 2 か所で指定できます。</span><span class="sxs-lookup"><span data-stu-id="2b98b-113">You can specify print page margins in two different locations: in design mode and in run mode.</span></span>  
  
-   <span data-ttu-id="2b98b-114">**デザイン モード。**</span><span class="sxs-lookup"><span data-stu-id="2b98b-114">**Design mode.**</span></span> <span data-ttu-id="2b98b-115">デザイン モードでページの余白を設定した場合は、レポートの保存時に、その設定がレポート定義に保存されます。</span><span class="sxs-lookup"><span data-stu-id="2b98b-115">When you set page margins in design mode, these settings are saved in the report definition when you save the report.</span></span>  
  
-   <span data-ttu-id="2b98b-116">**実行モード。**</span><span class="sxs-lookup"><span data-stu-id="2b98b-116">**Run mode.**</span></span> <span data-ttu-id="2b98b-117">実行モードでページの余白を設定した場合、この情報はレポート定義に保存されません。</span><span class="sxs-lookup"><span data-stu-id="2b98b-117">When you set page margins in run mode, this information is not saved in the report definition.</span></span> <span data-ttu-id="2b98b-118">次回レポートを印刷するときは、余白を再指定しない限り、レポート定義から設定が取得されます。</span><span class="sxs-lookup"><span data-stu-id="2b98b-118">The next time you print the report, you will get the settings from the report definition, unless you indicate your print margins again.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2b98b-119">印刷の余白は、デザイン モードでも実行モードでも表示されません。</span><span class="sxs-lookup"><span data-stu-id="2b98b-119">Print margins are not displayed in design or run modes.</span></span> <span data-ttu-id="2b98b-120">デザイン画面領域とレポートの印刷領域の間に関連はありません。</span><span class="sxs-lookup"><span data-stu-id="2b98b-120">There is no relationship between the design surface area and the print area of your report.</span></span> <span data-ttu-id="2b98b-121">印刷の余白を確認するには、実行モード時に、リボンの **[実行]** タブにある [印刷レイアウト] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b98b-121">To see print margins, in run mode, click Print Layout on the **Run** tab on the Ribbon.</span></span>  
  
 <span data-ttu-id="2b98b-122">レポートの改ページの詳細については、「[Reporting Services の改ページ (レポート ビルダーおよび SSRS)](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b98b-122">For more information about report paging, see [Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-print-a-report-in-report-builder"></a><span data-ttu-id="2b98b-123">レポート ビルダーでレポートを印刷するには</span><span class="sxs-lookup"><span data-stu-id="2b98b-123">To print a report in Report Builder</span></span>  
  
1.  <span data-ttu-id="2b98b-124">レポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="2b98b-124">Open a report.</span></span>  
  
2.  <span data-ttu-id="2b98b-125">[ホーム] タブで、[**実行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b98b-125">On the Home tab, click **Run**.</span></span>  
  
3.  <span data-ttu-id="2b98b-126">(省略可) 印刷するレポートの外観を確認するには、 **[印刷レイアウト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b98b-126">(optional) Click **Print Layout** to see how the report will look when it is printed.</span></span>  
  
4.  <span data-ttu-id="2b98b-127">(省略可) 用紙、用紙の向き、および余白を設定するには、 **[ページ設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b98b-127">(optional) Click **Page Setup** to set paper, orientation, and margins.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2b98b-128">これらの既定値は、[デザイン] ビューで設定されているレポート プロパティから取得されます。</span><span class="sxs-lookup"><span data-stu-id="2b98b-128">The default values for these come from the report properties, which are set in Design view.</span></span> <span data-ttu-id="2b98b-129">ここで設定した **[ページ設定]** ダイアログ ボックスの値は、このセッションでのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="2b98b-129">The values you set here in the **Page Setup** dialog box are for this session only.</span></span> <span data-ttu-id="2b98b-130">このレポートを閉じてから再度開くと、既定値に戻ります。</span><span class="sxs-lookup"><span data-stu-id="2b98b-130">When you close this report and reopen it, it will have the default values again.</span></span>  
  
5.  <span data-ttu-id="2b98b-131">**[印刷]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b98b-131">Click **Print**.</span></span>  
  
6.  <span data-ttu-id="2b98b-132">**[印刷]** ダイアログ ボックスで、プリンターを選択し、その他の印刷オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="2b98b-132">In the **Print** dialog box, select a printer and specify other printing options.</span></span>  
  
### <a name="to-print-a-report-from-a-web-browser-application"></a><span data-ttu-id="2b98b-133">Web ブラウザー アプリケーションからレポートを印刷するには</span><span class="sxs-lookup"><span data-stu-id="2b98b-133">To print a report from a Web browser application</span></span>  
  
1.  <span data-ttu-id="2b98b-134">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../report-manager-ssrs-native-mode.md) を開始します。</span><span class="sxs-lookup"><span data-stu-id="2b98b-134">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="2b98b-135">レポート マネージャーで、印刷するレポートに移動します。</span><span class="sxs-lookup"><span data-stu-id="2b98b-135">In Report Manager, navigate to the report that you want to print.</span></span> <span data-ttu-id="2b98b-136">レポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="2b98b-136">Open the report.</span></span>  
  
3.  <span data-ttu-id="2b98b-137">レポート上部のツール バーで **[印刷]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b98b-137">On the toolbar at the top of the report, click **Print**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2b98b-138">HTML レポートを初めて印刷する場合、印刷に必要な ActiveX コントロールのインストールを促すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b98b-138">The first time you print an HTML report, the report server prompts you to install an ActiveX control used for printing.</span></span> <span data-ttu-id="2b98b-139">印刷するためには、このコントロールをインストールして構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b98b-139">You must install and configure the control to print.</span></span>  
  
4.  <span data-ttu-id="2b98b-140">**[印刷]** ダイアログ ボックスでプリンターを選択し、 **[印刷]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b98b-140">In the **Print** dialog box, select a printer, and then click **Prin**t.</span></span>  
  
### <a name="to-print-a-report-from-other-applications"></a><span data-ttu-id="2b98b-141">他のアプリケーションからレポートを印刷するには</span><span class="sxs-lookup"><span data-stu-id="2b98b-141">To print a report from other applications</span></span>  
  
1.  <span data-ttu-id="2b98b-142">レポート マネージャーで、印刷するレポートに移動します。</span><span class="sxs-lookup"><span data-stu-id="2b98b-142">In Report Manager, navigate to the report that you want to print.</span></span> <span data-ttu-id="2b98b-143">レポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="2b98b-143">Open the report.</span></span>  
  
2.  <span data-ttu-id="2b98b-144">レポート上部のツール バーから表示形式を選択して、 **[エクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b98b-144">On the toolbar at the top of the report, select a rendering format, and then click **Export**.</span></span> <span data-ttu-id="2b98b-145">選択した表示形式に対応するビューアー アプリケーションでレポートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b98b-145">The report opens in a viewer application that corresponds to the rendering format.</span></span>  
  
     <span data-ttu-id="2b98b-146">たとえば、PDF を選択した場合、Adobe Acrobat Reader でレポートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b98b-146">For example, if you select PDF, the report opens in Adobe Acrobat Reader.</span></span>  
  
3.  <span data-ttu-id="2b98b-147">このプログラムで **[ファイル]** メニューの **[印刷]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b98b-147">On the **File** menu in that program, click **Print**.</span></span>  
  
### <a name="to-change-paper-size"></a><span data-ttu-id="2b98b-148">ページ サイズを変更するには</span><span class="sxs-lookup"><span data-stu-id="2b98b-148">To change paper size</span></span>  
  
1.  <span data-ttu-id="2b98b-149">レポート本文の外側を右クリックし、 **[レポートのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b98b-149">Right-click outside of the report body and click **Report Properties**.</span></span>  
  
2.  <span data-ttu-id="2b98b-150">**[ページ設定]** で **[用紙サイズ]** ボックスの一覧から値を選択します。</span><span class="sxs-lookup"><span data-stu-id="2b98b-150">In **Page Setup**, select a value from the **Paper Size** list.</span></span> <span data-ttu-id="2b98b-151">各オプションによって、 **[幅]** プロパティと **[高さ]** プロパティの値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="2b98b-151">Each option populates the **Width** and **Height** properties.</span></span> <span data-ttu-id="2b98b-152">**[幅]** ボックスと **[高さ]** ボックスに数値を入力することにより、カスタム サイズを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="2b98b-152">You can also specify a custom size by typing numeric values in the **Width** and **Height** boxes.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  <span data-ttu-id="2b98b-153">サイズの値には、ユーザーのロケール設定に基づいた既定の単位が使用されます。</span><span class="sxs-lookup"><span data-stu-id="2b98b-153">Size values have a default unit based on the user's locale settings.</span></span> <span data-ttu-id="2b98b-154">別の単位を指定するには、数値の後に cm、mm、pt、pc などの物理的な単位指定子を入力します。</span><span class="sxs-lookup"><span data-stu-id="2b98b-154">To designate a different unit, type a physical unit designator such as cm, mm, pt, or pc after the numeric value.</span></span>  
  
### <a name="to-set-page-margins-in-design-mode"></a><span data-ttu-id="2b98b-155">デザイン モードでページの余白を設定するには</span><span class="sxs-lookup"><span data-stu-id="2b98b-155">To set page margins in design mode</span></span>  
  
-   <span data-ttu-id="2b98b-156">デザイン画面の周りの青い領域を右クリックし、 **[レポートのプロパティ]** をクリックしてから **[ページ設定]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b98b-156">Right-click the blue area around the design surface, click **Report Properties**, and then click the **Page Setup** page.</span></span>  
  
### <a name="to-set-page-margins-in-run-mode"></a><span data-ttu-id="2b98b-157">実行モードでページの余白を設定するには</span><span class="sxs-lookup"><span data-stu-id="2b98b-157">To set page margins in run mode</span></span>  
  
-   <span data-ttu-id="2b98b-158">**[実行]** タブの **[ページ設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b98b-158">Click **Page Setup** on the **Run** tab.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b98b-159">参照</span><span class="sxs-lookup"><span data-stu-id="2b98b-159">See Also</span></span>  
 <span data-ttu-id="2b98b-160">[レポートの印刷 &#40;レポート ビルダーおよび SSRS&#41;](print-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2b98b-160">[Print Reports &#40;Report Builder and SSRS&#41;](print-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2b98b-161">[レポートのエクスポート &#40;レポートビルダーと SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2b98b-161">[Exporting Reports &#40;Report Builder and SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2b98b-162">[[ページ設定] ([レポートのプロパティ] ダイアログ ボックス) (レポート ビルダー)](../report-properties-dialog-box-page-setup-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="2b98b-162">[Report Properties Dialog Box, Page Setup &#40;Report Builder&#41;](../report-properties-dialog-box-page-setup-report-builder.md) </span></span>  
 [<span data-ttu-id="2b98b-163">レポート デザイン ビュー &#40;レポート ビルダー&#41;</span><span class="sxs-lookup"><span data-stu-id="2b98b-163">Report Design View &#40;Report Builder&#41;</span></span>](report-design-view-report-builder.md)  
  
  
