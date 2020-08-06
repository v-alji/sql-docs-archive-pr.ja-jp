---
title: '[アクションプロパティ] ダイアログボックス (レポートビルダーおよび SSRS) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.shared.action.f1
- "10413"
- "10504"
- sql12.rtp.rptdesigner.calculatedseriesproperties.action.f1
- sql12.rtp.rptdesigner.pictureproperties.action.f1
- sql12.rtp.rptdesigner.actionproperties.f1
- sql12.rtp.rptdesigner.charttitleproperties.action.f1
- "10133"
- "10052"
- "10147"
- sql12.rtp.rptdesigner.chartproperties.action.f1
- "10122"
- sql12.rtp.rptdesigner.serieslabelproperties.action.f1
- sql12.rtp.rptdesigner.textboxproperties.action.f1
- "10162"
- "10168"
- sql12.rtp.rptdesigner.textproperties.action.f1
- sql12.rtp.rptdesigner.placeholderproperties.action.f1
- "10250"
- "10129"
- "10244"
- sql12.rtp.rptdesigner.seriesproperties.action.f1
ms.assetid: 2c5d915b-4f97-42cf-b8f1-49ca3ff3d0f9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 77b51af0763010676b95fcedb433ab963fc7fcdf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642624"
---
# <a name="action-properties-dialog-box-report-builder-and-ssrs"></a><span data-ttu-id="9b4de-102">[アクション プロパティ] ダイアログ ボックス (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="9b4de-102">Action Properties Dialog Box (Report Builder and SSRS)</span></span>
  <span data-ttu-id="9b4de-103">**[アクション]** ダイアログ ボックスでは、グラフ、ゲージ、およびリンクをサポートするマップ要素に対してハイパーリンク オプションを有効にできます。</span><span class="sxs-lookup"><span data-stu-id="9b4de-103">The **Action** dialog box can be used to enable hyperlink options for a chart, gauge, and map elements that support links.</span></span> <span data-ttu-id="9b4de-104">ユーザーがレポート上でクリックして、URL、同じレポート サーバーまたはレポート サーバーと統合されている SharePoint サイト上の他のレポート、または同じレポート内の他の場所にリンクできるようにアクションを定義します。</span><span class="sxs-lookup"><span data-stu-id="9b4de-104">Define an action so that a user can click on the report and link to a URL, to a different report on the same report server or on a SharePoint site that is integrated with a report server, or to a different location in the same report.</span></span>  
  
