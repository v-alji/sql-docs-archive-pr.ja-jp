---
title: レポートの印刷 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4bad1b6e-7d94-4b17-9502-ccd3dce0fdd9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3004734226e67ec435e90a4e62895c94173b23d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633784"
---
# <a name="print-reports-report-builder-and-ssrs"></a><span data-ttu-id="a25d9-102">レポートの印刷 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="a25d9-102">Print Reports (Report Builder and SSRS)</span></span>
  <span data-ttu-id="a25d9-103">レポートをレポート サーバーに保存した後は、ブラウザーやレポート マネージャーのほか、エクスポートされたレポートの表示に使用する任意のアプリケーションで、レポートを表示および印刷できます。</span><span class="sxs-lookup"><span data-stu-id="a25d9-103">After you save a report to a report server, you can view and print the report from a browser, Report Manager, or any application that you use to view an exported report.</span></span> <span data-ttu-id="a25d9-104">レポートを保存する前にプレビューする場合は、印刷することができます。</span><span class="sxs-lookup"><span data-stu-id="a25d9-104">Before saving a report, you can print it when you preview it.</span></span>  
  
 <span data-ttu-id="a25d9-105">すべての印刷処理は、要求時にクライアント コンピューター上で行われます。</span><span class="sxs-lookup"><span data-stu-id="a25d9-105">All print processing is performed on demand and on the client computer.</span></span> <span data-ttu-id="a25d9-106">Web サーバーに接続されているプリンターに直接レポート サーバーから印刷ジョブを送信できるようなサーバー側印刷機能はありません。</span><span class="sxs-lookup"><span data-stu-id="a25d9-106">There is no server-side print functionality that enables you to route a print job directly from a report server to a printer that is attached to the Web server.</span></span> <span data-ttu-id="a25d9-107">プリンターや印刷オプションは、個々のレポート ユーザーが標準の **[印刷]** ダイアログ ボックスを使用して選択します。</span><span class="sxs-lookup"><span data-stu-id="a25d9-107">Printers and print options are selected by individual report users by using a standard **Print** dialog box.</span></span>  
  
 <span data-ttu-id="a25d9-108">印刷専用のレポートをデザインするレポート作成者は、改ページ、ページのヘッダーとフッター、式、背景画像などを使用して、印刷用のデザインを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a25d9-108">Report authors who design reports specifically for print output can use page breaks, page headers and footers, expressions, and background images to create a print-based design.</span></span> <span data-ttu-id="a25d9-109">印刷用のレポート デザイン要素としては、たとえば、どのレポートの裏面にもよく印刷される使用条件や、レターヘッドを模したグラフィック要素やテキスト要素などが考えられます。</span><span class="sxs-lookup"><span data-stu-id="a25d9-109">Examples of report design elements intended for print output might include terms and conditions that you print on the back of every report, or graphic and text elements that mimic letterhead.</span></span>  
  
 <span data-ttu-id="a25d9-110">表示形式によってページの割り当て方法が異なるため、すべてのレポートのすべての表示形式で最適な印刷結果が得られるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="a25d9-110">Due to the way pagination is implemented for different rendering formats, you might not be able to achieve optimum print output results for every report in every rendering format.</span></span> <span data-ttu-id="a25d9-111">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="a25d9-111">The following list provides examples:</span></span>  
  
1.  <span data-ttu-id="a25d9-112">レポートのページはデータ量の変化に適応するようにデザインされます。</span><span class="sxs-lookup"><span data-stu-id="a25d9-112">Report pages are designed to accommodate variable amounts of data.</span></span> <span data-ttu-id="a25d9-113">たとえば、マトリックスを含むレポートでは、ユーザーが行や列の表示を対話的に切り替えることによって、ページが上下左右に広がる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a25d9-113">Reports that include a matrix, for example, can cause a page to grow both horizontally and vertically depending on whether a user interactively toggles rows and columns.</span></span> <span data-ttu-id="a25d9-114">この場合、マトリックスを展開したユーザーと展開していないユーザーとでは、印刷結果が異なります。</span><span class="sxs-lookup"><span data-stu-id="a25d9-114">A user who does not expand a matrix will get different print results than a user who does.</span></span>  
  
2.  <span data-ttu-id="a25d9-115">横置きモードと縦置きモードの両方のページを同じレポートで使用することはできません。また、印刷用のレイアウトを作成して、それをブラウザーやその他のアプリケーションで表示されるレポートのレイアウトと置き換えたり、両方のレイアウトを共存させたりすることもできません。</span><span class="sxs-lookup"><span data-stu-id="a25d9-115">You cannot combine landscape and portrait mode pages in the same report, nor is there a way to create a print-based layout that replaces or exists alongside the layout of a report as rendered in a browser or other application.</span></span>  
  
