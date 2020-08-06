---
title: 可用性レプリカが切断されている | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.arp2connected.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 1a2162d3-54fb-4356-b349-effbdc15a5a4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1db92b8e73b6daaee7edf5042b1d73cfeb471d1d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716834"
---
# <a name="availability-replica-is-disconnected"></a><span data-ttu-id="6dafa-102">可用性レプリカが切断されている</span><span class="sxs-lookup"><span data-stu-id="6dafa-102">Availability replica is disconnected</span></span>
    
## <a name="introduction"></a><span data-ttu-id="6dafa-103">はじめに</span><span class="sxs-lookup"><span data-stu-id="6dafa-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6dafa-104">**ポリシー名**</span><span class="sxs-lookup"><span data-stu-id="6dafa-104">**Policy Name**</span></span>|<span data-ttu-id="6dafa-105">可用性レプリカの接続状態</span><span class="sxs-lookup"><span data-stu-id="6dafa-105">Availability Replica Connection State</span></span>|  
|<span data-ttu-id="6dafa-106">**問題点**</span><span class="sxs-lookup"><span data-stu-id="6dafa-106">**Issue**</span></span>|<span data-ttu-id="6dafa-107">可用性レプリカの接続が解除されます。</span><span class="sxs-lookup"><span data-stu-id="6dafa-107">Availability replica is disconnected.</span></span>|  
|<span data-ttu-id="6dafa-108">**カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="6dafa-108">**Category**</span></span>|<span data-ttu-id="6dafa-109">**重大**</span><span class="sxs-lookup"><span data-stu-id="6dafa-109">**Critical**</span></span>|  
|<span data-ttu-id="6dafa-110">**ファセット**</span><span class="sxs-lookup"><span data-stu-id="6dafa-110">**Facet**</span></span>|<span data-ttu-id="6dafa-111">可用性レプリカ</span><span class="sxs-lookup"><span data-stu-id="6dafa-111">Availability replica</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6dafa-112">説明</span><span class="sxs-lookup"><span data-stu-id="6dafa-112">Description</span></span>  
 <span data-ttu-id="6dafa-113">このポリシーは、可用性レプリカ間の接続状態を確認します。</span><span class="sxs-lookup"><span data-stu-id="6dafa-113">This policy checks the connection state between availability replicas.</span></span> <span data-ttu-id="6dafa-114">可用性レプリカ間の接続状態が DISCONNECTED の場合、ポリシーは通常とは異なる状態です。</span><span class="sxs-lookup"><span data-stu-id="6dafa-114">The policy is in an unhealthy state when the connection state of the availability replica is DISCONNECTED.</span></span> <span data-ttu-id="6dafa-115">それ以外の場合、ポリシーは正常な状態です。</span><span class="sxs-lookup"><span data-stu-id="6dafa-115">The policy is otherwise in a healthy state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6dafa-116">[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]のこのリリース向けに、TechNet Wiki の「 [可用性レプリカの接続が解除される](https://go.microsoft.com/fwlink/p/?LinkId=220857) 」に、考えられるエラーの原因および解決方法に関する情報が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="6dafa-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Availability replica is disconnected](https://go.microsoft.com/fwlink/p/?LinkId=220857) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="6dafa-117">考えられる原因</span><span class="sxs-lookup"><span data-stu-id="6dafa-117">Possible Causes</span></span>  
 <span data-ttu-id="6dafa-118">セカンダリ レプリカがプライマリ レプリカに接続されていません。</span><span class="sxs-lookup"><span data-stu-id="6dafa-118">The secondary replica is not connected to the primary replica.</span></span> <span data-ttu-id="6dafa-119">接続状態は DISCONNECTED です。</span><span class="sxs-lookup"><span data-stu-id="6dafa-119">The connected state is DISCONNECTED.</span></span> <span data-ttu-id="6dafa-120">この問題は、次の状況で発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6dafa-120">This issue can be caused by the following:</span></span>  
  
-   <span data-ttu-id="6dafa-121">接続ポートが他のアプリケーションと競合状態にある。</span><span class="sxs-lookup"><span data-stu-id="6dafa-121">The connection port might be in conflict with another application.</span></span>  
  
-   <span data-ttu-id="6dafa-122">暗号化の種類またはアルゴリズムが一致しない。</span><span class="sxs-lookup"><span data-stu-id="6dafa-122">The encryption type or algorithm is mismatched.</span></span>  
  
-   <span data-ttu-id="6dafa-123">接続エンドポイントが削除されているか、開始されていない。</span><span class="sxs-lookup"><span data-stu-id="6dafa-123">The connection endpoint has been deleted or has not been started.</span></span>  
  
-   <span data-ttu-id="6dafa-124">トランスポートが切断されている。</span><span class="sxs-lookup"><span data-stu-id="6dafa-124">The transport is disconnected.</span></span>  
  
## <a name="possible-solutions"></a><span data-ttu-id="6dafa-125">考えられる解決策</span><span class="sxs-lookup"><span data-stu-id="6dafa-125">Possible Solutions</span></span>  
 <span data-ttu-id="6dafa-126">この問題に対して考えられる解決策を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6dafa-126">Following are possible solutions for this issue:</span></span>  
  
-   <span data-ttu-id="6dafa-127">プライマリ レプリカおよびセカンダリ レプリカのインスタンスのデータベース ミラーリング エンドポイントの構成を確認し、対応していない構成を更新します。</span><span class="sxs-lookup"><span data-stu-id="6dafa-127">Check the database mirroring endpoint configuration for the instances of the primary and secondary replica and update the mismatched configuration.</span></span>  
  
-   <span data-ttu-id="6dafa-128">ポートが競合しているかどうかを確認し、競合している場合はポート番号を変更します。</span><span class="sxs-lookup"><span data-stu-id="6dafa-128">Check if the port is conflicting, and if so, change the port number.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dafa-129">参照</span><span class="sxs-lookup"><span data-stu-id="6dafa-129">See Also</span></span>  
 <span data-ttu-id="6dafa-130">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6dafa-130">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="6dafa-131">AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="6dafa-131">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
