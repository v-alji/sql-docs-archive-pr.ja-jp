---
title: 高可用性 (Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- high availability [SQL Server], Reporting Services
- high availability [Reporting Services]
- Reporting Services, high availability
ms.assetid: 50e0813f-f591-4688-9cd1-e6389a3808e5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dfa0548bc526b007c4301572cd1a8e47a2851e18
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646025"
---
# <a name="high-availability-reporting-services"></a><span data-ttu-id="9bced-102">高可用性 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="9bced-102">High Availability (Reporting Services)</span></span>
  <span data-ttu-id="9bced-103">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] レポート サーバーは、アプリケーションのデータ、コンテンツ、プロパティ、およびセッション情報を 2 つの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] リレーショナル データベースに格納するステートレス サーバーです。</span><span class="sxs-lookup"><span data-stu-id="9bced-103">A [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server is a stateless server that stores application data, content, properties, and session information in two [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] relational databases.</span></span> <span data-ttu-id="9bced-104">したがって、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] の可用性を確保するには、次のことを検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9bced-104">As such, the best way to ensure the availability of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] functionality is to do the following:</span></span>  
  
-   <span data-ttu-id="9bced-105">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] の高可用性機能を使用して、レポート サーバー データベースの稼働時間を最大限に保つ。</span><span class="sxs-lookup"><span data-stu-id="9bced-105">Use the high availability features of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] to maximize the uptime of the report server databases.</span></span> <span data-ttu-id="9bced-106">[!INCLUDE[ssDE](../includes/ssde-md.md)] インスタンスをフェールオーバー クラスターで実行するように構成した場合、そのインスタンスをレポート サーバー データベースの作成時に選択できます。</span><span class="sxs-lookup"><span data-stu-id="9bced-106">If you configure a [!INCLUDE[ssDE](../includes/ssde-md.md)] instance to run in a failover cluster, you can select that instance when you create a report server database.</span></span>  
  
-   <span data-ttu-id="9bced-107">できるだけ、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssHADR](../includes/sshadr-md.md)] を、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] データベースと共に、またデータ ソース用に使用する。</span><span class="sxs-lookup"><span data-stu-id="9bced-107">Use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssHADR](../includes/sshadr-md.md)] with the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] databases and for data sources, as possible.</span></span> <span data-ttu-id="9bced-108">詳細については、「[Reporting Services with AlwaysOn Availability Groups (SQL Server)](../database-engine/availability-groups/windows/reporting-services-with-always-on-availability-groups-sql-server.md)」(Reporting Services と AlwaysOn 可用性グループ (SQL Server)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9bced-108">For more information, see [Reporting Services with AlwaysOn Availability Groups &#40;SQL Server&#41;](../database-engine/availability-groups/windows/reporting-services-with-always-on-availability-groups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="9bced-109">複数のレポート サーバーをスケールアウト配置で実行するように構成する。この場合、すべてのサーバーは単一のレポート サーバー データベースを共有することになります。</span><span class="sxs-lookup"><span data-stu-id="9bced-109">Configure multiple report servers to run in a scale-out deployment, where all the servers share a single report server database.</span></span> <span data-ttu-id="9bced-110">複数のレポート サーバー インスタンスを (可能であれば異なるサーバーに) スケールアウト配置することにより、いずれかのレポート サーバー インスタンスがダウンした場合でも、サービスの中断を効果的に防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="9bced-110">Deploying multiple report server instances, preferably on different servers, in a scale-out deployment can help provide uninterrupted service in the event one of the report server instances goes down.</span></span>  
  
 <span data-ttu-id="9bced-111">スケールアウト配置により、データベースの共有が可能となります。</span><span class="sxs-lookup"><span data-stu-id="9bced-111">A scale-out deployment provides a way to share a database.</span></span> <span data-ttu-id="9bced-112">どれか 1 つのレポート サーバーがダウンしても、同じ配置内の他のサーバーが処理を続行します。</span><span class="sxs-lookup"><span data-stu-id="9bced-112">If one report server goes down, other servers in the same deployment will continue to work.</span></span>  
  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="9bced-113">はクラスターに対応していません。</span><span class="sxs-lookup"><span data-stu-id="9bced-113">is not cluster-aware.</span></span> <span data-ttu-id="9bced-114">スケールアウト配置自体は負荷分散機能を備えていないため、レポート サーバーの処理負荷を検出したり、新しい処理要求を最も負荷の低いサーバーにルーティングしたりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="9bced-114">By itself, a scale-out deployment does not provide load balancing; it does not detect the processing loads on a report server and route new processing requests to the least busy server.</span></span> <span data-ttu-id="9bced-115">エラーが発生して完了しなかった処理要求が再ルーティングされることもありません。</span><span class="sxs-lookup"><span data-stu-id="9bced-115">It does not re-route processing requests that failed before completion.</span></span> <span data-ttu-id="9bced-116">負荷分散機能を実現するためには、レポート サーバーをホストする Web サーバーに対して負荷分散を構成し、それらのレポート サーバーが同じレポート サーバー データベースを共有するようにスケールアウト配置で構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9bced-116">To get load balancing features, you must configure load balancing for the Web servers that host the report servers, and then configure the report servers in a scale-out deployment so that they share the same report server database.</span></span>  
  
 <span data-ttu-id="9bced-117">レポート サーバーの Web サービスと Windows サービスは単一のレポート サーバー インスタンスとして緊密に統合され、互いに連携して動作します。</span><span class="sxs-lookup"><span data-stu-id="9bced-117">The Report Server Web service and Windows service are tightly integrated and run together as a single report server instance.</span></span> <span data-ttu-id="9bced-118">どちらか一方のサービスに対して個別に可用性を構成することはできません。</span><span class="sxs-lookup"><span data-stu-id="9bced-118">You cannot configure availability for one service separately from the other.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bced-119">参照</span><span class="sxs-lookup"><span data-stu-id="9bced-119">See Also</span></span>  
 <span data-ttu-id="9bced-120">[高可用性ソリューション &#40;SQL Server&#41;](../sql-server/failover-clusters/high-availability-solutions-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9bced-120">[High Availability Solutions &#40;SQL Server&#41;](../sql-server/failover-clusters/high-availability-solutions-sql-server.md) </span></span>  
 [<span data-ttu-id="9bced-121">ネイティブ モード レポート サーバーのスケールアウト配置の構成 (SSRS 構成マネージャー)</span><span class="sxs-lookup"><span data-stu-id="9bced-121">Configure a Native Mode Report Server Scale-Out Deployment &#40;SSRS Configuration Manager&#41;</span></span>](install-windows/configure-a-native-mode-report-server-scale-out-deployment.md)  
  
  