## <a name="options"></a><span data-ttu-id="9b4de-105">Options</span><span class="sxs-lookup"><span data-stu-id="9b4de-105">Options</span></span>  
 <span data-ttu-id="9b4de-106">**アクションとして有効にする**</span><span class="sxs-lookup"><span data-stu-id="9b4de-106">**Enable as an action**</span></span>  
 <span data-ttu-id="9b4de-107">ユーザーがアイテムをクリックしたときに実行するアクションを示すオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="9b4de-107">Select an option to indicate the action to perform when the user clicks the item.</span></span>  
  
 <span data-ttu-id="9b4de-108">**なし**</span><span class="sxs-lookup"><span data-stu-id="9b4de-108">**None**</span></span>  
 <span data-ttu-id="9b4de-109">アイテムに対するアクションがないことを示します。</span><span class="sxs-lookup"><span data-stu-id="9b4de-109">Choose this option to indicate that the item has no action.</span></span>  
  
 <span data-ttu-id="9b4de-110">**[レポートに移動する]**</span><span class="sxs-lookup"><span data-stu-id="9b4de-110">**Go to report**</span></span>  
 <span data-ttu-id="9b4de-111">レポート サーバー上にある詳細レポートへのリンクを作成します。</span><span class="sxs-lookup"><span data-stu-id="9b4de-111">Choose this option to create a link to a drillthrough report that is located on a report server.</span></span> <span data-ttu-id="9b4de-112">**[レポートに移動する]** をクリックすると、次のオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9b4de-112">The following additional options appear when you select **Go to report**.</span></span>  
  
 <span data-ttu-id="9b4de-113">**[レポートの指定]**</span><span class="sxs-lookup"><span data-stu-id="9b4de-113">**Specify a report**</span></span>  
 <span data-ttu-id="9b4de-114">詳細レポートとして使用するレポート名を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="9b4de-114">Type or select the name of the report that you want to use as a drillthrough report.</span></span> <span data-ttu-id="9b4de-115">詳細レポートはこのレポートと同じレポート サーバーに存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b4de-115">Drillthrough reports must be on the same report server as this report.</span></span>  
  
 <span data-ttu-id="9b4de-116">ネイティブ モード用に構成されているレポート サーバーにレポートをパブリッシュする場合は、ファイル名の拡張子を含まない完全パスまたは相対パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="9b4de-116">For a report published to a report server configured for native mode, use a full or relative path without the file name extension.</span></span> <span data-ttu-id="9b4de-117">レポートが現在のレポートと同じフォルダーに保存されている場合は、レポートの名前のみを使用します。</span><span class="sxs-lookup"><span data-stu-id="9b4de-117">If the report is in the same folder as the current report, use the name of the report only.</span></span> <span data-ttu-id="9b4de-118">レポートが、同じレポート サーバー上の別のフォルダーに保存されている場合は、相対パスまたは完全パスを使用します。</span><span class="sxs-lookup"><span data-stu-id="9b4de-118">If the report is in a different folder on the same report server, use a relative path or a full path.</span></span> <span data-ttu-id="9b4de-119">相対パスは、現在のフォルダーから始まり、フォルダー階層を上に移動します (例: ../Folder2/Report1)。</span><span class="sxs-lookup"><span data-stu-id="9b4de-119">A relative path starts from the current folder and moves up the folder hierarchy, for example, ../Folder2/Report1.</span></span> <span data-ttu-id="9b4de-120">完全パスは Home フォルダー「/」から始まります。</span><span class="sxs-lookup"><span data-stu-id="9b4de-120">A full path starts from /, the Home folder.</span></span> <span data-ttu-id="9b4de-121">たとえば、「/Reports/Report1」のように指定します。</span><span class="sxs-lookup"><span data-stu-id="9b4de-121">For example, /Reports/Report1.</span></span>  
  
 <span data-ttu-id="9b4de-122">SharePoint 統合モードで構成されているレポート サーバーにレポートをパブリッシュする場合は、ファイル名の拡張子 (.rdl) を含めた完全修飾 URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="9b4de-122">For a report published to a report server configured in SharePoint integrated mode, use a fully qualified URL including the file name extension (.rdl).</span></span> <span data-ttu-id="9b4de-123">たとえば、http:// *\<SharePointservername>/\<site>* /documents/report1.rdl」</span><span class="sxs-lookup"><span data-stu-id="9b4de-123">For example, http://*\<SharePointservername>/\<site>*/Documents/Report1.rdl.</span></span> <span data-ttu-id="9b4de-124">相対パスはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="9b4de-124">Relative paths are not supported.</span></span>  
  
 <span data-ttu-id="9b4de-125">詳細については、msdn.microsoft.com の[レポート ビルダーに関するドキュメント](https://go.microsoft.com/fwlink/?LinkId=154494)の「[外部アイテムへのパスの指定 (レポート ビルダーおよび SSRS)](report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b4de-125">For more information, see [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md) in the [Report Builder documentation](https://go.microsoft.com/fwlink/?LinkId=154494) on msdn.microsoft.com.</span></span>  
  
 <span data-ttu-id="9b4de-126">**[レポートの実行に以下のパラメーターを使用]**</span><span class="sxs-lookup"><span data-stu-id="9b4de-126">**Use these parameters to run the report**</span></span>  
 <span data-ttu-id="9b4de-127">詳細レポートに渡すパラメーターの一覧を追加します。</span><span class="sxs-lookup"><span data-stu-id="9b4de-127">Add a list of parameters to pass to the drillthrough report.</span></span> <span data-ttu-id="9b4de-128">パラメーター名は、対象のレポートで定義されているパラメーターと一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b4de-128">The parameter names must match the parameters defined for the target report.</span></span> <span data-ttu-id="9b4de-129">パラメーターを追加または削除するには **[追加]** ボタンまたは **[削除]** ボタンを使用し、パラメーターの一覧の順序を設定するには上矢印および下矢印を使用します。</span><span class="sxs-lookup"><span data-stu-id="9b4de-129">Use the **Add** and **Delete** buttons to add and remove parameters and use the up and down arrows to order the list of parameters.</span></span>  
  
 <span data-ttu-id="9b4de-130">**[追加]**</span><span class="sxs-lookup"><span data-stu-id="9b4de-130">**Add**</span></span>  
 <span data-ttu-id="9b4de-131">詳細レポートに渡す新しいパラメーターを追加します。</span><span class="sxs-lookup"><span data-stu-id="9b4de-131">Add a new parameter to pass to the drillthrough report.</span></span>  
  
 <span data-ttu-id="9b4de-132">**削除**</span><span class="sxs-lookup"><span data-stu-id="9b4de-132">**Delete**</span></span>  
 <span data-ttu-id="9b4de-133">詳細レポートのパラメーターを削除します。</span><span class="sxs-lookup"><span data-stu-id="9b4de-133">Delete a parameter for the drillthrough report.</span></span>  
  
 <span data-ttu-id="9b4de-134">**上矢印**</span><span class="sxs-lookup"><span data-stu-id="9b4de-134">**Up arrow**</span></span>  
 <span data-ttu-id="9b4de-135">パラメーターを一覧内で上に移動します。</span><span class="sxs-lookup"><span data-stu-id="9b4de-135">Move the parameter up in the list.</span></span>  
  
 <span data-ttu-id="9b4de-136">**下方向キー**</span><span class="sxs-lookup"><span data-stu-id="9b4de-136">**Down arrow**</span></span>  
 <span data-ttu-id="9b4de-137">パラメーターを一覧内で下に移動します。</span><span class="sxs-lookup"><span data-stu-id="9b4de-137">Move the parameter down in the list.</span></span>  
  
 <span data-ttu-id="9b4de-138">**名前**</span><span class="sxs-lookup"><span data-stu-id="9b4de-138">**Name**</span></span>  
 <span data-ttu-id="9b4de-139">詳細レポートで定義されているパラメーターの名前のテキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="9b4de-139">Type text that is the name of a parameter defined in the drillthrough report.</span></span>  
  
 <span data-ttu-id="9b4de-140">**Value**</span><span class="sxs-lookup"><span data-stu-id="9b4de-140">**Value**</span></span>  
 <span data-ttu-id="9b4de-141">詳細レポート内の名前付きパラメーターに渡す値を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="9b4de-141">Type or select a value to pass for the named parameter in the drillthrough report.</span></span> <span data-ttu-id="9b4de-142">式を編集するには、**式**([*fx*]) ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b4de-142">Click the **Expression** (*fx*) button to edit the expression.</span></span>  
  
 <span data-ttu-id="9b4de-143">**[省略]**</span><span class="sxs-lookup"><span data-stu-id="9b4de-143">**Omit**</span></span>  
 <span data-ttu-id="9b4de-144">パラメーターを実行しないようにする場合にオンにします。</span><span class="sxs-lookup"><span data-stu-id="9b4de-144">Select to prevent the parameter from running.</span></span> <span data-ttu-id="9b4de-145">既定では、このチェック ボックスはオフになっており、アクティブではありません。</span><span class="sxs-lookup"><span data-stu-id="9b4de-145">By default, this check box is cleared and not active.</span></span> <span data-ttu-id="9b4de-146">このチェックボックスをオンにするには、**式**([*fx*]) ボタンをクリックし、「 **True** 」と入力するか、式を作成します。</span><span class="sxs-lookup"><span data-stu-id="9b4de-146">To select the check box, click the **Expression** (*fx*) button and either type **True** or create an expression.</span></span> <span data-ttu-id="9b4de-147">このチェック ボックスは、 **[式]** ダイアログ ボックスで **[OK]** をクリックするとオンになります。</span><span class="sxs-lookup"><span data-stu-id="9b4de-147">The check box is selected when you click **OK** in the **Expression** dialog box.</span></span>  
  
 <span data-ttu-id="9b4de-148">**[ブックマークに移動する]**</span><span class="sxs-lookup"><span data-stu-id="9b4de-148">**Go to bookmark**</span></span>  
 <span data-ttu-id="9b4de-149">現在のレポート内のブックマークへのリンクを定義します。</span><span class="sxs-lookup"><span data-stu-id="9b4de-149">Choose this option to define a link to a bookmark in the current report.</span></span> <span data-ttu-id="9b4de-150">**[ブックマークに移動する]** をクリックすると、次のオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9b4de-150">The following additional option appears when you select **Go to bookmark**.</span></span>  
  
 <span data-ttu-id="9b4de-151">**[ブックマークの選択]**</span><span class="sxs-lookup"><span data-stu-id="9b4de-151">**Select bookmark**</span></span>  
 <span data-ttu-id="9b4de-152">レポートのブックマーク ID を入力または選択し、ユーザーがリンクをクリックしたときに、そのブックマークに移動するようにします。</span><span class="sxs-lookup"><span data-stu-id="9b4de-152">Type or select the bookmark ID for the report to jump to when the user clicks the link.</span></span> <span data-ttu-id="9b4de-153">式を変更するには、式 ([**fx**]) ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b4de-153">Click the Expression (**fx**) button to change the expression.</span></span> <span data-ttu-id="9b4de-154">ブックマーク ID には、静的 ID、または結果がブックマーク ID になる式のいずれかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="9b4de-154">The bookmark ID can be either a static ID or an expression that evaluates to a bookmark ID.</span></span> <span data-ttu-id="9b4de-155">式には、ブックマーク ID を含むフィールドを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="9b4de-155">The expression can include a field that contains a bookmark ID.</span></span>  
  
 <span data-ttu-id="9b4de-156">ブックマークにリンクするには、まずレポート アイテムの Bookmark プロパティを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b4de-156">To link to a bookmark, you must first set the Bookmark property of a report item.</span></span> <span data-ttu-id="9b4de-157">Bookmark プロパティを設定するには、レポート アイテムを選択し、プロパティ ペインでブックマーク ID の値または式 (SalesChart、5TopSales など) を入力します。</span><span class="sxs-lookup"><span data-stu-id="9b4de-157">To set the Bookmark property, select a report item, and in the Properties pane, type a value or expression for the bookmark ID; for example, SalesChart or 5TopSales.</span></span>  
  
 <span data-ttu-id="9b4de-158">**[URL に移動する]**</span><span class="sxs-lookup"><span data-stu-id="9b4de-158">**Go to URL**</span></span>  
 <span data-ttu-id="9b4de-159">Web ページへのリンクを定義します。</span><span class="sxs-lookup"><span data-stu-id="9b4de-159">Choose this option to define a link to a Web page.</span></span> <span data-ttu-id="9b4de-160">Web ページの URL、または結果が Web ページの URL になる式を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="9b4de-160">Type or select the URL of a Web page or an expression that evaluates to the URL of a Web page.</span></span> <span data-ttu-id="9b4de-161">式を変更するには、**式**([*fx*]) ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b4de-161">Click the **Expression** (*fx*) button to change the expression.</span></span> <span data-ttu-id="9b4de-162">この式には、URL が格納されているフィールドを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="9b4de-162">This expression can include a field that contains a URL.</span></span> <span data-ttu-id="9b4de-163">**[URL に移動する]** をクリックすると、次のオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9b4de-163">The following additional option appears when you select **Go to URL**.</span></span>  
  
 <span data-ttu-id="9b4de-164">**[URL の選択]**</span><span class="sxs-lookup"><span data-stu-id="9b4de-164">**Select URL**</span></span>  
 <span data-ttu-id="9b4de-165">アイテムの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="9b4de-165">Type or enter the URL of the item.</span></span> <span data-ttu-id="9b4de-166">ネイティブ モード用に構成されているレポート サーバーにアイテムをパブリッシュする場合は、完全パスまたは相対パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="9b4de-166">For an item published to a report server configured for native mode, use a full or relative path.</span></span> <span data-ttu-id="9b4de-167">たとえば、http:// *\<servername>* /images/image1.jpg します。</span><span class="sxs-lookup"><span data-stu-id="9b4de-167">For example, http://*\<servername>*/images/image1.jpg.</span></span> <span data-ttu-id="9b4de-168">SharePoint 統合モードで構成されているレポートサーバーにアイテムをパブリッシュする場合は、完全修飾 URL を使用します (たとえば、http:// *\<SharePointservername>/\<site>* /Documents/images/image1.jpg)。</span><span class="sxs-lookup"><span data-stu-id="9b4de-168">For an item published to a report server configured in SharePoint integrated mode, use a fully qualified URL (for example, http://*\<SharePointservername>/\<site>*/Documents/images/image1.jpg).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b4de-169">参照</span><span class="sxs-lookup"><span data-stu-id="9b4de-169">See Also</span></span>  
 <span data-ttu-id="9b4de-170">[グラフ &#40;レポートビルダーと SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9b4de-170">[Charts &#40;Report Builder and SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="9b4de-171">[ダイアログボックス、ペイン、およびウィザードのヘルプのレポートビルダー](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="9b4de-171">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 <span data-ttu-id="9b4de-172">[レポートパラメーター &#40;レポートビルダーとレポートデザイナー&#41;](report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="9b4de-172">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="9b4de-173">[サブレポートとパラメーター &#40;レポートビルダーと SSRS に追加&#41;](report-design/add-a-subreport-and-parameters-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9b4de-173">[Add a Subreport and Parameters &#40;Report Builder and SSRS&#41;](report-design/add-a-subreport-and-parameters-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="9b4de-174">対話的な並べ替え、ドキュメント マップ、およびリンク &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9b4de-174">Interactive Sort, Document Maps, and Links &#40;Report Builder and SSRS&#41;</span></span>](report-design/interactive-sort-document-maps-and-links-report-builder-and-ssrs.md)  
  
  
