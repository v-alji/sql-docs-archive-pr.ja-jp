---
title: レポート サーバー Web サービスのエンドポイント | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- management endpoints [Reporting Services]
- Web service [Reporting Services], endpoints
- endpoints [Reporting Services]
- execution endpoints [Reporting Services]
- Report Server Web service, endpoints
ms.assetid: f3f5d85f-9359-4508-bc5a-7f78a3cf7421
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 70281c5171eb37d9888d663542a7850820c81bea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717360"
---
# <a name="report-server-web-service-endpoints"></a><span data-ttu-id="ba7c8-102">レポート サーバー Web サービスのエンドポイント</span><span class="sxs-lookup"><span data-stu-id="ba7c8-102">Report Server Web Service Endpoints</span></span>
  <span data-ttu-id="ba7c8-103">レポート サーバー Web サービスでは、レポートの実行およびナビゲーションに加えて、レポート サーバーの管理に利用できる複数のエンドポイントが提供されます。</span><span class="sxs-lookup"><span data-stu-id="ba7c8-103">The Report Server Web service provides several endpoints for managing a report server as well as executing and navigating reports.</span></span>  
  
## <a name="the-management-endpoints"></a><span data-ttu-id="ba7c8-104">管理エンドポイント</span><span class="sxs-lookup"><span data-stu-id="ba7c8-104">The Management Endpoints</span></span>  
 <span data-ttu-id="ba7c8-105"><xref:ReportService2005>、<xref:ReportService2006>、<xref:ReportService2010> という 3 つのエンドポイントを利用して、レポート サーバーでオブジェクトを管理できます。</span><span class="sxs-lookup"><span data-stu-id="ba7c8-105">There are three endpoints available for managing objects on a report server, <xref:ReportService2005>, <xref:ReportService2006>, and <xref:ReportService2010>.</span></span> <span data-ttu-id="ba7c8-106"><xref:ReportService2005> エンドポイントは、ネイティブ モード用に構成されたレポート サーバーのオブジェクトを管理するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="ba7c8-106">The <xref:ReportService2005> endpoint is used for managing objects on a report server that is configured for native mode.</span></span> <span data-ttu-id="ba7c8-107"><xref:ReportService2006> エンドポイントは、SharePoint 統合モード用に構成されたレポート サーバーのオブジェクトを管理するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="ba7c8-107">The <xref:ReportService2006> endpoint is used for managing objects on a report server that is configured for SharePoint integrated mode.</span></span> <span data-ttu-id="ba7c8-108"><xref:ReportService2010> エンドポイントは、<xref:ReportService2005> と <xref:ReportService2006> の機能をまとめたものであり、ネイティブ モード用または SharePoint 統合モード用に構成されているレポート サーバー上のオブジェクトを管理できます。</span><span class="sxs-lookup"><span data-stu-id="ba7c8-108">The <xref:ReportService2010> endpoint merges the functionalities of <xref:ReportService2005> and <xref:ReportService2006> and can manage objects on a report server that are configured for either native or SharePoint integrated mode.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ba7c8-109">レポート サーバーが SharePoint 統合モード用に構成されている場合、<xref:ReportService2005> API は `rsOperationNotSupportedSharePointMode` エラーを返します。</span><span class="sxs-lookup"><span data-stu-id="ba7c8-109">When a report server is configured for SharePoint integrated mode, the <xref:ReportService2005> APIs will return an `rsOperationNotSupportedSharePointMode` error.</span></span> <span data-ttu-id="ba7c8-110">レポート サーバーがネイティブ モード用に構成されている場合、<xref:ReportService2006> API は `rsOperationNotSupportedNativeMode` エラーを返します。</span><span class="sxs-lookup"><span data-stu-id="ba7c8-110">If the report server is configured for native mode, the <xref:ReportService2006> APIs will return an `rsOperationNotSupportedNativeMode` error.</span></span> <span data-ttu-id="ba7c8-111">同様に、<xref:ReportService2010> のモード固有 API を不適切なモードで使用した場合も、それぞれエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="ba7c8-111">Similarly, when mode-specific APIs in <xref:ReportService2010> are used on unintended modes, the APIs will return the respective errors.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ba7c8-112">[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] では、<xref:ReportService2005> エンドポイントと <xref:ReportService2006> エンドポイントは非推奨です。</span><span class="sxs-lookup"><span data-stu-id="ba7c8-112">The <xref:ReportService2005> and <xref:ReportService2006> endpoints are deprecated in [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)].</span></span> <span data-ttu-id="ba7c8-113"><xref:ReportService2010> エンドポイントには、両方のエンドポイントの機能と追加の管理機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ba7c8-113">The <xref:ReportService2010> endpoint includes the functionalities of both endpoints and contains additional management features.</span></span>  
  
 <span data-ttu-id="ba7c8-114">レポート サーバーがネイティブ モード用または SharePoint 統合モード用に構成されている場合、管理エンドポイントの WSDL には次の URL を使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="ba7c8-114">If the report server is configured for native mode or SharePoint integrate mode, the WSDL for the management endpoint can be accessed using one of the following URL:</span></span>  
  
