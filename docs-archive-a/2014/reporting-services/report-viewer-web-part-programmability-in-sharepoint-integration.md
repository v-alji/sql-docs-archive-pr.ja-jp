---
title: SharePoint 統合でのレポート ビューアー Web パーツのプログラミング | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
ms.assetid: 714017b7-1bd6-4950-a3c6-d0df8450a877
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 494ebc3e6668e4d95480019e522caf46b83a6c4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719526"
---
# <a name="report-viewer-web-part-programmability-in-sharepoint-integration"></a><span data-ttu-id="97e51-102">SharePoint 統合でのレポート ビューアー Web パーツのプログラミング</span><span class="sxs-lookup"><span data-stu-id="97e51-102">Report Viewer Web Part Programmability in SharePoint Integration</span></span>
  <span data-ttu-id="97e51-103">レポート ビューアー Web パーツは、`T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart` サーバー コントロールです。このサーバー コントロールには、開発者がカスタム SharePoint アプリケーションを作成するためのパブリック アプリケーション プログラミング インターフェイス (API) のセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="97e51-103">The Report Viewer Web Part is a `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart` server control, which contains a set of public application programming interfaces (API) that enables developers to create custom SharePoint applications.</span></span> <span data-ttu-id="97e51-104">Web パーツ接続を使用し、レポート ビューアー Web パーツにレポートのパスとパラメーターを指定するカスタム Web パーツを作成できます。</span><span class="sxs-lookup"><span data-stu-id="97e51-104">You can create custom Web Parts that supply report path and parameters to Report Viewer Web Part using Web Part connections.</span></span> <span data-ttu-id="97e51-105">Web パーツをカスタム SharePoint Web パーツ ページに埋め込み、パブリック API を使用してカスタマイズすることもできます。</span><span class="sxs-lookup"><span data-stu-id="97e51-105">You can also embed the Web Part in a custom SharePoint Web Part page and customize it using the public API.</span></span>  
  
