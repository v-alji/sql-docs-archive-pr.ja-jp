---
title: Developer&#39;s ガイド (Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- developer's guide [Reporting Services]
- Reporting Services, programming
- programming [Reporting Services]
ms.assetid: d8afa405-1012-4349-a72d-e10d94f8453d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bcf880db543c891a0ffccab932fddc614df34e17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719478"
---
# <a name="developer39s-guide-reporting-services"></a><span data-ttu-id="2163a-102">Developer&#39;s ガイド (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="2163a-102">Developer&#39;s Guide (Reporting Services)</span></span>
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="2163a-103">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] には、独自のアプリケーションで活用できるいくつかのプログラミング インターフェイスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="2163a-103">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] offers several programming interfaces that you can leverage in your own applications.</span></span> <span data-ttu-id="2163a-104">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] の既存機能を使用して、カスタム レポート ツールと管理ツールを Web サイトや Windows アプリケーションに組み込むことができます。また、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のプラットフォームを拡張することもできます。</span><span class="sxs-lookup"><span data-stu-id="2163a-104">You can use the existing features and capabilities of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] to build custom reporting and management tools into Web sites and Windows applications, or you can extend the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] platform.</span></span>  
  
 <span data-ttu-id="2163a-105">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] プラットフォームの拡張には、データへのアクセス、レポート配信などに使用できる新しいコンポーネントとリソースの作成もあります。</span><span class="sxs-lookup"><span data-stu-id="2163a-105">Extending the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] platform includes creating new components and resources that can be used for data access, report delivery and more.</span></span> <span data-ttu-id="2163a-106">これらのコンポーネントとリソースは、組織内で [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] を使用している企業に販売できます。</span><span class="sxs-lookup"><span data-stu-id="2163a-106">You can market these components and resources to companies that are using [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in their organization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2163a-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="2163a-107">In This Section</span></span>  
 [<span data-ttu-id="2163a-108">アプリケーションへの Reporting Services の統合</span><span class="sxs-lookup"><span data-stu-id="2163a-108">Integrating Reporting Services into Applications</span></span>](application-integration/integrating-reporting-services-into-applications.md)  
 <span data-ttu-id="2163a-109">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] を使用してレポート機能をカスタム アプリーションに統合する方法の概要です。</span><span class="sxs-lookup"><span data-stu-id="2163a-109">Provides an overview of how to use [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] to integrate reporting into custom applications.</span></span> <span data-ttu-id="2163a-110">レポート サーバーにアクセスするにあたり、どのような場合に直接的な URL アクセスを使用し、どのような場合に Web サービスを使用するかを説明します。</span><span class="sxs-lookup"><span data-stu-id="2163a-110">Describes when to use direct URL access and when to use the Web service to access the report server.</span></span>  
  
 [<span data-ttu-id="2163a-111">レポート サーバー web サービス</span><span class="sxs-lookup"><span data-stu-id="2163a-111">Report Server Web Service</span></span>](report-server-web-service/report-server-web-service.md)  
 <span data-ttu-id="2163a-112">レポート サーバー Web サービスでは、レポート サーバーのすべての機能にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="2163a-112">The Report Server Web service provides access to the full functionality of the report server.</span></span> <span data-ttu-id="2163a-113">Web サービスは、HTTP に対して SOAP を使用し、クライアント プログラムとレポート サーバー間の通信インターフェイスとして動作するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="2163a-113">The Web service uses SOAP over HTTP and is designed to act as a communications interface between client programs and the report server.</span></span> <span data-ttu-id="2163a-114">Web サービスとそのメソッドは、レポート サーバーの機能を提供するため、管理から実行までのレポートのライフ サイクルのあらゆる部分にカスタム ツールを作成できます。</span><span class="sxs-lookup"><span data-stu-id="2163a-114">The Web service and its methods expose the functionality of the report server and allow you to create custom tools for any part of the report life cycle, from management to execution.</span></span>  
  
 [<span data-ttu-id="2163a-115">URL アクセス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="2163a-115">URL Access &#40;SSRS&#41;</span></span>](url-access-ssrs.md)  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="2163a-116">では、レポートのナビゲーションおよび表示を行うためにすばやくかつ簡単なアクセス ポイントとして使用できる URL ベースの完全な要求セットをサポートします。</span><span class="sxs-lookup"><span data-stu-id="2163a-116">supports a complete set of URL-based requests that you can use as a quick and easy access point for report navigation and viewing.</span></span> <span data-ttu-id="2163a-117">このテクノロジをレポート サーバー Web サービスと組み合わせることにより、完全なレポート ソリューションをカスタム ビジネス アプリケーションに統合できます。</span><span class="sxs-lookup"><span data-stu-id="2163a-117">You can use this technology in conjunction with the Report Server Web service to integrate a complete reporting solution into your custom business applications.</span></span> <span data-ttu-id="2163a-118">Web ポータルの一部としてレポートを統合するとき、または Web ブラウザーからレポートを表示するときに、URL アクセスが特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="2163a-118">URL access is particularly useful when integrating reports as part of a Web portal or when viewing reports from a Web browser.</span></span>  
  
 [<span data-ttu-id="2163a-119">Reporting Services の拡張機能</span><span class="sxs-lookup"><span data-stu-id="2163a-119">Reporting Services Extensions</span></span>](extensions/reporting-services-extensions.md)  
 <span data-ttu-id="2163a-120">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のモジュール式アーキテクチャは、拡張性を考慮して設計されています。</span><span class="sxs-lookup"><span data-stu-id="2163a-120">The modular architecture of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] is designed for extensibility.</span></span> <span data-ttu-id="2163a-121">マネージド コード API を使用して、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] の多くのコンポーネントで使用される拡張機能を容易に開発、インストール、および管理できます。</span><span class="sxs-lookup"><span data-stu-id="2163a-121">A managed code API is available so that you can easily develop, install, and manage extensions consumed by many [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] components.</span></span> <span data-ttu-id="2163a-122">を使用してアセンブリを作成 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] し、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 進化するビジネスニーズに合わせて、新しいレンダリング、セキュリティ、配信、およびデータ処理機能を追加することができます。</span><span class="sxs-lookup"><span data-stu-id="2163a-122">You can create assemblies using the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] and add new [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] rendering, security, delivery, and data processing functionality to meet your evolving business needs.</span></span>  
  
 [<span data-ttu-id="2163a-123">カスタム レポート アイテム</span><span class="sxs-lookup"><span data-stu-id="2163a-123">Custom Report Items</span></span>](custom-report-items/custom-report-items.md)  
 <span data-ttu-id="2163a-124">カスタム レポート アイテムを作成して RDL に機能を追加する方法、または既存のコントロールの機能を拡張する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2163a-124">Describes how to create Custom Report Items to add functionality to RDL or extend functionality of existing controls.</span></span>  
  
 [<span data-ttu-id="2163a-125">レポートでのカスタム アセンブリの使用</span><span class="sxs-lookup"><span data-stu-id="2163a-125">Using Custom Assemblies with Reports</span></span>](custom-assemblies/using-custom-assemblies-with-reports.md)  
 <span data-ttu-id="2163a-126">レポート定義内にコード参照を含めることによって、カスタム アセンブリとレポートを併用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2163a-126">Describes how to use custom assemblies with Reports by including code references within the report definition.</span></span>  
  
 [<span data-ttu-id="2163a-127">Reporting Services WMI プロバイダーへのアクセス</span><span class="sxs-lookup"><span data-stu-id="2163a-127">Access the Reporting Services WMI Provider</span></span>](tools/access-the-reporting-services-wmi-provider.md)  
 <span data-ttu-id="2163a-128">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] WMI プロバイダーを使用して、レポート サーバーの配置を管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2163a-128">Describes how to use the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] WMI Provider to manage report server deployments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2163a-129">参照</span><span class="sxs-lookup"><span data-stu-id="2163a-129">See Also</span></span>  
 <span data-ttu-id="2163a-130">[Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md) </span><span class="sxs-lookup"><span data-stu-id="2163a-130">[Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md) </span></span>  
 <span data-ttu-id="2163a-131">[レポート定義言語 &#40;SSRS&#41;](reports/report-definition-language-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2163a-131">[Report Definition Language &#40;SSRS&#41;](reports/report-definition-language-ssrs.md) </span></span>  
 <span data-ttu-id="2163a-132">[SSRS&#41;&#40;テクニカルリファレンス](technical-reference-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2163a-132">[Technical Reference &#40;SSRS&#41;](technical-reference-ssrs.md) </span></span>  
 [<span data-ttu-id="2163a-133">セキュリティで保護された開発 &#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="2163a-133">Secure Development &#40;Reporting Services&#41;</span></span>](extensions/secure-development/secure-development-reporting-services.md)  
  
  
