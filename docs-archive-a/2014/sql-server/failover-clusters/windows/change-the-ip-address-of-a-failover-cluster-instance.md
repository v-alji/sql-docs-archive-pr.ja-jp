---
title: フェールオーバー クラスター インスタンスの IP アドレスの変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- modifying IP addresses
- failover clustering [SQL Server], IP addresses
- IP addresses [SQL Server]
- clusters [SQL Server], IP addresses
ms.assetid: b685f400-cbfe-4c5d-a070-227a1123dae4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 45d3ef0b70282efd870e4a076663719c2549deaa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640536"
---
# <a name="change-the-ip-address-of-a-failover-cluster-instance"></a><span data-ttu-id="e631b-102">フェールオーバー クラスター インスタンスの IP アドレスの変更</span><span class="sxs-lookup"><span data-stu-id="e631b-102">Change the IP Address of a Failover Cluster Instance</span></span>
  <span data-ttu-id="e631b-103">このトピックでは、フェールオーバー クラスター マネージャー スナップインを使用して、AlwaysOn フェールオーバー クラスター インスタンス (FCI) の IP アドレス リソースを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e631b-103">This topic describes how to change the IP address resource in an AlwaysOn Failover Cluster Instance (FCI) by using the Failover Cluster Manager snap-in.</span></span> <span data-ttu-id="e631b-104">フェールオーバー クラスター マネージャー スナップインは、Windows Server フェールオーバー クラスタリング (WSFC) サービスのクラスター管理アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="e631b-104">The Failover Cluster Manager snap-in is the cluster management application for the Windows Server Failover Clustering (WSFC) service.</span></span>  
  
-   <span data-ttu-id="e631b-105">**作業を開始する準備:** [セキュリティ](#Security)</span><span class="sxs-lookup"><span data-stu-id="e631b-105">**Before you begin:**  [Security](#Security)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e631b-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="e631b-106">Before You Begin</span></span>  
 <span data-ttu-id="e631b-107">開始する前に、「 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オンライン ブックのトピック: [フェールオーバー クラスタ リングをインストールする前に](../install/before-installing-failover-clustering.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e631b-107">Before you begin, review the following [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online topic: [Before Installing Failover Clustering](../install/before-installing-failover-clustering.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e631b-108">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="e631b-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e631b-109">Permissions</span><span class="sxs-lookup"><span data-stu-id="e631b-109">Permissions</span></span>  
 <span data-ttu-id="e631b-110">FCI を保持または更新するには、FCI のすべてのノードにおいて、サービスとしてログオンする権限を持つローカル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="e631b-110">To maintain or update an FCI, you must be a local administrator with permission to logon as a service on all nodes of the FCI.</span></span>  
  
##  <a name="using-the-failover-cluster-manager-snap-in"></a><a name="WSFC"></a> <span data-ttu-id="e631b-111">フェールオーバー クラスター マネージャー スナップインの使用</span><span class="sxs-lookup"><span data-stu-id="e631b-111">Using the Failover Cluster Manager Snap-in</span></span>  
 <span data-ttu-id="e631b-112">**FCI の IP アドレス リソースを変更するには**</span><span class="sxs-lookup"><span data-stu-id="e631b-112">**To change the IP address resource for an FCI**</span></span>  
  
1.  <span data-ttu-id="e631b-113">フェールオーバー クラスター マネージャー スナップインを開きます。</span><span class="sxs-lookup"><span data-stu-id="e631b-113">Open the Failover Cluster Manager snap-in.</span></span>  
  
2.  <span data-ttu-id="e631b-114">左側のペインで、 **[サービスとアプリケーション]** ノードを展開し、FCI をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e631b-114">Expand the **Services and applications** node, in the left pane and click on the FCI.</span></span>  
  
3.  <span data-ttu-id="e631b-115">右側のペインの **[サーバー名]** カテゴリの下で、SQL Server インスタンスを右クリックし、 **[プロパティ]** をクリックして **プロパティ** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="e631b-115">On the right pane, under the **Server Name** category, right-click the SQL Server Instance, and select **Properties** option to open the **Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="e631b-116">**[全般]** タブで、IP アドレス リソースを変更します。</span><span class="sxs-lookup"><span data-stu-id="e631b-116">On the **General** tab, change the IP address resource.</span></span>  
  
5.  <span data-ttu-id="e631b-117">**[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e631b-117">Click **OK** to close the dialog box.</span></span>  
  
6.  <span data-ttu-id="e631b-118">右側のペインで、[SQL IP Address1 (フェールオーバー クラスターのインスタンス名)] を右クリックし、 **[オフラインにする]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e631b-118">In the right-hand pane, right-click the SQL IP Address1(failover cluster instance name) and select **Take Offline**.</span></span> <span data-ttu-id="e631b-119">[SQL IP Address1 (フェールオーバー クラスターのインスタンス名)]、[SQL Network Name (フェールオーバー クラスターのインスタンス名)]、および [ [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ] の状態が、[オンライン]、[オフライン待ち]、[オフライン] と変化していくのを確認できます。</span><span class="sxs-lookup"><span data-stu-id="e631b-119">You will see the SQL IP Address1(failover cluster instance name), SQL Network Name(failover cluster instance name), and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] status change from Online to Offline Pending, and then to Offline.</span></span>  
  
7.  <span data-ttu-id="e631b-120">右側のペインで、[ [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]] を右クリックし、 **[オンラインにする]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e631b-120">In the right-hand pane, right-click [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], and then select **Bring Online**.</span></span> <span data-ttu-id="e631b-121">[SQL IP Address1 (フェールオーバー クラスターのインスタンス名)]、[SQL Network Name (フェールオーバー クラスターのインスタンス名)]、および [ [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ] の状態が、[オフライン]、[オンライン待ち]、[オンライン] と変化していくのを確認できます。</span><span class="sxs-lookup"><span data-stu-id="e631b-121">You will see the SQL IP Address1(failover cluster instance name), SQL Network Name(failover cluster instance name), and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] status change from Offline to Online Pending, and then to Online.</span></span>  
  
8.  <span data-ttu-id="e631b-122">フェールオーバー クラスター マネージャー スナップインを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e631b-122">Close the Failover Cluster Manager snap-in.</span></span>  
  
  
