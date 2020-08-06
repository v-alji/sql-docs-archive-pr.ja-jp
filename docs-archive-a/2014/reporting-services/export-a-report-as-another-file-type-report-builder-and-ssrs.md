---
title: 別の種類のファイルとしてレポートをエクスポートする (レポートビルダーおよび SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b577568b-ecbd-44c3-be88-31dab6fc38a2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 240d3266b7b8c9a445658a9fd21fb9ea18a4c113
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711761"
---
# <a name="export-a-report-as-another-file-type-report-builder-and-ssrs"></a><span data-ttu-id="4ed42-102">別の種類のファイルとしてレポートをエクスポートする (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="4ed42-102">Export a Report as Another File Type (Report Builder and SSRS)</span></span>
  <span data-ttu-id="4ed42-103">レポートは、レポート ビルダーまたはレポート デザイナーでプレビュー中に、CSV、Image、PDF、 [!INCLUDE[ofprword](../includes/ofprword-md.md)]、 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]などの他のファイル形式に変換できます。また、レポート サーバーで閲覧中に変換することもできます。</span><span class="sxs-lookup"><span data-stu-id="4ed42-103">You can render a report to another file format, such as CSV, Image, PDF, [!INCLUDE[ofprword](../includes/ofprword-md.md)], or [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)], while previewing your report in Report Builder or Report Designer, or you can render the report while viewing the report on the report server.</span></span> <span data-ttu-id="4ed42-104">レポートを特定の形式で表示することが便利であるのは、レポートをレポート サーバーにパブリッシュせずにすぐに別のファイルの種類で保存する場合や、レポートを特定の形式でユーザーに配信する際にレポートのデザインがどのように表示されるかを確認する場合です。</span><span class="sxs-lookup"><span data-stu-id="4ed42-104">Rendering the report in a specific format in is helpful when you want to immediately save the report as another file type without publishing the report to the report server or when you want to see how your report design will appear when delivered to your report readers in a specific format.</span></span> <span data-ttu-id="4ed42-105">レポート サーバーでレポートを変換するのが便利なのは、サブスクリプションを設定したり電子メールでレポートを配信したりする場合や、レポート サーバーで利用可能なレポートを保存する場合です。</span><span class="sxs-lookup"><span data-stu-id="4ed42-105">Rendering the report on the report server is useful when you set up subscriptions or deliver your reports via e-mail, or if you want to save a report that is available on the report server.</span></span> <span data-ttu-id="4ed42-106">詳細については「[サブスクリプションと配信 &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ed42-106">For more information, see [Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
### <a name="to-export-a-report-as-another-file-type-in-report-builder"></a><span data-ttu-id="4ed42-107">レポート ビルダーでレポートを別の種類のファイルとしてエクスポートするには</span><span class="sxs-lookup"><span data-stu-id="4ed42-107">To export a report as another file type in Report Builder</span></span>  
  
1.  <span data-ttu-id="4ed42-108">レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="4ed42-108">Preview the report.</span></span>  
  
2.  <span data-ttu-id="4ed42-109">リボンの **[エクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ed42-109">On the ribbon, click **Export**.</span></span>  
  
3.  <span data-ttu-id="4ed42-110">使用する形式を選択します。</span><span class="sxs-lookup"><span data-stu-id="4ed42-110">Select the format that you want to use.</span></span>  
  
     <span data-ttu-id="4ed42-111">**[名前を付けて保存]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="4ed42-111">The **Save As** dialog box opens.</span></span> <span data-ttu-id="4ed42-112">既定では、ファイル名はエクスポートしたレポートの名前になります。</span><span class="sxs-lookup"><span data-stu-id="4ed42-112">By default, the file name is that of the report that you exported.</span></span> <span data-ttu-id="4ed42-113">必要に応じてファイル名を変更できます。</span><span class="sxs-lookup"><span data-stu-id="4ed42-113">Optionally, you can change the file name.</span></span>  
  
4.  <span data-ttu-id="4ed42-114">レポートを保存した場所へ移動して、レポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="4ed42-114">Navigate to the location where you saved the exported report and open it.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4ed42-115">ファイルの種類に関連付けられたプログラムがないことが原因で、レポートを選択した形式で開くことができない場合は、エクスポートされたファイルを保存するか、レポートを開くためのプログラムをオンライン上で探すことが求められます。</span><span class="sxs-lookup"><span data-stu-id="4ed42-115">If the program cannot open the report in the format that you chose because you do not have a program associated with this file type, you will be prompted to save the exported report or to find a program online to open the report.</span></span>  
  
### <a name="to-export-a-report-as-another-file-type-in-report-manager"></a><span data-ttu-id="4ed42-116">レポート マネージャーでレポートを別の種類のファイルとしてエクスポートするには</span><span class="sxs-lookup"><span data-stu-id="4ed42-116">To export a report as another file type in Report Manager</span></span>  
  
1.  <span data-ttu-id="4ed42-117">レポート マネージャーの **[ホーム]** ページから、エクスポートするレポートに移動します。</span><span class="sxs-lookup"><span data-stu-id="4ed42-117">From the Report Manager **Home** page, navigate to the report that you want to export.</span></span>  
  
2.  <span data-ttu-id="4ed42-118">レポートをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ed42-118">Click the report.</span></span>  
  
     <span data-ttu-id="4ed42-119">レポートが生成されます。</span><span class="sxs-lookup"><span data-stu-id="4ed42-119">The report is generated.</span></span>  
  
3.  <span data-ttu-id="4ed42-120">レポート ビューアー ツール バーで、 **[形式の選択]** ボックスの矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ed42-120">On the Report Viewer toolbar, click the **Select a format** drop-down arrow.</span></span>  
  
4.  <span data-ttu-id="4ed42-121">使用する形式を選択します。</span><span class="sxs-lookup"><span data-stu-id="4ed42-121">Select the format that you want to use.</span></span>  
  
5.  <span data-ttu-id="4ed42-122">**[エクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ed42-122">Click **Export**.</span></span>  
  
     <span data-ttu-id="4ed42-123">ファイルを開くか保存するかを確認するメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4ed42-123">A message appears asking you if you want to open or save the file.</span></span>  
  
6.  <span data-ttu-id="4ed42-124">選択したエクスポート形式でレポートを表示するには、 **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ed42-124">To view the report in the selected export format, click **Open**.</span></span>  
  
     <span data-ttu-id="4ed42-125">\- または</span><span class="sxs-lookup"><span data-stu-id="4ed42-125">\- or -</span></span>  
  
     <span data-ttu-id="4ed42-126">選択したエクスポート形式でレポートをすぐに保存するには、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ed42-126">To immediately save the report in the selected export format, click **Save**.</span></span>  
  
     <span data-ttu-id="4ed42-127">選択した形式に関連付けられているアプリケーションを使用して、レポートが表示または保存されます。</span><span class="sxs-lookup"><span data-stu-id="4ed42-127">Using the application that is associated with the format that you chose, the report is either displayed or saved.</span></span> <span data-ttu-id="4ed42-128">**[保存]** をクリックした場合、レポートを保存する場所を指定するよう求められます。</span><span class="sxs-lookup"><span data-stu-id="4ed42-128">If you click **Save**, you will be prompted for a location where you can save your report.</span></span>  
  
     <span data-ttu-id="4ed42-129">**注** ファイルの種類に関連付けられたプログラムがないことが原因で、レポートを選択した形式で開くことができない場合は、エクスポートされたファイルを保存するか、レポートを開くためのプログラムをオンライン上で探すことが求められます。</span><span class="sxs-lookup"><span data-stu-id="4ed42-129">**Note** If the program cannot open the report in the format that you chose because you do not have a program associated with this file type, you will be prompted to save the exported report or to find a program online to open the report.</span></span>  
  
### <a name="to-export-a-report-as-another-file-type-in-a-sharepoint-library"></a><span data-ttu-id="4ed42-130">SharePoint ライブラリでレポートを別の種類のファイルとしてエクスポートするには</span><span class="sxs-lookup"><span data-stu-id="4ed42-130">To export a report as another file type in a SharePoint library</span></span>  
  
1.  <span data-ttu-id="4ed42-131">レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="4ed42-131">Preview the report.</span></span>  
  
2.  <span data-ttu-id="4ed42-132">ツール バーの **[アクション]** をクリックし、 **[エクスポート]** をポイントして、使用する形式を選択します。</span><span class="sxs-lookup"><span data-stu-id="4ed42-132">On the toolbar, click **Actions**, point to **Export**, and then select the format that you want to use.</span></span>  
  
     <span data-ttu-id="4ed42-133">**[ファイルのダウンロード]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="4ed42-133">The **File Download** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="4ed42-134">選択したエクスポート形式でレポートを表示するには、 **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ed42-134">To view the report in the selected export format, click **Open**.</span></span>  
  
     <span data-ttu-id="4ed42-135">\- または</span><span class="sxs-lookup"><span data-stu-id="4ed42-135">\- or -</span></span>  
  
     <span data-ttu-id="4ed42-136">選択したエクスポート形式でレポートをすぐに保存するには、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ed42-136">To immediately save the report in the selected export format, click **Save**.</span></span>  
  
     <span data-ttu-id="4ed42-137">選択した形式に関連付けられているアプリケーションを使用して、レポートが表示または保存されます。</span><span class="sxs-lookup"><span data-stu-id="4ed42-137">Using the application that is associated with the format that you chose, the report is either displayed or saved.</span></span> <span data-ttu-id="4ed42-138">**[保存]** をクリックした場合、レポートを保存する場所を指定するよう求められます。</span><span class="sxs-lookup"><span data-stu-id="4ed42-138">If you click **Save**, you will be prompted for a location where you can save your report.</span></span>  
  
     <span data-ttu-id="4ed42-139">必要に応じて、エクスポートしたレポートのファイル名を変更します。</span><span class="sxs-lookup"><span data-stu-id="4ed42-139">Optionally, change the file name of the exported report.</span></span>  
  
     <span data-ttu-id="4ed42-140">**注** ファイルの種類に関連付けられたプログラムがないことが原因で、レポートを選択した形式で開くことができない場合は、エクスポートされたファイルを保存するか、レポートを開くためのプログラムをオンライン上で探すことが求められます。</span><span class="sxs-lookup"><span data-stu-id="4ed42-140">**Note** If the program cannot open the report in the format that you chose because you do not have a program associated with this file type, you will be prompted to save the exported report or to find a program online to open the report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ed42-141">参照</span><span class="sxs-lookup"><span data-stu-id="4ed42-141">See Also</span></span>  
 <span data-ttu-id="4ed42-142">[レポートのエクスポート &#40;レポートビルダーと SSRS&#41;](report-builder/export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4ed42-142">[Exporting Reports &#40;Report Builder and SSRS&#41;](report-builder/export-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4ed42-143">[Reporting Services &#40;レポートビルダーおよび SSRS&#41;での改ページ](report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4ed42-143">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="4ed42-144">さまざまなレポート表示拡張機能の対話機能 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="4ed42-144">Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;</span></span>](report-builder/interactive-functionality-different-report-rendering-extensions.md)  
  
  
