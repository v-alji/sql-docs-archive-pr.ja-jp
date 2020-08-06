---
title: SOAP API へのアクセス | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- XML Web service [Reporting Services], WSDL
- Web service [Reporting Services], SOAP
- calling Web service
- SOAP [Reporting Services], accessing
- Report Server Web service, SOAP
- Web service [Reporting Services], WSDL
- WSDL [Reporting Services]
- XML Web service [Reporting Services], SOAP
- Report Server Web service, WSDL
- referencing WSDL
ms.assetid: 63bb870a-4dbf-46bd-8921-78f8ebe5fd75
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6e8a0c21bb53deff746cfd916b6ae2c96fa0de19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644296"
---
# <a name="accessing-the-soap-api"></a><span data-ttu-id="92e01-102">SOAP API へのアクセス</span><span class="sxs-lookup"><span data-stu-id="92e01-102">Accessing the SOAP API</span></span>
  <span data-ttu-id="92e01-103">レポート サーバー Web サービスは、SOAP (Simple Object Access Protocol) over HTTP を使用し、クライアント プログラムとレポート サーバー間の通信インターフェイスとして機能します。</span><span class="sxs-lookup"><span data-stu-id="92e01-103">The Report Server Web service uses Simple Object Access Protocol (SOAP) over HTTP and acts as a communications interface between client programs and the report server.</span></span> <span data-ttu-id="92e01-104">Web サービスには、レポート実行用とレポート管理用の 2 つのエンドポイントがあり、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の完全な機能にアクセスするために使用できるメソッドと複合型オブジェクトのセットで構成されます。</span><span class="sxs-lookup"><span data-stu-id="92e01-104">The Web service provides two endpoints - one for report execution and one for report management - and consists of methods and a set of complex type objects that you can use to access the complete functionality of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="92e01-105">Web サービスを呼び出すには、Reporting Services Web サービス記述言語 (WSDL) を参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="92e01-105">To call the service, you must reference the Reporting Services Web Services Description Language (WSDL).</span></span>  
  
## <a name="referencing-the-reporting-services-wsdl"></a><span data-ttu-id="92e01-106">Reporting Services WSDL の参照</span><span class="sxs-lookup"><span data-stu-id="92e01-106">Referencing the Reporting Services WSDL</span></span>  
 <span data-ttu-id="92e01-107">Web サービスを正常に呼び出すには、サービスへのアクセス方法、サービスがサポートする操作、サービスが想定するパラメーター、およびサービスが返すものを知っておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="92e01-107">To call a Web service successfully, you must know how to access the service, what operations the service supports, what parameters the service expects, and what the service returns.</span></span> <span data-ttu-id="92e01-108">WSDL は、コンピューターで読み取り、処理できる XML ドキュメントでこのような情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="92e01-108">WSDL provides this information in an XML document that can be read or processed by a computer.</span></span>  
  
 <span data-ttu-id="92e01-109">レポート サーバー Web サービスは、3 つの異なるエンドポイントで公開されます。</span><span class="sxs-lookup"><span data-stu-id="92e01-109">The Report Server Web services are exposed in three different endpoints.</span></span> <span data-ttu-id="92e01-110">WSDL ファイルの名前は、エンドポイントごとに異なります。</span><span class="sxs-lookup"><span data-stu-id="92e01-110">The name of the WSDL file is different for each endpoint.</span></span> <span data-ttu-id="92e01-111"><xref:ReportService2010> エンドポイントには、ネイティブ モードまたは SharePoint 統合モードでレポート サーバーのオブジェクトを管理するためのメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="92e01-111">The <xref:ReportService2010> endpoint contains methods for managing objects in a Report Server in either native or SharePoint integrated mode.</span></span> <span data-ttu-id="92e01-112">このエンドポイントの WSDL には、`ReportService2010.asmx?wsdl.` を通してアクセスします。</span><span class="sxs-lookup"><span data-stu-id="92e01-112">The WSDL for this endpoint is accessed through `ReportService2010.asmx?wsdl.`</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="92e01-113">[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] では、<xref:ReportService2005> エンドポイントと <xref:ReportService2006> エンドポイントは非推奨です。</span><span class="sxs-lookup"><span data-stu-id="92e01-113">The <xref:ReportService2005> and <xref:ReportService2006> endpoints are deprecated in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].</span></span> <span data-ttu-id="92e01-114"><xref:ReportService2010> エンドポイントには、両方のエンドポイントの機能と追加の管理機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="92e01-114">The <xref:ReportService2010> endpoint includes the functionalities of both endpoints and contains additional management features.</span></span>  
  
