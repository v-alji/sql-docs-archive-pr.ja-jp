---
title: MSSQLSERVER_14420 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 14420 (Database Engine error)
ms.assetid: 4a1d72b1-ab1b-4119-a11b-a8a05c6fdb45
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7a17ab1e2281530b06c9ad27ac2a31672de0681e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634554"
---
# <a name="mssqlserver_14420"></a><span data-ttu-id="587fc-102">MSSQLSERVER_14420</span><span class="sxs-lookup"><span data-stu-id="587fc-102">MSSQLSERVER_14420</span></span>
    
## <a name="details"></a><span data-ttu-id="587fc-103">詳細</span><span class="sxs-lookup"><span data-stu-id="587fc-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="587fc-104">製品名</span><span class="sxs-lookup"><span data-stu-id="587fc-104">Product Name</span></span>|<span data-ttu-id="587fc-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="587fc-105">SQL Server</span></span>|  
|<span data-ttu-id="587fc-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="587fc-106">Event ID</span></span>|<span data-ttu-id="587fc-107">14420</span><span class="sxs-lookup"><span data-stu-id="587fc-107">14420</span></span>|  
|<span data-ttu-id="587fc-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="587fc-108">Event Source</span></span>|<span data-ttu-id="587fc-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="587fc-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="587fc-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="587fc-110">Component</span></span>|<span data-ttu-id="587fc-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="587fc-111">SQLEngine</span></span>|  
|<span data-ttu-id="587fc-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="587fc-112">Symbolic Name</span></span>|<span data-ttu-id="587fc-113">SQLErrorNum14420</span><span class="sxs-lookup"><span data-stu-id="587fc-113">SQLErrorNum14420</span></span>|  
|<span data-ttu-id="587fc-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="587fc-114">Message Text</span></span>|<span data-ttu-id="587fc-115">ログ配布プライマリ データベース %s.%s では、バックアップのしきい値が %d 分間ですが、%d 分間バックアップ ログ操作が実行されていません。</span><span class="sxs-lookup"><span data-stu-id="587fc-115">The log shipping primary database %s.%s has backup threshold of %d minutes and has not performed a backup log operation for %d minutes.</span></span> <span data-ttu-id="587fc-116">エージェント ログおよびログ配布モニターの情報を調べてください。</span><span class="sxs-lookup"><span data-stu-id="587fc-116">Check agent log and logshipping monitor information.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="587fc-117">説明</span><span class="sxs-lookup"><span data-stu-id="587fc-117">Explanation</span></span>  
 <span data-ttu-id="587fc-118">バックアップのしきい値を超えましたが、ログ配布が同期されていません。</span><span class="sxs-lookup"><span data-stu-id="587fc-118">Log shipping is out of synchronization beyond the backup threshold.</span></span> <span data-ttu-id="587fc-119">バックアップのしきい値は、ログ配布のバックアップが完了するまでの許容時間 (分数) です。この時間が経過すると警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="587fc-119">The backup threshold is the number of minutes that are allowed to elapse between log-shipping backup jobs before an alert is generated.</span></span> <span data-ttu-id="587fc-120">このメッセージは、必ずしもログ配布に関する問題を示しません。</span><span class="sxs-lookup"><span data-stu-id="587fc-120">This message does not necessarily indicate a problem with log shipping.</span></span> <span data-ttu-id="587fc-121">このメッセージは次の問題のいずれかを示す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="587fc-121">Instead, this message might indicate one of the following problems:</span></span>  
  
-   <span data-ttu-id="587fc-122">バックアップ ジョブが実行されていない。</span><span class="sxs-lookup"><span data-stu-id="587fc-122">The backup job is not running.</span></span> <span data-ttu-id="587fc-123">原因として、プライマリ サーバー インスタンスで SQL Server エージェント サービスが実行されていないか、バックアップ ジョブが無効になっているか、またはバックアップ ジョブのスケジュールが変更されていることが考えられます。</span><span class="sxs-lookup"><span data-stu-id="587fc-123">Possible causes for this include the following: the SQL Server Agent service on the primary server instance is not running, the job is disabled, or the job's schedule has been changed.</span></span>  
  
-   <span data-ttu-id="587fc-124">バックアップ ジョブが失敗している。</span><span class="sxs-lookup"><span data-stu-id="587fc-124">The backup job is failing.</span></span> <span data-ttu-id="587fc-125">原因として、バックアップ フォルダーのパスが有効でないか、ディスクがいっぱいになっているか、またはその他の理由で BACKUP ステートメントが失敗したことが考えられます。</span><span class="sxs-lookup"><span data-stu-id="587fc-125">Possible causes for this include the following: the backup folder path is not valid, the disk is full, or any other reason that the BACKUP statement could fail.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="587fc-126">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="587fc-126">User Action</span></span>  
 <span data-ttu-id="587fc-127">このメッセージが表示された場合は、次の方法で対処してください。</span><span class="sxs-lookup"><span data-stu-id="587fc-127">To troubleshoot this message:</span></span>  
  
