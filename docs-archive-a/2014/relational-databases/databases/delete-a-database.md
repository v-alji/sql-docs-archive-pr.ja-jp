---
title: データベースの削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- database removal [SQL Server], SQL Server Management Studio
- removing databases
- deleting databases
- dropping databases
- databases [SQL Server], dropping
- database removal [SQL Server]
ms.assetid: 1fd8c0f5-03e1-449a-af45-b8cacb479d9c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 633d97815cf69da12f1aa67fd8ef626a2d46e0b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742198"
---
# <a name="delete-a-database"></a><span data-ttu-id="c0b6c-102">データベースの削除</span><span class="sxs-lookup"><span data-stu-id="c0b6c-102">Delete a Database</span></span>
  <span data-ttu-id="c0b6c-103">このトピックでは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、ユーザー定義のデータベースを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c0b6c-103">This topic describes how to delete a user-defined database in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="c0b6c-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="c0b6c-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c0b6c-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="c0b6c-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c0b6c-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="c0b6c-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="c0b6c-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="c0b6c-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="c0b6c-108">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="c0b6c-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="c0b6c-109">Security</span><span class="sxs-lookup"><span data-stu-id="c0b6c-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c0b6c-110">**以下を使用してデータベースを削除するには:**</span><span class="sxs-lookup"><span data-stu-id="c0b6c-110">**To delete a database, using:**</span></span>  
  
     [<span data-ttu-id="c0b6c-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c0b6c-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c0b6c-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c0b6c-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="c0b6c-113">**補足情報:** [データベースを削除した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="c0b6c-113">**Follow Up:**  [After deleting a database](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c0b6c-114">はじめに</span><span class="sxs-lookup"><span data-stu-id="c0b6c-114">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="c0b6c-115">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="c0b6c-115">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="c0b6c-116">システム データベースは削除できません。</span><span class="sxs-lookup"><span data-stu-id="c0b6c-116">System databases cannot be deleted.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="c0b6c-117">前提条件</span><span class="sxs-lookup"><span data-stu-id="c0b6c-117">Prerequisites</span></span>  
  
-   <span data-ttu-id="c0b6c-118">データベース上に存在するデータベース スナップショットをすべて削除します。</span><span class="sxs-lookup"><span data-stu-id="c0b6c-118">Delete any database snapshots that exist on the database.</span></span> <span data-ttu-id="c0b6c-119">詳細については、「 [データベース スナップショットの削除 &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c0b6c-119">For more information, see [Drop a Database Snapshot &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md).</span></span>  
  
-   <span data-ttu-id="c0b6c-120">データベースがログ配布に関係している場合は、ログ配布を削除します。</span><span class="sxs-lookup"><span data-stu-id="c0b6c-120">If the database is involved in log shipping, remove log shipping.</span></span>  
  
-   <span data-ttu-id="c0b6c-121">データベースをトランザクション レプリケーション用にパブリッシュしている場合、またはマージ レプリケーションにパブリッシュしたりサブスクライブしている場合は、レプリケーションをデータベースから削除します。</span><span class="sxs-lookup"><span data-stu-id="c0b6c-121">If the database is published for transactional replication, or published or subscribed to merge replication, remove replication from the database.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="c0b6c-122">推奨事項</span><span class="sxs-lookup"><span data-stu-id="c0b6c-122">Recommendations</span></span>  
  
-   <span data-ttu-id="c0b6c-123">データベースの完全バックアップを行うことを検討します。</span><span class="sxs-lookup"><span data-stu-id="c0b6c-123">Consider taking a full backup of the database.</span></span> <span data-ttu-id="c0b6c-124">削除したデータベースの再作成は、バックアップを復元することによってのみ可能です。</span><span class="sxs-lookup"><span data-stu-id="c0b6c-124">A deleted database can be re-created only by restoring a backup.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c0b6c-125">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c0b6c-125">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c0b6c-126">Permissions</span><span class="sxs-lookup"><span data-stu-id="c0b6c-126">Permissions</span></span>  
 <span data-ttu-id="c0b6c-127">DROP DATABASE を実行するには、少なくともユーザーがデータベースで CONTROL 権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c0b6c-127">To execute DROP DATABASE, at a minimum, a user must have CONTROL permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c0b6c-128">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="c0b6c-128">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-database"></a><span data-ttu-id="c0b6c-129">データベースを削除するには</span><span class="sxs-lookup"><span data-stu-id="c0b6c-129">To delete a database</span></span>  
  
1.  <span data-ttu-id="c0b6c-130">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="c0b6c-130">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="c0b6c-131">**[データベース]** を展開し、削除するデータベースを右クリックして、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c0b6c-131">Expand **Databases**, right-click the database to delete, and then click **Delete**.</span></span>  
  
3.  <span data-ttu-id="c0b6c-132">適切なデータベースが選択されていることを確認して、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c0b6c-132">Confirm the correct database is selected, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c0b6c-133">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="c0b6c-133">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-database"></a><span data-ttu-id="c0b6c-134">データベースを削除するには</span><span class="sxs-lookup"><span data-stu-id="c0b6c-134">To delete a database</span></span>  
  
1.  <span data-ttu-id="c0b6c-135">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="c0b6c-135">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c0b6c-136">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c0b6c-136">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c0b6c-137">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c0b6c-137">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="c0b6c-138">この例では、 `Sales` データベースと `NewSales` データベースを削除します。</span><span class="sxs-lookup"><span data-stu-id="c0b6c-138">The example removes the `Sales` and `NewSales` databases.</span></span>  
  
```sql  
USE master ;  
GO  
DROP DATABASE Sales, NewSales ;  
GO  
```  
  
##  <a name="follow-up-after-deleting-a-database"></a><a name="FollowUp"></a><span data-ttu-id="c0b6c-139">補足情報: データベースを削除した後</span><span class="sxs-lookup"><span data-stu-id="c0b6c-139">Follow Up: After deleting a database</span></span>  
 <span data-ttu-id="c0b6c-140">**master** データベースをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="c0b6c-140">Back up the **master** database.</span></span> <span data-ttu-id="c0b6c-141">**master** データベースを復元する必要がある場合、 **master** データベースが最後にバックアップされてから削除されたデータベースがあると、システム カタログ ビュー内にそのデータベースの参照が残っているので、エラー メッセージが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="c0b6c-141">If **master** must be restored, any database that has been deleted since the last backup of **master** will still have references in the system catalog views and may cause error messages to be raised.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0b6c-142">参照</span><span class="sxs-lookup"><span data-stu-id="c0b6c-142">See Also</span></span>  
 <span data-ttu-id="c0b6c-143">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c0b6c-143">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 [<span data-ttu-id="c0b6c-144">ALTER DATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c0b6c-144">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
