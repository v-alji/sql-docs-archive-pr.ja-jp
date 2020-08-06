---
title: '[プレビュー] ビュー | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.previewview.f1
helpviewer_keywords:
- Preview view [Reporting Services]
ms.assetid: 108255d1-5be8-47c1-80f3-1f2a055e4d02
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1ff7c59c3ac5143d4f4103edea1a5ee309046547
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716021"
---
# <a name="preview-view"></a><span data-ttu-id="b622c-102">[プレビュー] ビュー</span><span class="sxs-lookup"><span data-stu-id="b622c-102">Preview View</span></span>
  <span data-ttu-id="b622c-103">**[プレビュー]** ビューを使用すると、表示レポートを表示できます。</span><span class="sxs-lookup"><span data-stu-id="b622c-103">Use **Preview** view to display the rendered report.</span></span> <span data-ttu-id="b622c-104">レポートをプレビューすると、レポート デザイナーでは、レポートがローカルで実行され、[プレビュー] ビューに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b622c-104">When a report is previewed, Report Designer runs the report locally and displays it in the Preview view.</span></span> <span data-ttu-id="b622c-105">プレビュー モードでは、レポート全体が処理されます。</span><span class="sxs-lookup"><span data-stu-id="b622c-105">In preview mode, the report is processed in full.</span></span> <span data-ttu-id="b622c-106">レポートに複雑なクエリや大量のデータが含まれている場合、初回のプレビューは、完了するまでに数分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="b622c-106">If the report has a complex query or has a large amount of data, preview might take several minutes to complete the first time you view it.</span></span> <span data-ttu-id="b622c-107">その後の変更内容が、レポートの形式に関するのみである場合、プレビュー時にはキャッシュされたデータが使用されます。</span><span class="sxs-lookup"><span data-stu-id="b622c-107">For subsequent changes that affect only the format of the report, preview uses cached data.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b622c-108">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] を RemoteApp として実行すると、レポートを **の** [プレビュー] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]ビューに表示することはできません。</span><span class="sxs-lookup"><span data-stu-id="b622c-108">When [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] is run as a RemoteApp, reports cannot be displayed in **Preview** view in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="b622c-109">RemoteApp プログラムは、リモート デスクトップ サービスを使用してリモートでアクセスされるプログラムです。</span><span class="sxs-lookup"><span data-stu-id="b622c-109">RemoteApp programs are programs that are accessed remotely through Remote Desktop Services.</span></span> <span data-ttu-id="b622c-110">詳細については、「[ステップバイステップガイド TS RemoteApp](https://technet.microsoft.com/library/cc730673\(WS.10\).aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b622c-110">For more information, see [TS RemoteApp Step-by-Step Guide](https://technet.microsoft.com/library/cc730673\(WS.10\).aspx).</span></span>  
  
## <a name="options"></a><span data-ttu-id="b622c-111">Options</span><span class="sxs-lookup"><span data-stu-id="b622c-111">Options</span></span>  
 <span data-ttu-id="b622c-112">ツール バーは、プレビュー機能を管理するために使用します。</span><span class="sxs-lookup"><span data-stu-id="b622c-112">Use the toolbar to manage preview functions.</span></span>  
  
 <span data-ttu-id="b622c-113">**[ドキュメント マップの表示/非表示の切り替え]**</span><span class="sxs-lookup"><span data-stu-id="b622c-113">**Show or Hide Document Map**</span></span>  
 <span data-ttu-id="b622c-114">ドキュメント マップがある場合に、ドキュメント マップの表示と非表示を切り替えます。</span><span class="sxs-lookup"><span data-stu-id="b622c-114">Choose this option to show or hide the document map if one exists.</span></span>  
  
 <span data-ttu-id="b622c-115">**［パラメータ エリアの表示/非表示]**</span><span class="sxs-lookup"><span data-stu-id="b622c-115">**Show or Hide Parameter Area**</span></span>  
 <span data-ttu-id="b622c-116">レポートにパラメーターがある場合に、パラメーター ボックスの表示と非表示を切り替えます。</span><span class="sxs-lookup"><span data-stu-id="b622c-116">Choose this option to show or hide the parameters boxes for reports with parameters.</span></span>  
  
 <span data-ttu-id="b622c-117">**最初のページ**</span><span class="sxs-lookup"><span data-stu-id="b622c-117">**First Page**</span></span>  
 <span data-ttu-id="b622c-118">レポートの先頭ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="b622c-118">Choose this option to go to the first page of the report.</span></span>  
  
 <span data-ttu-id="b622c-119">**前のページ**</span><span class="sxs-lookup"><span data-stu-id="b622c-119">**Previous Page**</span></span>  
 <span data-ttu-id="b622c-120">レポートの前のページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="b622c-120">Choose this option to go to the previous page of the report.</span></span>  
  
 <span data-ttu-id="b622c-121">**現在のページ**</span><span class="sxs-lookup"><span data-stu-id="b622c-121">**Current Page**</span></span>  
 <span data-ttu-id="b622c-122">レポートの現在のページを表示します。</span><span class="sxs-lookup"><span data-stu-id="b622c-122">Displays the current page of the report.</span></span>  
  
 <span data-ttu-id="b622c-123">**合計ページ数**</span><span class="sxs-lookup"><span data-stu-id="b622c-123">**Total Pages**</span></span>  
 <span data-ttu-id="b622c-124">レポート内のページ総数を表示します。</span><span class="sxs-lookup"><span data-stu-id="b622c-124">Displays the total number of pages in the report.</span></span>  
  
 <span data-ttu-id="b622c-125">**次のページ**</span><span class="sxs-lookup"><span data-stu-id="b622c-125">**Next Page**</span></span>  
 <span data-ttu-id="b622c-126">レポートの次のページに移動します。</span><span class="sxs-lookup"><span data-stu-id="b622c-126">Choose this option to go to the next page of the report.</span></span>  
  
 <span data-ttu-id="b622c-127">**最後のページ**</span><span class="sxs-lookup"><span data-stu-id="b622c-127">**Last Page**</span></span>  
 <span data-ttu-id="b622c-128">レポートの最終ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="b622c-128">Choose this option to go to the last page of the report.</span></span>  
  
 <span data-ttu-id="b622c-129">**[親レポートに戻る]**</span><span class="sxs-lookup"><span data-stu-id="b622c-129">**Back to Parent Report**</span></span>  
 <span data-ttu-id="b622c-130">親のレポートに移動します。</span><span class="sxs-lookup"><span data-stu-id="b622c-130">Choose this option to go to the parent report.</span></span> <span data-ttu-id="b622c-131">このオプションは詳細レポートを参照する際に使用します。</span><span class="sxs-lookup"><span data-stu-id="b622c-131">This option is used to navigate drillthrough reports.</span></span>  
  
 <span data-ttu-id="b622c-132">**[表示の停止]**</span><span class="sxs-lookup"><span data-stu-id="b622c-132">**Stop Rendering**</span></span>  
 <span data-ttu-id="b622c-133">表示処理を停止します。</span><span class="sxs-lookup"><span data-stu-id="b622c-133">Choose this option to stop the rendering process.</span></span>  
  
 <span data-ttu-id="b622c-134">**[更新]**</span><span class="sxs-lookup"><span data-stu-id="b622c-134">**Refresh**</span></span>  
 <span data-ttu-id="b622c-135">データ キャッシュを更新し、レポートを再度実行します。</span><span class="sxs-lookup"><span data-stu-id="b622c-135">Choose this option to refresh the data cache and run the report again.</span></span>  
  
 <span data-ttu-id="b622c-136">**印刷**</span><span class="sxs-lookup"><span data-stu-id="b622c-136">**Print**</span></span>  
 <span data-ttu-id="b622c-137">レポートを印刷します。</span><span class="sxs-lookup"><span data-stu-id="b622c-137">Choose this option to print the report.</span></span>  
  
 <span data-ttu-id="b622c-138">**印刷レイアウト**</span><span class="sxs-lookup"><span data-stu-id="b622c-138">**Print Layout**</span></span>  
 <span data-ttu-id="b622c-139">レポート プレビューにするか、印刷されるページと同じ表示にするかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b622c-139">Choose this option to toggle between the preview report and the view of the report as it will appear on the printed page.</span></span>  
  
 <span data-ttu-id="b622c-140">**ページ設定**</span><span class="sxs-lookup"><span data-stu-id="b622c-140">**Page Setup**</span></span>  
 <span data-ttu-id="b622c-141">ページと印刷のプロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="b622c-141">Choose this option to conveniently change page and print properties.</span></span> <span data-ttu-id="b622c-142">印刷する前に変更を表示するには、[印刷レイアウト] を使用します。</span><span class="sxs-lookup"><span data-stu-id="b622c-142">Use Print Layout to view changes before printing.</span></span>  
  
 <span data-ttu-id="b622c-143">**エクスポート**</span><span class="sxs-lookup"><span data-stu-id="b622c-143">**Export**</span></span>  
 <span data-ttu-id="b622c-144">表示レポートを特定の形式でエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="b622c-144">Choose this option to export the rendered report in a specific format.</span></span>  
  
 <span data-ttu-id="b622c-145">**Zoom**</span><span class="sxs-lookup"><span data-stu-id="b622c-145">**Zoom**</span></span>  
 <span data-ttu-id="b622c-146">レポートを拡大または縮小するための、拡大率または縮小率を選択します。</span><span class="sxs-lookup"><span data-stu-id="b622c-146">Select a zoom factor to zoom in or out on the report.</span></span>  
  
 <span data-ttu-id="b622c-147">**検索テキスト**</span><span class="sxs-lookup"><span data-stu-id="b622c-147">**Search Text**</span></span>  
 <span data-ttu-id="b622c-148">レポート内で検索するテキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="b622c-148">Type text to search for a match within the report.</span></span> <span data-ttu-id="b622c-149">検索演算子は使用できません。</span><span class="sxs-lookup"><span data-stu-id="b622c-149">You cannot use search operators.</span></span> <span data-ttu-id="b622c-150">**[検索]** をクリックすると、最初に一致するインスタンスが検索されます。</span><span class="sxs-lookup"><span data-stu-id="b622c-150">Click **Find** to search for the first instance.</span></span>  
  
 <span data-ttu-id="b622c-151">**探す**</span><span class="sxs-lookup"><span data-stu-id="b622c-151">**Find**</span></span>  
 <span data-ttu-id="b622c-152">レポート内で検索テキストの検索を開始します。</span><span class="sxs-lookup"><span data-stu-id="b622c-152">Choose this option to begin searching the report for the search text.</span></span>  
  
 <span data-ttu-id="b622c-153">**[次を検索]**</span><span class="sxs-lookup"><span data-stu-id="b622c-153">**Find Next**</span></span>  
 <span data-ttu-id="b622c-154">検索テキストの次のインスタンスを検索します。</span><span class="sxs-lookup"><span data-stu-id="b622c-154">Choose this option to search for the next instance of the search text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b622c-155">参照</span><span class="sxs-lookup"><span data-stu-id="b622c-155">See Also</span></span>  
 <span data-ttu-id="b622c-156">[レポートのプレビュー](../reports/previewing-reports.md) </span><span class="sxs-lookup"><span data-stu-id="b622c-156">[Previewing Reports](../reports/previewing-reports.md) </span></span>  
 [<span data-ttu-id="b622c-157">レポート デザイナーの F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="b622c-157">Report Designer F1 Help</span></span>](report-designer-f1-help.md)  
  
  