3.  <span data-ttu-id="a25d9-116">エクスポートしたレポートでは、ほとんどの場合、レポートに表示されるすべての要素 (ユーザーがコンピューターの画面上で見るすべての要素) がレポートの印刷結果に含まれます。</span><span class="sxs-lookup"><span data-stu-id="a25d9-116">For most exported reports, report printouts include everything that is visible on the report, as viewed by the user on a computer monitor.</span></span> <span data-ttu-id="a25d9-117">レポート デザイン画面上の空白は保持されます。</span><span class="sxs-lookup"><span data-stu-id="a25d9-117">White space from the report design surface is preserved.</span></span> <span data-ttu-id="a25d9-118">水平方向の余分な空白ページを追加または削除するには、レポートのページの幅を変更します。</span><span class="sxs-lookup"><span data-stu-id="a25d9-118">To add or remove extra blank pages horizontally, change the report page width.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a25d9-119">ブラウザーの印刷コマンドを使用して HTML レポートを印刷すると、最初のページの内容しか印刷されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="a25d9-119">HTML report printouts may contain only the content on the first page if you are using the browser's Print command.</span></span> <span data-ttu-id="a25d9-120">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のクライアント側印刷機能を使用すると、より優れた HTML レポートの印刷結果を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="a25d9-120">You can achieve better results if you print HTML reports using the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] client printing functionality.</span></span> <span data-ttu-id="a25d9-121">詳細については、「 [印刷コントロールを使用したブラウザーからのレポートの印刷 (レポート ビルダーおよび SSRS)](print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a25d9-121">For more information, see [Print Reports from a Browser with the Print Control &#40;Report Builder and SSRS&#41;](print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="in-this-section"></a><span data-ttu-id="a25d9-122">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a25d9-122">In This Section</span></span>  
 [<span data-ttu-id="a25d9-123">印刷コントロールを使用したブラウザーからのレポートの印刷 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="a25d9-123">Print Reports from a Browser with the Print Control &#40;Report Builder and SSRS&#41;</span></span>](print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md)  
 <span data-ttu-id="a25d9-124">クライアント側印刷機能を使用して Web ブラウザーやレポート マネージャーからレポートを印刷する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a25d9-124">Describes how to use client-side printing to print reports from your Web browser or Report Manager.</span></span>  
  
 [<span data-ttu-id="a25d9-125">他のアプリケーションからのレポートの印刷 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="a25d9-125">Print Reports from Other Applications &#40;Report Builder and SSRS&#41;</span></span>](print-reports-from-other-applications-report-builder-and-ssrs.md)  
 <span data-ttu-id="a25d9-126">別のアプリケーションにエクスポートされたレポートを印刷する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a25d9-126">Describes how to print reports exported to another application.</span></span>  
  
 [<span data-ttu-id="a25d9-127">レポートの印刷 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="a25d9-127">Print a Report &#40;Report Builder and SSRS&#41;</span></span>](print-a-report-report-builder-and-ssrs.md)  
 <span data-ttu-id="a25d9-128">レポートを印刷する手順、ページの余白を制御する手順、およびハード改ページ レンダラー (PDF、画像、または印刷) によってレンダリングされるレポートの用紙サイズを指定する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="a25d9-128">Provides step-by-step instructions on how to print a report, how to control the margins on a page, and on how to specify the paper size for reports that will be rendered by hard-page break renderers: PDF, Image, or Print.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a25d9-129">参照</span><span class="sxs-lookup"><span data-stu-id="a25d9-129">See Also</span></span>  
 <span data-ttu-id="a25d9-130">[レポートのエクスポート &#40;レポートビルダーと SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a25d9-130">[Exporting Reports &#40;Report Builder and SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a25d9-131">[ページヘッダーとページフッター &#40;レポートビルダーと SSRS&#41;](../report-design/page-headers-and-footers-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a25d9-131">[Page Headers and Footers &#40;Report Builder and SSRS&#41;](../report-design/page-headers-and-footers-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a25d9-132">[&#40;レポートビルダーと SSRS&#41;の画像](../report-design/images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a25d9-132">[Images &#40;Report Builder and SSRS&#41;](../report-design/images-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="a25d9-133">Reporting Services の改ページ &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="a25d9-133">Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;</span></span>](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)  
  
  
