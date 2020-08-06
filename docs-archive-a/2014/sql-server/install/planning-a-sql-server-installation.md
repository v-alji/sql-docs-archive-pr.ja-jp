---
title: SQL Server のインストール計画 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- installing SQL Server, planning
ms.assetid: b1d56f2f-603f-48f2-b902-c715f14a6db9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e5b1dae9d2ef32298a9ddf2eeed1530e5ae97683
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643683"
---
# <a name="planning-a-sql-server-installation"></a><span data-ttu-id="17316-102">SQL Server のインストール計画</span><span class="sxs-lookup"><span data-stu-id="17316-102">Planning a SQL Server Installation</span></span>
  <span data-ttu-id="17316-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をインストールするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="17316-103">To install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], follow these steps:</span></span>  
  
-   <span data-ttu-id="17316-104">インストール要件、システム構成チェック、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストールに関するセキュリティ上の考慮事項を確認します。</span><span class="sxs-lookup"><span data-stu-id="17316-104">Review installation requirements, system configuration checks, and security considerations for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span>  
  
-   <span data-ttu-id="17316-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップを実行し、新しいバージョンをインストールするか、新しいバージョンへのアップグレードを行います。</span><span class="sxs-lookup"><span data-stu-id="17316-105">Run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup to install or upgrade to a later version.</span></span>  
  
