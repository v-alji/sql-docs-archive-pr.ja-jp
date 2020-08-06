---
title: 警告しきい値の設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dbmmonitor.setwarningthreshold.f1
ms.assetid: 17f93147-e7d9-4092-b4c2-c11b38051171
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2d5fd9c0213d74f3a6b5d0d4cb2f11d3531d336d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716717"
---
# <a name="set-warning-thresholds"></a><span data-ttu-id="55e23-102">[警告しきい値の設定]</span><span class="sxs-lookup"><span data-stu-id="55e23-102">Set Warning Thresholds</span></span>
  <span data-ttu-id="55e23-103">このダイアログ ボックスでは、 **[データベース ミラーリング モニター]** ダイアログ ボックスのナビゲーション ツリーで選択されているデータベースの警告しきい値を有効にしたり構成したりできます。</span><span class="sxs-lookup"><span data-stu-id="55e23-103">Use this dialog box to enable and configure one or more warning thresholds for the database selected in the navigation tree of the **Database Mirroring Monitor** dialog box.</span></span>  
  
 <span data-ttu-id="55e23-104">このダイアログ ボックスは、両方のサーバー インスタンスに接続を試みます。</span><span class="sxs-lookup"><span data-stu-id="55e23-104">The dialog box tries to connect to both server instances.</span></span> <span data-ttu-id="55e23-105">これらの接続は非同期的に確立されます。</span><span class="sxs-lookup"><span data-stu-id="55e23-105">These connections are established asynchronously.</span></span> <span data-ttu-id="55e23-106">ダイアログには、互いのパートナーの接続状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="55e23-106">The dialog shows the connection status of each partner.</span></span> <span data-ttu-id="55e23-107">パートナーが接続されていない場合は、 **[接続]** をクリックして接続できます。</span><span class="sxs-lookup"><span data-stu-id="55e23-107">If the partner is not connected, you can click **Connect**.</span></span>  
  
 <span data-ttu-id="55e23-108">**SQL Server Management Studio を使用してデータベース ミラーリングを監視するには**</span><span class="sxs-lookup"><span data-stu-id="55e23-108">**To use SQL Server Management Studio to monitor database mirroring**</span></span>  
  
