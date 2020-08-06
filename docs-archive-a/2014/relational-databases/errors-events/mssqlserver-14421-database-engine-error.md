---
title: MSSQLSERVER_14421 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 14421 (Database Engine error)
ms.assetid: 03e76d4a-d463-4673-8843-08e4ecaefe27
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d6bc793911797c334d87238ec46531f7afbf63ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643918"
---
# <a name="mssqlserver_14421"></a><span data-ttu-id="84ed2-102">MSSQLSERVER_14421</span><span class="sxs-lookup"><span data-stu-id="84ed2-102">MSSQLSERVER_14421</span></span>
    
## <a name="details"></a><span data-ttu-id="84ed2-103">詳細</span><span class="sxs-lookup"><span data-stu-id="84ed2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="84ed2-104">製品名</span><span class="sxs-lookup"><span data-stu-id="84ed2-104">Product Name</span></span>|<span data-ttu-id="84ed2-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="84ed2-105">SQL Server</span></span>|  
|<span data-ttu-id="84ed2-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="84ed2-106">Event ID</span></span>|<span data-ttu-id="84ed2-107">14421</span><span class="sxs-lookup"><span data-stu-id="84ed2-107">14421</span></span>|  
|<span data-ttu-id="84ed2-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="84ed2-108">Event Source</span></span>|<span data-ttu-id="84ed2-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="84ed2-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="84ed2-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="84ed2-110">Component</span></span>|<span data-ttu-id="84ed2-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="84ed2-111">SQLEngine</span></span>|  
|<span data-ttu-id="84ed2-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="84ed2-112">Symbolic Name</span></span>|<span data-ttu-id="84ed2-113">SQLErrorNum14421</span><span class="sxs-lookup"><span data-stu-id="84ed2-113">SQLErrorNum14421</span></span>|  
|<span data-ttu-id="84ed2-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="84ed2-114">Message Text</span></span>|<span data-ttu-id="84ed2-115">ログ配布のセカンダリ データベース %s.%s は復元のしきい値が %d 分間ですが、同期されていません。復元は %d 分間実行されていません。</span><span class="sxs-lookup"><span data-stu-id="84ed2-115">The log shipping secondary database %s.%s has restore threshold of %d minutes and is out of sync. No restore was performed for %d minutes.</span></span> <span data-ttu-id="84ed2-116">復元される待機時間は %d 分間です。</span><span class="sxs-lookup"><span data-stu-id="84ed2-116">Restored latency is %d minutes.</span></span> <span data-ttu-id="84ed2-117">エージェント ログおよびログ配布モニターの情報を調べてください。</span><span class="sxs-lookup"><span data-stu-id="84ed2-117">Check agent log and logshipping monitor information.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="84ed2-118">説明</span><span class="sxs-lookup"><span data-stu-id="84ed2-118">Explanation</span></span>  
 <span data-ttu-id="84ed2-119">このメッセージは、復元のしきい値を超えてもログ配布が同期されていないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="84ed2-119">This message indicates that log shipping is out of synchronization beyond the restore threshold.</span></span> <span data-ttu-id="84ed2-120">復元のしきい値は、復元操作が完了するまでの許容時間 (分数) です。この時間が経過すると警告メッセージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="84ed2-120">The restore threshold is the number of minutes that can elapse between restore operations before a message is generated.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="84ed2-121">考えられる原因</span><span class="sxs-lookup"><span data-stu-id="84ed2-121">Possible Causes</span></span>  
 <span data-ttu-id="84ed2-122">このメッセージは、必ずしもログ配布に関する問題を示しません。</span><span class="sxs-lookup"><span data-stu-id="84ed2-122">This message does not necessarily indicate a problem with log shipping.</span></span> <span data-ttu-id="84ed2-123">このメッセージは次の問題のいずれかを示す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="84ed2-123">Instead, this message might indicate one of the following problems:</span></span>  
  
