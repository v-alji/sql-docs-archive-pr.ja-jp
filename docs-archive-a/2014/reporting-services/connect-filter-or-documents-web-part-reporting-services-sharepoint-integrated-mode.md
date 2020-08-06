---
title: フィルター Web パーツまたはドキュメント Web パーツの接続 (SharePoint 統合モードの Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Filter Web Part [Reporting Services]
- SharePoint integration [Reporting Services], Web Parts
- Report Viewer Web Part [Reporting Services]
- Documents Web Part [Reporting Services]
ms.assetid: 6a303135-c0ef-44cd-a423-1cea8df3dcf3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5ea7b9f9aba128052ae6ac7f05ef40517eb50e6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633793"
---
# <a name="connect-filter-or-documents-web-part-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="0de4b-102">フィルター Web パーツまたはドキュメント Web パーツの接続 (Reporting Services の SharePoint 統合モード)</span><span class="sxs-lookup"><span data-stu-id="0de4b-102">Connect Filter or Documents Web Part (Reporting Services in SharePoint Integrated Mode)</span></span>
  <span data-ttu-id="0de4b-103">SharePoint 製品を使用している場合、フィルター Web パーツまたはドキュメント Web パーツとレポート ビューアー Web パーツを含む、ダッシュボードや Web パーツ ページを作成できます。</span><span class="sxs-lookup"><span data-stu-id="0de4b-103">If you are using a SharePoint product, you can create a dashboard or Web Part Page that includes a Filter Web Part or Documents Web part and a Report Viewer Web Part.</span></span> <span data-ttu-id="0de4b-104">サポートされているバージョンは [!INCLUDE[SPF2010](../includes/spf2010-md.md)] または [!INCLUDE[SPS2010](../includes/sps2010-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="0de4b-104">Supported versions are [!INCLUDE[SPF2010](../includes/spf2010-md.md)] or [!INCLUDE[SPS2010](../includes/sps2010-md.md)].</span></span> <span data-ttu-id="0de4b-105">[!INCLUDE[winSPServ3](../includes/winspserv3-md.md)] または [!INCLUDE[offSPServ](../includes/offspserv-md.md)] 2007 もサポートされています。</span><span class="sxs-lookup"><span data-stu-id="0de4b-105">Also supported are [!INCLUDE[winSPServ3](../includes/winspserv3-md.md)] or [!INCLUDE[offSPServ](../includes/offspserv-md.md)] 2007.</span></span> <span data-ttu-id="0de4b-106">フィルター Web パーツを接続することによって、フィルター値をフィルター Web パーツで選択するユーザーは、同じページでパラメーター化されたレポートに値を送信できるようになります。</span><span class="sxs-lookup"><span data-stu-id="0de4b-106">By connecting a Filter Web Part, users who select filter values in a Filter Web Part can send the value to a parameterized report on the same page.</span></span> <span data-ttu-id="0de4b-107">ドキュメント Web パーツを接続することによって、ドキュメント ライブラリでレポートをクリックするユーザーは、隣接するレポート ビューアー Web パーツでレポートを表示できるようになります。</span><span class="sxs-lookup"><span data-stu-id="0de4b-107">By connecting a Documents Web Part, users who click on reports in the Documents library can view the report in an adjacent Report Viewer Web Part.</span></span>  
  
 <span data-ttu-id="0de4b-108">フィルター Web パーツは、レポートで値を 1 つ以上のパラメーターに送信するために使用します。</span><span class="sxs-lookup"><span data-stu-id="0de4b-108">The Filter Web Part is used to send values to one or more parameters on a report.</span></span> <span data-ttu-id="0de4b-109">フィルター Web パーツを使用するには、この Web パーツによって送信される値、データ型、および形式との互換性がある、この Web パーツ用のパラメーターをレポートに定義しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="0de4b-109">To use a Filter Web Part, the report must have parameters defined for it that are compatible with the values, data type, and format sent by the Web Part.</span></span>  
  
 <span data-ttu-id="0de4b-110">ドキュメント Web パーツは、ホーム サイトのドキュメント ライブラリに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="0de4b-110">The Documents Web Part is associated with the Documents library of the Home site.</span></span> <span data-ttu-id="0de4b-111">ドキュメント ライブラリからアイテムを表示、追加、または削除するには、 **[すべてのサイト コンテンツの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0de4b-111">To view, add, or remove items from the Documents library, click **View All Site Content**.</span></span> <span data-ttu-id="0de4b-112">ライブラリで、 **[ドキュメント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0de4b-112">In Libraries, click **Documents**.</span></span> <span data-ttu-id="0de4b-113">**[新規]**、 **[アップロード]**、および **[アクション]** メニューを使用してドキュメント ライブラリのアイテムを管理できます。</span><span class="sxs-lookup"><span data-stu-id="0de4b-113">You can use the **New**, **Upload**, and **Actions** menu to manage the items in the Documents library.</span></span>  
  
### <a name="to-connect-a-filter-web-part"></a><span data-ttu-id="0de4b-114">フィルター Web パーツを接続するには</span><span class="sxs-lookup"><span data-stu-id="0de4b-114">To connect a Filter Web Part</span></span>  
  
1.  <span data-ttu-id="0de4b-115">Web パーツ ページまたはダッシュボードを開くか、作成します。</span><span class="sxs-lookup"><span data-stu-id="0de4b-115">Open or create the Web Part page or dashboard.</span></span>  
  
2.  <span data-ttu-id="0de4b-116">**[サイトの操作]** メニューの **[ページの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0de4b-116">On the **Site Actions** menu, click **Edit Page**.</span></span>  
  
3.  <span data-ttu-id="0de4b-117">[ **Web パーツの追加] を**クリックします。</span><span class="sxs-lookup"><span data-stu-id="0de4b-117">Click **Add a Web Part**.</span></span>  
  
4.  <span data-ttu-id="0de4b-118">[**すべての Web パーツ**の [**その他**] カテゴリで、[ **SQL Server Reporting Services レポートビューアー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0de4b-118">In **All Web Parts**, in the **Miscellaneous** category, select **SQL Server Reporting Services Report Viewer**.</span></span>  
  
5.  <span data-ttu-id="0de4b-119">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0de4b-119">Click **Add**.</span></span> <span data-ttu-id="0de4b-120">Web パーツが、ゾーンの一番上に追加されます。</span><span class="sxs-lookup"><span data-stu-id="0de4b-120">The Web Part is added at the top of the zone.</span></span>  
  
6.  <span data-ttu-id="0de4b-121">同じ Web パーツページまたはダッシュボードの別のゾーンで、[ **Web パーツの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0de4b-121">On another zone in the same Web Part page or dashboard, click **Add a Web Part**.</span></span>  
  
7.  <span data-ttu-id="0de4b-122">[**すべての Web パーツ**の [**フィルター** ] セクションで、Web パーツを選択します。</span><span class="sxs-lookup"><span data-stu-id="0de4b-122">In **All Web Parts**, in the **Filters** section, select a Web Part.</span></span>  
  
8.  <span data-ttu-id="0de4b-123">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0de4b-123">Click **Add**.</span></span> <span data-ttu-id="0de4b-124">Web パーツが、ゾーンの一番上に追加されます。</span><span class="sxs-lookup"><span data-stu-id="0de4b-124">The Web Part is added at the top of the zone.</span></span>  
  
9. <span data-ttu-id="0de4b-125">Web パーツを含むゾーンで、Web パーツの **[編集]** メニューの **[接続]** をポイントし、 **[フィルター値の送信先]** をポイントして [ **レポート ビューアー** - *レポート名*] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0de4b-125">In the zone that contains the Web Part, click the Web Part **edit** menu, point to **Connections**, point to **Send Filter Values To**, and then select **Report Viewer** - *report name*.</span></span>  
  
10. <span data-ttu-id="0de4b-126">変更をチェックインし、ページを保存します。</span><span class="sxs-lookup"><span data-stu-id="0de4b-126">Check in your changes and save the page.</span></span>  
  
### <a name="to-connect-a-documents-web-part"></a><span data-ttu-id="0de4b-127">ドキュメント Web パーツを接続するには</span><span class="sxs-lookup"><span data-stu-id="0de4b-127">To connect a Documents Web Part</span></span>  
  
1.  <span data-ttu-id="0de4b-128">Web パーツ ページまたはダッシュボードを開くか、作成します。</span><span class="sxs-lookup"><span data-stu-id="0de4b-128">Open or create the Web Part page or dashboard.</span></span>  
  
2.  <span data-ttu-id="0de4b-129">**[サイトの操作]** メニューの **[ページの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0de4b-129">On the **Site Actions** menu, click **Edit Page**.</span></span>  
  
3.  <span data-ttu-id="0de4b-130">[ **Web パーツの追加] を**クリックします。</span><span class="sxs-lookup"><span data-stu-id="0de4b-130">Click **Add a Web Part**.</span></span>  
  
4.  <span data-ttu-id="0de4b-131">**[すべての Web パーツ]** の **[リストまたはライブラリ]** セクションで **[ドキュメント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0de4b-131">In **All Web Parts**, in the **Lists and Library** section, select **Documents.**</span></span>  
  
5.  <span data-ttu-id="0de4b-132">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0de4b-132">Click **Add**.</span></span> <span data-ttu-id="0de4b-133">Web パーツが、ゾーンの一番上に追加されます。</span><span class="sxs-lookup"><span data-stu-id="0de4b-133">The Web Part is added at the top of the zone.</span></span>  
  
6.  <span data-ttu-id="0de4b-134">ツール ペインの下部で **[適用]** をクリックし、 **[OK]** をクリックしてペインを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0de4b-134">Click **Apply** at the bottom of the tool pane, and then click **OK** to close the pane.</span></span>  
  
7.  <span data-ttu-id="0de4b-135">同じ Web パーツページまたはダッシュボードの別のゾーンで、[ **Web パーツの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0de4b-135">On another zone in the same Web Part page or dashboard, click **Add a Web Part**.</span></span>  
  
8.  <span data-ttu-id="0de4b-136">**[すべての Web パーツ]** の **[その他]** カテゴリで、 **[SQL Server Reporting Services レポート ビューアー].**</span><span class="sxs-lookup"><span data-stu-id="0de4b-136">In **All Web Parts**, in the **Miscellaneous** category, select **SQL Server Reporting Services Report Viewer.**</span></span>  
  
9. <span data-ttu-id="0de4b-137">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0de4b-137">Click **Add**.</span></span> <span data-ttu-id="0de4b-138">Web パーツが、ゾーンの一番上に追加されます。</span><span class="sxs-lookup"><span data-stu-id="0de4b-138">The Web Part is added at the top of the zone.</span></span>  
  
10. <span data-ttu-id="0de4b-139">Web パーツを含むゾーンで、Web パーツの **[編集]** メニューの **[接続]** をポイントし、 **[レポート定義の取得元]** をポイントして **[ドキュメント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0de4b-139">In the zone that contains the Web Part, click the Web Part **edit** menu, point to **Connections**, point to **Get report definitions from**, and then select **Documents**.</span></span>  
  
11. <span data-ttu-id="0de4b-140">変更をチェックインし、ページを保存します。</span><span class="sxs-lookup"><span data-stu-id="0de4b-140">Check in your changes and save the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0de4b-141">参照</span><span class="sxs-lookup"><span data-stu-id="0de4b-141">See Also</span></span>  
 <span data-ttu-id="0de4b-142">[SharePoint 統合モードの Reporting Services &#40;Web ページにレポートビューアー Web パーツを追加&#41;](report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md) </span><span class="sxs-lookup"><span data-stu-id="0de4b-142">[Add the Report Viewer Web Part to a Web Page &#40;Reporting Services in SharePoint Integrated Mode&#41;](report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md) </span></span>  
 <span data-ttu-id="0de4b-143">[SharePoint サイトのレポートビューアー Web パーツ](../../2014/reporting-services/report-viewer-web-part-on-a-sharepoint-site.md) </span><span class="sxs-lookup"><span data-stu-id="0de4b-143">[Report Viewer Web Part on a SharePoint Site](../../2014/reporting-services/report-viewer-web-part-on-a-sharepoint-site.md) </span></span>  
 [<span data-ttu-id="0de4b-144">レポートビューアー Web パーツのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="0de4b-144">Customize the Report Viewer Web Part</span></span>](../../2014/reporting-services/customize-the-report-viewer-web-part.md)  
  
  
