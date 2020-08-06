---
title: Web 同期トポロジ | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Web synchronization, topologies
- IIS server configuration [SQL Server replication]
ms.assetid: 59444faf-bcb6-4421-a3df-8715753e453b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5e28ca5a222e2286d154c16ef41d3147dc56e25a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641605"
---
# <a name="topologies-for-web-synchronization"></a><span data-ttu-id="f4b61-102">Web 同期トポロジ</span><span class="sxs-lookup"><span data-stu-id="f4b61-102">Topologies for Web Synchronization</span></span>
  <span data-ttu-id="f4b61-103">さまざまな [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Web 同期レプリケーション トポロジを選択できます。</span><span class="sxs-lookup"><span data-stu-id="f4b61-103">You can choose from a variety of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Web synchronization replication topologies.</span></span> <span data-ttu-id="f4b61-104">Web 同期の一般的な構成には以下のものがあります。</span><span class="sxs-lookup"><span data-stu-id="f4b61-104">Common ways to configure Web synchronization include:</span></span>  
  
-   <span data-ttu-id="f4b61-105">単一サーバー</span><span class="sxs-lookup"><span data-stu-id="f4b61-105">Single server</span></span>  
  
-   <span data-ttu-id="f4b61-106">2 台のサーバー</span><span class="sxs-lookup"><span data-stu-id="f4b61-106">Two servers</span></span>  
  
-   <span data-ttu-id="f4b61-107">複数台の [!INCLUDE[msCoName](../../includes/msconame-md.md)] インターネット インフォメーション サービス (IIS) システムと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の再パブリッシュ</span><span class="sxs-lookup"><span data-stu-id="f4b61-107">Multiple [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) systems and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] republishing</span></span>  
  
 <span data-ttu-id="f4b61-108">Web 同期の構成の詳細については、「[Configure Web Synchronization (Web 同期の構成)](configure-web-synchronization.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f4b61-108">For information about configuring Web synchronization, see [Configure Web Synchronization](configure-web-synchronization.md).</span></span>  
  
## <a name="single-server"></a><span data-ttu-id="f4b61-109">シングル サーバー</span><span class="sxs-lookup"><span data-stu-id="f4b61-109">Single Server</span></span>  
 <span data-ttu-id="f4b61-110">最も単純なトポロジでは、IIS、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリッシャー、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ディストリビューターをすべて 1 つのサーバー上に配置します。</span><span class="sxs-lookup"><span data-stu-id="f4b61-110">In the simplest topology, IIS, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher, and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributor all reside on a single server.</span></span> <span data-ttu-id="f4b61-111">サブスクライバーは、パブリッシャー上の IIS に接続することによって同期します。</span><span class="sxs-lookup"><span data-stu-id="f4b61-111">Subscribers synchronize by connecting to IIS on the Publisher.</span></span> <span data-ttu-id="f4b61-112">パブリッシャーは、ファイアウォール内に置くこともできます。</span><span class="sxs-lookup"><span data-stu-id="f4b61-112">The Publisher can be located behind a firewall.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f4b61-113">この構成は、イントラネットを使用する場合にのみお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f4b61-113">This configuration is recommended only for intranet scenarios.</span></span> <span data-ttu-id="f4b61-114">他のケースでは、IIS サーバーと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリッシャー/ディストリビューターを別々のコンピューター上に配置することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f4b61-114">For other scenarios, it is recommended that the IIS server and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher/Distributor be on separate computers.</span></span>  
  
 <span data-ttu-id="f4b61-115">![シングル サーバーでの Web 同期](media/web-sync02.gif "シングル サーバーでの Web 同期")</span><span class="sxs-lookup"><span data-stu-id="f4b61-115">![Web synchronization with a single server](media/web-sync02.gif "Web synchronization with a single server")</span></span>  
  
## <a name="two-servers"></a><span data-ttu-id="f4b61-116">2 台のサーバー</span><span class="sxs-lookup"><span data-stu-id="f4b61-116">Two Servers</span></span>  
 <span data-ttu-id="f4b61-117">IIS を展開しているサーバーとは別のサーバーに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のパブリッシャーとディストリビューターを構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="f4b61-117">You can place IIS on one server and configure the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher and Distributor on another server.</span></span> <span data-ttu-id="f4b61-118">IIS を実行しているサーバーは、ファイアウォールを使用してインターネットから切り離すことができます。</span><span class="sxs-lookup"><span data-stu-id="f4b61-118">The server running IIS can be isolated from the Internet by a firewall.</span></span> <span data-ttu-id="f4b61-119">サブスクライバーは IIS に接続することによって同期します。</span><span class="sxs-lookup"><span data-stu-id="f4b61-119">Subscribers synchronize by connecting to IIS.</span></span>  
  
 <span data-ttu-id="f4b61-120">![2 台のサーバーでの Web 同期](media/web-sync03.gif "2 台のサーバーでの Web 同期")</span><span class="sxs-lookup"><span data-stu-id="f4b61-120">![Web synchronization with two servers](media/web-sync03.gif "Web synchronization with two servers")</span></span>  
  
## <a name="multiple-iis-systems-and-sql-server-republishing"></a><span data-ttu-id="f4b61-121">複数台の IIS システムと SQL Server の再パブリッシュ</span><span class="sxs-lookup"><span data-stu-id="f4b61-121">Multiple IIS Systems and SQL Server Republishing</span></span>  
 <span data-ttu-id="f4b61-122">多数のサブスクライバーをサポートし、それらを同時に同期する必要がある場合は、IIS を実行している複数のコンピューターに処理の負荷を分散させることができます。</span><span class="sxs-lookup"><span data-stu-id="f4b61-122">If you need to support very large numbers of Subscribers that synchronize at the same time, you can partition the work across multiple computers running IIS.</span></span>  
  
 <span data-ttu-id="f4b61-123">![複数の IIS サーバーでの Web 同期](media/web-sync04.gif "複数の IIS サーバーでの Web 同期")</span><span class="sxs-lookup"><span data-stu-id="f4b61-123">![Web synchronization with multiple IIS servers](media/web-sync04.gif "Web synchronization with multiple IIS servers")</span></span>  
  
 <span data-ttu-id="f4b61-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を実行しているコンピューターにも負荷の分散が必要となった場合は、複数のコンピューターに再パブリッシュの階層を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="f4b61-124">If further load balancing is required on the computer running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can create a republishing hierarchy on multiple computers.</span></span> <span data-ttu-id="f4b61-125">最上位レベルのパブリッシャーはデータをサブスクライバーにパブリッシュし、これを受けてサブスクライバーはデータを再パブリッシュします。結果としてサブスクライバーからの要求の負荷が分散されます。</span><span class="sxs-lookup"><span data-stu-id="f4b61-125">The top-level Publisher publishes data to Subscribers, which in turn republish the data, load balancing requests from the Subscribers.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f4b61-126">サブスクライバーは、特定のパブリッシャーとのみ同期できます。</span><span class="sxs-lookup"><span data-stu-id="f4b61-126">Subscribers can only synchronize with a specific Publisher.</span></span> <span data-ttu-id="f4b61-127">たとえば、リパブリッシャー A が使用できない場合に、リパブリッシャー A に対するサブスクライバーをリパブリッシャー B と同期することはできません。</span><span class="sxs-lookup"><span data-stu-id="f4b61-127">For example, a Subscriber to republisher A cannot synchronize with republisher B when A is not available.</span></span>  
  
 <span data-ttu-id="f4b61-128">![再パブリッシュでの Web 同期](media/web-sync05.gif "再パブリッシュでの Web 同期")</span><span class="sxs-lookup"><span data-stu-id="f4b61-128">![Web synchronization with republishing](media/web-sync05.gif "Web synchronization with republishing")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4b61-129">参照</span><span class="sxs-lookup"><span data-stu-id="f4b61-129">See Also</span></span>  
 <span data-ttu-id="f4b61-130">[Configure Web Synchronization](configure-web-synchronization.md) </span><span class="sxs-lookup"><span data-stu-id="f4b61-130">[Configure Web Synchronization](configure-web-synchronization.md) </span></span>  
 [<span data-ttu-id="f4b61-131">マージ レプリケーションの Web 同期</span><span class="sxs-lookup"><span data-stu-id="f4b61-131">Web Synchronization for Merge Replication</span></span>](web-synchronization-for-merge-replication.md)  
  
  
