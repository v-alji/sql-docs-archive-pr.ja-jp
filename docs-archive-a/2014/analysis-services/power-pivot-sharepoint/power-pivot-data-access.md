---
title: PowerPivot データアクセス |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 83dc82da-91fb-4e47-91a8-0e0db67339b8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8faeec7b2e12871467b93f136360e9a68a0e5acb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644159"
---
# <a name="powerpivot-data-access"></a><span data-ttu-id="9d062-102">PowerPivot データ アクセス</span><span class="sxs-lookup"><span data-stu-id="9d062-102">PowerPivot Data Access</span></span>
  <span data-ttu-id="9d062-103">このトピックでは、SharePoint ライブラリにパブリッシュされる PowerPivot ブックからデータを取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9d062-103">This topic describes the ways in which data is retrieved from a PowerPivot workbook that is published to a SharePoint library.</span></span>  
  
 <span data-ttu-id="9d062-104">PowerPivot データは Excel ブック内に格納されます。</span><span class="sxs-lookup"><span data-stu-id="9d062-104">PowerPivot data is stored inside an Excel workbook.</span></span> <span data-ttu-id="9d062-105">接続文字列は、SharePoint サイト上のブックの URL です。</span><span class="sxs-lookup"><span data-stu-id="9d062-105">The connection string is a URL to a workbook on a SharePoint site.</span></span>  
  
 <span data-ttu-id="9d062-106">PowerPivot データは、そのデータが含まれるブックによってピボットテーブルとピボットグラフのデータとして頻繁に使用されます。</span><span class="sxs-lookup"><span data-stu-id="9d062-106">PowerPivot data is most often used by the workbook that contains it, as the data behind PivotTables and PivotCharts.</span></span> <span data-ttu-id="9d062-107">または、PowerPivot データを外部データ ソースとして使用することもできます。その場合は、ブック、ダッシュボード、またはレポートが SharePoint で別の Excel (.xlsx) ファイルに接続してデータを取得し、そのデータを後で使用します。</span><span class="sxs-lookup"><span data-stu-id="9d062-107">Alternatively, PowerPivot data can also be used as an external data source, where a workbook, dashboard, or report connects to a separate Excel (.xlsx) file in SharePoint and retrieves the data for subsequent use.</span></span> <span data-ttu-id="9d062-108">PowerPivot データをよく使用するクライアント ツールは Excel、[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]、他の Reporting Services レポート、および PerformancePoint です。</span><span class="sxs-lookup"><span data-stu-id="9d062-108">Client tools that typically use PowerPivot data are Excel, [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], other Reporting Services reports, and PerformancePoint.</span></span>  
  
 <span data-ttu-id="9d062-109">デスクトップでは、PowerPivot アドインは AMO と ADOMD.NET を使用して、クライアント ワークスペースで PowerPivot データの作成、処理、およびクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="9d062-109">On the desktop, the PowerPivot add-in uses AMO and ADOMD.NET to create, process, and query the PowerPivot data in the client workspace.</span></span>  
  
 <span data-ttu-id="9d062-110">SharePoint ファームでは、Excel Services はローカル MSOLAP OLE DB プロバイダーを使用して PowerPivot データに接続します。</span><span class="sxs-lookup"><span data-stu-id="9d062-110">On a SharePoint farm, Excel Services uses the local MSOLAP OLE DB provider to connect to PowerPivot data.</span></span> <span data-ttu-id="9d062-111">プロバイダーは、この接続要求をファーム内の PowerPivot for SharePoint サーバーに送信します。</span><span class="sxs-lookup"><span data-stu-id="9d062-111">The provider sends the connection request to a PowerPivot for SharePoint server in the farm.</span></span> <span data-ttu-id="9d062-112">このサーバーがデータをロードし、クエリを実行し、結果セットを返します。</span><span class="sxs-lookup"><span data-stu-id="9d062-112">That server loads the data, runs the query, and returns the result set.</span></span>  
  
