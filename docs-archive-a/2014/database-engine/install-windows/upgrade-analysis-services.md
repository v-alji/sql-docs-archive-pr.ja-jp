---
title: Analysis Services のアップグレード | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- upgrading databases
- databases [Analysis Services], upgrading
- installing Analysis Services, side-by-side installations
- Analysis Services upgrades
- Analysis Services upgrades, about upgrading Analysis Services
- SSAS, database migration
- upgrading Analysis Services
- installing Analysis Services, upgrading
- SSAS, upgrading
ms.assetid: a131d329-386e-4470-aaa9-ffcde4e5ec0c
author: Minewiskan
ms.author: owend
ms.openlocfilehash: 78bf7f27233bcfd46bc1f189324eddc72adcc961
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634622"
---
# <a name="upgrade-analysis-services"></a><span data-ttu-id="93e07-102">Analysis Services のアップグレード</span><span class="sxs-lookup"><span data-stu-id="93e07-102">Upgrade Analysis Services</span></span>
  <span data-ttu-id="93e07-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="93e07-103">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup to upgrade [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="93e07-104">SharePoint モードでのアップグレードの詳細につい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ては、「 [Upgrade PowerPivot for SharePoint](upgrade-power-pivot-for-sharepoint.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93e07-104">For detailed information on upgrading [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in SharePoint mode, see [Upgrade PowerPivot for SharePoint](upgrade-power-pivot-for-sharepoint.md).</span></span> <span data-ttu-id="93e07-105">既存の SQL Server インスタンスのアップグレードの詳細については、[インストールウィザードを使用した SQL Server 2014 へのアップグレード &#40;のセットアップ&#41;を](upgrade-sql-server-using-the-installation-wizard-setup.md)参照してください。</span><span class="sxs-lookup"><span data-stu-id="93e07-105">For more information about upgrading an existing SQL Server instance, see [Upgrade to SQL Server 2014 Using the Installation Wizard &#40;Setup&#41;](upgrade-sql-server-using-the-installation-wizard-setup.md).</span></span>  
  
## <a name="known-upgrade-issues"></a><span data-ttu-id="93e07-106">アップグレードに関する既知の問題</span><span class="sxs-lookup"><span data-stu-id="93e07-106">Known Upgrade Issues</span></span>  
 <span data-ttu-id="93e07-107">にアップグレードする前に [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、次の内容を確認してください。</span><span class="sxs-lookup"><span data-stu-id="93e07-107">Before upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], review the following:</span></span>  
  
-   <span data-ttu-id="93e07-108">[SQL Server 2014 リリースノート](https://go.microsoft.com/fwlink/?LinkID=296445)。</span><span class="sxs-lookup"><span data-stu-id="93e07-108">[SQL Server 2014 Release Notes](https://go.microsoft.com/fwlink/?LinkID=296445).</span></span>  
  
-   <span data-ttu-id="93e07-109">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]廃止、非推奨、または変更された機能の詳細については、「 [Analysis Services 旧バージョン](https://docs.microsoft.com/analysis-services/analysis-services-backward-compatibility)との互換性」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93e07-109">To learn which [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] features and functionality have been discontinued, deprecated, or changed see [Analysis Services Backward Compatibility](https://docs.microsoft.com/analysis-services/analysis-services-backward-compatibility).</span></span>  
  
## <a name="pre-upgrade-checklist"></a><span data-ttu-id="93e07-110">アップグレード前のチェック リスト</span><span class="sxs-lookup"><span data-stu-id="93e07-110">Pre-Upgrade Checklist</span></span>  
 <span data-ttu-id="93e07-111">アップグレードの前に、次の情報を確認してください。</span><span class="sxs-lookup"><span data-stu-id="93e07-111">Before upgrading, review the following information:</span></span>  
  
-   [<span data-ttu-id="93e07-112">サポートされているバージョンとエディションのアップグレード</span><span class="sxs-lookup"><span data-stu-id="93e07-112">Supported Version and Edition Upgrades</span></span>](supported-version-and-edition-upgrades.md)  
  
-   [<span data-ttu-id="93e07-113">SQL Server 2014 のインストールに必要なハードウェアおよびソフトウェア</span><span class="sxs-lookup"><span data-stu-id="93e07-113">Hardware and Software Requirements for Installing SQL Server 2014</span></span>](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
-   [<span data-ttu-id="93e07-114">システム構成チェッカーの検査パラメーター</span><span class="sxs-lookup"><span data-stu-id="93e07-114">Check Parameters for the System Configuration Checker</span></span>](check-parameters-for-the-system-configuration-checker.md)  
  
-   [<span data-ttu-id="93e07-115">SQL Server インストールにおけるセキュリティの考慮事項</span><span class="sxs-lookup"><span data-stu-id="93e07-115">Security Considerations for a SQL Server Installation</span></span>](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
-   [<span data-ttu-id="93e07-116">Analysis Services データベースのバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="93e07-116">Backup and Restore of Analysis Services Databases</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases)  
  
-   [<span data-ttu-id="93e07-117">アップグレード アドバイザーを使用したアップグレードの準備</span><span class="sxs-lookup"><span data-stu-id="93e07-117">Use Upgrade Advisor to Prepare for Upgrades</span></span>](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)  
  
## <a name="upgrading-analysis-services"></a><span data-ttu-id="93e07-118">Analysis Services のアップグレード</span><span class="sxs-lookup"><span data-stu-id="93e07-118">Upgrading Analysis Services</span></span>  
 <span data-ttu-id="93e07-119">サーバーおよびデータをアップグレードするには、複数の方法から選択できます。</span><span class="sxs-lookup"><span data-stu-id="93e07-119">You can choose from several approaches to upgrade server and data:</span></span>  
  
-   <span data-ttu-id="93e07-120">**インプレースアップグレードで**は、既存のプログラムファイルがプログラムファイルに置き換えられ [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="93e07-120">An **in-place upgrade** replaces the existing program files with [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] program files.</span></span> <span data-ttu-id="93e07-121">データベースは、同じ場所に残ります。</span><span class="sxs-lookup"><span data-stu-id="93e07-121">Databases remain in the same location.</span></span> <span data-ttu-id="93e07-122">プログラム フォルダーは、新しい名前を反映して更新されます。</span><span class="sxs-lookup"><span data-stu-id="93e07-122">Program folders are updated to reflect the new name.</span></span>  
  
-   <span data-ttu-id="93e07-123">**サイドバイサイドアップグレード**は、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 既存の Analysis Services インスタンスがある同じコンピューター上のの新規インストールです。</span><span class="sxs-lookup"><span data-stu-id="93e07-123">A **side-by-side upgrade** is a new installation of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on the same computer that has an existing Analysis Services instance.</span></span> <span data-ttu-id="93e07-124">以前のバージョンを今後使用しない場合は、データベースを同じコンピューター上の新しいインスタンスへ移動し、以前のバージョンをアンインストールできます。</span><span class="sxs-lookup"><span data-stu-id="93e07-124">You can move databases over to the new instance on the same computer, and then uninstall the old version if you no longer use it.</span></span>  
  
-   <span data-ttu-id="93e07-125">Analysis Services を新しいハードウェア上にインストールし、既存のデータベースをそのサーバーへ移行することもできます。</span><span class="sxs-lookup"><span data-stu-id="93e07-125">You can also install Analysis Services on new hardware and then migrate existing databases to that server.</span></span>  
  
## <a name="in-place-upgrade"></a><span data-ttu-id="93e07-126">インプレース アップグレード</span><span class="sxs-lookup"><span data-stu-id="93e07-126">In-place Upgrade</span></span>  
 <span data-ttu-id="93e07-127">の既存のインスタンスをにアップグレードすることができます [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。また、アップグレードプロセスの一環として、既存のデータベースが古いインスタンスから新しいインスタンスに自動的に移行されます。</span><span class="sxs-lookup"><span data-stu-id="93e07-127">You can upgrade an existing instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and, as part of the upgrade process, automatically migrate existing databases from the old instance to the new instance.</span></span> <span data-ttu-id="93e07-128">メタデータおよびバイナリ データは 2 つのバージョン間で互換性があるため、アップグレード後もそのまま使用できます。手動でデータを移行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="93e07-128">Because the metadata and binary data is compatible between the two versions, you will retain the data after you upgrade and you do not have to manually migrate the data.</span></span>  
  
 <span data-ttu-id="93e07-129">既存のインスタンスをアップグレードするには、セットアップを実行し、新しいインスタンスの名前として既存のインスタンス名を指定します。</span><span class="sxs-lookup"><span data-stu-id="93e07-129">To upgrade an existing instance, run Setup and specify the name of the existing instance as the name of the new instance.</span></span>  
  
## <a name="upgrading-databases"></a><span data-ttu-id="93e07-130">データベースのアップグレード</span><span class="sxs-lookup"><span data-stu-id="93e07-130">Upgrading Databases</span></span>  
 <span data-ttu-id="93e07-131">以前のバージョンの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で作成されたデータベースは、アップグレード後のサーバー上で、古いデータベース互換性レベル設定で実行されます。</span><span class="sxs-lookup"><span data-stu-id="93e07-131">Databases that were created in previous versions of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] run on the upgraded server under an older database compatibility level setting.</span></span> <span data-ttu-id="93e07-132">次のバージョンで作成されたデータベースのデータベース互換性レベルは 105 になります。</span><span class="sxs-lookup"><span data-stu-id="93e07-132">Databases created in the following versions, have a database compatibility level of 105.</span></span> <span data-ttu-id="93e07-133">新しいデータベースの互換性レベルを必要とする機能を使用する場合は、互換性レベルを変更できます。</span><span class="sxs-lookup"><span data-stu-id="93e07-133">You can change the compatibility level if you want to use features that require a newer database compatibility level.</span></span> <span data-ttu-id="93e07-134">それ以外の場合は、元の設定を使用して、アップグレード後のサーバー上でデータベースを実行できます。</span><span class="sxs-lookup"><span data-stu-id="93e07-134">Otherwise, you can run the databases on the upgraded server using the original settings.</span></span> <span data-ttu-id="93e07-135">詳細については、「[多次元データベースの互換性レベルを設定する &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93e07-135">For more information, see [Set the Compatibility Level of a Multidimensional Database &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services).</span></span>  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="93e07-136">参照</span><span class="sxs-lookup"><span data-stu-id="93e07-136">See Also</span></span>  
 <span data-ttu-id="93e07-137">[SQL Server 2014 の各エディションがサポートする機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span><span class="sxs-lookup"><span data-stu-id="93e07-137">[Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span></span>  
 <span data-ttu-id="93e07-138">[SQL Server のインストール計画](../../sql-server/install/planning-a-sql-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="93e07-138">[Planning a SQL Server Installation](../../sql-server/install/planning-a-sql-server-installation.md) </span></span>  
 <span data-ttu-id="93e07-139">[Microsoft OLAP アーキテクチャについて](https://docs.microsoft.com/analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture) </span><span class="sxs-lookup"><span data-stu-id="93e07-139">[Understanding Microsoft OLAP Architecture](https://docs.microsoft.com/analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture) </span></span>  
 <span data-ttu-id="93e07-140">[PowerPivot for SharePoint のアップグレード](upgrade-power-pivot-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="93e07-140">[Upgrade PowerPivot for SharePoint](upgrade-power-pivot-for-sharepoint.md) </span></span>  
 <span data-ttu-id="93e07-141">[多次元およびデータマイニングモードでの Analysis Services のインストール](../../sql-server/install/install-analysis-services-in-multidimensional-and-data-mining-mode.md) </span><span class="sxs-lookup"><span data-stu-id="93e07-141">[Install Analysis Services in Multidimensional and Data Mining Mode](../../sql-server/install/install-analysis-services-in-multidimensional-and-data-mining-mode.md) </span></span>  
 [<span data-ttu-id="93e07-142">PowerPivot for SharePoint 2010 のインストール</span><span class="sxs-lookup"><span data-stu-id="93e07-142">PowerPivot for SharePoint 2010 Installation</span></span>](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
