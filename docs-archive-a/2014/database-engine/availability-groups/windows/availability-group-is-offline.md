---
title: 可用性グループがオフライン | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp2online.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 093c5208-bf7a-49f4-a546-72b48197cadf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b25e5b22a09783c8dfcad862500b5c0dfcb2c319
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632128"
---
# <a name="availability-group-is-offline"></a><span data-ttu-id="35bae-102">可用性グループがオフライン</span><span class="sxs-lookup"><span data-stu-id="35bae-102">Availability group is offline</span></span>
    
## <a name="introduction"></a><span data-ttu-id="35bae-103">はじめに</span><span class="sxs-lookup"><span data-stu-id="35bae-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="35bae-104">**ポリシー名**</span><span class="sxs-lookup"><span data-stu-id="35bae-104">**Policy Name**</span></span>|<span data-ttu-id="35bae-105">可用性グループのオンライン状態</span><span class="sxs-lookup"><span data-stu-id="35bae-105">Availability Group Online State</span></span>|  
|<span data-ttu-id="35bae-106">**問題点**</span><span class="sxs-lookup"><span data-stu-id="35bae-106">**Issue**</span></span>|<span data-ttu-id="35bae-107">可用性グループはオフラインです。</span><span class="sxs-lookup"><span data-stu-id="35bae-107">Availability group is offline.</span></span>|  
|<span data-ttu-id="35bae-108">**カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="35bae-108">**Category**</span></span>|<span data-ttu-id="35bae-109">**重大**</span><span class="sxs-lookup"><span data-stu-id="35bae-109">**Critical**</span></span>|  
|<span data-ttu-id="35bae-110">**ファセット**</span><span class="sxs-lookup"><span data-stu-id="35bae-110">**Facet**</span></span>|<span data-ttu-id="35bae-111">可用性グループ</span><span class="sxs-lookup"><span data-stu-id="35bae-111">Availability group</span></span>|  
  
