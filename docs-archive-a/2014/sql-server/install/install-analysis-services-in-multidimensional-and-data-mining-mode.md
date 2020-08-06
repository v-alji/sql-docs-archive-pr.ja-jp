---
title: 多次元およびデータマイニングモードでの Analysis Services のインストール |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Analysis Services, about installing Analysis Services
- installing Analysis Services
- SSAS, installing
- Analysis Services, installing
- SQL Server Analysis Services, installing
ms.assetid: 8a1f33e8-2bd6-4fb8-bd46-c86f2a067f60
author: heidisteen
ms.author: heidist
ms.openlocfilehash: e88d4440a65392b4f6351fa2503ea7819cf528b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632288"
---
# <a name="install-analysis-services-in-multidimensional-and-data-mining-mode"></a><span data-ttu-id="6b00f-102">多次元モードおよびデータ マイニング モードでの Analysis Services のインストール</span><span class="sxs-lookup"><span data-stu-id="6b00f-102">Install Analysis Services in Multidimensional and Data Mining Mode</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="6b00f-103">には、ビジネス インテリジェンス アプリケーション用のオンライン分析処理 (OLAP) 機能とデータ マイニング機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="6b00f-103">provides online analytical processing (OLAP) and data mining functionality for business intelligence applications.</span></span> <span data-ttu-id="6b00f-104">このリリースでは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] *多次元モード*でをインストールするときに、OLAP データベースとデータマイニングモデルのサポートを利用できます。</span><span class="sxs-lookup"><span data-stu-id="6b00f-104">In this release, support for OLAP databases and data mining models is available when you install [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in *Multidimensional mode*.</span></span> <span data-ttu-id="6b00f-105">多次元モードは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] が実行される 3 つのサーバー モードのうちの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="6b00f-105">Multidimensional mode is one of three server modes that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] runs in.</span></span> <span data-ttu-id="6b00f-106">これは既定のモードです。</span><span class="sxs-lookup"><span data-stu-id="6b00f-106">It is the default mode.</span></span> <span data-ttu-id="6b00f-107">既定値を使用して [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] をインストールすると、多次元データベースとデータ マイニング モデルを実行するインスタンスがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="6b00f-107">If you install [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] using default values, you will get an instance that runs multidimensional databases and data mining models.</span></span>  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="6b00f-108">は複数インスタンスに対応します。つまり、1 台のコンピューターに複数の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスをインストールすることも、新しいバージョンの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスを古いバージョンと共存して実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="6b00f-108">is a multi-instance feature, which means that you can install more than one instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] on a single computer, or run a new instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] side-by-side an earlier version.</span></span> <span data-ttu-id="6b00f-109">サーバー モードはインスタンスに固有です。</span><span class="sxs-lookup"><span data-stu-id="6b00f-109">Server mode is specific to an instance.</span></span> <span data-ttu-id="6b00f-110">他のモードを使用するには、サーバーの追加インスタンスをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b00f-110">Using other modes requires that you install additional instances of the server.</span></span>  
  
 <span data-ttu-id="6b00f-111">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、単体でインストールすることも、他のコンポーネントと共にインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="6b00f-111">You can install [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] by itself or with other components.</span></span> <span data-ttu-id="6b00f-112">だけをインストールする場合は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インストールウィザードの [機能の選択] ページで [ **Analysis Services** ] を選択すると、次の機能がインストールされ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="6b00f-112">If you install just [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the following features are installed when you select **Analysis Services** on the Feature Selection page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard:</span></span>  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="6b00f-113">データベースとデータ マイニング モデルを実行するための [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバー</span><span class="sxs-lookup"><span data-stu-id="6b00f-113">server for running [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases and data mining models</span></span>  
  
-   <span data-ttu-id="6b00f-114">ソース データベースへの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データのアクセスに使用されるデータ プロバイダー</span><span class="sxs-lookup"><span data-stu-id="6b00f-114">Data providers used for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data access to source databases</span></span>  
  
-   <span data-ttu-id="6b00f-115">SQL Server 構成マネージャー</span><span class="sxs-lookup"><span data-stu-id="6b00f-115">SQL Server Configuration Manager</span></span>  
  
## <a name="choosing-additional-features"></a><span data-ttu-id="6b00f-116">追加機能の選択</span><span class="sxs-lookup"><span data-stu-id="6b00f-116">Choosing additional features</span></span>  
 <span data-ttu-id="6b00f-117">Analysis Services OLAP およびデータ ウェアハウス ソリューションでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースの開発、配置、および管理を可能にするためにその他の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] コンポーネントもインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b00f-117">Analysis Services OLAP and data warehouse solutions will require the installation of additional [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components to enable the development, deployment, and administration of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases.</span></span> <span data-ttu-id="6b00f-118">一般的なユーザー シナリオでは、データベース サービスに加えて次の機能もインストールします。</span><span class="sxs-lookup"><span data-stu-id="6b00f-118">The following additional features are options for many typical user scenarios:</span></span>  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="6b00f-119">: Analysis Services データ構造およびデータ マイニング モデルの作成と表示に使用されます。</span><span class="sxs-lookup"><span data-stu-id="6b00f-119">, used to create and view Analysis Services data structures and data mining models.</span></span>  
  
-   <span data-ttu-id="6b00f-120">クライアント ツール接続コンポーネント: クライアントとサーバー間の通信に使用されます。DB-Library、ODBC、OLE DB 向けのネットワーク ライブラリなどが該当します。</span><span class="sxs-lookup"><span data-stu-id="6b00f-120">Client tools connectivity components, used for communication between clients and servers, including network libraries for DB-Library, ODBC, and OLE DB.</span></span>  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]<span data-ttu-id="6b00f-121">: データの移動、コピー、および変換に使用される、グラフィカル オブジェクトおよびプログラミング可能なオブジェクトのセットです。</span><span class="sxs-lookup"><span data-stu-id="6b00f-121">, a set of graphical and programmable objects for moving, copying, and transforming data.</span></span>  
  
-   <span data-ttu-id="6b00f-122">管理ツール: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャー、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]、レプリケーション モニターなどです。</span><span class="sxs-lookup"><span data-stu-id="6b00f-122">Management tools, including [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], and Replication Monitor.</span></span>  
  
