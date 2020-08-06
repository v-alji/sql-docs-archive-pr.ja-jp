---
title: SQL Server 2014 | のインストールMicrosoft Docs
ms.custom: ''
ms.date: 09/09/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
f1_keywords:
- sql12.portal.Installation.f1
helpviewer_keywords:
- installing SQL Server, initial installation
- installation [SQL Server]
- initial installation [SQL Server]
ms.assetid: edd75f68-dc62-4479-a596-57ce8ad632e5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 62630400f276b00de8acfa875244558cdb39e47b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713429"
---
# <a name="installation-for-sql-server-2014"></a><span data-ttu-id="276a6-102">SQL Server 2014 のインストール</span><span class="sxs-lookup"><span data-stu-id="276a6-102">Installation for SQL Server 2014</span></span>
 ## <a name="download-sql-server-2014-express"></a>[<span data-ttu-id="276a6-103">SQL Server 2014 Express のダウンロード</span><span class="sxs-lookup"><span data-stu-id="276a6-103">Download SQL Server 2014 Express</span></span>](http://www.hanselman.com/blog/DownloadSQLServerExpress.aspx)
  <span data-ttu-id="276a6-104">**すべてのインストーラーパッケージリンクを1か所で収集するために、 [Scott](http://www.hanselman.com/)マンマンに感謝します。**</span><span class="sxs-lookup"><span data-stu-id="276a6-104">**Thank you to [Scott Hanselman](http://www.hanselman.com/) for collecting all of the installer package links in one place!**</span></span>
  
  <span data-ttu-id="276a6-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール ウィザードの 1 つの機能ツリーから、次のすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="276a6-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard provides a single feature tree to install all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components:</span></span>  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]  
  
-   [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)]  
  
-   <span data-ttu-id="276a6-106">管理ツール</span><span class="sxs-lookup"><span data-stu-id="276a6-106">Management tools</span></span>  
  
