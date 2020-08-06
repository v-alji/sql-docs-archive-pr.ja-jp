---
title: サブレポート (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ab5bea3a-109e-4c25-92d9-494df7c52dd8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ce30cf575148af11d6485125089beace07fd5429
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631517"
---
# <a name="subreports-report-builder-and-ssrs"></a><span data-ttu-id="82997-102">サブレポート (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="82997-102">Subreports (Report Builder and SSRS)</span></span>
  <span data-ttu-id="82997-103">サブレポートは、メインのレポート本文内に別のレポートを表示するレポート アイテムです。</span><span class="sxs-lookup"><span data-stu-id="82997-103">A subreport is a report item that displays another report inside the body of a main report.</span></span> <span data-ttu-id="82997-104">概念上、レポート内のサブレポートは Web ページ内のフレームとほぼ同じです。</span><span class="sxs-lookup"><span data-stu-id="82997-104">Conceptually, a subreport in a report is similar to a frame in a Web page.</span></span> <span data-ttu-id="82997-105">これは、レポートをレポート内に埋め込むために使用されます。</span><span class="sxs-lookup"><span data-stu-id="82997-105">It is used to embed a report within a report.</span></span> <span data-ttu-id="82997-106">サブレポートには、任意のレポートを使用できます。</span><span class="sxs-lookup"><span data-stu-id="82997-106">Any report can be used as a subreport.</span></span> <span data-ttu-id="82997-107">サブレポートとして表示されるレポートは、レポート サーバー上に保存され、通常は親レポートと同じフォルダーに置かれます。</span><span class="sxs-lookup"><span data-stu-id="82997-107">The report that is displayed as the subreport is stored on a report server, usually in the same folder as the parent report.</span></span> <span data-ttu-id="82997-108">親レポートからサブレポートにパラメーターを渡すようにも設定できます。</span><span class="sxs-lookup"><span data-stu-id="82997-108">You can design the parent report to pass parameters to the subreport.</span></span> <span data-ttu-id="82997-109">パラメーターを使用してサブレポートの各インスタンスのデータをフィルター処理することにより、サブレポートをデータ領域内で繰り返し使用することができます。</span><span class="sxs-lookup"><span data-stu-id="82997-109">A subreport can be repeated within data regions, using a parameter to filter data in each instance of the subreport.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="82997-110">Tablix データ領域でサブレポートを使用する場合は、サブレポートとそのパラメーターが行ごとに処理されます。</span><span class="sxs-lookup"><span data-stu-id="82997-110">If you use a subreport in a tablix data region, the subreport and its parameters will be processed for every row.</span></span> <span data-ttu-id="82997-111">多くの行がある場合、詳細レポートが適切なものであるかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="82997-111">If there are many rows, consider whether a drillthrough report is more appropriate.</span></span>  
  
 <span data-ttu-id="82997-112">![rs_Subreport](../media/rs-subreport.gif "rs_Subreport")</span><span class="sxs-lookup"><span data-stu-id="82997-112">![rs_Subreport](../media/rs-subreport.gif "rs_Subreport")</span></span>  
  
 <span data-ttu-id="82997-113">この図の Sales Order メイン レポートに表示されている連絡先情報は、実際には Contacts サブレポートから取得されたものです。</span><span class="sxs-lookup"><span data-stu-id="82997-113">In this illustration, the contact information displayed in the main Sales Order report actually comes from a Contacts subreport.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="comparing-subreports-and-nested-data-regions"></a><span data-ttu-id="82997-114">サブレポートと入れ子になったデータ領域の比較</span><span class="sxs-lookup"><span data-stu-id="82997-114">Comparing Subreports and Nested Data Regions</span></span>  
 <span data-ttu-id="82997-115">サブレポートを使用してさまざまなデータ グループを表示しようと考えている場合は、代わりにテーブル、マトリックス、グラフなどのデータ領域を使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="82997-115">If you're thinking of using subreports to display separate groups of data, consider using data regions, such as tables, matrices, and charts, instead.</span></span> <span data-ttu-id="82997-116">データ領域を使用しているレポートの方が、サブレポートを使用しているレポートよりもパフォーマンスが優れている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="82997-116">Reports with data regions only may perform better than reports that include subreports.</span></span>  
  
 <span data-ttu-id="82997-117">同じデータ領域内の同じデータ ソースから取得されるデータ グループを入れ子にする場合は、データ領域を使用してください。</span><span class="sxs-lookup"><span data-stu-id="82997-117">Use data regions to nest groups of data from the same data source within a single data region.</span></span> <span data-ttu-id="82997-118">同じデータ領域内の異なるデータ ソースから取得されるデータのグループを入れ子にしたり、複数の親レポートで同じサブレポートを再利用したり、別のレポート内にスタンドアロンのレポートを表示する場合は、サブレポートを使用してください。</span><span class="sxs-lookup"><span data-stu-id="82997-118">Use subreports to nest groups of data from different data sources within a single data region, reuse a subreport in multiple parent reports, or display a standalone report inside of another report.</span></span> <span data-ttu-id="82997-119">たとえば、別のレポートの本文内に複数のサブレポートを配置して、"抄録ファイル" を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="82997-119">For example, you can create a "briefing book" by placing multiple subreports inside the body of another report.</span></span>  
  
 <span data-ttu-id="82997-120">データ領域はサブレポートと同じ機能の多くが提供され、柔軟性も同等ですが、パフォーマンスの点で優れています。</span><span class="sxs-lookup"><span data-stu-id="82997-120">Data regions provide much of the same functionality and flexibility as subreports, but with better performance.</span></span> <span data-ttu-id="82997-121">サブレポートは、それぞれのインスタンスが個別のレポートとして処理されるので、レポート サーバーのパフォーマンスに影響することがあります。</span><span class="sxs-lookup"><span data-stu-id="82997-121">Because the report server processes each instance of a subreport as a separate report, performance can be impacted.</span></span> <span data-ttu-id="82997-122">詳細については、「 [入れ子になったデータ領域 &#40;レポート ビルダーおよび SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="82997-122">For more information, see [Nested Data Regions &#40;Report Builder and SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md).</span></span>  
  
## <a name="using-parameters-in-subreports"></a><span data-ttu-id="82997-123">サブレポートでのパラメーターの使用</span><span class="sxs-lookup"><span data-stu-id="82997-123">Using Parameters in Subreports</span></span>  
 <span data-ttu-id="82997-124">親レポートからサブレポートにパラメーターを渡すには、サブレポートとして使用するレポートでレポート パラメーターを定義します。</span><span class="sxs-lookup"><span data-stu-id="82997-124">To pass parameters from the parent report to the subreport, define a report parameter in the report that you use as the subreport.</span></span> <span data-ttu-id="82997-125">親レポートにサブレポートを配置するときに、レポート パラメーターと、親レポートからサブレポート内のレポート パラメーターに渡す値を選択できます。</span><span class="sxs-lookup"><span data-stu-id="82997-125">When you place the subreport in the parent report, you can select the report parameter and a value to pass from the parent report to the report parameter in the subreport.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="82997-126">サブレポートから選択するパラメーターは、クエリ パラメーターではなくレポート パラメーターです。</span><span class="sxs-lookup"><span data-stu-id="82997-126">The parameter that you select from the subreport is a report parameter, not a query parameter.</span></span>  
  
 <span data-ttu-id="82997-127">サブレポートは、レポート本文内またはデータ領域内に配置できます。</span><span class="sxs-lookup"><span data-stu-id="82997-127">You can place a subreport in the main body of the report, or in a data region.</span></span> <span data-ttu-id="82997-128">データ領域にサブレポートを配置する場合、同じサブレポートがグループのインスタンスまたはデータ領域の行ごとに配置されます。</span><span class="sxs-lookup"><span data-stu-id="82997-128">If you place a subreport in a data region, the subreport will repeat with each instance of the group or row in the data region.</span></span> <span data-ttu-id="82997-129">グループまたは行からサブレポートに値を渡すには、サブレポートの値のプロパティで、サブレポート パラメーターに渡す値を含むフィールド用のフィールド式を使用します。</span><span class="sxs-lookup"><span data-stu-id="82997-129">To pass a value from the group or row to the subreport, in the subreport value property, use a field expression for the field containing the value you want to pass to the subreport parameter.</span></span>  
  
 <span data-ttu-id="82997-130">サブレポートの操作方法の詳細については、「[サブレポートおよびパラメーターの追加 &#40;レポート ビルダーおよび SSRS&#41;](add-a-subreport-and-parameters-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="82997-130">For more information about working with subreports, see [Add a Subreport and Parameters &#40;Report Builder and SSRS&#41;](add-a-subreport-and-parameters-report-builder-and-ssrs.md).</span></span>  
  
## <a name="specifying-subreport-names-and-locations"></a><span data-ttu-id="82997-131">サブレポートの名前と場所の指定</span><span class="sxs-lookup"><span data-stu-id="82997-131">Specifying Subreport Names and Locations</span></span>  
 <span data-ttu-id="82997-132">同じレポート サーバー上の異なるフォルダーにあるサブレポートを指定するようにメイン レポートを設定できます。</span><span class="sxs-lookup"><span data-stu-id="82997-132">You can design a main report to specify a subreport in a different folder on the same report server.</span></span>  
  
 <span data-ttu-id="82997-133">サブレポートを指定する構文は、レポート サーバーがネイティブ モードで動作しているか、SharePoint 統合モードで動作しているかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="82997-133">The syntax you use to specify the subreport depends on whether the report server is in native mode or SharePoint integrated mode.</span></span> <span data-ttu-id="82997-134">詳細については、「[外部アイテムへのパスの指定 &#40;レポート ビルダーおよび SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="82997-134">For more information, see [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="82997-135">レポート ビルダーからメイン レポートのサブレポートをプレビューするには、両方のレポートが同じレポート サーバーに存在するか、サブレポートの完全なパスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="82997-135">In Report Builder, to preview a subreport in a main report, both reports must be located in the same report server, or you must specify a full path to the subreport.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82997-136">参照</span><span class="sxs-lookup"><span data-stu-id="82997-136">See Also</span></span>  
 [<span data-ttu-id="82997-137">ドリルスルー、ドリルダウン、サブレポート、および入れ子になったデータ領域 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="82997-137">Drillthrough, Drilldown, Subreports, and Nested Data Regions &#40;Report Builder and SSRS&#41;</span></span>](drillthrough-drilldown-subreports-and-nested-data-regions.md)  
  
  