```  
http://<Server Name>/ReportServer/ReportService2010.asmx?wsdl  
```  
  
 <span data-ttu-id="ba7c8-115">詳細については、「[SOAP API へのアクセス](../accessing-the-soap-api.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba7c8-115">For more information, see [Accessing the SOAP API](../accessing-the-soap-api.md).</span></span>  
  
## <a name="the-execution-endpoint"></a><span data-ttu-id="ba7c8-116">実行エンドポイント</span><span class="sxs-lookup"><span data-stu-id="ba7c8-116">The Execution Endpoint</span></span>  
 <span data-ttu-id="ba7c8-117"><xref:ReportExecution2005> エンドポイントを使用すると、開発者はネイティブ モードと SharePoint 統合モードの両方でレポート サーバーによるレポートの処理と表示を容易にカスタマイズできるようになります。</span><span class="sxs-lookup"><span data-stu-id="ba7c8-117">The <xref:ReportExecution2005> endpoint makes it easy for developers to customize report processing and rendering from a report server in both native and SharePoint integrated modes.</span></span> <span data-ttu-id="ba7c8-118">このエンドポイントには、以前のバージョンのレポート サーバー Web サービスに存在していたクラスとメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ba7c8-118">The endpoint includes classes and methods that existed in earlier versions of the Report Server Web service.</span></span> <span data-ttu-id="ba7c8-119">さらに、実行エンドポイントにより公開される多くの新しいクラスとメソッドがレポート サーバー Web サービスに追加されました。</span><span class="sxs-lookup"><span data-stu-id="ba7c8-119">In addition, many new classes and methods have been added to the Report Server Web service that are exposed through the execution endpoint.</span></span>  
  
 <span data-ttu-id="ba7c8-120">管理エンドポイントの WSDL には、次の URL を使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="ba7c8-120">The WSDL for the management endpoint can be accessed using the following URL:</span></span>  
  
```  
http://<Server Name>/ReportServer/ReportExecution2005.asmx?wsdl  
```  
  
 <span data-ttu-id="ba7c8-121">レポート サーバーが SharePoint 統合モード用に構成されている場合、WSDL には次の URL を使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="ba7c8-121">If the report server is configured for SharePoint integrate mode, the WSDL can be accessed using the following URL:</span></span>  
  
```  
http://<Server Name>/<Site Name>/_vti_bin/ReportServer/ReportExecution2005.asmx?wsdl  
```  
  
 <span data-ttu-id="ba7c8-122">詳細については、「[SOAP API へのアクセス](../accessing-the-soap-api.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba7c8-122">For more information, please see [Accessing the SOAP API](../accessing-the-soap-api.md).</span></span>  
  
## <a name="sharepoint-proxy-endpoints"></a><span data-ttu-id="ba7c8-123">SharePoint プロキシ エンドポイント</span><span class="sxs-lookup"><span data-stu-id="ba7c8-123">SharePoint Proxy Endpoints</span></span>  
 <span data-ttu-id="ba7c8-124">レポート サーバーが SharePoint 統合モード用に構成されていて、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] アドインがインストールされている場合、SharePoint サーバーにプロキシ エンドポイントのセットがインストールされています。</span><span class="sxs-lookup"><span data-stu-id="ba7c8-124">When a report server is configured for SharePoint integrated mode and the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Add-in has been installed, a set of proxy endpoints are installed on the SharePoint server.</span></span> <span data-ttu-id="ba7c8-125">プロキシ エンドポイントは、レポート サーバーが SharePoint 統合モード用に構成されている場合に、レポート ソリューションを開発するための主要な API として利用できます。</span><span class="sxs-lookup"><span data-stu-id="ba7c8-125">The proxy endpoints are the primary API for developing report solutions when a report server is configured for SharePoint integrated mode.</span></span> <span data-ttu-id="ba7c8-126">プロキシ エンドポイントに対して開発を行う場合、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] アドインは、信頼されたアカウント認証モードを使用して SharePoint サーバーとレポート サーバーの間で資格情報の交換を管理します。</span><span class="sxs-lookup"><span data-stu-id="ba7c8-126">When developing against the proxy endpoints, the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Add-in manages the exchange of credentials between the SharePoint server and the report server in Trusted account authentication mode.</span></span> <span data-ttu-id="ba7c8-127">レポート サーバー エンドポイントに対して開発を行う場合、呼び出し元のアプリケーションは、信頼されたアカウント認証モードを使用して資格情報の交換を管理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba7c8-127">When developing against the report server endpoints, the calling application will have to manage the credential exchange in Trusted account authentication mode.</span></span> <span data-ttu-id="ba7c8-128">次の表は、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] アドインと共にインストールされるエンドポイントの一覧です。</span><span class="sxs-lookup"><span data-stu-id="ba7c8-128">The following table lists the endpoints that are installed with the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Add-in.</span></span>  
  
