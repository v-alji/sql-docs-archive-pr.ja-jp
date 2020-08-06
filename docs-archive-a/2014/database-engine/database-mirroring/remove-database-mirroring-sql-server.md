---
title: データベース ミラーリングの削除 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], removing
- removing database mirroring [SQL Server]
ms.assetid: bbc4d7f7-3bc7-40d6-a822-af195fe7f8c0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 19c1d0449fa1c7434aeaf9c51e3b2dc7bc6b68c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716754"
---
# <a name="remove-database-mirroring-sql-server"></a><span data-ttu-id="06f59-102">データベース ミラーリングの削除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="06f59-102">Remove Database Mirroring (SQL Server)</span></span>
  <span data-ttu-id="06f59-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でデータベースからデータベース ミラーリングを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="06f59-103">This topic describes how to remove database mirroring from a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  <span data-ttu-id="06f59-104">データベース所有者は、データベースからミラーリングを削除することで、いつでも手動でデータベース ミラーリング セッションを停止できます。</span><span class="sxs-lookup"><span data-stu-id="06f59-104">At any time, the database owner can manually stop a database mirroring session by removing mirroring from the database.</span></span>  
  
 
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="06f59-105">はじめに</span><span class="sxs-lookup"><span data-stu-id="06f59-105">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="06f59-106">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="06f59-106">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="06f59-107">Permissions</span><span class="sxs-lookup"><span data-stu-id="06f59-107">Permissions</span></span>  
 <span data-ttu-id="06f59-108">データベースに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="06f59-108">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="06f59-109">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="06f59-109">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-remove-database-mirroring"></a><span data-ttu-id="06f59-110">データベース ミラーリングを削除するには</span><span class="sxs-lookup"><span data-stu-id="06f59-110">To remove database mirroring</span></span>  
  
1.  <span data-ttu-id="06f59-111">データベース ミラーリング セッション中にプリンシパル サーバー インスタンスに接続します。次に、オブジェクト エクスプローラーで、サーバー名をクリックしてサーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="06f59-111">During a database mirroring session, connect to the principal server instance, in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="06f59-112">**[データベース]** を展開し、データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="06f59-112">Expand **Databases**, and select the database.</span></span>  
  
