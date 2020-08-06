---
title: 可用性グループの自動フェールオーバーの準備ができていない | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp3autofailover.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 28261014-342c-442a-bd89-6d04b8d4e8b7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2995ddec51cd70d8a3f209229d0ecb9b0132c79e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632131"
---
# <a name="availability-group-is-not-ready-for-automatic-failover"></a><span data-ttu-id="1c4b5-102">可用性グループの自動フェールオーバーの準備ができていない</span><span class="sxs-lookup"><span data-stu-id="1c4b5-102">Availability group is not ready for automatic failover</span></span>
    
## <a name="introduction"></a><span data-ttu-id="1c4b5-103">はじめに</span><span class="sxs-lookup"><span data-stu-id="1c4b5-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1c4b5-104">**ポリシー名**</span><span class="sxs-lookup"><span data-stu-id="1c4b5-104">**Policy Name**</span></span>|<span data-ttu-id="1c4b5-105">可用性グループの自動フェールオーバーの準備</span><span class="sxs-lookup"><span data-stu-id="1c4b5-105">Availability Group Automatic Failover Readiness</span></span>|  
|<span data-ttu-id="1c4b5-106">**問題点**</span><span class="sxs-lookup"><span data-stu-id="1c4b5-106">**Issue**</span></span>|<span data-ttu-id="1c4b5-107">可用性グループで自動フェールオーバーの準備ができていません。</span><span class="sxs-lookup"><span data-stu-id="1c4b5-107">Availability group is not ready for automatic failover.</span></span>|  
|<span data-ttu-id="1c4b5-108">**カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="1c4b5-108">**Category**</span></span>|<span data-ttu-id="1c4b5-109">**重大**</span><span class="sxs-lookup"><span data-stu-id="1c4b5-109">**Critical**</span></span>|  
|<span data-ttu-id="1c4b5-110">**ファセット**</span><span class="sxs-lookup"><span data-stu-id="1c4b5-110">**Facet**</span></span>|<span data-ttu-id="1c4b5-111">可用性グループ</span><span class="sxs-lookup"><span data-stu-id="1c4b5-111">Availability group</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1c4b5-112">説明</span><span class="sxs-lookup"><span data-stu-id="1c4b5-112">Description</span></span>  
 <span data-ttu-id="1c4b5-113">このポリシーは、フェールオーバーの準備が整っているセカンダリ レプリカが 1 つ以上可用性グループに存在するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="1c4b5-113">This policy checks to verify that the availability group has at least one secondary replica that is failover ready.</span></span> <span data-ttu-id="1c4b5-114">プライマリ レプリカのフェールオーバー モードが自動モードである一方で、可用性グループのセカンダリ レプリカのいずれもフェールオーバーの準備ができていない場合、ポリシーは通常とは異なる状態で、アラートが発生します。</span><span class="sxs-lookup"><span data-stu-id="1c4b5-114">The policy is in an unhealthy state and an alert is raised when the failover mode of the primary replica is automatic, however none of the secondary replicas in the availability group are failover ready.</span></span>  
  
 <span data-ttu-id="1c4b5-115">自動フェールオーバーの準備が整っているセカンダリ レプリカが 1 つ以上存在する場合、ポリシーは正常な状態です。</span><span class="sxs-lookup"><span data-stu-id="1c4b5-115">The policy is in a healthy state when at least one secondary replica is automatic failover ready.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1c4b5-116">[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]のこのリリース向けに、TechNet Wiki の「 [可用性グループの自動フェールオーバーの準備ができていない](https://go.microsoft.com/fwlink/p/?LinkId=220851) 」に、考えられるエラーの原因および解決方法に関する情報が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="1c4b5-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Availability group is not ready for automatic failover](https://go.microsoft.com/fwlink/p/?LinkId=220851) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="1c4b5-117">考えられる原因</span><span class="sxs-lookup"><span data-stu-id="1c4b5-117">Possible Causes</span></span>  
 <span data-ttu-id="1c4b5-118">可用性グループの自動フェールオーバーの準備ができていません。</span><span class="sxs-lookup"><span data-stu-id="1c4b5-118">The availability group is not ready for automatic failover.</span></span> <span data-ttu-id="1c4b5-119">プライマリ レプリカは自動フェールオーバー用に構成されていますが、セカンダリ レプリカは自動フェールオーバーの準備ができていません。</span><span class="sxs-lookup"><span data-stu-id="1c4b5-119">The primary replica is configured for automatic failover; however, the secondary replica is not ready for automatic failover.</span></span> <span data-ttu-id="1c4b5-120">自動フェールオーバー用に構成されているセカンダリ レプリカが使用できないか、そのデータ同期状態が現在 SYNCHRONIZED になっていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1c4b5-120">The secondary replica that is configured for automatic failover might be unavailable or its data synchronization state is currently not SYNCHRONIZED.</span></span>  
  
## <a name="possible-solutions"></a><span data-ttu-id="1c4b5-121">考えられる解決策</span><span class="sxs-lookup"><span data-stu-id="1c4b5-121">Possible Solutions</span></span>  
 <span data-ttu-id="1c4b5-122">この問題に対して考えられる解決策を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1c4b5-122">Following are possible solutions for this issue:</span></span>  
  
-   <span data-ttu-id="1c4b5-123">自動フェールオーバーとして 1 つ以上のセカンダリ レプリカが構成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1c4b5-123">Verify that at least one secondary replica is configured as automatic failover.</span></span> <span data-ttu-id="1c4b5-124">自動フェールオーバーとして構成されたセカンダリ レプリカが存在しない場合は、同期コミットが設定された自動フェールオーバー ターゲットとなるようにセカンダリ レプリカの構成を更新します。</span><span class="sxs-lookup"><span data-stu-id="1c4b5-124">If there is not a secondary replica configured as automatic failover, update the configuration of a secondary replica to be the automatic failover target with synchronous commit.</span></span>  
  
-   <span data-ttu-id="1c4b5-125">ポリシーを使用して、データが同期状態にあり、自動フェールオーバー ターゲットが SYNCHRONIZED 状態であることを確認した後、可用性レプリカの問題を解決します。</span><span class="sxs-lookup"><span data-stu-id="1c4b5-125">Use the policy to verify that the data is in a synchronization state and the automatic failover target is SYNCHRONIZED, and then resolve the issue at the availability replica.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c4b5-126">参照</span><span class="sxs-lookup"><span data-stu-id="1c4b5-126">See Also</span></span>  
 <span data-ttu-id="1c4b5-127">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1c4b5-127">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="1c4b5-128">AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="1c4b5-128">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
