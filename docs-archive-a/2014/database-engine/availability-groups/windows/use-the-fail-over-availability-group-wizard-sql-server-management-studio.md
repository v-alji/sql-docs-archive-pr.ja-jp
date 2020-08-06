---
title: 可用性グループのフェールオーバー ウィザードの使用 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.failoverwizard.progress.f1
- sql12.swb.failoverwizard.f1
- sql12.swb.failoverwizard.selectnewprimary.f1
- sql12.swb.failoverwizard.confirmdataloss.f1
- sql12.swb.failoverwizard.connecttoreplicas.f1
helpviewer_keywords:
- failover [SQL Server], failover
- Availability Groups [SQL Server], wizards
- Availability Groups [SQL Server], configuring
ms.assetid: 4a602584-63e4-4322-aafc-5d715b82b834
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6bd059712aae9c23ebbda107370ad112d7917cd5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634640"
---
# <a name="use-the-fail-over-availability-group-wizard-sql-server-management-studio"></a><span data-ttu-id="36ce7-102">可用性グループのフェールオーバー ウィザードの使用 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="36ce7-102">Use the Fail Over Availability Group Wizard (SQL Server Management Studio)</span></span>
  <span data-ttu-id="36ce7-103">このトピックでは、[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] の [!INCLUDE[tsql](../../../includes/tsql-md.md)]、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]、または PowerShell を使用して、AlwaysOn 可用性グループ上で計画的な手動フェールオーバーまたは強制手動フェールオーバー (強制フェールオーバー) を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="36ce7-103">This topic describes how to perform a planned manual failover or forced manual failover (forced failover) on an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="36ce7-104">可用性グループは、可用性レプリカのレベルでフェールオーバーします。</span><span class="sxs-lookup"><span data-stu-id="36ce7-104">An availability group fails over at the level of an availability replica.</span></span> <span data-ttu-id="36ce7-105">SYNCHRONIZED 状態のセカンダリ レプリカにフェールオーバーする場合は、ウィザードで計画的な手動フェールオーバー (データ損失なし) を実行します。</span><span class="sxs-lookup"><span data-stu-id="36ce7-105">If you fail over to a secondary replica in the SYNCHRONIZED state, the wizard performs a planned manual failover (without data loss).</span></span> <span data-ttu-id="36ce7-106">UNSYNCHRONIZED 状態または NOT SYNCHRONIZING 状態のセカンダリ レプリカにフェールオーバーする場合は、ウィザードで "*強制フェールオーバー*" とも呼ばれる強制手動フェールオーバー (データ損失の可能性あり) を実行します。</span><span class="sxs-lookup"><span data-stu-id="36ce7-106">If you fail over to a secondary replica in the UNSYNCHRONIZED or NOT SYNCHRONIZING state, the wizard performs a forced manual failover-also known as a *forced failover* (with possible data loss).</span></span> <span data-ttu-id="36ce7-107">どちらの形式の手動フェールオーバーでも、接続先のセカンダリ レプリカはプライマリ ロールに移行します。</span><span class="sxs-lookup"><span data-stu-id="36ce7-107">Both forms of manual failover transition the secondary replica to which you are connected to the primary role.</span></span> <span data-ttu-id="36ce7-108">計画的な手動フェールオーバーでは、同時に、元のプライマリ レプリカはセカンダリ ロールに移行します。</span><span class="sxs-lookup"><span data-stu-id="36ce7-108">A planned manual failover currently transitions the former primary replica to the secondary role.</span></span> <span data-ttu-id="36ce7-109">強制フェールオーバー後は、元のプライマリ レプリカはオンラインになると、セカンダリ ロールに移行します。</span><span class="sxs-lookup"><span data-stu-id="36ce7-109">After a forced failover, when the former primary replica comes online, it transitions to the secondary role.</span></span>  
  


  