-   <span data-ttu-id="276a6-107">接続コンポーネント</span><span class="sxs-lookup"><span data-stu-id="276a6-107">Connectivity components</span></span>  
  
 <span data-ttu-id="276a6-108">各コンポーネントを個別にインストールするか、上記のコンポーネントを組み合わせて選択できます。</span><span class="sxs-lookup"><span data-stu-id="276a6-108">You can install each component individually or select a combination of the components listed above.</span></span> <span data-ttu-id="276a6-109">で使用できるエディションとコンポーネントを選択するには [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、 [SQL Server 2014 のエディションとコンポーネント](../../sql-server/editions-and-components-of-sql-server-2016.md)、および[SQL Server 2014 の各エディションがサポートする機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="276a6-109">To make the best choice among the editions and components available in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Editions and Components of SQL Server 2014](../../sql-server/editions-and-components-of-sql-server-2016.md) and [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="276a6-110">には 32 ビット版と 64 ビット版があります。</span><span class="sxs-lookup"><span data-stu-id="276a6-110">is available in 32-bit and 64-bit editions.</span></span>
 
 <span data-ttu-id="276a6-111">**試してみてください。**</span><span class="sxs-lookup"><span data-stu-id="276a6-111">**Try it out:**</span></span>  
  
-   <span data-ttu-id="276a6-112">Azure アカウントをすでにお持ちですか?</span><span class="sxs-lookup"><span data-stu-id="276a6-112">Have an Azure account?</span></span>  <span data-ttu-id="276a6-113">次に、SQL Server 2014 Service Pack 1 (SP1) が既にインストールされている仮想マシンを起動するに**[は、ここ](https://ms.portal.azure.com/?flight=1#create/Microsoft.SQLServer2016RTMEnterpriseWindowsServer2012R2)** にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="276a6-113">Then go **[Here](https://ms.portal.azure.com/?flight=1#create/Microsoft.SQLServer2016RTMEnterpriseWindowsServer2012R2)** to spin up a Virtual Machine with SQL Server 2014 Service Pack 1 (SP1) already installed.</span></span> <span data-ttu-id="276a6-114">SQL Server 2014 (SP1) の詳細については、「 [SQL Server 2014 Service Pack 1 のリリース情報](https://support.microsoft.com/kb/3058865)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="276a6-114">For more information on SQL Server 2014 (SP1), see [SQL Server 2014 Service Pack 1 release information](https://support.microsoft.com/kb/3058865).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="276a6-115">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="276a6-115">In This Section</span></span>  
 <span data-ttu-id="276a6-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール ウィザードを使用する場合でも、コマンド プロンプトから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をインストールする場合でも、セットアップ時には以下の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="276a6-116">Regardless of whether you use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard or the command prompt to install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Setup involves the following steps:</span></span>  
  
 [<span data-ttu-id="276a6-117">SQL Server のインストール計画</span><span class="sxs-lookup"><span data-stu-id="276a6-117">Planning a SQL Server Installation</span></span>](../../sql-server/install/planning-a-sql-server-installation.md)  
 <span data-ttu-id="276a6-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]用にコンピューターを準備する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="276a6-118">Describes how to prepare your computer for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="276a6-119">ハードウェアとソフトウェアの要件</span><span class="sxs-lookup"><span data-stu-id="276a6-119">Hardware and software requirements.</span></span>  
  
-   <span data-ttu-id="276a6-120">システム構成チェッカーの要件とブロックの問題</span><span class="sxs-lookup"><span data-stu-id="276a6-120">System Configuration Checker requirements and blocking issues.</span></span>  
  
-   <span data-ttu-id="276a6-121">セキュリティに関する注意点</span><span class="sxs-lookup"><span data-stu-id="276a6-121">Security considerations.</span></span>  
  
 [<span data-ttu-id="276a6-122">SQL Server 2014 のインストール</span><span class="sxs-lookup"><span data-stu-id="276a6-122">Install SQL Server 2014</span></span>](install-sql-server.md)  
 <span data-ttu-id="276a6-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインストール オプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="276a6-123">Describes installation options for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="276a6-124">SQL Server 2014 へのアップグレード</span><span class="sxs-lookup"><span data-stu-id="276a6-124">Upgrade to SQL Server 2014</span></span>](upgrade-sql-server.md)  
 <span data-ttu-id="276a6-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]にアップグレードするためのオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="276a6-125">Describes options for upgrading to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="276a6-126">SQL Server 2014 のアンインストール</span><span class="sxs-lookup"><span data-stu-id="276a6-126">Uninstall SQL Server 2014</span></span>](../../sql-server/install/uninstall-sql-server.md)  
 <span data-ttu-id="276a6-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]のアンインストール手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="276a6-127">Describes procedures to uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].</span></span>  
  
 [<span data-ttu-id="276a6-128">SQL Server フェールオーバー クラスターのインストール</span><span class="sxs-lookup"><span data-stu-id="276a6-128">SQL Server Failover Cluster Installation</span></span>](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)  
 <span data-ttu-id="276a6-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップ ドキュメントのこのセクションでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスターをインストールして構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="276a6-129">This section of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup documentation explains how to install, and configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster.</span></span>  
  
 [<span data-ttu-id="276a6-130">SQL Server 2014 の BI 機能のインストール</span><span class="sxs-lookup"><span data-stu-id="276a6-130">Install SQL Server 2014 BI Features</span></span>](../../sql-server/install/install-sql-server-business-intelligence-features.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="276a6-131">で Microsoft BI プラットフォームに含まれる機能には、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]、および分析データの作成または操作に使用されるいくつかのクライアント アプリケーションがあります。</span><span class="sxs-lookup"><span data-stu-id="276a6-131">features that are part of the Microsoft BI platform include [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], and several client applications used for creating or working with analytical data.</span></span> <span data-ttu-id="276a6-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップ ドキュメントのこのセクションでは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] および [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]のインストール方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="276a6-132">This section of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup documentation explains how to install [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="276a6-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="276a6-133">Related Sections</span></span>  
 [<span data-ttu-id="276a6-134">インストール方法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="276a6-134">Installation How-to Topics</span></span>](../../sql-server/install/installation-how-to-topics.md)  
 <span data-ttu-id="276a6-135">インストール ウィザード、コマンド プロンプト、構成ファイル、および SysPrep を使用して [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] をインストールするための手順に関するトピックへのリンクが記載されています。</span><span class="sxs-lookup"><span data-stu-id="276a6-135">Provides links to procedural topics for installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] from the installation wizard, from the command prompt, by using configuration files, and by using SysPrep.</span></span>  
  
 [<span data-ttu-id="276a6-136">SharePoint &#40;PowerPivot および Reporting Services の SQL Server BI 機能のインストール&#41;</span><span class="sxs-lookup"><span data-stu-id="276a6-136">Install SQL Server BI Features with SharePoint &#40;PowerPivot and Reporting Services&#41;</span></span>](../../sql-server/install/install-sql-server-bi-features-sharepoint-powerpivot-reporting-services.md)  
 <span data-ttu-id="276a6-137">このセクションでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能を SharePoint 環境でインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="276a6-137">This section explains how to install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features in a SharePoint environment.</span></span> <span data-ttu-id="276a6-138">ここでは、特定のバージョンとエディションの SharePoint で使用できる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能を示します。</span><span class="sxs-lookup"><span data-stu-id="276a6-138">It identifies which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features are available given a specific version and edition of SharePoint.</span></span> <span data-ttu-id="276a6-139">また、PowerPivot for SharePoint と Reporting Services を SharePoint モードでインストールする手順についても説明します。</span><span class="sxs-lookup"><span data-stu-id="276a6-139">It also includes installation procedures for PowerPivot for SharePoint and Reporting Services in SharePoint mode.</span></span>  
  
 [<span data-ttu-id="276a6-140">SQL Server のサンプルとサンプル データベースのインストール</span><span class="sxs-lookup"><span data-stu-id="276a6-140">Installing SQL Server Samples and Sample Databases</span></span>](https://sqlserversamples.codeplex.com/)  
 <span data-ttu-id="276a6-141">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のサンプルおよびサンプル データベースをインストールして構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="276a6-141">Describes how to install and configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] samples and sample databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="276a6-142">参照</span><span class="sxs-lookup"><span data-stu-id="276a6-142">See Also</span></span>  
 <span data-ttu-id="276a6-143">[SQL Server インストールの新機能](../../sql-server/install/what-s-new-in-sql-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="276a6-143">[What's New in SQL Server Installation](../../sql-server/install/what-s-new-in-sql-server-installation.md) </span></span>  
 [<span data-ttu-id="276a6-144">SQL Server 2014 のインストールに必要なハードウェアおよびソフトウェア</span><span class="sxs-lookup"><span data-stu-id="276a6-144">Hardware and Software Requirements for Installing SQL Server 2014</span></span>](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