-   <span data-ttu-id="92e01-115"><xref:ReportExecution2005> エンドポイントでは、開発者がレポート サーバーのレポートをプログラムによって処理および表示できます。</span><span class="sxs-lookup"><span data-stu-id="92e01-115">The <xref:ReportExecution2005> endpoint allows developers to programmatically process and render reports in a Report Server.</span></span> <span data-ttu-id="92e01-116">このエンドポイントの WSDL には、`ReportExecution2005.asmx?wsdl` を通してアクセスします。</span><span class="sxs-lookup"><span data-stu-id="92e01-116">The WSDL for this endpoint is accessed through `ReportExecution2005.asmx?wsdl`.</span></span>  
  
 <span data-ttu-id="92e01-117">WSDL は、SDK などの SOAP および Web サービスをサポートする開発キットによって使用でき [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="92e01-117">WSDL can be consumed by development kits that support SOAP and Web services, such as the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.</span></span>  
  
 <span data-ttu-id="92e01-118">次の例は、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 管理 WSDL ファイルへの URL の書式を示しています。</span><span class="sxs-lookup"><span data-stu-id="92e01-118">The following example shows the format of the URL to the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] management WSDL file:</span></span>  
  
```  
http://server/reportserver/ReportService2010.asmx?wsdl  
```  
  
 <span data-ttu-id="92e01-119">次の表では、URL の各要素を説明します。</span><span class="sxs-lookup"><span data-stu-id="92e01-119">The following table describes each element in the URL.</span></span>  
  
|<span data-ttu-id="92e01-120">URL の要素</span><span class="sxs-lookup"><span data-stu-id="92e01-120">URL element</span></span>|<span data-ttu-id="92e01-121">説明</span><span class="sxs-lookup"><span data-stu-id="92e01-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="92e01-122">*server*</span><span class="sxs-lookup"><span data-stu-id="92e01-122">*server*</span></span>|<span data-ttu-id="92e01-123">レポート サーバーが配置されているサーバーの名前。</span><span class="sxs-lookup"><span data-stu-id="92e01-123">The name of the server on which the report server is deployed.</span></span>|  
|<span data-ttu-id="92e01-124">*reportserver*</span><span class="sxs-lookup"><span data-stu-id="92e01-124">*reportserver*</span></span>|<span data-ttu-id="92e01-125">XML Web サービスを含むフォルダーの名前。</span><span class="sxs-lookup"><span data-stu-id="92e01-125">The name of the folder that contains the XML Web service.</span></span> <span data-ttu-id="92e01-126">これはセットアップ中に構成されます。</span><span class="sxs-lookup"><span data-stu-id="92e01-126">This is configured during setup.</span></span>|  
|<span data-ttu-id="92e01-127">*\<endpoint name>.asmx*</span><span class="sxs-lookup"><span data-stu-id="92e01-127">*\<endpoint name>.asmx*</span></span>|<span data-ttu-id="92e01-128">Web サービス エンドポイントの名前。</span><span class="sxs-lookup"><span data-stu-id="92e01-128">The name of the web service endpoint.</span></span>|  
  
 <span data-ttu-id="92e01-129">WSDL フォーマットの詳細については、http://www.w3.org/TR/wsdl の W3C (World Wide Web Consortium) WSDL 仕様を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92e01-129">For more information about the WSDL format, see the World Wide Web Consortium (W3C) WSDL specification at http://www.w3.org/TR/wsdl.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92e01-130">参照</span><span class="sxs-lookup"><span data-stu-id="92e01-130">See Also</span></span>  
 <span data-ttu-id="92e01-131">[Web サービスと .NET Framework を使用してのアプリケーションの構築](net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="92e01-131">[Building Applications Using the Web Service and the .NET Framework](net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 [<span data-ttu-id="92e01-132">レポート サーバー web サービス</span><span class="sxs-lookup"><span data-stu-id="92e01-132">Report Server Web Service</span></span>](report-server-web-service.md)  
  
  