-   <span data-ttu-id="84ed2-124">復元ジョブが実行されていない。</span><span class="sxs-lookup"><span data-stu-id="84ed2-124">The restore job is not running.</span></span>  
  
     <span data-ttu-id="84ed2-125">原因として、セカンダリ サーバー インスタンスで SQL Server エージェント サービスが実行されていないか、復元ジョブが無効になっているか、または復元ジョブのスケジュールが変更されていることが考えられます。</span><span class="sxs-lookup"><span data-stu-id="84ed2-125">Possible causes of the job not running include the following: the SQL Server Agent service on the secondary server instance is not running, the job is disabled, or the schedule of the job has been changed.</span></span>  
  
-   <span data-ttu-id="84ed2-126">復元ジョブが失敗している。</span><span class="sxs-lookup"><span data-stu-id="84ed2-126">The restore job is failing.</span></span>  
  
     <span data-ttu-id="84ed2-127">原因として、復元フォルダーのパスが有効でないか、ディスクがいっぱいになっているか、またはその他の理由で RESTORE ステートメントが失敗したことが考えられます。</span><span class="sxs-lookup"><span data-stu-id="84ed2-127">Possible causes of the job failing include the following: the restore folder path is not valid, the disk is full, or any other reason that the RESTORE statement could fail.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="84ed2-128">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="84ed2-128">User Action</span></span>  
 <span data-ttu-id="84ed2-129">このメッセージが表示された場合は、次の方法で対処してください。</span><span class="sxs-lookup"><span data-stu-id="84ed2-129">To troubleshoot this message:</span></span>  
  
-   <span data-ttu-id="84ed2-130">セカンダリ サーバー インスタンスで SQL Server エージェント サービスが実行されていることを確認します。また、セカンダリ データベースの復元ジョブが有効になっており、適切な頻度で実行するようにスケジュール設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="84ed2-130">Make sure that the SQL Server Agent service is running for the secondary server instance and that the restore job for this secondary database is enabled and is scheduled to run at the appropriate frequency.</span></span>  
  
-   <span data-ttu-id="84ed2-131">セカンダリ サーバーの復元ジョブが失敗している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="84ed2-131">The restore job on the secondary server might be failing.</span></span> <span data-ttu-id="84ed2-132">この場合は、復元ジョブのジョブ履歴を参照して原因を探してください。</span><span class="sxs-lookup"><span data-stu-id="84ed2-132">In this case, check the job history for the restore job to look for the cause.</span></span>  
  
-   <span data-ttu-id="84ed2-133">セカンダリ サーバー インスタンスでログ配布の復元ジョブを実行する際、監視サーバー インスタンスに接続して **log_shipping_monitor_secondary** テーブルを更新できない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="84ed2-133">The log shipping restore job, which runs on the secondary server instance, might not be able to connect to the monitor server instance to update the **log_shipping_monitor_secondary** table.</span></span> <span data-ttu-id="84ed2-134">その場合、監視サーバー インスタンスとセカンダリ サーバー インスタンス間での認証に問題があると思われます。</span><span class="sxs-lookup"><span data-stu-id="84ed2-134">This might be caused by an authentication problem between the monitor server instance and the secondary server instance.</span></span>  
  
-   <span data-ttu-id="84ed2-135">バックアップの警告のしきい値に、正しくない値が設定されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="84ed2-135">The backup alert threshold might have an incorrect value.</span></span> <span data-ttu-id="84ed2-136">この値は、復元ジョブの少なくとも 3 倍の頻度に設定するのが理想的です。</span><span class="sxs-lookup"><span data-stu-id="84ed2-136">Ideally, this value is set to at least three times the frequency of the restore job.</span></span> <span data-ttu-id="84ed2-137">ログ配布を構成して有効にした後で、復元ジョブの頻度を変更した場合は、それに合わせて復元の警告しきい値も更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="84ed2-137">If you change the frequency of the restore job after log shipping is configured and functional, you must update the value of the backup alert threshold accordingly.</span></span>  
  
