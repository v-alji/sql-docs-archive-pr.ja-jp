---
title: 正常なロールのない可用性レプリカ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.arp1rolehealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: ebb2c9f4-2097-4688-b4fb-8f0571047317
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f7be26945903a5e3b602ef4a99c269de6a58b04a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716841"
---
# <a name="availability-replica-does-not-have-a-healthy-role"></a><span data-ttu-id="77418-102">正常なロールのない可用性レプリカ</span><span class="sxs-lookup"><span data-stu-id="77418-102">Availability replica does not have a healthy role</span></span>
    
## <a name="introduction"></a><span data-ttu-id="77418-103">はじめに</span><span class="sxs-lookup"><span data-stu-id="77418-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="77418-104">**ポリシー名**</span><span class="sxs-lookup"><span data-stu-id="77418-104">**Policy Name**</span></span>|<span data-ttu-id="77418-105">可用性レプリカのロールの状態</span><span class="sxs-lookup"><span data-stu-id="77418-105">Availability Replica Role State</span></span>|  
|<span data-ttu-id="77418-106">**問題点**</span><span class="sxs-lookup"><span data-stu-id="77418-106">**Issue**</span></span>|<span data-ttu-id="77418-107">可用性レプリカに正常なロールがありません。</span><span class="sxs-lookup"><span data-stu-id="77418-107">Availability replica does not have a healthy role.</span></span>|  
|<span data-ttu-id="77418-108">**カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="77418-108">**Category**</span></span>|<span data-ttu-id="77418-109">**重大**</span><span class="sxs-lookup"><span data-stu-id="77418-109">**Critical**</span></span>|  
|<span data-ttu-id="77418-110">**ファセット**</span><span class="sxs-lookup"><span data-stu-id="77418-110">**Facet**</span></span>|<span data-ttu-id="77418-111">可用性レプリカ</span><span class="sxs-lookup"><span data-stu-id="77418-111">Availability replica</span></span>|  
  
## <a name="description"></a><span data-ttu-id="77418-112">説明</span><span class="sxs-lookup"><span data-stu-id="77418-112">Description</span></span>  
 <span data-ttu-id="77418-113">このポリシーは、可用性レプリカのロールの状態をチェックします。</span><span class="sxs-lookup"><span data-stu-id="77418-113">This policy checks the state of the role of the availability replica.</span></span> <span data-ttu-id="77418-114">可用性レプリカのロールがプライマリでもセカンダリでもない場合、ポリシーは異常な状態です。</span><span class="sxs-lookup"><span data-stu-id="77418-114">The policy is in an unhealthy state when the role of the availability replica is neither primary nor secondary.</span></span> <span data-ttu-id="77418-115">それ以外の場合、ポリシーは正常な状態です。</span><span class="sxs-lookup"><span data-stu-id="77418-115">The policy is otherwise in a healthy state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="77418-116">[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]のこのリリース向けに、TechNet Wiki の「 [可用性レプリカに正常なロールがない](https://go.microsoft.com/fwlink/p/?LinkId=220856) 」に、考えられるエラーの原因および解決方法に関する情報が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="77418-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Availability replica does not have a healthy role](https://go.microsoft.com/fwlink/p/?LinkId=220856) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="77418-117">考えられる原因</span><span class="sxs-lookup"><span data-stu-id="77418-117">Possible Causes</span></span>  
 <span data-ttu-id="77418-118">この可用性レプリカのロールが正常ではありません。</span><span class="sxs-lookup"><span data-stu-id="77418-118">The role of this availability replica is unhealthy.</span></span> <span data-ttu-id="77418-119">このレプリカにはプライマリ ロールもセカンダリ ロールも割り当てられていません。</span><span class="sxs-lookup"><span data-stu-id="77418-119">The replica does not have either the primary or secondary role.</span></span>  
  
## <a name="possible-solution-information_still_to_come"></a><span data-ttu-id="77418-120">考えられる解決方法: ここに情報を挿入</span><span class="sxs-lookup"><span data-stu-id="77418-120">Possible Solution: Information_still_to_come</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77418-121">参照</span><span class="sxs-lookup"><span data-stu-id="77418-121">See Also</span></span>  
 <span data-ttu-id="77418-122">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="77418-122">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="77418-123">AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="77418-123">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
