---
title: レポート サーバー URL の構成 (SSRS 構成マネージャー) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Report Server Windows service, virtual directories
- report servers [Reporting Services], virtual directories
- virtual directories [Reporting Services]
- Report Manager [Reporting Services], virtual directories
ms.assetid: a0134ef0-086c-443e-93b9-7213a3d76393
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e32135ce1affb8e92ce1bdbac4f7fcb6e22326f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632982"
---
# <a name="configure-report-server-urls--ssrs-configuration-manager"></a><span data-ttu-id="1b936-102">レポート サーバー URL の構成 (SSRS 構成マネージャー)</span><span class="sxs-lookup"><span data-stu-id="1b936-102">Configure Report Server URLs  (SSRS Configuration Manager)</span></span>
  <span data-ttu-id="1b936-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では、レポート サーバー Web サービスとレポート マネージャーへのアクセスに URL が使用されます。</span><span class="sxs-lookup"><span data-stu-id="1b936-103">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], URLs are used to access the Report Server Web service and Report Manager.</span></span> <span data-ttu-id="1b936-104">どちらのアプリケーションを使用する場合も、事前に Web サービスとレポート マネージャーそれぞれに 1 つ以上の URL を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b936-104">Before you can use either application, you must configure at least one URL each for the Web service and Report Manager.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="1b936-105">では、両方のアプリケーションの URL に既定値が用意されています。この既定値は、他の Web サービスや Web アプリケーションとのサイド バイ サイドの配置をはじめとするほとんどの配置シナリオに有効です。</span><span class="sxs-lookup"><span data-stu-id="1b936-105">provides default values for both application URLs that work well in most deployment scenarios, including side-by-side deployments with other Web services and applications.</span></span>  
  
-   <span data-ttu-id="1b936-106">既定の構成をインストールした場合は、既定値を使用して自動的に URL が作成されます。</span><span class="sxs-lookup"><span data-stu-id="1b936-106">If you installed the default configuration, URLs were created automatically using the default values.</span></span>  
  
