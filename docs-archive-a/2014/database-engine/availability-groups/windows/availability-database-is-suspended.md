---
title: 可用性データベースが中断されている | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.drp1notsuspended.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 6baee70f-848c-4e86-b20d-78875c0f82cb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 07a547f217367f13df739348325461c862d831f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632135"
---
# <a name="availability-database-is-suspended"></a><span data-ttu-id="3a655-102">可用性データベースが中断されている</span><span class="sxs-lookup"><span data-stu-id="3a655-102">Availability database is suspended</span></span>
    
## <a name="introduction"></a><span data-ttu-id="3a655-103">はじめに</span><span class="sxs-lookup"><span data-stu-id="3a655-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3a655-104">**ポリシー名**</span><span class="sxs-lookup"><span data-stu-id="3a655-104">**Policy Name**</span></span>|<span data-ttu-id="3a655-105">可用性データベースの中断状態</span><span class="sxs-lookup"><span data-stu-id="3a655-105">Availability Database Suspension State</span></span>|  
|<span data-ttu-id="3a655-106">**問題点**</span><span class="sxs-lookup"><span data-stu-id="3a655-106">**Issue**</span></span>|<span data-ttu-id="3a655-107">可用性データベースが中断されています。</span><span class="sxs-lookup"><span data-stu-id="3a655-107">Availability database is suspended.</span></span>|  
|<span data-ttu-id="3a655-108">**カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="3a655-108">**Category**</span></span>|<span data-ttu-id="3a655-109">**警告**</span><span class="sxs-lookup"><span data-stu-id="3a655-109">**Warning**</span></span>|  
|<span data-ttu-id="3a655-110">**ファセット**</span><span class="sxs-lookup"><span data-stu-id="3a655-110">**Facet**</span></span>|<span data-ttu-id="3a655-111">可用性データベース</span><span class="sxs-lookup"><span data-stu-id="3a655-111">Availability database</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3a655-112">説明</span><span class="sxs-lookup"><span data-stu-id="3a655-112">Description</span></span>  
 <span data-ttu-id="3a655-113">このポリシーは、セカンダリ データベース ("セカンダリ データベース レプリカ" とも呼ばれます) のデータの移動状態をチェックします。</span><span class="sxs-lookup"><span data-stu-id="3a655-113">This policy checks the state of data movement of the secondary database (also known as a "secondary database replica").</span></span> <span data-ttu-id="3a655-114">データの移動が中断された場合、ポリシーは通常とは異なる状態です。</span><span class="sxs-lookup"><span data-stu-id="3a655-114">The policy is in an unhealthy state when the data movement is suspended.</span></span> <span data-ttu-id="3a655-115">それ以外の場合、ポリシーは正常な状態です。</span><span class="sxs-lookup"><span data-stu-id="3a655-115">The policy is otherwise in a healthy state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3a655-116">[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]のこのリリース向けに、TechNet Wiki の「 [可用性データベースが中断されている](https://go.microsoft.com/fwlink/p/?LinkId=220860) 」に、考えられるエラーの原因および解決方法に関する情報が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="3a655-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Availability database is suspended](https://go.microsoft.com/fwlink/p/?LinkId=220860) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="3a655-117">考えられる原因</span><span class="sxs-lookup"><span data-stu-id="3a655-117">Possible Causes</span></span>  
 <span data-ttu-id="3a655-118">この可用性データベースでのデータ同期が中断された原因として、次の原因が考えられます。</span><span class="sxs-lookup"><span data-stu-id="3a655-118">Data synchronization on this availability database might have been suspended because of the following:</span></span>  
  
-   <span data-ttu-id="3a655-119">エラーが原因でシステムによってデータの同期が中断された。</span><span class="sxs-lookup"><span data-stu-id="3a655-119">Due to an error, the system might have suspended data synchronization.</span></span>  
  
-   <span data-ttu-id="3a655-120">メンテナンスのためにデータベース管理者によってデータの同期が中断された。</span><span class="sxs-lookup"><span data-stu-id="3a655-120">The database administrator might have suspended data synchronization for maintenance purposes.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="3a655-121">考えられる解決方法</span><span class="sxs-lookup"><span data-stu-id="3a655-121">Possible Solution</span></span>  
 <span data-ttu-id="3a655-122">データの同期を再開します。</span><span class="sxs-lookup"><span data-stu-id="3a655-122">Resume data synchronization.</span></span> <span data-ttu-id="3a655-123">問題が解決しない場合は、イベント ログで可用性グループを調べ、データの移動が中断された原因を分析します。</span><span class="sxs-lookup"><span data-stu-id="3a655-123">If the issue persists, check the availability group in the Event log, and then diagnose why the system suspended data movement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a655-124">参照</span><span class="sxs-lookup"><span data-stu-id="3a655-124">See Also</span></span>  
 <span data-ttu-id="3a655-125">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3a655-125">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="3a655-126">AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="3a655-126">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
