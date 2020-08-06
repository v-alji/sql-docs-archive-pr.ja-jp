---
title: SQL Server フェールオーバークラスターのアップグレード |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- upgrading failover clusters
- clusters [SQL Server], upgrading
- failover clustering [SQL Server], upgrading
ms.assetid: daac41fe-7d0b-4f14-84c2-62952ad8cbfa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ca08e83c362e714f234a60ee358df3bcb03ade93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640521"
---
# <a name="upgrade-a-sql-server-failover-cluster"></a><span data-ttu-id="315ff-102">SQL Server フェールオーバー クラスターのアップグレード</span><span class="sxs-lookup"><span data-stu-id="315ff-102">Upgrade a SQL Server Failover Cluster</span></span>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="315ff-103">では、すべてのフェールオーバー クラスター ノードで個別に、[!INCLUDE[ssDE](../../../includes/ssde-md.md)]、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]、[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]、および [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] のフェールオーバー クラスターから[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]および [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] をアップグレードすることがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="315ff-103">supports upgrade of the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] and [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] from [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)], and [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] failover clusters separately on all failover cluster nodes.</span></span>  
  
 <span data-ttu-id="315ff-104">サポートの詳細は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="315ff-104">Support details are as follows:</span></span>  
  
-   <span data-ttu-id="315ff-105">ユーザー インターフェイスを使用したアップグレードとコマンド プロンプトからのアップグレードの両方がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="315ff-105">Upgrade is supported both through the user interface and from the command prompt.</span></span> <span data-ttu-id="315ff-106">詳細については、「[SQL Server フェールオーバー クラスター インスタンスのアップグレード &#40;セットアップ&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md)」および「[コマンド プロンプトからの SQL Server 2014 のインストール](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="315ff-106">For more information, see [Upgrade a SQL Server Failover Cluster Instance &#40;Setup&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md) and [Install SQL Server 2014 from the Command Prompt](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).</span></span>  
  
-   <span data-ttu-id="315ff-107">からアップグレードする [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] 場合は、各フェールオーバークラスターノードでコマンドプロンプトからアップグレードを実行するか、セットアップ UI を使用して各クラスターノードをアップグレードすることができます。</span><span class="sxs-lookup"><span data-stu-id="315ff-107">Upgrading from [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] - You can run upgrade from the command prompt on each failover cluster node, or by using the Setup UI to upgrade each cluster node.</span></span> <span data-ttu-id="315ff-108">アップグレードするインスタンスにフルテキスト検索機能およびレプリケーション機能が存在しない場合、これらの機能は、自動的にインストールされ、省略できません。</span><span class="sxs-lookup"><span data-stu-id="315ff-108">If Full-text search and Replication features do not exist on the instance being upgraded, they will be installed automatically with no option to omit them.</span></span>  
  
-   <span data-ttu-id="315ff-109">Service Pack のインストールについては、すべてのノードの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー クラスターに [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] の Service Pack と修正プログラムを個別に適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="315ff-109">Service pack installation - you must apply [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service packs and patches to [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] failover clusters separately on all nodes.</span></span>  
  
-   <span data-ttu-id="315ff-110">次のシナリオはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="315ff-110">The following scenarios are not supported:</span></span>  
  
    -   <span data-ttu-id="315ff-111">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のスタンドアロン インスタンスからフェールオーバー クラスターへの移行。</span><span class="sxs-lookup"><span data-stu-id="315ff-111">You cannot migrate from a stand-alone instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to a failover cluster.</span></span>  
  
    -   <span data-ttu-id="315ff-112">フェールオーバー クラスターへの機能の追加。</span><span class="sxs-lookup"><span data-stu-id="315ff-112">Add features to a failover cluster.</span></span> <span data-ttu-id="315ff-113">たとえば、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] のみの既存のフェールオーバー クラスターに [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]を追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="315ff-113">For example, you cannot add the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] to an existing [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-only failover cluster.</span></span>  
  
    -   <span data-ttu-id="315ff-114">フェールオーバー クラスター ノードからスタンドアロン インスタンスへのダウングレード。</span><span class="sxs-lookup"><span data-stu-id="315ff-114">You cannot downgrade a failover cluster node to a stand-alone instance.</span></span>  
  
-   <span data-ttu-id="315ff-115">詳細については、「[Always On フェールオーバー クラスター インスタンス (SQL Server)](always-on-failover-cluster-instances-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="315ff-115">For more information, see [AlwaysOn Failover Cluster Instances (SQL Server)](always-on-failover-cluster-instances-sql-server.md).</span></span>  
  
## <a name="upgrading-a-ssnoversion-multi-subnet-failover-cluster"></a><span data-ttu-id="315ff-116">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] マルチサブネット フェールオーバー クラスターのアップグレード</span><span class="sxs-lookup"><span data-stu-id="315ff-116">Upgrading a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Multi-Subnet Failover Cluster</span></span>  
 <span data-ttu-id="315ff-117">マルチサブネット [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバークラスターを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] マルチサブネットフェールオーバークラスターに直接アップグレードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="315ff-117">You cannot directly upgrade a non-multi-subnet [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] multi-subnet failover cluster.</span></span> <span data-ttu-id="315ff-118">詳細については、「[SQL Server フェールオーバー クラスター インスタンスのアップグレード &#40;セットアップ&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="315ff-118">For more information, see [Upgrade a SQL Server Failover Cluster Instance &#40;Setup&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="315ff-119">参照</span><span class="sxs-lookup"><span data-stu-id="315ff-119">See Also</span></span>  
 <span data-ttu-id="315ff-120">[サポートされているバージョンとエディションのアップグレード](../../../database-engine/install-windows/supported-version-and-edition-upgrades.md) </span><span class="sxs-lookup"><span data-stu-id="315ff-120">[Supported Version and Edition Upgrades](../../../database-engine/install-windows/supported-version-and-edition-upgrades.md) </span></span>  
 <span data-ttu-id="315ff-121">[SQL Server のフェールオーバークラスターインスタンスをアップグレードする &#40;セットアップ&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md) </span><span class="sxs-lookup"><span data-stu-id="315ff-121">[Upgrade a SQL Server Failover Cluster Instance &#40;Setup&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md) </span></span>  
 [<span data-ttu-id="315ff-122">コマンド プロンプトからの SQL Server 2014 のインストール</span><span class="sxs-lookup"><span data-stu-id="315ff-122">Install SQL Server 2014 from the Command Prompt</span></span>](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)  
  
  
