---
title: 一部の可用性レプリカでデータが同期されない | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp4synchronizing.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 3db6a569-e942-4321-a0dd-c4ab002087c8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 762b7da1f7b8a07257c2a900307eb1bb10408653
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641246"
---
# <a name="some-availability-replicas-are-not-synchronizing-data"></a><span data-ttu-id="bc958-102">一部の可用性レプリカでデータが同期されない</span><span class="sxs-lookup"><span data-stu-id="bc958-102">Some availability replicas are not synchronizing data</span></span>
    
## <a name="introduction"></a><span data-ttu-id="bc958-103">はじめに</span><span class="sxs-lookup"><span data-stu-id="bc958-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bc958-104">**ポリシー名**</span><span class="sxs-lookup"><span data-stu-id="bc958-104">**Policy Name**</span></span>|<span data-ttu-id="bc958-105">可用性レプリカのデータ同期状態</span><span class="sxs-lookup"><span data-stu-id="bc958-105">Availability Replicas Data Synchronization State</span></span>|  
|<span data-ttu-id="bc958-106">**問題点**</span><span class="sxs-lookup"><span data-stu-id="bc958-106">**Issue**</span></span>|<span data-ttu-id="bc958-107">一部の可用性レプリカでデータが同期されません。</span><span class="sxs-lookup"><span data-stu-id="bc958-107">Some availability replicas are not synchronizing data.</span></span>|  
|<span data-ttu-id="bc958-108">**カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="bc958-108">**Category**</span></span>|<span data-ttu-id="bc958-109">**警告**</span><span class="sxs-lookup"><span data-stu-id="bc958-109">**Warning**</span></span>|  
|<span data-ttu-id="bc958-110">**ファセット**</span><span class="sxs-lookup"><span data-stu-id="bc958-110">**Facet**</span></span>|<span data-ttu-id="bc958-111">可用性グループ</span><span class="sxs-lookup"><span data-stu-id="bc958-111">Availability group</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bc958-112">説明</span><span class="sxs-lookup"><span data-stu-id="bc958-112">Description</span></span>  
 <span data-ttu-id="bc958-113">このポリシーは、可用性グループのすべての可用性レプリカのデータ同期状態をロール アップし、可用性レプリカの同期が稼働しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="bc958-113">This policy rolls up the data synchronization state of all availability replicas in the availability group and checks if the synchronization of any availability replica is not operational.</span></span> <span data-ttu-id="bc958-114">可用性レプリカのデータ同期状態が NOT SYNCHRONIZING の場合、ポリシーは通常とは異なる状態です。</span><span class="sxs-lookup"><span data-stu-id="bc958-114">The policy is in an unhealthy state if any of the data synchronization states of the availability replica is NOT SYNCRONIZING.</span></span>  
  
 <span data-ttu-id="bc958-115">可用性レプリカのデータ同期状態が NOT SYNCHRONIZING でない場合、ポリシーは正常な状態です。</span><span class="sxs-lookup"><span data-stu-id="bc958-115">This policy is in a healthy state if none of the data synchronization states of the availability replica is NOT SYNCHRONIZING.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bc958-116">[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]のこのリリース向けに、TechNet Wiki の「 [一部の可用性レプリカでデータが同期されない](https://go.microsoft.com/fwlink/p/?LinkId=220852) 」に、考えられるエラーの原因および解決方法に関する情報が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="bc958-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Some availability replicas are not synchronizing data](https://go.microsoft.com/fwlink/p/?LinkId=220852) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="bc958-117">考えられる原因</span><span class="sxs-lookup"><span data-stu-id="bc958-117">Possible Causes</span></span>  
 <span data-ttu-id="bc958-118">この可用性グループで、少なくとも 1 つのセカンダリ レプリカが NOT SYNCHRONIZING 同期状態であり、プライマリ レプリカからデータを受け取っていません。</span><span class="sxs-lookup"><span data-stu-id="bc958-118">In this availability group, at least one secondary replica has a NOT SYNCHRONIZING synchronization state and is not receiving data from the primary replica.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="bc958-119">考えられる解決方法</span><span class="sxs-lookup"><span data-stu-id="bc958-119">Possible Solution</span></span>  
 <span data-ttu-id="bc958-120">可用性レプリカのポリシーの状態を検索条件として、NOT SYNCHRONIZING 状態の可用性レプリカを探し、問題を解決してください。</span><span class="sxs-lookup"><span data-stu-id="bc958-120">Use the availability replica policy state to find the availability replica with a NOT SYNCHROINIZING state, and then resolve the issue at the availability replica.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc958-121">参照</span><span class="sxs-lookup"><span data-stu-id="bc958-121">See Also</span></span>  
 <span data-ttu-id="bc958-122">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bc958-122">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="bc958-123">AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="bc958-123">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
