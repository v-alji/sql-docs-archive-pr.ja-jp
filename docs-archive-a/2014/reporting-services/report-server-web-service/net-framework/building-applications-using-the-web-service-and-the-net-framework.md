---
title: Web サービスと .NET Framework を使用してのアプリケーションの構築 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, application building
- .NET Framework [Reporting Services]
- XML Web service [Reporting Services], client creation
- reports [Reporting Services], building
- Web service [Reporting Services], application building
- Report Server Web service, client creation
- client configuration [Reporting Services]
- XML Web service [Reporting Services], application building
- Web service [Reporting Services], client creation
ms.assetid: 92a9678c-bc4f-4d7a-ba44-85989bfe27ca
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5f14a0f2d231d54d12129852b6226c02afd211d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713821"
---
# <a name="building-applications-using-the-web-service-and-the-net-framework"></a><span data-ttu-id="d1def-102">Web サービスと .NET Framework を使用したアプリケーションの構築</span><span class="sxs-lookup"><span data-stu-id="d1def-102">Building Applications Using the Web Service and the .NET Framework</span></span>
  <span data-ttu-id="d1def-103">では、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] メソッド、プリミティブ型、ユーザー定義の複合型などの使い慣れたプログラミング構成要素を使用して、Web サービスを操作できます。</span><span class="sxs-lookup"><span data-stu-id="d1def-103">With the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], you can use familiar programming constructs, such as methods, primitive types, and user-defined complex types to work with Web services.</span></span> <span data-ttu-id="d1def-104">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] により、W3C (World Wide Web Consortium) の標準に準拠した任意の Web サービスを呼び出すことができる、Web サービス クライアントを作成するためのインフラストラクチャとツールが提供されます。</span><span class="sxs-lookup"><span data-stu-id="d1def-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] contains an infrastructure and tools you can use to create Web service clients that can call any World Wide Web Consortium (W3C) standards-compliant Web service.</span></span>  
  
 <span data-ttu-id="d1def-105">レポート サーバー Web サービス クライアントとは、Simple Object Access Protocol (SOAP) メッセージを使用して、レポート サーバーと通信をする任意のコンポーネントまたはアプリケーションのことです。</span><span class="sxs-lookup"><span data-stu-id="d1def-105">A Report Server Web service client is any component or application that communicates with a report server using Simple Object Access Protocol (SOAP) messages.</span></span>  
  
 <span data-ttu-id="d1def-106">**.NET Framework を使用してレポート サーバー Web サービス クライアントを作成するには、以下の基本手順に従います。**</span><span class="sxs-lookup"><span data-stu-id="d1def-106">**To create a Report Server Web service client using the .NET Framework, follow these basic steps:**</span></span>  
  