|<span data-ttu-id="ba7c8-129">プロキシ エンドポイント</span><span class="sxs-lookup"><span data-stu-id="ba7c8-129">Proxy Endpoint</span></span>|<span data-ttu-id="ba7c8-130">説明</span><span class="sxs-lookup"><span data-stu-id="ba7c8-130">Description</span></span>|  
|--------------------|-----------------|  
|<xref:ReportService2006>|<span data-ttu-id="ba7c8-131">SharePoint 統合モード用に構成されたレポート サーバーを管理するための API を提供します。</span><span class="sxs-lookup"><span data-stu-id="ba7c8-131">Provides the APIs for managing a report server that is configured for SharePoint integrate mode.</span></span> <span data-ttu-id="ba7c8-132">**注:** このエンドポイントは、では非推奨とされ [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="ba7c8-132">**Note:**  This endpoint is deprecated in [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)].</span></span>|  
|<xref:ReportService2010>|<span data-ttu-id="ba7c8-133">ネイティブ モード用または SharePoint 統合モード用に構成されたレポート サーバーを管理するための API を提供します。</span><span class="sxs-lookup"><span data-stu-id="ba7c8-133">Provides the APIs for managing a report server that is configured for either native or SharePoint integrated mode.</span></span>|  
|<xref:ReportExecution2005>|<span data-ttu-id="ba7c8-134">レポートの実行とナビゲーションのための API を提供します。</span><span class="sxs-lookup"><span data-stu-id="ba7c8-134">Provides the APIs for running and navigating reports.</span></span>|  
|<xref:ReportServiceAuthentication>|<span data-ttu-id="ba7c8-135">SharePoint Web アプリケーションがフォーム認証用に構成されている場合にレポート サーバーに対してユーザーを認証するための API を提供します。</span><span class="sxs-lookup"><span data-stu-id="ba7c8-135">Provides the APIs for authenticating users against a report server when the SharePoint Web application is configured for Forms Authentication.</span></span>|  
  
 <span data-ttu-id="ba7c8-136">次の URL の例は、SharePoint サイトのプロキシ エンドポイントを参照しています。</span><span class="sxs-lookup"><span data-stu-id="ba7c8-136">The following are example URLs for referencing the proxy endpoints on a SharePoint site.</span></span>  
  
```  
http://<Server Name>/<Site Name>/_vti_bin/ReportServer/ReportService2010.asmx  
```  
  
```  
http://<Server Name>/<Site Name>/_vti_bin/ReportServer/ReportExecution2005.asmx  
```  
  
```  
http://<Server Name>/<Site Name>/_vti_bin/ReportServer/ReportServiceAuthentication.asmx  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba7c8-137">参照</span><span class="sxs-lookup"><span data-stu-id="ba7c8-137">See Also</span></span>  
 [<span data-ttu-id="ba7c8-138">Web サービスと .NET Framework を使用してのアプリケーションの構築</span><span class="sxs-lookup"><span data-stu-id="ba7c8-138">Building Applications Using the Web Service and the .NET Framework</span></span>](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
