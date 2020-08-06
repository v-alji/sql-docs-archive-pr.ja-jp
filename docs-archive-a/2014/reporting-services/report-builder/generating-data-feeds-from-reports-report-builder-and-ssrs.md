---
title: 複数のレポートからのデータ フィードの生成 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4e00789f-6967-42e5-b2b4-03181fdb1e2c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c7f999560bf3216ea84c672c733539d2cad44a15
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634302"
---
# <a name="generating-data-feeds-from-reports-report-builder-and-ssrs"></a><span data-ttu-id="e4f5e-102">複数のレポートからのデータ フィードの生成 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="e4f5e-102">Generating Data Feeds from Reports (Report Builder and SSRS)</span></span>
  <span data-ttu-id="e4f5e-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Atom 表示拡張機能は、レポートから利用できるデータ フィードおよびレポート内のデータ領域からのデータ フィードを一覧表示する Atom サービス ドキュメントを生成します。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-103">The [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Atom rendering extension generates an Atom service document that lists the data feeds available from a report and the data feeds from the data regions in a report.</span></span> <span data-ttu-id="e4f5e-104">この拡張機能を使用すると、レポートから生成されたデータ フィードを使用できるアプリケーションで読み取りおよび交換が可能な、Atom に準拠したデータ フィードを生成できます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-104">You use this extension to generate Atom-compliant data feeds that are readable and exchangeable with applications that can consume data feeds generated from reports.</span></span> <span data-ttu-id="e4f5e-105">たとえば、Atom 表示拡張機能を使用して、生成されたデータフィードをクライアントで使用でき [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-105">For example, you can use the Atom rendering extension to generated data feeds that you can then use in the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] client.</span></span>  
  
 <span data-ttu-id="e4f5e-106">Atom サービス ドキュメントには、レポート内の各データ領域について 1 つ以上のデータ フィードが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-106">The Atom service document lists at least one data feed for each data region in a report.</span></span> <span data-ttu-id="e4f5e-107">データ領域の種類およびデータ領域に表示されるデータによっては、 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] は、1 つのデータ領域から複数のデータ フィードを生成することがあります。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-107">Depending on the type of data region and the data that the data region displays, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] might generate multiple data feeds from a data region.</span></span> <span data-ttu-id="e4f5e-108">たとえば、マトリックスまたはグラフでは、複数のデータ フィードを提供できます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-108">For example, a matrix or chart can provide multiple data feeds.</span></span> <span data-ttu-id="e4f5e-109">Atom 表示拡張機能によって Atom サービス ドキュメントが作成されると、各データ フィードに対して一意な識別子が作成されます。URL 内でこの識別子を使用することで、データ フィードの内容にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-109">When the Atom rendering extension creates the Atom service document, a unique identifier is created for each data feed and you use the identifier in the URL to access the content of the data feed.</span></span>  
  
 <span data-ttu-id="e4f5e-110">Atom 表示拡張機能でデータ フィード用のデータを生成する方法は、コンマ区切り値 (CSV) 表示拡張機能でデータから CSV ファイルを提供する方法に似ています。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-110">The way that the Atom rendering extension generates data for a data feed is similar to how the Comma-Separated Value (CSV) rendering extension renders data to a CSV file.</span></span> <span data-ttu-id="e4f5e-111">CSV ファイルと同様に、データ フィードは、レポート データのフラット化された表現です。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-111">Like a CSV file, a data feed is a flattened representation of the report data.</span></span> <span data-ttu-id="e4f5e-112">たとえば、グループ内の売上を合計する行グループを含むテーブルでは、すべてのデータ行で合計が繰り返され、合計のみを含む独立した行がありません。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-112">For example, a table with a row group that sums the sales within a group repeats the sum in every data row and there is no separate row that contains only the sum.</span></span>  
  
 <span data-ttu-id="e4f5e-113">Atom サービス ドキュメントおよびデータ フィードは、レポート マネージャー、レポート サーバー、または [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]と統合された SharePoint サイトを使用して生成できます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-113">You can generate Atom service documents and data feeds using Report Manager, Report Server, or a SharePoint site that is integrated with [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="e4f5e-114">Atom は、一式の関連標準に適用されます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-114">Atom applies to a pair of related standards.</span></span> <span data-ttu-id="e4f5e-115">Atom サービス ドキュメントは RFC 5023 Atom パブリッシング プロトコル仕様に準拠し、データ フィードは RFC 4287 Atom 配信形式プロトコル仕様に準拠します。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-115">The Atom service document conforms to the RFC 5023 Atom publishing protocol specification and the data feeds conform to the RFC 4287 Atom syndication format protocol specification.</span></span>  
  
 <span data-ttu-id="e4f5e-116">以降のセクションでは、Atom 表示拡張機能の使用法に関する追加情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-116">The following sections provide additional information about how to use the Atom rendering extension:</span></span>  
  
 [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="reports-as-data-feeds"></a><a name="ReportDataAsDataFeeds"></a><span data-ttu-id="e4f5e-117">データフィードとしてのレポート</span><span class="sxs-lookup"><span data-stu-id="e4f5e-117">Reports as Data Feeds</span></span>  
 <span data-ttu-id="e4f5e-118">運用レポートをデータ フィードとしてエクスポートすることも、データ フィードの形式でアプリケーションにデータを提供することを第 1 の目的とするレポートを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-118">You can export a production report as a data feed or you can create a report whose primary purpose is provide data, in the form of data feeds, to applications.</span></span> <span data-ttu-id="e4f5e-119">データ フィードとしてのレポートは、クライアント データ プロバイダーを介してデータにアクセスするのが困難な場合や、データ ソースの複雑さを隠してデータをより簡単に使用できるようにする場合に、データをアプリケーションに提供するための方法の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-119">Using reports as a data feed gives you an additional way to provide data to applications when the data is not easy to access through client data providers, or when you prefer to hide the complexity of the data source and make it simpler to use the data.</span></span> <span data-ttu-id="e4f5e-120">レポート データをデータ フィードとして使用するもう 1 つのメリットは、レポート マネージャー、セキュリティ、スケジュール設定、レポート スナップショットなどの [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 機能を使用して、データ フィードを提供するレポートを管理できることです。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-120">Another benefit of using report data as a data feed is that you can use [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] features such as Report Manager, security, scheduling, and report snapshots to manage the reports that provide data feeds.</span></span>  
  
 <span data-ttu-id="e4f5e-121">Atom 表示拡張機能を有効に利用するためには、レポートがどのようにデータ フィードに表示されるかを理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-121">To get the most from the Atom rendering extension, you should understand how the report is rendered into data feeds.</span></span> <span data-ttu-id="e4f5e-122">既存のレポートを使用している場合は、レポートからどのようなデータ フィードが生成されるかを予測できることが必要です。データ フィードとして使用する専用のレポートを作成している場合は、データ フィードの有用性を最大限に高めるために、データを組み込んでレポート レイアウトを微調整できることが重要です。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-122">If you are using existing reports, being able to predict what the data feeds the reports will generate is useful; if you are writing report specifically for use as data feeds, being able to include the data and fine tune the report layout to maximize the usefulness of the data feeds is valuable.</span></span>  
  
 <span data-ttu-id="e4f5e-123">詳細については、「[1 つのレポートからのデータ フィードの生成 (レポート ビルダーおよび SSRS)](generate-data-feeds-from-a-report-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-123">For more information, see [Generate Data Feeds from a Report &#40;Report Builder and SSRS&#41;](generate-data-feeds-from-a-report-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="atom-service-document-atomsvc-file"></a><a name="AtomServiceDocument"></a><span data-ttu-id="e4f5e-124">Atom サービスドキュメント (.atomsvc ファイル)</span><span class="sxs-lookup"><span data-stu-id="e4f5e-124">Atom Service Document (.atomsvc file)</span></span>  
 <span data-ttu-id="e4f5e-125">Atom サービス ドキュメントは、1 つまたは複数のデータ フィードへの接続を指定します。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-125">An Atom service document specifies a connection to one or more data feeds.</span></span> <span data-ttu-id="e4f5e-126">接続は、少なくとも、フィードを生成するデータ サービスへの単純な URL です。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-126">At a minimum, the connection is a simple URL to the data service that produces the feed.</span></span>  
  
 <span data-ttu-id="e4f5e-127">Atom 表示拡張機能を使用してレポート データを表示すると、Atom サービス ドキュメントによってレポートで利用できるデータ フィードが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-127">When you render report data by using the Atom rendering extension, the Atom service document lists the data feeds available for a report.</span></span> <span data-ttu-id="e4f5e-128">このドキュメントには、レポート内の各データ領域について 1 つ以上のデータ フィードが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-128">The document lists at least one data feed for each data region in the report.</span></span> <span data-ttu-id="e4f5e-129">テーブルおよびゲージから生成されるデータ フィードはそれぞれ 1 つのみです。これに対し、マトリックス、リスト、およびグラフの場合、表示するデータによっては複数のデータ フィードが生成される場合があります。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-129">Tables and gauges generate only one data feed each, but matrices, lists, and charts might generated multiple depending on the data they display.</span></span>  
  
 <span data-ttu-id="e4f5e-130">次の図に、2 つのテーブルと 1 つのグラフを使用するレポートを示します。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-130">The following diagram shows a report that uses two tables and a chart.</span></span>  
  
 <span data-ttu-id="e4f5e-131">![RS_Atom_TableAndChartDataFeeds](../media/rs-atom-tableandchartdatafeeds.gif "RS_Atom_TableAndChartDataFeeds")</span><span class="sxs-lookup"><span data-stu-id="e4f5e-131">![RS_Atom_TableAndChartDataFeeds](../media/rs-atom-tableandchartdatafeeds.gif "RS_Atom_TableAndChartDataFeeds")</span></span>  
  
 <span data-ttu-id="e4f5e-132">このレポートから生成される Atom サービス ドキュメントには、各テーブルから 1 つずつ、グラフから 1 つの、合計 3 つのデータ フィードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-132">The Atom service document generated from this report includes three data feeds, one for each table and one for the chart.</span></span>  
  
 <span data-ttu-id="e4f5e-133">マトリックス データ領域には、マトリックスの構造に応じて複数のデータ フィードが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-133">The matrix data regions might have more than one data feed, depending on the structure of the matrix.</span></span> <span data-ttu-id="e4f5e-134">次の図に、2 つのデータ フィードを生成するマトリックスが使用されているレポートを示します。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-134">The following diagram shows a report that uses a matrix that generates two data feeds.</span></span>  
  
 <span data-ttu-id="e4f5e-135">![RS_Atom_PeerDynamicColumns](../media/rs-atom-peerdynamiccolumns.gif "RS_Atom_PeerDynamicColumns")</span><span class="sxs-lookup"><span data-stu-id="e4f5e-135">![RS_Atom_PeerDynamicColumns](../media/rs-atom-peerdynamiccolumns.gif "RS_Atom_PeerDynamicColumns")</span></span>  
  
 <span data-ttu-id="e4f5e-136">このレポートから生成される Atom サービス ドキュメントには、動的なピア列 Territory と Year に対応する 2 つのデータ フィードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-136">The Atom service document generated from this report includes two data feeds, one for each of the dynamic peer columns: Territory and Year.</span></span> <span data-ttu-id="e4f5e-137">次の図に、各データ フィードの内容を示します。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-137">The following diagram shows the content of each data feed.</span></span>  
  
 <span data-ttu-id="e4f5e-138">![RS_Atom_PeerDynamicDataFeeds](../media/rs-atom-peerdynamicdatafeeds.gif "RS_Atom_PeerDynamicDataFeeds")</span><span class="sxs-lookup"><span data-stu-id="e4f5e-138">![RS_Atom_PeerDynamicDataFeeds](../media/rs-atom-peerdynamicdatafeeds.gif "RS_Atom_PeerDynamicDataFeeds")</span></span>  
  

  
##  <a name="data-feeds"></a><a name="DataFeeds"></a> <span data-ttu-id="e4f5e-139">データ フィード</span><span class="sxs-lookup"><span data-stu-id="e4f5e-139">Data Feeds</span></span>  
 <span data-ttu-id="e4f5e-140">データ フィードは、時間が経過しても変化しない一貫した表形式と、レポートを実行するたびに変化する可能性のある可変データから成る、XML ファイルです。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-140">The data feed is an XML file that has a consistent tabular format that does not change over time and variable data that can be different each time the report is run.</span></span> <span data-ttu-id="e4f5e-141">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] によって生成されるデータ フィードは、ADO.NET Data Services によって生成されるデータ フィードと同じ形式です。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-141">The data feeds generated by [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] are in the same format as those generated by  that ADO.NET Data Services.</span></span>  
  
 <span data-ttu-id="e4f5e-142">データ フィードには、ヘッダー セクションとデータ セクションの 2 つのセクションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-142">A data feed contains two sections: header and data.</span></span> <span data-ttu-id="e4f5e-143">Atom 仕様には、各セクションの要素が定義されています。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-143">The Atom specification defines the elements in each section.</span></span> <span data-ttu-id="e4f5e-144">ヘッダーには、データ フィードで使用する文字エンコード スキーマなどの情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-144">The header includes information such as the character encoding schema to use with the data feeds.</span></span>  
  
### <a name="header-section"></a><span data-ttu-id="e4f5e-145">ヘッダー セクション</span><span class="sxs-lookup"><span data-stu-id="e4f5e-145">Header Section</span></span>  
 <span data-ttu-id="e4f5e-146">次の XML コードは、データ フィードのヘッダー セクションを示しています。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-146">The following XML code shows the header section of a data feed.</span></span>  
  
 `<?xml version="1.0" encoding="utf-8" standalone="yes"?><feed xmlns:d="https://schemas.microsoft.com/ado/2007/08/dataservices" xmlns:m="https://schemas.microsoft.com/ado/2007/08/dataservices/metadata" xmlns="http://www.w3.org/2005/Atom">`  
  
 `<title type="text"></title>`  
  
 `<id>uuid:1795992c-a6f3-40ec-9243-fbfd0b1a5be3;id=166321</id>`  
  
 `<updated>2009-05-08T23:09:58Z</updated>`  
  
### <a name="data-section"></a><span data-ttu-id="e4f5e-147">データ セクション</span><span class="sxs-lookup"><span data-stu-id="e4f5e-147">Data Section</span></span>  
 <span data-ttu-id="e4f5e-148">データフィードのデータセクションには、 `entry` Atom 表示拡張機能によって生成されるフラット化された行セットの行ごとに1つの <> 要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-148">The data section of the data feeds contains one <`entry`> element for each row in the flattened rowset generated by the Atom rendering extension.</span></span>  
  
 <span data-ttu-id="e4f5e-149">次の図に、グループと合計を使用するレポートを示します。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-149">The following diagram shows a report that uses groups and totals.</span></span>  
  
 <span data-ttu-id="e4f5e-150">![RS_Atom_ProductSalesSummaryCircledValues](../media/rs-atom-productsalessummarycircledvalues.gif "RS_Atom_ProductSalesSummaryCircledValues")</span><span class="sxs-lookup"><span data-stu-id="e4f5e-150">![RS_Atom_ProductSalesSummaryCircledValues](../media/rs-atom-productsalessummarycircledvalues.gif "RS_Atom_ProductSalesSummaryCircledValues")</span></span>  
  
 <span data-ttu-id="e4f5e-151">次の XML は、 `entry` データフィード内のレポートの <> 要素を示しています。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-151">The following XML shows an <`entry`> element from that report in a data feed.</span></span> <span data-ttu-id="e4f5e-152"><の> 要素には、 `entry` グループの売上および注文の合計と、すべてのグループの売上および注文の合計が含まれていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-152">Notice that the <`entry`> element includes the totals of the sales and orders for the group and the totals of sales and orders for all the groups.</span></span> <span data-ttu-id="e4f5e-153"><> 要素には、 `entry` レポート上のすべての値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-153">The <`entry`> element includes all values on the report.</span></span>  
  
 `<entry><id>uuid:1795992c-a6f3-40ec-9243-fbfd0b1a5be3;id=166322</id><title type="text"></title><updated>2009-05-08T23:09:58Z</updated><author /><content type="application/xml"><m:properties>`  
  
 `<d:ProductCategory_Value>Accessories</d:ProductCategory_Value>`  
  
 `<d:OrderYear_Value m:type="Edm.Int32">2001</d:OrderYear_Value>`  
  
 `<d:SumLineTotal_Value m:type="Edm.Decimal">20235.364608</d:SumLineTotal_Value>`  
  
 `<d:SumOrderQty_Value m:type="Edm.Int32">1003</d:SumOrderQty_Value>`  
  
 `<d:SumLineTotal_Total_2_1 m:type="Edm.Decimal">1272072.883926</d:SumLineTotal_Total_2_1>`  
  
 `<d:SumOrderQty_Total_2_1 m:type="Edm.Double">61932</d:SumOrderQty_Total_2_1>`  
  
 `<d:SumLineTotal_Total_2_2 m:type="Edm.Decimal">109846381.399888</d:SumLineTotal_Total_2_2>`  
  
 `<d:SumOrderQty_Total_2_2 m:type="Edm.Double">274914</d:SumOrderQty_Total_2_2></m:properties></content>`  
  
 `</entry>`  
  
### <a name="working-with-data-feeds"></a><span data-ttu-id="e4f5e-154">データ フィードの操作</span><span class="sxs-lookup"><span data-stu-id="e4f5e-154">Working with Data Feeds</span></span>  
 <span data-ttu-id="e4f5e-155">レポートによって生成されるすべてのデータ フィードには、データ フィードを生成するデータ領域の親のスコープ内のレポート アイテムが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-155">All data feeds generated by the report include the report items that are in scope of the parent of the data region that generate the data feeds.</span></span> <span data-ttu-id="e4f5e-156">.</span><span class="sxs-lookup"><span data-stu-id="e4f5e-156">.</span></span> <span data-ttu-id="e4f5e-157">複数のテーブルと 1 つのグラフが含まれているレポートを想像してください。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-157">Imagine a report that has several tables and a chart.</span></span> <span data-ttu-id="e4f5e-158">レポート本文のテキスト ボックスは、各データ領域の説明テキストを提供します。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-158">Text boxes in the report body provides descriptive text of each data region.</span></span> <span data-ttu-id="e4f5e-159">レポートによって生成されるすべてのデータ フィードのすべてのエントリには、テキスト ボックスの値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-159">Every entry in every data feed that the report generates includes the value of the text box.</span></span> <span data-ttu-id="e4f5e-160">たとえば、テキストが "販売地域別の月次売上の平均を示すグラフ" の場合、3 つのすべてのデータ フィードの各行にこのテキストが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-160">For example, if the text is "Chart displays monthly sales averages by sales region", all three data feeds would include this text on each row.</span></span>  
  
 <span data-ttu-id="e4f5e-161">入れ子になったデータ領域のような階層データ リレーションシップがレポート レイアウトに含まれている場合、これらのリレーションシップは、レポート データのフラット化された行セットに含まれます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-161">If the report layout includes hierarchical data relationships, such as nested data regions, those relationships are included in the flattened rowset of report data.</span></span>  
  
 <span data-ttu-id="e4f5e-162">一般に、入れ子になったデータ領域のデータ行は幅が広くなります。入れ子になったテーブルおよびマトリックスにグループや合計が含まれる場合は特にそうです。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-162">The data rows for nested data regions are typically wide, especially if the nested tables and matrices include groups and totals.</span></span> <span data-ttu-id="e4f5e-163">期待どおりのデータが生成されるかどうかを確認するには、レポートをデータ フィードにエクスポートした後でデータ フィードを表示すると便利です。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-163">You might find it useful to export the report to a data feed and view the data feed to verify that the data generated is what you expected.</span></span>  
  
 <span data-ttu-id="e4f5e-164">Atom 表示拡張機能によって Atom サービス ドキュメントが作成されると、データ フィードに対して一意な識別子が作成されます。URL 内でこの識別子を使用することで、データ フィードの内容を確認できます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-164">When the Atom rendering extension creates the Atom service document, a unique identifier is created for the data feed and you use the identifier in the URL to view the content of the data feed.</span></span> <span data-ttu-id="e4f5e-165">上に示したサンプルの Atom サービスドキュメントには、"" という URL が含まれてい <http://ServerName/ReportServer?%2fProduct+Sales+Summary&rs%3aCommand=Render&rs%3aFormat=ATOM&rc%3aDataFeed=xAx0x1> ます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-165">The sample Atom service document, shown above, includes the URL <http://ServerName/ReportServer?%2fProduct+Sales+Summary&rs%3aCommand=Render&rs%3aFormat=ATOM&rc%3aDataFeed=xAx0x1>".</span></span> <span data-ttu-id="e4f5e-166">この URL は、レポート (Product Sales Summary)、Atom 表示形式 (ATOM)、およびデータ フィードの名前 (xAx0x1) を識別します。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-166">The URL identifies the report (Product Sales Summary), the Atom rendering format (ATOM), and the name of the data feed (xAx0x1).</span></span>  
  
 <span data-ttu-id="e4f5e-167">レポート アイテムの名前には、直感的でなく覚えにくい、レポート アイテムのレポート定義言語 (RDL) 要素の名前が既定で使用されます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-167">Report item names default to the report definition language (RDL) element names of the report items and often they are not intuitive or easy to remember.</span></span> <span data-ttu-id="e4f5e-168">たとえば、レポートに配置された最初のマトリックスの既定の名前は Tablix 1 となります。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-168">For example, the default name of the first matrix placed in a report is Tablix 1.</span></span> <span data-ttu-id="e4f5e-169">データ フィードでは、これらの名前が使用されます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-169">The data feeds use these names.</span></span>  
  
 <span data-ttu-id="e4f5e-170">データ領域の DataElementName プロパティを使用してわかりやすい名前を付けることで、データ フィードの操作を容易にすることができます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-170">To make the data feed easier to work with, you can use the DataElementName property of the data region to provide friendly names.</span></span> <span data-ttu-id="e4f5e-171">DataElementName の値を指定した場合、データフィードのサブ要素 <`d`> では既定のデータ領域名の代わりにが使用されます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-171">If you provide a value for DataElementName the data feed subelement <`d`> will use is it instead of the default data region name.</span></span> <span data-ttu-id="e4f5e-172">たとえば、データ領域の既定の名前が Tablix1 で、DataElementName が SalesByTerritoryYear に設定されている場合、 `d` データフィード内の <> は SalesByTerritoryYear を使用します。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-172">For example, if the default name of a data regions is Tablix1 and DataElementName set SalesByTerritoryYear then the <`d`> in the data feed uses SalesByTerritoryYear.</span></span> <span data-ttu-id="e4f5e-173">上で説明したマトリックス レポートのようにデータ領域に 2 つのデータ フィードがある場合、データ フィードで使用される名前は、SalesByTerritoryYear _Territory と SalesByTerritoryYear _Year となります。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-173">If the data regions has two data feeds like the matrix report described above, the names used in the data feeds are SalesByTerritoryYear _Territory and SalesByTerritoryYear _Year.</span></span>  
  
 <span data-ttu-id="e4f5e-174">レポート上に表示されたデータとデータ フィード内のデータを比較した場合、いくつかの相違があります。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-174">If you compare the data shown on the report and the data in the data feed, you might notice some differences.</span></span> <span data-ttu-id="e4f5e-175">通常、レポートに表示される数値データや日時データは書式設定されていますが、データ フィードには書式設定されていないデータが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-175">Reports often shows formatted numeric and time/date data whereas the data feed contains unformatted data.</span></span>  
  
 <span data-ttu-id="e4f5e-176">データ フィードは、拡張子が .atom のファイル名で保存されます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-176">A data feed is saved with the .atom file name extension.</span></span> <span data-ttu-id="e4f5e-177">テキスト エディターまたは XML エディター (たとえば、メモ帳や XML Editor) を使用して、ファイルの構造および内容を確認できます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-177">You can use a text or XML editor such as Notepad or XML Editor to view the file structure and content.</span></span>  
  

  
##  <a name="flattening-report-data"></a><a name="FlatteningReportData"></a><span data-ttu-id="e4f5e-178">レポートデータのフラット化</span><span class="sxs-lookup"><span data-stu-id="e4f5e-178">Flattening Report Data</span></span>  
 <span data-ttu-id="e4f5e-179">Atom レンダラーは、XML 形式のフラット化された行セットとしてレポート データを提供します。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-179">The Atom renderer provides report data as flattened rowsets in an XML format.</span></span> <span data-ttu-id="e4f5e-180">データ テーブルをフラット化する場合のルールは、いくつかの例外を除き、CSV レンダラーに適用されるルールと同じです。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-180">The rules for flattening data tables are the same to those of the CSV renderer with a few exceptions:</span></span>  
  
-   <span data-ttu-id="e4f5e-181">スコープ内のアイテムは、詳細レベルにフラット化されます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-181">Items in scope are flattened to the detail level.</span></span> <span data-ttu-id="e4f5e-182">CSV レンダラーとは異なり、最上位レベルにあるテキスト ボックスは、データ フィードに書き込まれるすべてのエントリに含められます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-182">Unlike the CSV renderer, the text boxes at the top level appear in each entry written to the data feed.</span></span>  
  
-   <span data-ttu-id="e4f5e-183">レポート パラメーター値は、出力の行ごとに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-183">Report parameter values are rendered on each row of the output.</span></span>  
  
 <span data-ttu-id="e4f5e-184">階層データとグループ化データは、Atom に準拠した形式で表示するためにフラット化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-184">Hierarchical and grouped data must be flattened in order to be represented in the Atom-compliant format.</span></span> <span data-ttu-id="e4f5e-185">表示拡張機能では、レポートをフラット化して、データ領域内で入れ子になっているグループを表すツリー構造にします。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-185">The rendering extension flattens the report into a tree structure that represents the nested groups within the data region.</span></span> <span data-ttu-id="e4f5e-186">レポートをフラット化する手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-186">To flatten the report:</span></span>  
  
-   <span data-ttu-id="e4f5e-187">行階層がフラット化されてから列階層がフラット化されます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-187">A row hierarchy is flattened before a column hierarchy.</span></span>  
  
-   <span data-ttu-id="e4f5e-188">行階層のメンバーがデータ フィードに表示された後、列階層のメンバーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-188">Members of the row hierarchy are rendered to the data feed before members of the column hierarchy.</span></span>  
  
-   <span data-ttu-id="e4f5e-189">列が並べ替えられます。本文中のテキスト ボックスが左から右、上から下に並べ替えられた後、データ領域が左から右、上から下に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-189">Columns are ordered as follows: text boxes in body order left-to-right, top-to-bottom followed by data regions ordered left-to-right, top-to-bottom.</span></span>  
  
-   <span data-ttu-id="e4f5e-190">データ領域内の列が、コーナーのメンバー、行階層メンバー、列階層メンバー、セルの順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-190">Within a data region, the columns are ordered as follows: corner members, row hierarchy members, column hierarchy members, and then cells.</span></span>  
  
-   <span data-ttu-id="e4f5e-191">ピア データ領域は、一般的なデータ領域または動的な先祖を共有する、データ領域または動的グループです。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-191">Peer data regions are data regions or dynamic groups that share a common data region or dynamic ancestor.</span></span> <span data-ttu-id="e4f5e-192">ピア データがフラットなツリーの分岐で識別されます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-192">Peer data is identified by branching of the flattened tree.</span></span>  
  
 <span data-ttu-id="e4f5e-193">詳細については、「 [テーブル、マトリックス、および一覧 (レポート ビルダーおよび SSRS)](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-193">For more information, see [Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="atom-rendering-rules"></a><a name="AtomRendering"></a><span data-ttu-id="e4f5e-194">Atom 表示規則</span><span class="sxs-lookup"><span data-stu-id="e4f5e-194">Atom Rendering Rules</span></span>  
 <span data-ttu-id="e4f5e-195">Atom 表示拡張機能は、データ フィードを表示するときに次の情報を無視します。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-195">The Atom rendering extension ignores the following information when rendering a data feed:</span></span>  
  
-   <span data-ttu-id="e4f5e-196">書式設定およびレイアウト</span><span class="sxs-lookup"><span data-stu-id="e4f5e-196">Formatting and layout</span></span>  
  
-   <span data-ttu-id="e4f5e-197">ページ ヘッダー</span><span class="sxs-lookup"><span data-stu-id="e4f5e-197">Page header</span></span>  
  
-   <span data-ttu-id="e4f5e-198">ページ フッター</span><span class="sxs-lookup"><span data-stu-id="e4f5e-198">Page footer</span></span>  
  
-   <span data-ttu-id="e4f5e-199">カスタム レポート アイテム</span><span class="sxs-lookup"><span data-stu-id="e4f5e-199">Custom report items</span></span>  
  
-   <span data-ttu-id="e4f5e-200">矩形</span><span class="sxs-lookup"><span data-stu-id="e4f5e-200">Rectangles</span></span>  
  
-   <span data-ttu-id="e4f5e-201">路線</span><span class="sxs-lookup"><span data-stu-id="e4f5e-201">Lines</span></span>  
  
-   <span data-ttu-id="e4f5e-202">イメージ</span><span class="sxs-lookup"><span data-stu-id="e4f5e-202">Images</span></span>  
  
-   <span data-ttu-id="e4f5e-203">自動集計</span><span class="sxs-lookup"><span data-stu-id="e4f5e-203">Automatic subtotals</span></span>  
  
 <span data-ttu-id="e4f5e-204">その他のレポート アイテムは、まず先頭から末尾に、そして左から右に向かって並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-204">The remaining report items are sorted, from top to bottom, and then left to right.</span></span> <span data-ttu-id="e4f5e-205">その後、各アイテムが列に生成されます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-205">Each item is then rendered to a column.</span></span> <span data-ttu-id="e4f5e-206">レポートに一覧やテーブルなどの入れ子になったデータ アイテムがある場合は、親アイテムが各行に繰り返し使用されます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-206">If the report has nested data items like lists or tables, the parent items are repeated on each row.</span></span>  
  
 <span data-ttu-id="e4f5e-207">次の表では、表示した際のレポート アイテムの外観について説明します。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-207">The following table indicates the appearance of report items when rendered:</span></span>  
  
|<span data-ttu-id="e4f5e-208">Item</span><span class="sxs-lookup"><span data-stu-id="e4f5e-208">Item</span></span>|<span data-ttu-id="e4f5e-209">表示動作</span><span class="sxs-lookup"><span data-stu-id="e4f5e-209">Rendering behavior</span></span>|  
|----------|------------------------|  
|<span data-ttu-id="e4f5e-210">テーブル</span><span class="sxs-lookup"><span data-stu-id="e4f5e-210">Table</span></span>|<span data-ttu-id="e4f5e-211">テーブルを展開して表示します。最も詳細なレベルでの各行と列に対応した、行と列が作成されます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-211">Renders by expanding the table and creating a row and column for each row and column at the lowest level of detail.</span></span> <span data-ttu-id="e4f5e-212">集計の行と列には、列見出しまたは行見出しは付けられません。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-212">Subtotal rows and columns do not have column or row headings.</span></span> <span data-ttu-id="e4f5e-213">詳細レポートはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-213">Drillthrough reports are not supported.</span></span>|  
|<span data-ttu-id="e4f5e-214">Matrix</span><span class="sxs-lookup"><span data-stu-id="e4f5e-214">Matrix</span></span>|<span data-ttu-id="e4f5e-215">マトリックスを展開して表示します。最も詳細なレベルでの各行と列に対応した、行と列が作成されます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-215">Renders by expanding the matrix and creating a row and column for each row and column at the lowest level of detail.</span></span> <span data-ttu-id="e4f5e-216">集計の行と列には、列見出しまたは行見出しは付けられません。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-216">Subtotal rows and columns do not have column or row headings.</span></span>|  
|<span data-ttu-id="e4f5e-217">List</span><span class="sxs-lookup"><span data-stu-id="e4f5e-217">List</span></span>|<span data-ttu-id="e4f5e-218">一覧の詳細行またはインスタンスそれぞれに対応するレコードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-218">Renders a record for each detail row or instance in the list.</span></span>|  
|<span data-ttu-id="e4f5e-219">サブレポート</span><span class="sxs-lookup"><span data-stu-id="e4f5e-219">Subreport</span></span>|<span data-ttu-id="e4f5e-220">親アイテムは、コンテンツのインスタンスごとに繰り返し表示されます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-220">The parent item is repeated for each instance of the contents.</span></span>|  
|<span data-ttu-id="e4f5e-221">グラフ</span><span class="sxs-lookup"><span data-stu-id="e4f5e-221">Chart</span></span>|<span data-ttu-id="e4f5e-222">それぞれのグラフ値にすべてのグラフ ラベルを付けてレコードを表示します。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-222">Renders a record with all chart labels for each chart value.</span></span> <span data-ttu-id="e4f5e-223">階層内の系列およびカテゴリのラベルは、フラット化され、グラフ値の行内に含まれています。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-223">Labels from series and categories in hierarchies are flattened and included in the row for a chart value.</span></span>|  
|<span data-ttu-id="e4f5e-224">データ バー</span><span class="sxs-lookup"><span data-stu-id="e4f5e-224">Data bar</span></span>|<span data-ttu-id="e4f5e-225">グラフのように表示されます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-225">Renders like a chart.</span></span> <span data-ttu-id="e4f5e-226">通常、データ バーには階層またはラベルは含まれません。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-226">Typically, a data bar does not include hierarchies or labels.</span></span>|  
|<span data-ttu-id="e4f5e-227">スパークライン</span><span class="sxs-lookup"><span data-stu-id="e4f5e-227">Sparkline</span></span>|<span data-ttu-id="e4f5e-228">グラフのように表示されます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-228">Renders like a chart.</span></span> <span data-ttu-id="e4f5e-229">通常、スパークラインには階層またはラベルは含まれません。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-229">Typically, a sparkline does not include hierarchies or labels.</span></span>|  
|<span data-ttu-id="e4f5e-230">ゲージ</span><span class="sxs-lookup"><span data-stu-id="e4f5e-230">Gauge</span></span>|<span data-ttu-id="e4f5e-231">線形スケールの最小値/最大値、範囲の開始値/終了値、およびポインターの値を含む単一のレコードとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-231">Renders as a single record with the minimum and maximum values of the linear scale, start and end values of the range, and the value of the pointer.</span></span>|  
|<span data-ttu-id="e4f5e-232">インジケーター</span><span class="sxs-lookup"><span data-stu-id="e4f5e-232">Indicator</span></span>|<span data-ttu-id="e4f5e-233">アクティブな状態名、使用可能な状態、およびデータ値を持つ単一のレコードとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-233">Renders as a single record with the active state name, available states, and the data value.</span></span>|  
|<span data-ttu-id="e4f5e-234">マップ</span><span class="sxs-lookup"><span data-stu-id="e4f5e-234">Map</span></span>|<span data-ttu-id="e4f5e-235">各マップ データ領域にデータ フィードを生成します。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-235">Generates a data feed for each map data region.</span></span> <span data-ttu-id="e4f5e-236">複数のマップ レイヤーが同じデータ領域を使用している場合、データ フィードにはすべてのマップ レイヤーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-236">If multiple map layers use the same data region, the data feed includes all of them.</span></span> <span data-ttu-id="e4f5e-237">データ フィードには、マップ レイヤーのマップ メンバーごとにラベルと値を持つレコードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-237">The data feed includes a record with the labels and values for each map member of the map layer.</span></span>|  
  

  
##  <a name="device-information-settings"></a><a name="DeviceInfo"></a><span data-ttu-id="e4f5e-238">デバイス情報の設定</span><span class="sxs-lookup"><span data-stu-id="e4f5e-238">Device Information Settings</span></span>  
 <span data-ttu-id="e4f5e-239">使用するエンコード スキーマなど、このレンダラーのいくつかの既定の設定は変更することができます。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-239">You can change some default settings for this renderer, including the encoding schema to use.</span></span> <span data-ttu-id="e4f5e-240">詳細については、「 [ATOM Device Information Settings](../atom-device-information-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e4f5e-240">For more information, see [ATOM Device Information Settings](../atom-device-information-settings.md).</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="e4f5e-241">参照</span><span class="sxs-lookup"><span data-stu-id="e4f5e-241">See Also</span></span>  
 <span data-ttu-id="e4f5e-242">[CSV ファイルへのエクスポート &#40;レポートビルダーと SSRS&#41;](exporting-to-a-csv-file-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e4f5e-242">[Exporting to a CSV File &#40;Report Builder and SSRS&#41;](exporting-to-a-csv-file-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="e4f5e-243">レポートのエクスポート &#40;レポートビルダーと SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e4f5e-243">Exporting Reports &#40;Report Builder and SSRS&#41;</span></span>](export-reports-report-builder-and-ssrs.md)  
  
  
