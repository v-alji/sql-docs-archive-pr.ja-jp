---
title: 高度な複数 Web サイト構成 (SSRS ネイティブモード) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.advancedmultiplewebsiteconfig.F1
ms.assetid: af4ede43-2225-45b5-ae7e-9202411551ba
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 65061eae928227f16b1088a0fb5448b19093cb1d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640501"
---
# <a name="advanced-multiple-web-site-configuration-ssrs-native-mode"></a><span data-ttu-id="a05ad-102">高度な複数 Web サイト構成 (SSRS ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="a05ad-102">Advanced Multiple Web Site Configuration (SSRS Native Mode)</span></span>
  <span data-ttu-id="a05ad-103">このダイアログ ボックスは、レポート サーバーまたはレポート マネージャーへのアクセスに使用される URL を作成し、管理するために使用します。</span><span class="sxs-lookup"><span data-stu-id="a05ad-103">Use this dialog box to create and manage the URLs used to access a report server or Report Manager.</span></span> <span data-ttu-id="a05ad-104">**[高度な複数 Web サイト構成]** ダイアログ ボックスでは、追加の URL、つまりホスト ヘッダー名を含んだカスタム URL を作成することも、IPv4 または IPv6 形式の IP アドレスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="a05ad-104">The **Advanced Multiple Web Site Configuration** dialog box is used to create additional URLs, custom URLs that include a host header name, or specify an IP address in the IPv4 or IPv6 format.</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="a05ad-105">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ネイティブモード。</span><span class="sxs-lookup"><span data-stu-id="a05ad-105">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
 <span data-ttu-id="a05ad-106">レポート サーバーに複数の方法でアクセスできるように構成する場合は、複数の URL を作成すると便利です。</span><span class="sxs-lookup"><span data-stu-id="a05ad-106">Creating multiple URLs is useful if you want to configure different ways to access a report server.</span></span> <span data-ttu-id="a05ad-107">たとえば、イントラネットおよびエクストラネット接続を介してレポート サーバーにアクセスするには、接続の種類ごとに異なる URL を用意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a05ad-107">For example, report server access over intranet and extranet connection typically requires that you have different URLs for each type of connection.</span></span>  
  
 <span data-ttu-id="a05ad-108">**[高度な複数 Web サイト構成]** ダイアログ ボックスを開くには、 **構成マネージャーの** [Web サービス URL] **ページまたは** [レポート マネージャー URL] **ページで** [詳細設定] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a05ad-108">To open the **Advanced Multiple Web Site Configuration** dialog box, click **Advanced** on the **Web Service URL** or the **Report Manager URL** page in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="a05ad-109">**[高度な複数 Web サイト構成]** ダイアログ ボックスが開いたら、 **[追加]** または **[編集]** をクリックして、新しい URL の定義、既存の URL の変更や削除ができます。</span><span class="sxs-lookup"><span data-stu-id="a05ad-109">After the **Advanced Multiple Web Site Configuration** dialog box is open, you can click **Add** or **Edit** to define new URLs or modify or delete existing URLs.</span></span>  
  
 <span data-ttu-id="a05ad-110">**[OK]** をクリックして変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="a05ad-110">Click **OK** to save your changes.</span></span> <span data-ttu-id="a05ad-111">URL を追加または削除した後に、 **[OK]** をクリックせずにダイアログ ボックスを閉じると、変更は失われます。</span><span class="sxs-lookup"><span data-stu-id="a05ad-111">If you add or remove URLs, but then close the dialog box without first clicking **OK**, your changes will be lost.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a05ad-112">Options</span><span class="sxs-lookup"><span data-stu-id="a05ad-112">Options</span></span>  
 <span data-ttu-id="a05ad-113">**IP アドレス**</span><span class="sxs-lookup"><span data-stu-id="a05ad-113">**IP Address**</span></span>  
 <span data-ttu-id="a05ad-114">TCP/IP ネットワーク上でレポート サーバー コンピューターを識別します。</span><span class="sxs-lookup"><span data-stu-id="a05ad-114">Identifies the report server computer on a TCP/IP network.</span></span> <span data-ttu-id="a05ad-115">有効な値は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a05ad-115">Valid values include:</span></span>  
  
