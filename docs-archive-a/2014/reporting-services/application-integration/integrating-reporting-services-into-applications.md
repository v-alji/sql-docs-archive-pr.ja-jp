---
title: アプリケーションへの Reporting Services の統合 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- integrating reports [Reporting Services]
- custom applications [SSRS]
- Reporting Services, application integration
- application integration [Reporting Services]
- reports [Reporting Services], integrating
ms.assetid: 49eb539c-d89b-4291-839a-0ec1a65cd270
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3ab92008c5beb4d931e8e781857d766bb56a1efd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631673"
---
# <a name="integrating-reporting-services-into-applications"></a><span data-ttu-id="200df-102">アプリケーションへの Reporting Services の統合</span><span class="sxs-lookup"><span data-stu-id="200df-102">Integrating Reporting Services into Applications</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="200df-103">は、拡張性のあるオープンなレポート プラットフォームであり、ソリューションを開発するための API の包括的なセットを開発者に提供するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="200df-103">is an open and extensible reporting platform designed to provide developers with a comprehensive set of APIs for developing solutions.</span></span>  
  
 <span data-ttu-id="200df-104">カスタムアプリケーションに統合するには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポートサーバー Web サービス (SOAP API とも呼ばれます)、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の ReportViewer コントロール、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] および URL アクセスの3つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="200df-104">There are three options for integrating [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into custom applications: the Report Server Web service, also known as the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SOAP API, the ReportViewer controls for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)], and URL access.</span></span> <span data-ttu-id="200df-105">アプリケーションに [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を統合する方法は、オプションごとに異なります。</span><span class="sxs-lookup"><span data-stu-id="200df-105">Each option provides a different approach for integrating [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into your applications.</span></span>  
  
## <a name="report-server-web-service"></a><span data-ttu-id="200df-106">レポート サーバー Web サービス</span><span class="sxs-lookup"><span data-stu-id="200df-106">Report Server Web Service</span></span>  
 <span data-ttu-id="200df-107">レポート サーバー Web サービスは、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] に対して開発を行うための主要なインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="200df-107">The Report Server Web service is the primary interface for developing against [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="200df-108">レポート カタログを管理するためのコードを開発する場合でも、サポートされている形式でレポートを表示するためのコードを開発する場合でも、Web サービスでは [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をアプリケーションに統合するために必要なすべての方法が公開されています。</span><span class="sxs-lookup"><span data-stu-id="200df-108">Whether you are developing code to manage your report catalog or developing code to render reports to a supported format, the Web service exposes all the necessary methods to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into your applications.</span></span> <span data-ttu-id="200df-109">そのようなアプリケーションの一例が、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] に付属のレポート マネージャーです。レポート マネージャーでは、Web サービスを使用してレポート サーバー データベースを管理します。</span><span class="sxs-lookup"><span data-stu-id="200df-109">An example of one such application is Report Manager, which is included with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]; it uses the Web service to manage the report server database.</span></span>  
  
## <a name="reportviewer-controls-for-visual-studio"></a><span data-ttu-id="200df-110">Visual Studio の ReportViewer コントロール</span><span class="sxs-lookup"><span data-stu-id="200df-110">ReportViewer Controls for Visual Studio</span></span>  
 <span data-ttu-id="200df-111">[!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] に付属の ReportViewer コントロールは、レポート表示機能をアプリケーションに統合するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="200df-111">The ReportViewer controls included with [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] are used for integrating report viewing into your applications.</span></span> <span data-ttu-id="200df-112">コントロールには、Windows フォームベースのアプリケーション用と Web フォームのアプリケーション用の 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="200df-112">There are two controls: one for Windows Forms-based applications and one for Web Forms applications.</span></span> <span data-ttu-id="200df-113">どちらのコントロールにも、レポート サーバーに配置されたレポートを表示する機能と、レポート サーバーがインストールされていない環境にあるレポートを表示する機能があります。</span><span class="sxs-lookup"><span data-stu-id="200df-113">Each control provides the capability for viewing reports that have been deployed to a report server as well as the ability to render reports that exist in an environment where a report server has not been installed.</span></span>  
  
## <a name="url-access"></a><span data-ttu-id="200df-114">URL アクセス</span><span class="sxs-lookup"><span data-stu-id="200df-114">URL Access</span></span>  
 <span data-ttu-id="200df-115">URL アクセスは、ReportViewer コントロールがオプションでない場合にレポート表示機能をアプリケーションに統合するためのもう 1 つのオプションです。</span><span class="sxs-lookup"><span data-stu-id="200df-115">URL access is another option for integrating report viewing into your applications if the ReportViewer controls are not an option.</span></span> <span data-ttu-id="200df-116">さらに、電子メールを介してユーザーにレポートへのリンクを送信するためにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="200df-116">In addition, URL access is useful for sending links to reports to users via e-mail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="200df-117">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="200df-117">In This Section</span></span>  
 [<span data-ttu-id="200df-118">SOAP を使用した Reporting Services の統合</span><span class="sxs-lookup"><span data-stu-id="200df-118">Integrating Reporting Services Using SOAP</span></span>](../application-integration/integrating-reporting-services-using-soap.md)  
 <span data-ttu-id="200df-119">レポート サーバー Web サービスを使用して、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のレポート ナビゲーションおよび管理を既存のビジネス アプリケーションに統合する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="200df-119">Describes how to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report navigation and management into your existing business applications using the Report Server Web service.</span></span>  
  
 [<span data-ttu-id="200df-120">ReportViewer コントロールを使用した Reporting Services の統合</span><span class="sxs-lookup"><span data-stu-id="200df-120">Integrating Reporting Services Using the ReportViewer Controls</span></span>](../application-integration/integrating-reporting-services-using-reportviewer-controls.md)  
 <span data-ttu-id="200df-121">ReportViewer コントロールを使用して、レポート表示機能を既存のアプリケーションに統合する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="200df-121">Describes how to integrate report viewing into your existing applications using the ReportViewer controls.</span></span>  
  
 [<span data-ttu-id="200df-122">URL アクセスを使用した Reporting Services の統合</span><span class="sxs-lookup"><span data-stu-id="200df-122">Integrating Reporting Services Using URL Access</span></span>](../application-integration/integrating-reporting-services-using-url-access.md)  
 <span data-ttu-id="200df-123">URL アクセスを使用して、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のレポート ナビゲーションを既存のビジネス アプリケーションに統合する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="200df-123">Describes how to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report navigation into your existing business applications using URL access.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="200df-124">参照</span><span class="sxs-lookup"><span data-stu-id="200df-124">See Also</span></span>  
 <span data-ttu-id="200df-125">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="200df-125">[Report Manager  &#40;SSRS Native Mode&#41;](../../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="200df-126">[URL アクセスと SOAP の選択](../../../2014/reporting-services/application-integration/choosing-between-url-access-and-soap.md) </span><span class="sxs-lookup"><span data-stu-id="200df-126">[Choosing Between URL Access and SOAP](../../../2014/reporting-services/application-integration/choosing-between-url-access-and-soap.md) </span></span>  
 <span data-ttu-id="200df-127">[SSRS&#41;&#40;テクニカルリファレンス](../../../2014/reporting-services/technical-reference-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="200df-127">[Technical Reference &#40;SSRS&#41;](../../../2014/reporting-services/technical-reference-ssrs.md) </span></span>  
 [<span data-ttu-id="200df-128">レポート サーバー web サービス</span><span class="sxs-lookup"><span data-stu-id="200df-128">Report Server Web Service</span></span>](../report-server-web-service/report-server-web-service.md)  
  
  