-   <span data-ttu-id="17316-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を構成します。</span><span class="sxs-lookup"><span data-stu-id="17316-106">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilities to configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="17316-107">どのインストール方法を使用するかにかかわらず、個人として、または組織を代表して、ソフトウェア ライセンス条項に同意するかどうかを確認する必要があります。ただし、ソフトウェアの使用に別の契約 ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] ボリューム ライセンス契約、ISV や OEM とのサード パーティ契約など) が適用される場合を除きます。</span><span class="sxs-lookup"><span data-stu-id="17316-107">Regardless of the installation method, you are required to confirm acceptance of the software license terms as an individual or on behalf of an entity, unless your use of the software is governed by a separate agreement such as a [!INCLUDE[msCoName](../../includes/msconame-md.md)] volume licensing agreement or a third-party agreement with an ISV or OEM.</span></span>  
  
 <span data-ttu-id="17316-108">ライセンス条項は、セットアップのユーザー インターフェイスで確認し、同意することができます。</span><span class="sxs-lookup"><span data-stu-id="17316-108">The license terms are displayed for review and acceptance in the Setup user interface.</span></span> <span data-ttu-id="17316-109">/Q または /QS パラメーターを使用した自動インストールでは、/IAcceptSQLServerLicenseTerms パラメーターを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17316-109">Unattended installations (using the /Q or /QS parameters) must include the /IAcceptSQLServerLicenseTerms parameter.</span></span> <span data-ttu-id="17316-110">ライセンス条項は、「 [マイクロソフト ソフトウェア ライセンス条項](https://go.microsoft.com/fwlink/?LinkID=148209)」で別途確認できます。</span><span class="sxs-lookup"><span data-stu-id="17316-110">You can review the license terms separately at [Microsoft Software License Terms](https://go.microsoft.com/fwlink/?LinkID=148209).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="17316-111">ソフトウェアの入手方法 ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] のボリューム ライセンスを通じて入手した場合など) によっては、ソフトウェアの使用に追加の条件が課されることがあります。</span><span class="sxs-lookup"><span data-stu-id="17316-111">Depending on how you received the software (for example, through [!INCLUDE[msCoName](../../includes/msconame-md.md)] volume licensing), your use of the software may be subject to additional terms and conditions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="17316-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="17316-112">In This Section</span></span>  
 [<span data-ttu-id="17316-113">SQL Server インストールの新機能</span><span class="sxs-lookup"><span data-stu-id="17316-113">What's New in SQL Server Installation</span></span>](../../../2014/sql-server/install/what-s-new-in-sql-server-installation.md)  
 <span data-ttu-id="17316-114">このトピックでは、今バージョンの [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]でのインストールに関する、新しい機能や強化された機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="17316-114">This topic describes the details about the new or improved features of installation in this version of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 [<span data-ttu-id="17316-115">SQL Server 2014 のインストールに必要なハードウェアおよびソフトウェア</span><span class="sxs-lookup"><span data-stu-id="17316-115">Hardware and Software Requirements for Installing SQL Server 2014</span></span>](hardware-and-software-requirements-for-installing-sql-server.md)  
 <span data-ttu-id="17316-116">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のインスタンスのインストールおよび実行に必要な最低限のハードウェア要件とソフトウェア要件について説明します。</span><span class="sxs-lookup"><span data-stu-id="17316-116">This topic lists the minimum hardware and software requirements to install and run an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 [<span data-ttu-id="17316-117">SQL Server インストールにおけるセキュリティの考慮事項</span><span class="sxs-lookup"><span data-stu-id="17316-117">Security Considerations for a SQL Server Installation</span></span>](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
 <span data-ttu-id="17316-118">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール前と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインストール後で考慮する必要があるセキュリティのベスト プラクティスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="17316-118">This topic describes some security best practices that you should consider before you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and after you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="17316-119">Windows サービス アカウントと権限の構成</span><span class="sxs-lookup"><span data-stu-id="17316-119">Configure Windows Service Accounts and Permissions</span></span>](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)  
 <span data-ttu-id="17316-120">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のこのリリースにおける既定のサービス構成、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール時およびインストール後に設定できる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスの構成オプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="17316-120">This topic describes the default configuration of services in this release of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and configuration options for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services that you can set during and after [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span>  
  
 [<span data-ttu-id="17316-121">ネットワーク プロトコルとネットワーク ライブラリ</span><span class="sxs-lookup"><span data-stu-id="17316-121">Network Protocols and Network Libraries</span></span>](../../../2014/sql-server/install/network-protocols-and-network-libraries.md)  
 <span data-ttu-id="17316-122">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のこのリリースにおけるネットワーク プロトコルの既定の構成と、利用可能な構成オプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="17316-122">This topic describes the default configuration of network protocols in this release of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and the configuration options available.</span></span>  
  
 [<span data-ttu-id="17316-123">SQL Server の複数のバージョンおよびインスタンスの操作</span><span class="sxs-lookup"><span data-stu-id="17316-123">Work with Multiple Versions and Instances of SQL Server</span></span>](../../../2014/sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md)  
 <span data-ttu-id="17316-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の複数のバージョンおよびインスタンスのインストールに関する考慮事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="17316-124">This topic describes the considerations for installing multiple versions and instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="17316-125">SQL Server のローカル言語版</span><span class="sxs-lookup"><span data-stu-id="17316-125">Local Language Versions in SQL Server</span></span>](../../../2014/sql-server/install/local-language-versions-in-sql-server.md)  
 <span data-ttu-id="17316-126">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のローカライズ版について説明します。</span><span class="sxs-lookup"><span data-stu-id="17316-126">This topic describes about the localized versions of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="17316-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="17316-127">Related Sections</span></span>  
 [<span data-ttu-id="17316-128">SQL Server 2014 のインストール</span><span class="sxs-lookup"><span data-stu-id="17316-128">Install SQL Server 2014</span></span>](../../database-engine/install-windows/install-sql-server.md)  
 <span data-ttu-id="17316-129">このセクションでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]の各種インストール オプションについて概説します。</span><span class="sxs-lookup"><span data-stu-id="17316-129">This section provides an overview of different installation options we have for installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 [<span data-ttu-id="17316-130">SQL Server 2014 の BI 機能のインストール</span><span class="sxs-lookup"><span data-stu-id="17316-130">Install SQL Server 2014 BI Features</span></span>](install-sql-server-business-intelligence-features.md)  
 <span data-ttu-id="17316-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップのドキュメントのこのセクションでは、Microsoft BI プラットフォームの一部である [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能のインストール方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="17316-131">This section of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup documentation explains how to install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features that are part of the Microsoft BI platform.</span></span>  
  
 [<span data-ttu-id="17316-132">SQL Server 2014 へのアップグレード</span><span class="sxs-lookup"><span data-stu-id="17316-132">Upgrade to SQL Server 2014</span></span>](../../database-engine/install-windows/upgrade-sql-server.md)  
 <span data-ttu-id="17316-133">このセクションでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の以前のバージョンのインスタンスを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]にアップグレードする方法について概説します。</span><span class="sxs-lookup"><span data-stu-id="17316-133">The section provides an overview of upgrading instances of previous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versions to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 [<span data-ttu-id="17316-134">SQL Server 2014 のアンインストール</span><span class="sxs-lookup"><span data-stu-id="17316-134">Uninstall SQL Server 2014</span></span>](uninstall-sql-server.md)  
 <span data-ttu-id="17316-135">このセクションでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の既存のインスタンスを完全にアンインストールし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を再インストールできるようにシステムを準備する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="17316-135">Refer this section to uninstall an existing instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] completely, and prepare the system so that you can reinstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="17316-136">SQL Server フェールオーバー クラスターのインストール</span><span class="sxs-lookup"><span data-stu-id="17316-136">SQL Server Failover Cluster Installation</span></span>](../failover-clusters/install/sql-server-failover-cluster-installation.md)  
 <span data-ttu-id="17316-137">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップ ドキュメントのこのセクションでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスターをインストールして構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="17316-137">This section of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup documentation explains how to install, and configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17316-138">参照</span><span class="sxs-lookup"><span data-stu-id="17316-138">See Also</span></span>  
 <span data-ttu-id="17316-139">[SQL Server 2014 のクイックスタートインストール](../../../2014/getting-started/quick-start-installation-of-sql-server-2014.md) </span><span class="sxs-lookup"><span data-stu-id="17316-139">[Quick-Start Installation of SQL Server 2014](../../../2014/getting-started/quick-start-installation-of-sql-server-2014.md) </span></span>  
 <span data-ttu-id="17316-140">[コマンドプロンプトから SQL Server 2014 をインストールする](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md) </span><span class="sxs-lookup"><span data-stu-id="17316-140">[Install SQL Server 2014 from the Command Prompt](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md) </span></span>  
 <span data-ttu-id="17316-141">[高可用性ソリューション &#40;SQL Server&#41;](../failover-clusters/high-availability-solutions-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="17316-141">[High Availability Solutions &#40;SQL Server&#41;](../failover-clusters/high-availability-solutions-sql-server.md) </span></span>  
 <span data-ttu-id="17316-142">[フェールオーバークラスタリングをインストールする前に](../failover-clusters/install/before-installing-failover-clustering.md) </span><span class="sxs-lookup"><span data-stu-id="17316-142">[Before Installing Failover Clustering](../failover-clusters/install/before-installing-failover-clustering.md) </span></span>  
 [<span data-ttu-id="17316-143">インストールウィザード &#40;セットアップを使用して SQL Server 2014 にアップグレード&#41;</span><span class="sxs-lookup"><span data-stu-id="17316-143">Upgrade to SQL Server 2014 Using the Installation Wizard &#40;Setup&#41;</span></span>](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)  
  
  
