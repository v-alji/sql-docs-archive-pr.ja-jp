---
title: SOAP を使用した Reporting Services の統合 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, application integration
- SOAP [Reporting Services]
- SOAP [Reporting Services], about report integration
- integrating reports [Reporting Services]
- Web service [Reporting Services], application integration
ms.assetid: 6bc17af5-883c-4bfa-87d9-48cd7056d145
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7b6fffd65b22900d7c505c4b50ec290b95fe9ab4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631667"
---
# <a name="integrating-reporting-services-using-soap"></a><span data-ttu-id="95178-102">SOAP を使用した Reporting Services の統合</span><span class="sxs-lookup"><span data-stu-id="95178-102">Integrating Reporting Services Using SOAP</span></span>
  <span data-ttu-id="95178-103">SOAP API には、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] カスタムレポートソリューションを開発するための Web サービスエンドポイントがいくつか用意されています。</span><span class="sxs-lookup"><span data-stu-id="95178-103">The [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SOAP API provides several Web service endpoints for developing custom reporting solutions.</span></span> <span data-ttu-id="95178-104">現在、このエンドポイントは、管理と実行という 2 つのカテゴリに分類されます。</span><span class="sxs-lookup"><span data-stu-id="95178-104">The endpoints currently fall into two categories: management and execution.</span></span> <span data-ttu-id="95178-105">管理機能は、<xref:ReportService2005> エンドポイント、<xref:ReportService2006> エンドポイント、および <xref:ReportService2010> エンドポイントを介して公開されます。</span><span class="sxs-lookup"><span data-stu-id="95178-105">The management functionality is exposed through the <xref:ReportService2005>, <xref:ReportService2006>, and <xref:ReportService2010> endpoints.</span></span> <span data-ttu-id="95178-106"><xref:ReportService2005> エンドポイントは、ネイティブ モードで構成されたレポート サーバーを管理するために使用され、<xref:ReportService2006> エンドポイントは、SharePoint 統合モード用に構成されたレポート サーバーを管理するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="95178-106">The <xref:ReportService2005> endpoint is used for managing a report server that is configured in native mode and the <xref:ReportService2006> endpoint is used for managing a report server that is configured for SharePoint integrated mode.</span></span> <span data-ttu-id="95178-107"><xref:ReportService2010> は、<xref:ReportService2005> と <xref:ReportService2006> の機能をまとめたものであり、ネイティブ モード用または SharePoint 統合モード用に構成されているレポート サーバーを管理できます。</span><span class="sxs-lookup"><span data-stu-id="95178-107">The <xref:ReportService2010> merges the functionalities of <xref:ReportService2005> and <xref:ReportService2006> and can manage a report server that is configured for either native or SharePoint integrated mode.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="95178-108">[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] では、<xref:ReportService2005> エンドポイントと <xref:ReportService2006> エンドポイントは非推奨です。</span><span class="sxs-lookup"><span data-stu-id="95178-108">The <xref:ReportService2005> and <xref:ReportService2006> endpoints are deprecated in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].</span></span> <span data-ttu-id="95178-109"><xref:ReportService2010> エンドポイントには、両方のエンドポイントの機能と追加の管理機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="95178-109">The <xref:ReportService2010> endpoint includes the functionalities of both endpoints and contains additional management features.</span></span>  
  
 <span data-ttu-id="95178-110">実行機能は <xref:ReportExecution2005> エンドポイントを介して公開され、レポート サーバーがネイティブ モードまたは SharePoint 統合モードで構成されているときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="95178-110">The execution functionality is exposed through the <xref:ReportExecution2005> endpoint and it is used when the report server is configured in native or SharePoint integrated mode.</span></span> <span data-ttu-id="95178-111">次の各トピックでは、これらのエンドポイントを使用して [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows、SharePoint、および Web アプリケーションでどのようにレポート ソリューションを開発するかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="95178-111">The following topics show how these endpoints can be used for developing reporting solutions in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, SharePoint, and Web applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="95178-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="95178-112">In This Section</span></span>  
 [<span data-ttu-id="95178-113">Windows アプリケーションでの SOAP API の使用</span><span class="sxs-lookup"><span data-stu-id="95178-113">Using the SOAP API in a Windows Application</span></span>](integrating-reporting-services-using-soap-windows-application.md)  
 <span data-ttu-id="95178-114">SOAP API を使用して [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を Windows 環境に統合する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="95178-114">Describes how to use the SOAP API to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into a Windows environment.</span></span>  
  
 [<span data-ttu-id="95178-115">Web アプリケーションでの SOAP API の使用</span><span class="sxs-lookup"><span data-stu-id="95178-115">Using the SOAP API in a Web Application</span></span>](integrating-reporting-services-using-soap-web-application.md)  
 <span data-ttu-id="95178-116">SOAP API を使用して [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を Web 環境に統合する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="95178-116">Describes how to use the SOAP API to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into a Web environment.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95178-117">参照</span><span class="sxs-lookup"><span data-stu-id="95178-117">See Also</span></span>  
 <span data-ttu-id="95178-118">[アプリケーションへの Reporting Services の統合](../application-integration/integrating-reporting-services-into-applications.md) </span><span class="sxs-lookup"><span data-stu-id="95178-118">[Integrating Reporting Services into Applications](../application-integration/integrating-reporting-services-into-applications.md) </span></span>  
 <span data-ttu-id="95178-119">[レポート サーバー Web サービス](../report-server-web-service/report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="95178-119">[Report Server Web Service](../report-server-web-service/report-server-web-service.md) </span></span>  
 [<span data-ttu-id="95178-120">Web サービスと .NET Framework を使用してのアプリケーションの構築</span><span class="sxs-lookup"><span data-stu-id="95178-120">Building Applications Using the Web Service and the .NET Framework</span></span>](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
