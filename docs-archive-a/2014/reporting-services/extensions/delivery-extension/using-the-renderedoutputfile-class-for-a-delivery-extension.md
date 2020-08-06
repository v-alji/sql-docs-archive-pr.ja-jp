---
title: 配信拡張機能での RenderedOutputFile クラスの使用 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- RenderedOutputFile class
- data streams [Reporting Services]
- delivery extensions [Reporting Services], data streams
ms.assetid: 8b591801-42d5-49fa-b710-bf7e6917accf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1dcbf250a367326e5cad528384e533a9ac9d945b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646037"
---
# <a name="using-the-renderedoutputfile-class-for-a-delivery-extension"></a><span data-ttu-id="2c067-102">配信拡張機能での RenderedOutputFile クラスの使用</span><span class="sxs-lookup"><span data-stu-id="2c067-102">Using the RenderedOutputFile Class for a Delivery Extension</span></span>
  <span data-ttu-id="2c067-103"><xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> クラスは、データ ストリームおよびデータ ストリームの関連付けられたプロパティに関する情報を表します。</span><span class="sxs-lookup"><span data-stu-id="2c067-103">The <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> class represents a data stream and information about the data stream's associated properties.</span></span> <span data-ttu-id="2c067-104"><xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> クラスの **Data** プロパティは、表示レポートまたはレポート リソースを **Stream** オブジェクトとして表すために使用します。</span><span class="sxs-lookup"><span data-stu-id="2c067-104">The **Data** property of the <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> class is used to represent a rendered report or report resource as a **Stream** object.</span></span>  
  
 <span data-ttu-id="2c067-105">**Report** オブジェクトの <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> メソッドは、1 つの表示レポートを一緒に構成する 1 つ以上の <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> オブジェクトの配列を返します。</span><span class="sxs-lookup"><span data-stu-id="2c067-105">The <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> method of the **Report** object returns an array of one or more <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> objects that together constitute a single rendered report.</span></span> <span data-ttu-id="2c067-106">1 番目の <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> オブジェクトが表示レポートです。</span><span class="sxs-lookup"><span data-stu-id="2c067-106">The first <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> object is the rendered report.</span></span> <span data-ttu-id="2c067-107">その他の <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> オブジェクトは、レポート データと一緒に配信される必要があるリソースです (HTML ファイルや関連付けられた画像など)。</span><span class="sxs-lookup"><span data-stu-id="2c067-107">Any other <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> objects are resources that must be delivered along with the report data (for example, an HTML file and associated images).</span></span> <span data-ttu-id="2c067-108">表示拡張機能がシングル ストリーム表示拡張機能である場合は (IMAGE、PDF、MHTML、および EXCEL)、配列の <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> オブジェクトを 1 つだけ返します。</span><span class="sxs-lookup"><span data-stu-id="2c067-108">Rendering extensions that are single-stream rendering extensions (IMAGE, PDF, MHTML, and EXCEL) return only one <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> object in the array.</span></span>  
  
 <span data-ttu-id="2c067-109"><xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> クラスの使用例については、「[SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)」 (SQL Server Reporting Services 製品サンプル) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c067-109">For an example of how to use the <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> class, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c067-110">参照</span><span class="sxs-lookup"><span data-stu-id="2c067-110">See Also</span></span>  
 <span data-ttu-id="2c067-111">[配信拡張機能の実装](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="2c067-111">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="2c067-112">Reporting Services 拡張機能ライブラリ</span><span class="sxs-lookup"><span data-stu-id="2c067-112">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
