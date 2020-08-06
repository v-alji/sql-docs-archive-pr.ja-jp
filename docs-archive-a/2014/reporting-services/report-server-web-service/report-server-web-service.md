---
title: レポート サーバー Web サービス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SSIS, Web service
- Web service [Reporting Services]
- Reporting Services, extending
- SQL Server Reporting Services, Web service
- Reporting Services, Web service
- XML Web service [Reporting Services]
- Report Server Web service
ms.assetid: 16c21dec-6b46-4497-9a0c-1b0f2b6ab8fc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8bb43a0fa52a243bd250f70fac16e18d949f8197
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640606"
---
# <a name="report-server-web-service"></a><span data-ttu-id="b6d7b-102">レポート サーバー Web サービス</span><span class="sxs-lookup"><span data-stu-id="b6d7b-102">Report Server Web Service</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="b6d7b-103">レポートサーバー [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Web サービスを使用して、レポートサーバーのすべての機能にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="b6d7b-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] provides access to the full functionality of the report server through the Report Server Web service.</span></span> <span data-ttu-id="b6d7b-104">レポート サーバー Web サービスは、SOAP API を使用した XML Web サービスです。</span><span class="sxs-lookup"><span data-stu-id="b6d7b-104">The Report Server Web service is an XML Web service with a SOAP API.</span></span> <span data-ttu-id="b6d7b-105">SOAP over HTTP を使用し、クライアント プログラムとレポート サーバー間の通信インターフェイスとして機能します。</span><span class="sxs-lookup"><span data-stu-id="b6d7b-105">It uses SOAP over HTTP and acts as a communications interface between client programs and the report server.</span></span> <span data-ttu-id="b6d7b-106">Web サービスは 2 つのエンドポイントを提供します。1 つはレポートを実行するためのもので、もう 1 つはレポートを管理するためのものです。加えて、レポート サーバーの機能を公開するメソッドが用意されています。このメソッドにより、レポートのライフ サイクルの任意の時点に対するカスタム ツールを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b6d7b-106">The Web service provides two endpoints - one for report execution and one for report management - with methods that expose the functionality of the report server and enable you to create custom tools for any part of the report life cycle.</span></span>  
  
 <span data-ttu-id="b6d7b-107">Web サービスに基づいた [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アプリケーションを開発する主な方法は 3 種類あります。</span><span class="sxs-lookup"><span data-stu-id="b6d7b-107">There are three primary ways to develop [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] applications based on the Web service.</span></span> <span data-ttu-id="b6d7b-108">次のようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="b6d7b-108">You can:</span></span>  
  
-   <span data-ttu-id="b6d7b-109">および SDK を使用してアプリケーションを開発し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="b6d7b-109">Develop applications using [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.</span></span> <span data-ttu-id="b6d7b-110">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] の使用方法の詳細については、「[Web サービスと、.NET Framework を使用してのアプリケーションの構築](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6d7b-110">For more information about using the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] to build Web service applications, see [Building Applications Using the Web Service and the .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md).</span></span>  
  
-   <span data-ttu-id="b6d7b-111">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のスクリプト環境である、**rs** ユーティリティ (RS.exe) を使用してアプリケーションを開発する。</span><span class="sxs-lookup"><span data-stu-id="b6d7b-111">Develop applications using the **rs** utility (RS.exe), the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] script environment.</span></span> <span data-ttu-id="b6d7b-112">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] と [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] スクリプトを使用すると、レポート サーバー Web サービスのあらゆる操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="b6d7b-112">With [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] scripts, you can run any of the Report Server Web service operations.</span></span> <span data-ttu-id="b6d7b-113">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]のスクリプトの詳細については、「[rs.exe ユーティリティと Web サービスを使用したスクリプト](../tools/script-with-the-rs-exe-utility-and-the-web-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6d7b-113">For more information about scripting in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], see [Script with the rs.exe Utility and the Web Service](../tools/script-with-the-rs-exe-utility-and-the-web-service.md).</span></span>  
  
-   <span data-ttu-id="b6d7b-114">SOAP 対応の開発ツールを使用してアプリケーションを開発する。</span><span class="sxs-lookup"><span data-stu-id="b6d7b-114">Develop applications using any SOAP-enabled set of development tools.</span></span> <span data-ttu-id="b6d7b-115">詳細については、「[Reporting Services における SOAP の役割](../report-server-web-service/the-role-of-soap-in-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6d7b-115">For more information, see [The Role of SOAP in Reporting Services](../report-server-web-service/the-role-of-soap-in-reporting-services.md).</span></span>  
  
## <a name="programming-diagram"></a><span data-ttu-id="b6d7b-116">プログラミング図</span><span class="sxs-lookup"><span data-stu-id="b6d7b-116">Programming Diagram</span></span>  
 <span data-ttu-id="b6d7b-117">![レポート サーバー Web サービスの配置オプション](../../../2014/reporting-services/media/reportserviceswebserviceprog-01.gif "レポート サーバー Web サービスの配置オプション")</span><span class="sxs-lookup"><span data-stu-id="b6d7b-117">![Report Server Web service development options](../../../2014/reporting-services/media/reportserviceswebserviceprog-01.gif "Report Server Web service development options")</span></span>  
<span data-ttu-id="b6d7b-118">Reporting Services で利用可能な Web サービス開発オプション</span><span class="sxs-lookup"><span data-stu-id="b6d7b-118">Reporting Services available Web service development options</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b6d7b-119">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b6d7b-119">In This Section</span></span>  
 [<span data-ttu-id="b6d7b-120">レポート サーバー Web サービス メソッド</span><span class="sxs-lookup"><span data-stu-id="b6d7b-120">Report Server Web Service Methods</span></span>](../report-server-web-service/methods/report-server-web-service-methods.md)  
 <span data-ttu-id="b6d7b-121">各レポート サーバー Web サービスの機能とメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b6d7b-121">Describes the features and methods of each Report Server Web service.</span></span>  
  
 [<span data-ttu-id="b6d7b-122">Reporting Services における SOAP の役割</span><span class="sxs-lookup"><span data-stu-id="b6d7b-122">The Role of SOAP in Reporting Services</span></span>](../report-server-web-service/the-role-of-soap-in-reporting-services.md)  
 <span data-ttu-id="b6d7b-123">SOAP の概要およびレポート サーバー Web サービスでの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b6d7b-123">Provides an overview of SOAP and how it is used in the Report Server Web services.</span></span>  
  
 [<span data-ttu-id="b6d7b-124">SOAP API へのアクセス</span><span class="sxs-lookup"><span data-stu-id="b6d7b-124">Accessing the SOAP API</span></span>](../report-server-web-service/accessing-the-soap-api.md)  
 <span data-ttu-id="b6d7b-125">Web サービス記述言語 (WSDL) について説明し、Reporting Services WSDL ファイルにアクセスするための URL を記載します。</span><span class="sxs-lookup"><span data-stu-id="b6d7b-125">Describes the Web Service Description Language (WSDL) and provides URLs for accessing a Reporting Services WSDL file.</span></span>  
  
 [<span data-ttu-id="b6d7b-126">Web サービスと .NET Framework を使用してのアプリケーションの構築</span><span class="sxs-lookup"><span data-stu-id="b6d7b-126">Building Applications Using the Web Service and the .NET Framework</span></span>](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
 <span data-ttu-id="b6d7b-127">Reporting Services SOAP API を呼び出すアプリケーションと Web サービスの開発について説明します。</span><span class="sxs-lookup"><span data-stu-id="b6d7b-127">Contains information about developing applications and Web services that call the Reporting Services SOAP API.</span></span>  
  
 [<span data-ttu-id="b6d7b-128">rs.exe ユーティリティと Web サービスを使用したスクリプト</span><span class="sxs-lookup"><span data-stu-id="b6d7b-128">Script with the rs.exe Utility and the Web Service</span></span>](../tools/script-with-the-rs-exe-utility-and-the-web-service.md)  
 <span data-ttu-id="b6d7b-129">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] スクリプト環境の概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="b6d7b-129">Provides an overview of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] scripting environment.</span></span>  
  
 [<span data-ttu-id="b6d7b-130">テクニカル リファレンス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="b6d7b-130">Technical Reference &#40;SSRS&#41;</span></span>](../../../2014/reporting-services/technical-reference-ssrs.md)  
 <span data-ttu-id="b6d7b-131">レポート サーバー Web サービスのメソッドおよび対応する複合型のリファレンス情報です。</span><span class="sxs-lookup"><span data-stu-id="b6d7b-131">Contains reference material specific to Report Server Web services methods and corresponding complex types.</span></span>  
  
## <a name="user-requirements-for-web-service-development"></a><span data-ttu-id="b6d7b-132">Web サービスを開発するためのユーザーの必要条件</span><span class="sxs-lookup"><span data-stu-id="b6d7b-132">User Requirements for Web Service Development</span></span>  
 <span data-ttu-id="b6d7b-133">レポート サーバー Web サービスを使用してアプリケーションを開発するには、次の必要条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6d7b-133">To develop applications using the Report Server Web service, you need:</span></span>  
  
-   <span data-ttu-id="b6d7b-134">レポート サーバーへのインターネット接続とアクセスが可能なコンピューターに [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer 5.5 以降がインストールされていること。</span><span class="sxs-lookup"><span data-stu-id="b6d7b-134">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer 5.5 or later installed on a computer with an Internet connection to and access to the report server.</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="b6d7b-135">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]また [!INCLUDE[msCoName](../../includes/msconame-md.md)] は [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]を使用してアプリケーションを開発および配置する場合は、コンピューターに SDK をインストールし [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="b6d7b-135">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK installed on a computer if you want to develop and deploy [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] applications using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].</span></span>  
  
-   <span data-ttu-id="b6d7b-136">機能の詳細について説明し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="b6d7b-136">An in-depth understanding of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features and capabilities.</span></span>  
  
-   <span data-ttu-id="b6d7b-137">SOAP および [!INCLUDE[vstecwebservices](../../includes/vstecwebservices-md.md)]に関する十分な知識があること。</span><span class="sxs-lookup"><span data-stu-id="b6d7b-137">A firm understanding of SOAP and [!INCLUDE[vstecwebservices](../../includes/vstecwebservices-md.md)].</span></span>  
  
-   <span data-ttu-id="b6d7b-138">を [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 開発プラットフォームとして使用する予定の場合、やなどの互換性のある言語での開発エクスペリエンス [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b6d7b-138">Development experience in a [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-compatible language such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] or [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], if you plan to use the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] as your development platform.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6d7b-139">参照</span><span class="sxs-lookup"><span data-stu-id="b6d7b-139">See Also</span></span>  
 [<span data-ttu-id="b6d7b-140">レポート サーバー web サービス</span><span class="sxs-lookup"><span data-stu-id="b6d7b-140">Report Server Web Service</span></span>](../report-server-web-service/report-server-web-service.md)  
  
  
