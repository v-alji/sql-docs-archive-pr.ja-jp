---
title: データベース ミラーリング セッションの一時停止または再開 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- resuming database mirroring
- database mirroring [SQL Server], sessions
- database mirroring [SQL Server], pausing
- database mirroring [SQL Server], resuming
- pausing database mirroring
ms.assetid: 05ede3b4-6abe-4442-abb7-9f5aee1d6bc0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b8a9e30bed3ff268fcfdc6e352ad15ebedfe4e8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716794"
---
# <a name="pause-or-resume-a-database-mirroring-session-sql-server"></a><span data-ttu-id="f48a9-102">データベース ミラーリング セッションの一時停止または再開 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f48a9-102">Pause or Resume a Database Mirroring Session (SQL Server)</span></span>
  <span data-ttu-id="f48a9-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でデータベース ミラーリングを一時停止または再開する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f48a9-103">This topic describes how to pause or resume database mirroring in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="f48a9-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="f48a9-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f48a9-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="f48a9-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f48a9-106">Security</span><span class="sxs-lookup"><span data-stu-id="f48a9-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f48a9-107">**ReplaceThisText:**</span><span class="sxs-lookup"><span data-stu-id="f48a9-107">**To ReplaceThisText, using:**</span></span>  
  
     [<span data-ttu-id="f48a9-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f48a9-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f48a9-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f48a9-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="f48a9-110">**補足情報:**  [データベース ミラーリングの一時停止または再開した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="f48a9-110">**Follow Up:**  [After Pausing or Resuming Database Mirroring](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f48a9-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="f48a9-111">Before You Begin</span></span>  
 <span data-ttu-id="f48a9-112">データベース ミラーリング セッションをいつでも中断して、ボトルネックの発生中にパフォーマンスを向上させることができます。また、中断したセッションはいつでも再開できます。</span><span class="sxs-lookup"><span data-stu-id="f48a9-112">At any time, you can suspend a database mirroring session, which might improve performance during bottlenecks, and you can resume a suspended session at any time.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="f48a9-113">強制的なサービスの後に、最初のプリンシパル サーバーが再接続されると、ミラーリングが中断します。</span><span class="sxs-lookup"><span data-stu-id="f48a9-113">After a forced service, when the original principal server reconnects, mirroring is suspended.</span></span> <span data-ttu-id="f48a9-114">この状況でミラーリングを再開すると、元のプリンシパル サーバーのデータが失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f48a9-114">Resuming mirroring in this situation could possibly cause data loss on the original principal server.</span></span> <span data-ttu-id="f48a9-115">データ損失の可能性への対処の詳細については、「[データベース ミラーリング セッション中の役割の交代 &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f48a9-115">For information about managing the potential data loss, see [Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f48a9-116">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="f48a9-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f48a9-117">Permissions</span><span class="sxs-lookup"><span data-stu-id="f48a9-117">Permissions</span></span>  
 <span data-ttu-id="f48a9-118">データベースに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="f48a9-118">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f48a9-119">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="f48a9-119">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="f48a9-120">データベース ミラーリング セッションを一時停止または再開するには、 **[データベースのプロパティ]** の [ミラーリング] ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="f48a9-120">To pause or resume a database mirroring session use the **Database Properties Mirroring** page.</span></span>  
  
#### <a name="to-pause-or-resume-database-mirroring"></a><span data-ttu-id="f48a9-121">データベース ミラーリングを一時停止または再開するには</span><span class="sxs-lookup"><span data-stu-id="f48a9-121">To pause or resume database mirroring</span></span>  
  
1.  <span data-ttu-id="f48a9-122">データベース ミラーリング セッション中にプリンシパル サーバー インスタンスに接続します。次に、オブジェクト エクスプローラーで、サーバー名をクリックしてサーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="f48a9-122">During a database mirroring session, connect to the principal server instance, in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="f48a9-123">**[データベース]** を展開し、データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="f48a9-123">Expand **Databases**, and select the database.</span></span>  
  
3.  <span data-ttu-id="f48a9-124">データベースを右クリックして **[タスク]** を選択し、 **[ミラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f48a9-124">Right-click the database, select **Tasks**, and then click **Mirror**.</span></span> <span data-ttu-id="f48a9-125">**[データベースのプロパティ]** ダイアログ ボックスの **[ミラーリング]** ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="f48a9-125">This opens the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="f48a9-126">セッションを一時停止するには、 **[一時停止]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f48a9-126">To pause the session, click **Pause**.</span></span>  
  
     <span data-ttu-id="f48a9-127">確認を求めるメッセージが表示されます。 **[はい]** をクリックすると、セッションが一時停止し、ボタンが **[再開]** に変わります。</span><span class="sxs-lookup"><span data-stu-id="f48a9-127">A prompt asks for confirmation; if you click **Yes**, the session is paused, and the button changes to **Resume**.</span></span>  
  
     <span data-ttu-id="f48a9-128">セッションを一時停止した場合の影響の詳細については、「[データベース ミラーリングの一時停止と再開 &#40;SQL Server&#41;](database-mirroring-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f48a9-128">For more information about the impact of pausing a session, see [Pausing and Resuming Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
5.  <span data-ttu-id="f48a9-129">セッションを再開するには、 **[再開]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f48a9-129">To resume the session, click **Resume**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f48a9-130">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="f48a9-130">Using Transact-SQL</span></span>  
  
#### <a name="to-pause-database-mirroring"></a><span data-ttu-id="f48a9-131">データベース ミラーリングを一時停止するには</span><span class="sxs-lookup"><span data-stu-id="f48a9-131">To pause database mirroring</span></span>  
  
1.  <span data-ttu-id="f48a9-132">いずれかのパートナーの [!INCLUDE[ssDE](../../includes/ssde-md.md)] に接続します。</span><span class="sxs-lookup"><span data-stu-id="f48a9-132">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] for either partner.</span></span>  
  
2.  <span data-ttu-id="f48a9-133">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f48a9-133">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f48a9-134">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="f48a9-134">Issue the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
     <span data-ttu-id="f48a9-135">ALTER DATABASE *database_name* SET PARTNER SUSPEND</span><span class="sxs-lookup"><span data-stu-id="f48a9-135">ALTER DATABASE *database_name* SET PARTNER SUSPEND</span></span>  
  
     <span data-ttu-id="f48a9-136">*database_name* は、セッションを中断しようとしているミラー化データベースです。</span><span class="sxs-lookup"><span data-stu-id="f48a9-136">where *database_name* is the mirrored database whose session you want to you want to suspend.</span></span>  
  
     <span data-ttu-id="f48a9-137">次の例では、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースを一時停止します。</span><span class="sxs-lookup"><span data-stu-id="f48a9-137">The following example pauses the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET PARTNER SUSPEND;  
    ```  
  
##### <a name="to-resume-database-mirroring"></a><span data-ttu-id="f48a9-138">データベース ミラーリングを再開するには</span><span class="sxs-lookup"><span data-stu-id="f48a9-138">To resume database mirroring</span></span>  
  
1.  <span data-ttu-id="f48a9-139">いずれかのパートナーの [!INCLUDE[ssDE](../../includes/ssde-md.md)] に接続します。</span><span class="sxs-lookup"><span data-stu-id="f48a9-139">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] for either partner.</span></span>  
  
2.  <span data-ttu-id="f48a9-140">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f48a9-140">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f48a9-141">次の Transact-SQL ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="f48a9-141">Issue the following Transact-SQL statement:</span></span>  
  
     <span data-ttu-id="f48a9-142">ALTER DATABASE *database_name* SET PARTNER RESUME</span><span class="sxs-lookup"><span data-stu-id="f48a9-142">ALTER DATABASE *database_name* SET PARTNER RESUME</span></span>  
  
     <span data-ttu-id="f48a9-143">*database_name* は、再開するセッションのミラー化されたデータベースです。</span><span class="sxs-lookup"><span data-stu-id="f48a9-143">where *database_name* is the mirrored database whose session you want to resume.</span></span>  
  
     <span data-ttu-id="f48a9-144">次の例では、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースを一時停止します。</span><span class="sxs-lookup"><span data-stu-id="f48a9-144">The following example pauses the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET PARTNER RESUME;  
    ```  
  
##  <a name="follow-up-after-pausing-or-resuming-database-mirroring"></a><a name="FollowUp"></a> <span data-ttu-id="f48a9-145">補足情報: データベース ミラーリングの一時停止または再開した後</span><span class="sxs-lookup"><span data-stu-id="f48a9-145">Follow Up: After Pausing or Resuming Database Mirroring</span></span>  
  
-   <span data-ttu-id="f48a9-146">**データベース ミラーリングを一時停止した後**</span><span class="sxs-lookup"><span data-stu-id="f48a9-146">**After pausing database mirroring**</span></span>  
  
     <span data-ttu-id="f48a9-147">プライマリ データベースで、トランザクション ログが満杯にならないように予防策をとります。</span><span class="sxs-lookup"><span data-stu-id="f48a9-147">On the primary database, take precautions to avoid a full transaction log.</span></span> <span data-ttu-id="f48a9-148">詳細については、「 [トランザクション ログ &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f48a9-148">For more information, see [The Transaction Log &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md).</span></span>  
  
-   <span data-ttu-id="f48a9-149">**データベース ミラーリングを再開した後**</span><span class="sxs-lookup"><span data-stu-id="f48a9-149">**After resuming database mirroring**</span></span>  
  
     <span data-ttu-id="f48a9-150">データベース ミラーリングを再開することで、ミラー データベースを SYNCHRONIZING 状態にします。</span><span class="sxs-lookup"><span data-stu-id="f48a9-150">Resuming database mirroring places the mirror database in the SYNCHRONIZING state.</span></span> <span data-ttu-id="f48a9-151">安全性レベルが FULL の場合、プリンシパルに対するミラーの遅れが解消され、ミラー データベースが SYNCHRONIZED 状態になります。</span><span class="sxs-lookup"><span data-stu-id="f48a9-151">If the safety level is FULL, the mirror catches up with the principal and the mirror database enters the SYNCHRONIZED state.</span></span> <span data-ttu-id="f48a9-152">この時点で、フェールオーバーが可能になります。</span><span class="sxs-lookup"><span data-stu-id="f48a9-152">At this point, failover becomes possible.</span></span> <span data-ttu-id="f48a9-153">ミラーリング監視サーバーが存在していて、オンになっている場合は、自動フェールオーバーが可能です。</span><span class="sxs-lookup"><span data-stu-id="f48a9-153">If the witness is present and ON, automatic failover is possible.</span></span> <span data-ttu-id="f48a9-154">ミラーリング監視サーバーが存在しない場合は、手動フェールオーバーが可能です。</span><span class="sxs-lookup"><span data-stu-id="f48a9-154">In the absence of a witness, manual failover is possible.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="f48a9-155">関連タスク</span><span class="sxs-lookup"><span data-stu-id="f48a9-155">Related Tasks</span></span>  
  
-   [<span data-ttu-id="f48a9-156">データベース ミラーリングを削除する &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f48a9-156">Remove Database Mirroring &#40;SQL Server&#41;</span></span>](remove-database-mirroring-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="f48a9-157">参照</span><span class="sxs-lookup"><span data-stu-id="f48a9-157">See Also</span></span>  
 [<span data-ttu-id="f48a9-158">データベース ミラーリング &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f48a9-158">Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
  
