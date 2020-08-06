---
title: 可用性レプリカが参加していない | Microsoft Docs
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.arp4joined.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 9c0d10b1-9e12-430c-83b9-ca2bd0a3afc4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7c4f76e98d373e50124f5ca2b135a9fad8f34226
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716833"
---
# <a name="availability-replica-is-not-joined"></a><span data-ttu-id="80c97-102">可用性レプリカが参加していない</span><span class="sxs-lookup"><span data-stu-id="80c97-102">Availability replica is not joined</span></span>
    
## <a name="introduction"></a><span data-ttu-id="80c97-103">はじめに</span><span class="sxs-lookup"><span data-stu-id="80c97-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="80c97-104">**ポリシー名**</span><span class="sxs-lookup"><span data-stu-id="80c97-104">**Policy Name**</span></span>|<span data-ttu-id="80c97-105">可用性レプリカの参加状態</span><span class="sxs-lookup"><span data-stu-id="80c97-105">Availability Replica Join State</span></span>|  
|<span data-ttu-id="80c97-106">**問題点**</span><span class="sxs-lookup"><span data-stu-id="80c97-106">**Issue**</span></span>|<span data-ttu-id="80c97-107">可用性レプリカが参加していません。</span><span class="sxs-lookup"><span data-stu-id="80c97-107">Availability Replica is not joined.</span></span>|  
|<span data-ttu-id="80c97-108">**カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="80c97-108">**Category**</span></span>|<span data-ttu-id="80c97-109">**警告**</span><span class="sxs-lookup"><span data-stu-id="80c97-109">**Warning**</span></span>|  
|<span data-ttu-id="80c97-110">**ファセット**</span><span class="sxs-lookup"><span data-stu-id="80c97-110">**Facet**</span></span>|<span data-ttu-id="80c97-111">可用性レプリカ</span><span class="sxs-lookup"><span data-stu-id="80c97-111">Availability replica</span></span>|  
  
## <a name="description"></a><span data-ttu-id="80c97-112">説明</span><span class="sxs-lookup"><span data-stu-id="80c97-112">Description</span></span>  
 <span data-ttu-id="80c97-113">このポリシーは、可用性レプリカの参加状態をチェックします。</span><span class="sxs-lookup"><span data-stu-id="80c97-113">This policy checks the join state of the availability replica.</span></span> <span data-ttu-id="80c97-114">可用性レプリカが可用性グループに追加されていても、適切に参加していない場合、ポリシーは異常な状態です。</span><span class="sxs-lookup"><span data-stu-id="80c97-114">The policy is in an unhealthy state when the availability replica is added to the availability group, but is not joined properly.</span></span> <span data-ttu-id="80c97-115">それ以外の場合、ポリシーは正常な状態です。</span><span class="sxs-lookup"><span data-stu-id="80c97-115">The policy is otherwise in a healthy state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="80c97-116">[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]のこのリリース向けに、TechNet Wiki の「 [Availability Replica Is not joined (可用性レプリカが参加していない)](https://go.microsoft.com/fwlink/p/?LinkId=220859) 」に、考えられるエラーの原因および解決方法に関する情報が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="80c97-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Availability replica is not joined](https://go.microsoft.com/fwlink/p/?LinkId=220859) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="80c97-117">考えられる原因</span><span class="sxs-lookup"><span data-stu-id="80c97-117">Possible Causes</span></span>  
 <span data-ttu-id="80c97-118">セカンダリ レプリカが可用性グループに参加していません。</span><span class="sxs-lookup"><span data-stu-id="80c97-118">The secondary replica is not joined to the availability group.</span></span> <span data-ttu-id="80c97-119">可用性レプリカを可用性グループに正しく参加させるには、参加状態が Joined Standalone Instance (1) または Joined Failover Cluster (2) である必要があります。</span><span class="sxs-lookup"><span data-stu-id="80c97-119">For an availability replica to be successfully joined to the availability group, the join state must be Joined Standalone Instance (1) or Joined Failover Cluster (2).</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="80c97-120">考えられる解決方法</span><span class="sxs-lookup"><span data-stu-id="80c97-120">Possible Solution</span></span>  
 <span data-ttu-id="80c97-121">Transact-SQL、PowerShell、または SQL Server Management Studio を使用して、セカンダリ レプリカを可用性グループに参加させます。</span><span class="sxs-lookup"><span data-stu-id="80c97-121">Use Transact-SQL, PowerShell, or SQL Server Management Studio to join the secondary replica to the availability group.</span></span> <span data-ttu-id="80c97-122">セカンダリ レプリカを可用性グループに参加させる方法の詳細については、「 [可用性グループへのセカンダリ レプリカの参加 (SQL Server)](https://msdn.microsoft.com/library/ff878473\(en-us,SQL.110\).aspx)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="80c97-122">For more information about joining secondary replicas to availability groups, see [Joining a Secondary Replica to an Availability Group (SQL Server)](https://msdn.microsoft.com/library/ff878473\(en-us,SQL.110\).aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80c97-123">参照</span><span class="sxs-lookup"><span data-stu-id="80c97-123">See Also</span></span>  
 <span data-ttu-id="80c97-124">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="80c97-124">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="80c97-125">AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="80c97-125">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