## <a name="description"></a><span data-ttu-id="35bae-112">説明</span><span class="sxs-lookup"><span data-stu-id="35bae-112">Description</span></span>  
 <span data-ttu-id="35bae-113">このポリシーは、可用性グループのオンライン状態またはオフライン状態をチェックします。</span><span class="sxs-lookup"><span data-stu-id="35bae-113">This policy checks the online or offline state of the availability group.</span></span> <span data-ttu-id="35bae-114">可用性グループのクラスター リソースがオフライン状態である場合、または可用性グループがプライマリ レプリカを持たない場合、ポリシーは通常とは異なる状態で、アラートが発生します。</span><span class="sxs-lookup"><span data-stu-id="35bae-114">The policy is in an unhealthy state and an alert is raised when the cluster resource of the availability group is offline or the availability group does not have a primary replica.</span></span>  
  
 <span data-ttu-id="35bae-115">可用性グループのクラスター リソースがオンライン状態で、可用性グループがプライマリ レプリカを持つ場合、ポリシーは正常な状態です。</span><span class="sxs-lookup"><span data-stu-id="35bae-115">The policy state is healthy when the cluster resource of the availability group is online and the availability group has a primary replica.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="35bae-116">[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]のこのリリース向けに、TechNet Wiki の「 [可用性グループがオフライン](https://go.microsoft.com/fwlink/p/?LinkId=220850) 」に、考えられるエラーの原因および解決方法に関する情報が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="35bae-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Availability group is offline](https://go.microsoft.com/fwlink/p/?LinkId=220850) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="35bae-117">考えられる原因</span><span class="sxs-lookup"><span data-stu-id="35bae-117">Possible Causes</span></span>  
 <span data-ttu-id="35bae-118">この問題は、プライマリ レプリカをホストするサーバー インスタンスのエラー、またはオフラインになっている Windows Server フェールオーバー クラスター (WSFC) 可用性グループ リソースによって発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="35bae-118">This issue can be caused by a failure in the server instance that hosts the primary replica or by the Windows Server Failover Cluster (WSFC) availability group resource going offline.</span></span> <span data-ttu-id="35bae-119">可用性グループがオフラインになる原因として、次のような状況が考えられます。</span><span class="sxs-lookup"><span data-stu-id="35bae-119">Following are possible causes for the availability group to be offline:</span></span>  
  
-   <span data-ttu-id="35bae-120">可用性グループで自動フェールオーバー モードが構成されていません。</span><span class="sxs-lookup"><span data-stu-id="35bae-120">The availability group is not configured with automatic failover mode.</span></span> <span data-ttu-id="35bae-121">プライマリ レプリカが使用できなくなり、可用性グループ内のすべてのレプリカのロールが "解決中" になります。</span><span class="sxs-lookup"><span data-stu-id="35bae-121">The primary replica becomes unavailable and the role of all replicas in the availability group become RESOLVING.</span></span>  
  
    -   <span data-ttu-id="35bae-122">プライマリ レプリカ インスタンス サービスがダウンしているか、または応答しません。</span><span class="sxs-lookup"><span data-stu-id="35bae-122">The primary replica instance service is down or unresponsive.</span></span>  
  
    -   <span data-ttu-id="35bae-123">可用性グループのクラスターへの接続に問題があります。</span><span class="sxs-lookup"><span data-stu-id="35bae-123">The availability group has a connectivity issue with the cluster.</span></span>  
  
-   <span data-ttu-id="35bae-124">可用性グループで自動フェールオーバー モードが構成されていますが、正常に完了していません。</span><span class="sxs-lookup"><span data-stu-id="35bae-124">The availability group is configured with automatic failover mode and does not complete successfully.</span></span>  
  
    -   <span data-ttu-id="35bae-125">自動フェールオーバー中、ターゲット レプリカ上でのプライマリ準備チェックが失敗し、新しいプライマリとなるレプリカがありません。</span><span class="sxs-lookup"><span data-stu-id="35bae-125">During the automatic failover, the primary readiness check on the target replica fails, and there is no replica available to become the new primary.</span></span>  
  
-   <span data-ttu-id="35bae-126">クラスターの可用性グループ リソースがオフラインになりました。</span><span class="sxs-lookup"><span data-stu-id="35bae-126">The availability group resource in the cluster becomes offline.</span></span>  
  
    -   <span data-ttu-id="35bae-127">いずれかの依存クラスター リソースで重大な問題が発生し、オフラインになりました。</span><span class="sxs-lookup"><span data-stu-id="35bae-127">Any dependent cluster resource encounters a critical issue and becomes offline.</span></span> <span data-ttu-id="35bae-128">可用性グループのリソースは、依存リソースがオンラインになるまでオフライン状態です。</span><span class="sxs-lookup"><span data-stu-id="35bae-128">The availability group resource is also offline until the dependent resource becomes online.</span></span>  
  
    -   <span data-ttu-id="35bae-129">クラスターでの重要な問題により、可用性グループ リソースがオフになりました。</span><span class="sxs-lookup"><span data-stu-id="35bae-129">A critical issue in the cluster turns off the availability group resource.</span></span>  
  
-   <span data-ttu-id="35bae-130">可用性グループに対する自動、手動、または強制フェールオーバーの実行中です。</span><span class="sxs-lookup"><span data-stu-id="35bae-130">There is an automatic, manual, or forced failover in progress for the availability group.</span></span>  
  
## <a name="possible-solutions"></a><span data-ttu-id="35bae-131">考えられる解決策</span><span class="sxs-lookup"><span data-stu-id="35bae-131">Possible Solutions</span></span>  
 <span data-ttu-id="35bae-132">この問題に対して考えられる解決策を次に示します。</span><span class="sxs-lookup"><span data-stu-id="35bae-132">Following are possible solutions for this issue:</span></span>  
  
-   <span data-ttu-id="35bae-133">プライマリ レプリカの SQL Server インスタンスがダウンしている場合は、サーバーを再起動した後、可用性グループが正常な状態であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="35bae-133">If the SQL Server instance of the primary replica is down, restart the server and then verify that the availability group recovers to a healthy state.</span></span>  
  
-   <span data-ttu-id="35bae-134">自動フェールオーバーが失敗していると考えられる場合は、レプリカ上のデータベースが以前の既知のプライマリ レプリカと同期されていることを確認した後、プライマリ レプリカにフェールオーバーします。</span><span class="sxs-lookup"><span data-stu-id="35bae-134">If the automatic failover appears to have failed, verify that the databases on the replica are synchronized with the previously known primary replica, and then failover to the primary replica.</span></span> <span data-ttu-id="35bae-135">データベースが同期していない場合は、データの紛失が最小限に収まるレプリカを選択し、フェールオーバー モードに復旧します。</span><span class="sxs-lookup"><span data-stu-id="35bae-135">If the databases are not synchronized, select a replica with a minimum loss of data, and then recover to failover mode.</span></span>  
  
-   <span data-ttu-id="35bae-136">SQL Server のインスタンスが正常である一方でクラスターのリソースがオフラインになっている場合は、フェールオーバー クラスター マネージャーを使用して、クラスターの正常性またはサーバー上の他のクラスターの問題を調べます。</span><span class="sxs-lookup"><span data-stu-id="35bae-136">If the resource in the cluster is offline while the instances of SQL Server appear to be healthy, use Failover Cluster Manager to check the cluster health or other cluster issues on the server.</span></span> <span data-ttu-id="35bae-137">フェールオーバー クラスター マネージャーを使用して可用性グループ リソースをオンラインにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="35bae-137">You can also use the Failover Cluster Manager to attempt to turn the availability group resource online.</span></span>  
  
-   <span data-ttu-id="35bae-138">フェールオーバーが進行中の場合は、フェールオーバーが完了するのを待ちます。</span><span class="sxs-lookup"><span data-stu-id="35bae-138">If there is a failover in progress, wait for the failover to complete.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35bae-139">参照</span><span class="sxs-lookup"><span data-stu-id="35bae-139">See Also</span></span>  
 <span data-ttu-id="35bae-140">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="35bae-140">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="35bae-141">AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="35bae-141">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
