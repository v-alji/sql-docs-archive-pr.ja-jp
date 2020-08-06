---
title: いくつかの可用性レプリカが、正常なロールを持っていません | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp6allroleshealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 7ec5b337-7201-4a66-a541-7560f8b18784
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 801fe20edf6f2dbe09bc800722cf4210988ebc69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641245"
---
# <a name="some-availability-replicas-do-not-have-a-healthy-role"></a><span data-ttu-id="c58fc-102">いくつかの可用性レプリカが、正常なロールを持っていません</span><span class="sxs-lookup"><span data-stu-id="c58fc-102">Some availability replicas do not have a healthy role</span></span>
    
## <a name="introduction"></a><span data-ttu-id="c58fc-103">はじめに</span><span class="sxs-lookup"><span data-stu-id="c58fc-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c58fc-104">**ポリシー名**</span><span class="sxs-lookup"><span data-stu-id="c58fc-104">**Policy Name**</span></span>|<span data-ttu-id="c58fc-105">可用性レプリカのロールの状態</span><span class="sxs-lookup"><span data-stu-id="c58fc-105">Availability Replicas Role State</span></span>|  
|<span data-ttu-id="c58fc-106">**問題点**</span><span class="sxs-lookup"><span data-stu-id="c58fc-106">**Issue**</span></span>|<span data-ttu-id="c58fc-107">一部の可用性レプリカに正常なロールがありません。</span><span class="sxs-lookup"><span data-stu-id="c58fc-107">Some availability replicas do not have a healthy role.</span></span>|  
|<span data-ttu-id="c58fc-108">**カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="c58fc-108">**Category**</span></span>|<span data-ttu-id="c58fc-109">**警告**</span><span class="sxs-lookup"><span data-stu-id="c58fc-109">**Warning**</span></span>|  
|<span data-ttu-id="c58fc-110">**ファセット**</span><span class="sxs-lookup"><span data-stu-id="c58fc-110">**Facet**</span></span>|<span data-ttu-id="c58fc-111">可用性グループ</span><span class="sxs-lookup"><span data-stu-id="c58fc-111">Availability group</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c58fc-112">説明</span><span class="sxs-lookup"><span data-stu-id="c58fc-112">Description</span></span>  
 <span data-ttu-id="c58fc-113">このポリシーは、すべての可用性レプリカの接続状態をロール アップし、正常なロールに属していない可用性レプリカがないか確認します。</span><span class="sxs-lookup"><span data-stu-id="c58fc-113">This policy rolls up the connection state of all availability replicas and checks if there are any availability replicas that are not in a healthy role.</span></span> <span data-ttu-id="c58fc-114">可用性レプリカがプライマリでもセカンダリでもない場合、ポリシーは通常とは異なる状態です。</span><span class="sxs-lookup"><span data-stu-id="c58fc-114">The policy is in an unhealthy state when any availability replica is neither primary nor secondary.</span></span> <span data-ttu-id="c58fc-115">それ以外の場合、ポリシーは正常な状態です。</span><span class="sxs-lookup"><span data-stu-id="c58fc-115">The policy is otherwise in a healthy state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c58fc-116">[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]のこのリリース向けに、TechNet Wiki の「 [一部の可用性レプリカに正常なロールがない](https://go.microsoft.com/fwlink/p/?LinkId=220854) 」に、考えられるエラーの原因および解決方法に関する情報が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="c58fc-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Some availability replicas do not have a healthy role](https://go.microsoft.com/fwlink/p/?LinkId=220854) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="c58fc-117">考えられる原因</span><span class="sxs-lookup"><span data-stu-id="c58fc-117">Possible Causes</span></span>  
 <span data-ttu-id="c58fc-118">現在プライマリとセカンダリのいずれのロールも持たない可用性レプリカがこの可用性グループに少なくとも 1 つ存在します。</span><span class="sxs-lookup"><span data-stu-id="c58fc-118">In this availability group, at least one availability replica does not currently have the primary or secondary role.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="c58fc-119">考えられる解決方法</span><span class="sxs-lookup"><span data-stu-id="c58fc-119">Possible Solution</span></span>  
 <span data-ttu-id="c58fc-120">可用性レプリカのポリシーの状態を検索条件として、プライマリ ロールにもセカンダリ ロールにも該当しない可用性レプリカを探し、問題を解決してください。</span><span class="sxs-lookup"><span data-stu-id="c58fc-120">Use the availability replica policy state to find the availability replica whose role is not primary or secondary, and then resolve the issue at the availability replica.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c58fc-121">参照</span><span class="sxs-lookup"><span data-stu-id="c58fc-121">See Also</span></span>  
 <span data-ttu-id="c58fc-122">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c58fc-122">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="c58fc-123">AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="c58fc-123">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
