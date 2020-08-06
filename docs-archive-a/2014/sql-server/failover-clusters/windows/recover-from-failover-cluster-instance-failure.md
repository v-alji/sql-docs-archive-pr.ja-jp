---
title: フェールオーバー クラスター インスタンス障害からの復旧 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- clusters [SQL Server], recovery from failure
- failover clustering [SQL Server], recovery from failure
- hardware failures [SQL Server]
- recovering failover cluster failures [SQL Server]
ms.assetid: 3d151d0c-e841-4325-8606-c094de37d7d1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 60db4c2e480b094c18d0a8071e947a38cdc779d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740753"
---
# <a name="recover-from-failover-cluster-instance-failure"></a><span data-ttu-id="41adf-102">フェールオーバー クラスター インスタンス障害からの復旧</span><span class="sxs-lookup"><span data-stu-id="41adf-102">Recover from Failover Cluster Instance Failure</span></span>
  <span data-ttu-id="41adf-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]でフェールオーバーが発生した後にフェールオーバー クラスター マネージャー スナップインを使用してクラスター障害から復旧する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="41adf-103">This topic describes how to recover from cluster failures by using the Failover Cluster Manager snap-in after a failover occurs in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="41adf-104">フェールオーバー クラスター マネージャー スナップインは、Windows Server フェールオーバー クラスタリング (WSFC) サービスのクラスター管理アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="41adf-104">The Failover Cluster Manager snap-in is the cluster management application for the Windows Serer Failover Clustering (WSFC) service.</span></span>  
  
-   [<span data-ttu-id="41adf-105">修復不可能な障害からの復旧</span><span class="sxs-lookup"><span data-stu-id="41adf-105">Recover from an irreparable failure</span></span>](#Scenario1)  
  
-   [<span data-ttu-id="41adf-106">ソフトウェア障害からの復旧</span><span class="sxs-lookup"><span data-stu-id="41adf-106">Recover from a software failure</span></span>](#Scenario2)  
  
##  <a name="recover-from-an-irreparable-failure"></a><a name="Scenario1"></a><span data-ttu-id="41adf-107">修復不可能な障害からの復旧</span><span class="sxs-lookup"><span data-stu-id="41adf-107">Recover from an irreparable failure</span></span>  
 <span data-ttu-id="41adf-108">修復不可能な障害から復旧するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="41adf-108">Use the following steps to recover from an irreparable failure.</span></span> <span data-ttu-id="41adf-109">この障害の原因としては、ディスク コントローラーやオペレーティング システムの異常などが考えられます。</span><span class="sxs-lookup"><span data-stu-id="41adf-109">The failure could be caused, for example, by the failure of a disk controller or the operating system.</span></span> <span data-ttu-id="41adf-110">この例では、2 ノード クラスターのノード 1 でハードウェア障害が発生したものとします。</span><span class="sxs-lookup"><span data-stu-id="41adf-110">In this case, failure is caused by hardware failure in Node 1 of a two-node cluster.</span></span>  
  
1.  <span data-ttu-id="41adf-111">ノード 1 で障害が発生した後、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] FCI がノード 2 にフェールオーバーされます。</span><span class="sxs-lookup"><span data-stu-id="41adf-111">After Node 1 fails, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] FCI fails over to Node 2.</span></span>  
  