-   [<span data-ttu-id="55e23-109">データベース ミラーリング モニターの起動 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="55e23-109">Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;</span></span>](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
## <a name="options"></a><span data-ttu-id="55e23-110">Options</span><span class="sxs-lookup"><span data-stu-id="55e23-110">Options</span></span>  
 <span data-ttu-id="55e23-111">*サーバー インスタンスと接続状態*</span><span class="sxs-lookup"><span data-stu-id="55e23-111">*Server instance and its connection status*</span></span>  
 <span data-ttu-id="55e23-112">_システム_INSTANCE_NAME の形式で、パートナーサーバーインスタンスの名前 **\\** _INSTANCE_NAME_。</span><span class="sxs-lookup"><span data-stu-id="55e23-112">Name of a partner server instance in the form _SYSTEM_**\\**_INSTANCE_NAME_.</span></span> <span data-ttu-id="55e23-113">既定のサーバー インスタンスの場合、システム名だけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="55e23-113">For a default server instance, only the system name is displayed.</span></span>  
  
 <span data-ttu-id="55e23-114">このフィールドには、該当のサーバー インスタンスに対して現在モニターが接続されているかどうかも示されます。</span><span class="sxs-lookup"><span data-stu-id="55e23-114">This field also indicates whether the monitor is currently connected to this server instance.</span></span> <span data-ttu-id="55e23-115">次の接続ステータスがあります。</span><span class="sxs-lookup"><span data-stu-id="55e23-115">The possible connection statuses are:</span></span>  
  
-   <span data-ttu-id="55e23-116">*server_instance_name* **に接続していません**</span><span class="sxs-lookup"><span data-stu-id="55e23-116">**Not connected to**  *server_instance_name*</span></span>  
  
-   <span data-ttu-id="55e23-117">*server_instance_name* **に接続しようとしています**</span><span class="sxs-lookup"><span data-stu-id="55e23-117">**Trying to connect to**  *server_instance_name*</span></span>  
  
-   <span data-ttu-id="55e23-118">*server_instance_name* **に接続**</span><span class="sxs-lookup"><span data-stu-id="55e23-118">**Connected to**  *server_instance_name*</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="55e23-119">**sysadmin** 固定サーバー ロールのメンバーでない場合、このステータスは "*server_instance_name* **に接続** **(制限された権限)** " になります。</span><span class="sxs-lookup"><span data-stu-id="55e23-119">If you do are not a member of the **sysadmin** fixed server role, this status is **Connected to** *server_instance_name* **(Limited permissions)**.</span></span>  
  
 <span data-ttu-id="55e23-120">パートナー サーバーの各インスタンスについて、その名前が *サーバー インスタンスと接続状態* を示すフィールドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="55e23-120">The name of each of the partner server instances is displayed in a separate *Server instance and its connection status* field.</span></span> <span data-ttu-id="55e23-121">一番上のフィールドには、モニターを開始した時点におけるプリンシパル サーバーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="55e23-121">The top field lists the principal server when the monitor started running.</span></span>  
  
 <span data-ttu-id="55e23-122">**接続**/**キャンセル**</span><span class="sxs-lookup"><span data-stu-id="55e23-122">**Connect**/**Cancel**</span></span>  
 <span data-ttu-id="55e23-123">**[接続]** / **[キャンセル]** ボタンは、 *サーバー インスタンスと接続状態* を示す各フィールドに関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="55e23-123">A **Connect**/**Cancel** button is associated with each *Server instance and its connection status* fields.</span></span> <span data-ttu-id="55e23-124">ボタンの状態は、接続ステータスによって異なります。</span><span class="sxs-lookup"><span data-stu-id="55e23-124">The state of the button depends on the connection status:</span></span>  
  
-   <span data-ttu-id="55e23-125">サーバー インスタンスに接続されていない場合、ボタンのテキストには **"接続"** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="55e23-125">If there is no connection to the server instance, the button text is **Connect**.</span></span> <span data-ttu-id="55e23-126">このボタンをクリックすると、サーバー インスタンスに接続できます。</span><span class="sxs-lookup"><span data-stu-id="55e23-126">Click to connect to the server instance.</span></span>  
  
-   <span data-ttu-id="55e23-127">接続を試行中の場合、ボタン テキストには **"キャンセル"** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="55e23-127">When a connection attempt is in progress, the button text is **Cancel**.</span></span> <span data-ttu-id="55e23-128">このボタンをクリックすると、試行中の接続が取り消されます。</span><span class="sxs-lookup"><span data-stu-id="55e23-128">Click to cancel the connection attempt.</span></span>  
  
-   <span data-ttu-id="55e23-129">サーバーが接続されている場合、ボタン テキストには **"接続済み"** と表示され、ボタンが淡色表示されます。</span><span class="sxs-lookup"><span data-stu-id="55e23-129">If the server is connected, the button text is **Connected**, and the button is dimmed.</span></span>  
  
 <span data-ttu-id="55e23-130">**しきい値**</span><span class="sxs-lookup"><span data-stu-id="55e23-130">**Thresholds**</span></span>  
 <span data-ttu-id="55e23-131">**[しきい値]** グリッドには、2 つのサーバー インスタンスに対する警告設定が表示されます。</span><span class="sxs-lookup"><span data-stu-id="55e23-131">The **Thresholds** grid displays the warnings settings for the two server instances.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="55e23-132">サーバー インスタンスが接続されていない場合、対応する列には空のセルが表示され、背景が淡色表示されます。</span><span class="sxs-lookup"><span data-stu-id="55e23-132">If a server instance is not connected, its columns are displayed with empty cells and a gray background.</span></span> <span data-ttu-id="55e23-133">接続が確立されている場合、グリッドには、対応するインスタンスからの情報が自動的に表示されます。</span><span class="sxs-lookup"><span data-stu-id="55e23-133">When the connection opens, the grid automatically displays the content from the instance.</span></span>  
  
 <span data-ttu-id="55e23-134">このグリッドには次の列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="55e23-134">The grid contains the following columns:</span></span>  
  
 <span data-ttu-id="55e23-135">**Warnings**</span><span class="sxs-lookup"><span data-stu-id="55e23-135">**Warnings**</span></span>  
 <span data-ttu-id="55e23-136">サポートされている警告が一覧表示されます。サポートされている警告は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="55e23-136">Lists the supported warnings:</span></span>  
  
|<span data-ttu-id="55e23-137">警告</span><span class="sxs-lookup"><span data-stu-id="55e23-137">Warning</span></span>|<span data-ttu-id="55e23-138">説明</span><span class="sxs-lookup"><span data-stu-id="55e23-138">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="55e23-139">**[未送信のログがしきい値を超えた場合に警告する]**</span><span class="sxs-lookup"><span data-stu-id="55e23-139">**Warn if the unsent log exceeds the threshold**</span></span>|<span data-ttu-id="55e23-140">プリンシパルの送信キューにある未送信ログのキロバイト (KB) 数を示すしきい値です。</span><span class="sxs-lookup"><span data-stu-id="55e23-140">The threshold indicates the number of kilobytes (KB) of the unsent log in the send queue on the principal.</span></span>|  
|<span data-ttu-id="55e23-141">**[復元されていないログがしきい値を超えた場合に警告する]**</span><span class="sxs-lookup"><span data-stu-id="55e23-141">**Warn if the unrestored log exceeds the threshold**</span></span>|<span data-ttu-id="55e23-142">ミラー サーバー インスタンスの再実行キューのキロバイト数を示すしきい値です。</span><span class="sxs-lookup"><span data-stu-id="55e23-142">The threshold indicates the number of KB of the redo queue on the mirror server instance.</span></span>|  
|<span data-ttu-id="55e23-143">**[最も古い未送信のトランザクションの経過期間がしきい値を超えた場合に警告する]**</span><span class="sxs-lookup"><span data-stu-id="55e23-143">**Warn if the age of the oldest unsent transaction exceeds the threshold**</span></span>|<span data-ttu-id="55e23-144">送信キューからミラー サーバー インスタンスにトランザクションが送信されない状態の経過時間 (分単位) を示すしきい値です。</span><span class="sxs-lookup"><span data-stu-id="55e23-144">The threshold indicates the number of minutes of transactions that have not yet been sent from the send queue to the mirror server instance.</span></span> <span data-ttu-id="55e23-145">この値は、データ損失の可能性を時間の観点から測定するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="55e23-145">This value helps measure the potential for data loss in terms of time.</span></span>|  
|<span data-ttu-id="55e23-146">**[ミラー コミットのオーバーヘッドがしきい値を超えた場合に警告する]**</span><span class="sxs-lookup"><span data-stu-id="55e23-146">**Warn if the mirror commit overhead exceeds the threshold**</span></span>|<span data-ttu-id="55e23-147">トランザクションあたりの遅延をミリ秒単位で示すしきい値です (高い安全性モードでのみ有効)。</span><span class="sxs-lookup"><span data-stu-id="55e23-147">The threshold indicates the number of milliseconds of delay per transaction (relevant only in high-safety mode).</span></span> <span data-ttu-id="55e23-148">この遅延時間は、ミラー サーバー インスタンスによってトランザクションのログ レコードが再実行キューに書き込まれるのをプリンシパル サーバー インスタンスが待機している間、発生したオーバーヘッドの量になります。</span><span class="sxs-lookup"><span data-stu-id="55e23-148">This delay is the amount of overhead incurred while the principal server instance waits for the mirror server instance to write the transaction's log record into the redo queue.</span></span>|  
  
 <span data-ttu-id="55e23-149">**'** *\<server instance>* **' で有効**</span><span class="sxs-lookup"><span data-stu-id="55e23-149">**Enabled at '** *\<server instance>* **'**</span></span>  
 <span data-ttu-id="55e23-150">チェック ボックスがオフの場合、現在、そのサーバー インスタンスでは警告が無効になっています。</span><span class="sxs-lookup"><span data-stu-id="55e23-150">A blank check box indicates that the warning is currently disabled on the server instance.</span></span> <span data-ttu-id="55e23-151">警告を有効にするには、対応するチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="55e23-151">To enable a warning, click its check box.</span></span>  
  
 <span data-ttu-id="55e23-152">**'** *\<server instance>* **' でのしきい値**</span><span class="sxs-lookup"><span data-stu-id="55e23-152">**Threshold at '** *\<server instance>* **'**</span></span>  
 <span data-ttu-id="55e23-153">警告を有効にする場合は、この列の左側にしきい値を設定します。</span><span class="sxs-lookup"><span data-stu-id="55e23-153">When a warning is enabled, set the threshold on the left side of this column.</span></span> <span data-ttu-id="55e23-154">状態テーブルが更新され、指定されたしきい値に達した場合、イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="55e23-154">An event occurs if the specified threshold has been reached when the status table is updated.</span></span> <span data-ttu-id="55e23-155">値を設定した後でしきい値を無効にした場合、その値はフィールドに表示されたままになり、警告を再度有効化した場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="55e23-155">If you disable a threshold after configuring a value, your value remains in this field and will be used if you re-enable the warning.</span></span>  
  
 <span data-ttu-id="55e23-156">警告が無効になっている場合、このフィールドは無効になります。</span><span class="sxs-lookup"><span data-stu-id="55e23-156">When a warning is not enabled, this field is inactive.</span></span>  
  
 <span data-ttu-id="55e23-157">**[OK]**</span><span class="sxs-lookup"><span data-stu-id="55e23-157">**OK**</span></span>  
 <span data-ttu-id="55e23-158">**[OK]** をクリックすると、このダイアログ ボックスが閉じ、 **[警告]** タブ ページの **[しきい値]** グリッドに、現在指定されている警告しきい値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="55e23-158">Clicking **OK** closes this dialog box and displays the currently specified values of warning thresholds in the **Thresholds** grid on the **Warnings**tabbed page.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55e23-159">解説</span><span class="sxs-lookup"><span data-stu-id="55e23-159">Remarks</span></span>  
 <span data-ttu-id="55e23-160">実際にしきい値が適用されるのは一度に 1 パートナーだけです。ただし、データベースのフェールオーバーが発生した場合にも警告が保持されるように、両方のパートナーに対してイベントのしきい値を設定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="55e23-160">A threshold is only applicable at one partner at a time, but we recommend that you set a threshold for a given event on both partners to ensure that the warning persists if the database fails over.</span></span> <span data-ttu-id="55e23-161">適切なしきい値は、各パートナーのシステムのパフォーマンスによって異なります。</span><span class="sxs-lookup"><span data-stu-id="55e23-161">The appropriate threshold for each partner depends on the performance capabilities of that partner's system.</span></span>  
  
 <span data-ttu-id="55e23-162">イベントがパフォーマンスのイベント ログに書き込まれるのは、状態テーブルの更新時に、該当する値がしきい値以上になった場合だけです。</span><span class="sxs-lookup"><span data-stu-id="55e23-162">An event is written to the event log for a performance only if its value is at or above its threshold when the status table is being updated.</span></span> <span data-ttu-id="55e23-163">状態が更新されるまでの間に、一時的にピーク値がしきい値に達した場合、そのピーク値は反映されません。</span><span class="sxs-lookup"><span data-stu-id="55e23-163">If a peak value reaches the threshold momentarily between status updates that peak is missed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55e23-164">参照</span><span class="sxs-lookup"><span data-stu-id="55e23-164">See Also</span></span>  
 <span data-ttu-id="55e23-165">[データベース ミラーリング モニターの起動 &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="55e23-165">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="55e23-166">[データベース ミラーリングの監視 &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="55e23-166">[Monitoring Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="55e23-167">データベース ミラーリング セキュリティ構成ウィザードの起動 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="55e23-167">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
  
