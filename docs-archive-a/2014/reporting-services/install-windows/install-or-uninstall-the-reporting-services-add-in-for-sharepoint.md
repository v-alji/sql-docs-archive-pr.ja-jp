---
title: SharePoint 用 Reporting Services アドインのインストールまたはアンインストール (SharePoint 2010 および SharePoint 2013) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c2804a9a-08ea-4f4a-805d-a2c19c68733d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e30014ec823e89172b36f35d7f313568432a26f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642600"
---
# <a name="install-or-uninstall-the-reporting-services-add-in-for-sharepoint-sharepoint-2010-and-sharepoint-2013"></a><span data-ttu-id="691ad-102">SharePoint 用 Reporting Services アドインのインストールまたはアンインストール (SharePoint 2010 および SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="691ad-102">Install or Uninstall the Reporting Services Add-in for SharePoint (SharePoint 2010 and SharePoint 2013)</span></span>
  <span data-ttu-id="691ad-103">Sharepoint サーバー上の sharepoint 製品用のインストールパッケージ (rsSharePoint.msi) を実行して、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sharepoint 配置内の機能を有効にし [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="691ad-103">Run the installation package [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in for SharePoint products (rsSharePoint.msi) on SharePoint servers to enable [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features within a SharePoint deployment.</span></span> <span data-ttu-id="691ad-104">提供される機能には、Power View、レポート ビューアー Web パーツ、URL プロキシ エンドポイント、コンテンツの種類、アプリケーション ページなどがあります。これにより、レポート、レポート モデル、データ ソース、およびその他のレポート サーバー コンテンツを SharePoint サイト上で作成、表示、管理できます。</span><span class="sxs-lookup"><span data-stu-id="691ad-104">Features include Power View, a Report Viewer Web Part, a URL proxy endpoint, content types, and application pages so that you can create, view, and manage reports, report models, data sources and other report server content on a SharePoint site.</span></span> <span data-ttu-id="691ad-105">SharePoint 製品用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインは、SharePoint モードで実行されるレポート サーバーに必要なコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="691ad-105">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in for SharePoint products is a required component for a report server that runs in SharePoint mode.</span></span> <span data-ttu-id="691ad-106">アドインは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] セットアップ ウィザードからインストールするか、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 機能パックから rsSharePoint.msi をダウンロードしてインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="691ad-106">The add-in can be installed from either the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] setup wizard or by downloading the rsSharePoint.msi from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] feature pack.</span></span> <span data-ttu-id="691ad-107">アドインのバージョンの一覧およびダウンロード ページについては、「 [SharePoint 製品用 Reporting Services アドインの検索場所](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="691ad-107">For a list of the versions of the add-in and download pages, see [Where to find the Reporting Services add-in for SharePoint Products](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).</span></span>

||
|-|
|<span data-ttu-id="691ad-108">**[!INCLUDE[applies](../../includes/applies-md.md)]** Sharepoint 2013 &#124; sharepoint 2010</span><span class="sxs-lookup"><span data-stu-id="691ad-108">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010</span></span>|

 <span data-ttu-id="691ad-109">**このトピックの内容:**</span><span class="sxs-lookup"><span data-stu-id="691ad-109">**In this topic:**</span></span>

-   [<span data-ttu-id="691ad-110">前提条件</span><span class="sxs-lookup"><span data-stu-id="691ad-110">Prerequisites</span></span>](#bkmk_prereq)

-   [<span data-ttu-id="691ad-111">アドインがインストールする内容</span><span class="sxs-lookup"><span data-stu-id="691ad-111">What Does The Add-in Install?</span></span>](#bkmk_whatinstalled)

-   [<span data-ttu-id="691ad-112">インストール方法の概要</span><span class="sxs-lookup"><span data-stu-id="691ad-112">Overview of the Installation Methods</span></span>](#bkmk_3ways_to_install)

-   [<span data-ttu-id="691ad-113">インストールファイルを使用してアドインをインストール rsSharePoint.msi</span><span class="sxs-lookup"><span data-stu-id="691ad-113">Install the add-in using the installation file rsSharePoint.msi</span></span>](#bkmk_install_rssharepoint)

    -   [<span data-ttu-id="691ad-114">ファイルのみのインストール</span><span class="sxs-lookup"><span data-stu-id="691ad-114">Files-only installation</span></span>](#bkmk_files_only_installation)

-   [<span data-ttu-id="691ad-115">Reporting Services アドインを削除する方法</span><span class="sxs-lookup"><span data-stu-id="691ad-115">How to Remove the Reporting Services Add-in</span></span>](#bkmk_remove_addin)

-   [<span data-ttu-id="691ad-116">コマンド ラインから rssharepoint.msi を修復する方法</span><span class="sxs-lookup"><span data-stu-id="691ad-116">How to Repair rssharepoint.msi from the Command Line</span></span>](#bkmk_repair)

-   [<span data-ttu-id="691ad-117">セットアップ ログ ファイル</span><span class="sxs-lookup"><span data-stu-id="691ad-117">Setup Log Files</span></span>](#bkmk_logfiles)

-   [<span data-ttu-id="691ad-118">アップグレード</span><span class="sxs-lookup"><span data-stu-id="691ad-118">Upgrade</span></span>](#bkmk_upgrade)

-   [<span data-ttu-id="691ad-119">rsCustomAction.exe</span><span class="sxs-lookup"><span data-stu-id="691ad-119">RsCustomAction.exe</span></span>](#bkmk_rscustomaction)

##  <a name="prerequisites"></a><a name="bkmk_prereq"></a> <span data-ttu-id="691ad-120">前提条件</span><span class="sxs-lookup"><span data-stu-id="691ad-120">Prerequisites</span></span>
 <span data-ttu-id="691ad-121">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインのインストールは、レポート サーバーと SharePoint 製品のインスタンスを統合するために必要ないくつかの手順の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="691ad-121">Installing the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in is one of several steps that are necessary for integrating a report server with an instance of a SharePoint product.</span></span> <span data-ttu-id="691ad-122">SharePoint モードの使用のすべての前提条件の詳細については、「 [Hardware and Software Requirements for Reporting Services in SharePoint Mode](../../../2014/sql-server/install/hardware-and-software-requirements-for-reporting-services-in-sharepoint-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="691ad-122">For more information about the complete set of requirements for using SharePoint mode, see [Hardware and Software Requirements for Reporting Services in SharePoint Mode](../../../2014/sql-server/install/hardware-and-software-requirements-for-reporting-services-in-sharepoint-mode.md).</span></span> <span data-ttu-id="691ad-123">のインストールと構成の詳細につい [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ては、「 [sharepoint 2013 用 Reporting Services sharepoint モードのインストール](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="691ad-123">For more information on installing and configuring [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], see [Install Reporting Services SharePoint Mode for SharePoint 2013](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md).</span></span>

-   <span data-ttu-id="691ad-124">複数の Web フロントエンド アプリケーションがある SharePoint ファームに [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を統合する場合は、Web サーバー フロントエンドがあるファームの各コンピューターにアドインをインストールします。</span><span class="sxs-lookup"><span data-stu-id="691ad-124">If you are integrating [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] with a SharePoint farm that has multiple Web front end applications, install the add-in to each computer in the farm that has a Web server front-end.</span></span> <span data-ttu-id="691ad-125">この作業は、レポート サーバー コンテンツのアクセスに使用する Web フロントエンドに対してのみ行ってください。</span><span class="sxs-lookup"><span data-stu-id="691ad-125">Do this only for Web front ends that will be used to access report server content.</span></span>

-   <span data-ttu-id="691ad-126">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインをインストールするには、コンピューターの管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="691ad-126">To install the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in, you must be an administrator on the computer.</span></span> <span data-ttu-id="691ad-127">たとえば、コマンド プロンプトで rsSharePoint.msi を実行する場合は、 **[管理者として実行]** オプションを使用して、管理者特権でコマンド プロンプトを開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="691ad-127">For example if you are going to run the rsSharePoint.msi at the command prompt, you should open the command prompt with administrator privileges by using the **Run as administrator** option.</span></span>

-   <span data-ttu-id="691ad-128">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインをインストールするには、SharePoint ファーム管理者グループのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="691ad-128">To install the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in, you must be a member of the SharePoint Farm Administrators group.</span></span>

-   <span data-ttu-id="691ad-129">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 統合機能をアクティブ化するには、サイト コレクションの管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="691ad-129">You must be a Site Collection administrator to activate the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] integration feature.</span></span>

-   <span data-ttu-id="691ad-130">アドインを使用した配置例の図については、「 [SharePoint の SQL SERVER BI 機能の配置トポロジ](../../sql-server/install/deployment-topologies-for-sql-server-bi-features-in-sharepoint.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="691ad-130">For diagrams of example deployments with the add-in, see [Deployment Topologies for SQL Server BI Features in SharePoint](../../sql-server/install/deployment-topologies-for-sql-server-bi-features-in-sharepoint.md).</span></span>

##  <a name="what-does-the-add-in-install"></a><a name="bkmk_whatinstalled"></a><span data-ttu-id="691ad-131">アドインはどのようにインストールされますか。</span><span class="sxs-lookup"><span data-stu-id="691ad-131">What Does The Add-in Install?</span></span>
 <span data-ttu-id="691ad-132">アドインのセットアップ プロセスは、2 つのフェーズで構成されます。標準インストールが完了すると、どちらのフェーズも自動的に完了します。</span><span class="sxs-lookup"><span data-stu-id="691ad-132">The add-in setup process is composed of two phases, both are completed automatically when you complete a standard installation:</span></span>

-   <span data-ttu-id="691ad-133">最初のフェーズでは、正しいフォルダーにファイルをインストールします。</span><span class="sxs-lookup"><span data-stu-id="691ad-133">The first phase is to install files to the proper folders.</span></span> <span data-ttu-id="691ad-134">それらのフォルダーは、SharePoint 配置では標準です。</span><span class="sxs-lookup"><span data-stu-id="691ad-134">The folders are standard for SharePoint deployments.</span></span> <span data-ttu-id="691ad-135">インストールされるファイルの 1 つに rsCustomAction.exe ファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="691ad-135">One of the files that is installed is rsCustomAction.exe.</span></span>

-   <span data-ttu-id="691ad-136">インストールの 2 つ目の部分では、一連のカスタム アクションを実行して、SharePoint に [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ファイルを登録します。</span><span class="sxs-lookup"><span data-stu-id="691ad-136">The second portion of the installation is to run a set of custom actions to register the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] files with SharePoint.</span></span> <span data-ttu-id="691ad-137">カスタム アクションは、rsCustomAction.exe から実行します。</span><span class="sxs-lookup"><span data-stu-id="691ad-137">The custom actions are run from rsCustomAction.exe.</span></span> <span data-ttu-id="691ad-138">2 つのフェーズで構成される完全なインストールが終了すると、exe ファイルは削除されます。</span><span class="sxs-lookup"><span data-stu-id="691ad-138">The exe is removed when the full two phase installation completes.</span></span> <span data-ttu-id="691ad-139">**[ファイルのみ]** のインストールを実行すると、インストールの終わりに rsCustomAction.exe は実行されず、ドライブに残ります。</span><span class="sxs-lookup"><span data-stu-id="691ad-139">You can run a **files only** installation and rsCustomAction.exe is not run at the end of installation and it is left on the drive.</span></span>

## <a name="the-reporting-services-installation-order"></a><span data-ttu-id="691ad-140">Reporting Services のインストールの順序</span><span class="sxs-lookup"><span data-stu-id="691ad-140">The Reporting Services Installation order</span></span>
 <span data-ttu-id="691ad-141">アドインは、SharePoint をインストールする前でも後でもインストールできます。</span><span class="sxs-lookup"><span data-stu-id="691ad-141">The add-in can be installed before installing SharePoint or after SharePoint installation.</span></span> <span data-ttu-id="691ad-142">アドインは、SharePoint の配置前の標準に準拠し、SharePoint のインストールで使用された場所にファイルをインストールします。</span><span class="sxs-lookup"><span data-stu-id="691ad-142">The add-in follows SharePoint pre-deployment standards and installs files in locations used by the SharePoint installation.</span></span>

> [!NOTE]
>  <span data-ttu-id="691ad-143">SharePoint 製品より前にアドインをインストールする利点は、新しいサーバーをファームに追加すると、Reporting Services アドインが SharePoint ファームによって構成およびアクティブ化されることです。</span><span class="sxs-lookup"><span data-stu-id="691ad-143">The advantage of installing the add-in prior to the SharePoint product is that as new servers are added to the farm, the Reporting Services Add-in will be configured and activated by the SharePoint farm.</span></span>

 <span data-ttu-id="691ad-144">**SharePoint 2010**</span><span class="sxs-lookup"><span data-stu-id="691ad-144">**SharePoint 2010**</span></span>

-   <span data-ttu-id="691ad-145">SharePoint 2010 製品準備ツールにより、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] バージョンの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="691ad-145">The SharePoint 2010 Products Preparation tool installs the [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] version of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in.</span></span> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="691ad-146">には、の機能に必要な新しいバージョンのアドインが含まれてい [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="691ad-146">includes a new version of the add-in that is required for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] features.</span></span>

     <span data-ttu-id="691ad-147">SharePoint 製品準備ツールを実行する場合でも、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] バージョンの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="691ad-147">If you run the SharePoint Products Preparation Tool, you still need to install the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in.</span></span>

-   <span data-ttu-id="691ad-148">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] バージョンの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインをインストールした場合は、SharePoint 製品準備ツールを実行すると、新しいバージョンが検知されたために準備ツールによってアドインの旧バージョンがインストールされなかったことを示す次のダイアログが表示されます。</span><span class="sxs-lookup"><span data-stu-id="691ad-148">If you install [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in first, then when you run the SharePoint Products preparation tool you will see the following dialog indicating the preparation tool did not install the older version of the add-in as the newer version was detected.</span></span> <span data-ttu-id="691ad-149">これは想定されている動作です。</span><span class="sxs-lookup"><span data-stu-id="691ad-149">This is expected behavior</span></span>

     <span data-ttu-id="691ad-150">![SSRS アドインが既にインストールされています。](../../../2014/sql-server/install/media/rs-sharepointprereq-complete.gif "SSRS アドインが既にインストールされています。")</span><span class="sxs-lookup"><span data-stu-id="691ad-150">![SSRS add-in is already installed.](../../../2014/sql-server/install/media/rs-sharepointprereq-complete.gif "SSRS add-in is already installed.")</span></span>

 <span data-ttu-id="691ad-151">**SharePoint 2013**</span><span class="sxs-lookup"><span data-stu-id="691ad-151">**SharePoint 2013**</span></span>

 <span data-ttu-id="691ad-152">SharePoint 20103 製品準備ツールでは、SharePoint 製品用アドインはインストール**されません** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="691ad-152">The SharePoint 20103 Products Preparation tool does **Not** install the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint products.</span></span>

##  <a name="overview-of-the-installation-methods"></a><a name="bkmk_3ways_to_install"></a> <span data-ttu-id="691ad-153">インストール方法の概要</span><span class="sxs-lookup"><span data-stu-id="691ad-153">Overview of the Installation Methods</span></span>
 <span data-ttu-id="691ad-154">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 製品用アドインは、次の2つの方法のいずれかを使用してインストールできます。</span><span class="sxs-lookup"><span data-stu-id="691ad-154">The [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in for SharePoint products can be installed using one of the following two methods:</span></span>

-   <span data-ttu-id="691ad-155">**インストールウィザード:** ![で新しく導入](../../../2014/reporting-services/media/rs-fyinote.png "注意")されたアドインは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インストールウィザードでインストールでき [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="691ad-155">**The installation wizard:** ![note](../../../2014/reporting-services/media/rs-fyinote.png "note")New with [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the add-in can be installed by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation wizard.</span></span> <span data-ttu-id="691ad-156">ウィザードの **[機能の選択]** ページで、 **[SharePoint 製品用 Reporting Services アドイン]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="691ad-156">Choose **Reporting Services Add-in for SharePoint Products** on the **Feature Selection** page of the wizard.</span></span>

-   <span data-ttu-id="691ad-157">**rsSharepoint.msi:** インストール メディアまたはダウンロードからアドインを直接インストールする。</span><span class="sxs-lookup"><span data-stu-id="691ad-157">**rsSharepoint.msi:** The add-in can be installed directly from the installation media or downloaded and installed.</span></span> <span data-ttu-id="691ad-158">rsSharepoint.msi は、グラフィカル ユーザー インターフェイスもコマンド ライン インストールもサポートしています。</span><span class="sxs-lookup"><span data-stu-id="691ad-158">The rsSharepoint.msi supports both a graphical user interface and a command line installation.</span></span> <span data-ttu-id="691ad-159">.msi を管理者特権を使用して実行する必要があるため、まず高度な権限でコマンド プロンプトを開いてから、コマンド ラインから rsSharepoint.msi を実行します。</span><span class="sxs-lookup"><span data-stu-id="691ad-159">You must run the .msi with administrator privileges by first opening a command prompt with elevated permissions, and then running the rsSharepoint.msi from the command line.</span></span> <span data-ttu-id="691ad-160">アドインのダウンロードの詳細については、「 [SharePoint 製品用 Reporting Services アドインの検索場所](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="691ad-160">For more information on downloading the add-in, see [Where to find the Reporting Services add-in for SharePoint Products](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).</span></span>

    > [!NOTE]
    >  <span data-ttu-id="691ad-161">サイレント コマンド ライン インストールで **/q** スイッチを使用する場合、使用許諾契約書は表示されません。</span><span class="sxs-lookup"><span data-stu-id="691ad-161">If you use the **/q** switch for a silent command line installation, the end-user license agreement will not be displayed.</span></span> <span data-ttu-id="691ad-162">インストール方法にかかわらず、このソフトウェアの使用は、使用許諾契約に基づいています。ユーザーは使用許諾契約に準拠する責任があります。</span><span class="sxs-lookup"><span data-stu-id="691ad-162">Regardless of the installation method, the use of this software is governed by a license agreement and you are responsible for complying with the license agreement.</span></span>

##  <a name="install-the-add-in-using-the-installation-file-rssharepointmsi"></a><a name="bkmk_install_rssharepoint"></a> <span data-ttu-id="691ad-163">rsSharePoint.msi インストール ファイルを使用したアドインのインストール</span><span class="sxs-lookup"><span data-stu-id="691ad-163">Install the add-in using the installation file rsSharePoint.msi</span></span>
 <span data-ttu-id="691ad-164">このセクションは、.msi インストール ウィザードの実行またはコマンド ライン インストールにより、rssharepoint.msi を直接インストールすることに関連しています。</span><span class="sxs-lookup"><span data-stu-id="691ad-164">This section is related to installing the rssharepoint.msi directly, by either running the .msi installation wizard or a command line installation.</span></span> <span data-ttu-id="691ad-165">SQL Server インストール ウィザードを使用してアドインをインストールする場合は、次の手順を実行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="691ad-165">If you installed the add-in using the SQL Server installation Wizard, you do not need to follow these steps.</span></span>

 <span data-ttu-id="691ad-166">次のコマンドを実行すると、コマンド ライン スイッチの全リストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="691ad-166">You can see a full list of command line switches by running the following command:</span></span>

```
Rssharepoint.msi /?
```

1.  <span data-ttu-id="691ad-167">アドインのセットアッププログラム () をダウンロードし `rsSharepoint.msi` [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="691ad-167">Download the Setup program (`rsSharepoint.msi`) for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in.</span></span> <span data-ttu-id="691ad-168">アドインのダウンロードの詳細については、「 [SharePoint 製品用 Reporting Services アドインの検索場所](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="691ad-168">For more information on downloading the add-in, see [Where to find the Reporting Services add-in for SharePoint Products](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).</span></span>

2.  <span data-ttu-id="691ad-169">管理者は、`rsSharepoint.msi` を実行して、インストール ウィザードを実行します。</span><span class="sxs-lookup"><span data-stu-id="691ad-169">As an administrator, run `rsSharepoint.msi` to run the Installation Wizard.</span></span> <span data-ttu-id="691ad-170">ウィザードに、"ようこそ" ページ、ソフトウェア ライセンス条項、および登録情報ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="691ad-170">The wizard displays a Welcome page, the Software license terms, and a registration information page.</span></span> <span data-ttu-id="691ad-171">セットアップ時に、次のパスにフォルダーが作成され、そのフォルダーにファイルがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="691ad-171">Setup creates folders under the following path and copies files to the folders:</span></span>

     `%program files%\common files\Microsoft Shared\Web Server Extensions\14\`

     <span data-ttu-id="691ad-172">or</span><span class="sxs-lookup"><span data-stu-id="691ad-172">or</span></span>

     `%program files%\common files\Microsoft Shared\Web Server Extensions\15\`

3.  <span data-ttu-id="691ad-173">SharePoint サーバーの全体管理で、レポート サーバーの設定と機能のアクティブ化を構成します。</span><span class="sxs-lookup"><span data-stu-id="691ad-173">Configure the report server settings and feature activation in SharePoint Central Administration.</span></span> <span data-ttu-id="691ad-174">.</span><span class="sxs-lookup"><span data-stu-id="691ad-174">.</span></span> <span data-ttu-id="691ad-175">Sharepoint モードのインストールと構成の詳細につい [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ては、「sharepoint [2010 用 Reporting Services sharepoint モードのインストール](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="691ad-175">For more information on installing and configuring [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode, see [Install Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).</span></span>

###  <a name="files-only-installation"></a><a name="bkmk_files_only_installation"></a><span data-ttu-id="691ad-176">ファイルのみのインストール</span><span class="sxs-lookup"><span data-stu-id="691ad-176">Files-only installation</span></span>
 <span data-ttu-id="691ad-177">インストールのカスタム アクション フェーズをスキップしてファイルをインストールするには、SKIPCA オプションを指定してコマンド ラインから rssharepoint.msi を実行します。</span><span class="sxs-lookup"><span data-stu-id="691ad-177">To install the files but skip the custom action phase of installation, run the rssharepoint.msi from the command line with the SKIPCA option:</span></span>

1.  <span data-ttu-id="691ad-178">**管理者権限を使用して**コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="691ad-178">Open a command prompt **with administrator permissions**.</span></span>

2.  <span data-ttu-id="691ad-179">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="691ad-179">Run the following command:</span></span>

    ```cmd
    Msiexec.exe /i rsSharePoint.msi SKIPCA=1
    ```

 <span data-ttu-id="691ad-180">インストールのユーザー インターフェイスが開き、正常に実行され、`rsCustomAction.exe` ファイルがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="691ad-180">The installation user interface will open and run as normal and the `rsCustomAction.exe` file is installed.</span></span> <span data-ttu-id="691ad-181">ただし、.exe はインストールの終了時には実行されず、インストールの終了後、`rsCustomAction.exe` はコンピューター上に残ります。</span><span class="sxs-lookup"><span data-stu-id="691ad-181">However, the .exe will not run at the end of the installation and `rsCustomAction.exe` will remain on the computer when the installation is completed.</span></span>

### <a name="use-a-two-step-installation-to-troubleshoot-installation-issues-or-install-the-content-types"></a><span data-ttu-id="691ad-182">2 ステップのインストールを使用したインストールの問題のトラブルシューティングまたはコンテンツの種類のインストール</span><span class="sxs-lookup"><span data-stu-id="691ad-182">Use a two-step installation to troubleshoot installation issues or install the content types</span></span>
 <span data-ttu-id="691ad-183">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のコンテンツの種類のインストール中にエラーが発生するか、コンテンツの種類がドキュメント ライブラリの設定に表示されない場合は、コマンド ラインから Setup を 2 ステップ プロセスとして実行します。</span><span class="sxs-lookup"><span data-stu-id="691ad-183">If you get errors during installation or the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] content types do not appear in the document library settings, you can run Setup as a two-step process from the command line:</span></span>

1.  <span data-ttu-id="691ad-184">**管理者権限で** コマンド プロンプトを開き、前のセクションの説明に従い、ファイルのみのインストールを実行します。</span><span class="sxs-lookup"><span data-stu-id="691ad-184">Open a command prompt **with administrator permissions** and run a files only installation as described in the previous section.</span></span>

2.  <span data-ttu-id="691ad-185">カスタム アクションの実行可能ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="691ad-185">Run the custom actions executable:</span></span>

    1.  <span data-ttu-id="691ad-186">`rsCustomAction.exe` ファイルのあるフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="691ad-186">Navigate to the folder that contains the file `rsCustomAction.exe`.</span></span> <span data-ttu-id="691ad-187">このファイルは、アドインのファイルのみのインストールを実行することで、コンピューターにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="691ad-187">This file is copied to your computer by the files only installation of the add-in.</span></span> <span data-ttu-id="691ad-188">`rsCustomAction.exe`は **% Temp%** ディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="691ad-188">`rsCustomAction.exe` is located in the **%Temp%** directory.</span></span> <span data-ttu-id="691ad-189">ファイルに移動するには、コマンド プロンプトから次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="691ad-189">To navigate to the file, type the following from the command prompt:</span></span>

         <span data-ttu-id="691ad-190">**CD %temp%**。</span><span class="sxs-lookup"><span data-stu-id="691ad-190">**CD %temp%**.</span></span>

         <span data-ttu-id="691ad-191">ファイルを **\Users\\<ユーザー名\>\AppData\Local\Temp** に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="691ad-191">The file should be located in: **\Users\\<your name\>\AppData\Local\Temp**</span></span>

    2.  <span data-ttu-id="691ad-192">次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="691ad-192">Type the following command.</span></span> <span data-ttu-id="691ad-193">この構成手順は、完了まで数分かかります。</span><span class="sxs-lookup"><span data-stu-id="691ad-193">This configuration step will take several minutes to finish.</span></span> <span data-ttu-id="691ad-194">この処理中に W3SVC サービスが再起動されます。</span><span class="sxs-lookup"><span data-stu-id="691ad-194">The W3SVC service will be restarted during this process.</span></span> <span data-ttu-id="691ad-195">プログラムでファイルがコピーされ、コンポーネントが登録され、SharePoint 製品構成ウィザードが実行されると共に、状態メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="691ad-195">Several Status messages will be displayed as the program copies files, registers components, and runs the SharePoint Product Configuration Wizard.</span></span>

        ```cmd
        rsCustomAction.exe /i
        ```

    3.  <span data-ttu-id="691ad-196">変更が有効になるまでの時間はサーバー環境によって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="691ad-196">The amount of time it takes for the changes to take effect may vary, depending on your server environment.</span></span> <span data-ttu-id="691ad-197">**iisreset** 実行して、更新にかかる時間を短縮することもできます。</span><span class="sxs-lookup"><span data-stu-id="691ad-197">You can also run **iisreset** to force a quicker update.</span></span>

### <a name="quiet-installation-for-scripting"></a><span data-ttu-id="691ad-198">スクリプト作成のためのサイレント インストール</span><span class="sxs-lookup"><span data-stu-id="691ad-198">Quiet installation for scripting</span></span>
 <span data-ttu-id="691ad-199">**/Q**または **/quiet**スイッチを使用して、ダイアログや警告が表示されない "quiet" インストールを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="691ad-199">You can use the **/q** or **/quiet** switches for a "quiet" installation that will not display any dialogs or warnings.</span></span> <span data-ttu-id="691ad-200">サイレント インストールは、アドインのインストールのスクリプトを作成する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="691ad-200">The quiet installation is useful if you want to script the installation of the add-in.</span></span>

> [!NOTE]
>  <span data-ttu-id="691ad-201">サイレント コマンド ライン インストールで **/q** スイッチを使用する場合、使用許諾契約書は表示されません。</span><span class="sxs-lookup"><span data-stu-id="691ad-201">If you use the **/q** switch for a silent command line installation, the end-user license agreement will not be displayed.</span></span> <span data-ttu-id="691ad-202">インストール方法にかかわらず、このソフトウェアの使用は、使用許諾契約に基づいています。ユーザーは使用許諾契約に準拠する責任があります。</span><span class="sxs-lookup"><span data-stu-id="691ad-202">Regardless of the installation method, the use of this software is governed by a license agreement and you are responsible for complying with the license agreement.</span></span>

 <span data-ttu-id="691ad-203">サイレント インストールを行うには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="691ad-203">To perform a quiet installation:</span></span>

1.  <span data-ttu-id="691ad-204">**管理者権限を使用して**コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="691ad-204">Open a command prompt **with administrator permissions**.</span></span>

2.  <span data-ttu-id="691ad-205">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="691ad-205">Run the following command:</span></span>

    ```cmd
    Msiexec.exe /i rsSharePoint.msi /q
    ```

##  <a name="how-to-remove-the-reporting-services-add-in"></a><a name="bkmk_remove_addin"></a><span data-ttu-id="691ad-206">Reporting Services アドインを削除する方法</span><span class="sxs-lookup"><span data-stu-id="691ad-206">How to Remove the Reporting Services Add-in</span></span>
 <span data-ttu-id="691ad-207">SharePoint 製品用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のコントロール パネルまたはコマンド ラインからアンインストールできます。</span><span class="sxs-lookup"><span data-stu-id="691ad-207">You can uninstall the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in for SharePoint Products from [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows control panel or the command line.</span></span>

1.  <span data-ttu-id="691ad-208">コントロール パネルを使用すると、現在のコンピューター上のファイルが完全にアンインストールされます。 **さらに** 、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のオブジェクトと機能が SharePoint ファームから削除されます。</span><span class="sxs-lookup"><span data-stu-id="691ad-208">Using control panel will run a complete uninstall of the files on the current computer **AND** it will remove the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] object and features from the SharePoint farm.</span></span> <span data-ttu-id="691ad-209">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のオブジェクトと機能が削除されると、レポートの確認と更新ができなくなります。</span><span class="sxs-lookup"><span data-stu-id="691ad-209">When the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] object and features are removed you can no longer review and update reports.</span></span>

2.  <span data-ttu-id="691ad-210">コマンド ラインでアドインをアンインストールする場合は、LocalOnly パラメーターを使用して、ローカル コンピューターからアドイン ファイルのみを削除できます。ファーム内にある [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のオブジェクトと機能は変更されません。</span><span class="sxs-lookup"><span data-stu-id="691ad-210">The command line method to uninstall the add-in allows you to use the LocalOnly parameter to only remove the add-in files from the local computer and the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] object and features in the farm will not be changed.</span></span>

 <span data-ttu-id="691ad-211">アドインをアンインストールすると、レポート サーバーでレポートの処理に使用されているサーバー統合機能が削除されます。</span><span class="sxs-lookup"><span data-stu-id="691ad-211">Uninstalling the add-in will remove server integration features that are used to process reports on a report server.</span></span> <span data-ttu-id="691ad-212">SharePoint サーバーの全体管理ページおよびその他のカスタム [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ページから、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のページも削除されます。</span><span class="sxs-lookup"><span data-stu-id="691ad-212">It will also remove the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pages from SharePoint Central Administration and other custom [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pages.</span></span> <span data-ttu-id="691ad-213">また、影響を受ける SharePoint サイトで、今後使用しないレポートとその他のレポート サーバー アイテムをすべて削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="691ad-213">You may also want to remove any reports and other report server items that you no longer use on the affected SharePoint sites.</span></span> <span data-ttu-id="691ad-214">これらは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインを削除すると実行できなくなります。</span><span class="sxs-lookup"><span data-stu-id="691ad-214">They will not run after the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in is removed.</span></span>

 <span data-ttu-id="691ad-215">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインをアンインストールするには、[!INCLUDE[SPF2010](../../includes/spf2010-md.md)] または [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="691ad-215">To uninstall the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in, you must have a [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] or [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] installation still running.</span></span> <span data-ttu-id="691ad-216">SharePoint 2010 を先にアンインストールした場合は、それを再インストールしないと [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインをアンインストールできません。</span><span class="sxs-lookup"><span data-stu-id="691ad-216">If you uninstall the SharePoint 2010 first, you must reinstall it to uninstall the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in.</span></span>

 <span data-ttu-id="691ad-217">アドインをアンインストールする手順は、スタンドアロンのサーバーの場合もサーバー ファームの場合も同じです。</span><span class="sxs-lookup"><span data-stu-id="691ad-217">The steps for uninstalling the add-in are the same for both stand-alone servers and server farms.</span></span> <span data-ttu-id="691ad-218">セットアップにより、インストール時に追加されたプログラム ファイルと構成設定が削除されます。</span><span class="sxs-lookup"><span data-stu-id="691ad-218">Setup will remove program files and any configuration settings that were added during installation.</span></span>

 <span data-ttu-id="691ad-219">アドインをアンインストールしても次のものは削除されません。</span><span class="sxs-lookup"><span data-stu-id="691ad-219">Uninstalling the add-in will not remove the following:</span></span>

-   <span data-ttu-id="691ad-220">SharePoint の構成データベースとコンテンツ データベースへのアクセスに使用される、レポート サーバー サービス アカウント用に作成されたログイン。</span><span class="sxs-lookup"><span data-stu-id="691ad-220">Logins created for the Report Server service account that is used to access the SharePoint configuration and content databases.</span></span> <span data-ttu-id="691ad-221">レポートサーバーサービスアカウントのすべてのログインは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] SharePoint データベースのホストに使用するインスタンスから削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="691ad-221">You must delete any logins for the Report Server service account from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance used to host the SharePoint databases.</span></span>

-   <span data-ttu-id="691ad-222">レポート ユーザー用に作成した権限またはグループ。</span><span class="sxs-lookup"><span data-stu-id="691ad-222">Permissions or groups that you created for report users.</span></span> <span data-ttu-id="691ad-223">レポート サーバーの機能へのアクセスを許可するためにカスタム権限レベルまたは SharePoint グループを作成した場合は、不要になった権限を取り消す必要があります。</span><span class="sxs-lookup"><span data-stu-id="691ad-223">If you created custom permission levels or SharePoint groups to grant access to report server features, you should revoke any permissions that are no longer required.</span></span>

-   <span data-ttu-id="691ad-224">SharePoint ライブラリにアップロードしたデータ ファイル。レポート定義 (.rdl)、共有データ ソース (.rsds)、パブリッシュ済みレポート アイテム (.rsc) などのファイルは</span><span class="sxs-lookup"><span data-stu-id="691ad-224">Data files that you uploaded to a SharePoint library, including report definition (.rdl), shared data source (.rsds), and published report items (.rsc) files.</span></span> <span data-ttu-id="691ad-225">削除されませんが、実行されなくなります。</span><span class="sxs-lookup"><span data-stu-id="691ad-225">They are not deleted, but they will no longer run.</span></span> <span data-ttu-id="691ad-226">これらのファイルは手動で削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="691ad-226">You must delete the files manually.</span></span>

-   <span data-ttu-id="691ad-227">セットアップによって、レポート サーバー データベースが削除されたり、統合操作に使用されていたレポート サーバー インスタンスが変更されることはありません。</span><span class="sxs-lookup"><span data-stu-id="691ad-227">Setup will not delete the report server database or modify the report server instance that was used for integrated operations.</span></span>

### <a name="to-uninstall-from-windows-control-panel"></a><span data-ttu-id="691ad-228">Windows のコントロール パネルからアンインストールを行うには</span><span class="sxs-lookup"><span data-stu-id="691ad-228">To Uninstall from Windows Control Panel</span></span>
 <span data-ttu-id="691ad-229">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のコントロール パネルからウィザードを起動してアドインを削除するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="691ad-229">To start the wizard from [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Control Panel and remove the add-in:</span></span>

1.  <span data-ttu-id="691ad-230">コントロール パネルの **[プログラム]** で、 **[プログラムのアンインストール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="691ad-230">In Control Panel, in **Programs**, select **Uninstall a Program**</span></span>

2.  <span data-ttu-id="691ad-231">**[SharePoint 用 Microsoft SQL Server RS アドイン]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="691ad-231">Select **Microsoft SQL Server RS Add-in for SharePoint**.</span></span> <span data-ttu-id="691ad-232">コマンド プロンプトから、スイッチを指定せずに **rssharepoint.msi** を実行してアンインストール ウィザードを起動することもできます。</span><span class="sxs-lookup"><span data-stu-id="691ad-232">You can also start the uninstall wizard by running **rssharepoint.msi** from the command prompt with no switches.</span></span>

3.  <span data-ttu-id="691ad-233">**[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="691ad-233">Click **Remove**.</span></span>

### <a name="uninstall-from-the-command-line"></a><span data-ttu-id="691ad-234">コマンドラインからアンインストールする</span><span class="sxs-lookup"><span data-stu-id="691ad-234">Uninstall from the command line</span></span>
 <span data-ttu-id="691ad-235">アドインをコマンド ラインからアンインストールするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="691ad-235">To uninstall the add-in from the command line:</span></span>

1.  <span data-ttu-id="691ad-236">**管理者権限を使用して**コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="691ad-236">Open a command prompt **with administrator permissions**.</span></span>

2.  <span data-ttu-id="691ad-237">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="691ad-237">Run the following command:</span></span>

    ```cmd
    msiexec.exe /uninstall rsSharePoint.msi
    ```

3.  <span data-ttu-id="691ad-238">確認メッセージ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="691ad-238">You will see a confirmation message box.</span></span> <span data-ttu-id="691ad-239">**[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="691ad-239">Click **Yes**.</span></span>

### <a name="uninstall-the-add-in-from-the-local-server-only"></a><span data-ttu-id="691ad-240">ローカル サーバーのみからのアドインのアンインストール</span><span class="sxs-lookup"><span data-stu-id="691ad-240">Uninstall the add-in from the local server only</span></span>
 <span data-ttu-id="691ad-241">前に説明したアドインのアンインストール方法では、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の機能とオブジェクトがファームから削除されます。</span><span class="sxs-lookup"><span data-stu-id="691ad-241">The previous methods of uninstalling the add-in will remove the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features and object from the farm.</span></span> <span data-ttu-id="691ad-242">マルチサーバー ファームにおいて、ローカル コンピューターからのみアドインをアンインストールして、SharePoint ファームは稼働させておく場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="691ad-242">If you have a multi-server farm and want to uninstall the add-in from only the local computer and leave the SharePoint farm in a functional state, complete the following steps:</span></span>

1.  <span data-ttu-id="691ad-243">**管理者権限を使用して**コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="691ad-243">Open a command prompt **with administrator permissions**.</span></span>

2.  <span data-ttu-id="691ad-244">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="691ad-244">Run the following command:</span></span>

    ```cmd
    Msiexec.exe /uninstall rsSharePoint.msi LocalOnly=1
    ```

 <span data-ttu-id="691ad-245">これにより、SharePoint から [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コンポーネントの登録が解除され、ファイルが削除されます。ただし対象は、ローカル コンピューターのみです。</span><span class="sxs-lookup"><span data-stu-id="691ad-245">This will unregister the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components from SharePoint and remove the files, but for the local computer only.</span></span>

 <span data-ttu-id="691ad-246">SharePoint から [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の機能の登録を解除するが、後で使用するためにファイルをディスクに残しておくには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="691ad-246">If you want to unregister the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features from SharePoint but leave the files on the disk for use later, complete the following steps:</span></span>

1.  <span data-ttu-id="691ad-247">**管理者権限を使用して**コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="691ad-247">Open a command prompt **with administrator permissions**.</span></span>

2.  <span data-ttu-id="691ad-248">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="691ad-248">Run the following command:</span></span>

    ```cmd
    rsCustomAction.exe /p
    ```

 <span data-ttu-id="691ad-249">上記の手順は、SkipCA=1 で .msi がインストールされていること、および rscusstomaction.exe が使用可能であることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="691ad-249">The above steps assume you completed an installation of the .msi with SkipCA=1 and the rscusstomaction.exe is available.</span></span> <span data-ttu-id="691ad-250">詳細については、ファイルのみのインストールを説明したセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="691ad-250">For more information, see the section describing the files only installation.</span></span>

##  <a name="how-to-repair-rssharepointmsi-from-the-command-line"></a><a name="bkmk_repair"></a><span data-ttu-id="691ad-251">コマンドラインから rssharepoint.msi を修復する方法</span><span class="sxs-lookup"><span data-stu-id="691ad-251">How to Repair rssharepoint.msi from the Command Line</span></span>
 <span data-ttu-id="691ad-252">コマンド ラインを使用して [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインを修復またはアンインストールするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="691ad-252">To repair or uninstall the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in using the command line, complete the following steps:</span></span>

1.  <span data-ttu-id="691ad-253">**管理者権限を使用して**コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="691ad-253">Open a command prompt **with administrator permissions**.</span></span>

2.  <span data-ttu-id="691ad-254">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="691ad-254">Run the following command:</span></span>

    ```cmd
    msiexec.exe /f rssharepoint.msi
    ```

##  <a name="setup-log-files"></a><a name="bkmk_logfiles"></a><span data-ttu-id="691ad-255">セットアップログファイル</span><span class="sxs-lookup"><span data-stu-id="691ad-255">Setup Log Files</span></span>
 <span data-ttu-id="691ad-256">セットアップの実行中は、 **アドインをインストールしたユーザーの** %temp% [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] フォルダー内のログ ファイルに情報が記録されます。</span><span class="sxs-lookup"><span data-stu-id="691ad-256">When Setup runs, it logs information to a log file in the **%temp%** folder for the user who installed the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in.</span></span> <span data-ttu-id="691ad-257">たとえば、 **c:\Users \\<username \> \AppData\Local\Temp**のようになります。ファイル名は**RS_SP_ \<number> .log**( **RS_SP_0 .log**など) です。</span><span class="sxs-lookup"><span data-stu-id="691ad-257">For example **c:\Users\\<username\>\AppData\Local\Temp** .The file name is **RS_SP_\<number>.log**, for example **RS_SP_0.log**.</span></span> <span data-ttu-id="691ad-258">ログ内では、エラーは "SSRSCustomActionError" という文字列から始まります。</span><span class="sxs-lookup"><span data-stu-id="691ad-258">Each error in the log starts with the string "SSRSCustomActionError".</span></span>

> [!NOTE]
>  <span data-ttu-id="691ad-259">AppData は Windows オペレーティング システム内の隠れたフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="691ad-259">AppData is a hidden folder in the Windows operating system.</span></span> <span data-ttu-id="691ad-260">隠れたファイルとフォルダーを表示するには、Windows エクスプローラーのフォルダー設定を変更する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="691ad-260">You may need to modify your Windows Explorer folder settings so you can see hidden files and folders.</span></span>

#### <a name="view-a-log-file-with-windows-notepad"></a><span data-ttu-id="691ad-261">Windows メモ帳でのログ ファイルの表示</span><span class="sxs-lookup"><span data-stu-id="691ad-261">View a log file with Windows Notepad</span></span>

1.  <span data-ttu-id="691ad-262">次のコマンドは、コマンド プロンプトのパスを変更し、rs ログ ファイルを一覧表示し、Windows メモ帳でそれらのファイルの 1 つを表示します。</span><span class="sxs-lookup"><span data-stu-id="691ad-262">The following commands will change the command prompt path, list the rs log files and then open one of the files with Windows Notepad:</span></span>

    ```cmd
    cd %temp%
    ```

    ```cmd
    dir rs_sp*.log
    ```

    ```cmd
    notepad rs_sp_3.log
    ```

#### <a name="view-a-log-file-with-powershell"></a><span data-ttu-id="691ad-263">PowerShell でのログ ファイルの表示</span><span class="sxs-lookup"><span data-stu-id="691ad-263">View a Log file with PowerShell</span></span>

1.  <span data-ttu-id="691ad-264">SharePoint 管理シェルから次のコマンドを入力すると、フィルター選択された "ssrscustomactionerror" を含む行の一覧がファイルから返されます。</span><span class="sxs-lookup"><span data-stu-id="691ad-264">Type the following command from the SharePoint Management Shell to return a filtered list of rows from the file, that contain "ssrscustomactionerror":</span></span>

    ```powershell
    Get-Content -Path C:\Users\<UserName\AppData\Local\Temp\rs_sp_0.log | Select-String "ssrscustomactionerror"
    ```

2.  <span data-ttu-id="691ad-265">出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="691ad-265">The output will look similar to the following:</span></span>

     <span data-ttu-id="691ad-266">`2011-05-23 12:40:12: SSRSCustomActionError: SharePoint is installed, but not configured`.</span><span class="sxs-lookup"><span data-stu-id="691ad-266">`2011-05-23 12:40:12: SSRSCustomActionError: SharePoint is installed, but not configured`.</span></span>

##  <a name="upgrade"></a><a name="bkmk_upgrade"></a><span data-ttu-id="691ad-267">増設</span><span class="sxs-lookup"><span data-stu-id="691ad-267">Upgrade</span></span>
 <span data-ttu-id="691ad-268">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインの既存のバージョンがインストールされている場合は、最新のバージョンにアップグレードできます。</span><span class="sxs-lookup"><span data-stu-id="691ad-268">If you have an existing installation of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in, you can upgrade to the current version.</span></span> <span data-ttu-id="691ad-269">アドイン セットアップ時に既存のバージョンが検出され、更新するかどうかを確認するメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="691ad-269">The add-in setup will detect the existing version and prompt you to confirm the update.</span></span> <span data-ttu-id="691ad-270">エラー メッセージは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="691ad-270">The message will be similar to the following:</span></span>

 <span data-ttu-id="691ad-271">**この製品の古いバージョンがシステムで検出されました。既存のインストールをアップグレードしますか?**</span><span class="sxs-lookup"><span data-stu-id="691ad-271">**A Lower version of this product has been detected on your system. Would you like to upgrade your existing installation?**</span></span>

 <span data-ttu-id="691ad-272">確認すると、アドインの古いバージョンが削除され、新しいバージョンがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="691ad-272">If you confirm, the older version of the add-in will be removed and then the new version will be installed.</span></span>

 <span data-ttu-id="691ad-273">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインはインスタンス対応ではありません。</span><span class="sxs-lookup"><span data-stu-id="691ad-273">Note that the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in is not instance-aware.</span></span> <span data-ttu-id="691ad-274">このアドインのインスタンスは 1 台のコンピューターで 1 つだけ実行できます。</span><span class="sxs-lookup"><span data-stu-id="691ad-274">You can only have one instance of the add-in on a computer.</span></span> <span data-ttu-id="691ad-275">異なるバージョンと現在のバージョンとを同時に実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="691ad-275">You cannot run different versions side-by-side the current version.</span></span>

##  <a name="rscustomactionexe"></a><a name="bkmk_rscustomaction"></a><span data-ttu-id="691ad-276">RsCustomAction.exe</span><span class="sxs-lookup"><span data-stu-id="691ad-276">RsCustomAction.exe</span></span>
 <span data-ttu-id="691ad-277">次の表は、rscustomaction.exe スイッチについてまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="691ad-277">The following table summarizes the rscustomaction.exe switches:</span></span>

|<span data-ttu-id="691ad-278">Switch</span><span class="sxs-lookup"><span data-stu-id="691ad-278">Switch</span></span>|<span data-ttu-id="691ad-279">説明</span><span class="sxs-lookup"><span data-stu-id="691ad-279">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="691ad-280">i</span><span class="sxs-lookup"><span data-stu-id="691ad-280">i</span></span>|<span data-ttu-id="691ad-281">カスタム アクションをインストールします。</span><span class="sxs-lookup"><span data-stu-id="691ad-281">Install the custom actions.</span></span> <span data-ttu-id="691ad-282">これにより、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コンポーネントが SharePoint に登録されます。</span><span class="sxs-lookup"><span data-stu-id="691ad-282">This will register the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components in SharePoint.</span></span> <span data-ttu-id="691ad-283">W3SVCservice サービスが再起動されます。</span><span class="sxs-lookup"><span data-stu-id="691ad-283">This will restart the W3SVCservice.</span></span>|
|<span data-ttu-id="691ad-284">r</span><span class="sxs-lookup"><span data-stu-id="691ad-284">r</span></span>|<span data-ttu-id="691ad-285">修復</span><span class="sxs-lookup"><span data-stu-id="691ad-285">Repair</span></span>|
|<span data-ttu-id="691ad-286">u</span><span class="sxs-lookup"><span data-stu-id="691ad-286">u</span></span>|<span data-ttu-id="691ad-287">アンインストール。</span><span class="sxs-lookup"><span data-stu-id="691ad-287">Uninstall.</span></span> <span data-ttu-id="691ad-288">これにより、SharePoint ファーム全体から [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コンポーネントの登録が解除されますが、ファイルはディスクに残ります。</span><span class="sxs-lookup"><span data-stu-id="691ad-288">This will unregister the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components from the entire SharePoint farm but leave the files on disk.</span></span> <span data-ttu-id="691ad-289">W3SVCservice サービスが再起動されます。</span><span class="sxs-lookup"><span data-stu-id="691ad-289">This will restart the W3SVCservice.</span></span>|
|<span data-ttu-id="691ad-290">p</span><span class="sxs-lookup"><span data-stu-id="691ad-290">p</span></span>|<span data-ttu-id="691ad-291">ローカル アンインストール。</span><span class="sxs-lookup"><span data-stu-id="691ad-291">Local uninstall.</span></span> <span data-ttu-id="691ad-292">これにより、ローカル コンピューターのみから [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コンポーネントの登録が解除されます。</span><span class="sxs-lookup"><span data-stu-id="691ad-292">This will unregister the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components from only the local computer.</span></span> <span data-ttu-id="691ad-293">ファイルはディスクに残ります。</span><span class="sxs-lookup"><span data-stu-id="691ad-293">The files will remain on disk.</span></span> <span data-ttu-id="691ad-294">W3SVCservice サービスが再起動されます。</span><span class="sxs-lookup"><span data-stu-id="691ad-294">This will restart the W3SVCservice.</span></span>|
|<span data-ttu-id="691ad-295">t</span><span class="sxs-lookup"><span data-stu-id="691ad-295">t</span></span>|<span data-ttu-id="691ad-296">SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 2005 のみ。</span><span class="sxs-lookup"><span data-stu-id="691ad-296">SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 2005 only.</span></span> <span data-ttu-id="691ad-297">レポート サーバーにレポート サーバー データベースに対して機能する接続があるかどうかをテストします。</span><span class="sxs-lookup"><span data-stu-id="691ad-297">The switch tests if the report server has a working connection to the report server database.</span></span>|

## <a name="configuring-reporting-services"></a><span data-ttu-id="691ad-298">Reporting Services の構成</span><span class="sxs-lookup"><span data-stu-id="691ad-298">Configuring Reporting Services</span></span>
 <span data-ttu-id="691ad-299">必要なコンピューターにアドインをインストールしたら、SharePoint サーバーの全体管理からレポート サーバーを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="691ad-299">After you have installed the add-in on all the necessary computers, you need to configure the report server from SharePoint Central Administration.</span></span> <span data-ttu-id="691ad-300">必要な手順は、さまざまなテクノロジがインストールされた順序によって異なります。</span><span class="sxs-lookup"><span data-stu-id="691ad-300">The steps that are needed depend on the order which the different technologies were installed.</span></span> <span data-ttu-id="691ad-301">詳細については、「sharepoint [2010 用 Reporting Services Sharepoint モードをインストールする](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)」および「sharepoint[モードのレポートサーバーの Reporting Services &#40;](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md) 」を参照してください&#41;</span><span class="sxs-lookup"><span data-stu-id="691ad-301">For more information, see [Install Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md) and [Reporting Services Report Server &#40;SharePoint Mode&#41;](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="691ad-302">参照</span><span class="sxs-lookup"><span data-stu-id="691ad-302">See Also</span></span>
 <span data-ttu-id="691ad-303">Sharepoint 2010 [Reporting Services レポートサーバー &#40;Sharepoint モード](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md)[の Sharepoint モードをインストール Reporting Services](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)&#41;</span><span class="sxs-lookup"><span data-stu-id="691ad-303">[Install Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md) [Reporting Services Report Server &#40;SharePoint Mode&#41;](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md)</span></span>