-   <span data-ttu-id="a05ad-116">**[すべて割り当て]** は、レポート サーバー アプリケーションを指す URL に、コンピューターに割り当てられている IP アドレスをどれでも使用できることを示します。</span><span class="sxs-lookup"><span data-stu-id="a05ad-116">**All Assigned** specifies that any of the IP addresses that are assigned to the computer can be used in a URL that points to a report server application.</span></span> <span data-ttu-id="a05ad-117">コンピューターに割り当てられている IP アドレスに対してドメイン ネーム サーバーによって解決されるわかりやすいホスト名 (コンピューター名など) も、この値の対象に含まれます。</span><span class="sxs-lookup"><span data-stu-id="a05ad-117">This value also encompasses friendly host names (such as computer names) that can be resolved by a domain name server to an IP address that is assigned to the computer.</span></span> <span data-ttu-id="a05ad-118">これは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URL の既定値です。</span><span class="sxs-lookup"><span data-stu-id="a05ad-118">This is the default value for a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URL.</span></span>  
  
-   <span data-ttu-id="a05ad-119">**[すべて未割り当て]** は、IP アドレスまたはホスト名が正確に一致しない要求をレポート サーバーがすべて受け入れることを示します。</span><span class="sxs-lookup"><span data-stu-id="a05ad-119">**All Unassigned** specifies that the report server will accept any request that does not have an exact match for the IP address or host name.</span></span> <span data-ttu-id="a05ad-120">別の Web アプリケーションが既に使用している場合は、この値を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="a05ad-120">Do not use this value if another Web application is already using it.</span></span> <span data-ttu-id="a05ad-121">使用すると、他のアプリケーションのサービスが中断されます。</span><span class="sxs-lookup"><span data-stu-id="a05ad-121">If you do so, you will disrupt service for the other application.</span></span>  
  
-   <span data-ttu-id="a05ad-122">**[127.0.0.1]** は、localhost にアクセスする場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="a05ad-122">**127.0.0.1** is used to access to localhost.</span></span> <span data-ttu-id="a05ad-123">この値は、レポート サーバー コンピューターでのローカル管理をサポートします。</span><span class="sxs-lookup"><span data-stu-id="a05ad-123">It supports local administration on the report server computer.</span></span> <span data-ttu-id="a05ad-124">この値のみを選択すると、レポート サーバー コンピューターにローカルにログオンしているユーザーだけがアプリケーションにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="a05ad-124">If you select only this value, only users who are logged on locally to the report server computer will have access the application.</span></span>  
  
