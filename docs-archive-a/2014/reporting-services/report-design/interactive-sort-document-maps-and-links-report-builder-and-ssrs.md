---
title: 対話的な並べ替え、ドキュメント マップ、およびリンク (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: cc6ef408-4a76-408a-9d3f-033481fe21cf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 35d88e89ed14a205153374d44562e6d3fda92e02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739295"
---
# <a name="interactive-sort-document-maps-and-links-report-builder-and-ssrs"></a><span data-ttu-id="756de-102">対話的な並べ替え、ドキュメント マップ、およびリンク (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="756de-102">Interactive Sort, Document Maps, and Links (Report Builder and SSRS)</span></span>
  <span data-ttu-id="756de-103">Web ベースの環境では、ユーザーがレポートと対話できるようにするさまざまな機能を追加できます。</span><span class="sxs-lookup"><span data-stu-id="756de-103">In Web-based environments, you can add a number of features that let your users interact with reports.</span></span> <span data-ttu-id="756de-104">ユーザーは、レポート内の値の並べ替え順序を変更したり、レポート内のアイテムの表示と非表示を切り替えたり、リンクをクリックして他のレポートや Web ページを表示したりできます。</span><span class="sxs-lookup"><span data-stu-id="756de-104">Your users can change the sort order of values in your report, show or hide items in the report, or click links that go to other reports or Web pages.</span></span> <span data-ttu-id="756de-105">また、目次やドキュメント マップを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="756de-105">You can also add a table of contents or document map.</span></span> <span data-ttu-id="756de-106">レポート ユーザーは、目次またはドキュメント マップ内のアイテムをクリックして、レポート内の領域に直接移動できます。</span><span class="sxs-lookup"><span data-stu-id="756de-106">Your report users can click items in the table of contents or document map to jump to areas within a report.</span></span>  
  
 <span data-ttu-id="756de-107">レポート ビルダーおよびレポート デザイナーでは、次のアクションが設定された 3 種類のリンクがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="756de-107">Report Builder and Report Designer support three types of links with the following actions:</span></span>  
  
-   <span data-ttu-id="756de-108">**ブックマーク リンク** 同じレポート内の他の領域に移動します。</span><span class="sxs-lookup"><span data-stu-id="756de-108">**Bookmark links** Jump to other areas within the report.</span></span>  
  
-   <span data-ttu-id="756de-109">**ハイパーリンク** URL アクセスを使用して Web ページのアドレスまたはレポート サーバー上のレポートを指定する URL に移動します。</span><span class="sxs-lookup"><span data-stu-id="756de-109">**Hyperlinks** Jump to URLs that specify the address of Web pages or reports on a report server by using URL access.</span></span>  
  
-   <span data-ttu-id="756de-110">**詳細レポート リンク** 同じレポート サーバー上にあるその他のレポートに移動します。</span><span class="sxs-lookup"><span data-stu-id="756de-110">**Drillthrough report links** Jump to other reports on the same report server.</span></span> <span data-ttu-id="756de-111">詳細については、「[詳細レポート &#40;レポート ビルダーおよび SSRS&#41;](drillthrough-reports-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="756de-111">For more information, see [Drillthrough Reports &#40;Report Builder and SSRS&#41;](drillthrough-reports-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="756de-112">データセット フィールドにバインドされているリンクは、悪意的な改ざんに対して脆弱である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="756de-112">Links that are bound to dataset fields can be vulnerable to tampering for malicious purposes.</span></span> <span data-ttu-id="756de-113">詳細については、msdn.microsoft.com で、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][オンライン ブック](https://go.microsoft.com/fwlink/?LinkId=154888)の「[レポートとリソースの保護](../security/secure-reports-and-resources.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="756de-113">For more information, see [Secure Reports and Resources](../security/secure-reports-and-resources.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][Books Online](https://go.microsoft.com/fwlink/?LinkId=154888) on msdn.microsoft.com.</span></span>  
  
 <span data-ttu-id="756de-114">また、並べ替え、フィルター、表示などのパラメーター参照を含む式を作成すると、ユーザーがレポートの表示や内容を制御できるようになります。</span><span class="sxs-lookup"><span data-stu-id="756de-114">You can also let your users control report display and content by designing expressions that include parameter references for sort, filter, and visibility.</span></span> <span data-ttu-id="756de-115">詳細については、「[レポート パラメーター &#40;レポート ビルダーおよびレポート デザイナー&#41;](report-parameters-report-builder-and-report-designer.md)」、「[データのフィルター、グループ化、および並べ替え &#40;レポート ビルダーおよび SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md)」、および「[データセット フィルター、データ領域フィルター、およびグループ フィルターの追加 &#40;レポート ビルダーおよび SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="756de-115">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md), [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md), and [Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="in-this-section"></a><span data-ttu-id="756de-116">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="756de-116">In This Section</span></span>  
 [<span data-ttu-id="756de-117">対話的な並べ替え (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="756de-117">Interactive Sort &#40;Report Builder and SSRS&#41;</span></span>](interactive-sort-report-builder-and-ssrs.md)  
 <span data-ttu-id="756de-118">対話型の並べ替えボタンを列ヘッダーに追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="756de-118">Explains how to add interactive sort buttons to column headers.</span></span>  
  
 [<span data-ttu-id="756de-119">ドキュメント マップの作成 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="756de-119">Create a Document Map &#40;Report Builder and SSRS&#41;</span></span>](create-a-document-map-report-builder-and-ssrs.md)  
 <span data-ttu-id="756de-120">サイズの大きなレポートでの移動をサポートする目次を追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="756de-120">Explains how to add a table of contents to support navigation in a large report.</span></span>  
  
 [<span data-ttu-id="756de-121">レポートへのブックマークの追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="756de-121">Add a Bookmark to a Report &#40;Report Builder and SSRS&#41;</span></span>](add-a-bookmark-to-a-report-report-builder-and-ssrs.md)  
 <span data-ttu-id="756de-122">ブックマークを追加して、レポート内にリンクを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="756de-122">Explains how to add bookmarks to create links within a report.</span></span>  
  
 [<span data-ttu-id="756de-123">URL へのハイパーリンクの追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="756de-123">Add a Hyperlink to a URL &#40;Report Builder and SSRS&#41;</span></span>](add-a-hyperlink-to-a-url-report-builder-and-ssrs.md)  
 <span data-ttu-id="756de-124">レポートから URL へのリンクを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="756de-124">Explains how to add a link from your report to a URL</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="756de-125">参照</span><span class="sxs-lookup"><span data-stu-id="756de-125">See Also</span></span>  
 [<span data-ttu-id="756de-126">ドリルスルー、ドリルダウン、サブレポート、および入れ子になったデータ領域 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="756de-126">Drillthrough, Drilldown, Subreports, and Nested Data Regions &#40;Report Builder and SSRS&#41;</span></span>](drillthrough-drilldown-subreports-and-nested-data-regions.md)  
  
  