3.  <span data-ttu-id="06f59-113">データベースを右クリックして **[タスク]** を選択し、 **[ミラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="06f59-113">Right-click the database, select **Tasks**, and then click **Mirror**.</span></span> <span data-ttu-id="06f59-114">**[データベースのプロパティ]** ダイアログ ボックスの **[ミラーリング]** ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="06f59-114">This opens the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="06f59-115">**[ページの選択]** ペインの **[ミラーリング]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="06f59-115">In the **Select a Page** pane, click **Mirroring**.</span></span>  
  
5.  <span data-ttu-id="06f59-116">ミラーリングを削除するには、 **[ミラーリングの削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="06f59-116">To remove mirroring, click **Remove Mirroring**.</span></span> <span data-ttu-id="06f59-117">確認を求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="06f59-117">A prompt asks for confirmation.</span></span> <span data-ttu-id="06f59-118">**[はい]** をクリックすると、セッションが停止し、データベースからミラーリングが削除されます。</span><span class="sxs-lookup"><span data-stu-id="06f59-118">If you click **Yes**, the session is stopped and mirroring is removed from the database.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="06f59-119">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="06f59-119">Using Transact-SQL</span></span>  
 <span data-ttu-id="06f59-120">データベース ミラーリングを削除するには、 **[データベースのプロパティ]** を使用します。</span><span class="sxs-lookup"><span data-stu-id="06f59-120">To remove database mirroring, use the **Database Properties**.</span></span> <span data-ttu-id="06f59-121">**[データベースのプロパティ]** ダイアログ ボックスの **[ミラーリング]** ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="06f59-121">use the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
#### <a name="to-remove-database-mirroring"></a><span data-ttu-id="06f59-122">データベース ミラーリングを削除するには</span><span class="sxs-lookup"><span data-stu-id="06f59-122">To remove database mirroring</span></span>  
  
1.  <span data-ttu-id="06f59-123">いずれかのミラーリング パートナーの [!INCLUDE[ssDE](../../includes/ssde-md.md)] に接続します。</span><span class="sxs-lookup"><span data-stu-id="06f59-123">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] of either mirroring partner.</span></span>  
  
2.  <span data-ttu-id="06f59-124">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="06f59-124">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="06f59-125">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="06f59-125">Issue the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```  
    ALTER DATABASE database_name SET PARTNER OFF  
    ```  
  
     <span data-ttu-id="06f59-126">*database_name* は、削除するセッションのミラー化されたデータベースです。</span><span class="sxs-lookup"><span data-stu-id="06f59-126">where *database_name* is the mirrored database whose session you want to remove.</span></span>  
  
     <span data-ttu-id="06f59-127">次の例では、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースからデータベース ミラーリングを削除します。</span><span class="sxs-lookup"><span data-stu-id="06f59-127">The following example removes database mirroring from the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET PARTNER OFF;  
    ```  
  
##  <a name="follow-up-removing-database-mirroring"></a><a name="FollowUp"></a><span data-ttu-id="06f59-128">補足情報: データベース ミラーリングの削除</span><span class="sxs-lookup"><span data-stu-id="06f59-128">Follow Up: Removing Database Mirroring</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="06f59-129">ミラーリングの削除による影響の詳細については、「[データベース ミラーリングの削除 &#40;SQL Server&#41;](database-mirroring-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06f59-129">For information about the impact of removing mirroring, see [Removing Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
-   <span data-ttu-id="06f59-130">**データベースでミラーリングを再開する場合**</span><span class="sxs-lookup"><span data-stu-id="06f59-130">**If you intend to restart mirroring on the database**</span></span>  
  
     <span data-ttu-id="06f59-131">ミラーリングを再開する前に、ミラーリングが削除された後にプリンシパル データベースで作成されたログ バックアップをすべて、ミラー データベースに適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="06f59-131">Any log backups taken on the principal database after mirroring was removed must all be applied to the mirror database before you can restart mirroring.</span></span>  
  
-   <span data-ttu-id="06f59-132">**ミラーリングを再開しない場合**</span><span class="sxs-lookup"><span data-stu-id="06f59-132">**If you do not intent to restart mirroring**</span></span>  
  
     <span data-ttu-id="06f59-133">必要に応じて、以前のミラー データベースを復旧できます。</span><span class="sxs-lookup"><span data-stu-id="06f59-133">Optionally, you can recover the former mirror database.</span></span> <span data-ttu-id="06f59-134">以前にミラー サーバーだったサーバー インスタンスで、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="06f59-134">On the server instance that was the mirror server, you can use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```  
    RESTORE DATABASE database_name WITH RECOVERY;  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="06f59-135">このデータベースを復旧すると、異なる 2 つのデータベースが同じ名前でオンラインになります。</span><span class="sxs-lookup"><span data-stu-id="06f59-135">If you recover this database, two divergent databases with the same name are online.</span></span> <span data-ttu-id="06f59-136">そのため、クライアントがどちらか一方のデータベース (通常は最新のプリンシパル データベース) にしかアクセスできないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="06f59-136">Therefore, you need to ensure that clients can access only one of them-typically the most recent principal database.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="06f59-137">関連タスク</span><span class="sxs-lookup"><span data-stu-id="06f59-137">Related Tasks</span></span>  
  
-   [<span data-ttu-id="06f59-138">データベース ミラーリング セッションを一時停止または再開する &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="06f59-138">Pause or Resume a Database Mirroring Session &#40;SQL Server&#41;</span></span>](pause-or-resume-a-database-mirroring-session-sql-server.md)  
  
-   [<span data-ttu-id="06f59-139">データベース ミラーリング セッションからのミラーリング監視サーバーの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="06f59-139">Remove the Witness from a Database Mirroring Session &#40;SQL Server&#41;</span></span>](remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
-   [<span data-ttu-id="06f59-140">Windows 認証を使用してデータベース ミラーリング セッションを確立する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="06f59-140">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="06f59-141">Windows 認証を使用してデータベース ミラーリング セッションを確立する方法 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="06f59-141">Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](database-mirroring-establish-session-windows-authentication.md)  
  
-   [<span data-ttu-id="06f59-142">例:証明書を使用したデータベース ミラーリングの設定 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="06f59-142">Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;</span></span>](example-setting-up-database-mirroring-using-certificates-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="06f59-143">参照</span><span class="sxs-lookup"><span data-stu-id="06f59-143">See Also</span></span>  
 <span data-ttu-id="06f59-144">[データベース ミラーリング &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="06f59-144">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="06f59-145">[データベース ミラーリングの設定 &#40;SQL Server&#41;](setting-up-database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="06f59-145">[Setting Up Database Mirroring &#40;SQL Server&#41;](setting-up-database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="06f59-146">AlwaysOn 可用性グループ (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="06f59-146">AlwaysOn Availability Groups (SQL Server)</span></span>](../availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
