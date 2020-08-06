---
title: レポートビルダーの開始 (レポートビルダー) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Builder, launching
- launching Report Builder
- SharePoint integration [Reporting Services], starting Report Builder
- starting Report Builder
ms.assetid: 8c8c7d2e-b315-418d-bf65-90e7685e4259
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 28c046f5f46e1633cb108bf2d7f1803d6adc702b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643199"
---
# <a name="start-report-builder-report-builder"></a><span data-ttu-id="3c755-102">レポート ビルダーの起動 (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="3c755-102">Start Report Builder (Report Builder)</span></span>
  [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]<span data-ttu-id="3c755-103">には、スタンドアロンバージョンとバージョンのレポートビルダーが含まれてい [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="3c755-103">includes stand-alone and [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] versions of Report Builder.</span></span> <span data-ttu-id="3c755-104">[!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] バージョンは、ネイティブ モードまたは SharePoint 統合モードでインストールされた [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] と共に使用できます。</span><span class="sxs-lookup"><span data-stu-id="3c755-104">The [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] version can be used with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installed in native or SharePoint integrated mode.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3c755-105">レポート ビルダーは、Itanium 64 ベースのコンピューターにはインストールできません。</span><span class="sxs-lookup"><span data-stu-id="3c755-105">Report Builder cannot be installed on Itanium 64-based computers.</span></span> <span data-ttu-id="3c755-106">[!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] バージョンおよびスタンドアロン バージョンのレポート ビルダーの場合も同様です。</span><span class="sxs-lookup"><span data-stu-id="3c755-106">This applies to the [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] and stand-alone versions of Report Builder.</span></span>  
  
 <span data-ttu-id="3c755-107">[!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)]開いているレポートビルダーのバージョンがレポートビルダーの以前のバージョンである場合は、管理者に連絡して、のバージョンを使用するようにレポートマネージャーおよび SharePoint サイトを更新することができ [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] レポートビルダー</span><span class="sxs-lookup"><span data-stu-id="3c755-107">If the [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] version of Report Builder that opens is an earlier version of Report Builder, contact your administrator who can update Report Manager and the SharePoint site to use the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of Report Builder</span></span>  
  
 <span data-ttu-id="3c755-108">[!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] バージョンのレポート ビルダーを使用して、SharePoint にパブリッシュされている [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] ブックについてのレポートを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="3c755-108">You can also use the [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] version of Report Builder to create reports on a [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] workbook that has been published to SharePoint.</span></span> <span data-ttu-id="3c755-109">でレポートビルダーを使用する方法の詳細につい [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ては、「technet.microsoft.com で[PowerPivot データを使用して Reporting Services レポートを作成する](https://go.microsoft.com/fwlink/?LinkId=185238)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c755-109">For more information about using Report Builder with [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], see [Create a Reporting Services Report with PowerPivot Data](https://go.microsoft.com/fwlink/?LinkId=185238) on technet.microsoft.com.</span></span>  
  
 <span data-ttu-id="3c755-110">ローカルコンピューターの [**スタート**] メニューからスタンドアロンレポートビルダー起動するには、ツールを使用できるようにする前に、ユーザーまたは管理者がレポートビルダーをコンピューターに直接インストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c755-110">To start Report Builder stand-alone from the **Start** menu on your local computer, you or an administrator must install Report Builder directly on your computer before the tool is available for you to use.</span></span> <span data-ttu-id="3c755-111">スタンドアロン バージョンは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のインストール時にインストールされません。別途ダウンロードして、インストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c755-111">The stand-alone version is not installed when you install [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]; you must download and install it separately.</span></span> <span data-ttu-id="3c755-112">レポートビルダーをダウンロードするには、「 [Microsoft® SQL Server®2012レポートビルダー](https://go.microsoft.com/fwlink/?LinkId=401502)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c755-112">To download Report Builder, see [Microsoft® SQL Server® 2012 Report Builder](https://go.microsoft.com/fwlink/?LinkId=401502).</span></span>  
  
### <a name="to-start-report-builder-clickonce-from-report-manager"></a><span data-ttu-id="3c755-113">レポート マネージャーからレポート ビルダー ClickOnce を起動するには</span><span class="sxs-lookup"><span data-stu-id="3c755-113">To start Report Builder ClickOnce from Report Manager</span></span>  
  
1.  <span data-ttu-id="3c755-114">Web ブラウザーで、アドレス バーにレポート サーバーの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="3c755-114">In your Web browser, type the URL for your report server in the address bar.</span></span> <span data-ttu-id="3c755-115">既定では、URL は http:// \<*servername*> /レポートです。</span><span class="sxs-lookup"><span data-stu-id="3c755-115">By default, the URL is http://\<*servername*>/reports.</span></span> <span data-ttu-id="3c755-116">レポート マネージャーが開きます。</span><span class="sxs-lookup"><span data-stu-id="3c755-116">Report Manager opens.</span></span>  
  
2.  <span data-ttu-id="3c755-117">**[レポート ビルダー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c755-117">Click **Report Builder**.</span></span>  
  
     <span data-ttu-id="3c755-118">レポート ビルダーが開き、レポート サーバー上でレポートを作成したり、レポートを開いたりできます。</span><span class="sxs-lookup"><span data-stu-id="3c755-118">Report Builder opens and you can create a report or open a report on the report server.</span></span>  
  
### <a name="to-start-report-builder-clickonce-using-a-url"></a><span data-ttu-id="3c755-119">URL を使用してレポート ビルダー ClickOnce を起動するには</span><span class="sxs-lookup"><span data-stu-id="3c755-119">To start Report Builder ClickOnce using a URL</span></span>  
  
1.  <span data-ttu-id="3c755-120">Web ブラウザーでアドレス バーに次の URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="3c755-120">In your Web browser, type the following URL in the address bar:</span></span>  
  
     <span data-ttu-id="3c755-121">http:// \<servername> /reportserver/reportbuilder/ReportBuilder_3_0_0_0</span><span class="sxs-lookup"><span data-stu-id="3c755-121">http://\<servername>/reportserver/reportbuilder/ReportBuilder_3_0_0_0.application</span></span>  
  
2.  <span data-ttu-id="3c755-122">Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="3c755-122">Press ENTER.</span></span>  
  
     <span data-ttu-id="3c755-123">レポート ビルダーが開き、レポート サーバー上でレポートを作成したり、レポートを開いたりできます。</span><span class="sxs-lookup"><span data-stu-id="3c755-123">Report Builder opens and you can create a report or open a report on the report server.</span></span>  
  
### <a name="to-start-report-builder-clickonce-in-sharepoint-integrated-mode"></a><span data-ttu-id="3c755-124">レポート ビルダー ClickOnce を SharePoint 統合モードで起動するには</span><span class="sxs-lookup"><span data-stu-id="3c755-124">To start Report Builder ClickOnce in SharePoint integrated mode</span></span>  
  
1.  <span data-ttu-id="3c755-125">目的のライブラリがある SharePoint サイトに移動します。</span><span class="sxs-lookup"><span data-stu-id="3c755-125">Navigate to the SharePoint site that contains the library you want.</span></span>  
  
2.  <span data-ttu-id="3c755-126">ライブラリを開きます。</span><span class="sxs-lookup"><span data-stu-id="3c755-126">Open the library.</span></span>  
  
3.  <span data-ttu-id="3c755-127">**[ドキュメント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c755-127">Click **Documents**.</span></span>  
  
4.  <span data-ttu-id="3c755-128">**[新しいドキュメント]** メニューの **[レポート ビルダー レポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c755-128">On the **New Document** menu, click **Report Builder Report**.</span></span>  
  
     <span data-ttu-id="3c755-129">レポート ビルダーが開き、レポート サーバー上でレポートを作成したり、レポートを開いたりできます。</span><span class="sxs-lookup"><span data-stu-id="3c755-129">Report Builder opens and you can create a report or open a report on the report server.</span></span>  
  
     <span data-ttu-id="3c755-130">**メモ**[**新しいドキュメント**] メニューに [レポートの**レポートビルダー**、**レポートビルダーモデル**]、および [**レポートデータソース**] オプションが表示されない場合は、そのコンテンツの種類を SharePoint ライブラリに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c755-130">**Note** If the **New Document** menu does not list the **Report Builder Report**, **Report Builder Model**, and **Report Data Source** options, their content types need to be added to the SharePoint library.</span></span> <span data-ttu-id="3c755-131">詳細については、msdn.microsoft.com のオンラインブックの「 [SharePoint 統合&#41;モードでのレポートサーバーコンテンツタイプのライブラリへの追加 &#40;Reporting Services](../add-reporting-services-content-types-to-a-sharepoint-library.md) 」を参照してください [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?LinkId=154888) 。</span><span class="sxs-lookup"><span data-stu-id="3c755-131">For more information, see [Add Report Server Content Types to a Library &#40;Reporting Services in SharePoint Integrated Mode&#41;](../add-reporting-services-content-types-to-a-sharepoint-library.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?LinkId=154888) on msdn.microsoft.com.</span></span>  
  
### <a name="to-start-report-builder-stand-alone-from-the-start-menu"></a><span data-ttu-id="3c755-132">[スタート] メニューからレポート ビルダー スタンドアロンを起動するには</span><span class="sxs-lookup"><span data-stu-id="3c755-132">To start Report Builder stand-alone from the Start menu</span></span>  
  
1.  <span data-ttu-id="3c755-133">[スタート] メニューの [**すべてのプログラム**] をクリックし、[レポートビルダー] をクリックし [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)] **Report Builder**ます。</span><span class="sxs-lookup"><span data-stu-id="3c755-133">On the Start menu, click **All Programs**, and then click [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)] **Report Builder**.</span></span>  
  
2.  <span data-ttu-id="3c755-134">**[レポート ビルダー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c755-134">Click **Report Builder** .</span></span>  
  
     <span data-ttu-id="3c755-135">レポート ビルダーが開き、レポートを作成したり、レポートを開いたりできます。</span><span class="sxs-lookup"><span data-stu-id="3c755-135">Report Builder opens and you can create or open a report.</span></span>  
  
3.  <span data-ttu-id="3c755-136">新しいレポートを作成するには、レポート ビルダーの左上隅の SQL Server アイコンをクリックし、[新規作成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c755-136">To create a new report, click the SQL Server icon in the upper left-hand corner of Report Builder, and then click New.</span></span>  
  
4.  <span data-ttu-id="3c755-137">ローカル コンピューターまたはレポート サーバーに保管された既存のレポートを開くには、左上隅の SQL Server アイコンをクリックし、[開く] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c755-137">To open an existing report stored on your local machine or a report server, click the SQL Server icon in the upper left-hand corner, and then click Open.</span></span>  
  
     <span data-ttu-id="3c755-138">既存のサーバーの一覧にレポートサーバーが表示されない場合は、[**レポートを開く**] ダイアログボックスを閉じ、レポートビルダーの下部にある [**接続**] をクリックしてサーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="3c755-138">If you don't see the report server in the list of existing servers, close the **Open Report** dialog box and then click **Connect** at the bottom of Report Builder to connect to the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c755-139">参照</span><span class="sxs-lookup"><span data-stu-id="3c755-139">See Also</span></span>  
 [<span data-ttu-id="3c755-140">SQL Server 2014 のレポート ビルダー</span><span class="sxs-lookup"><span data-stu-id="3c755-140">Report Builder in SQL Server 2014</span></span>](report-builder-in-sql-server-2016.md)  
  
  
