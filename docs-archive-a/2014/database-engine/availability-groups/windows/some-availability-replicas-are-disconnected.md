---
title: いくつかの可用性レプリカが切断されている | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp7allconnected.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: aea808be-6f0f-40c2-9aa2-a2a435ec6443
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1bb6535b513770b9b4718a0e8372c0a5bc3cba84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641249"
---
# <a name="some-availability-replicas-are-disconnected"></a><span data-ttu-id="e7a4a-102">いくつかの可用性レプリカが切断されている</span><span class="sxs-lookup"><span data-stu-id="e7a4a-102">Some availability replicas are disconnected</span></span>
    
## <a name="introduction"></a><span data-ttu-id="e7a4a-103">はじめに</span><span class="sxs-lookup"><span data-stu-id="e7a4a-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e7a4a-104">**ポリシー名**</span><span class="sxs-lookup"><span data-stu-id="e7a4a-104">**Policy Name**</span></span>|<span data-ttu-id="e7a4a-105">可用性レプリカの接続状態</span><span class="sxs-lookup"><span data-stu-id="e7a4a-105">Availability Replicas Connection State</span></span>|  
|<span data-ttu-id="e7a4a-106">**問題点**</span><span class="sxs-lookup"><span data-stu-id="e7a4a-106">**Issue**</span></span>|<span data-ttu-id="e7a4a-107">一部の可用性レプリカの接続が解除されます。</span><span class="sxs-lookup"><span data-stu-id="e7a4a-107">Some availability replicas are disconnected.</span></span>|  
|<span data-ttu-id="e7a4a-108">**カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="e7a4a-108">**Category**</span></span>|<span data-ttu-id="e7a4a-109">**警告**</span><span class="sxs-lookup"><span data-stu-id="e7a4a-109">**Warning**</span></span>|  
|<span data-ttu-id="e7a4a-110">**ファセット**</span><span class="sxs-lookup"><span data-stu-id="e7a4a-110">**Facet**</span></span>|<span data-ttu-id="e7a4a-111">可用性グループ</span><span class="sxs-lookup"><span data-stu-id="e7a4a-111">Availability group</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e7a4a-112">説明</span><span class="sxs-lookup"><span data-stu-id="e7a4a-112">Description</span></span>  
 <span data-ttu-id="e7a4a-113">このポリシーは、すべての可用性レプリカの接続状態をロール アップし、DISCONENCTED 状態の可用性レプリカがないか確認します。</span><span class="sxs-lookup"><span data-stu-id="e7a4a-113">This policy rolls up the connection state of all availability replicas and checks for any availability replicas that are DISCONENCTED.</span></span> <span data-ttu-id="e7a4a-114">DISCONNECTED の可用性レプリカが存在する場合、ポリシーは異常な状態です。</span><span class="sxs-lookup"><span data-stu-id="e7a4a-114">The policy is in an unhealthy state when any availability replica is DISCONNECTED.</span></span> <span data-ttu-id="e7a4a-115">それ以外の場合、ポリシーは正常な状態です。</span><span class="sxs-lookup"><span data-stu-id="e7a4a-115">The policy is otherwise in a healthy state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e7a4a-116">[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]のこのリリース向けに、TechNet Wiki の「 [一部の可用性レプリカの接続が解除されている](https://go.microsoft.com/fwlink/p/?LinkId=220855) 」に、考えられるエラーの原因および解決方法に関する情報が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="e7a4a-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Some availability replicas are disconnected](https://go.microsoft.com/fwlink/p/?LinkId=220855) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="e7a4a-117">考えられる原因</span><span class="sxs-lookup"><span data-stu-id="e7a4a-117">Possible Causes</span></span>  
 <span data-ttu-id="e7a4a-118">プライマリ レプリカに接続されていないセカンダリ レプリカがこの可用性グループに少なくとも 1 つ存在します。</span><span class="sxs-lookup"><span data-stu-id="e7a4a-118">In this availability group, at least one secondary replica is not connected to the primary replica.</span></span> <span data-ttu-id="e7a4a-119">接続状態は DISCONNECTED です。</span><span class="sxs-lookup"><span data-stu-id="e7a4a-119">The connected state is DISCONNECTED.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="e7a4a-120">考えられる解決方法</span><span class="sxs-lookup"><span data-stu-id="e7a4a-120">Possible Solution</span></span>  
 <span data-ttu-id="e7a4a-121">可用性レプリカのポリシーの状態を検索条件として、DISCONNECTED 状態の可用性レプリカを探し、問題を解決してください。</span><span class="sxs-lookup"><span data-stu-id="e7a4a-121">Use the availability replica policy state to find the availability replica that is DISCONNECTED, and then resolve the issue at the availability replica.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7a4a-122">参照</span><span class="sxs-lookup"><span data-stu-id="e7a4a-122">See Also</span></span>  
 <span data-ttu-id="e7a4a-123">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e7a4a-123">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="e7a4a-124">AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="e7a4a-124">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
