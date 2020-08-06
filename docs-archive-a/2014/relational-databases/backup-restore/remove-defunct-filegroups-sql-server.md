---
title: 機能していないファイル グループの削除 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- piecemeal restores [SQL Server], defunct filegroups
- defunct filegroups
- restoring filegroups [SQL Server]
- deferred transactions
- filegroups [SQL Server], defunct
- unrestored filegroups
ms.assetid: 055f9c6a-5c18-4942-98e7-ec918f0ff975
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a2bcba095d668c5c1ab317269a18af4dc996f63b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736432"
---
# <a name="remove-defunct-filegroups-sql-server"></a><span data-ttu-id="cf37c-102">機能していないファイル グループの削除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="cf37c-102">Remove Defunct Filegroups (SQL Server)</span></span>
  <span data-ttu-id="cf37c-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、機能していないファイル グループを削除する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="cf37c-103">This topic describes how to remove defunct filegroups in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="cf37c-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="cf37c-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="cf37c-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="cf37c-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="cf37c-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="cf37c-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
-   [<span data-ttu-id="cf37c-107">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="cf37c-107">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="cf37c-108">Security</span><span class="sxs-lookup"><span data-stu-id="cf37c-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="cf37c-109">**機能していないファイル グループを削除する方法:**</span><span class="sxs-lookup"><span data-stu-id="cf37c-109">**To remove defunct filegroups, using:**</span></span>  
  
     [<span data-ttu-id="cf37c-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cf37c-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="cf37c-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cf37c-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="cf37c-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="cf37c-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="cf37c-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="cf37c-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="cf37c-114">このトピックの内容は、複数のファイルまたはファイル グループを含む [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース (単純復旧モデルでは、読み取り専用ファイル グループのみ) に関するものです。</span><span class="sxs-lookup"><span data-stu-id="cf37c-114">This topic is relevant for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases that contain multiple files or filegroups; and, under the simple model, only for read-only filegroups.</span></span>  
  
-   <span data-ttu-id="cf37c-115">オフラインのファイル グループが削除されると、ファイル グループ内のすべてのファイルが機能しなくなります。</span><span class="sxs-lookup"><span data-stu-id="cf37c-115">All files in a filegroup become defunct when an offline filegroup is removed.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="cf37c-116">推奨事項</span><span class="sxs-lookup"><span data-stu-id="cf37c-116">Recommendations</span></span>  
  
-   <span data-ttu-id="cf37c-117">ファイル グループが復元されておらず、復元する必要もなければ、データベースからそのファイル グループを削除することで、 *機能していない* 状態にすることができます。</span><span class="sxs-lookup"><span data-stu-id="cf37c-117">If an unrestored filegroup will never have to be restored, you can make the filegroup *defunct* by removing it from the database.</span></span> <span data-ttu-id="cf37c-118">機能していないファイル グループをこのデータベースに復元することはできませんが、そのメタデータはデータベース内に残ります。</span><span class="sxs-lookup"><span data-stu-id="cf37c-118">The defunct filegroup can never be restored to this database, but its metadata remains.</span></span> <span data-ttu-id="cf37c-119">ファイル グループが機能しなくなった後、データベースを再起動でき、復旧によって、復元されるファイル グループ間でデータベースの一貫性が維持されます。</span><span class="sxs-lookup"><span data-stu-id="cf37c-119">After the filegroup is defunct, the database can be restarted, and recovery will make the database consistent across the restored filegroups.</span></span>  
  
     <span data-ttu-id="cf37c-120">たとえば、ファイル グループを機能していない状態にすることは、データベース内で不要になったオフライン ファイル グループによって生じた遅延トランザクションを解決する方法の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="cf37c-120">For example, making a filegroup defunct is an option for resolving deferred transactions that were caused by an offline filegroup that you no longer want in the database.</span></span> <span data-ttu-id="cf37c-121">ファイル グループがオフラインであったことが原因で遅延されたトランザクションは、ファイル グループを機能していない状態にすると、遅延状態ではなくなります。</span><span class="sxs-lookup"><span data-stu-id="cf37c-121">Transactions that were deferred because the filegroup was offline are moved out of the deferred state after the filegroup becomes defunct.</span></span> <span data-ttu-id="cf37c-122">詳細については、「 [遅延トランザクション &#40;SQL Server&#41;](deferred-transactions-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf37c-122">For more information, see [Deferred Transactions &#40;SQL Server&#41;](deferred-transactions-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="cf37c-123">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="cf37c-123">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="cf37c-124">Permissions</span><span class="sxs-lookup"><span data-stu-id="cf37c-124">Permissions</span></span>  
 <span data-ttu-id="cf37c-125">データベースに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="cf37c-125">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="cf37c-126">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="cf37c-126">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-remove-defunct-filegroups"></a><span data-ttu-id="cf37c-127">機能していないファイル グループを削除するには</span><span class="sxs-lookup"><span data-stu-id="cf37c-127">To remove defunct filegroups</span></span>  
  
1.  <span data-ttu-id="cf37c-128">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="cf37c-128">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="cf37c-129">**[データベース]** を展開し、ファイルを削除するデータベースを右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cf37c-129">Expand **Databases**, right-click the database from which to delete the file, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="cf37c-130">**[ファイル]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cf37c-130">Select the **Files** page.</span></span>  
  
4.  <span data-ttu-id="cf37c-131">**[データベース ファイル]** グリッドで、削除するファイルを選択し、 **[削除]** をクリックした後 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cf37c-131">In the **Database files** grid, select the files to delete, click **Remove**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="cf37c-132">**[ファイル グループ]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cf37c-132">Select the **Filegroups** page.</span></span>  
  
6.  <span data-ttu-id="cf37c-133">**[行]** グリッドで、削除するファイル グループを選択し、 **[削除]** をクリックした後 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cf37c-133">In the **Rows** grid, select the filegroup to delete, click **Remove**, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="cf37c-134">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="cf37c-134">Using Transact-SQL</span></span>  
  
#### <a name="to-remove-defunct-filegroups"></a><span data-ttu-id="cf37c-135">機能していないファイル グループを削除するには</span><span class="sxs-lookup"><span data-stu-id="cf37c-135">To remove defunct filegroups</span></span>  
  
1.  <span data-ttu-id="cf37c-136">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="cf37c-136">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="cf37c-137">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cf37c-137">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="cf37c-138">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cf37c-138">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="cf37c-139">(**注:** この例では、ファイルとファイル グループが既に存在することを前提としています。</span><span class="sxs-lookup"><span data-stu-id="cf37c-139">(**Note:** This example assumes that the files and filegroup already exist.</span></span> <span data-ttu-id="cf37c-140">これらのオブジェクトを作成するには、「[ALTER DATABASE の File および Filegroup オプション](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)」トピックの例 B を参照してください)。最初の例では、`test1dat3` ステートメントと `test1dat4` 句を使用して、`ALTER DATABASE` ファイルと `REMOVE FILE` ファイルを機能していないファイル グループから削除します。</span><span class="sxs-lookup"><span data-stu-id="cf37c-140">To create these objects, see example B in the [ALTER DATABASE File and Filegroup Options](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) topic.) The first example removes the `test1dat3` and `test1dat4` files from the defunct filegroup by using the `ALTER DATABASE` statement with the `REMOVE FILE` clause.</span></span> <span data-ttu-id="cf37c-141">2 番目の例では、 `Test1FG1`句を使用して、機能していないファイル グループ `REMOVE FILEGROUP` を削除します。</span><span class="sxs-lookup"><span data-stu-id="cf37c-141">The second example removes the defunct filegroup `Test1FG1`by using the `REMOVE FILEGROUP` clause.</span></span>  
  
```sql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
REMOVE FILE test1dat3 ;  
ALTER DATABASE AdventureWorks2012  
REMOVE FILE test1dat4 ;  
GO  
  
```  
  
```sql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
REMOVE FILEGROUP Test1FG1 ;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="cf37c-142">参照</span><span class="sxs-lookup"><span data-stu-id="cf37c-142">See Also</span></span>  
 <span data-ttu-id="cf37c-143">[ALTER DATABASE の File および Filegroup オプション &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) </span><span class="sxs-lookup"><span data-stu-id="cf37c-143">[ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) </span></span>  
 <span data-ttu-id="cf37c-144">[遅延トランザクション &#40;SQL Server&#41;](deferred-transactions-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cf37c-144">[Deferred Transactions &#40;SQL Server&#41;](deferred-transactions-sql-server.md) </span></span>  
 <span data-ttu-id="cf37c-145">[ファイルの復元 &#40;完全復旧モデル&#41;](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="cf37c-145">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="cf37c-146">[ファイルの復元 &#40;単純復旧モデル&#41;](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="cf37c-146">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="cf37c-147">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cf37c-147">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="cf37c-148">[ページ復元 &#40;SQL Server&#41;](restore-pages-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cf37c-148">[Restore Pages &#40;SQL Server&#41;](restore-pages-sql-server.md) </span></span>  
 [<span data-ttu-id="cf37c-149">段階的な部分復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cf37c-149">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
