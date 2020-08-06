---
title: 可用性データベースのデータ同期状態が正常でない | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.arp3datasynchealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 4fd003e7-808e-4b0e-b28a-47d9f2616f06
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a179008c20b108a2f6aaefd5dd80b22708e94a8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743446"
---
# <a name="data-synchronization-state-of-availability-database-is-not-healthy"></a><span data-ttu-id="ef706-102">可用性データベースのデータ同期状態が正常でない</span><span class="sxs-lookup"><span data-stu-id="ef706-102">Data synchronization state of availability database is not healthy</span></span>
    
## <a name="introduction"></a><span data-ttu-id="ef706-103">はじめに</span><span class="sxs-lookup"><span data-stu-id="ef706-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ef706-104">**ポリシー名**</span><span class="sxs-lookup"><span data-stu-id="ef706-104">**Policy Name**</span></span>|<span data-ttu-id="ef706-105">可用性データベースのデータ同期状態</span><span class="sxs-lookup"><span data-stu-id="ef706-105">Availability Database Data Synchronization State</span></span>|  
|<span data-ttu-id="ef706-106">**問題点**</span><span class="sxs-lookup"><span data-stu-id="ef706-106">**Issue**</span></span>|<span data-ttu-id="ef706-107">可用性データベースのデータ同期状態が正常ではありません。</span><span class="sxs-lookup"><span data-stu-id="ef706-107">Data synchronization state of availability database is not healthy.</span></span>|  
|<span data-ttu-id="ef706-108">**カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="ef706-108">**Category**</span></span>|<span data-ttu-id="ef706-109">**警告**</span><span class="sxs-lookup"><span data-stu-id="ef706-109">**Warning**</span></span>|  
|<span data-ttu-id="ef706-110">**ファセット**</span><span class="sxs-lookup"><span data-stu-id="ef706-110">**Facet**</span></span>|<span data-ttu-id="ef706-111">可用性データベース</span><span class="sxs-lookup"><span data-stu-id="ef706-111">Availability database</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ef706-112">説明</span><span class="sxs-lookup"><span data-stu-id="ef706-112">Description</span></span>  
 <span data-ttu-id="ef706-113">このポリシーは、可用性レプリカ内のすべての可用性データベース ("データベース レプリカ" とも呼ばれます) のデータ同期状態を集計します。</span><span class="sxs-lookup"><span data-stu-id="ef706-113">This policy rolls up the data synchronization state of all availability databases (also known as "database replicas") in the availability replica.</span></span> <span data-ttu-id="ef706-114">いずれかのデータベース レプリカが予想されるデータ同期状態ではない場合、ポリシーは通常とは異なる状態です。</span><span class="sxs-lookup"><span data-stu-id="ef706-114">The policy is in an unhealthy sate when any database replica is not in the expected data synchronization state.</span></span> <span data-ttu-id="ef706-115">それ以外の場合、ポリシーは正常な状態です。</span><span class="sxs-lookup"><span data-stu-id="ef706-115">The policy is otherwise in a healthy state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ef706-116">[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]のこのリリース向けに、TechNet Wiki の「 [一部の可用性データベースのデータ同期状態が正常でない](https://go.microsoft.com/fwlink/p/?LinkId=220858) 」に、考えられるエラーの原因および解決方法に関する情報が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="ef706-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Data synchronization state of some availability database is not healthy](https://go.microsoft.com/fwlink/p/?LinkId=220858) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="ef706-117">考えられる原因</span><span class="sxs-lookup"><span data-stu-id="ef706-117">Possible Causes</span></span>  
 <span data-ttu-id="ef706-118">この可用性データベースのデータ同期状態が正常ではありません。</span><span class="sxs-lookup"><span data-stu-id="ef706-118">The data synchronization state of this availability database is unhealthy.</span></span> <span data-ttu-id="ef706-119">非同期コミット可用性レプリカでは、各可用性データベースは SYNCHRONIZING 状態である必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef706-119">On an asynchronous-commit availability replica, every availability database should be in the SYNCHRONIZING state.</span></span> <span data-ttu-id="ef706-120">同期コミット レプリカでは、各可用性データベースは SYNCHRONIZED 状態である必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef706-120">On a synchronous-commit replica, every availability database must be in the SYNCHRONIZED state.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="ef706-121">考えられる解決方法</span><span class="sxs-lookup"><span data-stu-id="ef706-121">Possible Solution</span></span>  
 <span data-ttu-id="ef706-122">データベース レプリカ ポリシーを使用して通常とは異なるデータ同期状態のデータベース レプリカを見つけ、データベース レプリカの問題を解決します。</span><span class="sxs-lookup"><span data-stu-id="ef706-122">Use the database replica policy to find the database replica with an unhealthy data synchronization state, and then resolve the issue at the database replica.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef706-123">参照</span><span class="sxs-lookup"><span data-stu-id="ef706-123">See Also</span></span>  
 <span data-ttu-id="ef706-124">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ef706-124">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="ef706-125">AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="ef706-125">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
