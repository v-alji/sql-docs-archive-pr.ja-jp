---
title: いくつかの同期のレプリカが同期されていません | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp5synchronized.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: e58ed56e-4c30-42e6-a9fc-a8c401620e02
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ecef2d16e80e128834a71e1f1f112096f8ccc9cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641240"
---
# <a name="some-synchronous-replicas-are-not-synchronized"></a><span data-ttu-id="c1ea6-102">いくつかの同期のレプリカが同期されていません</span><span class="sxs-lookup"><span data-stu-id="c1ea6-102">Some synchronous replicas are not synchronized</span></span>
    
## <a name="introduction"></a><span data-ttu-id="c1ea6-103">はじめに</span><span class="sxs-lookup"><span data-stu-id="c1ea6-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c1ea6-104">**ポリシー名**</span><span class="sxs-lookup"><span data-stu-id="c1ea6-104">**Policy Name**</span></span>|<span data-ttu-id="c1ea6-105">同期レプリカのデータの同期状態</span><span class="sxs-lookup"><span data-stu-id="c1ea6-105">Synchronous Replicas Data Synchronization State</span></span>|  
|<span data-ttu-id="c1ea6-106">**問題点**</span><span class="sxs-lookup"><span data-stu-id="c1ea6-106">**Issue**</span></span>|<span data-ttu-id="c1ea6-107">一部の同期レプリカが同期されていません。</span><span class="sxs-lookup"><span data-stu-id="c1ea6-107">Some synchronous replicas are not synchronized.</span></span>|  
|<span data-ttu-id="c1ea6-108">**カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="c1ea6-108">**Category**</span></span>|<span data-ttu-id="c1ea6-109">**警告**</span><span class="sxs-lookup"><span data-stu-id="c1ea6-109">**Warning**</span></span>|  
|<span data-ttu-id="c1ea6-110">**ファセット**</span><span class="sxs-lookup"><span data-stu-id="c1ea6-110">**Facet**</span></span>|<span data-ttu-id="c1ea6-111">可用性グループ</span><span class="sxs-lookup"><span data-stu-id="c1ea6-111">Availability group</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c1ea6-112">説明</span><span class="sxs-lookup"><span data-stu-id="c1ea6-112">Description</span></span>  
 <span data-ttu-id="c1ea6-113">このポリシーは、すべての可用性レプリカのデータ同期状態をロール アップし、期待される状態とは異なる可用性レプリカがないかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="c1ea6-113">This policy rolls up the data synchronization state of all availability replicas and checks for any availability replicas that are not in the expected synchronization state.</span></span> <span data-ttu-id="c1ea6-114">非同期レプリカが SYNCHRONIZING 状態ではない場合、および同期レプリカが SYNCHRONIZED 状態ではない場合、ポリシーは異常な状態です。</span><span class="sxs-lookup"><span data-stu-id="c1ea6-114">The policy is in an unhealthy state when any asynchronous replica is not in a SYNCHRONIZING state and any synchronous replica is not in a SYNCHRONIZED state.</span></span> <span data-ttu-id="c1ea6-115">それ以外の場合、ポリシーは正常な状態です。</span><span class="sxs-lookup"><span data-stu-id="c1ea6-115">The policy state is otherwise healthy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c1ea6-116">[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]のこのリリース向けに、TechNet Wiki の「 [Some synchronous replicas are not synchronized (一部の同期レプリカが同期されていない)](https://go.microsoft.com/fwlink/p/?LinkId=220853) 」に、考えられるエラーの原因および解決方法に関する情報が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="c1ea6-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Some synchronous replicas are not synchronized](https://go.microsoft.com/fwlink/p/?LinkId=220853) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="c1ea6-117">考えられる原因</span><span class="sxs-lookup"><span data-stu-id="c1ea6-117">Possible Causes</span></span>  
 <span data-ttu-id="c1ea6-118">この可用性グループには、現在同期されていない同期レプリカが少なくとも 1 つ存在します。</span><span class="sxs-lookup"><span data-stu-id="c1ea6-118">In this availability group, at least one synchronous replica is not currently synchronized.</span></span> <span data-ttu-id="c1ea6-119">レプリカの同期状態は、SYNCHONIZING と NOT SYNCHRONIZING のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="c1ea6-119">The replica synchronization state could be either SYNCHONIZING or NOT SYNCHRONIZING.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="c1ea6-120">考えられる解決方法</span><span class="sxs-lookup"><span data-stu-id="c1ea6-120">Possible Solution</span></span>  
 <span data-ttu-id="c1ea6-121">可用性レプリカのポリシーの状態を検索条件として、同期状態が不適切な可用性レプリカを探し、問題を解決してください。</span><span class="sxs-lookup"><span data-stu-id="c1ea6-121">Use the availability replica policy state to find the availability replica with the incorrect synchronization state, and then resolve the issue at the availability replica.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1ea6-122">参照</span><span class="sxs-lookup"><span data-stu-id="c1ea6-122">See Also</span></span>  
 <span data-ttu-id="c1ea6-123">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c1ea6-123">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="c1ea6-124">AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="c1ea6-124">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