-   <span data-ttu-id="84ed2-138">監視サーバー インスタンスがオフラインになり、その後オンラインに戻ったとき、警告メッセージ ジョブが実行される前に、**log_shipping_monitor_secondary** テーブルが現在の値に更新されません。</span><span class="sxs-lookup"><span data-stu-id="84ed2-138">When the monitor server instance goes offline and then comes back online, the **log_shipping_monitor_secondary** table is not updated with the current values before the alert message job runs.</span></span> <span data-ttu-id="84ed2-139">復元ジョブに成功し、"セカンダリ データベースに適用できるログ バックアップ ファイルが見つかりませんでした。" というメッセージが表示された場合に、エラー 14421 が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="84ed2-139">Error 14421 can be raised when a restore job succeeds with, "Could not find a log backup file that could be applied to secondary database."</span></span> <span data-ttu-id="84ed2-140">このエラーが発生すると、復元時間は更新されません。</span><span class="sxs-lookup"><span data-stu-id="84ed2-140">When this occurs, the restore time is not updated.</span></span> <span data-ttu-id="84ed2-141">この場合のエラーの原因は、コピー ジョブに問題があります。</span><span class="sxs-lookup"><span data-stu-id="84ed2-141">The cause of the error in this case might be an issue with the copy job.</span></span>  
  
     <span data-ttu-id="84ed2-142">監視テーブルを更新して、セカンダリ データベースの最新データを反映させるには、セカンダリ サーバー インスタンスで **sp_refresh_log_shipping_monitor** を実行します。</span><span class="sxs-lookup"><span data-stu-id="84ed2-142">To update the monitor tables with the latest data for the secondary database, run **sp_refresh_log_shipping_monitor** on the secondary server instance.</span></span>  
  
-   <span data-ttu-id="84ed2-143">セカンダリ サーバー インスタンスまたは監視サーバー インスタンスで、日付または時刻が正しく設定されていません。</span><span class="sxs-lookup"><span data-stu-id="84ed2-143">On the secondary or monitor server instance, the date or time is incorrect.</span></span> <span data-ttu-id="84ed2-144">これが原因で、警告メッセージが生成される場合もあります。</span><span class="sxs-lookup"><span data-stu-id="84ed2-144">This may also generate alert messages.</span></span> <span data-ttu-id="84ed2-145">これらいずれかのサーバーで、システムの日付または時刻が変更された可能性があります。</span><span class="sxs-lookup"><span data-stu-id="84ed2-145">Possibly the system date or time was modified on the one of them.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="84ed2-146">2 つのサーバー インスタンスでタイム ゾーンが異なることによって、問題が発生することはありません。</span><span class="sxs-lookup"><span data-stu-id="84ed2-146">Different time zones for the two server instances should not cause a problem.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84ed2-147">参照</span><span class="sxs-lookup"><span data-stu-id="84ed2-147">See Also</span></span>  
 <span data-ttu-id="84ed2-148">[log_shipping_monitor_secondary &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/log-shipping-monitor-secondary-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="84ed2-148">[log_shipping_monitor_secondary &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/log-shipping-monitor-secondary-transact-sql) </span></span>  
 <span data-ttu-id="84ed2-149">[ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="84ed2-149">[About Log Shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md) </span></span>  
 <span data-ttu-id="84ed2-150">[sp_help_log_shipping_monitor_secondary &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-secondary-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="84ed2-150">[sp_help_log_shipping_monitor_secondary &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-secondary-transact-sql) </span></span>  
 <span data-ttu-id="84ed2-151">[sp_refresh_log_shipping_monitor &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="84ed2-151">[sp_refresh_log_shipping_monitor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql) </span></span>  
 [<span data-ttu-id="84ed2-152">ログ配布について &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="84ed2-152">About Log Shipping &#40;SQL Server&#41;</span></span>](../../database-engine/log-shipping/about-log-shipping-sql-server.md)  
  
  
