---
title: PowerPivot for SharePoint アドインのインストールまたはアンインストール (SharePoint 2013) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: fe13ce8b-9369-4126-928a-9426f9119424
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7df54d11021163167149e5b0c1edd960fee1a2ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713601"
---
# <a name="install-or-uninstall-the-powerpivot-for-sharepoint-add-in-sharepoint-2013"></a><span data-ttu-id="1d94a-102">PowerPivot for SharePoint アドインのインストールまたはアンインストール (SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="1d94a-102">Install or Uninstall the PowerPivot for SharePoint Add-in (SharePoint 2013)</span></span>
  [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)]<span data-ttu-id="1d94a-103">[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] ファームでの [!INCLUDE[SPS2013](../../../includes/sps2013-md.md)] データ アクセスを提供するアプリケーション サーバー コンポーネントとバックエンド サービスのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="1d94a-103">is a collection of application server components and back-end services that provide [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] data access in a [!INCLUDE[SPS2013](../../../includes/sps2013-md.md)] farm.</span></span> <span data-ttu-id="1d94a-104">[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint アドイン (**spPowerpivot.msi**) は、アプリケーション サーバー コンポーネントのインストールに使用されるインストーラー パッケージです。</span><span class="sxs-lookup"><span data-stu-id="1d94a-104">The [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint add-in (**spPowerpivot.msi**) is an installer package used to install the application server components.</span></span>

-   <span data-ttu-id="1d94a-105">このアドインは、SharePoint 2010 の配置に必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="1d94a-105">The add-in is not required for SharePoint 2010 deployments.</span></span>

-   <span data-ttu-id="1d94a-106">このアドインは、SharePoint 2013 と SharePoint モードの [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] が含まれるシングル サーバー配置では必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="1d94a-106">The add-in is not required on a single server deployment that includes SharePoint 2013 and [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] in SharePoint mode.</span></span> <span data-ttu-id="1d94a-107">アドインによってインストールされたコンポーネントは、SharePoint モードで [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サーバーをインストールするときに含まれます。</span><span class="sxs-lookup"><span data-stu-id="1d94a-107">The components installed by the add-in are included when you install an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server in SharePoint mode.</span></span> <span data-ttu-id="1d94a-108">アドインを使用した配置例の図については、「 [SharePoint の SQL SERVER BI 機能の配置トポロジ](../../../sql-server/install/deployment-topologies-for-sql-server-bi-features-in-sharepoint.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d94a-108">For diagrams of example deployments with the add-in, see [Deployment Topologies for SQL Server BI Features in SharePoint](../../../sql-server/install/deployment-topologies-for-sql-server-bi-features-in-sharepoint.md).</span></span>

 <span data-ttu-id="1d94a-109">**注** : このトピックでは、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] ソリューション ファイルと [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2013 構成ツールのインストールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="1d94a-109">**Note:** This topic describes installing the [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] solution files and [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2013 Configuration tool.</span></span> <span data-ttu-id="1d94a-110">インストール後に、構成ツールとその他の機能の詳細については、次のトピックを参照してください。 [SharePoint 2013&#41;&#40;、PowerPivot の構成とソリューションの配置](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013)です。</span><span class="sxs-lookup"><span data-stu-id="1d94a-110">After the installation, see the following topic for information on the configuration tool and additional features, [Configure PowerPivot and Deploy Solutions &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013).</span></span>

 <span data-ttu-id="1d94a-111">**spPowerPivot.msi**をダウンロードする方法の詳細については、「 [Microsoft® SQL Server® 2014 PowerPivot® for Microsoft SharePoint®](https://go.microsoft.com/fwlink/?LinkID=324854)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d94a-111">For information on how to download **spPowerPivot.msi**, see [Microsoft® SQL Server® 2014 PowerPivot® for Microsoft SharePoint®](https://go.microsoft.com/fwlink/?LinkID=324854).</span></span>

 <span data-ttu-id="1d94a-112">**このトピックの内容:**</span><span class="sxs-lookup"><span data-stu-id="1d94a-112">**In this topic:**</span></span>

-   [<span data-ttu-id="1d94a-113">背景</span><span class="sxs-lookup"><span data-stu-id="1d94a-113">Background</span></span>](#bkmk_background)

-   [<span data-ttu-id="1d94a-114">spPowerPivot.msi をインストールする場所</span><span class="sxs-lookup"><span data-stu-id="1d94a-114">Where to Install spPowerPivot.msi?</span></span>](#bkmk_where_to_install)

-   [<span data-ttu-id="1d94a-115">要件と前提条件</span><span class="sxs-lookup"><span data-stu-id="1d94a-115">Requirements and Prerequisites</span></span>](#bkmk_prereq)

-   [<span data-ttu-id="1d94a-116">PowerPivot for SharePoint をインストールするには</span><span class="sxs-lookup"><span data-stu-id="1d94a-116">To Install PowerPivot for SharePoint</span></span>](#bkmk_install)

-   [<span data-ttu-id="1d94a-117">PowerPivot for SharePoint 2013 構成ツールを使用した SharePoint ソリューション ファイルの配置</span><span class="sxs-lookup"><span data-stu-id="1d94a-117">Deploy the SharePoint Solution Files with the PowerPivot for SharePoint 2013 Configuration Tool</span></span>](#bkmk_deploy_solution)

-   [<span data-ttu-id="1d94a-118">アドインのアンインストールまたは修復</span><span class="sxs-lookup"><span data-stu-id="1d94a-118">Uninstall or repair the add-in</span></span>](#bkmk_remove_addin)

##  <a name="background"></a><a name="bkmk_background"></a> <span data-ttu-id="1d94a-119">背景情報</span><span class="sxs-lookup"><span data-stu-id="1d94a-119">Background</span></span>

-   <span data-ttu-id="1d94a-120">**アプリケーション サーバー:** [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 機能には、データ ソースとしてのブックの使用、定期データ更新、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 管理ダッシュボードなどが含まれます。</span><span class="sxs-lookup"><span data-stu-id="1d94a-120">**Application Server:** [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] functionality in SharePoint 2013 includes using workbooks as a data source, scheduled data refresh, and the [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] Management Dashboard.</span></span>

     [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] <span data-ttu-id="1d94a-121">Analysis Services クライアント ライブラリを配置し、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] インストール ファイルをコンピューターにコピーする**Windows インストーラー パッケージ (** spPowerpivot.msi [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] ) です。</span><span class="sxs-lookup"><span data-stu-id="1d94a-121">is a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows Installer package (**spPowerpivot.msi**) that deploys Analysis Services client libraries and copies [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] installation files to the computer.</span></span> <span data-ttu-id="1d94a-122">インストーラーは、SharePoint での [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 機能の配置や構成は行いません。</span><span class="sxs-lookup"><span data-stu-id="1d94a-122">The installer does not deploy or configure [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] features in SharePoint.</span></span> <span data-ttu-id="1d94a-123">既定では、次のコンポーネントがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="1d94a-123">The following components install by default:</span></span>

    -   [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] <span data-ttu-id="1d94a-124">2013。このコンポーネントには、PowerShell スクリプト (.ps1 ファイル)、SharePoint ソリューション パッケージ (.wsp)、および SharePoint 2013 ファームに [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] を配置するための [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 2013 構成ツールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1d94a-124">2013. This component includes PowerShell scripts (.ps1 files), SharePoint solution packages (.wsp), and the [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 2013 configuration tool to deploy [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] in a SharePoint 2013 farm.</span></span>

    -   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="1d94a-125">OLE DB Provider for Analysis Services (MSOLAP)。</span><span class="sxs-lookup"><span data-stu-id="1d94a-125">OLE DB Provider for Analysis Services (MSOLAP).</span></span>

    -   <span data-ttu-id="1d94a-126">ADOMD.NET データ プロバイダー。</span><span class="sxs-lookup"><span data-stu-id="1d94a-126">ADOMD.NET data provider.</span></span>

    -   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="1d94a-127">分析管理オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="1d94a-127">Analysis Management Objects.</span></span>

-   <span data-ttu-id="1d94a-128">**バックエンド サービス:**[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for Excel を使用して分析データが含まれたブックを作成した場合、サーバー環境でそのデータにアクセスするには、BI サーバーが SharePoint モードで [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] を実行するように Excel Services を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1d94a-128">**Backend services:** If you use [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for Excel to create workbooks that contain analytical data, you must have Excel Services configured with a BI server running [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] in SharePoint mode to access that data in a server environment.</span></span> <span data-ttu-id="1d94a-129">SQL Server セットアップは、SharePoint Server 2013 がインストールされているコンピューターで実行することも、SharePoint ソフトウェアがインストールされていない別のコンピューターで実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="1d94a-129">You can run SQL Server Setup on a computer that has SharePoint Server 2013 installed, or on a different computer that has no SharePoint software.</span></span> <span data-ttu-id="1d94a-130">Analysis Services には、SharePoint との依存関係はありません。</span><span class="sxs-lookup"><span data-stu-id="1d94a-130">Analysis Services does not have any dependencies on SharePoint.</span></span>

     <span data-ttu-id="1d94a-131">バックエンド サービスのインストール、アンインストール、構成の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d94a-131">For more information on installing, uninstalling, and configuring the backend services, see the following:</span></span>

    -   [<span data-ttu-id="1d94a-132">PowerPivot for SharePoint 2013 のインストール</span><span class="sxs-lookup"><span data-stu-id="1d94a-132">PowerPivot for SharePoint 2013 Installation</span></span>](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode)

    -   [<span data-ttu-id="1d94a-133">PowerPivot for SharePoint のアンインストール</span><span class="sxs-lookup"><span data-stu-id="1d94a-133">Uninstall PowerPivot for SharePoint</span></span>](../../../sql-server/install/uninstall-power-pivot-for-sharepoint.md)

##  <a name="where-to-install-sppowerpivotmsi"></a><a name="bkmk_where_to_install"></a><span data-ttu-id="1d94a-134">spPowerPivot.msi のインストール場所</span><span class="sxs-lookup"><span data-stu-id="1d94a-134">Where to Install spPowerPivot.msi?</span></span>
 <span data-ttu-id="1d94a-135">ベスト プラクティスとして、構成の一貫性を確保するために、SharePoint ファームのすべてのサーバー (アプリケーション サーバーや Web フロントエンド サーバーなど) に **spPowerPivot.msi** をインストールすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1d94a-135">A recommended best practice is to install **spPowerPivot.msi** on all servers in the SharePoint farm for configuration consistency, including application servers and web-front end servers.</span></span> <span data-ttu-id="1d94a-136">インストーラー パッケージには、Analysis Services データ プロバイダーと [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] 構成ツールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1d94a-136">The installer package includes the Analysis Services data providers as well as the [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] configuration tool.</span></span> <span data-ttu-id="1d94a-137">**spPowerPivot.msi** をインストールするときに、個々のコンポーネントを除外することで、インストールをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="1d94a-137">When you install **spPowerPivot.msi** you can customize the installation by excluding individual components.</span></span>

 <span data-ttu-id="1d94a-138">**データ プロバイダー:** SharePoint と SQL Server のさまざまなテクノロジで Analysis Services データ プロバイダー (Excel Services、PerformancePoint Services、Power View など) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="1d94a-138">**Data providers:** Several SharePoint and SQL Server technologies use the Analysis Services data providers including Excel Services, PerformancePoint Services, and Power View.</span></span> <span data-ttu-id="1d94a-139">**spPowerPivot.msi** をすべての SharePoint サーバーにインストールすると、Analysis Services データ プロバイダーの完全なセットと PowerPivot の接続をファーム全体で常に使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="1d94a-139">Installing **spPowerPivot.msi** on all SharePoint servers ensures the full set of Analysis Services data providers and PowerPivot connectivity is consistently available across the farm.</span></span>

> [!NOTE]
>  <span data-ttu-id="1d94a-140">Analysis Services データ プロバイダーは、 **spPowerPivot.msi**を使用して SharePoint 2013 サーバーにインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1d94a-140">You must install the Analysis Services data providers on a SharePoint 2013 server using **spPowerPivot.msi**.</span></span> <span data-ttu-id="1d94a-141">[!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] Feature Pack に用意されている他のインストーラー パッケージには、この環境でデータ プロバイダーが必要とする SharePoint 2013 サポート ファイルが含まれていないため、これらのパッケージはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="1d94a-141">Other installer packages available in the [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] Feature Pack are not supported because these packages do not include the SharePoint 2013 support files that the data providers require in this environment.</span></span>

 <span data-ttu-id="1d94a-142">**構成ツール:** PowerPivot for SharePoint 2013 構成ツールが必須となる SharePoint サーバーは 1 台だけです。</span><span class="sxs-lookup"><span data-stu-id="1d94a-142">**Configuration Tool:** The PowerPivot for SharePoint 2013 configuration tool is required on only one of the SharePoint servers.</span></span> <span data-ttu-id="1d94a-143">ただし、ベスト プラクティスとして、マルチサーバー ファームでは少なくとも 2 台のサーバーに構成ツールをインストールし、一方のサーバーがオフラインの場合でも構成ツールにアクセスできるようにしておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1d94a-143">However a recommended best practice in multi-server farms is to install the configuration tool on at least two servers so you have access to the configuration tool if one of the two servers is offline.</span></span>

##  <a name="requirements-and-prerequisites"></a><a name="bkmk_prereq"></a><span data-ttu-id="1d94a-144">要件と前提条件</span><span class="sxs-lookup"><span data-stu-id="1d94a-144">Requirements and Prerequisites</span></span>

-   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="1d94a-145">SharePoint Server 2013。</span><span class="sxs-lookup"><span data-stu-id="1d94a-145">SharePoint Server 2013.</span></span>

-   <span data-ttu-id="1d94a-146">SharePoint 製品およびテクノロジの要件に従い、**spPowerPivot.msi** は 64 ビットのみです。</span><span class="sxs-lookup"><span data-stu-id="1d94a-146">**spPowerPivot.msi** is 64-bit only, in accordance with the requirements of SharePoint products and technologies.</span></span>

-   <span data-ttu-id="1d94a-147">PowerPivot モードの [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] サーバー。</span><span class="sxs-lookup"><span data-stu-id="1d94a-147">A [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] server in PowerPivot mode.</span></span> <span data-ttu-id="1d94a-148">Excel Services では、PowerPivot サーバーとして SQL Server Analysis Services インスタンスを使用します。</span><span class="sxs-lookup"><span data-stu-id="1d94a-148">Excel Services will use the SQL Server Analysis Services instance as a PowerPivot server.</span></span> <span data-ttu-id="1d94a-149">Analysis Services は、ローカル コンピューターでもリモート コンピューターでも実行できます。</span><span class="sxs-lookup"><span data-stu-id="1d94a-149">Analysis Services can run on the local or a remote computer.</span></span>

-   <span data-ttu-id="1d94a-150">**権限:**[!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)]をインストールするには、現在のユーザーがコンピューターの管理者であり、SharePoint ファーム管理者グループのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="1d94a-150">**Permissions:** To install [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)], the current user is required to be an administrator on the computer and a SharePoint Farm Administrators group.</span></span>

-   <span data-ttu-id="1d94a-151">要件と前提条件の詳細について [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] は、「 [SharePoint モードの Analysis Services Server のハードウェアとソフトウェアの要件 &#40;SQL Server 2014&#41;」](../../../sql-server/install/hardware-software-requirements-analysis-services-server-sharepoint-mode.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d94a-151">For more information on [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] requirements and pre-requisites, go to [Hardware and Software Requirements for Analysis Services Server in SharePoint Mode &#40;SQL Server 2014&#41;](../../../sql-server/install/hardware-software-requirements-analysis-services-server-sharepoint-mode.md).</span></span>

##  <a name="to-install-powerpivot-for-sharepoint"></a><a name="bkmk_install"></a><span data-ttu-id="1d94a-152">PowerPivot for SharePoint をインストールするには</span><span class="sxs-lookup"><span data-stu-id="1d94a-152">To Install PowerPivot for SharePoint</span></span>
 <span data-ttu-id="1d94a-153">**spPowerpivot.msi** インストーラー パッケージは、グラフィカル ユーザー インターフェイスとコマンド ライン モードの両方をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="1d94a-153">The **spPowerpivot.msi** installer package supports both a graphical user interface and a command-line mode.</span></span> <span data-ttu-id="1d94a-154">どちらのインストール方法でも、管理者特権で .msi を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1d94a-154">Both methods of installation require that you run the .msi with administrator privileges.</span></span> <span data-ttu-id="1d94a-155">インストール後に、構成ツールとその他の機能の詳細については、次のトピックを参照してください。 [SharePoint 2013&#41;&#40;、PowerPivot の構成とソリューションの配置](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013)です。</span><span class="sxs-lookup"><span data-stu-id="1d94a-155">After the installation, see the following topic for information on the configuration tool and additional features, [Configure PowerPivot and Deploy Solutions &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013).</span></span>

### <a name="user-interface-installation"></a><span data-ttu-id="1d94a-156">ユーザー インターフェイスを使用したインストール</span><span class="sxs-lookup"><span data-stu-id="1d94a-156">User interface installation</span></span>
 <span data-ttu-id="1d94a-157">グラフィカル ユーザー インターフェイスを使用して [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] をインストールするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="1d94a-157">To install [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] with the graphical user interface, complete the following steps:</span></span>

1.  <span data-ttu-id="1d94a-158">**SpPowerPivot.msi**を実行します。</span><span class="sxs-lookup"><span data-stu-id="1d94a-158">Run **SpPowerPivot.msi**.</span></span>

2.  <span data-ttu-id="1d94a-159">[ようこそ] ページで **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d94a-159">Click **Next** on the Welcome page.</span></span>

3.  <span data-ttu-id="1d94a-160">使用許諾契約書を確認して同意し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d94a-160">Review and accept the license agreement, then click **Next**.</span></span>

4.  <span data-ttu-id="1d94a-161">**[機能の選択]** ページでは、すべての機能が既定で選択されています。</span><span class="sxs-lookup"><span data-stu-id="1d94a-161">On the **Feature Selection** page, all of the features are selected by default.</span></span>

5.  <span data-ttu-id="1d94a-162">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d94a-162">Click **Next**.</span></span>

6.  <span data-ttu-id="1d94a-163">**[インストール]** をクリックしてインストールを実行し、インストールを終了します。</span><span class="sxs-lookup"><span data-stu-id="1d94a-163">Click **Install** to install to finish the installation.</span></span>

### <a name="command-line-installation"></a><span data-ttu-id="1d94a-164">コマンド ライン インストール</span><span class="sxs-lookup"><span data-stu-id="1d94a-164">Command Line Installation</span></span>
 <span data-ttu-id="1d94a-165">コマンド ライン インストールでは、管理権限でコマンド プロンプトを開き、 **spPowerPivot.msi**を実行します。</span><span class="sxs-lookup"><span data-stu-id="1d94a-165">For a command-line installation, open a command prompt with administrative permissions, and then run the **spPowerPivot.msi**.</span></span> <span data-ttu-id="1d94a-166">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="1d94a-166">For example:</span></span>

 <span data-ttu-id="1d94a-167">`Msiexec.exe /i SpPowerPivot.msi`.</span><span class="sxs-lookup"><span data-stu-id="1d94a-167">`Msiexec.exe /i SpPowerPivot.msi`.</span></span>

 <span data-ttu-id="1d94a-168">インストール ログを作成するには、MsiExec の標準のログ スイッチを使用します。</span><span class="sxs-lookup"><span data-stu-id="1d94a-168">To create an installation log, use the standard MsiExec logging switches.</span></span> <span data-ttu-id="1d94a-169">次の例では、"v" 詳細ログスイッチを使用して、ログファイル "Install_Log.txt" を作成します。</span><span class="sxs-lookup"><span data-stu-id="1d94a-169">The following example creates the log file "Install_Log.txt" using the "v" verbose logging switch.</span></span>

```cmd
Msiexec.exe /i SpPowerPivot.msi /L v c:\test\Install_Log.txt
```

### <a name="quiet-command-line-installation-for-scripting"></a><span data-ttu-id="1d94a-170">スクリプト作成のためのサイレント コマンド ライン インストール</span><span class="sxs-lookup"><span data-stu-id="1d94a-170">Quiet Command Line Installation for scripting</span></span>
 <span data-ttu-id="1d94a-171">**/Q**または **/quiet**スイッチを使用して、ダイアログや警告が表示されない "quiet" インストールを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="1d94a-171">You can use the **/q** or **/quiet** switches for a "quiet" installation that will not display any dialogs or warnings.</span></span> <span data-ttu-id="1d94a-172">サイレント インストールは、アドインのインストールのスクリプトを作成する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1d94a-172">The quiet installation is useful if you want to script the installation of the add-in.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="1d94a-173">サイレント コマンド ライン インストールで **/q** スイッチを使用する場合、使用許諾契約書は表示されません。</span><span class="sxs-lookup"><span data-stu-id="1d94a-173">If you use the **/q** switch for a silent command line installation, the end-user license agreement will not be displayed.</span></span> <span data-ttu-id="1d94a-174">インストール方法にかかわらず、このソフトウェアの使用は、使用許諾契約に基づいています。ユーザーは使用許諾契約に準拠する責任があります。</span><span class="sxs-lookup"><span data-stu-id="1d94a-174">Regardless of the installation method, the use of this software is governed by a license agreement and you are responsible for complying with the license agreement.</span></span>

#### <a name="to-perform-a-quiet-installation"></a><span data-ttu-id="1d94a-175">サイレントインストールを実行するには</span><span class="sxs-lookup"><span data-stu-id="1d94a-175">To perform a quiet installation</span></span>

1.  <span data-ttu-id="1d94a-176">**管理者権限を使用して**コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="1d94a-176">Open a command prompt **with administrator permissions**.</span></span>

2.  <span data-ttu-id="1d94a-177">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="1d94a-177">Run the following command:</span></span>

    ```cmd
    Msiexec.exe /i spPowerPivot.msi /q
    ```

### <a name="command-line-installation-to-include-specific-components"></a><span data-ttu-id="1d94a-178">コマンド ラインを使用した特定のコンポーネントのインストール</span><span class="sxs-lookup"><span data-stu-id="1d94a-178">Command Line Installation to include specific components</span></span>
 <span data-ttu-id="1d94a-179">[!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] 構成ツールは、すべての SharePoint サーバーで必須というわけではありません (ただし、必要なときに使用できるように、少なくとも 2 台のサーバーにインストールすることをお勧めします)。</span><span class="sxs-lookup"><span data-stu-id="1d94a-179">The [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] Configuration tool is not required on every SharePoint server, however it is recommended to install it on at least two servers so the configuration tool is available when you need it.</span></span>

 <span data-ttu-id="1d94a-180">spPowerPivot.msi をインストールするときに、コマンド ライン オプションを使用して、 [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] 構成ツールではなく、データ プロバイダーなどの特定の項目をインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="1d94a-180">When you install the spPowerPivot.msi, you can use the command line options to install specific items, such as the data providers and not the [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] Configuration tool.</span></span> <span data-ttu-id="1d94a-181">構成ツール以外のすべてのコンポーネントをインストールするコマンド ラインの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1d94a-181">The following command line is an example of installing all components except the configuration tool:</span></span>

```
Msiexec /i spPowerPivot.msi AGREETOLICENSE="yes" ADDLOCAL=" SQL_OLAPDM,SQL_ADOMD,SQL_AMO,SQLAS_SP_Common"
```

|<span data-ttu-id="1d94a-182">オプション</span><span class="sxs-lookup"><span data-stu-id="1d94a-182">Option</span></span>|<span data-ttu-id="1d94a-183">説明</span><span class="sxs-lookup"><span data-stu-id="1d94a-183">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="1d94a-184">Analysis_Server_SP_addin</span><span class="sxs-lookup"><span data-stu-id="1d94a-184">Analysis_Server_SP_addin</span></span>|<span data-ttu-id="1d94a-185">PowerPivot 構成ツール</span><span class="sxs-lookup"><span data-stu-id="1d94a-185">PowerPivot Configuration</span></span>|
|<span data-ttu-id="1d94a-186">SQL_OLAPDM</span><span class="sxs-lookup"><span data-stu-id="1d94a-186">SQL_OLAPDM</span></span>|<span data-ttu-id="1d94a-187">MSOLAP</span><span class="sxs-lookup"><span data-stu-id="1d94a-187">MSOLAP</span></span>|
|<span data-ttu-id="1d94a-188">SQL_ADOMD</span><span class="sxs-lookup"><span data-stu-id="1d94a-188">SQL_ADOMD</span></span>|<span data-ttu-id="1d94a-189">ADOMD.net プロバイダー</span><span class="sxs-lookup"><span data-stu-id="1d94a-189">ADOMD.net provider</span></span>|
|<span data-ttu-id="1d94a-190">SQL_AMO</span><span class="sxs-lookup"><span data-stu-id="1d94a-190">SQL_AMO</span></span>|<span data-ttu-id="1d94a-191">AMO プロバイダー</span><span class="sxs-lookup"><span data-stu-id="1d94a-191">AMO provider</span></span>|
|<span data-ttu-id="1d94a-192">SQLAS_SP_Common</span><span class="sxs-lookup"><span data-stu-id="1d94a-192">SQLAS_SP_Common</span></span>|<span data-ttu-id="1d94a-193">SharePoint 2013 の Analysis Services 共通コンポーネント</span><span class="sxs-lookup"><span data-stu-id="1d94a-193">Analysis Services common components for SharePoint 2013</span></span>|

##  <a name="deploy-the-sharepoint-solution-files-with-the-powerpivot-for-sharepoint-2013-configuration-tool"></a><a name="bkmk_deploy_solution"></a><span data-ttu-id="1d94a-194">PowerPivot for SharePoint 2013 構成ツールを使用した SharePoint ソリューションファイルのデプロイ</span><span class="sxs-lookup"><span data-stu-id="1d94a-194">Deploy the SharePoint Solution Files with the PowerPivot for SharePoint 2013 Configuration Tool</span></span>
 <span data-ttu-id="1d94a-195">spPowerPivot.msi によって、3 つの SharePoint ソリューション ファイルがハード ドライブにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="1d94a-195">Three of the files copied to the hard drive by spPowerPivot.msi are SharePoint solution files.</span></span> <span data-ttu-id="1d94a-196">ソリューション ファイルのスコープは 1 つが Web アプリケーション レベル、残り 2 つがファーム レベルです。</span><span class="sxs-lookup"><span data-stu-id="1d94a-196">The scope of one solution file is the Web application level while the scope of the other files is the farm level.</span></span> <span data-ttu-id="1d94a-197">次のファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="1d94a-197">The files are the following:</span></span>

-   `PowerPivotFarmSolution.wsp`

-   `PowerPivotFarm14Solution.wsp`

-   `PowerPivotWebApplicationSolution.wsp`

 <span data-ttu-id="1d94a-198">ソリューション ファイルは次のフォルダーにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="1d94a-198">The solution files are copied to the following folder:</span></span>

 `C:\Program Files\Microsoft SQL Server\120\Tools\PowerPivotTools\SPAddinConfiguration\Resources`

 <span data-ttu-id="1d94a-199">.msi をインストールした後、 [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] 構成ツールを実行して、SharePoint ファームでソリューションを構成し、配置します。</span><span class="sxs-lookup"><span data-stu-id="1d94a-199">Following the .msi installation, run the [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] Configuration Tool to configure and deploy the solutions in the SharePoint farm.</span></span>

### <a name="to-start-the-configuration-tool"></a><span data-ttu-id="1d94a-200">構成ツールを起動するには</span><span class="sxs-lookup"><span data-stu-id="1d94a-200">To start the configuration tool</span></span> 

 <span data-ttu-id="1d94a-201">Windows のスタート画面から「power」と入力し、アプリの検索結果で [ **PowerPivot for SharePoint 2013 構成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d94a-201">From the Windows Start screen type "power" and in the Apps search results, click **PowerPivot for SharePoint 2013 Configuration**.</span></span> <span data-ttu-id="1d94a-202">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のセットアップによって SharePoint 2010 と SharePoint 2013 のそれぞれの [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 構成ツールがインストールされるため、検索結果には 2 つのリンクが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="1d94a-202">Note that the search results may include two links because [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] setup installs separate [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] configuration tools for SharePoint 2010 and SharePoint 2013.</span></span> <span data-ttu-id="1d94a-203">必ず SharePoint 2013 構成ツールの [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] を起動してください。</span><span class="sxs-lookup"><span data-stu-id="1d94a-203">Make sure you start the [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2013 Configuration tool.</span></span>

 <span data-ttu-id="1d94a-204">![2つの powerpivot 構成ツール](../../media/as-powerpivot-configtools-bothicons.gif "2つの powerpivot 構成ツール")</span><span class="sxs-lookup"><span data-stu-id="1d94a-204">![two powerpivot configuration tools](../../media/as-powerpivot-configtools-bothicons.gif "two powerpivot configuration tools")</span></span>

 <span data-ttu-id="1d94a-205">**Or**</span><span class="sxs-lookup"><span data-stu-id="1d94a-205">**Or**</span></span>

1.  <span data-ttu-id="1d94a-206">**[スタート]** ボタンをクリックし、 **[すべてのプログラム]** をポイントします。</span><span class="sxs-lookup"><span data-stu-id="1d94a-206">Go to **Start**, **All Programs**.</span></span>

2.  <span data-ttu-id="1d94a-207">**[Microsoft SQL Server 2014]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d94a-207">Click **Microsoft SQL Server 2014**.</span></span>

3.  <span data-ttu-id="1d94a-208">**[構成ツール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d94a-208">Click **Configuration Tools**.</span></span>

4.  <span data-ttu-id="1d94a-209">**[PowerPivot for SharePoint 2013 の構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d94a-209">Click **PowerPivot for SharePoint 2013 Configuration**.</span></span>

 <span data-ttu-id="1d94a-210">構成ツールの詳細については、「 [PowerPivot Configuration Tools](../../power-pivot-sharepoint/power-pivot-configuration-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d94a-210">For more information on the configuration tool, see [PowerPivot Configuration Tools](../../power-pivot-sharepoint/power-pivot-configuration-tools.md).</span></span>

##  <a name="uninstall-or-repair-the-add-in"></a><a name="bkmk_remove_addin"></a><span data-ttu-id="1d94a-211">アドインをアンインストールまたは修復する</span><span class="sxs-lookup"><span data-stu-id="1d94a-211">Uninstall or repair the add-in</span></span>

> [!CAUTION]
>  <span data-ttu-id="1d94a-212">**spPowerPivot.msi** をアンインストールすると、データ プロバイダーと構成ツールがアンインストールされます。</span><span class="sxs-lookup"><span data-stu-id="1d94a-212">If you uninstall **spPowerPivot.msi** the data providers and the configuration tool are uninstalled.</span></span> <span data-ttu-id="1d94a-213">データ プロバイダーをアンインストールすると、サーバーは PowerPivot に接続できなくなります。</span><span class="sxs-lookup"><span data-stu-id="1d94a-213">Uninstalling the data providers will cause the server to be unable to connect to PowerPivot.</span></span>

 <span data-ttu-id="1d94a-214">[!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] をアンインストールまたは修復するには、次のいずれかの方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="1d94a-214">You can uninstall or repair [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] using one of the following methods:</span></span>

1.  <span data-ttu-id="1d94a-215">**Windows のコントロール パネル:\*\*\*\*[Microsoft SQL Server 2012 PowerPivot for SharePoint 2013]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1d94a-215">**Windows control panel:** Select **Microsoft SQL Server 2012 PowerPivot for SharePoint 2013**.</span></span> <span data-ttu-id="1d94a-216">**[アンインストール]** または **[修復]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d94a-216">Click either **Uninstall** or **Repair**.</span></span>

2.  <span data-ttu-id="1d94a-217">spPowerPivot.msi を実行し、 **[削除]** または **[修復]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1d94a-217">Run the spPowerPivot.msi and select the **Remove** option or the **Repair** option.</span></span>

 <span data-ttu-id="1d94a-218">**コマンド ライン:** コマンド ラインを使用して PowerPivot for SharePoint 2013 を修復またはアンインストールするには、 **管理者権限** でコマンド プロンプトを開き、次のいずれかのコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="1d94a-218">**Command Line:** To repair or uninstall PowerPivot for SharePoint 2013 using the command line, open a command prompt **with administrator permissions** and run one of the following commands:</span></span>

-   <span data-ttu-id="1d94a-219">修復するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="1d94a-219">To Repair, run the following command:</span></span>

    ```cmd
    msiexec.exe /f spPowerPivot.msi
    ```

 <span data-ttu-id="1d94a-220">または</span><span class="sxs-lookup"><span data-stu-id="1d94a-220">OR</span></span>

-   <span data-ttu-id="1d94a-221">アンインストールするには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="1d94a-221">To uninstall, run the following command:</span></span>

    ```cmd
    msiexec.exe /uninstall spPowerPivot.msi
    ```