-   <span data-ttu-id="587fc-128">プライマリ サーバー インスタンスで SQL Server エージェント サービスが実行されていることを確認します。また、プライマリ データベースのバックアップ ジョブが有効になっており、適切な頻度で実行するようにスケジュール設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="587fc-128">Make sure that the SQL Server Agent service is running for the primary server instance and that the backup job for this primary database is enabled and is scheduled to run at the appropriate frequency.</span></span>  
  
-   <span data-ttu-id="587fc-129">プライマリ サーバーのバックアップ ジョブが失敗している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="587fc-129">The backup job on the primary server might be failing.</span></span> <span data-ttu-id="587fc-130">この場合は、バックアップ ジョブのジョブ履歴を参照して原因を探してください。</span><span class="sxs-lookup"><span data-stu-id="587fc-130">In this case, examine the job history for the backup job to look for the cause.</span></span>  
  
-   <span data-ttu-id="587fc-131">プライマリ サーバー インスタンスでログ配布のバックアップ ジョブを実行する際、監視サーバー インスタンスに接続して **log_shipping_monitor_primary** テーブルを更新できない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="587fc-131">The log shipping backup job, which runs on the primary server instance, might not be able to connect to the monitor server instance to update the **log_shipping_monitor_primary** table.</span></span> <span data-ttu-id="587fc-132">その場合、監視サーバー インスタンスとプライマリ サーバー インスタンス間での認証に問題があると思われます。</span><span class="sxs-lookup"><span data-stu-id="587fc-132">This could be caused by an authentication problem between the monitor server instance and the primary server instance.</span></span>  
  
-   <span data-ttu-id="587fc-133">バックアップの警告のしきい値に、正しくない値が設定されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="587fc-133">The backup alert threshold might have an incorrect value.</span></span> <span data-ttu-id="587fc-134">この値は、バックアップ ジョブの少なくとも 3 倍の頻度に設定するのが理想的です。</span><span class="sxs-lookup"><span data-stu-id="587fc-134">Ideally, this value is set to at least three times the frequency of the backup job.</span></span> <span data-ttu-id="587fc-135">ログ配布を構成し、有効にした後で、バックアップ ジョブの頻度を変更した場合は、それに合わせてバックアップの警告しきい値も更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="587fc-135">If you change the frequency of the backup job after log shipping is configured and functional, you must update the value of the backup alert threshold accordingly.</span></span>  
  
-   <span data-ttu-id="587fc-136">監視サーバー インスタンスがオフラインになり、その後オンラインに戻ったとき、警告メッセージ ジョブが実行される前に、**log_shipping_monitor_primary** テーブルが現在の値に更新されません。</span><span class="sxs-lookup"><span data-stu-id="587fc-136">When the monitor server instance goes offline and then comes back online, the **log_shipping_monitor_primary** table is not updated with the current values before the alert message job runs.</span></span> <span data-ttu-id="587fc-137">監視テーブルを更新して、プライマリ データベースの最新データを反映させるには、プライマリ サーバー インスタンスで **sp_refresh_log_shipping_monitor** を実行します。</span><span class="sxs-lookup"><span data-stu-id="587fc-137">To update the monitor tables with the latest data for the primary database, run **sp_refresh_log_shipping_monitor** on the primary server instance.</span></span>  
  
-   <span data-ttu-id="587fc-138">プライマリ サーバー インスタンスまたは監視サーバー インスタンスで、日付または時刻が正しく設定されていません。</span><span class="sxs-lookup"><span data-stu-id="587fc-138">On the primary or monitor server instance, the date or time is incorrect.</span></span> <span data-ttu-id="587fc-139">これが原因で、警告メッセージが生成される場合もあります。</span><span class="sxs-lookup"><span data-stu-id="587fc-139">This may also generate alert messages.</span></span> <span data-ttu-id="587fc-140">これらいずれかのサーバーで、システムの日付または時刻が変更された可能性があります。</span><span class="sxs-lookup"><span data-stu-id="587fc-140">Possibly the system date or time was modified on the one of them.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="587fc-141">2 つのサーバー インスタンスでタイム ゾーンが異なることによって、問題が発生することはありません。</span><span class="sxs-lookup"><span data-stu-id="587fc-141">Different time zones for the two server instances should not cause a problem.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="587fc-142">参照</span><span class="sxs-lookup"><span data-stu-id="587fc-142">See Also</span></span>  
 <span data-ttu-id="587fc-143">[log_shipping_monitor_primary &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/log-shipping-monitor-primary-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="587fc-143">[log_shipping_monitor_primary &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/log-shipping-monitor-primary-transact-sql) </span></span>  
 <span data-ttu-id="587fc-144">[ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="587fc-144">[About Log Shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md) </span></span>  
 <span data-ttu-id="587fc-145">[sp_help_log_shipping_monitor_primary &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-primary-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="587fc-145">[sp_help_log_shipping_monitor_primary &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-primary-transact-sql) </span></span>  
 <span data-ttu-id="587fc-146">[sp_refresh_log_shipping_monitor &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="587fc-146">[sp_refresh_log_shipping_monitor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql) </span></span>  
 [<span data-ttu-id="587fc-147">ログ配布について &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="587fc-147">About Log Shipping &#40;SQL Server&#41;</span></span>](../../database-engine/log-shipping/about-log-shipping-sql-server.md)  
  
  