##  <a name="querying-powerpivot-data-in-sharepoint"></a><a name="queryproc"></a><span data-ttu-id="9d062-113">SharePoint での PowerPivot データのクエリ</span><span class="sxs-lookup"><span data-stu-id="9d062-113">Querying PowerPivot Data in SharePoint</span></span>  
 <span data-ttu-id="9d062-114">PowerPivot ブックを SharePoint ライブラリから表示すると、ブック内の PowerPivot データがファームにある Analysis Services サーバー インスタンスで個別に検出、抽出、および処理されて、同時に Excel Services によってプレゼンテーション層が描画されます。</span><span class="sxs-lookup"><span data-stu-id="9d062-114">When you view a PowerPivot workbook from a SharePoint library, the PowerPivot data that is inside the workbook is detected, extracted, and processed separately on Analysis Services server instances within the farm, while Excel Services renders the presentation layer.</span></span> <span data-ttu-id="9d062-115">完全に処理されたブックは、ブラウザー ウィンドウ、または PowerPivot アドインを持つ Excel 2010 デスクトップ アプリケーションで表示できます。</span><span class="sxs-lookup"><span data-stu-id="9d062-115">You can view the fully-processed workbook in a browser window or in an Excel 2010 desktop application that has the PowerPivot add-in.</span></span>  
  
 <span data-ttu-id="9d062-116">次の図は、クエリ処理の要求がファーム内をどのように移動するかを示しています。</span><span class="sxs-lookup"><span data-stu-id="9d062-116">The following diagram shows how a request for query processing moves through the farm.</span></span> <span data-ttu-id="9d062-117">PowerPivot データは Excel 2010 ブックの一部なので、クエリ処理の要求は、ユーザーが Excel ブックを SharePoint ライブラリから開いて、PowerPivot データを含むピボットテーブルまたはピボットグラフを操作したときに発生します。</span><span class="sxs-lookup"><span data-stu-id="9d062-117">Because PowerPivot data is part of an Excel 2010 workbook, a request for query processing occurs when a user opens an Excel workbook from a SharePoint library and interacts with a PivotTable or PivotChart that contains PowerPivot data.</span></span>  
  
 <span data-ttu-id="9d062-118">![GMNI_DataProcReq](../media/gmni-dataprocreq.gif "GMNI_DataProcReq")</span><span class="sxs-lookup"><span data-stu-id="9d062-118">![GMNI_DataProcReq](../media/gmni-dataprocreq.gif "GMNI_DataProcReq")</span></span>  
  
 <span data-ttu-id="9d062-119">Excel Services と PowerPivot for SharePoint コンポーネントは、同じブック (.xlsx) ファイルの異なる部分を処理します。</span><span class="sxs-lookup"><span data-stu-id="9d062-119">Excel Services and PowerPivot for SharePoint components process different parts of the same workbook (.xlsx) file.</span></span> <span data-ttu-id="9d062-120">Excel Services は、PowerPivot データを検出して、ファーム内の PowerPivot サーバーから処理を要求します。</span><span class="sxs-lookup"><span data-stu-id="9d062-120">Excel Services detects PowerPivot data and requests processing from a PowerPivot server in the farm.</span></span> <span data-ttu-id="9d062-121">PowerPivot サーバーは、コンテンツ ライブラリのブックからデータを抽出して読み込む [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] インスタンスに要求を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="9d062-121">The PowerPivot server allocates the request to an [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] instance, which extracts the data from the workbook in the content library and loads the data.</span></span> <span data-ttu-id="9d062-122">メモリに格納されたデータは描画されたブックにマージされ、ブラウザー ウィンドウに表示するために Excel Web Access に返されます。</span><span class="sxs-lookup"><span data-stu-id="9d062-122">Data that is stored in memory is merged back into the rendered workbook, and passed back to Excel Web Access for presentation in a browser window.</span></span>  
  
 <span data-ttu-id="9d062-123">PowerPivot ブックのデータの一部は、PowerPivot for SharePoint によって処理されません。</span><span class="sxs-lookup"><span data-stu-id="9d062-123">Not all data in a PowerPivot workbook is handled by PowerPivot for SharePoint.</span></span> <span data-ttu-id="9d062-124">ワークシートのテーブルおよびセル データは Excel Services によって処理されます。</span><span class="sxs-lookup"><span data-stu-id="9d062-124">Excel Services processes tables and cell data in a worksheet.</span></span> <span data-ttu-id="9d062-125">PowerPivot for SharePoint によって処理されるのは、PowerPivot データに合わないピボットテーブル、ピボットグラフ、およびスライサーだけです。</span><span class="sxs-lookup"><span data-stu-id="9d062-125">Only PivotTables, PivotCharts, and Slicers that go against PowerPivot data are handled by the PowerPivot for SharePoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d062-126">参照</span><span class="sxs-lookup"><span data-stu-id="9d062-126">See Also</span></span>  
 <span data-ttu-id="9d062-127">[Analysis Services への接続](../instances/connect-to-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="9d062-127">[Connect to Analysis Services](../instances/connect-to-analysis-services.md) </span></span>  
 [<span data-ttu-id="9d062-128">テーブル モデル データ アクセス</span><span class="sxs-lookup"><span data-stu-id="9d062-128">Tabular Model Data Access</span></span>](../tabular-models/tabular-model-data-access.md)  
  
  
