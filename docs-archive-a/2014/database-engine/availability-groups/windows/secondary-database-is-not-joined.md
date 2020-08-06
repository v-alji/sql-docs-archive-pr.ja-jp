---
title: セカンダリ データベースが参加していない | Microsoft Docs
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.drp2joined.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 10817e5e-75fa-42dd-baa2-359bea3ad051
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 81275e85fd865924778f6d6f985e170a5bda9f9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740471"
---
# <a name="secondary-database-is-not-joined"></a><span data-ttu-id="a0900-102">セカンダリ データベースが参加していない</span><span class="sxs-lookup"><span data-stu-id="a0900-102">Secondary database is not joined</span></span>
    
## <a name="introduction"></a><span data-ttu-id="a0900-103">はじめに</span><span class="sxs-lookup"><span data-stu-id="a0900-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a0900-104">**ポリシー名**</span><span class="sxs-lookup"><span data-stu-id="a0900-104">**Policy Name**</span></span>|<span data-ttu-id="a0900-105">可用性データベースの参加状態</span><span class="sxs-lookup"><span data-stu-id="a0900-105">Availability Database Join State</span></span>|  
|<span data-ttu-id="a0900-106">**問題点**</span><span class="sxs-lookup"><span data-stu-id="a0900-106">**Issue**</span></span>|<span data-ttu-id="a0900-107">セカンダリ データベースが参加していません。</span><span class="sxs-lookup"><span data-stu-id="a0900-107">Secondary database is not joined.</span></span>|  
|<span data-ttu-id="a0900-108">**カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="a0900-108">**Category**</span></span>|<span data-ttu-id="a0900-109">**警告**</span><span class="sxs-lookup"><span data-stu-id="a0900-109">**Warning**</span></span>|  
|<span data-ttu-id="a0900-110">**ファセット**</span><span class="sxs-lookup"><span data-stu-id="a0900-110">**Facet**</span></span>|<span data-ttu-id="a0900-111">可用性データベース</span><span class="sxs-lookup"><span data-stu-id="a0900-111">Availability database</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a0900-112">説明</span><span class="sxs-lookup"><span data-stu-id="a0900-112">Description</span></span>  
 <span data-ttu-id="a0900-113">このポリシーは、セカンダリ データベース ("セカンダリ データベース レプリカ" とも呼ばれます) の参加状態をチェックします。</span><span class="sxs-lookup"><span data-stu-id="a0900-113">This policy checks the join state of the secondary database (also known as a "secondary database replica").</span></span> <span data-ttu-id="a0900-114">データセット レプリカが参加していない場合、ポリシーは通常とは異なる状態です。</span><span class="sxs-lookup"><span data-stu-id="a0900-114">The policy is in an unhealthy state when the dataset replica is not joined.</span></span> <span data-ttu-id="a0900-115">それ以外の場合、ポリシーは正常な状態です。</span><span class="sxs-lookup"><span data-stu-id="a0900-115">The policy is otherwise in a healthy state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a0900-116">[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]のこのリリース向けに、TechNet Wiki の「 [Secondary database is not joined](https://go.microsoft.com/fwlink/p/?LinkId=220862) 」 (セカンダリ データベースが参加していない) に、考えられるエラーの原因および解決方法に関する情報が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="a0900-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Secondary database is not joined](https://go.microsoft.com/fwlink/p/?LinkId=220862) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="a0900-117">考えられる原因</span><span class="sxs-lookup"><span data-stu-id="a0900-117">Possible Causes</span></span>  
 <span data-ttu-id="a0900-118">このセカンダリ データベースは可用性グループに参加していません。</span><span class="sxs-lookup"><span data-stu-id="a0900-118">This secondary database is not joined to the availability group.</span></span> <span data-ttu-id="a0900-119">このセカンダリ データベースの構成が不完全です。</span><span class="sxs-lookup"><span data-stu-id="a0900-119">The configuration of this secondary database is incomplete.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="a0900-120">考えられる解決方法</span><span class="sxs-lookup"><span data-stu-id="a0900-120">Possible Solution</span></span>  
 <span data-ttu-id="a0900-121">Transact-SQL、PowerShell、または SQL Server Management Studio を使用して、セカンダリ レプリカを可用性グループに参加させます。</span><span class="sxs-lookup"><span data-stu-id="a0900-121">Use Transact-SQL, PowerShell, or SQL Server Management Studio to join the secondary replica to the availability group.</span></span> <span data-ttu-id="a0900-122">セカンダリ レプリカを可用性グループに参加させる方法の詳細については、「 [可用性グループへのセカンダリ レプリカの参加 (SQL Server)](https://msdn.microsoft.com/library/ff878473\(en-us,SQL.110\).aspx)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a0900-122">For more information about joining secondary replicas to availability groups, see [Joining a Secondary Replica to an Availability Group (SQL Server)](https://msdn.microsoft.com/library/ff878473\(en-us,SQL.110\).aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0900-123">参照</span><span class="sxs-lookup"><span data-stu-id="a0900-123">See Also</span></span>  
 <span data-ttu-id="a0900-124">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a0900-124">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="a0900-125">AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="a0900-125">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
