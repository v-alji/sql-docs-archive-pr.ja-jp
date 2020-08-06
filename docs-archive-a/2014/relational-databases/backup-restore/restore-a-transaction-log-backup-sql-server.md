---
title: トランザクション ログ バックアップの復元 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restoretlog.options.f1
- sql12.swb.restoretlog.general.f1
helpviewer_keywords:
- restore log
- backing up transaction logs [SQL Server], restoring
- transaction log backups [SQL Server], restoring
- restoring transaction logs [SQL Server], restoring backups
- transaction log restores [SQL Server], SQL Server Management Studio
ms.assetid: 1de2b888-78a6-4fb2-a647-ba4bf097caf3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 68fe4bbc199d6555bd490d25f92491100b8bbfcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643424"
---
# <a name="restore-a-transaction-log-backup-sql-server"></a><span data-ttu-id="9ce6f-102">トランザクション ログ バックアップの復元 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9ce6f-102">Restore a Transaction Log Backup (SQL Server)</span></span>
  <span data-ttu-id="9ce6f-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、トランザクション ログ バックアップを復元する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-103">This topic describes how to restore a transaction log backup in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="9ce6f-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="9ce6f-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9ce6f-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="9ce6f-106">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="9ce6f-107">Security</span><span class="sxs-lookup"><span data-stu-id="9ce6f-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9ce6f-108">**トランザクション ログ バックアップを復元するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-108">**To restore a transaction log backup, using:**</span></span>  
  
     [<span data-ttu-id="9ce6f-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9ce6f-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="9ce6f-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9ce6f-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   [<span data-ttu-id="9ce6f-111">関連タスク</span><span class="sxs-lookup"><span data-stu-id="9ce6f-111">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9ce6f-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="9ce6f-112">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="9ce6f-113">前提条件</span><span class="sxs-lookup"><span data-stu-id="9ce6f-113">Prerequisites</span></span>  
  
-   <span data-ttu-id="9ce6f-114">バックアップは、作成された順序で復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-114">Backups must be restored in the order in which they were created.</span></span> <span data-ttu-id="9ce6f-115">特定のトランザクション ログ バックアップを復元する前に、まず、次に示す以前のバックアップを復元する必要があります。ただし、コミットされていないトランザクションはロールバックしません (WITH NORECOVERY)。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-115">Before you can restore a particular transaction log backup, you must first restore the following previous backups without rolling back uncommitted transactions, that is WITH NORECOVERY:</span></span>  
  
    -   <span data-ttu-id="9ce6f-116">データベース全体のバックアップおよび、特定のトランザクション ログ バックアップの前に行われた差分バックアップがある場合は、最後の差分バックアップ</span><span class="sxs-lookup"><span data-stu-id="9ce6f-116">The full database backup and the last differential backup, if any, taken before the particular transaction log backup.</span></span> <span data-ttu-id="9ce6f-117">データベースの最新の完全バックアップまたは差分バックアップが作成される前に、データベースが完全復旧モデルまたは一括ログ復旧モデルを使用していた。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-117">Before the most recent full or differential database backup was created, the database must have been using the full recovery model or bulk-logged recovery model.</span></span>  
  
    -   <span data-ttu-id="9ce6f-118">データベース全体のバックアップまたは差分バックアップ (差分バックアップを復元する場合) 以降、特定のトランザクション ログ バックアップ以前に行われたすべてのトランザクション ログ バックアップ</span><span class="sxs-lookup"><span data-stu-id="9ce6f-118">All transaction log backups taken after the full database backup or the differential backup (if you restore one) and before the particular transaction log backup.</span></span> <span data-ttu-id="9ce6f-119">ログ バックアップが、作成された順序で、ログ チェーンにギャップがないように、適用されている。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-119">Log backups must be applied in the sequence in which they were created, without any gaps in the log chain.</span></span>  
  
         <span data-ttu-id="9ce6f-120">トランザクション ログ バックアップの詳細については、「[トランザクション ログ バックアップ &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)」および「[トランザクション ログ バックアップの適用 &#40;SQL Server&#41;](apply-transaction-log-backups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-120">For more information about transaction log backups, see [Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) and [Apply Transaction Log Backups &#40;SQL Server&#41;](apply-transaction-log-backups-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9ce6f-121">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="9ce6f-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9ce6f-122">Permissions</span><span class="sxs-lookup"><span data-stu-id="9ce6f-122">Permissions</span></span>  
 <span data-ttu-id="9ce6f-123">RESTORE 権限は、サーバーでメンバーシップ情報を常に確認できるロールに与えられます。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-123">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="9ce6f-124">固定データベース ロールのメンバーシップは、データベースがアクセス可能で破損していない場合にのみ確認することができますが、RESTORE の実行時にはデータベースがアクセス可能で損傷していないことが必ずしも保証されないため、 **db_owner** 固定データベース ロールのメンバーには RESTORE 権限は与えられません。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-124">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9ce6f-125">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="9ce6f-125">Using SQL Server Management Studio</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="9ce6f-126">通常の復元処理では、データ バックアップおよび差分バックアップと共に、 **[データベースの復元]** ダイアログ ボックスでログ バックアップを選択します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-126">The normal process of a restore is to select the log backups in the **Restore Database** dialog box along with the data and differential backups.</span></span>  
  
#### <a name="to-restore-a-transaction-log-backup"></a><span data-ttu-id="9ce6f-127">トランザクション ログ バックアップを復元するには</span><span class="sxs-lookup"><span data-stu-id="9ce6f-127">To restore a transaction log backup</span></span>  
  
1.  <span data-ttu-id="9ce6f-128">オブジェクト エクスプローラーで適切な [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続した後、サーバー名をクリックしてサーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-128">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="9ce6f-129">**[データベース]** を展開します。さらに、そのデータベースに応じて、ユーザー データベースを選択するか、または **[システム データベース]** を展開してシステム データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-129">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="9ce6f-130">データベースを右クリックして **[タスク]** をポイントし、 **[復元]** をポイントします。次に、 **[トランザクション ログ]** をクリックし、 **[トランザクション ログの復元]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-130">Right-click the database, point to **Tasks**, point to **Restore**, and then click **Transaction Log**, which opens the **Restore Transaction Log** dialog box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9ce6f-131">**[トランザクション ログ]** がグレーで表示される場合は、最初に完全バックアップまたは差分バックアップを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-131">If **Transaction Log** is grayed out, you may need to restore a full or differential backup first.</span></span> <span data-ttu-id="9ce6f-132">**[データベース]** バックアップ ダイアログ ボックスを使用してください。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-132">Use the **Database** backup dialog box.</span></span>  
  
4.  <span data-ttu-id="9ce6f-133">**[全般]** ページの **[データベース]** ボックスの一覧で、データベースの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-133">On the **General** page, in the **Database** list box, select the name of a database.</span></span> <span data-ttu-id="9ce6f-134">復元状態のデータベースだけが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-134">Only databases in the restoring state are listed.</span></span>  
  
5.  <span data-ttu-id="9ce6f-135">復元するバックアップ セットの復元元ファイルと場所を指定するには、次のいずれかのオプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-135">To specify the source and location of the backup sets to restore, click one of the following options:</span></span>  
  
    -   <span data-ttu-id="9ce6f-136">**[データベースの以前のバックアップから]**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-136">**From previous backups of database**</span></span>  
  
         <span data-ttu-id="9ce6f-137">復元するデータベースをドロップダウン リストから選択します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-137">Select the database to restore from the drop-down list.</span></span> <span data-ttu-id="9ce6f-138">このリストには、 **msdb** バックアップ履歴に従ってバックアップされたデータベースのみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-138">The list contains only databases that have been backed up according to the **msdb** backup history.</span></span>  
  
    -   <span data-ttu-id="9ce6f-139">**[ファイルまたはテープから]**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-139">**From file or tape**</span></span>  
  
         <span data-ttu-id="9ce6f-140">参照ボタン ( **[...]** ) をクリックし、 **[バックアップ デバイスの選択]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-140">Click the browse (**...**) button to open the **Select backup devices** dialog box.</span></span> <span data-ttu-id="9ce6f-141">**[バックアップ メディアの種類]** ボックスから、デバイスの種類を 1 つ選択します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-141">In the **Backup media type** box, select one of the listed device types.</span></span> <span data-ttu-id="9ce6f-142">**[バックアップ メディア]** ボックスにデバイスを追加するには、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-142">To select one or more devices for the **Backup media** box, click **Add**.</span></span>  
  
         <span data-ttu-id="9ce6f-143">**[バックアップ メディア]** ボックスに目的のデバイスを追加したら、 **[OK]** をクリックして、 **[全般]** ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-143">After you add the devices you want to the **Backup media** list box, click **OK** to return to the **General** page.</span></span>  
  
6.  <span data-ttu-id="9ce6f-144">**[復元するトランザクション ログのバックアップを選択]** グリッドで、復元するバックアップを選択します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-144">In the **Select the transaction log backups to restore** grid, select the backups to restore.</span></span> <span data-ttu-id="9ce6f-145">このグリッドには、選択したデータベースで使用できるトランザクション ログ バックアップが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-145">This grid lists the transaction log backups available for the selected database.</span></span> <span data-ttu-id="9ce6f-146">ログ バックアップは、データベースの **[最初の LSN]** が **[最後の LSN]** よりも大きい場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-146">A log backup is available only if its **First LSN** greater than the **Last LSN** of the database.</span></span> <span data-ttu-id="9ce6f-147">ログ バックアップは、含まれているログ シーケンス番号 (LSN) の順に一覧表示され、この順序で復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-147">Log backups are listed in the order of the log sequence numbers (LSN) they contain, and they must be restored in this order.</span></span>  
  
     <span data-ttu-id="9ce6f-148">次の表は、グリッドの列ヘッダーとその値を示しています。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-148">The following table lists the column headers of the grid and describes their values.</span></span>  
  
    |<span data-ttu-id="9ce6f-149">ヘッダー</span><span class="sxs-lookup"><span data-stu-id="9ce6f-149">Header</span></span>|<span data-ttu-id="9ce6f-150">値</span><span class="sxs-lookup"><span data-stu-id="9ce6f-150">Value</span></span>|  
    |------------|-----------|  
    |<span data-ttu-id="9ce6f-151">**復元**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-151">**Restore**</span></span>|<span data-ttu-id="9ce6f-152">チェック ボックスをオンにしたバックアップ セットが復元されます。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-152">Selected check boxes indicate the backup sets to be restored.</span></span>|  
    |<span data-ttu-id="9ce6f-153">**名前**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-153">**Name**</span></span>|<span data-ttu-id="9ce6f-154">バックアップ セットの名前。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-154">Name of the backup set.</span></span>|  
    |<span data-ttu-id="9ce6f-155">**コンポーネント**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-155">**Component**</span></span>|<span data-ttu-id="9ce6f-156">バックアップされるコンポーネント: **[データベース]** 、 **[ファイル]** 、または \<blank> (トランザクション ログ用)。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-156">Backed-up component: **Database**, **File**, or \<blank> (for transaction logs).</span></span>|  
    |<span data-ttu-id="9ce6f-157">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-157">**Database**</span></span>|<span data-ttu-id="9ce6f-158">バックアップ操作に関係するデータベース名。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-158">Name of the database involved in the backup operation.</span></span>|  
    |<span data-ttu-id="9ce6f-159">**[開始日]**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-159">**Start Date**</span></span>|<span data-ttu-id="9ce6f-160">バックアップ操作の開始日時 (クライアントの地域設定に準拠)。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-160">Date and time when the backup operation began, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="9ce6f-161">**完了日**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-161">**Finish Date**</span></span>|<span data-ttu-id="9ce6f-162">バックアップ操作の完了日時 (クライアントの地域設定に準拠)。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-162">Date and time when the backup operation finished, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="9ce6f-163">**最初の LSN**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-163">**First LSN**</span></span>|<span data-ttu-id="9ce6f-164">バックアップ セット内の先頭のトランザクションのログ シーケンス番号。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-164">Log sequence number of the first transaction in the backup set.</span></span> <span data-ttu-id="9ce6f-165">ファイル バックアップの場合は空白。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-165">Blank for file backups.</span></span>|  
    |<span data-ttu-id="9ce6f-166">**最後の LSN**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-166">**Last LSN**</span></span>|<span data-ttu-id="9ce6f-167">バックアップ セット内の最後のトランザクションのログ シーケンス番号。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-167">Log sequence number of the last transaction in the backup set.</span></span> <span data-ttu-id="9ce6f-168">ファイル バックアップの場合は空白。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-168">Blank for file backups.</span></span>|  
    |<span data-ttu-id="9ce6f-169">**チェックポイントの LSN**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-169">**Checkpoint LSN**</span></span>|<span data-ttu-id="9ce6f-170">バックアップが作成された時点における最新チェックポイントのログ シーケンス番号。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-170">Log sequence number of the most recent checkpoint at the time the backup was created.</span></span>|  
    |<span data-ttu-id="9ce6f-171">**全 LSN**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-171">**Full LSN**</span></span>|<span data-ttu-id="9ce6f-172">データベース全体の最新バックアップのログ シーケンス番号。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-172">Log sequence number of the most recent full database backup.</span></span>|  
    |<span data-ttu-id="9ce6f-173">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-173">**Server**</span></span>|<span data-ttu-id="9ce6f-174">バックアップ操作を実行したデータベース エンジン インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-174">Name of the Database Engine instance that performed the backup operation.</span></span>|  
    |<span data-ttu-id="9ce6f-175">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-175">**User Name**</span></span>|<span data-ttu-id="9ce6f-176">バックアップ操作を実行したユーザーの名前。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-176">Name of the user who performed the backup operation.</span></span>|  
    |<span data-ttu-id="9ce6f-177">**[サイズ]**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-177">**Size**</span></span>|<span data-ttu-id="9ce6f-178">バックアップ セットのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-178">Size of the backup set in bytes.</span></span>|  
    |<span data-ttu-id="9ce6f-179">**Position**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-179">**Position**</span></span>|<span data-ttu-id="9ce6f-180">ボリューム内でのバックアップ セットの位置。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-180">Position of the backup set in the volume.</span></span>|  
    |<span data-ttu-id="9ce6f-181">**[有効期限]**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-181">**Expiration**</span></span>|<span data-ttu-id="9ce6f-182">バックアップ セットの期限が切れる日付と時刻。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-182">Date and time the backup set expires.</span></span>|  
  
7.  <span data-ttu-id="9ce6f-183">次のいずれかを選択してください。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-183">Select one of the following:</span></span>  
  
    -   <span data-ttu-id="9ce6f-184">**[特定の時点]**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-184">**Point in time**</span></span>  
  
         <span data-ttu-id="9ce6f-185">既定値 ( **[最新の候補]** ) をそのまま使用するか、または参照ボタンをクリックして **[特定の時点に復元]** ダイアログ ボックスを開き、特定の日付と時刻を選択します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-185">Either retain the default (**Most recent possible**) or select a specific date and time by clicking the browse button, which opens the **Point in Time Restore** dialog box.</span></span>  
  
    -   <span data-ttu-id="9ce6f-186">**[マークされたトランザクション]**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-186">**Marked transaction**</span></span>  
  
         <span data-ttu-id="9ce6f-187">以前にマークされたトランザクションにデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-187">Restore the database to a previously marked transaction.</span></span> <span data-ttu-id="9ce6f-188">このオプションを選択すると、 **[マークされたトランザクションの選択]** ダイアログ ボックスが開いて、選択されたトランザクション ログ バックアップで使用できるマークされたトランザクションの一覧がグリッドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-188">Selecting this option launches the **Select Marked Transaction** dialog box, which displays a grid listing the marked transactions available in the selected transaction log backups.</span></span>  
  
         <span data-ttu-id="9ce6f-189">既定では、マークされたトランザクションの前まで復元され、マークされたトランザクションは復元されません。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-189">By default, the restore is up to, but excluding, the marked transaction.</span></span> <span data-ttu-id="9ce6f-190">マークされたトランザクションも復元するには、 **[マークされたトランザクションを含める]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-190">To restore the marked transaction also, select **Include marked transaction**.</span></span>  
  
         <span data-ttu-id="9ce6f-191">次の表は、グリッドの列ヘッダーとその値を示しています。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-191">The following table lists the column headers of the grid and describes their values.</span></span>  
  
        |<span data-ttu-id="9ce6f-192">ヘッダー</span><span class="sxs-lookup"><span data-stu-id="9ce6f-192">Header</span></span>|<span data-ttu-id="9ce6f-193">値</span><span class="sxs-lookup"><span data-stu-id="9ce6f-193">Value</span></span>|  
        |------------|-----------|  
        |\<blank>|<span data-ttu-id="9ce6f-194">マークを選択するためのチェック ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-194">Displays a checkbox for selecting the mark.</span></span>|  
        |<span data-ttu-id="9ce6f-195">**トランザクション マーク**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-195">**Transaction Mark**</span></span>|<span data-ttu-id="9ce6f-196">トランザクションがコミットされたときにユーザーによって指定された、マークされたトランザクションの名前。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-196">Name of the marked transaction specified by the user when the transaction was committed.</span></span>|  
        |<span data-ttu-id="9ce6f-197">**Date**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-197">**Date**</span></span>|<span data-ttu-id="9ce6f-198">トランザクションがコミットされた日時。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-198">Date and time of the transaction when it was committed.</span></span> <span data-ttu-id="9ce6f-199">トランザクションの日付と時刻は、クライアント コンピューターの日付と時刻ではなく、 **msdbgmarkhistory** テーブルに記録されたとおりに表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-199">Transaction date and time are displayed as recorded in the **msdbgmarkhistory** table, not in the client computer's date and time.</span></span>|  
        |<span data-ttu-id="9ce6f-200">**説明**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-200">**Description**</span></span>|<span data-ttu-id="9ce6f-201">トランザクションがコミットされたときにユーザーが指定したマークされたトランザクションの説明 (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-201">Description of marked transaction specified by the user when the transaction was committed (if any).</span></span>|  
        |<span data-ttu-id="9ce6f-202">**LSN (LSN)**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-202">**LSN**</span></span>|<span data-ttu-id="9ce6f-203">マークされたトランザクションのログ シーケンス番号。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-203">Log sequence number of the marked transaction.</span></span>|  
        |<span data-ttu-id="9ce6f-204">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-204">**Database**</span></span>|<span data-ttu-id="9ce6f-205">マークされたトランザクションがコミットされたデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-205">Name of the database where the marked transaction was committed.</span></span>|  
        |<span data-ttu-id="9ce6f-206">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-206">**User Name**</span></span>|<span data-ttu-id="9ce6f-207">マークされたトランザクションをコミットしたデータベース ユーザーの名前。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-207">Name of the database user who committed the marked transaction.</span></span>|  
  
8.  <span data-ttu-id="9ce6f-208">詳細設定オプションを表示または選択するには、 **[ページの選択]** ペインの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-208">To view or select the advanced options, click **Options** in the **Select a page** pane.</span></span>  
  
9. <span data-ttu-id="9ce6f-209">**[復元オプション]** セクションには次の選択肢があります。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-209">In the **Restore options** section, the choices are:</span></span>  
  
    -   <span data-ttu-id="9ce6f-210">**[レプリケーションの設定を保存する (WITH KEEP_REPLICATION)]**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-210">**Preserve the replication settings (WITH KEEP_REPLICATION)**</span></span>  
  
         <span data-ttu-id="9ce6f-211">パブリッシュされたデータベースを、そのデータベースが作成されたサーバー以外のサーバーに復元するときに、レプリケーションの設定を保存します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-211">Preserves the replication settings when restoring a published database to a server other than the server where the database was created.</span></span>  
  
         <span data-ttu-id="9ce6f-212">このオプションは、[コミットされていない**トランザクションをロールバックして、データベースを使用**可能な状態にする (後で説明します)] オプションでのみ使用できます。これは、オプションを使用してバックアップを復元することと同じです。 `RECOVERY`</span><span class="sxs-lookup"><span data-stu-id="9ce6f-212">This option is available only with the **Leave the database ready for use by rolling back the uncommitted transactions...** option (described later), which is equivalent to restoring a backup with the `RECOVERY` option.</span></span>  
  
         <span data-ttu-id="9ce6f-213">このオプションをオンにすることは、 `KEEP_REPLICATION` ステートメントでオプションを使用することと同じです [!INCLUDE[tsql](../../includes/tsql-md.md)] `RESTORE` 。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-213">Checking this option is equivalent to using the `KEEP_REPLICATION` option in a [!INCLUDE[tsql](../../includes/tsql-md.md)]`RESTORE` statement.</span></span>  
  
    -   <span data-ttu-id="9ce6f-214">**[各バックアップを復元する前に確認する]**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-214">**Prompt before restoring each backup**</span></span>  
  
         <span data-ttu-id="9ce6f-215">このオプションは、各バックアップ セットの復元前 (最初のバックアップ セットでは、その後) に、復元シーケンスを続行するかどうかをたずねる **[復元の続行]** ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-215">Before restoring each backup set (after the first), this option brings up the **Continue with Restore** dialog box, which asks you to indicate whether you want to continue the restore sequence.</span></span> <span data-ttu-id="9ce6f-216">このダイアログには、次のメディア セットの名前 (使用可能な場合)、バックアップ セット名、およびバックアップ セットの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-216">This dialog displays the name of the next media set (if available), the backup set name, and backup set description.</span></span>  
  
         <span data-ttu-id="9ce6f-217">このオプションは、異なるメディア セットのテープを交換する必要がある場合に特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-217">This option is particularly useful when you must swap tapes for different media sets.</span></span> <span data-ttu-id="9ce6f-218">たとえば、サーバーにテープ デバイスが 1 台しかない場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-218">For example, you can use it when the server has only one tape device.</span></span> <span data-ttu-id="9ce6f-219">続行する準備ができたら **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-219">Wait until you are ready to proceed before clicking **OK**.</span></span>  
  
         <span data-ttu-id="9ce6f-220">**[いいえ]** をクリックすると、データベースは復元状態のままになります。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-220">Clicking **No** leaves the database in the restoring state.</span></span> <span data-ttu-id="9ce6f-221">最後の復元が完了した後、都合のよいときに復元シーケンスを継続できます。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-221">At your convenience, you can continue the restore sequence after the last restore that completed.</span></span> <span data-ttu-id="9ce6f-222">次のバックアップがデータまたは差分バックアップの場合は、 **[データベースの復元]** タスクを再度使用します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-222">If the next backup is a data or differential backup, use the **Restore Database** task again.</span></span> <span data-ttu-id="9ce6f-223">次のバックアップがログ バックアップの場合は、 **[トランザクション ログの復元]** タスクを使用します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-223">If the next backup is a log backup, use the **Restore Transaction Log** task.</span></span>  
  
    -   <span data-ttu-id="9ce6f-224">**[復元するデータベースへのアクセスを制限する (WITH RESTRICTED_USER)]**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-224">**Restrict access to the restored database (WITH RESTRICTED_USER)**</span></span>  
  
         <span data-ttu-id="9ce6f-225">復元するデータベースの使用を、 **db_owner**、 **dbcreator**、または **sysadmin**のメンバーだけに制限します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-225">Makes the restored database available only to the members of **db_owner**, **dbcreator**, or **sysadmin**.</span></span>  
  
         <span data-ttu-id="9ce6f-226">このオプションをオンにすることは、 `RESTRICTED_USER` ステートメントでオプションを使用することと同義です [!INCLUDE[tsql](../../includes/tsql-md.md)] `RESTORE` 。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-226">Checking this option is synonymous to using the `RESTRICTED_USER` option in a [!INCLUDE[tsql](../../includes/tsql-md.md)]`RESTORE` statement.</span></span>  
  
10. <span data-ttu-id="9ce6f-227">**[復旧状態]** オプションでは、復元操作後のデータベースの状態を指定します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-227">For the **Recovery state** options, specify the state of the database after the restore operation.</span></span>  
  
    -   <span data-ttu-id="9ce6f-228">**[コミットされていないトランザクションをロールバックして、データベースを使用可能な状態にする。別のトランザクション ログは復元できません。(RESTORE WITH RECOVERY)]**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-228">**Leave the database ready for use by rolling back uncommitted transactions. Additional transaction logs cannot be restored. (RESTORE WITH RECOVERY)**</span></span>  
  
         <span data-ttu-id="9ce6f-229">データベースを復旧します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-229">Recovers the database.</span></span> <span data-ttu-id="9ce6f-230">このオプションは、ステートメントのオプションに相当し `RECOVERY` [!INCLUDE[tsql](../../includes/tsql-md.md)] `RESTORE` ます。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-230">This option is equivalent to the `RECOVERY` option in a [!INCLUDE[tsql](../../includes/tsql-md.md)]`RESTORE` statement.</span></span>  
  
         <span data-ttu-id="9ce6f-231">このオプションは、復元するログ ファイルがない場合にのみ選択します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-231">Choose this option only if you have no log files you want to restore.</span></span>  
  
    -   <span data-ttu-id="9ce6f-232">**[データベースは操作不可状態のままで、コミットされていないトランザクションはロールバックしない。別のトランザクション ログは復元できます(RESTORE WITH NORECOVERY)]**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-232">**Leave the database non-operational, and do not roll back uncommitted transactions. Additional transaction logs can be restored. (RESTORE WITH NORECOVERY)**</span></span>  
  
         <span data-ttu-id="9ce6f-233">データベースを `RESTORING` 状態で未復旧のままにします。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-233">Leaves the database unrecovered, in the `RESTORING` state.</span></span> <span data-ttu-id="9ce6f-234">このオプションは、 `NORECOVERY` ステートメントでオプションを使用することと同じです [!INCLUDE[tsql](../../includes/tsql-md.md)] `RESTORE` 。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-234">This option is equivalent to using the `NORECOVERY` option in a [!INCLUDE[tsql](../../includes/tsql-md.md)]`RESTORE` statement.</span></span>  
  
         <span data-ttu-id="9ce6f-235">このオプションを選択した場合は、 **[レプリケーションの設定を保存する]** オプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-235">When you choose this option, the **Preserve replication settings** option is unavailable.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="9ce6f-236">ミラー データベースまたはセカンダリ データベースの場合は、常にこのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-236">For a mirror or secondary database, always select this option.</span></span>  
  
    -   <span data-ttu-id="9ce6f-237">**[データベースを読み取り専用モードにする。コミットされていないトランザクションは元に戻されますが、復旧結果を元に戻せるように元に戻す操作をファイルに保存します。(RESTORE WITH STANDBY)]**</span><span class="sxs-lookup"><span data-stu-id="9ce6f-237">**Leave the database in read-only mode. Undo uncommitted transactions, but save the undo actions in a file so that recovery effects can be reversed. (RESTORE WITH STANDBY)**</span></span>  
  
         <span data-ttu-id="9ce6f-238">データベースをスタンバイ状態のままにします。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-238">Leaves the database in a standby state.</span></span> <span data-ttu-id="9ce6f-239">このオプションは、 `STANDBY` ステートメントでオプションを使用することと同じです [!INCLUDE[tsql](../../includes/tsql-md.md)] `RESTORE` 。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-239">This option is equivalent to using the `STANDBY` option in a [!INCLUDE[tsql](../../includes/tsql-md.md)]`RESTORE` statement.</span></span>  
  
         <span data-ttu-id="9ce6f-240">このオプションを選択した場合は、スタンバイ ファイルを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-240">Choosing this option requires that you specify a standby file.</span></span>  
  
11. <span data-ttu-id="9ce6f-241">必要に応じて、 **[スタンバイ ファイル]** ボックスで、スタンバイ ファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-241">Optionally, specify a standby file name in the **Standby file** text box.</span></span> <span data-ttu-id="9ce6f-242">このオプションは、データベースを読み取り専用モードのままにする場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-242">This option is required if you leave the database in read-only mode.</span></span> <span data-ttu-id="9ce6f-243">スタンバイ ファイルは参照して指定するか、またはテキスト ボックスにパス名を入力します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-243">You can browse for the standby file or type its pathname in the text box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="9ce6f-244">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="9ce6f-244">Using Transact-SQL</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9ce6f-245">指定があいまいにならないよう、すべての RESTORE ステートメントにおいて WITH NORECOVERY または WITH RECOVERY を常に明示的に指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-245">We recommend that you always explicitly specify either WITH NORECOVERY or WITH RECOVERY in every RESTORE statement to eliminate ambiguity.</span></span> <span data-ttu-id="9ce6f-246">これは、スクリプトを作成するときに特に重要です。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-246">This is particularly important when writing scripts.</span></span>  
  
#### <a name="to-restore-a-transaction-log-backup"></a><span data-ttu-id="9ce6f-247">トランザクション ログ バックアップを復元するには</span><span class="sxs-lookup"><span data-stu-id="9ce6f-247">To restore a transaction log backup</span></span>  
  
1.  <span data-ttu-id="9ce6f-248">次の項目を指定して RESTORE LOG ステートメントを実行し、トランザクション ログ バックアップを適用します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-248">Execute the RESTORE LOG statement to apply the transaction log backup, specifying:</span></span>  
  
    -   <span data-ttu-id="9ce6f-249">トランザクション ログが適用されるデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-249">The name of the database to which the transaction log will be applied.</span></span>  
  
    -   <span data-ttu-id="9ce6f-250">適用するトランザクション ログ バックアップが格納されているバックアップ デバイス。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-250">The backup device where the transaction log backup will be restored from.</span></span>  
  
    -   <span data-ttu-id="9ce6f-251">NORECOVERY 句。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-251">The NORECOVERY clause.</span></span>  
  
     <span data-ttu-id="9ce6f-252">このステートメントの基本構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-252">The basic syntax for this statement is as follows:</span></span>  
  
     <span data-ttu-id="9ce6f-253">RESTORE LOG *database_name* FROM <backup_device> WITH NORECOVERY</span><span class="sxs-lookup"><span data-stu-id="9ce6f-253">RESTORE LOG *database_name* FROM <backup_device> WITH NORECOVERY.</span></span>  
  
     <span data-ttu-id="9ce6f-254">*database_name* は、データベース名です。<backup_device> は、復元するログ バックアップを保持するデバイスの名前です。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-254">Where *database_name* is the name of database and <backup_device>is the name of the device that contains the log backup being restored.</span></span>  
  
2.  <span data-ttu-id="9ce6f-255">適用する必要があるトランザクション ログ バックアップごとに、手順 1. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-255">Repeat step 1 for each transaction log backup you have to apply.</span></span>  
  
3.  <span data-ttu-id="9ce6f-256">復元シーケンスの最後のバックアップを復元した後、データベースを復旧するには、次のステートメントのいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-256">After restoring the last backup in your restore sequence, to recover the database use one of the following statements:</span></span>  
  
    -   <span data-ttu-id="9ce6f-257">最後の RESTORE LOG ステートメントの一部としてデータベースを復旧する。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-257">Recover the database as part of the last RESTORE LOG statement:</span></span>  
  
        ```  
        RESTORE LOG <database_name> FROM <backup_device> WITH RECOVERY;  
        GO  
        ```  
  
    -   <span data-ttu-id="9ce6f-258">個別の RESTORE DATABASE ステートメントを使用してデータベースの復旧を待機する。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-258">Wait to recover the database by using a separate RESTORE DATABASE statement:</span></span>  
  
        ```  
        RESTORE LOG <database_name> FROM <backup_device> WITH NORECOVERY;   
        RESTORE DATABASE <database_name> WITH RECOVERY;  
        GO  
        ```  
  
         <span data-ttu-id="9ce6f-259">データベースの復旧を待機すると、必要なログ バックアップがすべて復元されていることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-259">Waiting to recover the database gives you the opportunity to verify that you have restored all of the necessary log backups.</span></span> <span data-ttu-id="9ce6f-260">これは、特定の時点への復元を実行する際の操作として、多くの場合は推奨される方法です。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-260">This approach is often advisable when you are performing a point-in-time restore.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="9ce6f-261">ミラー データベースを作成している場合は、復旧ステップを省略します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-261">If you are creating a mirror database, omit the recovery step.</span></span> <span data-ttu-id="9ce6f-262">ミラー データベースは、RESTORING 状態のままにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-262">A mirror database must remain in the RESTORING state.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="9ce6f-263">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9ce6f-263">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="9ce6f-264">既定では、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースは単純復旧モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-264">By default, the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database uses the simple recovery model.</span></span> <span data-ttu-id="9ce6f-265">以下の例では、次に示すように、完全復旧モデルが使用されるようにデータベースを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-265">The following examples require modifying the database to use the full recovery model, as follows:</span></span>  
  
```sql  
ALTER DATABASE AdventureWorks2012 SET RECOVERY FULL;  
```  
  
#### <a name="a-applying-a-single-transaction-log-backup"></a><span data-ttu-id="9ce6f-266">A.</span><span class="sxs-lookup"><span data-stu-id="9ce6f-266">A.</span></span> <span data-ttu-id="9ce6f-267">1 つのトランザクション ログ バックアップの適用</span><span class="sxs-lookup"><span data-stu-id="9ce6f-267">Applying a single transaction log backup</span></span>  
 <span data-ttu-id="9ce6f-268">次の例では、まず [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] というバックアップ デバイスに存在するデータベースの完全バックアップを使用して `AdventureWorks2012_1`データベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-268">The following example starts by restoring the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database by using a full database backup that resides on a backup device named `AdventureWorks2012_1`.</span></span> <span data-ttu-id="9ce6f-269">次に、 `AdventureWorks2012_log`というバックアップ デバイスにある最初のトランザクション ログ バックアップを適用します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-269">The example then applies the first transaction log backup that resides on a backup device named `AdventureWorks2012_log`.</span></span> <span data-ttu-id="9ce6f-270">最後に、データベースを復旧します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-270">Finally, the example recovers the database.</span></span>  
  
```sql  
RESTORE DATABASE AdventureWorks2012  
   FROM AdventureWorks2012_1  
   WITH NORECOVERY;  
GO  
RESTORE LOG AdventureWorks2012  
   FROM AdventureWorks2012_log  
   WITH FILE = 1,  
   WITH NORECOVERY;  
GO  
RESTORE DATABASE AdventureWorks2012  
   WITH RECOVERY;  
GO  
```  
  
#### <a name="b-applying-multiple-transaction-log-backups"></a><span data-ttu-id="9ce6f-271">B.</span><span class="sxs-lookup"><span data-stu-id="9ce6f-271">B.</span></span> <span data-ttu-id="9ce6f-272">複数のトランザクション ログ バックアップの適用</span><span class="sxs-lookup"><span data-stu-id="9ce6f-272">Applying multiple transaction log backups</span></span>  
 <span data-ttu-id="9ce6f-273">次の例では、まず [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] というバックアップ デバイスに存在するデータベースの完全バックアップを使用して `AdventureWorks2012_1`データベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-273">The following example starts by restoring the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database by using a full database backup that resides on a backup device named `AdventureWorks2012_1`.</span></span> <span data-ttu-id="9ce6f-274">次に、 `AdventureWorks2012_log`という名前のバックアップ デバイスにある最初の 3 つのトランザクション ログ バックアップを、1 つずつ適用します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-274">The example then applies, one by one, the first three transaction log backups that reside on a backup device named `AdventureWorks2012_log`.</span></span> <span data-ttu-id="9ce6f-275">最後に、データベースを復旧します。</span><span class="sxs-lookup"><span data-stu-id="9ce6f-275">Finally, the example recovers the database.</span></span>  
  
```sql  
RESTORE DATABASE AdventureWorks2012  
   FROM AdventureWorks2012_1  
   WITH NORECOVERY;  
GO  
RESTORE LOG AdventureWorks2012  
   FROM AdventureWorks2012_log  
   WITH FILE = 1,  
   NORECOVERY;  
GO  
RESTORE LOG AdventureWorks2012  
   FROM AdventureWorks2012_log  
   WITH FILE = 2,  
   WITH NORECOVERY;  
GO  
RESTORE LOG AdventureWorks2012  
   FROM AdventureWorks2012_log  
   WITH FILE = 3,  
   WITH NORECOVERY;  
GO  
RESTORE DATABASE AdventureWorks2012  
   WITH RECOVERY;  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="9ce6f-276">関連タスク</span><span class="sxs-lookup"><span data-stu-id="9ce6f-276">Related Tasks</span></span>  
  
-   [<span data-ttu-id="9ce6f-277">トランザクション ログのバックアップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9ce6f-277">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   [<span data-ttu-id="9ce6f-278">データベースバックアップを復元する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="9ce6f-278">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="9ce6f-279">完全復旧モデルで障害発生時点までデータベースを復元する &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9ce6f-279">Restore a Database to the Point of Failure Under the Full Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-database-to-point-of-failure-full-recovery.md)  
  
-   [<span data-ttu-id="9ce6f-280">SQL Server データベースを特定の時点に復元する &#40;完全復旧モデル&#41;</span><span class="sxs-lookup"><span data-stu-id="9ce6f-280">Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;</span></span>](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
-   [<span data-ttu-id="9ce6f-281">マークされたトランザクションへのデータベースの復元 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="9ce6f-281">Restore a Database to a Marked Transaction &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)  
  
## <a name="see-also"></a><span data-ttu-id="9ce6f-282">参照</span><span class="sxs-lookup"><span data-stu-id="9ce6f-282">See Also</span></span>  
 <span data-ttu-id="9ce6f-283">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9ce6f-283">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="9ce6f-284">トランザクション ログ バックアップの適用 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9ce6f-284">Apply Transaction Log Backups &#40;SQL Server&#41;</span></span>](apply-transaction-log-backups-sql-server.md)  
  
  
