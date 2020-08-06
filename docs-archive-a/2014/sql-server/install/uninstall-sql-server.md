---
title: SQL Server 2014 | のアンインストールMicrosoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: e6255f8e-a25e-4b3d-9310-c5da2f9c9333
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e72f153c28a1ccd827150eb3dddc0b52321518a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640393"
---
# <a name="uninstall-sql-server-2014"></a><span data-ttu-id="9b92e-102">SQL Server 2014 のアンインストール</span><span class="sxs-lookup"><span data-stu-id="9b92e-102">Uninstall SQL Server 2014</span></span>
  <span data-ttu-id="9b92e-103">以下のトピックに従って [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の既存のインスタンスを完全にアンインストールし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を再インストールできるようにシステムを準備します。</span><span class="sxs-lookup"><span data-stu-id="9b92e-103">Follow the topics below to uninstall an existing instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] completely, and prepare the system so that you can reinstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9b92e-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="9b92e-104">In This Section</span></span>  
 [<span data-ttu-id="9b92e-105">SQL Server の既存のインスタンスのアンインストール &#40;セットアップ&#41;</span><span class="sxs-lookup"><span data-stu-id="9b92e-105">Uninstall an Existing Instance of SQL Server &#40;Setup&#41;</span></span>](uninstall-an-existing-instance-of-sql-server-setup.md)  
 <span data-ttu-id="9b92e-106">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のスタンドアロン インスタンスを手動でアンインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9b92e-106">This topic describes how to manually uninstall a stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="9b92e-107">PowerPivot for SharePoint のアンインストール</span><span class="sxs-lookup"><span data-stu-id="9b92e-107">Uninstall PowerPivot for SharePoint</span></span>](uninstall-power-pivot-for-sharepoint.md)  
 <span data-ttu-id="9b92e-108">このトピックでは、PowerPivot for SharePoint を手動でアンインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9b92e-108">This topic describes how to manually uninstall PowerPivot for SharePoint.</span></span>  
  
 [<span data-ttu-id="9b92e-109">Reporting Services のアンインストール</span><span class="sxs-lookup"><span data-stu-id="9b92e-109">Uninstall Reporting Services</span></span>](uninstall-reporting-services.md)  
 <span data-ttu-id="9b92e-110">このトピックでは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サーバーをアンインストールする方法について説明します。SharePoint モードとネイティブ モードの両方のサーバーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9b92e-110">This topic describes how to uninstall [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] servers for both SharePoint mode and Native mode servers.</span></span>  
  
 [<span data-ttu-id="9b92e-111">マスター データ サービスのアンインストールと削除</span><span class="sxs-lookup"><span data-stu-id="9b92e-111">Uninstall and Remove Master Data Services</span></span>](uninstall-and-remove-master-data-services.md)  
 <span data-ttu-id="9b92e-112">このトピックでは、ローカル コンピューターから [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] をアンインストールして削除する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="9b92e-112">This topic describes the process of uninstalling and removing [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] from the local computer.</span></span>  
  
 [<span data-ttu-id="9b92e-113">Data Quality Server オブジェクトの削除</span><span class="sxs-lookup"><span data-stu-id="9b92e-113">Remove Data Quality Server Objects</span></span>](remove-data-quality-server-objects.md)  
 <span data-ttu-id="9b92e-114">このトピックでは、 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (DQS) の [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] コンポーネントのみをアンインストールした後に [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] オブジェクトを手動で削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9b92e-114">This topic describes how to manually remove the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] objects after uninstalling either [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or just the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] component in [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9b92e-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b92e-115">Related Sections</span></span>  
  
-   [<span data-ttu-id="9b92e-116">SQL Server のフェールオーバー クラスター インスタンスの削除 &#40;セットアップ&#41;</span><span class="sxs-lookup"><span data-stu-id="9b92e-116">Remove a SQL Server Failover Cluster Instance &#40;Setup&#41;</span></span>](../failover-clusters/install/remove-a-sql-server-failover-cluster-instance-setup.md)  
  
-   [<span data-ttu-id="9b92e-117">SQL Server フェールオーバー クラスターでのノードの追加または削除 &#40;セットアップ&#41;</span><span class="sxs-lookup"><span data-stu-id="9b92e-117">Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;</span></span>](../failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)  
  
-   [<span data-ttu-id="9b92e-118">SQL Server 2014 のインストールの削除</span><span class="sxs-lookup"><span data-stu-id="9b92e-118">Drop a SQL Server 2014 Installation</span></span>](../../database-engine/install-windows/repair-a-failed-sql-server-installation.md)  
  
## <a name="see-also"></a><span data-ttu-id="9b92e-119">参照</span><span class="sxs-lookup"><span data-stu-id="9b92e-119">See Also</span></span>  
 <span data-ttu-id="9b92e-120">[SQL Server のインストール計画](planning-a-sql-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="9b92e-120">[Planning a SQL Server Installation](planning-a-sql-server-installation.md) </span></span>  
 <span data-ttu-id="9b92e-121">[SQL Server 2014 をインストールする](../../database-engine/install-windows/install-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9b92e-121">[Install SQL Server 2014](../../database-engine/install-windows/install-sql-server.md) </span></span>  
 [<span data-ttu-id="9b92e-122">SQL Server 2014 へのアップグレード</span><span class="sxs-lookup"><span data-stu-id="9b92e-122">Upgrade to SQL Server 2014</span></span>](../../database-engine/install-windows/upgrade-sql-server.md)  
  
  
