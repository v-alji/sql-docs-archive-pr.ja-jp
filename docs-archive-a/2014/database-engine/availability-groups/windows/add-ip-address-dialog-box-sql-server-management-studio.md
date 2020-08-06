---
title: '[IP アドレスの追加] ダイアログ ボックス (SQL Server Management Studio) | Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygrouplistener.addipaddress.f1
ms.assetid: 98c9ad3b-ff3c-4c1d-b344-59a72fca137c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5192e6414b34bee6de09d45a7284f25404235dc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632716"
---
# <a name="add-ip-address-dialog-box-sql-server-management-studio"></a><span data-ttu-id="95dfd-102">[IP アドレスの追加] ダイアログ ボックス (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="95dfd-102">Add IP Address Dialog Box (SQL Server Management Studio)</span></span>
  <span data-ttu-id="95dfd-103">この F1 ヘルプ トピックでは、 **[IP アドレスの追加]** ダイアログ ボックスのオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="95dfd-103">This F1 help topic describes the options of the **Add IP Address** dialog box.</span></span> <span data-ttu-id="95dfd-104">このダイアログ ボックスには、 **[新しい可用性グループ リスナー]** ダイアログ ボックスと **[リスナー]** タブ ( **の** または [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] の [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] [レプリカの指定] [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]ページ上) からアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="95dfd-104">This dialog box accessed from the **New Availability Group Listener** dialog box and the **Listener** tab of the **Specify Replicas** page of the [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] or the [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="95dfd-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="95dfd-105">Prerequisites</span></span>  
 <span data-ttu-id="95dfd-106">サブネットを可用性グループ リスナーに追加するには、サブネットごとの IP アドレスと、IPv4 アドレスのサブネット マスクを把握している必要があります。</span><span class="sxs-lookup"><span data-stu-id="95dfd-106">Before you begin to add subnets to an availability group listener, ensure that know the IP address for each subnet and, for an IPv4 address, the subnet mask.</span></span>  
  
##  <a name="add-ip-address-options"></a><a name="PageOptions"></a> <span data-ttu-id="95dfd-107">[IP アドレスの追加] オプション</span><span class="sxs-lookup"><span data-stu-id="95dfd-107">Add IP Address Options</span></span>  
 <span data-ttu-id="95dfd-108">**サブネット**</span><span class="sxs-lookup"><span data-stu-id="95dfd-108">**Subnet**</span></span>  
 <span data-ttu-id="95dfd-109">ドロップダウン リストを使用して、可用性グループ リスナーに追加するサブネットのアドレスを選択します。</span><span class="sxs-lookup"><span data-stu-id="95dfd-109">Use the drop list to select an address for the subnet that you are adding to the availability group listener.</span></span> <span data-ttu-id="95dfd-110">既定では、サブネットには IPv4 アドレスと IPv6 アドレスの両方があります。</span><span class="sxs-lookup"><span data-stu-id="95dfd-110">By default a subnet possesses both an IPv4 address and an IPv6 address.</span></span> <span data-ttu-id="95dfd-111">**[IP アドレスの追加]** ダイアログを初めて使用するときは、 **[サブネット]** ボックスの一覧に、可用性グループのレプリカをホストするサブネットごとに両方のサブネット アドレスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="95dfd-111">The first time you use the **Add IP Address** dialog,  the **Subnet** drop list displays both subnet addresses for each subnet that hosts a replica for the availability group.</span></span> <span data-ttu-id="95dfd-112">特定のサブネットをリスナーに追加するには、そのサブネット アドレスのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="95dfd-112">To add a given subnet to the listener, select one of its subnet addresses.</span></span>  
  
 <span data-ttu-id="95dfd-113">**[IP アドレスの追加]** ダイアログ ボックスで作業を終え、 **[OK]** をクリックして、選択したサブネット アドレスをリスナーに追加すると、 **[サブネット]** ボックスの一覧でそのサブネット アドレスが除外されます。</span><span class="sxs-lookup"><span data-stu-id="95dfd-113">After you complete the **Add IP Address** dialog box and click **OK** to add a selected subnet address to the listener, the **Subnet** drop list filters out that subnet address.</span></span> <span data-ttu-id="95dfd-114">選択されなかったすべてのサブネット アドレスは、ドロップダウン リストに残ります。</span><span class="sxs-lookup"><span data-stu-id="95dfd-114">All unselected subnet addresses remain on the drop list.</span></span> <span data-ttu-id="95dfd-115">サブネットごとにサブネット アドレスを 1 つだけリスナーに追加したことを確認してください。それ以外の場合、リスナーの作成に失敗します。</span><span class="sxs-lookup"><span data-stu-id="95dfd-115">Be sure that you add one and only one subnet address per subnet to the listener, or listener creation will fail.</span></span>  
  
 <span data-ttu-id="95dfd-116">**アドレス**</span><span class="sxs-lookup"><span data-stu-id="95dfd-116">**Addresses**</span></span>  
 <span data-ttu-id="95dfd-117">このフィールドを使用して、選択したサブネット アドレスの静的 IP アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="95dfd-117">Use this field to enter a static IP address for the selected subnet address.</span></span> <span data-ttu-id="95dfd-118">この IP アドレスは、ネットワーク管理者に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="95dfd-118">Contact your network administrator for this IP address.</span></span> <span data-ttu-id="95dfd-119">選択したサブネット アドレスの有効なアドレスを入力したことを確認します。アドレスが無効な場合、リスナーの作成に失敗します。</span><span class="sxs-lookup"><span data-stu-id="95dfd-119">Ensure that you enter a valid address for the selected subnet address, or listener creation will fail.</span></span>  
  
 <span data-ttu-id="95dfd-120">**IPv4 アドレス**</span><span class="sxs-lookup"><span data-stu-id="95dfd-120">**IPv4 Address**</span></span>  
 <span data-ttu-id="95dfd-121">サブネットの IPv4 サブネット アドレスを選択した場合は、有効な IPv4 静的アドレスをここに入力します。</span><span class="sxs-lookup"><span data-stu-id="95dfd-121">If you selected the IPv4 subnet address of a subnet, enter a valid IPv4 static address here.</span></span>  
  
 <span data-ttu-id="95dfd-122">**サブネットマスク**</span><span class="sxs-lookup"><span data-stu-id="95dfd-122">**Subnet Mask**</span></span>  
 <span data-ttu-id="95dfd-123">IPv4 アドレスの場合は、この読み取り専用フィールドに、選択したサブネットのサブネット マスクが表示されます。</span><span class="sxs-lookup"><span data-stu-id="95dfd-123">For an IPv4 address, this read-only field displays the subnet mask of the selected subnet.</span></span>  
  
 <span data-ttu-id="95dfd-124">**IPv6 アドレス**</span><span class="sxs-lookup"><span data-stu-id="95dfd-124">**IPv6 Address**</span></span>  
 <span data-ttu-id="95dfd-125">サブネットの IPv6 サブネット アドレスを選択した場合は、有効な IPv6 静的アドレスをここに入力します。</span><span class="sxs-lookup"><span data-stu-id="95dfd-125">If you selected the IPv6 subnet address of a subnet, enter a valid IPv6 static address here.</span></span>  
  
 <span data-ttu-id="95dfd-126">**[OK]**</span><span class="sxs-lookup"><span data-stu-id="95dfd-126">**OK**</span></span>  
 <span data-ttu-id="95dfd-127">クリックすると、選択したアドレスのサブネットと指定した静的 IP アドレスが追加されます。</span><span class="sxs-lookup"><span data-stu-id="95dfd-127">Click to create add the subnet whose address you selected, along with the static IP address that you specified.</span></span> <span data-ttu-id="95dfd-128">これらの値が含まれる行は、 **[新しい可用性グループ リスナー]** または **[レプリカの指定]** ダイアログ ボックスのサブネット グリッドに追加されます。</span><span class="sxs-lookup"><span data-stu-id="95dfd-128">A row containing these values will be added to the subnet grid of the **New Availability Group Listener** or **Specify Replicas** dialog box.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="95dfd-129">**[IP アドレスの追加]** ダイアログでは、IP アドレスは検証されません。</span><span class="sxs-lookup"><span data-stu-id="95dfd-129">The **Add IP Address** dialog does not verify the IP address.</span></span> <span data-ttu-id="95dfd-130">また、既に可用性グループ リスナーに追加されているサブネットのサブネット アドレスを追加できないようになっていません。</span><span class="sxs-lookup"><span data-stu-id="95dfd-130">Also the dialog does not prevent you from adding the second subnet address for a subnet that you have already added to the availability group listener.</span></span>  
  
 <span data-ttu-id="95dfd-131">**キャンセル**</span><span class="sxs-lookup"><span data-stu-id="95dfd-131">**Cancel**</span></span>  
 <span data-ttu-id="95dfd-132">クリックすると、選択が取り消され、 **[新しい可用性グループ リスナー]** ダイアログ ボックスまたは **[リスナー]** タブに戻ります。サブネットの静的 IP アドレスは追加されません。</span><span class="sxs-lookup"><span data-stu-id="95dfd-132">Click to cancel your selections, and return to the **New Availability Group Listener** dialog box or **Listener** tab without adding a static IP address for any subnet.</span></span>  
  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="95dfd-133">関連タスク</span><span class="sxs-lookup"><span data-stu-id="95dfd-133">Related Tasks</span></span>  
  
-   [<span data-ttu-id="95dfd-134">可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="95dfd-134">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   <span data-ttu-id="95dfd-135">[[新しい可用性グループ] ダイアログ ボックスの使用 &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="95dfd-135">[Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)</span></span>  
  
-   [<span data-ttu-id="95dfd-136">可用性グループへのレプリカ追加ウィザードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="95dfd-136">Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
  
## <a name="see-also"></a><span data-ttu-id="95dfd-137">参照</span><span class="sxs-lookup"><span data-stu-id="95dfd-137">See Also</span></span>  
 <span data-ttu-id="95dfd-138">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="95dfd-138">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="95dfd-139">[可用性グループ リスナー、クライアント接続、およびアプリケーションのフェールオーバー &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span><span class="sxs-lookup"><span data-stu-id="95dfd-139">[Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span></span>  
 [<span data-ttu-id="95dfd-140">AlwaysOn クライアント接続 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="95dfd-140">AlwaysOn Client Connectivity (SQL Server)</span></span>](always-on-client-connectivity-sql-server.md)  
  
  
