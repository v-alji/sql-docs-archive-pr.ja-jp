---
title: データベース ミラーリングの履歴 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dbmmonitor.databasemirroringhistory.f1
ms.assetid: 1d6e4b10-4a23-47d7-9918-c417992f09d3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3e32ad9bfdce15413d89fbd5ba3d79a5ef14f7a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643473"
---
# <a name="database-mirroring-history"></a><span data-ttu-id="f4c25-102">[データベース ミラーリングの履歴]</span><span class="sxs-lookup"><span data-stu-id="f4c25-102">Database Mirroring History</span></span>
  <span data-ttu-id="f4c25-103">このダイアログ ボックスは、指定したサーバー インスタンスでミラー化されたデータベースについて、ミラーリング状態の履歴を表示するために使用します。</span><span class="sxs-lookup"><span data-stu-id="f4c25-103">Use this dialog box to view the history of mirroring status for a mirrored database on a specified server instance.</span></span>  
  
 <span data-ttu-id="f4c25-104">**SQL Server Management Studio を使用してデータベース ミラーリングを監視するには**</span><span class="sxs-lookup"><span data-stu-id="f4c25-104">**To use SQL Server Management Studio to monitor database mirroring**</span></span>  
  
-   [<span data-ttu-id="f4c25-105">データベース ミラーリング モニターの起動 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="f4c25-105">Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;</span></span>](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
## <a name="options"></a><span data-ttu-id="f4c25-106">Options</span><span class="sxs-lookup"><span data-stu-id="f4c25-106">Options</span></span>  
 <span data-ttu-id="f4c25-107">**サーバー インスタンス**</span><span class="sxs-lookup"><span data-stu-id="f4c25-107">**Server instance**</span></span>  
 <span data-ttu-id="f4c25-108">履歴レポートの対象となるサーバー インスタンスの名前です。</span><span class="sxs-lookup"><span data-stu-id="f4c25-108">Name of the server instance from which the history is being reported.</span></span>  
  
 <span data-ttu-id="f4c25-109">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="f4c25-109">**Database**</span></span>  
 <span data-ttu-id="f4c25-110">履歴レポートの対象となるデータベースの名前です。</span><span class="sxs-lookup"><span data-stu-id="f4c25-110">Name of the database whose history is being reported.</span></span>  
  
 <span data-ttu-id="f4c25-111">**[一覧のフィルター]**</span><span class="sxs-lookup"><span data-stu-id="f4c25-111">**Filter list by**</span></span>  
 <span data-ttu-id="f4c25-112">フィルター値が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="f4c25-112">Lists filter values.</span></span> <span data-ttu-id="f4c25-113">新しい値を選択すると、グリッドが自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="f4c25-113">Choosing a new value refreshes the grid automatically.</span></span>  
  
 <span data-ttu-id="f4c25-114">使用できるフィルター値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f4c25-114">The possible filter values are:</span></span>  
  
-   <span data-ttu-id="f4c25-115">[過去 2 時間]</span><span class="sxs-lookup"><span data-stu-id="f4c25-115">Last two hours</span></span>  
  
-   <span data-ttu-id="f4c25-116">[過去 4 時間]</span><span class="sxs-lookup"><span data-stu-id="f4c25-116">Last four hours</span></span>  
  
-   <span data-ttu-id="f4c25-117">[過去 8 時間]</span><span class="sxs-lookup"><span data-stu-id="f4c25-117">Last eight hours</span></span>  
  
-   <span data-ttu-id="f4c25-118">[過去 1 日間]</span><span class="sxs-lookup"><span data-stu-id="f4c25-118">Last day</span></span>  
  
-   <span data-ttu-id="f4c25-119">[過去 2 日間]</span><span class="sxs-lookup"><span data-stu-id="f4c25-119">Last two days</span></span>  
  
-   <span data-ttu-id="f4c25-120">[最新 100 レコード]</span><span class="sxs-lookup"><span data-stu-id="f4c25-120">Last 100 records</span></span>  
  
-   <span data-ttu-id="f4c25-121">[最新 500 レコード]</span><span class="sxs-lookup"><span data-stu-id="f4c25-121">Last 500 records</span></span>  
  
-   <span data-ttu-id="f4c25-122">[最新 1000 レコード]</span><span class="sxs-lookup"><span data-stu-id="f4c25-122">Last 1000 records</span></span>  
  
-   <span data-ttu-id="f4c25-123">[すべてのレコード]</span><span class="sxs-lookup"><span data-stu-id="f4c25-123">All records</span></span>  
  
 <span data-ttu-id="f4c25-124">**[更新]**</span><span class="sxs-lookup"><span data-stu-id="f4c25-124">**Refresh**</span></span>  
 <span data-ttu-id="f4c25-125">履歴一覧を更新する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="f4c25-125">Click to refresh the history list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f4c25-126">このダイアログ ボックスに表示される履歴一覧は、自動的には更新されません。</span><span class="sxs-lookup"><span data-stu-id="f4c25-126">This dialog box does not automatically refresh the history list.</span></span> <span data-ttu-id="f4c25-127">一覧を更新するには、 **[最新の情報に更新]** をクリックするか、別のフィルター オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="f4c25-127">To refresh the list, either click **Refresh** or choose another filter option.</span></span> <span data-ttu-id="f4c25-128">ミラーリング履歴を更新できるのは、 **sysadmin** 固定サーバー ロールのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="f4c25-128">Only members of the **sysadmin** fixed server role can update the mirroring history.</span></span>  
  
 <span data-ttu-id="f4c25-129">**HISTORY**</span><span class="sxs-lookup"><span data-stu-id="f4c25-129">**History**</span></span>  
 <span data-ttu-id="f4c25-130">履歴一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="f4c25-130">Displays the history list.</span></span> <span data-ttu-id="f4c25-131">列のヘッダーをクリックすると、その列のデータを使用してグリッドが並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="f4c25-131">Clicking on a column header sorts the grid by that column.</span></span> <span data-ttu-id="f4c25-132">一覧には次の列があります。</span><span class="sxs-lookup"><span data-stu-id="f4c25-132">The list contains the following columns:</span></span>  
  
|<span data-ttu-id="f4c25-133">列名</span><span class="sxs-lookup"><span data-stu-id="f4c25-133">Column name</span></span>|<span data-ttu-id="f4c25-134">説明</span><span class="sxs-lookup"><span data-stu-id="f4c25-134">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="f4c25-135">**[記録された日時]**</span><span class="sxs-lookup"><span data-stu-id="f4c25-135">**Time Recorded**</span></span>|<span data-ttu-id="f4c25-136">履歴行のタイムスタンプです。</span><span class="sxs-lookup"><span data-stu-id="f4c25-136">Timestamp of the history row.</span></span>|  
|<span data-ttu-id="f4c25-137">**ロール**</span><span class="sxs-lookup"><span data-stu-id="f4c25-137">**Role**</span></span>|<span data-ttu-id="f4c25-138">このデータベースに対するサーバー インスタンスの現在のミラーリング ロールです。[プリンシパル] または [ミラー] のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="f4c25-138">Current mirroring role of the server instance for this database, either Principal or Mirror.</span></span>|  
|<span data-ttu-id="f4c25-139">**[ミラー化の状態]**</span><span class="sxs-lookup"><span data-stu-id="f4c25-139">**Mirroring State**</span></span>|<span data-ttu-id="f4c25-140">データベースの状態。</span><span class="sxs-lookup"><span data-stu-id="f4c25-140">State of the database:</span></span><br /><br /> <span data-ttu-id="f4c25-141">[Disconnected]\(切断済み\)</span><span class="sxs-lookup"><span data-stu-id="f4c25-141">Disconnected</span></span><br /><br /> <span data-ttu-id="f4c25-142">[フェールオーバーを保留しています]</span><span class="sxs-lookup"><span data-stu-id="f4c25-142">Pending Failover</span></span><br /><br /> <span data-ttu-id="f4c25-143">Suspended</span><span class="sxs-lookup"><span data-stu-id="f4c25-143">Suspended</span></span><br /><br /> <span data-ttu-id="f4c25-144">同期済み</span><span class="sxs-lookup"><span data-stu-id="f4c25-144">Synchronized</span></span><br /><br /> <span data-ttu-id="f4c25-145">[同期中]</span><span class="sxs-lookup"><span data-stu-id="f4c25-145">Synchronizing</span></span><br /><br /> <span data-ttu-id="f4c25-146">Unknown</span><span class="sxs-lookup"><span data-stu-id="f4c25-146">Unknown</span></span>|  
|<span data-ttu-id="f4c25-147">**[ミラーリング監視接続]**</span><span class="sxs-lookup"><span data-stu-id="f4c25-147">**Witness Connection**</span></span>|<span data-ttu-id="f4c25-148">データベースのミラーリング セッションにおけるミラーリング監視接続の状態です。[接続済み] または [接続解除] のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="f4c25-148">State of the witness connection in the mirroring session of the database, either Connected or Disconnected.</span></span> <span data-ttu-id="f4c25-149">ミラーリング監視が存在しない場合、値は NULL になります。</span><span class="sxs-lookup"><span data-stu-id="f4c25-149">If there is no witness, the value is NULL.</span></span>|  
|<span data-ttu-id="f4c25-150">**[未送信のログ]**</span><span class="sxs-lookup"><span data-stu-id="f4c25-150">**Unsent Log**</span></span>|<span data-ttu-id="f4c25-151">プリンシパル サーバー インスタンスの送信キューにある未送信ログのサイズをキロバイト (KB) 単位で表します。</span><span class="sxs-lookup"><span data-stu-id="f4c25-151">Size, in kilobytes (KB), of the unsent log in the send queue on the principal server instance.</span></span>|  
|<span data-ttu-id="f4c25-152">**[送信する日時]**</span><span class="sxs-lookup"><span data-stu-id="f4c25-152">**Time to Send**</span></span>|<span data-ttu-id="f4c25-153">プリンシパル サーバー インスタンスが、送信キューに現在存在するログをミラー サーバー インスタンスに送信するために必要な、おおよその時間です。その際の速度は、 *送信比率*で表されます。</span><span class="sxs-lookup"><span data-stu-id="f4c25-153">Approximate amount of time the principal server instance will require to send the log that is currently in the send queue to the mirror server instance (the *send rate*).</span></span> <span data-ttu-id="f4c25-154">入力トランザクションの送信比率は著しく変化するため、ログの送信にかかる時間は、推定値になります。</span><span class="sxs-lookup"><span data-stu-id="f4c25-154">Because the rate of incoming transactions can vary significantly, the time to send log is an estimate.</span></span> <span data-ttu-id="f4c25-155">ただし、送信比率は、手動フェールオーバーに必要な時間を推定する際の目安として使用できます。</span><span class="sxs-lookup"><span data-stu-id="f4c25-155">However, the send rate can be useful for roughly estimating the time required for a manual failover.</span></span>|  
|<span data-ttu-id="f4c25-156">**Send Rate**</span><span class="sxs-lookup"><span data-stu-id="f4c25-156">**Send Rate**</span></span>|<span data-ttu-id="f4c25-157">トランザクションがミラー サーバー インスタンスに送信される速度 (KB/秒) です。</span><span class="sxs-lookup"><span data-stu-id="f4c25-157">Rate at which transactions are being sent to the mirror server instance, in KB per second.</span></span>|  
|<span data-ttu-id="f4c25-158">**[新しいトランザクションの比率]**</span><span class="sxs-lookup"><span data-stu-id="f4c25-158">**New Transaction Rate**</span></span>|<span data-ttu-id="f4c25-159">入力トランザクションが、プリンシパルのログに記録される速度 (KB/秒) です。</span><span class="sxs-lookup"><span data-stu-id="f4c25-159">Rate at which incoming transactions are being entered into the principal's log, in KB per second.</span></span> <span data-ttu-id="f4c25-160">この値と **[送信する日時]** の値を比較することによって、ミラーリングの状況 (遅延している、順調に進行している、遅延が解消されつつあるなど) を確認できます。</span><span class="sxs-lookup"><span data-stu-id="f4c25-160">To determine whether mirroring is falling behind, staying up, or catching up, compare this value to the **Time to Send** value.</span></span>|  
|<span data-ttu-id="f4c25-161">**[最も古い未送信のトランザクション]**</span><span class="sxs-lookup"><span data-stu-id="f4c25-161">**Oldest Unsent Transaction**</span></span>|<span data-ttu-id="f4c25-162">送信キュー内で最も古い未送信トランザクションの経過期間。</span><span class="sxs-lookup"><span data-stu-id="f4c25-162">Age of the oldest unsent transaction in the send queue.</span></span> <span data-ttu-id="f4c25-163">トランザクションの経過期間は、トランザクションがミラー サーバー インスタンスに送信されないまま経過した時間を分単位で示します。</span><span class="sxs-lookup"><span data-stu-id="f4c25-163">The age of this transaction indicates how many minutes of transactions have not yet been sent to the mirror server instance.</span></span> <span data-ttu-id="f4c25-164">この値は、データ損失の可能性を時間の観点から測定するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f4c25-164">This value helps measure the potential for data loss in terms of time.</span></span>|  
|<span data-ttu-id="f4c25-165">**[復元されていないログ]**</span><span class="sxs-lookup"><span data-stu-id="f4c25-165">**Unrestored Log**</span></span>|<span data-ttu-id="f4c25-166">再実行キューで待機しているログのサイズ (KB) です。</span><span class="sxs-lookup"><span data-stu-id="f4c25-166">The amount of log waiting in the redo queue, in KB.</span></span>|  
|<span data-ttu-id="f4c25-167">**[復元する日時]**</span><span class="sxs-lookup"><span data-stu-id="f4c25-167">**Time to Restore**</span></span>|<span data-ttu-id="f4c25-168">現在再実行キューに格納されているログをミラー データベースに適用するために必要な時間の概算値 (分)。</span><span class="sxs-lookup"><span data-stu-id="f4c25-168">Approximate number of minutes required for the log currently in the redo queue to be applied to the mirror database.</span></span>|  
|<span data-ttu-id="f4c25-169">**[復元比率]**</span><span class="sxs-lookup"><span data-stu-id="f4c25-169">**Restore Rate**</span></span>|<span data-ttu-id="f4c25-170">トランザクションがミラー データベースに復元される速度 (KB/秒) です。</span><span class="sxs-lookup"><span data-stu-id="f4c25-170">Rate at which transactions are being restored into the mirror database, in KB per second.</span></span>|  
|<span data-ttu-id="f4c25-171">**[ミラー コミットのオーバーヘッド]**</span><span class="sxs-lookup"><span data-stu-id="f4c25-171">**Mirror Commit Overhead**</span></span>|<span data-ttu-id="f4c25-172">トランザクションあたりの平均遅延時間をミリ秒で表します (同期モードのみ)。</span><span class="sxs-lookup"><span data-stu-id="f4c25-172">Average delay per transaction in milliseconds (only in synchronous modes).</span></span> <span data-ttu-id="f4c25-173">この遅延時間は、ミラー サーバー インスタンスによってトランザクションのログ レコードが再実行キューに書き込まれるのをプリンシパル サーバー インスタンスが待機している間、発生したオーバーヘッドの量になります。</span><span class="sxs-lookup"><span data-stu-id="f4c25-173">This delay is the amount of overhead incurred while the principal server instance waits for the mirror server instance to write the transaction's log record into the redo queue.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f4c25-174">参照</span><span class="sxs-lookup"><span data-stu-id="f4c25-174">See Also</span></span>  
 <span data-ttu-id="f4c25-175">[データベース ミラーリング モニターの起動 &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="f4c25-175">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="f4c25-176">[データベース ミラーリングの監視 &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f4c25-176">[Monitoring Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="f4c25-177">データベース ミラーリング セキュリティ構成ウィザードの起動 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="f4c25-177">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
  