-   <span data-ttu-id="1b936-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールを使用して URL を作成または変更する場合は、URL の既定値をそのまま使用するか、カスタム値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1b936-107">If you are using the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool to create or modify the URLs, you can accept the default values for a URL or specify custom values.</span></span> <span data-ttu-id="1b936-108">URL を定義すると URL のテスト リンクがページに表示されるので、指定した設定が有効な接続であるかどうかを即座に確認できます。</span><span class="sxs-lookup"><span data-stu-id="1b936-108">A test link of the URL appears on page when you define the URL so that you can immediately confirm that the settings you specified result in a valid connection.</span></span> <span data-ttu-id="1b936-109">URL の構成とテストの手順については、「 [URL の構成 &#40;SSRS 構成マネージャー&#41;](configure-a-url-ssrs-configuration-manager.md)へのアクセスに URL が使用されます。</span><span class="sxs-lookup"><span data-stu-id="1b936-109">For step-by-step instructions on how to configure and test a URL, see [Configure a URL  &#40;SSRS Configuration Manager&#41;](configure-a-url-ssrs-configuration-manager.md).</span></span>  
  
## <a name="defining-a-report-server-url"></a><span data-ttu-id="1b936-110">レポート サーバーの URL の定義</span><span class="sxs-lookup"><span data-stu-id="1b936-110">Defining a Report Server URL</span></span>  
 <span data-ttu-id="1b936-111">URL は、ネットワーク上のレポート サーバー アプリケーション インスタンスの場所を厳密に特定します。</span><span class="sxs-lookup"><span data-stu-id="1b936-111">The URL precisely identifies the location of an instance of a report server application on your network.</span></span> <span data-ttu-id="1b936-112">レポート サーバーの URL を作成するときは、次の要素を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b936-112">When you create a report server URL, you must specify the following parts.</span></span>  
  
|<span data-ttu-id="1b936-113">要素</span><span class="sxs-lookup"><span data-stu-id="1b936-113">Part</span></span>|<span data-ttu-id="1b936-114">説明</span><span class="sxs-lookup"><span data-stu-id="1b936-114">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="1b936-115">ホスト名</span><span class="sxs-lookup"><span data-stu-id="1b936-115">Host name</span></span>|<span data-ttu-id="1b936-116">TCP/IP ネットワークでは、IP アドレスを使用してネットワーク上のデバイスを一意に識別します。</span><span class="sxs-lookup"><span data-stu-id="1b936-116">A TCP/IP network uses an IP address to uniquely identify a device on the network.</span></span> <span data-ttu-id="1b936-117">コンピューターにインストールされているネットワーク アダプター カードごとに、物理 IP アドレスが存在します。</span><span class="sxs-lookup"><span data-stu-id="1b936-117">There is a physical IP address for each network adapter card installed in a computer.</span></span> <span data-ttu-id="1b936-118">IP アドレスがホスト ヘッダーに解決される場合、ホスト ヘッダーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="1b936-118">If the IP address resolves to a host header, you can specify the host header.</span></span> <span data-ttu-id="1b936-119">レポート サーバーを企業ネットワークに配置している場合は、コンピューターのネットワーク名を使用できます。</span><span class="sxs-lookup"><span data-stu-id="1b936-119">If you are deploying the report server on a corporate network, you can use the network name of the computer.</span></span>|  
|<span data-ttu-id="1b936-120">Port</span><span class="sxs-lookup"><span data-stu-id="1b936-120">Port</span></span>|<span data-ttu-id="1b936-121">TCP ポートはデバイス上のエンドポイントです。</span><span class="sxs-lookup"><span data-stu-id="1b936-121">A TCP port is an endpoint on the device.</span></span> <span data-ttu-id="1b936-122">レポート サーバーは、指定されたポートで要求をリッスンします。</span><span class="sxs-lookup"><span data-stu-id="1b936-122">The report server will listen for requests on a designated port.</span></span>|  
|<span data-ttu-id="1b936-123">仮想ディレクトリ</span><span class="sxs-lookup"><span data-stu-id="1b936-123">Virtual directory</span></span>|<span data-ttu-id="1b936-124">1 つのポートが複数の Web サービスまたはアプリケーションで共有されていることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="1b936-124">A port is often shared by multiple Web services or applications.</span></span> <span data-ttu-id="1b936-125">このため、レポート サーバーの URL には、要求を受け取るアプリケーションに対応する仮想ディレクトリが必ず含まれています。</span><span class="sxs-lookup"><span data-stu-id="1b936-125">For this reason, a report server URL always includes a virtual directory that corresponds to the application that gets the request.</span></span> <span data-ttu-id="1b936-126">同じ IP アドレスとポートでリッスンする [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アプリケーションごとに、一意の仮想ディレクトリ名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b936-126">You must specify unique virtual directory names for each [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] application that listens on the same IP address and port.</span></span>|  
|<span data-ttu-id="1b936-127">SSL 設定</span><span class="sxs-lookup"><span data-stu-id="1b936-127">SSL settings</span></span>|<span data-ttu-id="1b936-128">コンピューターに以前にインストールした既存の SSL 証明書を使用するように、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の URL を構成できます。</span><span class="sxs-lookup"><span data-stu-id="1b936-128">URLs in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] can be configured to use an existing SSL certificate that you previously installed on the computer.</span></span> <span data-ttu-id="1b936-129">詳細については、 [オンライン ブックの「](../security/configure-ssl-connections-on-a-native-mode-report-server.md) ネイティブ モードのレポート サーバーでの SSL 接続の構成 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b936-129">For more information, see [Configure SSL Connections on a Native Mode Report Server](../security/configure-ssl-connections-on-a-native-mode-report-server.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>|  
  
## <a name="default-urls"></a><span data-ttu-id="1b936-130">既定の URL</span><span class="sxs-lookup"><span data-stu-id="1b936-130">Default URLs</span></span>  
 <span data-ttu-id="1b936-131">レポート サーバーまたはレポート マネージャーに URL を通じてアクセスする場合は、URL に IP アドレスではなくホスト名を指定します。</span><span class="sxs-lookup"><span data-stu-id="1b936-131">When you access a report server or Report Manager through its URL, the URL should include the host name and not the IP address.</span></span> <span data-ttu-id="1b936-132">TCP/IP ネットワークでは、IP アドレスがホスト名 (またはコンピューターのネットワーク名) に解決されます。</span><span class="sxs-lookup"><span data-stu-id="1b936-132">On a TCP/IP network, the IP address will resolve to a host name (or the network name of the computer).</span></span> <span data-ttu-id="1b936-133">既定値を使用して URL を構成した場合は、コンピューター名または localhost をホスト名として指定する URL を使用して、レポート サーバー Web サービスにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1b936-133">If you used the default values to configure URLs, you should be able to access the Report Server Web service using URLs that specify the computer name or localhost as the host name:</span></span>  
  
-   <span data-ttu-id="1b936-134">http:// \<computername> /reportserver</span><span class="sxs-lookup"><span data-stu-id="1b936-134">http://\<computername>/reportserver</span></span>  
  
-   http://localhost/reportserver  
  
 <span data-ttu-id="1b936-135">上記の URL の使用を可能にする設定を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="1b936-135">The settings that make these URLs available appear in the following table.</span></span> <span data-ttu-id="1b936-136">この表の既定値を使用することで、ホスト名を含んだ URL を通じてレポート サーバーに接続できるようになります。</span><span class="sxs-lookup"><span data-stu-id="1b936-136">This table shows the default values that enable a report server connection though URLs that include a host name:</span></span>  
  
|<span data-ttu-id="1b936-137">要素</span><span class="sxs-lookup"><span data-stu-id="1b936-137">Part</span></span>|<span data-ttu-id="1b936-138">値</span><span class="sxs-lookup"><span data-stu-id="1b936-138">Value</span></span>|<span data-ttu-id="1b936-139">説明</span><span class="sxs-lookup"><span data-stu-id="1b936-139">Explanation</span></span>|  
|----------|-----------|-----------------|  
|<span data-ttu-id="1b936-140">IP アドレス</span><span class="sxs-lookup"><span data-stu-id="1b936-140">IP address</span></span>|<span data-ttu-id="1b936-141">すべて割り当て</span><span class="sxs-lookup"><span data-stu-id="1b936-141">All Assigned</span></span>|<span data-ttu-id="1b936-142">ネットワーク上のドメイン ネーム サービスによって、URL のホスト名がコンピューターの IP アドレスに解決されます。</span><span class="sxs-lookup"><span data-stu-id="1b936-142">The domain name service on your network resolves the host name on the URL to the computer's IP address.</span></span> <span data-ttu-id="1b936-143">定義した URL に IP アドレスが指定されていれば、特定のホストに送られる要求は目的の宛先に届きます。</span><span class="sxs-lookup"><span data-stu-id="1b936-143">As long as the IP address is specified in the URL that you define, a request that is sent to a specific host will reach its intended target.</span></span>|  
|<span data-ttu-id="1b936-144">Port</span><span class="sxs-lookup"><span data-stu-id="1b936-144">Port</span></span>|<span data-ttu-id="1b936-145">80</span><span class="sxs-lookup"><span data-stu-id="1b936-145">80</span></span>|<span data-ttu-id="1b936-146">ポート 80 は、コンピューターにおける TCP/IP 接続の既定のポートです。</span><span class="sxs-lookup"><span data-stu-id="1b936-146">Port 80 is the default port for TCP/IP connections on a computer.</span></span> <span data-ttu-id="1b936-147">レポート サーバーはポート 80 でリッスンしているため、URL ではポート番号を省略できます。</span><span class="sxs-lookup"><span data-stu-id="1b936-147">Because the report server is listening on port 80, you can omit the port number from the URL.</span></span> <span data-ttu-id="1b936-148">別のポートを指定する場合は、URL 内でそのポートを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b936-148">If you specify another port, you must specify it in the URL.</span></span>|  
|<span data-ttu-id="1b936-149">仮想ディレクトリ</span><span class="sxs-lookup"><span data-stu-id="1b936-149">Virtual directory</span></span>|<span data-ttu-id="1b936-150">ReportServer</span><span class="sxs-lookup"><span data-stu-id="1b936-150">ReportServer</span></span>|<span data-ttu-id="1b936-151">どちらの URL 例にも仮想ディレクトリ名が含まれていることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="1b936-151">Notice that both of the example URLs includes the virtual directory name.</span></span> <span data-ttu-id="1b936-152">URL 定義をカスタマイズしない限り、アプリケーションの仮想ディレクトリ名を必ず URL 内に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b936-152">Unless you customize the URL definition, you must always specify the application's virtual directory name on the URL.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="1b936-153">基になる URL 予約により、任意の有効なホスト名を URL で使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="1b936-153">An underlying URL reservation enables any valid host name to be used on a URL.</span></span> <span data-ttu-id="1b936-154">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールでは、複数種類のホスト名を特定のレポート サーバー インスタンスに解決できるようにする構文を使用して、HTTP.SYS に URL 予約が作成されます。</span><span class="sxs-lookup"><span data-stu-id="1b936-154">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool creates a URL reservation in HTTP.SYS using syntax that allows variations of the host name to resolve to a particular report server instance.</span></span> <span data-ttu-id="1b936-155">URL 予約の詳細については、「 [URL の予約と登録について &#40;SSRS 構成マネージャー&#41;](about-url-reservations-and-registration-ssrs-configuration-manager.md)へのアクセスに URL が使用されます。</span><span class="sxs-lookup"><span data-stu-id="1b936-155">For more information about URL reservations, see [About URL Reservations and Registration  &#40;SSRS Configuration Manager&#41;](about-url-reservations-and-registration-ssrs-configuration-manager.md).</span></span>  
  
## <a name="server-side-permissions-on-a-report-server-url"></a><span data-ttu-id="1b936-156">レポート サーバーの URL に対するサーバー側の権限</span><span class="sxs-lookup"><span data-stu-id="1b936-156">Server-side Permissions on a Report Server URL</span></span>  
 <span data-ttu-id="1b936-157">各 URL エンドポイントに対する権限は、レポート サーバー サービス アカウントに排他的に付与されます。</span><span class="sxs-lookup"><span data-stu-id="1b936-157">Permissions on each URL endpoint are granted exclusively to the Report Server service account.</span></span> <span data-ttu-id="1b936-158">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の URL に送信された要求を受け付ける権限を持つのはこのアカウントのみです。</span><span class="sxs-lookup"><span data-stu-id="1b936-158">Only this account has rights to accept requests that are directed to the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URLs.</span></span> <span data-ttu-id="1b936-159">セットアップまたは [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールでサービス ID を構成すると、アカウントに対してアクセス制限付きの随意アクセス制御リスト (DACL) が作成され、管理されます。</span><span class="sxs-lookup"><span data-stu-id="1b936-159">Discretionary Access Control Lists (DACLs) are created and maintained for the account when you configure the service identity through Setup or the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool.</span></span> <span data-ttu-id="1b936-160">サービス アカウントを変更した場合は、作成済みの URL 予約が [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールによってすべて更新され、新しいアカウント情報が反映されます。</span><span class="sxs-lookup"><span data-stu-id="1b936-160">If you change the service account, the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool will update all URL reservations that you created to pick up the new account information.</span></span> <span data-ttu-id="1b936-161">詳細については、 [URL 予約構文 &#40;SSRS 構成マネージャー&#41;](url-reservation-syntax-ssrs-configuration-manager.md)へのアクセスに URL が使用されます。</span><span class="sxs-lookup"><span data-stu-id="1b936-161">For more information, see [URL Reservation Syntax  &#40;SSRS Configuration Manager&#41;](url-reservation-syntax-ssrs-configuration-manager.md).</span></span>  
  
## <a name="authenticating-client-requests-sent-to-a-report-server-url"></a><span data-ttu-id="1b936-162">レポート サーバーの URL に送信されたクライアント要求の認証</span><span class="sxs-lookup"><span data-stu-id="1b936-162">Authenticating Client Requests Sent to a Report Server URL</span></span>  
 <span data-ttu-id="1b936-163">URL エンドポイントで既定でサポートされる認証の種類は Windows 認証です。</span><span class="sxs-lookup"><span data-stu-id="1b936-163">By default, the authentication type supported on the URL endpoints is Windows Authentication.</span></span> <span data-ttu-id="1b936-164">これは既定のセキュリティ拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="1b936-164">This is the default security extension.</span></span> <span data-ttu-id="1b936-165">カスタムまたはフォーム認証プロバイダーを実装している場合は、レポート サーバーの認証設定を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b936-165">If you are implementing a custom or Forms authentication provider, you must modify the authentication settings on the report server.</span></span> <span data-ttu-id="1b936-166">必要に応じて、Windows 認証の設定を、ネットワークで使用されている認証サブシステムに合わせて変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="1b936-166">Optionally, you can also change the Windows Authentication settings to match the authentication subsystem used in your network.</span></span> <span data-ttu-id="1b936-167">詳細については、 [オンライン ブックで「](../security/authentication-with-the-report-server.md) レポート サーバーでの認証 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b936-167">For more information, see [Authentication with the Report Server](../security/authentication-with-the-report-server.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1b936-168">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="1b936-168">In This Section</span></span>  
 [<span data-ttu-id="1b936-169">URL の構成 &#40;SSRS 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="1b936-169">Configure a URL  &#40;SSRS Configuration Manager&#41;</span></span>](configure-a-url-ssrs-configuration-manager.md)  
 <span data-ttu-id="1b936-170">このトピックでは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールで URL 予約を設定および変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1b936-170">This topic provides instructions for setting and modifying a URL reservation in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool.</span></span>  
  
 [<span data-ttu-id="1b936-171">URL の予約と登録について &#40;SSRS 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="1b936-171">About URL Reservations and Registration  &#40;SSRS Configuration Manager&#41;</span></span>](about-url-reservations-and-registration-ssrs-configuration-manager.md)  
 <span data-ttu-id="1b936-172">アプリケーションおよびレポートへのアクセスには URL が使用されます。</span><span class="sxs-lookup"><span data-stu-id="1b936-172">URLs are used to access applications and reports.</span></span> <span data-ttu-id="1b936-173">このトピックでは、アプリケーションの URL、既定の URL、および [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]での URL 予約と登録のしくみについて説明します。</span><span class="sxs-lookup"><span data-stu-id="1b936-173">This topic explains the application URLs, the default URLs, and how URL reservations and registration work in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="1b936-174">URL 予約の構文 &#40;SSRS 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="1b936-174">URL Reservation Syntax  &#40;SSRS Configuration Manager&#41;</span></span>](url-reservation-syntax-ssrs-configuration-manager.md)  
 <span data-ttu-id="1b936-175">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] で使用される既定の URL 予約は、ほとんどのシナリオに有効です。</span><span class="sxs-lookup"><span data-stu-id="1b936-175">The default URL reservations that [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] uses are valid for most scenarios.</span></span> <span data-ttu-id="1b936-176">ただし、アクセスを制限する場合や、インターネットまたはエクストラネットにアクセスできるように配置を拡張する場合は、要件に合わせて設定をカスタマイズする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b936-176">However, if you want to restrict access or extend the deployment to enable Internet or extranet access, you might have to customize the settings to fit your requirements.</span></span> <span data-ttu-id="1b936-177">このトピックでは、URL 予約の構文について説明し、各自の配置に合わせてカスタムの予約を作成する場合の推奨事項を示します。</span><span class="sxs-lookup"><span data-stu-id="1b936-177">This topic describes the syntax of a URL reservation and provides recommendations for creating custom reservations for your deployment.</span></span>  
  
 [<span data-ttu-id="1b936-178">構成ファイル内の URL &#40;SSRS 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="1b936-178">URLs in Configuration Files  &#40;SSRS Configuration Manager&#41;</span></span>](urls-in-configuration-files-ssrs-configuration-manager.md)  
 <span data-ttu-id="1b936-179">RSReportServer.config ファイルには、URL 予約の複数のエントリと、レポート マネージャーおよびレポート サーバーの電子メール配信で使用される URL が含まれています。</span><span class="sxs-lookup"><span data-stu-id="1b936-179">The RSReportServer.config file contains multiple entries for URL reservations and the URLs used by Report Manager and report server e-mail delivery.</span></span> <span data-ttu-id="1b936-180">このトピックでは、URL 構成設定の違いを理解できるように、それらの設定について概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="1b936-180">This topic summarizes the URL configuration settings so that you can understand how they compare.</span></span>  
  
 [<span data-ttu-id="1b936-181">レポート サーバーの複数インスタンス配置における URL 予約 &#40;SSRS 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="1b936-181">URL Reservations for Multi-Instance Report Server Deployments  &#40;SSRS Configuration Manager&#41;</span></span>](url-reservations-for-multi-instance-report-server-deployments.md)  
 <span data-ttu-id="1b936-182">1 台のコンピューターに複数の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インスタンスをインストールすると、URL 登録時に URL の重複が発生する可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="1b936-182">When you install multiple instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] on a single computer, you increase the probability of encountering URL duplication when a URL is registered.</span></span> <span data-ttu-id="1b936-183">このエラーを回避するには、このトピックの推奨事項に従ってインスタンス固有の URL 予約を作成します。</span><span class="sxs-lookup"><span data-stu-id="1b936-183">To avoid these errors, follow the recommendations in this topic for creating instance-specific URL reservations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b936-184">参照</span><span class="sxs-lookup"><span data-stu-id="1b936-184">See Also</span></span>  
 <span data-ttu-id="1b936-185">[SSRS Configuration Manager の URL &#40;構成&#41;](configure-a-url-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="1b936-185">[Configure a URL  &#40;SSRS Configuration Manager&#41;](configure-a-url-ssrs-configuration-manager.md) </span></span>  
 [<span data-ttu-id="1b936-186">Web サービス URL &#40;SSRS ネイティブモード&#41;</span><span class="sxs-lookup"><span data-stu-id="1b936-186">Web Service URL &#40;SSRS Native Mode&#41;</span></span>](../../sql-server/install/web-service-url-ssrs-native-mode.md)  
  
  