-   <span data-ttu-id="36ce7-110">**[!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)]トピック**</span><span class="sxs-lookup"><span data-stu-id="36ce7-110">**[!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)] pages:**</span></span>  
  
     <span data-ttu-id="36ce7-111">[[新しいプライマリ レプリカの選択] ページ](#SelectNewPrimaryReplica) (このトピックで後述)</span><span class="sxs-lookup"><span data-stu-id="36ce7-111">[Select New Primary Replica page](#SelectNewPrimaryReplica) (later in this topic)</span></span>  
  
     <span data-ttu-id="36ce7-112">[[レプリカへの接続] ページ](#ConnectToReplica) (このトピックで後述)</span><span class="sxs-lookup"><span data-stu-id="36ce7-112">[Connect to Replica page](#ConnectToReplica) (later in this topic)</span></span>  
  
     <span data-ttu-id="36ce7-113">[[データ損失の可能性の確認] ページ](#ConfirmPotentialDataLoss) (このトピックで後述)</span><span class="sxs-lookup"><span data-stu-id="36ce7-113">[Confirm Potential Data Loss page](#ConfirmPotentialDataLoss) (later in this topic)</span></span>  
  
     <span data-ttu-id="36ce7-114">[[概要] ページ &#40;AlwaysOn 可用性グループウィザード&#41;](summary-page-always-on-availability-group-wizards.md)</span><span class="sxs-lookup"><span data-stu-id="36ce7-114">[Summary Page &#40;AlwaysOn Availability Group Wizards&#41;](summary-page-always-on-availability-group-wizards.md)</span></span>  
  
     <span data-ttu-id="36ce7-115">[AlwaysOn 可用性グループウィザードの [進行状況] ページ &#40;&#41;](progress-page-always-on-availability-group-wizards.md)</span><span class="sxs-lookup"><span data-stu-id="36ce7-115">[Progress Page &#40;AlwaysOn Availability Group Wizards&#41;](progress-page-always-on-availability-group-wizards.md)</span></span>  
  
     <span data-ttu-id="36ce7-116">[[結果] ページ &#40;AlwaysOn 可用性グループウィザード&#41;](results-page-always-on-availability-group-wizards.md)</span><span class="sxs-lookup"><span data-stu-id="36ce7-116">[Results Page &#40;AlwaysOn Availability Group Wizards&#41;](results-page-always-on-availability-group-wizards.md)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="36ce7-117">はじめに</span><span class="sxs-lookup"><span data-stu-id="36ce7-117">Before You Begin</span></span>  
 <span data-ttu-id="36ce7-118">計画的な手動フェールオーバーを初めて実行する前に、「 [可用性グループの計画的な手動フェールオーバーの実行 &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)、または PowerShell を使用して、AlwaysOn 可用性グループ上で計画的な手動フェールオーバーまたは強制手動フェールオーバー (強制フェールオーバー) を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="36ce7-118">Before your first planned manual failover, see the "Before You Begin" section in [Perform a Planned Manual Failover of an Availability Group &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md).</span></span>  
  
 <span data-ttu-id="36ce7-119">強制手動フェールオーバーを初めて実行する前に、「[可用性グループの強制手動フェールオーバーの実行 &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)」の「補足情報: 強制フェールオーバー後の必須タスク」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="36ce7-119">Before your first forced failover, see the "Before You Begin" and "Follow Up: Essential Tasks After a Forced Failover" sections in [Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md).</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="36ce7-120">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="36ce7-120">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="36ce7-121">フェールオーバー コマンドは、ターゲットのセカンダリ レプリカがコマンドを受け入れた直後に戻ります。</span><span class="sxs-lookup"><span data-stu-id="36ce7-121">A failover command returns as soon as the target secondary replica has accepted the command.</span></span> <span data-ttu-id="36ce7-122">ただし、データベースの復旧は、可用性グループがフェールオーバーを完了した後に非同期で行われます。</span><span class="sxs-lookup"><span data-stu-id="36ce7-122">However, database recovery occurs asynchronously after the availability group has finished failing over.</span></span>  
  
-   <span data-ttu-id="36ce7-123">フェールオーバー時に、可用性グループ内のデータベース間の一貫性は維持されません。</span><span class="sxs-lookup"><span data-stu-id="36ce7-123">Cross-database consistency across databases within the availability group is not maintained on failover.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="36ce7-124">複数のデータベースにまたがるトランザクションおよび分散トランザクションは、[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="36ce7-124">Cross-database transactions and distributed transactions are not supported by [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="36ce7-125">詳細については、「[データベース ミラーリングまたは AlwaysOn 可用性グループではサポートされない複数データベースにまたがるトランザクション &#40;SQL Server&#41;](transactions-always-on-availability-and-database-mirroring.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36ce7-125">For more information, see [Cross-Database Transactions Not Supported For Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;](transactions-always-on-availability-and-database-mirroring.md).</span></span>  
  
###  <a name="prerequisites-for-using-the-failover-availability-group-wizard"></a><a name="Prerequisites"></a> <span data-ttu-id="36ce7-126">可用性グループのフェールオーバー ウィザードを使用するための前提条件</span><span class="sxs-lookup"><span data-stu-id="36ce7-126">Prerequisites for Using the Failover Availability Group Wizard</span></span>  
  
-   <span data-ttu-id="36ce7-127">現在使用可能な可用性レプリカをホストするサーバー インスタンスに接続している必要があります。</span><span class="sxs-lookup"><span data-stu-id="36ce7-127">You must be connected to the server instance that hosts an availability replica that is currently available.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="36ce7-128">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="36ce7-128">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="36ce7-129">Permissions</span><span class="sxs-lookup"><span data-stu-id="36ce7-129">Permissions</span></span>  
 <span data-ttu-id="36ce7-130">可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="36ce7-130">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="36ce7-131">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="36ce7-131">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="36ce7-132">**可用性グループのフェールオーバー ウィザードを使用するには**</span><span class="sxs-lookup"><span data-stu-id="36ce7-132">**To Use the Failover Availability Group Wizard**</span></span>  
  
1.  <span data-ttu-id="36ce7-133">オブジェクト エクスプローラーで、フェールオーバーを行う可用性グループのセカンダリ レプリカをホストするサーバー インスタンスに接続し、サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="36ce7-133">In Object Explorer, connect to the server instance that hosts a secondary replica of the availability group that needs to be failed over, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="36ce7-134">**[AlwaysOn 高可用性]** ノードと **[可用性グループ]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="36ce7-134">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="36ce7-135">可用性グループのフェールオーバー ウィザードを起動するには、フェールオーバーを行う可用性グループを右クリックして **[フェールオーバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36ce7-135">To launch the Failover Availability Group Wizard, right-click the availability group that you are going to fail over, and select **Failover**.</span></span>  
  
4.  <span data-ttu-id="36ce7-136">**[説明]** ページに表示される情報は、セカンダリ レプリカが計画的フェールオーバーの対象であるかどうかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="36ce7-136">The information presented by the **Introduction** page depends on whether any secondary replica is eligible for a planned failover.</span></span> <span data-ttu-id="36ce7-137">このページに **"この可用性グループの計画的フェールオーバーを実行します"** と表示されている場合は、データを失わずに可用性グループをフェールオーバーできます。</span><span class="sxs-lookup"><span data-stu-id="36ce7-137">If this page says, "**Perform a planned failover for this availability group**", you can failover the availability group without data loss.</span></span>  
  
5.  <span data-ttu-id="36ce7-138">**[新しいプライマリ レプリカの選択]** ページで、新しいプライマリ レプリカになるセカンダリ レプリカ ( *フェールオーバー ターゲット*) を選択する前に、現在のプライマリ レプリカと WSFC クォーラムの状態を確認できます。</span><span class="sxs-lookup"><span data-stu-id="36ce7-138">On the **Select New Primary Replica** page, you can view the status of the current primary replica and of the WSFC quorum, before you choose the secondary replica that will become the new primary replica (the *failover target*).</span></span> <span data-ttu-id="36ce7-139">計画的な手動フェールオーバーの場合は、 **[フェールオーバーの準備]** の値が **[データ損失なし]** になっているセカンダリ レプリカを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="36ce7-139">For a planned manual failover, be sure to select a secondary replica whose **Failover Readiness** value is "**No data loss**".</span></span> <span data-ttu-id="36ce7-140">強制フェールオーバーの場合、可能なすべてのフェールオーバーターゲットについて、この値は "**データ損失、警告 ( ***#*** )**" になり *#* ます。は、特定のセカンダリレプリカに存在する警告の数を示します。</span><span class="sxs-lookup"><span data-stu-id="36ce7-140">For a forced failover, for all the possible failover targets, this value will be "**Data loss, Warnings(***#***)**", where *#* indicates the number of warnings that exist for a given secondary replica.</span></span> <span data-ttu-id="36ce7-141">特定のフェールオーバー ターゲットの警告を表示するには、その [フェールオーバーの準備] の値をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36ce7-141">To view the warnings for a given failover target, click its "Failover Readiness" value.</span></span>  
  
     <span data-ttu-id="36ce7-142">詳細については、このトピックの「 [[新しいプライマリ レプリカの選択] ページ](#SelectNewPrimaryReplica)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36ce7-142">For more information, see [Select New Primary Replica page](#SelectNewPrimaryReplica), later in this topic.</span></span>  
  
6.  <span data-ttu-id="36ce7-143">**[レプリカへの接続]** ページで、フェールオーバー ターゲットに接続します。</span><span class="sxs-lookup"><span data-stu-id="36ce7-143">On the **Connect to Replica** page,  connect to the failover target.</span></span> <span data-ttu-id="36ce7-144">詳細については、このトピックの「 [[レプリカへの接続] ページ](#ConnectToReplica)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36ce7-144">For more information, see [Connect to Replica page](#ConnectToReplica), later in this topic.</span></span>  
  
7.  <span data-ttu-id="36ce7-145">強制フェールオーバーを実行する場合は、 **[データ損失の可能性の確認]** ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="36ce7-145">If you are performing a forced failover, the wizard displays the **Confirm Potential Data Loss** page.</span></span> <span data-ttu-id="36ce7-146">フェールオーバーを続行するには、 **[ここをクリックしてデータ損失の可能性があるフェールオーバーを実行する]** を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="36ce7-146">To proceed with the failover, you must select **Click here to confirm failover with potential data loss**.</span></span> <span data-ttu-id="36ce7-147">詳細については、このトピックの「[[データ損失の可能性の確認] ページ](#ConfirmPotentialDataLoss)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36ce7-147">For more information, see .[Confirm Potential Data Loss page](#ConfirmPotentialDataLoss), later in this topic.</span></span>  
  
8.  <span data-ttu-id="36ce7-148">**[概要]** ページで、選択したセカンダリ レプリカへのフェールオーバーの影響を確認します。</span><span class="sxs-lookup"><span data-stu-id="36ce7-148">On the **Summary** page, review the implications of failing over to the selected secondary replica.</span></span>  
  
     <span data-ttu-id="36ce7-149">選択内容に問題がなければ、 **[スクリプト]** をクリックして、ウィザードが実行する手順のスクリプトを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="36ce7-149">If you are satisfied with your selections, optionally click **Script** to create a script of the steps the wizard will execute.</span></span> <span data-ttu-id="36ce7-150">その後、可用性グループを選択したセカンダリ レプリカにフェールオーバーするには、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36ce7-150">Then, to failover the availability group to the selected secondary replica, click **Finish**.</span></span>  
  
9. <span data-ttu-id="36ce7-151">**[進行状況]** ページに、可用性グループのフェールオーバーの進行状況が表示されます。</span><span class="sxs-lookup"><span data-stu-id="36ce7-151">The **Progress** page displays the progress of failing over the availability group.</span></span>  
  
10. <span data-ttu-id="36ce7-152">フェールオーバー操作が完了すると、 **[結果]** ページに結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="36ce7-152">When the failover operation finishes, the **Results** page displays the result.</span></span> <span data-ttu-id="36ce7-153">ウィザードでの作業が完了したら、 **[閉じる]** をクリックして終了します。</span><span class="sxs-lookup"><span data-stu-id="36ce7-153">When the wizard completes, click **Close** to exit.</span></span>  
  
     <span data-ttu-id="36ce7-154">詳細については、「[[結果] ページ &#40;AlwaysOn 可用性グループ ウィザード&#41;](results-page-always-on-availability-group-wizards.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36ce7-154">For more information, see [Results Page &#40;AlwaysOn Availability Group Wizards&#41;](results-page-always-on-availability-group-wizards.md).</span></span>  
  
11. <span data-ttu-id="36ce7-155">強制フェールオーバーの後は、「[可用性グループの強制手動フェールオーバーの実行 &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)」の「補足情報: 強制フェールオーバー後」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="36ce7-155">After a forced failover, see the "Follow Up: After a Forced Failover" section in the [Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md).</span></span>  
  
## <a name="help-for-pages-that-are-exclusive-to-this-wizard"></a><span data-ttu-id="36ce7-156">このウィザードに固有のページのヘルプ</span><span class="sxs-lookup"><span data-stu-id="36ce7-156">Help for Pages that are Exclusive to This Wizard</span></span>  
 <span data-ttu-id="36ce7-157">ここでは、 [!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)]に固有のページについて説明します。</span><span class="sxs-lookup"><span data-stu-id="36ce7-157">This section describes the pages that are unique to the [!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)].</span></span>  
  
 
  
 <span data-ttu-id="36ce7-158">このウィザードの他のページのヘルプは、他の AlwaysOn 可用性グループ ウィザードと共通で、個別の F1 ヘルプ トピックに記載されています。</span><span class="sxs-lookup"><span data-stu-id="36ce7-158">The other pages of this wizard share help with one or more of the other AlwaysOn Availability Groups wizards and are documented in separate F1 help topics.</span></span>  
  
###  <a name="select-new-primary-replica-page"></a><a name="SelectNewPrimaryReplica"></a> <span data-ttu-id="36ce7-159">Select New Primary Replica Page</span><span class="sxs-lookup"><span data-stu-id="36ce7-159">Select New Primary Replica Page</span></span>  
 <span data-ttu-id="36ce7-160">ここでは、 **[新しいプライマリ レプリカの選択]** ページのオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="36ce7-160">This section describes the options of the **Select New Primary Replica** page.</span></span> <span data-ttu-id="36ce7-161">このページを使用すると、可用性グループのフェールオーバー先のセカンダリ レプリカ (フェールオーバー ターゲット) を選択できます。</span><span class="sxs-lookup"><span data-stu-id="36ce7-161">Use this page to select the secondary replica (failover target) to which the availability group will fail over.</span></span> <span data-ttu-id="36ce7-162">このレプリカは新しいプライマリ レプリカになります。</span><span class="sxs-lookup"><span data-stu-id="36ce7-162">This replica will become the new primary replica.</span></span>  
  
#### <a name="page-options"></a><span data-ttu-id="36ce7-163">ページのオプション</span><span class="sxs-lookup"><span data-stu-id="36ce7-163">Page Options</span></span>  
 <span data-ttu-id="36ce7-164">**現在のプライマリ レプリカ**</span><span class="sxs-lookup"><span data-stu-id="36ce7-164">**Current Primary Replica**</span></span>  
 <span data-ttu-id="36ce7-165">オンラインの場合、現在のプライマリ レプリカの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="36ce7-165">Displays the name of the current primary replica, if it is online.</span></span>  
  
 <span data-ttu-id="36ce7-166">**[プライマリ レプリカの状態]**</span><span class="sxs-lookup"><span data-stu-id="36ce7-166">**Primary Replica Status**</span></span>  
 <span data-ttu-id="36ce7-167">オンラインの場合、現在のプライマリ レプリカの状態を表示します。</span><span class="sxs-lookup"><span data-stu-id="36ce7-167">Displays the status of the current primary replica, if it is online.</span></span>  
  
 <span data-ttu-id="36ce7-168">**[クォーラムの状態]**</span><span class="sxs-lookup"><span data-stu-id="36ce7-168">**Quorum Status**</span></span>  
 <span data-ttu-id="36ce7-169">可用性レプリカの WSFC クォーラムの状態を表示します。次のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="36ce7-169">Displays the WSFC quorum status for the availability replica, one of:</span></span>  
  
|<span data-ttu-id="36ce7-170">値</span><span class="sxs-lookup"><span data-stu-id="36ce7-170">Value</span></span>|<span data-ttu-id="36ce7-171">説明</span><span class="sxs-lookup"><span data-stu-id="36ce7-171">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="36ce7-172">**[標準のクォーラム]**</span><span class="sxs-lookup"><span data-stu-id="36ce7-172">**Normal quorum**</span></span>|<span data-ttu-id="36ce7-173">クラスターは、標準のクォーラムを使用して起動しました。</span><span class="sxs-lookup"><span data-stu-id="36ce7-173">The cluster has started with normal quorum.</span></span>|  
|<span data-ttu-id="36ce7-174">**強制されたクォーラム**</span><span class="sxs-lookup"><span data-stu-id="36ce7-174">**Forced quorum**</span></span>|<span data-ttu-id="36ce7-175">クラスターは、強制されたクォーラムを使用して起動しました。</span><span class="sxs-lookup"><span data-stu-id="36ce7-175">The cluster has started with forced quorum.</span></span>|  
|<span data-ttu-id="36ce7-176">**[不明なクォーラム]**</span><span class="sxs-lookup"><span data-stu-id="36ce7-176">**Unknown quorum**</span></span>|<span data-ttu-id="36ce7-177">クラスター クォーラムの状態が不明です。</span><span class="sxs-lookup"><span data-stu-id="36ce7-177">The cluster quorum status is unavailable.</span></span>|  
|<span data-ttu-id="36ce7-178">**適用不可**</span><span class="sxs-lookup"><span data-stu-id="36ce7-178">**Not applicable**</span></span>|<span data-ttu-id="36ce7-179">可用性レプリカをホストするノードにクォーラムがありません。</span><span class="sxs-lookup"><span data-stu-id="36ce7-179">The node that hosts the availability replica has no quorum.</span></span>|  
  
 <span data-ttu-id="36ce7-180">詳細については、「[WSFC クォーラム モードと投票の構成 &#40;SQL Server&#41;](../../../sql-server/failover-clusters/windows/wsfc-quorum-modes-and-voting-configuration-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36ce7-180">For more information, see [WSFC Quorum Modes and Voting Configuration &#40;SQL Server&#41;](../../../sql-server/failover-clusters/windows/wsfc-quorum-modes-and-voting-configuration-sql-server.md).</span></span>  
  
 <span data-ttu-id="36ce7-181">**[新しいプライマリ レプリカの選択]**</span><span class="sxs-lookup"><span data-stu-id="36ce7-181">**Choose a new primary replica**</span></span>  
 <span data-ttu-id="36ce7-182">このグリッドを使用して、新しいプライマリ レプリカになるセカンダリ レプリカを選択します。</span><span class="sxs-lookup"><span data-stu-id="36ce7-182">Use this grid to select a secondary replica to become the new primary replica.</span></span> <span data-ttu-id="36ce7-183">このグリッドの列は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="36ce7-183">The columns in this grid are as follows:</span></span>  
  
 <span data-ttu-id="36ce7-184">**サーバー インスタンス**</span><span class="sxs-lookup"><span data-stu-id="36ce7-184">**Server Instance**</span></span>  
 <span data-ttu-id="36ce7-185">セカンダリ レプリカをホストするサーバー インスタンスの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="36ce7-185">Displays the name of a server instance that hosts a secondary replica.</span></span>  
  
 <span data-ttu-id="36ce7-186">**可用性モード**</span><span class="sxs-lookup"><span data-stu-id="36ce7-186">**Availability Mode**</span></span>  
 <span data-ttu-id="36ce7-187">サーバー インスタンスの可用性モードを表示します。次のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="36ce7-187">Displays the availability mode of the server instance, one of:</span></span>  
  
|<span data-ttu-id="36ce7-188">値</span><span class="sxs-lookup"><span data-stu-id="36ce7-188">Value</span></span>|<span data-ttu-id="36ce7-189">説明</span><span class="sxs-lookup"><span data-stu-id="36ce7-189">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="36ce7-190">**[同期コミット]**</span><span class="sxs-lookup"><span data-stu-id="36ce7-190">**Synchronous commit**</span></span>|<span data-ttu-id="36ce7-191">同期コミット モードの場合、同期コミット プライマリ レプリカは、同期コミット セカンダリ レプリカによるログ書き込みが確認されるまで待機した後で、トランザクションをコミットします。</span><span class="sxs-lookup"><span data-stu-id="36ce7-191">Under synchronous-commit mode, before committing transactions, a synchronous-commit primary replica waits for a synchronous-commit secondary replica to acknowledge that it has finished hardening the log.</span></span> <span data-ttu-id="36ce7-192">同期コミット モードでは、特定のセカンダリ データベースがプライマリ データベースに 1 回同期されれば、コミットされたトランザクションが完全に保護されることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="36ce7-192">Synchronous-commit mode ensures that once a given secondary database is synchronized with the primary database, committed transactions are fully protected.</span></span>|  
|<span data-ttu-id="36ce7-193">**[非同期コミット]**</span><span class="sxs-lookup"><span data-stu-id="36ce7-193">**Asynchronous commit**</span></span>|<span data-ttu-id="36ce7-194">非同期コミット モードでは、非同期コミット セカンダリ レプリカによりログが書き込まれことが確認されるまで待機せずに、プライマリ レプリカがトランザクションをコミットします。</span><span class="sxs-lookup"><span data-stu-id="36ce7-194">Under asynchronous-commit mode, the primary replica commits transactions without waiting for acknowledgement that an asynchronous-commit secondary replica has hardened the log.</span></span> <span data-ttu-id="36ce7-195">非同期コミット モードでは、セカンダリ データベースでのトランザクションの遅延が最小になりますが、セカンダリ データベースがプライマリ データベースよりも遅延する場合があるため、一部のデータが失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="36ce7-195">Asynchronous-commit mode minimizes transaction latency on the secondary databases but allows them to lag behind the primary databases, making some data loss possible.</span></span>|  
  
 <span data-ttu-id="36ce7-196">詳細については、「[可用性モード (AlwaysOn 可用性グループ)](availability-modes-always-on-availability-groups.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36ce7-196">For more information, see [Availability Modes (AlwaysOn Availability Groups)](availability-modes-always-on-availability-groups.md).</span></span>  
  
 <span data-ttu-id="36ce7-197">**フェールオーバー モード**</span><span class="sxs-lookup"><span data-stu-id="36ce7-197">**Failover Mode**</span></span>  
 <span data-ttu-id="36ce7-198">サーバー インスタンスのフェールオーバー モードを表示します。次のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="36ce7-198">Displays the failover mode of the server instance, one of:</span></span>  
  
|<span data-ttu-id="36ce7-199">値</span><span class="sxs-lookup"><span data-stu-id="36ce7-199">Value</span></span>|<span data-ttu-id="36ce7-200">説明</span><span class="sxs-lookup"><span data-stu-id="36ce7-200">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="36ce7-201">**自動**</span><span class="sxs-lookup"><span data-stu-id="36ce7-201">**Automatic**</span></span>|<span data-ttu-id="36ce7-202">自動フェールオーバー用に構成されているセカンダリ レプリカでは、そのセカンダリ レプリカがプライマリ レプリカと同期されている場合は計画的な手動フェールオーバーもサポートされます。</span><span class="sxs-lookup"><span data-stu-id="36ce7-202">A secondary replica that is configured for automatic failover also supports planned manual failover whenever the secondary replica is synchronized with the primary replica.</span></span>|  
|<span data-ttu-id="36ce7-203">**手動**</span><span class="sxs-lookup"><span data-stu-id="36ce7-203">**Manual**</span></span>|<span data-ttu-id="36ce7-204">手動フェールオーバーには、計画的 (データ損失なし) および強制 (データ損失の可能性あり) の 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="36ce7-204">Two types of manual failover exist: planned (without data loss) and forced (with possible data loss).</span></span> <span data-ttu-id="36ce7-205">特定のセカンダリ レプリカでサポートされる手動フェールオーバーはどちらか 1 つだけで、このサポートは可用性モードによって異なり、同期コミット モードのサポートはセカンダリ レプリカの同期状態によって決まります。</span><span class="sxs-lookup"><span data-stu-id="36ce7-205">For a given secondary replica, only one of these is supported, depending on the availability mode and, for synchronous-commit mode, the synchronization state of the secondary replica.</span></span> <span data-ttu-id="36ce7-206">特定のセカンダリ レプリカで現在サポートされている手動フェールオーバーの形式を調べるには、このグリッドの **[フェールオーバーの準備]** 列を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36ce7-206">To determine which form of manual failover is currently supported by a given secondary replica, see the **Failover Readiness** column of this grid.</span></span>|  
  
 <span data-ttu-id="36ce7-207">詳細については、「[フェールオーバーとフェールオーバー モード &#40;AlwaysOn 可用性グループ&#41;](failover-and-failover-modes-always-on-availability-groups.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36ce7-207">For more information, see [Failover and Failover Modes &#40;AlwaysOn Availability Groups&#41;](failover-and-failover-modes-always-on-availability-groups.md).</span></span>  
  
 <span data-ttu-id="36ce7-208">**[フェールオーバーの準備]**</span><span class="sxs-lookup"><span data-stu-id="36ce7-208">**Failover Readiness**</span></span>  
 <span data-ttu-id="36ce7-209">セカンダリ レプリカのフェールオーバーの準備を表示します。次のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="36ce7-209">Displays failover readiness of the secondary replica, one of:</span></span>  
  
|<span data-ttu-id="36ce7-210">値</span><span class="sxs-lookup"><span data-stu-id="36ce7-210">Value</span></span>|<span data-ttu-id="36ce7-211">説明</span><span class="sxs-lookup"><span data-stu-id="36ce7-211">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="36ce7-212">**[データ損失なし]**</span><span class="sxs-lookup"><span data-stu-id="36ce7-212">**No data loss**</span></span>|<span data-ttu-id="36ce7-213">このセカンダリ レプリカでは現在、計画的フェールオーバーがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="36ce7-213">This secondary replica currently supports planned failover.</span></span> <span data-ttu-id="36ce7-214">この値は、同期コミット モードのセカンダリ レプリカが現在、プライマリ レプリカと同期されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="36ce7-214">This value occurs only when a synchronous-commit mode secondary replica is currently synchronized with the primary replica.</span></span>|  
|<span data-ttu-id="36ce7-215">**[データ損失、警告 (** *#* **)]**</span><span class="sxs-lookup"><span data-stu-id="36ce7-215">**Data loss, Warnings(** *#* **)**</span></span>|<span data-ttu-id="36ce7-216">このセカンダリ レプリカでは現在、強制フェールオーバー (データ損失の可能性あり) がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="36ce7-216">This secondary replica currently supports forced failover (with possible data loss).</span></span> <span data-ttu-id="36ce7-217">この値は、セカンダリ レプリカがプライマリ レプリカと同期されていない場合に表示されます。</span><span class="sxs-lookup"><span data-stu-id="36ce7-217">This value occurs whenever the secondary replica is not synchronized with the primary replica.</span></span> <span data-ttu-id="36ce7-218">データ損失の警告リンクをクリックすると、データ損失の可能性に関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="36ce7-218">Click the data-loss warnings link for information about the possible data loss.</span></span>|  
  
 <span data-ttu-id="36ce7-219">**[更新]**</span><span class="sxs-lookup"><span data-stu-id="36ce7-219">**Refresh**</span></span>  
 <span data-ttu-id="36ce7-220">グリッドを更新します。</span><span class="sxs-lookup"><span data-stu-id="36ce7-220">Click to update the grid.</span></span>  
  
 <span data-ttu-id="36ce7-221">**キャンセル**</span><span class="sxs-lookup"><span data-stu-id="36ce7-221">**Cancel**</span></span>  
 <span data-ttu-id="36ce7-222">ウィザードをキャンセルします。</span><span class="sxs-lookup"><span data-stu-id="36ce7-222">Click to cancel the wizard.</span></span> <span data-ttu-id="36ce7-223">**[新しいプライマリ レプリカの選択]** ページでウィザードをキャンセルすると、何もアクションを実行せずに終了します。</span><span class="sxs-lookup"><span data-stu-id="36ce7-223">On the **Select New Primary Replica** page, cancelling the wizard cause it to exit without performing any actions.</span></span>  
  
###  <a name="confirm-potential-data-loss-page"></a><a name="ConfirmPotentialDataLoss"></a> <span data-ttu-id="36ce7-224">Confirm Potential Data Loss Page</span><span class="sxs-lookup"><span data-stu-id="36ce7-224">Confirm Potential Data Loss Page</span></span>  
 <span data-ttu-id="36ce7-225">ここでは、強制フェールオーバーを実行する場合にのみ表示される **[データ損失の可能性の確認]** ページのオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="36ce7-225">This section describes the options of the **Confirm Potential Data Loss** page, which is displayed only if you are performing a forced failover.</span></span> <span data-ttu-id="36ce7-226">このトピックの対象は、 [!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)]だけです。</span><span class="sxs-lookup"><span data-stu-id="36ce7-226">This topic is used only by the [!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)].</span></span> <span data-ttu-id="36ce7-227">このページを使用すると、可用性グループを強制的にフェールオーバーするためにデータの損失を許容できるかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="36ce7-227">Use this page to indicate whether you are willing to risk possible data loss in order to force the availability group to fail over.</span></span>  
  
#### <a name="confirm-potential-data-loss-options"></a><span data-ttu-id="36ce7-228">[データ損失の可能性の確認] のオプション</span><span class="sxs-lookup"><span data-stu-id="36ce7-228">Confirm Potential Data Loss Options</span></span>  
 <span data-ttu-id="36ce7-229">選択したセカンダリ レプリカがプライマリ レプリカと同期されていない場合は、このセカンダリ レプリカにフェールオーバーすると 1 つ以上のデータベースのデータが失われる可能性があるという警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="36ce7-229">If the selected secondary replica is not synchronized with the primary replica, the wizard displays a warning that failing over to this secondary replica could cause data loss on one or more databases.</span></span>  
  
 <span data-ttu-id="36ce7-230">**[ここをクリックしてデータ損失の可能性があるフェールオーバーを実行する。]**</span><span class="sxs-lookup"><span data-stu-id="36ce7-230">**Click here to confirm failover with potential data loss.**</span></span>  
 <span data-ttu-id="36ce7-231">ユーザーがこの可用性グループのデータベースを使用できるようにするためにデータの損失を許容できる場合は、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="36ce7-231">If you are willing to risk data loss in order to make the databases in this availability group available to users, click this checkbox.</span></span> <span data-ttu-id="36ce7-232">データの損失を許容できない場合は、 **[戻る]** をクリックして **[新しいプライマリ レプリカの選択]** ページに戻るか、 **[キャンセル]** をクリックして可用性グループをフェールオーバーせずにウィザードを終了することができます。</span><span class="sxs-lookup"><span data-stu-id="36ce7-232">If you are not willing to risk data loss, you can either click **Previous** to return to the **Select New Primary Replica** page, or click **Cancel** to exit the wizard without failing over the availability group.</span></span>  
  
 <span data-ttu-id="36ce7-233">**キャンセル**</span><span class="sxs-lookup"><span data-stu-id="36ce7-233">**Cancel**</span></span>  
 <span data-ttu-id="36ce7-234">ウィザードをキャンセルします。</span><span class="sxs-lookup"><span data-stu-id="36ce7-234">Click to cancel the wizard.</span></span> <span data-ttu-id="36ce7-235">**[データ損失の可能性の確認]** ページでウィザードをキャンセルすると、何もアクションを実行せずに終了します。</span><span class="sxs-lookup"><span data-stu-id="36ce7-235">On the **Confirm Potential Data Loss** page, cancelling the wizard cause it to exit without performing any actions.</span></span>  
  
###  <a name="connect-to-replica-page"></a><a name="ConnectToReplica"></a> <span data-ttu-id="36ce7-236">Connect to Replica Page</span><span class="sxs-lookup"><span data-stu-id="36ce7-236">Connect to Replica Page</span></span>  
 <span data-ttu-id="36ce7-237">ここでは、 **の** [レプリカへの接続] [!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)]ページのオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="36ce7-237">This section describes the options of the **Connect to Replica** page of the [!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)].</span></span> <span data-ttu-id="36ce7-238">このページは、ターゲット セカンダリ レプリカに接続していない場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="36ce7-238">This page is displayed only if you are not connected to the target secondary replica.</span></span> <span data-ttu-id="36ce7-239">このページを使用すると、新しいプライマリ レプリカとして選択したセカンダリ レプリカに接続できます。</span><span class="sxs-lookup"><span data-stu-id="36ce7-239">Use this page to connect to the secondary replica that you have selected as the new primary replica.</span></span>  
  
#### <a name="page-options"></a><span data-ttu-id="36ce7-240">ページのオプション</span><span class="sxs-lookup"><span data-stu-id="36ce7-240">Page Options</span></span>  
 <span data-ttu-id="36ce7-241">**グリッド列:**</span><span class="sxs-lookup"><span data-stu-id="36ce7-241">**Grid columns:**</span></span>  
 <span data-ttu-id="36ce7-242">**サーバー インスタンス**</span><span class="sxs-lookup"><span data-stu-id="36ce7-242">**Server Instance**</span></span>  
 <span data-ttu-id="36ce7-243">可用性レプリカをホストするサーバー インスタンスの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="36ce7-243">Displays the name of the server instance that will host the availability replica.</span></span>  
  
 <span data-ttu-id="36ce7-244">**接続ユーザー**</span><span class="sxs-lookup"><span data-stu-id="36ce7-244">**Connected As**</span></span>  
 <span data-ttu-id="36ce7-245">接続が確立されると、サーバー インスタンスに接続されるアカウントを表示します。</span><span class="sxs-lookup"><span data-stu-id="36ce7-245">Displays the account that is connected to the server instance, once the connection has been established.</span></span> <span data-ttu-id="36ce7-246">この列で、特定のサーバー インスタンスについて **"未接続"** と表示される場合、 **[接続]** ボタンをクリックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="36ce7-246">If this column displays "**Not Connected**" for a given server instance, you will need to click the **Connect** button.</span></span>  
  
 <span data-ttu-id="36ce7-247">**接続する**</span><span class="sxs-lookup"><span data-stu-id="36ce7-247">**Connect**</span></span>  
 <span data-ttu-id="36ce7-248">このサーバー インスタンスが、接続する他のサーバー インスタンスとは異なるアカウントで実行されている場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="36ce7-248">Click if this server instance is running under a different account than other server instances to which you need to connect.</span></span>  
  
 <span data-ttu-id="36ce7-249">**キャンセル**</span><span class="sxs-lookup"><span data-stu-id="36ce7-249">**Cancel**</span></span>  
 <span data-ttu-id="36ce7-250">ウィザードをキャンセルします。</span><span class="sxs-lookup"><span data-stu-id="36ce7-250">Click to cancel the wizard.</span></span> <span data-ttu-id="36ce7-251">**[レプリカへの接続]** ページでウィザードをキャンセルすると、何もアクションを実行せずに終了します。</span><span class="sxs-lookup"><span data-stu-id="36ce7-251">On the **Connect to Replica** page, cancelling the wizard cause it to exit without performing any actions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36ce7-252">参照</span><span class="sxs-lookup"><span data-stu-id="36ce7-252">See Also</span></span>  
 <span data-ttu-id="36ce7-253">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="36ce7-253">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="36ce7-254">[可用性モード (AlwaysOn 可用性グループ)](availability-modes-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="36ce7-254">[Availability Modes (AlwaysOn Availability Groups)](availability-modes-always-on-availability-groups.md) </span></span>  
 <span data-ttu-id="36ce7-255">[フェールオーバーとフェールオーバーモード &#40;AlwaysOn 可用性グループ&#41;](failover-and-failover-modes-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="36ce7-255">[Failover and Failover Modes &#40;AlwaysOn Availability Groups&#41;](failover-and-failover-modes-always-on-availability-groups.md) </span></span>  
 <span data-ttu-id="36ce7-256">[可用性グループの計画的な手動フェールオーバーの実行 &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="36ce7-256">[Perform a Planned Manual Failover of an Availability Group &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md) </span></span>  
 <span data-ttu-id="36ce7-257">[可用性グループの強制手動フェールオーバーの実行 &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="36ce7-257">[Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md) </span></span>  
 [<span data-ttu-id="36ce7-258">WSFC の強制クォーラムによる災害復旧 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="36ce7-258">WSFC Disaster Recovery through Forced Quorum &#40;SQL Server&#41;</span></span>](../../../sql-server/failover-clusters/windows/wsfc-disaster-recovery-through-forced-quorum-sql-server.md)  
  
  
