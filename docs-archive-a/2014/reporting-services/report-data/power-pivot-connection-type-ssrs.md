---
title: PowerPivot の接続の種類 (SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a104c3c7-f118-4d02-9a0f-6859f1469d11
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 08ce995afa7d458e8ce3ae50a9f572a086a3c697
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742861"
---
# <a name="powerpivot-connection-type-ssrs"></a><span data-ttu-id="5bf66-102">PowerPivot の接続の種類 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="5bf66-102">PowerPivot Connection Type (SSRS)</span></span>
  <span data-ttu-id="5bf66-103">SQL Server Analysis Services データ処理拡張機能を使用すると、SharePoint の PowerPivot ギャラリーにパブリッシュされた PowerPivot ブックからデータを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="5bf66-103">You can use SQL Server Analysis Services data processing extension to retrieve data from a PowerPivot workbook that is published in a SharePoint PowerPivot Gallery.</span></span>  
  
 <span data-ttu-id="5bf66-104">このトピックの情報を使用して、データ ソースを構築してください。</span><span class="sxs-lookup"><span data-stu-id="5bf66-104">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="5bf66-105">詳細な手順については、「[データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;の追加と検証](add-and-verify-a-data-connection-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5bf66-105">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5bf66-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="5bf66-106">Prerequisites</span></span>  
 <span data-ttu-id="5bf66-107">PowerPivot データ ソースは、SharePoint サイトの PowerPivot ギャラリーにパブリッシュされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="5bf66-107">The PowerPivot data source must be published in a PowerPivot Gallery on a SharePoint site.</span></span>  
  
 <span data-ttu-id="5bf66-108">レポート ビルダーから PowerPivot ブックへの接続をサポートするには、ワークステーション コンピューターに SQL Server 2008 R2 ADOMD.NET が必要です。</span><span class="sxs-lookup"><span data-stu-id="5bf66-108">To support connections from Report Builder to a PowerPivot workbook, you must have SQL Server 2008 R2 ADOMD.NET on your workstation computer.</span></span> <span data-ttu-id="5bf66-109">このクライアントライブラリは PowerPivot for Excel と共にインストールされますが、このアプリケーションがインストールされていないコンピューターを使用している場合は、 [SQL Server 2008 R2 Feature Pack](https://www.microsoft.com/download/details.aspx?id=44272)から ADOMD.NET をダウンロードしてインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5bf66-109">This client library is installed with PowerPivot for Excel, but if you are using a computer that does not have this application, you must download and install ADOMD.NET from the [SQL Server 2008 R2 Feature Pack](https://www.microsoft.com/download/details.aspx?id=44272).</span></span>  
  
## <a name="data-source-type"></a><span data-ttu-id="5bf66-110">データ ソースの種類</span><span class="sxs-lookup"><span data-stu-id="5bf66-110">Data Source Type</span></span>  
 <span data-ttu-id="5bf66-111">使用するレポート データ ソースの種類は **Microsoft SQL Server Analysis Services**です。</span><span class="sxs-lookup"><span data-stu-id="5bf66-111">Use report data source type **Microsoft SQL Server Analysis Services**.</span></span>  
  
## <a name="connection-string"></a><span data-ttu-id="5bf66-112">接続文字列</span><span class="sxs-lookup"><span data-stu-id="5bf66-112">Connection String</span></span>  
 <span data-ttu-id="5bf66-113">接続文字列は、PowerPivot ギャラリーまたはその他のライブラリ (など) の SharePoint でパブリッシュされた PowerPivot ブックの URL です http://contoso-srv/subsite/PowerPivotLibrary/ContosoSales.xlsx 。</span><span class="sxs-lookup"><span data-stu-id="5bf66-113">The connection string is the URL to PowerPivot workbook published on SharePoint in the PowerPivot Gallery or other library, for example, http://contoso-srv/subsite/PowerPivotLibrary/ContosoSales.xlsx.</span></span>  
  
## <a name="credentials"></a><span data-ttu-id="5bf66-114">[資格情報]</span><span class="sxs-lookup"><span data-stu-id="5bf66-114">Credentials</span></span>  
 <span data-ttu-id="5bf66-115">PowerPivot ブックおよび SharePoint サイトへのアクセスに必要な資格情報を指定します (Windows 認証 (統合セキュリティ) など)。</span><span class="sxs-lookup"><span data-stu-id="5bf66-115">Specify the credentials that you need to access the PowerPivot workbook and SharePoint site, for example, Windows Authentication (Integrated Security).</span></span> <span data-ttu-id="5bf66-116">詳細については、「 [Reporting Services のデータ接続、データソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)」または「[レポートビルダーで資格情報を指定する](../specify-credentials-in-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5bf66-116">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
## <a name="queries"></a><span data-ttu-id="5bf66-117">クエリ</span><span class="sxs-lookup"><span data-stu-id="5bf66-117">Queries</span></span>  
 <span data-ttu-id="5bf66-118">PowerPivot データ ソースに接続した後、MDX グラフィカル クエリを使用して、基となるデータ構造を参照および選択してクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="5bf66-118">After you connect to the PowerPivot data source, use the MDX graphical query to build a query by browsing and selecting from the underlying data structures.</span></span> <span data-ttu-id="5bf66-119">クエリを作成したら、それを実行して結果ペインにサンプル データを表示します。</span><span class="sxs-lookup"><span data-stu-id="5bf66-119">After you build a query, run the query to see sample data in the results pane.</span></span>  
  
 <span data-ttu-id="5bf66-120">クエリ デザイナーにより、クエリを分析してデータセット フィールドが決定されます。</span><span class="sxs-lookup"><span data-stu-id="5bf66-120">The query designer analyzes the query to determine the dataset fields.</span></span> <span data-ttu-id="5bf66-121">また、 **レポート データ** ペインでデータセット フィールド コレクションを手動で編集することもできます。</span><span class="sxs-lookup"><span data-stu-id="5bf66-121">You can also manually edit the dataset field collection in the **Report Data** pane.</span></span> <span data-ttu-id="5bf66-122">詳細については、「[レポート データ ペインでのフィールドの追加、編集、更新 &#40;レポート ビルダーおよび SSRS&#41;](add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5bf66-122">For more information, see [Add, Edit, Refresh Fields in the Report Data Pane &#40;Report Builder and SSRS&#41;](add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs.md).</span></span>  
  
## <a name="filters"></a><span data-ttu-id="5bf66-123">フィルター</span><span class="sxs-lookup"><span data-stu-id="5bf66-123">Filters</span></span>  
 <span data-ttu-id="5bf66-124">フィルター ペインで、クエリ結果から除外するか、クエリ結果に追加するディメンションおよびメンバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="5bf66-124">In the Filters pane, specify dimensions and members to filter out or to include in the query results.</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="5bf66-125">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5bf66-125">Parameters</span></span>  
 <span data-ttu-id="5bf66-126">フィルター ペインで、フィルターの **[パラメーター]** オプションを選択して、フィルターの選択に対応する使用可能な値を持つレポート パラメーターが自動的に作成されるようにします。</span><span class="sxs-lookup"><span data-stu-id="5bf66-126">In the Filters pane, select the **Parameters** option for a filter to automatically create a report parameter with available values that correspond to the filter selections.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5bf66-127">解説</span><span class="sxs-lookup"><span data-stu-id="5bf66-127">Remarks</span></span>  
 <span data-ttu-id="5bf66-128">PowerPivot ギャラリーの PowerPivot ブックからレポート ビルダーを開いた場合、PowerPivot ブックのピボットテーブル、ピボットグラフ、スライサー、およびその他のレイアウト機能や分析機能は、レポートで再作成されません。</span><span class="sxs-lookup"><span data-stu-id="5bf66-128">If you open Report Builder from the PowerPivot workbook in a PowerPivot Gallery, the PivotTables, PivotCharts, slicers, and other layout and analytical features from the PowerPivot workbook are not re-created in the report.</span></span> <span data-ttu-id="5bf66-129">代わりに、PowerPivot ブック内のデータを参照する、あらかじめ構成されたデータ ソースが空のレポートに含まれます。</span><span class="sxs-lookup"><span data-stu-id="5bf66-129">Instead, the blank report includes a preconfigured data source that points to the data in the PowerPivot workbook.</span></span> <span data-ttu-id="5bf66-130">PowerPivot ブックに基づくレポートをデザインする場合、レポートで再作成するスライサー、フィルター、およびテーブルやグラフの数によっては、手間と時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="5bf66-130">Designing reports based on a PowerPivot workbook can be labor-intensive and time-consuming depending on the number of slicers, filters, and tables or charts that you want to re-create in the report.</span></span> <span data-ttu-id="5bf66-131">そのため、レポートでのデータの表示方法については、PowerPivot のデザインとは切り離して考えることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5bf66-131">A better approach is to envision the presentation of the data that you want in a report independently from the PowerPivot design.</span></span>  
  
 <span data-ttu-id="5bf66-132">PowerPivot ブック内のデータは大幅に圧縮されていますが、PowerPivot ブックから取得されたレポートのデータは圧縮されません。</span><span class="sxs-lookup"><span data-stu-id="5bf66-132">The data in a PowerPivot workbook is highly compressed; data retrieved from the PowerPivot workbook for a report is not compressed.</span></span> <span data-ttu-id="5bf66-133">クエリ デザイナーを使用してフィルターとパラメーターを指定し、レポートに必要なデータだけに制限します。</span><span class="sxs-lookup"><span data-stu-id="5bf66-133">Use the query designer to specify filters and parameters to limit the data to just what is needed in the report.</span></span>  
  
 <span data-ttu-id="5bf66-134">Analysis Services キューブへの接続とは異なり、PowerPivot モデルには階層はありません。</span><span class="sxs-lookup"><span data-stu-id="5bf66-134">Unlike connecting to an Analysis Services cube, a PowerPivot model has no hierarchies.</span></span> <span data-ttu-id="5bf66-135">ブック内の関連するスライサーに同様の機能を提供するには、レポートでカスケード型パラメーターを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5bf66-135">To provide similar functionality to related slicers in the workbook, you must create cascading parameters in the report.</span></span> <span data-ttu-id="5bf66-136">詳細については、「 [カスケード型パラメーターのレポートへの追加 (レポート ビルダーおよび SSRS)](../report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)で作成するモバイル レポートで使用できます。</span><span class="sxs-lookup"><span data-stu-id="5bf66-136">For more information, see [Add Cascading Parameters to a Report &#40;Report Builder and SSRS&#41;](../report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="5bf66-137">PowerPivot モデルの基になるデータ値に対応するように、式を調整しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="5bf66-137">In some cases, you might need to adjust expressions to accommodate the underlying data values from the PowerPivot model.</span></span> <span data-ttu-id="5bf66-138">式を変更してデータを適切なデータ型に変換したり、集計関数を追加または削除したりすることが必要になります。</span><span class="sxs-lookup"><span data-stu-id="5bf66-138">You might need to modify expressions to convert data to the right data type or to add or remove an aggregate function.</span></span> <span data-ttu-id="5bf66-139">たとえば、データ型を文字列型から整数型に変換するには、 `=CInt`を使用します。</span><span class="sxs-lookup"><span data-stu-id="5bf66-139">For example, to convert data type from String to Integer, use `=CInt`.</span></span> <span data-ttu-id="5bf66-140">レポートをパブリッシュする前に、PowerPivot モデルのデータから意図した値が表示されることを必ず確認してください。</span><span class="sxs-lookup"><span data-stu-id="5bf66-140">Always verify that the report displays the expected values from the data in the PowerPivot model before you publish the report.</span></span>  
  
 <span data-ttu-id="5bf66-141">PowerPivot ギャラリーのレポートのプレビュー イメージは、以下の条件を満たしている場合にのみ生成されます。</span><span class="sxs-lookup"><span data-stu-id="5bf66-141">Preview images of a report in a PowerPivot Gallery are generated only if the following conditions are met:</span></span>  
  
-   <span data-ttu-id="5bf66-142">データを提供するレポートおよび PowerPivot ブックは、同じ PowerPivot ギャラリーに一緒に保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5bf66-142">The report and the PowerPivot workbook that provides the data must be stored together in the same PowerPivot Gallery.</span></span>  
  
-   <span data-ttu-id="5bf66-143">レポートには、PowerPivot データ ソースからの PowerPivot データのみが格納されます。</span><span class="sxs-lookup"><span data-stu-id="5bf66-143">The report contains only PowerPivot data from a PowerPivot data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bf66-144">参照</span><span class="sxs-lookup"><span data-stu-id="5bf66-144">See Also</span></span>  
 <span data-ttu-id="5bf66-145">[Analysis Services の MDX クエリ デザイナーのユーザー インターフェイス &#40;レポート ビルダー&#41;](../analysis-services-mdx-query-designer-user-interface-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="5bf66-145">[Analysis Services MDX Query Designer User Interface &#40;Report Builder&#41;](../analysis-services-mdx-query-designer-user-interface-report-builder.md) </span></span>  
 [<span data-ttu-id="5bf66-146">式 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="5bf66-146">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
