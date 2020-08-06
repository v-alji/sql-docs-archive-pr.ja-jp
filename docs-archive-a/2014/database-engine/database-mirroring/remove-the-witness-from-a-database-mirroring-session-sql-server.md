---
title: データベース ミラーリング セッションからのミラーリング監視の削除 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- witness [SQL Server], turning off
- witness [SQL Server], removing
- database mirroring [SQL Server], witness
ms.assetid: f3ce7afc-8936-4d35-80ce-d0f8fbc318d3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d5ede54aca3588a6fcd7cee8759112b606eac752
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716753"
---
# <a name="remove-the-witness-from-a-database-mirroring-session-sql-server"></a><span data-ttu-id="f409d-102">データベース ミラーリング セッションからのミラーリング監視の削除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f409d-102">Remove the Witness from a Database Mirroring Session (SQL Server)</span></span>
  <span data-ttu-id="f409d-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でデータベース ミラーリング セッションからミラーリング監視サーバーを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f409d-103">This topic describes how to remove a witness from a database mirroring session in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="f409d-104">データベース ミラーリング セッション中のどの時点でも、データベース所有者は、データベース ミラーリング セッションのミラーリング監視サーバーを無効にできます。</span><span class="sxs-lookup"><span data-stu-id="f409d-104">At any time during a database mirroring session, the database owner can turn off the witness for a database mirroring session.</span></span>  
  
 <span data-ttu-id="f409d-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="f409d-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f409d-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="f409d-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f409d-107">Security</span><span class="sxs-lookup"><span data-stu-id="f409d-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f409d-108">**ミラーリング監視サーバーの削除に使用するツール:**</span><span class="sxs-lookup"><span data-stu-id="f409d-108">**To Replace remove the witness, using:**</span></span>  
  
     [<span data-ttu-id="f409d-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f409d-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f409d-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f409d-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="f409d-111">**補足情報:**  [ミラーリング監視サーバーを削除した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="f409d-111">**Follow Up:**  [After Removing the Witness](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f409d-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="f409d-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f409d-113">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="f409d-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f409d-114">Permissions</span><span class="sxs-lookup"><span data-stu-id="f409d-114">Permissions</span></span>  
 <span data-ttu-id="f409d-115">データベースに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="f409d-115">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f409d-116">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="f409d-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-remove-the-witness"></a><span data-ttu-id="f409d-117">ミラーリング監視サーバーを削除するには</span><span class="sxs-lookup"><span data-stu-id="f409d-117">To remove the witness</span></span>  
  
1.  <span data-ttu-id="f409d-118">プリンシパル サーバー インスタンスに接続し、 **[オブジェクト エクスプローラー]** ペインでサーバー名をクリックして、サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="f409d-118">Connect to the principal server instance and, in the **Object Explorer** pane, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="f409d-119">**[データベース]** を展開し、削除するミラーリング監視が設定されているデータベースをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f409d-119">Expand **Databases**, and select the database whose witness you want to remove.</span></span>  
  
3.  <span data-ttu-id="f409d-120">データベースを右クリックして **[タスク]** を選択し、 **[ミラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f409d-120">Right-click the database, select **Tasks**, and then click **Mirror**.</span></span> <span data-ttu-id="f409d-121">**[データベースのプロパティ]** ダイアログ ボックスの **[ミラーリング]** ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="f409d-121">This opens the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="f409d-122">ミラーリング監視サーバーを削除するには、 **[ミラーリング監視]** フィールドからそのサーバー ネットワーク アドレスを削除します。</span><span class="sxs-lookup"><span data-stu-id="f409d-122">To remove the witness, delete its server network address from the **Witness** field.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f409d-123">自動フェールオーバーを伴う高い安全性モードから高パフォーマンス モードに切り替えると、 **[ミラーリング監視]** フィールドの内容は自動的に消去されます。</span><span class="sxs-lookup"><span data-stu-id="f409d-123">If you switch from high-safety mode with automatic failover to high-performance mode, the **Witness** field is automatically cleared.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f409d-124">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="f409d-124">Using Transact-SQL</span></span>  
  
#### <a name="to-remove-the-witness"></a><span data-ttu-id="f409d-125">ミラーリング監視サーバーを削除するには</span><span class="sxs-lookup"><span data-stu-id="f409d-125">To remove the witness</span></span>  
  
1.  <span data-ttu-id="f409d-126">パートナー サーバー インスタンスで [!INCLUDE[ssDE](../../includes/ssde-md.md)] に接続します。</span><span class="sxs-lookup"><span data-stu-id="f409d-126">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on either partner server instance.</span></span>  
  
2.  <span data-ttu-id="f409d-127">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f409d-127">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f409d-128">次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="f409d-128">Issue the following statement:</span></span>  
  
     <span data-ttu-id="f409d-129">[ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) *database_name* SET WITNESS OFF</span><span class="sxs-lookup"><span data-stu-id="f409d-129">[ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) *database_name* SET WITNESS OFF</span></span>  
  
     <span data-ttu-id="f409d-130">*database_name* はミラー化されたデータベースの名前です。</span><span class="sxs-lookup"><span data-stu-id="f409d-130">where *database_name* is the name of the mirrored database.</span></span>  
  
     <span data-ttu-id="f409d-131">次の例では、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースからミラーリング監視サーバーを削除します。</span><span class="sxs-lookup"><span data-stu-id="f409d-131">The following example removes the witness from the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET WITNESS OFF ;  
    ```  
  
##  <a name="follow-up-after-removing-the-witness"></a><a name="FollowUp"></a><span data-ttu-id="f409d-132">補足情報: ミラーリング監視サーバーを削除した後</span><span class="sxs-lookup"><span data-stu-id="f409d-132">Follow Up: After Removing the Witness</span></span>  
 <span data-ttu-id="f409d-133">ミラーリング監視を無効にすると、 [動作モード](database-mirroring-operating-modes.md)トランザクションの安全性の設定に応じて変更されます。</span><span class="sxs-lookup"><span data-stu-id="f409d-133">Turning off the witness changes the [operating mode](database-mirroring-operating-modes.md)in accordance with the transaction-safety setting:</span></span>  
  
-   <span data-ttu-id="f409d-134">トランザクションの安全性の設定が FULL (既定値) の場合、セッションは自動フェールオーバーを伴わない高い安全性の同期モードで動作します。</span><span class="sxs-lookup"><span data-stu-id="f409d-134">If transaction safety is set to FULL (the default), the session uses high-safety, synchronous mode without automatic failover.</span></span>  
  
-   <span data-ttu-id="f409d-135">トランザクションの安全性が OFF に設定されている場合、セッションは非同期 (高パフォーマンス モード) で動作し、クォーラムを必要としません。</span><span class="sxs-lookup"><span data-stu-id="f409d-135">If transaction safety is set to OFF, the session operates asynchronously (in high-performance mode) without requiring quorum.</span></span> <span data-ttu-id="f409d-136">ただし、トランザクションの安全性を OFF に設定した場合は常に、WITNESS も OFF に設定することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f409d-136">Whenever transaction safety is turned off, we strongly recommend also turning the witness off.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="f409d-137">データベースのトランザクションの安全性設定は、各パートナーについて [sys.database_mirroring](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql) カタログ ビューの **mirroring_safety_level** 列と **mirroring_safety_level_desc** 列に記録されます。</span><span class="sxs-lookup"><span data-stu-id="f409d-137">The transaction safety setting of the database is recorded on each partner in the [sys.database_mirroring](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql) catalog view in the **mirroring_safety_level** and **mirroring_safety_level_desc** columns.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="f409d-138">関連タスク</span><span class="sxs-lookup"><span data-stu-id="f409d-138">Related Tasks</span></span>  
  
-   [<span data-ttu-id="f409d-139">Windows 認証を使用してデータベースのミラーリング監視を追加する &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f409d-139">Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="f409d-140">データベース ミラーリング監視サーバーを追加または置き換える方法 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="f409d-140">Add or Replace a Database Mirroring Witness &#40;SQL Server Management Studio&#41;</span></span>](../database-mirroring/add-or-replace-a-database-mirroring-witness-sql-server-management-studio.md)  
  
## <a name="see-also"></a><span data-ttu-id="f409d-141">参照</span><span class="sxs-lookup"><span data-stu-id="f409d-141">See Also</span></span>  
 <span data-ttu-id="f409d-142">[ALTER DATABASE データベース ミラーリング &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span><span class="sxs-lookup"><span data-stu-id="f409d-142">[ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span></span>  
 <span data-ttu-id="f409d-143">[データベースミラーリングセッションでのトランザクションの安全性の変更 Transact-sql&#41;の &#40;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="f409d-143">[Change Transaction Safety in a Database Mirroring Session &#40;Transact-SQL&#41;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md) </span></span>  
 <span data-ttu-id="f409d-144">[Windows 認証 &#40;使用してデータベースミラーリング監視サーバーを追加する Transact-sql&#41;](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="f409d-144">[Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md) </span></span>  
 [<span data-ttu-id="f409d-145">データベース ミラーリング監視サーバー</span><span class="sxs-lookup"><span data-stu-id="f409d-145">Database Mirroring Witness</span></span>](database-mirroring-witness.md)  
  
  
