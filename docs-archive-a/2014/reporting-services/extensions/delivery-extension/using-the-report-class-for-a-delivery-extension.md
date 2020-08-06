---
title: 配信拡張機能での Report クラスの使用 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], report information
- Report class
ms.assetid: 1145ac63-eafd-452a-82af-16f85b1676dd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a3f750c2383253636db255cbe9f1ce0ee676a9d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646034"
---
# <a name="using-the-report-class-for-a-delivery-extension"></a><span data-ttu-id="3ec46-102">配信拡張機能での Report クラスの使用</span><span class="sxs-lookup"><span data-stu-id="3ec46-102">Using the Report Class for a Delivery Extension</span></span>
  <span data-ttu-id="3ec46-103"><xref:Microsoft.ReportingServices.Interfaces.Report> クラスは、レポート サーバー データベースのレポートを表します。</span><span class="sxs-lookup"><span data-stu-id="3ec46-103">The <xref:Microsoft.ReportingServices.Interfaces.Report> class represents a report in the report server database.</span></span> <span data-ttu-id="3ec46-104">すべてのサブスクリプションは特定のレポートに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="3ec46-104">Any subscription is associated with a specific report.</span></span> <span data-ttu-id="3ec46-105">レポートは通知に含まれます。</span><span class="sxs-lookup"><span data-stu-id="3ec46-105">The report is contained in the notification.</span></span> <span data-ttu-id="3ec46-106">配信拡張機能では、通知の一部である <xref:Microsoft.ReportingServices.Interfaces.Report> オブジェクトを使用してレポートを生成できます。</span><span class="sxs-lookup"><span data-stu-id="3ec46-106">Your delivery extension can use the <xref:Microsoft.ReportingServices.Interfaces.Report> object that is part of the notification to render the report.</span></span> <span data-ttu-id="3ec46-107"><xref:Microsoft.ReportingServices.Interfaces.Report> オブジェクトには、レポート サーバーのレポートの URL やレポート名など、レポート固有のプロパティも含まれています。</span><span class="sxs-lookup"><span data-stu-id="3ec46-107">The <xref:Microsoft.ReportingServices.Interfaces.Report> object also contains report-specific properties, such as the URL to the report on the report server and the name of the report.</span></span> <span data-ttu-id="3ec46-108">これらのプロパティすべてを配信プロバイダーの一部として使用できます。</span><span class="sxs-lookup"><span data-stu-id="3ec46-108">These properties can all be used as part of your delivery provider.</span></span>  
  
 <span data-ttu-id="3ec46-109"><xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> クラスの <xref:Microsoft.ReportingServices.Interfaces.Report> メソッドを使用して、レポートを表示できます。</span><span class="sxs-lookup"><span data-stu-id="3ec46-109">The <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> method of the <xref:Microsoft.ReportingServices.Interfaces.Report> class can be used to render a report.</span></span> <span data-ttu-id="3ec46-110"><xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> メソッドは、1 つの表示レポートを構成する <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> オブジェクトの配列を 1 つ以上返します。</span><span class="sxs-lookup"><span data-stu-id="3ec46-110">The <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> method returns an array of one or more <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> objects that together comprise a single rendered report.</span></span> <span data-ttu-id="3ec46-111">1 番目の <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> オブジェクトが表示レポートです。</span><span class="sxs-lookup"><span data-stu-id="3ec46-111">The first <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> object is the rendered report.</span></span> <span data-ttu-id="3ec46-112">その他の <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> オブジェクトは、レポート データと一緒に配信される必要があるリソースです (HTML ファイルや関連付けられた画像など)。</span><span class="sxs-lookup"><span data-stu-id="3ec46-112">Any other <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> objects are resources that must be delivered along with the report data (for example, an HTML file and associated images).</span></span> <span data-ttu-id="3ec46-113">表示拡張機能がシングル ストリーム表示拡張機能である場合は (IMAGE、PDF、MHTML、および Excel)、配列の <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> オブジェクトを 1 つだけ返します。</span><span class="sxs-lookup"><span data-stu-id="3ec46-113">Rendering extensions that are single-stream rendering extensions (IMAGE, PDF, MHTML, and Excel) return only one <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> object in the array.</span></span>  
  
 <span data-ttu-id="3ec46-114">レポート ストリームを含む <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> オブジェクトは、配信の一部として含めることができます。</span><span class="sxs-lookup"><span data-stu-id="3ec46-114">The <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> object, which contains the report stream, can be included as part of a delivery.</span></span>  
  
 <span data-ttu-id="3ec46-115"><xref:Microsoft.ReportingServices.Interfaces.Report> クラスの使用例については、「[SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)」 (SQL Server Reporting Services 製品サンプル) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ec46-115">For an example of how to use the <xref:Microsoft.ReportingServices.Interfaces.Report> class, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ec46-116">参照</span><span class="sxs-lookup"><span data-stu-id="3ec46-116">See Also</span></span>  
 <span data-ttu-id="3ec46-117">[配信拡張機能の実装](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="3ec46-117">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 <span data-ttu-id="3ec46-118">[Reporting Services 拡張機能ライブラリ](../reporting-services-extension-library.md) </span><span class="sxs-lookup"><span data-stu-id="3ec46-118">[Reporting Services Extension Library](../reporting-services-extension-library.md) </span></span>  
 [<span data-ttu-id="3ec46-119">配信拡張機能での RenderedOutputFile クラスの使用</span><span class="sxs-lookup"><span data-stu-id="3ec46-119">Using the RenderedOutputFile Class for a Delivery Extension</span></span>](using-the-renderedoutputfile-class-for-a-delivery-extension.md)  
  
  