## <a name="connecting-to-report-viewer-web-part-with-custom-web-parts"></a><span data-ttu-id="97e51-106">レポート ビューアー Web パーツとカスタム Web パーツとの接続</span><span class="sxs-lookup"><span data-stu-id="97e51-106">Connecting to Report Viewer Web Part with Custom Web Parts</span></span>  
 <span data-ttu-id="97e51-107">レポート ビューアー Web パーツは、<xref:System.Web.UI.WebControls.WebParts.IWebPartRow> または `T:Microsoft.SharePoint.WebPartPages.IFilterValues` を実装する SharePoint Web パーツに接続するコンシューマーです。</span><span class="sxs-lookup"><span data-stu-id="97e51-107">The Report Viewer Web Part is a connection consumer to SharePoint Web Parts that implement <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> or `T:Microsoft.SharePoint.WebPartPages.IFilterValues`.</span></span> <span data-ttu-id="97e51-108">**ドキュメント** Web パーツなどの <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web パーツを同じ Web パーツ ページにレポート ビューアー Web パーツとして配置すると、レポート ビューアー Web パーツにレポート パスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="97e51-108">An <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web Part, such as the **Documents** Web Part can supply a report path to a Report Viewer Web Part when placed on the same Web Part page as the Report Viewer Web Part.</span></span> <span data-ttu-id="97e51-109">同様に、 `T:Microsoft.SharePoint.WebPartPages.IFilterValues` **テキストフィルター**や**選択フィルター**などの web パーツは、レポートビューアー Web パーツと同じ web パーツページに配置されているレポートビューアー web パーツにレポートパラメーターを指定できます。</span><span class="sxs-lookup"><span data-stu-id="97e51-109">Likewise, an `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web Part, such as the **Text Filter** or the **Choice Filter**, can supply a report parameter to a Report Viewer Web Part when placed on the same Web Part page as the Report Viewer Web Part.</span></span>  
  
### <a name="implementing-a-report-path-provider-with-iwebpartrow"></a><span data-ttu-id="97e51-110">レポート パス プロバイダーと IWebPartRow の実装</span><span class="sxs-lookup"><span data-stu-id="97e51-110">Implementing a Report Path Provider with IWebPartRow</span></span>  
 <span data-ttu-id="97e51-111">Web パーツ接続を通じてレポート ビューアー Web パーツにレポートのパスを指定するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="97e51-111">To supply a report path to the Report Viewer Web Part through Web Part connections, do the following:</span></span>  
  
1.  <span data-ttu-id="97e51-112"><xref:System.Web.UI.WebControls.WebParts.IWebPartRow> インターフェイスを実装する Web パーツを作成します。</span><span class="sxs-lookup"><span data-stu-id="97e51-112">Create a Web Part that implements the <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> interface.</span></span>  
  
2.  <span data-ttu-id="97e51-113">Web パーツを同じ Web パーツ ページにレポート ビューアー Web パーツとして追加します。</span><span class="sxs-lookup"><span data-stu-id="97e51-113">Add the Web Part to the same Web Part page as the Report Viewer Web Part.</span></span>  
  
3.  <span data-ttu-id="97e51-114">Web ベースの Web パーツ デザイン ユーザー インターフェイスで Web パーツをレポート ビューアー Web パーツに接続します。</span><span class="sxs-lookup"><span data-stu-id="97e51-114">Connect your Web Part to the Report Viewer Web Part in the Web-based Web Part design user interface.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="97e51-115">レポート ビューアー Web パーツに一度に接続できる <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web パーツは 1 つだけです。レポート ビューアー Web パーツに <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web パーツおよび `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web パーツの両方を同時に接続することはできません。</span><span class="sxs-lookup"><span data-stu-id="97e51-115">You can only connect one <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web Part to the Report Viewer Web Part at a time, and you cannot connect both an <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web Part and an `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web Part to the Report Viewer Web Part at the same time.</span></span>  
  
 <span data-ttu-id="97e51-116"><xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web パーツが `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart` で適切に機能するようにするには、<xref:System.Web.UI.WebControls.WebParts.IWebPartRow.GetRowData%2A> メソッドで次の操作を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="97e51-116">For your <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web Part to work properly with the `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart`, you must do the following in the <xref:System.Web.UI.WebControls.WebParts.IWebPartRow.GetRowData%2A> method:</span></span>  
  
-   <span data-ttu-id="97e51-117"><xref:System.Data.DataRowView> オブジェクトを入力パラメーターとして使用してコールバック メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="97e51-117">Invoke the callback method with a <xref:System.Data.DataRowView> object as the input parameter.</span></span>  
  
-   <span data-ttu-id="97e51-118"><xref:System.Data.DataRowView> オブジェクトに、レポート パスを含む "DocUrl" という列が含まれるようにします。</span><span class="sxs-lookup"><span data-stu-id="97e51-118">Make sure that the <xref:System.Data.DataRowView> object contains a column called "DocUrl" that contains the report path.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="97e51-119">[!INCLUDE[offSPServ](../includes/offspserv-md.md)] 2010 用アドインのレポート ビューアー Web パーツでは、"FileRef" 列を使用するレポート パスを受信することもできます。</span><span class="sxs-lookup"><span data-stu-id="97e51-119">The Report Viewer Web Part in the add-in for [!INCLUDE[offSPServ](../includes/offspserv-md.md)] 2010 also supports receiving the report path using the "FileRef" column.</span></span>  
  
### <a name="implementing-a-report-parameter-provider-with-ifiltervalues"></a><span data-ttu-id="97e51-120">レポート パラメーター プロバイダーと IFilterValues の実装</span><span class="sxs-lookup"><span data-stu-id="97e51-120">Implementing a Report Parameter Provider with IFilterValues</span></span>  
 <span data-ttu-id="97e51-121">`T:Microsoft.SharePoint.WebPartPages.IFilterValues` を実装する Web パーツは、レポート ビューアー Web パーツに 1 つのパラメーター値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="97e51-121">A Web Part that implements `T:Microsoft.SharePoint.WebPartPages.IFilterValues` can provide one parameter value to the Report Viewer Web Part.</span></span> <span data-ttu-id="97e51-122">レポート ビューアー Web パーツに送信されるパラメーター値には、レポート定義で指定された、レポート パラメーターに対する制限と同じ制限 (データ型、有効な値など) が課されます。</span><span class="sxs-lookup"><span data-stu-id="97e51-122">The parameter value sent to the Report Viewer Web Part is subject to the same restrictions placed on the report parameter as specified in the report definition, such as data type, valid values, and so on</span></span>  
  
 <span data-ttu-id="97e51-123">レポート ビューアー Web パーツにレポート パラメーターを指定するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="97e51-123">To supply a report parameter to the Report Viewer Web Part, do the following:</span></span>  
  
1.  <span data-ttu-id="97e51-124">`T:Microsoft.SharePoint.WebPartPages.IFilterValues` インターフェイスを実装する Web パーツを作成します。</span><span class="sxs-lookup"><span data-stu-id="97e51-124">Create a Web Part that implements the `T:Microsoft.SharePoint.WebPartPages.IFilterValues` interface.</span></span>  
  
2.  <span data-ttu-id="97e51-125">Web パーツを同じ Web パーツ ページに `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart` として追加します。</span><span class="sxs-lookup"><span data-stu-id="97e51-125">Add the Web Part to the same page as the `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart`.</span></span>  
  
3.  <span data-ttu-id="97e51-126">Web ベースの Web パーツ デザイン ユーザー インターフェイスで `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web パーツをレポート ビューアー Web パーツに接続します。</span><span class="sxs-lookup"><span data-stu-id="97e51-126">Connect your `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web Part to the Report Viewer Web Part in the Web-based Web Part design user interface.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="97e51-127">一度に複数の `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web パーツをレポート ビューアー Web パーツに接続できます。</span><span class="sxs-lookup"><span data-stu-id="97e51-127">You can connect multiple `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web Parts to the Report Viewer Web Part at a time.</span></span> <span data-ttu-id="97e51-128">ただし、レポート ビューアー Web パーツに <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web パーツと `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web パーツの両方を同時に接続することはできません。</span><span class="sxs-lookup"><span data-stu-id="97e51-128">However, you cannot connect both an <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web Part and an `T:Microsoft.SharePoint.WebPartPages.IFilterValues` Web Part to the Report Viewer Web Part at the same time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97e51-129">参照</span><span class="sxs-lookup"><span data-stu-id="97e51-129">See Also</span></span>  
 <span data-ttu-id="97e51-130">[IFilterValues インターフェイス](https://msdn.microsoft.com/library/office/microsoft.sharepoint.webpartpages.ifiltervalues\(v=office.15\).aspx)</span><span class="sxs-lookup"><span data-stu-id="97e51-130">[IFilterValues interface](https://msdn.microsoft.com/library/office/microsoft.sharepoint.webpartpages.ifiltervalues\(v=office.15\).aspx)</span></span>  
  
  
