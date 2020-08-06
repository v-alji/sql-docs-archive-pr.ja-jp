---
title: 一部の可用性データベースのデータ同期状態が正常でない | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.drp3datasynchealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 89f95d15-33c6-4768-bccd-9dbf8c4f49a9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 221f25a1ee7e4a8719acc133372c742ca4a79303
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743437"
---
# <a name="data-synchronization-state-of-some-availability-database-is-not-healthy"></a><span data-ttu-id="b5107-102">一部の可用性データベースのデータ同期状態が正常ではない</span><span class="sxs-lookup"><span data-stu-id="b5107-102">Data synchronization state of some availability database is not healthy</span></span>
    
## <a name="introduction"></a><span data-ttu-id="b5107-103">はじめに</span><span class="sxs-lookup"><span data-stu-id="b5107-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b5107-104">**ポリシー名**</span><span class="sxs-lookup"><span data-stu-id="b5107-104">**Policy Name**</span></span>|<span data-ttu-id="b5107-105">可用性レプリカのデータの同期状態</span><span class="sxs-lookup"><span data-stu-id="b5107-105">Availability Replica Data Synchronization State</span></span>|  
|<span data-ttu-id="b5107-106">**問題点**</span><span class="sxs-lookup"><span data-stu-id="b5107-106">**Issue**</span></span>|<span data-ttu-id="b5107-107">一部の可用性データベースのデータ同期状態が正常ではありません。</span><span class="sxs-lookup"><span data-stu-id="b5107-107">Data synchronization state of some availability database is not healthy.</span></span>|  
|<span data-ttu-id="b5107-108">**カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="b5107-108">**Category**</span></span>|<span data-ttu-id="b5107-109">**警告**</span><span class="sxs-lookup"><span data-stu-id="b5107-109">**Warning**</span></span>|  
|<span data-ttu-id="b5107-110">**ファセット**</span><span class="sxs-lookup"><span data-stu-id="b5107-110">**Facet**</span></span>|<span data-ttu-id="b5107-111">可用性レプリカ</span><span class="sxs-lookup"><span data-stu-id="b5107-111">Availability replica</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b5107-112">[説明]</span><span class="sxs-lookup"><span data-stu-id="b5107-112">Description</span></span>  
 <span data-ttu-id="b5107-113">このポリシーは、可用性データベース ("データベース レプリカ" とも呼ばれます) のデータの同期状態をチェックします。</span><span class="sxs-lookup"><span data-stu-id="b5107-113">This policy checks the data synchronization state of the availability database (also known as a "database replica").</span></span> <span data-ttu-id="b5107-114">データの同期状態が NOT SYNCHRONIZING である (同期コミット データベース レプリカでは、状態が SYNCHRONIZED 以外である) 場合、ポリシーは異常な状態です。</span><span class="sxs-lookup"><span data-stu-id="b5107-114">The policy is in an unhealthy state when the data synchronization state is NOT SYNCHRONIZING or the state is not SYNCHRONIZED for the synchronous-commit database replica.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b5107-115">[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]のこのリリース向けに、TechNet Wiki の「 [可用性データベースのデータ同期状態が正常でない](https://go.microsoft.com/fwlink/p/?LinkId=220863) 」に、考えられるエラーの原因および解決方法に関する情報が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="b5107-115">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Data synchronization state of availability database is not healthy](https://go.microsoft.com/fwlink/p/?LinkId=220863) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="b5107-116">考えられる原因</span><span class="sxs-lookup"><span data-stu-id="b5107-116">Possible Causes</span></span>  
 <span data-ttu-id="b5107-117">データの同期状態に異常の見られる可用性データベースがレプリカに少なくとも 1 つ存在します。</span><span class="sxs-lookup"><span data-stu-id="b5107-117">At least one availability database on the replica has an unhealthy data synchronization state.</span></span> <span data-ttu-id="b5107-118">これが非同期コミット可用性レプリカである場合は、すべての可用性データベースが SYNCHRONIZING 状態である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5107-118">If this is an asynchronous-commit availability replica, all availability databases should be in the SYNCHRONIZING state.</span></span> <span data-ttu-id="b5107-119">同期コミットの可用性レプリカである場合、すべての可用性データベースが SYNCHRONIZED 状態であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="b5107-119">If this is a synchronous-commit availability replica, all availability databases should be in the SYNCHRONIZED state.</span></span> <span data-ttu-id="b5107-120">この問題は、次の状況で発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b5107-120">This issue can be caused by the following:</span></span>  
  
-   <span data-ttu-id="b5107-121">可用性レプリカが切断されている。</span><span class="sxs-lookup"><span data-stu-id="b5107-121">The availability replica might be disconnected.</span></span>  
  
-   <span data-ttu-id="b5107-122">データの移動が中断されている。</span><span class="sxs-lookup"><span data-stu-id="b5107-122">The data movement might be suspended.</span></span>  
  
-   <span data-ttu-id="b5107-123">データベースにアクセスできない。</span><span class="sxs-lookup"><span data-stu-id="b5107-123">The database might not be accessible.</span></span>  
  
-   <span data-ttu-id="b5107-124">ネットワークの待機時間やプライマリ/セカンダリ レプリカへの負荷が原因で一時的に遅延の問題が生じている。</span><span class="sxs-lookup"><span data-stu-id="b5107-124">There might be a temporary delay issue due to network latency or the load on the primary or secondary replica.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="b5107-125">考えられる解決方法</span><span class="sxs-lookup"><span data-stu-id="b5107-125">Possible Solution</span></span>  
 <span data-ttu-id="b5107-126">接続の問題やデータの移動の中断が見られるようであればすべて解決します。</span><span class="sxs-lookup"><span data-stu-id="b5107-126">Resolve any connection or data movement suspend issues.</span></span> <span data-ttu-id="b5107-127">SQL Server Management Studio を使用してこの問題に対応するイベントをチェックし、データベース エラーを見つけます。</span><span class="sxs-lookup"><span data-stu-id="b5107-127">Check the events for this issue using SQL Server Management Studio, and find the database error.</span></span> <span data-ttu-id="b5107-128">特定のエラーのトラブルシューティングの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="b5107-128">Follow the troubleshooting steps for the specific error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5107-129">参照</span><span class="sxs-lookup"><span data-stu-id="b5107-129">See Also</span></span>  
 <span data-ttu-id="b5107-130">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b5107-130">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="b5107-131">AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b5107-131">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
