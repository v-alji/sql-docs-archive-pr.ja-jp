---
title: WSFC クラスター サービスはオフライン | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp1WSFCquorum.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: d502548d-ece6-4a42-9ded-2157d33e3d21
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e6e7b48f96eb09638291b1d0655d385d606b1666
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716825"
---
# <a name="wsfc-cluster-service-is-offline"></a><span data-ttu-id="024c1-102">WSFC クラスター サービスはオフライン</span><span class="sxs-lookup"><span data-stu-id="024c1-102">WSFC cluster service is offline</span></span>
    
## <a name="introduction"></a><span data-ttu-id="024c1-103">はじめに</span><span class="sxs-lookup"><span data-stu-id="024c1-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="024c1-104">**ポリシー名**</span><span class="sxs-lookup"><span data-stu-id="024c1-104">**Policy Name**</span></span>|<span data-ttu-id="024c1-105">WSFC クラスターの状態</span><span class="sxs-lookup"><span data-stu-id="024c1-105">WSFC Cluster State</span></span>|  
|<span data-ttu-id="024c1-106">**問題点**</span><span class="sxs-lookup"><span data-stu-id="024c1-106">**Issue**</span></span>|<span data-ttu-id="024c1-107">WSFC クラスター サービスはオフラインです。</span><span class="sxs-lookup"><span data-stu-id="024c1-107">WSFC cluster service is offline.</span></span>|  
|<span data-ttu-id="024c1-108">**カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="024c1-108">**Category**</span></span>|<span data-ttu-id="024c1-109">**重大**</span><span class="sxs-lookup"><span data-stu-id="024c1-109">**Critical**</span></span>|  
|<span data-ttu-id="024c1-110">**ファセット**</span><span class="sxs-lookup"><span data-stu-id="024c1-110">**Facet**</span></span>|<span data-ttu-id="024c1-111">SQL Server のインスタンス</span><span class="sxs-lookup"><span data-stu-id="024c1-111">Instance of SQL Server</span></span>|  
  
## <a name="description"></a><span data-ttu-id="024c1-112">説明</span><span class="sxs-lookup"><span data-stu-id="024c1-112">Description</span></span>  
 <span data-ttu-id="024c1-113">このポリシーは、Windows Server フェールオーバー クラスター (WSFC) の状態をチェックします。</span><span class="sxs-lookup"><span data-stu-id="024c1-113">This policy checks the state of the Windows Server Failover Cluster (WSFC).</span></span> <span data-ttu-id="024c1-114">WSFC クラスターがオフラインであるか、強制されたクォーラムの状態である場合、ポリシーは異常な状態で、アラートが発生します。</span><span class="sxs-lookup"><span data-stu-id="024c1-114">The policy is in an unhealthy state and an alert is raised when the WSFC cluster is offline or in the forced quorum state.</span></span> <span data-ttu-id="024c1-115">このクラスター内でホストされているすべての可用性グループはオフラインであるか、またはディザスター リカバリー アクションが必要です。</span><span class="sxs-lookup"><span data-stu-id="024c1-115">All availability groups hosted within this cluster are offline or a disaster recovery action is required.</span></span>  
  
 <span data-ttu-id="024c1-116">クラスターの状態が標準のクォーラムである場合、ポリシーは正常な状態です。</span><span class="sxs-lookup"><span data-stu-id="024c1-116">The policy state is healthy when the cluster state is in the normal quorum.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="024c1-117">[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]のこのリリース向けに、TechNet Wiki の「 [WSFC クラスター サービスがオフライン](https://go.microsoft.com/fwlink/p/?LinkId=220849) 」に、考えられるエラーの原因および解決方法に関する情報が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="024c1-117">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [WSFC cluster service is offline](https://go.microsoft.com/fwlink/p/?LinkId=220849) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="024c1-118">考えられる原因</span><span class="sxs-lookup"><span data-stu-id="024c1-118">Possible Causes</span></span>  
 <span data-ttu-id="024c1-119">この問題は、クラスター サービスの問題や、クラスターのクォーラムの損失によって発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="024c1-119">This issue can be caused by a cluster service issue or by the loss of the quorum in the cluster.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="024c1-120">考えられる解決方法</span><span class="sxs-lookup"><span data-stu-id="024c1-120">Possible Solution</span></span>  
 <span data-ttu-id="024c1-121">クラスター アドミニストレーター ツールを使用して、強制クォーラムまたはディザスター リカバリー ワークフローを実行できます。</span><span class="sxs-lookup"><span data-stu-id="024c1-121">Use the Cluster Administrator tool to perform the forced quorum or disaster recovery workflow.</span></span> <span data-ttu-id="024c1-122">強制クォーラムまたはディザスター リカバリーを行っても問題が解決されない場合は、クラスター アドミニストレーターに問題の解決を依頼してください。</span><span class="sxs-lookup"><span data-stu-id="024c1-122">If you cannot resolve the issue by performing the forced quorum or disaster recovery, contact your cluster administrator to help resolve this issue.</span></span> <span data-ttu-id="024c1-123">詳細については、 [オンライン ブックの「](../../../sql-server/failover-clusters/windows/force-a-wsfc-cluster-to-start-without-a-quorum.md) クォーラムを使用せずに WSFC クラスターを強制的に起動する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="024c1-123">For more information, see [Force a WSFC Cluster to Start Without a Quorum](../../../sql-server/failover-clusters/windows/force-a-wsfc-cluster-to-start-without-a-quorum.md) in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="024c1-124">参照</span><span class="sxs-lookup"><span data-stu-id="024c1-124">See Also</span></span>  
 <span data-ttu-id="024c1-125">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="024c1-125">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="024c1-126">AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="024c1-126">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