## <a name="installation-tasks"></a><span data-ttu-id="6b00f-123">インストール作業</span><span class="sxs-lookup"><span data-stu-id="6b00f-123">Installation Tasks</span></span>  
 <span data-ttu-id="6b00f-124">インストール作業では、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="6b00f-124">Installation tasks include the following:</span></span>  
  
|<span data-ttu-id="6b00f-125">リンク</span><span class="sxs-lookup"><span data-stu-id="6b00f-125">Links</span></span>|<span data-ttu-id="6b00f-126">タスク</span><span class="sxs-lookup"><span data-stu-id="6b00f-126">Tasks</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="6b00f-127">SQL Server 2014 をインストールし、 [Windows サービスアカウントとアクセス許可を構成](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)する[ためのハードウェアとソフトウェアの要件](hardware-and-software-requirements-for-installing-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="6b00f-127">[Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>|<span data-ttu-id="6b00f-128">セットアップを実行する前に、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインストールの前提条件を確認し、サーバーの準備に使用するアカウントを決定します。</span><span class="sxs-lookup"><span data-stu-id="6b00f-128">Before you run Setup, check prerequisites for installing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and determine which account you will use to provision the server.</span></span>|  
|<span data-ttu-id="6b00f-129">[インストールウィザード &#40;セットアップ&#41;から SQL Server 2014 をインストール](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)します。</span><span class="sxs-lookup"><span data-stu-id="6b00f-129">[Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).</span></span>|<span data-ttu-id="6b00f-130">SQL Server セットアップを実行して、ソフトウェアをインストールします。</span><span class="sxs-lookup"><span data-stu-id="6b00f-130">Run SQL Server Setup to install the software.</span></span>|  
|[<span data-ttu-id="6b00f-131">Analysis Services のアクセスを許可するための Windows ファイアウォールの構成</span><span class="sxs-lookup"><span data-stu-id="6b00f-131">Configure the Windows Firewall to Allow Analysis Services Access</span></span>](https://docs.microsoft.com/analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access)|<span data-ttu-id="6b00f-132">セットアップが完了したら、ファイアウォールの設定を構成して、サーバーに対するリモート接続を許可する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b00f-132">After Setup is finished, you must configure firewall settings to allow remote connections to the server.</span></span>|  
|[<span data-ttu-id="6b00f-133">オブジェクトと操作へのアクセスの承認 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6b00f-133">Authorizing access to objects and operations &#40;Analysis Services&#41;</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services)|<span data-ttu-id="6b00f-134">Analysis Services データベースにアクセスするユーザーには、サーバー上の少なくとも 1 つのデータベースに対する読み取り権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="6b00f-134">Users who access Analysis Services databases must have Read permission on at least one database on the server.</span></span>|  
  
## <a name="related-content"></a><span data-ttu-id="6b00f-135">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="6b00f-135">Related Content</span></span>  
 <span data-ttu-id="6b00f-136">その他のセットアップ コンテンツは次のトピックで確認できます。</span><span class="sxs-lookup"><span data-stu-id="6b00f-136">Additional setup content can be found in the following topics:</span></span>  
  
 [<span data-ttu-id="6b00f-137">表形式モードでの Analysis Services のインストール</span><span class="sxs-lookup"><span data-stu-id="6b00f-137">Install Analysis Services in Tabular Mode</span></span>](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services)  
  
 [<span data-ttu-id="6b00f-138">PowerPivot for SharePoint 2010 のインストール</span><span class="sxs-lookup"><span data-stu-id="6b00f-138">PowerPivot for SharePoint 2010 Installation</span></span>](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
 [<span data-ttu-id="6b00f-139">Analysis Services インスタンスのサーバー モードの決定</span><span class="sxs-lookup"><span data-stu-id="6b00f-139">Determine the Server Mode of an Analysis Services Instance</span></span>](https://docs.microsoft.com/analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance)  
  
 [<span data-ttu-id="6b00f-140">データマイニングアドインの SQL Server</span><span class="sxs-lookup"><span data-stu-id="6b00f-140">SQL Server Data Mining Add-ins</span></span>](https://www.microsoft.com/download/details.aspx?id=35578)  
  
 <span data-ttu-id="6b00f-141">既定では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップ時にサンプル データベース、サンプル コード、およびクライアント アプリケーション アドインはインストールされません。</span><span class="sxs-lookup"><span data-stu-id="6b00f-141">By default, sample databases, sample code, and client application add-ins are not installed as part of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup.</span></span> <span data-ttu-id="6b00f-142">サンプル データベースとサンプル コードをインストールする場合は、 [CodePlex Web サイト](https://go.microsoft.com/fwlink/?LinkId=87843)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b00f-142">To install sample databases and sample code, see the [CodePlex Web site](https://go.microsoft.com/fwlink/?LinkId=87843).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b00f-143">参照</span><span class="sxs-lookup"><span data-stu-id="6b00f-143">See Also</span></span>  
 <span data-ttu-id="6b00f-144">[SQL Server 2012 の各エディションがサポートする機能](https://go.microsoft.com/fwlink/?linkid=232473) </span><span class="sxs-lookup"><span data-stu-id="6b00f-144">[Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) </span></span>  
 <span data-ttu-id="6b00f-145">[言語と照合順序 &#40;Analysis Services&#41;](../../../2014/analysis-services/languages-and-collations-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="6b00f-145">[Languages and Collations &#40;Analysis Services&#41;](../../../2014/analysis-services/languages-and-collations-analysis-services.md) </span></span>  
 [<span data-ttu-id="6b00f-146">Analysis Services のアップグレード</span><span class="sxs-lookup"><span data-stu-id="6b00f-146">Upgrade Analysis Services</span></span>](../../database-engine/install-windows/upgrade-analysis-services.md)  
  
  
