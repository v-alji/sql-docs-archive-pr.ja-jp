---
title: 1 つのレポートからのデータ フィードの生成 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e68baae2-9f2a-4f13-9179-9ac7f29111c5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 340191396aaaa92fe14fe8c3c6b42539a713eb45
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631618"
---
# <a name="generate-data-feeds-from-a-report-report-builder-and-ssrs"></a><span data-ttu-id="a52e2-102">1 つのレポートからのデータ フィードの生成 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="a52e2-102">Generate Data Feeds from a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="a52e2-103">レポートから Atom 準拠のデータフィードを生成し、データフィードを使用できるクライアントなどのアプリケーションでデータフィードを使用でき [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="a52e2-103">You can generate Atom-compliant data feeds from reports, and then use the data feeds in applications, such as the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] client, that can consume data feeds.</span></span>  
  
 <span data-ttu-id="a52e2-104">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Atom 表示拡張機能では、レポートで使用可能なデータ フィードを一覧表示する Atom サービス ドキュメントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="a52e2-104">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Atom rendering extension generates an Atom service document that lists the data feeds available from a report.</span></span> <span data-ttu-id="a52e2-105">このドキュメントには、レポート内の各データ領域について 1 つ以上のデータ フィードが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="a52e2-105">The document lists at least one data feed for each data region in the report.</span></span> <span data-ttu-id="a52e2-106">データ領域の種類およびデータ領域に表示されるデータによっては、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] は、1 つのデータ領域から複数のデータ フィードを生成することがあります。</span><span class="sxs-lookup"><span data-stu-id="a52e2-106">Depending on the type of data region and the data that the data region displays, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] might generate multiple data feeds from a data region.</span></span>  
  
 <span data-ttu-id="a52e2-107">Atom サービス ドキュメントには、データ フィードごとに一意の識別子が含まれています。データ フィードの内容を表示するには、URL でこの識別子を使用します。</span><span class="sxs-lookup"><span data-stu-id="a52e2-107">Atom service document contains a unique identifier for each the data feed and you use the identifier in a URL to view the content of the data feed.</span></span>  
  
 <span data-ttu-id="a52e2-108">詳細については、「 [複数のレポートからのデータ フィードの生成 &#40;レポート ビルダーおよび SSRS&#41;](generating-data-feeds-from-reports-report-builder-and-ssrs.md)で操作できます。</span><span class="sxs-lookup"><span data-stu-id="a52e2-108">For more information, see [Generating Data Feeds from Reports &#40;Report Builder and SSRS&#41;](generating-data-feeds-from-reports-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-generate-an-atom-service-document"></a><span data-ttu-id="a52e2-109">Atom サービス ドキュメントを生成するには</span><span class="sxs-lookup"><span data-stu-id="a52e2-109">To generate an Atom service document</span></span>  
  
1.  <span data-ttu-id="a52e2-110">レポート マネージャーの **[ホーム]** ページから、データ フィードを生成するレポートに移動します。</span><span class="sxs-lookup"><span data-stu-id="a52e2-110">From the Report Manager **Home** page, navigate to the report from which you want to generate data feeds.</span></span>  
  
2.  <span data-ttu-id="a52e2-111">レポートをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a52e2-111">Click the report.</span></span>  
  
     <span data-ttu-id="a52e2-112">レポートが実行されます。</span><span class="sxs-lookup"><span data-stu-id="a52e2-112">The report is run.</span></span>  
  
3.  <span data-ttu-id="a52e2-113">ツール バーで、[データ フィードへエクスポート] アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a52e2-113">On the toolbar, click the Export to Data Feed icon.</span></span>  
  
     <span data-ttu-id="a52e2-114">データ フィードを含む Atom ドキュメントを保存するか開くかを確認するメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a52e2-114">A message appears asking you if you want to save or open the atom document that contains the data feed.</span></span>  
  
4.  <span data-ttu-id="a52e2-115">**[保存]** をクリックしてドキュメントをファイル システムに保存するか、 **[開く]** をクリックして保存の前にドキュメントの内容を表示します。</span><span class="sxs-lookup"><span data-stu-id="a52e2-115">Click **Save** to save the document to the file system, or click **Open** to view the document content before saving.</span></span> <span data-ttu-id="a52e2-116">**既定では、ブラウザーにドキュメントが開きます。**</span><span class="sxs-lookup"><span data-stu-id="a52e2-116">**By default, the document opens in a browser.**</span></span>  
  
5.  <span data-ttu-id="a52e2-117">ドキュメントを保存する場所を参照します。</span><span class="sxs-lookup"><span data-stu-id="a52e2-117">Browse to the location to save the document.</span></span>  
  
6.  <span data-ttu-id="a52e2-118">必要に応じてドキュメントの名前を変更できます。</span><span class="sxs-lookup"><span data-stu-id="a52e2-118">Optionally, change the name of the document.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a52e2-119">既定では、ドキュメント名がレポート名になります。</span><span class="sxs-lookup"><span data-stu-id="a52e2-119">By default, the document name is the report name.</span></span>  
  
7.  <span data-ttu-id="a52e2-120">ドキュメントの種類が、 **ATOMSVC ファイル**であることを確認し、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a52e2-120">Verify the document type is **ATOMSVC File**, and then click **Save**.</span></span>  
  
8.  <span data-ttu-id="a52e2-121">必要に応じて、ブラウザーで、またはテキスト エディターか XML エディターで、.atomsvc ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="a52e2-121">Optionally, open the .atomsvc file in a browser or text or XML editor.</span></span>  
  
### <a name="to-view-an-atom-compliant-data-feed"></a><span data-ttu-id="a52e2-122">Atom 準拠のデータ フィードを表示するには</span><span class="sxs-lookup"><span data-stu-id="a52e2-122">To view an Atom-compliant data feed</span></span>  
  
1.  <span data-ttu-id="a52e2-123">Atom サービス ドキュメントがまだ開かれていない場合は、そのサービス ドキュメントを検索し、Internet Explorer などのブラウザーで開きます。</span><span class="sxs-lookup"><span data-stu-id="a52e2-123">If the Atom service document is not already open, locate it and open it in a browser such as Internet Explorer.</span></span>  
  
2.  <span data-ttu-id="a52e2-124">表示するデータ フィードの URL を Atom サービス ドキュメントからブラウザーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="a52e2-124">Copy the URL of the data feed that you want to view from the Atom service document to the browser.</span></span>  
  
     <span data-ttu-id="a52e2-125">URL の形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a52e2-125">The format of the URL is the following:</span></span>  
  
 `http://<server name>/ReportServer?%2f<ReportName>rs%3aCommand=Render&rs%3aFormat=ATOM&rc%3aDataFeed=<Identifier>`  
  
1.  <span data-ttu-id="a52e2-126">Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a52e2-126">Press ENTER.</span></span>  
  
     <span data-ttu-id="a52e2-127">データ フィードを含む Atom ドキュメントを保存するか開くかを確認するメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a52e2-127">A message appears asking you if you want to save or open the atom document that contains the data feed.</span></span>  
  
2.  <span data-ttu-id="a52e2-128">**[保存]** をクリックしてドキュメントをファイル システムに保存するか、 **[開く]** をクリックして保存の前にデータ フィードを表示します。</span><span class="sxs-lookup"><span data-stu-id="a52e2-128">Click **Save** to save the document to the file system, or click **Open** to view the data feed before saving.</span></span>  
  
3.  <span data-ttu-id="a52e2-129">ドキュメントを保存する場所を参照します。</span><span class="sxs-lookup"><span data-stu-id="a52e2-129">Browse to the location to save the document.</span></span>  
  
4.  <span data-ttu-id="a52e2-130">必要に応じてドキュメントの名前を変更できます。</span><span class="sxs-lookup"><span data-stu-id="a52e2-130">Optionally, change the name of the document.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a52e2-131">既定では、ドキュメント名がレポート名になります。</span><span class="sxs-lookup"><span data-stu-id="a52e2-131">By default the document name is the report name.</span></span> <span data-ttu-id="a52e2-132">Atom サービス ドキュメントに複数のフィードがある場合、既定ではすべて同じ名前 (レポート名) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a52e2-132">If the Atom service document has multiple feeds, by default all use the same name, the report name.</span></span> <span data-ttu-id="a52e2-133">それらを区別するには、名前を変更してわかりやすい名前を使用してください。</span><span class="sxs-lookup"><span data-stu-id="a52e2-133">To differentiate them, rename them to use meaningful names.</span></span>  
  
5.  <span data-ttu-id="a52e2-134">ドキュメントの種類が、 **ATOM ファイル**であることを確認し、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a52e2-134">Verify the document type is **ATOM File**, and then click **Save**.</span></span>  
  
6.  <span data-ttu-id="a52e2-135">必要に応じて、ブラウザーで、またはテキスト エディターか XML エディターで、.atom ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="a52e2-135">Optionally, open the .atom file in a browser or text editor or XML editor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a52e2-136">参照</span><span class="sxs-lookup"><span data-stu-id="a52e2-136">See Also</span></span>  
 [<span data-ttu-id="a52e2-137">レポートのエクスポート &#40;レポートビルダーと SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="a52e2-137">Exporting Reports &#40;Report Builder and SSRS&#41;</span></span>](export-reports-report-builder-and-ssrs.md)  
  
  