1.  <span data-ttu-id="d1def-107">Web サービスのプロキシ クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="d1def-107">Create a proxy class for the Web service.</span></span>  
  
     <span data-ttu-id="d1def-108">そのためには、プロキシ クラスまたは Web 参照を開発プロジェクトに追加し、クライアント コードでそのプロキシ クラスを参照します。次に、そのプロキシのインスタンスを生成します。</span><span class="sxs-lookup"><span data-stu-id="d1def-108">To do this, add a proxy class or Web reference to your development project, reference the proxy class in your client code, and create an instance of that proxy.</span></span> <span data-ttu-id="d1def-109">詳細については、「[Web サービス プロキシの作成](creating-the-web-service-proxy.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1def-109">For more information, see [Creating the Web Service Proxy](creating-the-web-service-proxy.md).</span></span>  
  
2.  <span data-ttu-id="d1def-110">レポート サーバーで Web サービス クライアントを認証します。</span><span class="sxs-lookup"><span data-stu-id="d1def-110">Authenticate the Web service client with the report server.</span></span>  
  
     <span data-ttu-id="d1def-111">そのためには、サービス オブジェクトの <xref:System.Web.Services.Protocols.WebClientProtocol.Credentials%2A> プロパティを、レポート サーバーで認証されるユーザーの資格情報と同じに設定します。</span><span class="sxs-lookup"><span data-stu-id="d1def-111">To do this, set the service object's <xref:System.Web.Services.Protocols.WebClientProtocol.Credentials%2A> property equal to the credentials of an authenticated user on the report server.</span></span> <span data-ttu-id="d1def-112">詳細については、「[Web サービス認証](web-service-authentication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1def-112">For more information, see [Web Service Authentication](web-service-authentication.md).</span></span>  
  
3.  <span data-ttu-id="d1def-113">呼び出す Web サービス操作に対応したプロキシ クラスのメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d1def-113">Call the method of the proxy class corresponding to the Web service operation that you want to invoke.</span></span>  
  
     <span data-ttu-id="d1def-114">そのためには、Web サービス メソッドを呼び出し、必要な引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="d1def-114">To do this, call a Web service method and supply the necessary arguments.</span></span> <span data-ttu-id="d1def-115">Web サービス メソッドの詳細については、「[レポート サーバー Web サービス メソッド](../methods/report-server-web-service-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1def-115">For more information about the Web service methods, see [Report Server Web Service Methods](../methods/report-server-web-service-methods.md).</span></span> <span data-ttu-id="d1def-116">呼び出しの詳細については、「[Web サービス メソッドの呼び出し](calling-web-service-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1def-116">For more information about calling, see [Calling Web Service Methods](calling-web-service-methods.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d1def-117">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d1def-117">In This Section</span></span>  
  
|<span data-ttu-id="d1def-118">トピック</span><span class="sxs-lookup"><span data-stu-id="d1def-118">Topic</span></span>|<span data-ttu-id="d1def-119">説明</span><span class="sxs-lookup"><span data-stu-id="d1def-119">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="d1def-120">Web サービス プロキシの作成</span><span class="sxs-lookup"><span data-stu-id="d1def-120">Creating the Web Service Proxy</span></span>](creating-the-web-service-proxy.md)|<span data-ttu-id="d1def-121">を使用してプロジェクトにプロキシクラスを追加する方法について説明し [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="d1def-121">Describes the ways to add a proxy class to your project using [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>|  
|[<span data-ttu-id="d1def-122">Web サービス認証</span><span class="sxs-lookup"><span data-stu-id="d1def-122">Web Service Authentication</span></span>](web-service-authentication.md)|<span data-ttu-id="d1def-123">レポート サーバー Web サービスに対する呼び出しの認証方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1def-123">Describes how calls to the Report Server Web service are authenticated.</span></span>|  
|[<span data-ttu-id="d1def-124">Web サービス メソッドの呼び出し</span><span class="sxs-lookup"><span data-stu-id="d1def-124">Calling Web Service Methods</span></span>](calling-web-service-methods.md)|<span data-ttu-id="d1def-125">SOAP API を使用して、の Web サービスメソッドを呼び出す方法について説明し [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="d1def-125">Describes how to use the SOAP API to call Web service methods in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span>|  
|[<span data-ttu-id="d1def-126">Web サービスの Url プロパティの設定</span><span class="sxs-lookup"><span data-stu-id="d1def-126">Setting the Url Property of the Web Service</span></span>](setting-the-url-property-of-the-web-service.md)|<span data-ttu-id="d1def-127">Web 参照の作成後に新しいサーバーの URL を Web サービス プロキシに知らせるためのプログラミング方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1def-127">Explains how to programmatically direct your Web service proxy to a new server URL after you have created your Web reference.</span></span>|  
|[<span data-ttu-id="d1def-128">Web サービス メソッドの引数の指定</span><span class="sxs-lookup"><span data-stu-id="d1def-128">Supplying Web Service Method Arguments</span></span>](supplying-web-service-method-arguments.md)|<span data-ttu-id="d1def-129">Web サービス メソッドを呼び出す方法およびメソッドの引数の指定方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="d1def-129">Describes how to invoke a Web service method and supply method arguments.</span></span>|  
|[<span data-ttu-id="d1def-130">オプションの Web サービス オブジェクトの値の省略</span><span class="sxs-lookup"><span data-stu-id="d1def-130">Omitting Values for Optional Web Service Objects</span></span>](omitting-values-for-optional-web-service-objects.md)|<span data-ttu-id="d1def-131">省略可能な Web サービス オブジェクトの値の省略方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="d1def-131">Describes how to omit values for optional Web service objects.</span></span>|  
|[<span data-ttu-id="d1def-132">セキュリティで保護された Web サービス メソッドの使用</span><span class="sxs-lookup"><span data-stu-id="d1def-132">Using Secure Web Service Methods</span></span>](using-secure-web-service-methods.md)|<span data-ttu-id="d1def-133">**SecureConnectionLevel** の設定、およびそれが Reporting Services SOAP API の使用にどのように影響するのかを説明します。</span><span class="sxs-lookup"><span data-stu-id="d1def-133">Describes the **SecureConnectionLevel** setting and the way in which it affects the use of the Reporting Services SOAP API.</span></span>|  
|[<span data-ttu-id="d1def-134">表示拡張機能にデバイス情報設定を渡す</span><span class="sxs-lookup"><span data-stu-id="d1def-134">Passing Device Information Settings to Rendering Extensions</span></span>](passing-device-information-settings-to-rendering-extensions.md)|<span data-ttu-id="d1def-135">異なる形式でレポートを表示するための、デバイス情報の設定について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1def-135">Describes the device information settings that are used to render reports to different formats.</span></span>|  
|[<span data-ttu-id="d1def-136">Reporting Services 配信拡張機能の設定</span><span class="sxs-lookup"><span data-stu-id="d1def-136">Reporting Services Delivery Extension Settings</span></span>](reporting-services-delivery-extension-settings.md)|<span data-ttu-id="d1def-137">レポート サーバーの電子メールを使用してレポートを配信するための設定について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1def-137">Describes the settings that are used to deliver reports using report server e-mail.</span></span>|  
|[<span data-ttu-id="d1def-138">Reporting Services の SOAP ヘッダーの使用</span><span class="sxs-lookup"><span data-stu-id="d1def-138">Using Reporting Services SOAP Headers</span></span>](../../report-server-web-service-net-framework-soap-headers/using-reporting-services-soap-headers.md)|<span data-ttu-id="d1def-139">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] の SOAP ヘッダーの使用について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1def-139">Explains the use of SOAP headers in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="d1def-140">Reporting Services における例外処理の概要</span><span class="sxs-lookup"><span data-stu-id="d1def-140">Introducing Exception Handling in Reporting Services</span></span>](../../report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)|<span data-ttu-id="d1def-141">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のエラー処理方法に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="d1def-141">Provides information about the way in which [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] handles errors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1def-142">参照</span><span class="sxs-lookup"><span data-stu-id="d1def-142">See Also</span></span>  
 <span data-ttu-id="d1def-143">[レポート サーバー Web サービス](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="d1def-143">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 [<span data-ttu-id="d1def-144">テクニカル リファレンス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="d1def-144">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
