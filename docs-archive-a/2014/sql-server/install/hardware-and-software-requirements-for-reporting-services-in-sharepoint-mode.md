---
title: SharePoint モードの Reporting Services のハードウェアとソフトウェアの要件 |Microsoft Docs
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ed91877d-4f74-4266-a932-b824b4810c99
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: a4fc19b2871d7d5731649c61a8d5231d7e3479dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644813"
---
# <a name="hardware-and-software-requirements-for-reporting-services-in-sharepoint-mode"></a><span data-ttu-id="5f87d-102">Reporting Services の SharePoint モードに関するハードウェアとソフトウェアの要件</span><span class="sxs-lookup"><span data-stu-id="5f87d-102">Hardware and Software Requirements for Reporting Services in SharePoint Mode</span></span>

  <span data-ttu-id="5f87d-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] SharePoint モードで実行するための前提条件、ハードウェア要件、およびインストールに関する考慮事項について説明し [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="5f87d-103">This topic describes prerequisites, hardware requirements, and installation considerations for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] running in SharePoint mode.</span></span> <span data-ttu-id="5f87d-104">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モードには SharePoint Server が必要なため、要件のほとんどは SharePoint 環境に基づきます。</span><span class="sxs-lookup"><span data-stu-id="5f87d-104">Because [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode requires a SharePoint server, most of the requirements are based on the SharePoint environment.</span></span> <span data-ttu-id="5f87d-105">ネイティブ モード レポート サーバーの場合、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]を実行するための最低限のハードウェア要件とソフトウェア要件をハードウェアが満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f87d-105">For native mode report servers, your hardware should meet minimum hardware and software requirements for running [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="5f87d-106">詳細については、「 [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)」をご参照ください。</span><span class="sxs-lookup"><span data-stu-id="5f87d-106">For more information, see [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).</span></span>  
  
-   [<span data-ttu-id="5f87d-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="5f87d-107">Prerequisites</span></span>](#bkmk_prereq)  
  
-   [<span data-ttu-id="5f87d-108">レポートサーバーデータベースの要件</span><span class="sxs-lookup"><span data-stu-id="5f87d-108">Report Server Database Requirements</span></span>](#bkmk_report_server_database)  
  
-   [<span data-ttu-id="5f87d-109">Power View の要件</span><span class="sxs-lookup"><span data-stu-id="5f87d-109">Power View Requirements</span></span>](#bkmk_powerview)  
  
-   [<span data-ttu-id="5f87d-110">その他の情報</span><span class="sxs-lookup"><span data-stu-id="5f87d-110">More Information</span></span>](#bkmk_more_information)  
  
##  <a name="prerequisites"></a><a name="bkmk_prereq"></a> <span data-ttu-id="5f87d-111">前提条件</span><span class="sxs-lookup"><span data-stu-id="5f87d-111">Prerequisites</span></span>  
  
-   <span data-ttu-id="5f87d-112">ローカル インストールの場合は、SharePoint と [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインストール時にログインしたアカウントは、ローカルのオペレーティング システムの Administrators グループのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f87d-112">For local installations, the account logged in during installation of SharePoint and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] needs to be a member of the administrators group in the local operating system.</span></span> <span data-ttu-id="5f87d-113">セットアップ アカウントは、SharePoint ファーム管理者グループのメンバーである必要はありません。</span><span class="sxs-lookup"><span data-stu-id="5f87d-113">The setup account does not need to be a member of the SharePoint farm administrators group.</span></span>  
  
     <span data-ttu-id="5f87d-114">詳細については、「 [SharePoint 2013 のアカウントのアクセス許可とセキュリティ設定](https://technet.microsoft.com/library/cc678863.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f87d-114">For more information, see [Account permissions and security settings in SharePoint 2013](https://technet.microsoft.com/library/cc678863.aspx).</span></span>  
  
-   <span data-ttu-id="5f87d-115">SharePoint モードで実行している [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] には、SharePoint サーバーが必要です。</span><span class="sxs-lookup"><span data-stu-id="5f87d-115">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] running in SharePoint mode requires SharePoint Server.</span></span> <span data-ttu-id="5f87d-116">SharePoint の要件および構成の詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f87d-116">For more information about SharePoint requirements and configurations, see the following:</span></span>  
  
    -   <span data-ttu-id="5f87d-117">[ハードウェアとソフトウェアの要件 (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=256365) (https://go.microsoft.com/fwlink/p/?LinkId=256365)</span><span class="sxs-lookup"><span data-stu-id="5f87d-117">[Hardware and software requirements (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=256365) (https://go.microsoft.com/fwlink/p/?LinkId=256365)</span></span>  
  
    -   [<span data-ttu-id="5f87d-118">SharePoint Server 2013 の容量管理およびサイズ変更</span><span class="sxs-lookup"><span data-stu-id="5f87d-118">Capacity management and sizing for SharePoint Server 2013</span></span>](https://technet.microsoft.com/library/cc261700.aspx)  
  
    -   [<span data-ttu-id="5f87d-119">ビジネス インテリジェンスのソフトウェア要件 (SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="5f87d-119">Software requirements for business intelligence (SharePoint 2013)</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=256367)  
  
    -   <span data-ttu-id="5f87d-120">[ハードウェア要件およびソフトウェア要件 (SharePoint Server 2010)](https://technet.microsoft.com/library/cc262485\(v=office.14\))</span><span class="sxs-lookup"><span data-stu-id="5f87d-120">[Hardware and software requirements (SharePoint Server 2010)](https://technet.microsoft.com/library/cc262485\(v=office.14\))</span></span>  
  
    -   <span data-ttu-id="5f87d-121">[SharePoint Server 2010 の容量管理およびサイズ変更](https://technet.microsoft.com/library/cc261700.aspx\(v=office.14\))</span><span class="sxs-lookup"><span data-stu-id="5f87d-121">[Capacity management and sizing for SharePoint Server 2010](https://technet.microsoft.com/library/cc261700.aspx\(v=office.14\))</span></span>  
  
-   <span data-ttu-id="5f87d-122">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]を使用して既存の [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]SharePoint インストールをアップグレードまたは更新する場合は、「 [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)を実行するための最低限のハードウェア要件とソフトウェア要件をハードウェアが満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f87d-122">If you want to upgrade or update existing [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint installation with [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], see [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).</span></span>  
  
-   <span data-ttu-id="5f87d-123">**SharePoint 2013 Administration** Service が開始されていることを Windows サーバー マネージャーで確認します。</span><span class="sxs-lookup"><span data-stu-id="5f87d-123">Verify the **SharePoint 2013 Administration** service is started in Windows Server Manager.</span></span>  
  
###  <a name="report-server-database-requirements"></a><a name="bkmk_report_server_database"></a> <span data-ttu-id="5f87d-124">レポート サーバー データベースの要件</span><span class="sxs-lookup"><span data-stu-id="5f87d-124">Report Server Database Requirements</span></span>  
  
-   <span data-ttu-id="5f87d-125">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] および SharePoint 製品とテクノロジはどちらも、SQL Server のリレーショナル データベースを使用して、アプリケーション データを格納します。</span><span class="sxs-lookup"><span data-stu-id="5f87d-125">Both [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and SharePoint products and technologies use SQL Server relational databases to store application data.</span></span>  
  
-   [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] <span data-ttu-id="5f87d-126">には、互換性のある SQL Server エディションの [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="5f87d-126">requires an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] of a compatible SQL Server edition.</span></span> <span data-ttu-id="5f87d-127">ハードウェアとソフトウェアの要件の詳細については、「 [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f87d-127">For more information on hardware and software requirements, see [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).</span></span>  
  
-   <span data-ttu-id="5f87d-128">SharePoint 製品では、既存のデータベース インスタンスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5f87d-128">SharePoint products can use an existing database instance.</span></span> <span data-ttu-id="5f87d-129">[!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスがインストールされていない場合、SharePoint 製品のセットアップ プログラムでは SharePoint アプリケーションのデータベース用に SQL Server Express Edition がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="5f87d-129">If an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] is not installed, the SharePoint Products Setup program installs SQL Server Express Edition for the SharePoint application databases.</span></span>  
  
-   <span data-ttu-id="5f87d-130">レポート サーバー インスタンスの場合、データベースに SQL Server Express Edition を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="5f87d-130">The report server instance cannot use the SQL Server Express Edition for its database.</span></span> <span data-ttu-id="5f87d-131">ただし、SharePoint 製品によってインストールされる SQL Server Express Edition インスタンスは、他のデータベース エンジン エディションと共存できます。</span><span class="sxs-lookup"><span data-stu-id="5f87d-131">However, the SQL Server Express Edition instance installed by the SharePoint product can exist side-by-side with other Database Engine editions.</span></span>  
  
##  <a name="sscrescent-requirements"></a><a name="bkmk_powerview"></a><span data-ttu-id="5f87d-132">[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]要件</span><span class="sxs-lookup"><span data-stu-id="5f87d-132">[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] Requirements</span></span>

 <span data-ttu-id="5f87d-133">Office.Microsoft.com で最新の [Power View 関連ドキュメント](https://office.microsoft.com/excel-help/power-view-explore-visualize-and-present-your-data-HA102835634.aspx) を確認してください。</span><span class="sxs-lookup"><span data-stu-id="5f87d-133">Review the most up-to-date [Power View documentation](https://office.microsoft.com/excel-help/power-view-explore-visualize-and-present-your-data-HA102835634.aspx) on Office.Microsoft.com.</span></span> [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] <span data-ttu-id="5f87d-134">は Microsoft Excel 2013 の機能の 1 つであり、Microsoft SharePoint Server 2010 および 2013 の Enterprise Edition 用の [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Reporting Services アドインに含まれています。</span><span class="sxs-lookup"><span data-stu-id="5f87d-134">is a feature of Microsoft Excel 2013, and is part of the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Reporting Services add-in for Microsoft SharePoint Server 2010 and 2013 Enterprise Editions.</span></span>  
  
##  <a name="more-information"></a><a name="bkmk_more_information"></a> <span data-ttu-id="5f87d-135">その他の情報</span><span class="sxs-lookup"><span data-stu-id="5f87d-135">More Information</span></span>

 <span data-ttu-id="5f87d-136">SharePoint の変更の詳細については、「 [sharepoint 2010 から sharepoint 2013 への変更](https://technet.microsoft.com/library/ff607742\(office.15\).aspx)()」を参照してください https://technet.microsoft.com/library/ff607742(office.15).aspx) 。</span><span class="sxs-lookup"><span data-stu-id="5f87d-136">For information on SharePoint changes, see [Changes from SharePoint 2010 to SharePoint 2013](https://technet.microsoft.com/library/ff607742\(office.15\).aspx) (https://technet.microsoft.com/library/ff607742(office.15).aspx).</span></span>  
  
 <span data-ttu-id="5f87d-137">[SQL Server 2014 リリースノート](https://go.microsoft.com/fwlink/?LinkID=296445)。</span><span class="sxs-lookup"><span data-stu-id="5f87d-137">[SQL Server 2014 Release Notes](https://go.microsoft.com/fwlink/?LinkID=296445).</span></span>  
  