-   <span data-ttu-id="a05ad-125">"*nnn.nnn.nnn.nnn* " は、コンピューターのネットワーク アダプター カードの IPv4 アドレスです。</span><span class="sxs-lookup"><span data-stu-id="a05ad-125">*Nnn.nnn.nnn.nnn* is the IPv4 address of a network adapter card on your computer.</span></span> <span data-ttu-id="a05ad-126">ネットワークで IPv6 アドレス指定を使用している場合、IP アドレスは、次の形式の 8 4 バイトのフィールドの128ビット値になります: \<header> :*nnnn: nnnn: nnnn: nnnn*。</span><span class="sxs-lookup"><span data-stu-id="a05ad-126">If your network uses IPv6 addressing, the IP address will be a 128-bit value of 8 4-byte fields similar to the following format: \<header>:*nnnn:nnnn:nnnn:nnnn*.</span></span>  
  
     <span data-ttu-id="a05ad-127">複数のカードがある場合は、それぞれに IP アドレスが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="a05ad-127">If you have multiple cards, you will see an IP address for each one.</span></span> <span data-ttu-id="a05ad-128">この値のみを選択すると、アプリケーション アクセスがその IP アドレス (およびドメイン ネーム サーバーによってそのアドレスにマップされるホスト名) に限定されます。</span><span class="sxs-lookup"><span data-stu-id="a05ad-128">If you select only this value, it will limit application access to the just the IP address (and any host name that a domain name server maps to that address).</span></span> <span data-ttu-id="a05ad-129">localhost を使用してレポート サーバーにアクセスすることはできません。また、レポート サーバー コンピューターにインストールされている他のネットワーク アダプター カードの IP アドレスは使用できません。</span><span class="sxs-lookup"><span data-stu-id="a05ad-129">You cannot use localhost to access a report server, and you cannot use the IP addresses of other network adapter cards that are installed on the report server computer.</span></span>  
  
 <span data-ttu-id="a05ad-130">**[ポート]**</span><span class="sxs-lookup"><span data-stu-id="a05ad-130">**Port**</span></span>  
 <span data-ttu-id="a05ad-131">レポート サーバーが要求を監視するポートを指定します。</span><span class="sxs-lookup"><span data-stu-id="a05ad-131">Specifies the port that report server monitors for requests.</span></span> <span data-ttu-id="a05ad-132">既定のポートは、ポート 80 です。</span><span class="sxs-lookup"><span data-stu-id="a05ad-132">Port 80 is the default port.</span></span> <span data-ttu-id="a05ad-133">ポート 80 を使用する場合は、URL にポートを含める必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a05ad-133">If you use port 80, you do not have to include it in the URL.</span></span> <span data-ttu-id="a05ad-134">その他のポート番号を使用する場合は、URL に必ず含める必要があります (たとえば、 http://localhost:8181/reports)</span><span class="sxs-lookup"><span data-stu-id="a05ad-134">If you use any other port number, you must always include it in the URL (for example, http://localhost:8181/reports).</span></span>  
  
 <span data-ttu-id="a05ad-135">**ホスト ヘッダー**</span><span class="sxs-lookup"><span data-stu-id="a05ad-135">**Host Header**</span></span>  
 <span data-ttu-id="a05ad-136">コンピューターに解決されるホスト ヘッダーをドメイン ネーム サーバーに既に定義している場合は、レポート サーバー アクセス用に構成する URL にそのホスト ヘッダーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a05ad-136">If you already have a host header defined on a domain name server that resolves to your computer, you can specify that host header in a URL that you configure for report server access.</span></span>  
  
 <span data-ttu-id="a05ad-137">ホスト ヘッダーは一意の名前であり、これを使用して複数の Web サイトで単一の IP アドレスとポートを共有できます。</span><span class="sxs-lookup"><span data-stu-id="a05ad-137">A host header is a unique name that allows multiple Web sites to share a single IP address and port.</span></span> <span data-ttu-id="a05ad-138">ホスト ヘッダー名は、IP アドレスとポート番号に比べて容易に記憶でき、入力も簡単です。</span><span class="sxs-lookup"><span data-stu-id="a05ad-138">Host header names are easier to remember and type than IP address and port numbers.</span></span> <span data-ttu-id="a05ad-139">たとえば、 www.adventure-works.com などはホスト ヘッダー名の一例です。</span><span class="sxs-lookup"><span data-stu-id="a05ad-139">An example of a host header name might be www.adventure-works.com.</span></span>  
  
 <span data-ttu-id="a05ad-140">**[SSL ポート]**</span><span class="sxs-lookup"><span data-stu-id="a05ad-140">**SSL Port**</span></span>  
 <span data-ttu-id="a05ad-141">SSL 接続のポートを指定します。</span><span class="sxs-lookup"><span data-stu-id="a05ad-141">Specifies the port for SSL connections.</span></span> <span data-ttu-id="a05ad-142">SSL の既定のポートは 443 です。</span><span class="sxs-lookup"><span data-stu-id="a05ad-142">The default port for SSL is 443.</span></span>  
  
 <span data-ttu-id="a05ad-143">**[SSL 証明書]**</span><span class="sxs-lookup"><span data-stu-id="a05ad-143">**SSL Certificate**</span></span>  
 <span data-ttu-id="a05ad-144">対象のコンピューターにインストールした SSL 証明書の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="a05ad-144">Specifies the certificate name of an SSL certificate that you installed on this computer.</span></span> <span data-ttu-id="a05ad-145">証明書がワイルドカードにマップされている場合は、それをレポート サーバーの接続に使用できます。</span><span class="sxs-lookup"><span data-stu-id="a05ad-145">If the certificate maps to a wildcard, you can use it for a report server connection.</span></span>  
  
 <span data-ttu-id="a05ad-146">証明書が登録されている完全修飾コンピューター名を指定します。</span><span class="sxs-lookup"><span data-stu-id="a05ad-146">Specifies the fully qualified computer name for which the certificate is registered.</span></span> <span data-ttu-id="a05ad-147">証明書が登録されている名前と同じ名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a05ad-147">The name that you specify must be identical to the name for which the certificate is registered.</span></span>  
  
 <span data-ttu-id="a05ad-148">このオプションを使用するには、証明書がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a05ad-148">You must have a certificate installed to use this option.</span></span> <span data-ttu-id="a05ad-149">また、RSReportServer.config ファイルの UrlRoot 構成設定を、証明書で登録されたコンピューターの完全修飾名を指すように変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a05ad-149">You must also modify the UrlRoot configuration setting in the RSReportServer.config file so that it specifies the fully qualified name of the computer for which the certificate is registered.</span></span> <span data-ttu-id="a05ad-150">詳細については、 [オンライン ブックの「](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md) ネイティブ モードのレポート サーバーでの SSL 接続の構成 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a05ad-150">For more information, see [Configure SSL Connections on a Native Mode Report Server](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="a05ad-151">**発行先**</span><span class="sxs-lookup"><span data-stu-id="a05ad-151">**Issued To**</span></span>  
 <span data-ttu-id="a05ad-152">証明書が作成されたコンピューターの名前を示します。</span><span class="sxs-lookup"><span data-stu-id="a05ad-152">Shows the name of the computer for which the certificate was created.</span></span>  
  
 <span data-ttu-id="a05ad-153">**[追加]**</span><span class="sxs-lookup"><span data-stu-id="a05ad-153">**Add**</span></span>  
 <span data-ttu-id="a05ad-154">追加の URL を定義します。</span><span class="sxs-lookup"><span data-stu-id="a05ad-154">Define an additional URL.</span></span>  
  
 <span data-ttu-id="a05ad-155">**[編集]**</span><span class="sxs-lookup"><span data-stu-id="a05ad-155">**Edit**</span></span>  
 <span data-ttu-id="a05ad-156">URL 構文の一部を変更します。</span><span class="sxs-lookup"><span data-stu-id="a05ad-156">Modify any part of the URL syntax.</span></span>  
  
 <span data-ttu-id="a05ad-157">**削除**</span><span class="sxs-lookup"><span data-stu-id="a05ad-157">**Remove**</span></span>  
 <span data-ttu-id="a05ad-158">一覧から URL エントリを削除します。</span><span class="sxs-lookup"><span data-stu-id="a05ad-158">Clear a URL entry from the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a05ad-159">参照</span><span class="sxs-lookup"><span data-stu-id="a05ad-159">See Also</span></span>  
 <span data-ttu-id="a05ad-160">[Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="a05ad-160">[Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md) </span></span>  
 <span data-ttu-id="a05ad-161">[SSRS Configuration Manager の URL &#40;構成&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="a05ad-161">[Configure a URL  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) </span></span>  
 [<span data-ttu-id="a05ad-162">レポート サーバー URL の構成 &#40;SSRS 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="a05ad-162">Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;</span></span>](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
  
  