2.  <span data-ttu-id="41adf-112">FCI からノード 1 を削除します。</span><span class="sxs-lookup"><span data-stu-id="41adf-112">Evict Node 1 from the FCI.</span></span> <span data-ttu-id="41adf-113">そのためには、ノード 2 でフェールオーバー クラスター マネージャー スナップインを開きます。ノード 1 を右クリックし、 **[移動アクション]** をクリックし、 **[ノードの削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="41adf-113">To do this, from Node 2, open the Failover Cluster Manager snap-in, right-click Node1, click **Move Actions**, and then click **Evict Node**.</span></span>  
  
3.  <span data-ttu-id="41adf-114">ノード 1 がクラスターの定義から削除されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="41adf-114">Verify that Node 1 has been evicted from the cluster definition.</span></span>  
  
4.  <span data-ttu-id="41adf-115">新しいハードウェアをインストールし、ノード 1 で故障したハードウェアと交換します。</span><span class="sxs-lookup"><span data-stu-id="41adf-115">Install new hardware to replace the failed hardware in Node 1.</span></span>  
  
5.  <span data-ttu-id="41adf-116">フェールオーバー クラスター マネージャー スナップインを使用して、ノード 1 を既存のクラスターに追加します。</span><span class="sxs-lookup"><span data-stu-id="41adf-116">Using the Failover Cluster Manager snap-in, add Node 1 to the existing cluster.</span></span> <span data-ttu-id="41adf-117">詳細については、「 [フェールオーバー クラスタリングをインストールする前に](../install/before-installing-failover-clustering.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="41adf-117">For more information, see [Before Installing Failover Clustering](../install/before-installing-failover-clustering.md).</span></span>  
  
6.  <span data-ttu-id="41adf-118">管理者アカウントは、すべてのクラスター ノードで同じになるようにします。</span><span class="sxs-lookup"><span data-stu-id="41adf-118">Ensure that the administrator accounts are the same on all cluster nodes.</span></span>  
  
7.  <span data-ttu-id="41adf-119">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] セットアップを実行してノード 1 を FCI に追加します。</span><span class="sxs-lookup"><span data-stu-id="41adf-119">Run [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Setup to add Node 1 to the FCI.</span></span> <span data-ttu-id="41adf-120">詳細については、「 [SQL Server フェールオーバークラスターでのノードの追加または削除」 &#40;セットアップ&#41;](../install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="41adf-120">For more information, see [Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;](../install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).</span></span>  
  
##  <a name="recover-from-a-reparable-failure"></a><a name="Scenario2"></a><span data-ttu-id="41adf-121">修復可能障害からの復旧</span><span class="sxs-lookup"><span data-stu-id="41adf-121">Recover from a reparable failure</span></span>  
 <span data-ttu-id="41adf-122">修復可能な障害から復旧するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="41adf-122">Us the following steps to recover from a reparable failure.</span></span> <span data-ttu-id="41adf-123">このケースでは、障害の原因はダウンまたはオフラインになっているノード 1 です。ただし、復旧できないほどの損傷ではありません。</span><span class="sxs-lookup"><span data-stu-id="41adf-123">In this case, failure is caused by Node 1 being down or offline but not irretrievably broken.</span></span> <span data-ttu-id="41adf-124">この障害の原因としては、オペレーティング システム、ハードウェア、または [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス自体の障害が考えられます。</span><span class="sxs-lookup"><span data-stu-id="41adf-124">This could be caused by an operating system failure, hardware failure, or failure in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance itself.</span></span>  
  
1.  <span data-ttu-id="41adf-125">ノード 1 で障害が発生した後、FCI がノード 2 にフェールオーバーされます。</span><span class="sxs-lookup"><span data-stu-id="41adf-125">After Node 1 fails, the FCI fails over to Node 2.</span></span>  
  
2.  <span data-ttu-id="41adf-126">ノード 1 の問題を解決します。</span><span class="sxs-lookup"><span data-stu-id="41adf-126">Resolve the problem with Node 1.</span></span>  
  
3.  <span data-ttu-id="41adf-127">すべてのノードがオンライン状態であり、WSFC サービスが動作していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="41adf-127">Ensure that all nodes are online and the WSFC service is working.</span></span>  
  
4.  <span data-ttu-id="41adf-128">復旧したノードに [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] をフェールオーバーします。</span><span class="sxs-lookup"><span data-stu-id="41adf-128">Fail over [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to the recovered node.</span></span>  
  
  
