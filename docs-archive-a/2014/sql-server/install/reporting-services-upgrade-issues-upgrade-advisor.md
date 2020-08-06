---
title: Reporting Services のアップグレードに関する問題 (アップグレードアドバイザー) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Report Manager [Reporting Services], upgrade issues
- Reporting Services, upgrades
- upgrading Reporting Services
- report servers [Reporting Services], upgrade issues
ms.assetid: d9663f25-98d7-4508-ae3c-55a7277211bd
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 569afe735d68a724c0b4cc61ad2b7767088c2b30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645355"
---
# <a name="reporting-services-upgrade-issues-upgrade-advisor"></a><span data-ttu-id="a2f08-102">Reporting Services のアップグレードに関するその他の問題 (アップグレード アドバイザー)</span><span class="sxs-lookup"><span data-stu-id="a2f08-102">Reporting Services Upgrade Issues (Upgrade Advisor)</span></span>
  <span data-ttu-id="a2f08-103">次のトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] へのアップグレードに影響する可能性がある問題について説明し [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="a2f08-103">The following topics describe the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] issues that might affect your upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="a2f08-104">これらのトピックでは、これらの変更が環境に与える影響を軽減するために実行できる操作について説明します。</span><span class="sxs-lookup"><span data-stu-id="a2f08-104">The topics describe actions that you can take to mitigate the effect of these changes on your environment.</span></span>  
  
 <span data-ttu-id="a2f08-105">アップグレード アドバイザーによって、現在インストールされているレポート サーバーが分析されます。</span><span class="sxs-lookup"><span data-stu-id="a2f08-105">Upgrade Advisor analyzes a report server installation.</span></span> <span data-ttu-id="a2f08-106">コンピューターにインストールされている [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コンポーネントがレポート デザイナーのみであるなど、クライアント コンポーネントのみがインストールされている場合は、問題は報告されません。</span><span class="sxs-lookup"><span data-stu-id="a2f08-106">If only client components are installed (for example, if Report Designer is the only [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] component installed on the computer), no issues will be reported.</span></span>  
  
 <span data-ttu-id="a2f08-107">インストールの構成によっては、アップグレード アドバイザーでは報告されない問題が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="a2f08-107">Depending on how you configured your installation, you may encounter additional issues that are not reported by Upgrade Advisor.</span></span> <span data-ttu-id="a2f08-108">これらの問題によって [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をアップグレードできなくなることはありませんが、アップグレード完了後にレポートとアプリケーションの実行に影響する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a2f08-108">These issues do not prevent a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] upgrade from succeeding, but they may affect how reports and applications run after an upgrade is finished.</span></span> <span data-ttu-id="a2f08-109">これらの問題の詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「Reporting Services の旧バージョンとの互換性」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2f08-109">To learn about these issues, see "Reporting Services Backward Compatibility" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="a2f08-110">セットアップを使用して [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をアップグレードできない場合は、新しい [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インスタンスをインストールし、既存の Reporting Services を新しいインスタンスに移行できます。</span><span class="sxs-lookup"><span data-stu-id="a2f08-110">If you cannot use Setup to upgrade a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation, you can install a new [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance and migrate your existing installation to the new instance.</span></span> <span data-ttu-id="a2f08-111">詳細については、オンラインブックの「Reporting Services のアップグレードと移行」 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、「[アップグレードと移行](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)」を参照してください Reporting Services。</span><span class="sxs-lookup"><span data-stu-id="a2f08-111">For more information, see "Upgrade and Migrate Reporting Services" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online, [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).</span></span>  
  
 <span data-ttu-id="a2f08-112">次に示すトピックでは、アップグレード アドバイザーによって報告される既知の問題、および既存インストールを修正してアップグレードを可能にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a2f08-112">The following topics describe known issues that are reported by Upgrade Advisor, and explain how you can modify your existing installation to allow an upgrade to occur.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a2f08-113">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインスタンスを分析するには、アップグレード アドバイザーをレポート サーバーにインストールしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2f08-113">Upgrade Advisor must be installed on the report server to analyze an instance of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="a2f08-114">はリモート分析をサポートしません。</span><span class="sxs-lookup"><span data-stu-id="a2f08-114">does not support remote analysis.</span></span>  
>   
>  <span data-ttu-id="a2f08-115">詳細については、「 [Upgrade Advisor のインストール](../../../2014/sql-server/install/installing-upgrade-advisor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2f08-115">For more information, see [Installing Upgrade Advisor](../../../2014/sql-server/install/installing-upgrade-advisor.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a2f08-116">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a2f08-116">In This Section</span></span>  
  
-   [<span data-ttu-id="a2f08-117">レポートサーバー web サイトのクライアント証明書 &#40;Upgrade Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="a2f08-117">Client certificates on the report server web site &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/client-certificates-on-the-report-server-web-site-upgrade-advisor.md)  
  
-   [<span data-ttu-id="a2f08-118">レポートサーバー &#40;アップグレードアドバイザーでカスタム拡張機能が検出されました&#41;</span><span class="sxs-lookup"><span data-stu-id="a2f08-118">Custom extensions were detected on the report server &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/custom-extensions-were-detected-on-the-report-server-upgrade-advisor.md)  
  
-   [<span data-ttu-id="a2f08-119">カスタムレポートアイテムがレポートサーバー &#40;アップグレードアドバイザーで検出されました&#41;</span><span class="sxs-lookup"><span data-stu-id="a2f08-119">Custom report items were detected on the report server &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/custom-report-items-were-detected-on-the-report-server-upgrade-advisor.md)  
  
-   [<span data-ttu-id="a2f08-120">アップグレードアドバイザー &#40;IIS の下位互換性コンポーネントが検出されませんでした&#41;</span><span class="sxs-lookup"><span data-stu-id="a2f08-120">IIS backward compatibility components were not detected &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/iis-backward-compatibility-components-were-not-detected-upgrade-advisor.md)  
  
-   [<span data-ttu-id="a2f08-121">アップグレードアドバイザーの &#40;IP アドレス制限が検出されました&#41;</span><span class="sxs-lookup"><span data-stu-id="a2f08-121">IP address restriction detected &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/ip-address-restriction-detected-upgrade-advisor.md)  
  
-   [<span data-ttu-id="a2f08-122">レポートサーバーサイト &#40;アップグレードアドバイザーで検出された ISAPI フィルター&#41;</span><span class="sxs-lookup"><span data-stu-id="a2f08-122">ISAPI filters detected on the report server site &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/isapi-filters-detected-on-the-report-server-site-upgrade-advisor.md)  
  
-   [<span data-ttu-id="a2f08-123">古い拡張機能がレポートサーバーコンピューター &#40;アップグレードアドバイザーで検出されました&#41;</span><span class="sxs-lookup"><span data-stu-id="a2f08-123">Obsolete extensions were detected on the report server computer &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/obsolete-extensions-were-detected-on-the-report-server-computer-upgrade-advisor.md)  
  
-   [<span data-ttu-id="a2f08-124">レポートサーバーデータベースがアップグレードアドバイザー &#40;構成されていません&#41;</span><span class="sxs-lookup"><span data-stu-id="a2f08-124">Report server database is not configured &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/report-server-database-is-not-configured-upgrade-advisor.md)  
  
-   [<span data-ttu-id="a2f08-125">SQL Server 2005 レポートサーバー Web サービスグループが &#40;アップグレードアドバイザーを検出しました&#41;</span><span class="sxs-lookup"><span data-stu-id="a2f08-125">SQL Server 2005 Report Server Web Service group detected &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/sql-server-2005-report-server-web-service-group-detected-upgrade-advisor.md)  
  
-   [<span data-ttu-id="a2f08-126">仮想ディレクトリは &#40;アップグレードアドバイザーでは指定されていません&#41;</span><span class="sxs-lookup"><span data-stu-id="a2f08-126">Virtual directories are unspecified &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/virtual-directories-are-unspecified-upgrade-advisor.md)  
  
-   [<span data-ttu-id="a2f08-127">仮想ディレクトリに、アップグレードアドバイザー &#40;サポートされていない認証方法があり&#41;</span><span class="sxs-lookup"><span data-stu-id="a2f08-127">Virtual directory has unsupported authentication method &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/virtual-directory-has-unsupported-authentication-method-upgrade-advisor.md)  
  
-   [<span data-ttu-id="a2f08-128">SQL Server Standard と Enterprise &#40;Upgrade Advisor の CPU およびメモリの制限に対する変更&#41;</span><span class="sxs-lookup"><span data-stu-id="a2f08-128">Changes to CPU and memory limits for SQL Server Standard and Enterprise &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/cpu-memory-limits-changes-sql-server-standard-enterprise-upgrade-advisor.md)  
  
-   [<span data-ttu-id="a2f08-129">SharePoint ファームに必要なドメインアカウント &#40;Upgrade Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="a2f08-129">Domain accounts required for SharePoint farm &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/domain-accounts-required-for-sharepoint-farm-upgrade-advisor.md)  
  
-   [<span data-ttu-id="a2f08-130">レポートサーバー &#40;アップグレードアドバイザーの直接参照&#41;</span><span class="sxs-lookup"><span data-stu-id="a2f08-130">Direct Browsing to Report Server &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/direct-browsing-to-report-server-upgrade-advisor.md)  
  
-   [<span data-ttu-id="a2f08-131">Microsoft SharePoint 2007 は &#40;Upgrade Advisor にインストールされて&#41;</span><span class="sxs-lookup"><span data-stu-id="a2f08-131">Microsoft SharePoint 2007 is Installed &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/microsoft-sharepoint-2007-is-installed-upgrade-advisor.md)  
  
-   [<span data-ttu-id="a2f08-132">SharePoint 共有サービスがサイドバイサイド &#40;アップグレードアドバイザーによってインストールされている Microsoft SQL Server Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a2f08-132">Microsoft SQL Server Reporting Services SharePoint Shared Service is Installed Side by Side &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/sql-server-reporting-services-sharepoint-shared-service-side-by-side-upgrade-advisor.md)  
  
-   [<span data-ttu-id="a2f08-133">互換性のないデータベースエンジン Server 照合順序 &#40;アップグレードアドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="a2f08-133">Incompatible Database Engine Server Collation &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/incompatible-database-engine-server-collation-upgrade-advisor.md)  
  
-   [<span data-ttu-id="a2f08-134">Reporting Services のアップグレードに関するその他の問題</span><span class="sxs-lookup"><span data-stu-id="a2f08-134">Other Reporting Services Upgrade Issues</span></span>](../../../2014/sql-server/install/other-reporting-services-upgrade-issues.md)  
  
  
