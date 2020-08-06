---
title: データベース ミラーリング モニターの概要 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dbmmonitor.main.f1
helpviewer_keywords:
- Database Mirroring Monitor [SQL Server], interface
ms.assetid: 8ebbdcd6-565a-498f-b674-289c84b985eb
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d19f9a2aa66aaee30bcf623e254d6f24aa690277
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716801"
---
# <a name="database-mirroring-monitor-overview"></a><span data-ttu-id="0c92f-102">データベース ミラーリング モニターの概要</span><span class="sxs-lookup"><span data-stu-id="0c92f-102">Database Mirroring Monitor Overview</span></span>
  <span data-ttu-id="0c92f-103">適切な権限を持つユーザーであれば、データベース ミラーリング モニターを使用することにより、サーバー インスタンス上のミラー化されたデータベースのサブセットを監視できます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-103">If you have the correct permissions, you can use Database Mirroring Monitor to monitor any subset of the mirrored databases on a server instance.</span></span> <span data-ttu-id="0c92f-104">監視を行うことにより、データベース ミラーリング セッションで適切なデータ フローが保たれているかどうかを詳細に検証できます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-104">Monitoring enables you to verify whether and how well data is flowing in the database mirroring session.</span></span> <span data-ttu-id="0c92f-105">データベース ミラーリング モニターは、データ フローの停滞の原因をトラブルシューティングするときにも有効に使用できます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-105">Database Mirroring Monitor is also useful for troubleshooting the cause of reduced data flow.</span></span>  
  
 <span data-ttu-id="0c92f-106">各フェールオーバー パートナーにおける監視の対象としては、ミラー化された任意のデータベースを登録できます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-106">You can register any of your mirrored databases for monitoring on each of the failover partners individually.</span></span> <span data-ttu-id="0c92f-107">データベースを登録すると、そのデータベースに関して、次の情報がデータベース ミラーリング モニターによってキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-107">When you register a database, Database Mirroring Monitor caches the following information about the database:</span></span>  
  
-   <span data-ttu-id="0c92f-108">データベース名</span><span class="sxs-lookup"><span data-stu-id="0c92f-108">Database name</span></span>  
  
-   <span data-ttu-id="0c92f-109">2 つのパートナー サーバー インスタンスの名前</span><span class="sxs-lookup"><span data-stu-id="0c92f-109">The names of the two partner server instances</span></span>  
  
-   <span data-ttu-id="0c92f-110">各パートナーの最後に認識されたロール (プリンシパルまたはミラー)</span><span class="sxs-lookup"><span data-stu-id="0c92f-110">The last known roles of each partner (principal or mirror)</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="0c92f-111">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="0c92f-111">Permissions</span></span>  
 <span data-ttu-id="0c92f-112">データベース ミラーリングを監視するには、サーバー インスタンスの **msdb** データベースにおいて、 **sysadmin** 固定サーバー ロールまたは **dbm_monitor** 固定データベース ロールのメンバーであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="0c92f-112">To monitor database mirroring, you must be a member of either the **sysadmin** fixed server role or the **dbm_monitor** fixed database role in the **msdb** database on the server instance.</span></span> <span data-ttu-id="0c92f-113">1 つのパートナー サーバー インスタンスだけが **sysadmin** または **dbm_monitor** のメンバーの場合、モニターは、該当するパートナーにのみ接続でき、他のパートナーからは情報を取得できません。</span><span class="sxs-lookup"><span data-stu-id="0c92f-113">If you are a member of **sysadmin** or **dbm_monitor** on only one of the partner server instances, the monitor can connect only to that partner; the monitor cannot retrieve information from the other partner.</span></span>  
  
 <span data-ttu-id="0c92f-114">サーバー インスタンスで、 **dbm_monitor** だけのメンバーである場合、そのサーバー インスタンスにおける権限は制限されます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-114">If you are a member of just **dbm_monitor** on a server instance, you will have limited permissions on that server instance.</span></span> <span data-ttu-id="0c92f-115">最新の状態行を読み取り専用で参照することしかできません。</span><span class="sxs-lookup"><span data-stu-id="0c92f-115">You will only be able to view the most recent status row.</span></span> <span data-ttu-id="0c92f-116">**dbm_monitor** の権限でサーバー インスタンスに接続した場合、権限が制限されることが、データベース ミラーリング モニターによって通知されます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-116">If you connect to a server instance using **dbm_monitor** permissions, Database Mirroring Monitor informs you that you have limited permissions.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0c92f-117">**dbm_monitor** 固定データベース ロールは、データベース ミラーリング モニターに最初のデータベースが登録されたときに、 **msdb** データベースに作成されます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-117">The **dbm_monitor** fixed database role is created in the **msdb** database when the first database is registered in Database Mirroring Monitor.</span></span> <span data-ttu-id="0c92f-118">新しい **dbm_monitor** ロールには、メンバーは割り当てられていません。システム管理者がそのロールにユーザーを割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="0c92f-118">The new **dbm_monitor** role has no members until a system administrator assigns users to the role.</span></span>  
  
## <a name="navigation-tree"></a><span data-ttu-id="0c92f-119">ナビゲーション ツリー</span><span class="sxs-lookup"><span data-stu-id="0c92f-119">Navigation Tree</span></span>  
 <span data-ttu-id="0c92f-120">データベース ミラーリング モニターによる監視の対象としてデータベースが登録されている場合、登録されたデータベースがナビゲーション ツリーに一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-120">If any databases have been registered for monitoring by the Database Mirroring Monitor, a list of registered databases is displayed in the navigation tree.</span></span> <span data-ttu-id="0c92f-121">ツリーは 30 秒ごとに自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-121">The tree automatically refreshes every 30 seconds.</span></span> <span data-ttu-id="0c92f-122">登録されたデータベースの状態を調べるには、目的のデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="0c92f-122">To see the status of a registered database, select it.</span></span> <span data-ttu-id="0c92f-123">詳細については、このトピックの「詳細ペイン」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0c92f-123">For more information, see "Detail Pane," later in this topic.</span></span>  
  
 <span data-ttu-id="0c92f-124">次の情報が登録されたデータベースごとに表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-124">For each registered database, the following information is displayed:</span></span>  
  
 <span data-ttu-id="0c92f-125">_<Database_name>_ **(** _\<Status>_ **,** _<PRINCIPAL_SERVER>_ **->** _<MIRROR_SERVER>_ **)**</span><span class="sxs-lookup"><span data-stu-id="0c92f-125">_<Database_name>_ **(** _\<Status>_ **,** _<PRINCIPAL_SERVER>_ **->** _<MIRROR_SERVER>_ **)**</span></span>  
  
 <span data-ttu-id="0c92f-126">*<Database_name>*</span><span class="sxs-lookup"><span data-stu-id="0c92f-126">*<Database_name>*</span></span>  
 <span data-ttu-id="0c92f-127">データベース ミラーリング モニターに登録されている、ミラー化されたデータベースの名前です。</span><span class="sxs-lookup"><span data-stu-id="0c92f-127">The name of a mirrored database that is registered with the Database Mirroring Monitor.</span></span>  
  
 *\<Status>*  
 <span data-ttu-id="0c92f-128">表示される状態および対応するアイコンを次に示します。</span><span class="sxs-lookup"><span data-stu-id="0c92f-128">The possible statuses and their associated icons are as follows:</span></span>  
  
|<span data-ttu-id="0c92f-129">アイコン</span><span class="sxs-lookup"><span data-stu-id="0c92f-129">Icon</span></span>|<span data-ttu-id="0c92f-130">Status</span><span class="sxs-lookup"><span data-stu-id="0c92f-130">Status</span></span>|<span data-ttu-id="0c92f-131">説明</span><span class="sxs-lookup"><span data-stu-id="0c92f-131">Description</span></span>|  
|----------|------------|-----------------|  
|<span data-ttu-id="0c92f-132">警告アイコン</span><span class="sxs-lookup"><span data-stu-id="0c92f-132">Warning icon</span></span>|<span data-ttu-id="0c92f-133">**Unknown**</span><span class="sxs-lookup"><span data-stu-id="0c92f-133">**Unknown**</span></span>|<span data-ttu-id="0c92f-134">モニターがいずれのパートナーにも接続されていません。</span><span class="sxs-lookup"><span data-stu-id="0c92f-134">The monitor is not connected to either partner.</span></span> <span data-ttu-id="0c92f-135">モニターによってキャッシュされている情報だけを確認できます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-135">The only available information is what has been cached by the monitor.</span></span>|  
|<span data-ttu-id="0c92f-136">警告アイコン</span><span class="sxs-lookup"><span data-stu-id="0c92f-136">Warning icon</span></span>|<span data-ttu-id="0c92f-137">**[同期中]**</span><span class="sxs-lookup"><span data-stu-id="0c92f-137">**Synchronizing**</span></span>|<span data-ttu-id="0c92f-138">ミラー データベースの内容が、プリンシパル データベースの内容に遅れています。</span><span class="sxs-lookup"><span data-stu-id="0c92f-138">The contents of the mirror database are lagging behind the contents of the principal database.</span></span> <span data-ttu-id="0c92f-139">プリンシパル サーバー インスタンスからミラー サーバー インスタンスにログ レコードを送信して、ミラー データベースを更新するための変更を適用しています。</span><span class="sxs-lookup"><span data-stu-id="0c92f-139">The principal server instance is sending log records to the mirror server instance, which is applying the changes to the mirror database to roll it forward.</span></span><br /><br /> <span data-ttu-id="0c92f-140">データベース ミラーリング セッションの開始時には、ミラー データベースとプリンシパル データベースはこの状態です。</span><span class="sxs-lookup"><span data-stu-id="0c92f-140">At the start of a database mirroring session, the mirror and principal databases are in this state.</span></span>|  
|<span data-ttu-id="0c92f-141">データベースを表す円柱形のアイコン</span><span class="sxs-lookup"><span data-stu-id="0c92f-141">Standard database cylinder</span></span>|<span data-ttu-id="0c92f-142">**同期済み**</span><span class="sxs-lookup"><span data-stu-id="0c92f-142">**Synchronized**</span></span>|<span data-ttu-id="0c92f-143">ミラー サーバーがプリンシパル サーバーとの遅延を解消すると、データベースの状態が **[同期済み]** になります。</span><span class="sxs-lookup"><span data-stu-id="0c92f-143">When the mirror server becomes sufficiently caught up to the principal server, the database state changes to **Synchronized**.</span></span> <span data-ttu-id="0c92f-144">プリンシパル サーバーがミラー サーバーに変更を送信し、ミラー サーバーがミラー データベースに変更を適用する、という処理が継続されている限り、データベースはこの状態のままです。</span><span class="sxs-lookup"><span data-stu-id="0c92f-144">The database remains in this state as long as the principal server continues to send changes to the mirror server and the mirror server continues to apply changes to the mirror database.</span></span><br /><br /> <span data-ttu-id="0c92f-145">高い安全性モードの場合、自動フェールオーバーおよび手動フェールオーバーの両方がサポートされています。データの損失はありません。</span><span class="sxs-lookup"><span data-stu-id="0c92f-145">For high-safety mode, automatic failover and manual failover are both possible, without any data loss.</span></span><br /><br /> <span data-ttu-id="0c92f-146">高パフォーマンス モードの場合、 **[同期済み]** 状態でも、一部のデータが損失する可能性は常にあります。</span><span class="sxs-lookup"><span data-stu-id="0c92f-146">For high-performance mode, some data loss is always possible, even in the **Synchronized** state.</span></span>|  
|<span data-ttu-id="0c92f-147">警告アイコン</span><span class="sxs-lookup"><span data-stu-id="0c92f-147">Warning icon</span></span>|<span data-ttu-id="0c92f-148">**中断済み**</span><span class="sxs-lookup"><span data-stu-id="0c92f-148">**Suspended**</span></span>|<span data-ttu-id="0c92f-149">プリンシパル データベースは使用できますが、ミラー サーバーにログを送信していません。</span><span class="sxs-lookup"><span data-stu-id="0c92f-149">The principal database is available but is not sending any logs to the mirror server.</span></span>|  
|<span data-ttu-id="0c92f-150">エラー アイコン</span><span class="sxs-lookup"><span data-stu-id="0c92f-150">Error icon</span></span>|<span data-ttu-id="0c92f-151">**切断**</span><span class="sxs-lookup"><span data-stu-id="0c92f-151">**Disconnected**</span></span>|<span data-ttu-id="0c92f-152">サーバー インスタンスがパートナーに接続できません。</span><span class="sxs-lookup"><span data-stu-id="0c92f-152">The server instance cannot connect to its partner.</span></span>|  
  
 <span data-ttu-id="0c92f-153">*<PRINCIPAL_SERVER>*</span><span class="sxs-lookup"><span data-stu-id="0c92f-153">*<PRINCIPAL_SERVER>*</span></span>  
 <span data-ttu-id="0c92f-154">現在プリンシパル サーバー インスタンスとして動作しているパートナーの名前です。</span><span class="sxs-lookup"><span data-stu-id="0c92f-154">The name of the partner that is currently the principal server instance.</span></span> <span data-ttu-id="0c92f-155">名前には次の形式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-155">The name is in the following format:</span></span>  
  
 <span data-ttu-id="0c92f-156">*<システム名>* [ **\\** _<インスタンス名>_ ]</span><span class="sxs-lookup"><span data-stu-id="0c92f-156">*<SYSTEM_NAME>*[**\\**_<instance_name>_]</span></span>  
  
 <span data-ttu-id="0c92f-157">ここで、 *<システム名>* は、サーバー インスタンスが存在するシステムの名前です。</span><span class="sxs-lookup"><span data-stu-id="0c92f-157">where *<SYSTEM_NAME>* is the name of the system on which the server instance resides.</span></span> <span data-ttu-id="0c92f-158">既定以外のサーバー インスタンスについても、 _<システム名>_ **\\** _<インスタンス名>_ という形式でインスタンス名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-158">For a non-default server instance, the instance name is also displayed: _<SYSTEM_NAME>_**\\**_<instance_name>_.</span></span>  
  
 <span data-ttu-id="0c92f-159">*<MIRROR_SERVER>*</span><span class="sxs-lookup"><span data-stu-id="0c92f-159">*<MIRROR_SERVER>*</span></span>  
 <span data-ttu-id="0c92f-160">現在ミラー サーバー インスタンスとして動作しているパートナーの名前です。</span><span class="sxs-lookup"><span data-stu-id="0c92f-160">The name of the partner that is currently the mirror server instance.</span></span> <span data-ttu-id="0c92f-161">名前の形式はプリンシパル サーバーと同じです。</span><span class="sxs-lookup"><span data-stu-id="0c92f-161">The format is the same as for the principal server.</span></span>  
  
## <a name="detail-pane"></a><span data-ttu-id="0c92f-162">詳細ペイン</span><span class="sxs-lookup"><span data-stu-id="0c92f-162">Detail Pane</span></span>  
 <span data-ttu-id="0c92f-163">モニターのインターフェイスは、選択されているデータベースによって異なります。</span><span class="sxs-lookup"><span data-stu-id="0c92f-163">The appearance of the monitor depends on whether a database is selected.</span></span> <span data-ttu-id="0c92f-164">モニターを開くと、詳細ペインに **[ミラー化されたデータベースの登録]** というリンクが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-164">When you open the monitor, the detail pane displays a **Register mirrored database** link.</span></span> <span data-ttu-id="0c92f-165">このリンクをクリックすると、データベースを登録できます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-165">Click this to register a database.</span></span> <span data-ttu-id="0c92f-166">登録されたデータベースは、ナビゲーション ツリーの **[データベース ミラーリング モニター]** ノードに一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-166">Registered databases are listed below the **Database Mirroring Monitor** node in the navigation tree.</span></span> <span data-ttu-id="0c92f-167">データベース ミラーリング モニターは常に、資格情報を保持しているすべてのサーバー インスタンスに対して接続を試みます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-167">Database Mirroring Monitor always tries to connect to every server instance for which it has stored credentials.</span></span>  
  
 <span data-ttu-id="0c92f-168">データベースを選択すると、その状態が詳細ペインの **[状態]** タブ ページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-168">When you select a database, its status is displayed on the **Status** tabbed page in the detail pane.</span></span> <span data-ttu-id="0c92f-169">このページには、プリンシパル サーバー インスタンスとミラー サーバー インスタンスの両方から取得された情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-169">The content of this page comes from both the principal and mirror server instances.</span></span> <span data-ttu-id="0c92f-170">状態はプリンシパル サーバー インスタンスとミラー サーバー インスタンスへの別個の接続を使用して収集されるので、このページの値は非同期に設定されます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-170">The page is filled asynchronously as status is gathered through separate connections to the principal and mirror server instances.</span></span> <span data-ttu-id="0c92f-171">状態は 30 秒間隔で自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-171">The status automatically refreshes at 30-second intervals.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0c92f-172">監視の更新頻度を変更することはできません。ただし、 **[データベース ミラーリングの履歴]** ダイアログ ボックスから状態テーブルを更新することは可能です。</span><span class="sxs-lookup"><span data-stu-id="0c92f-172">You cannot change the monitor's refresh rate, but you can refresh the status table from the **Database Mirroring History** dialog box.</span></span>  
  
 <span data-ttu-id="0c92f-173">システム管理者は、 **[警告]** タブ ページをクリックすることにより、データベースに対する現在の警告構成を表示できます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-173">A system administrator can view the current configuration of warnings for the database by selecting the **Warnings** tabbed page.</span></span> <span data-ttu-id="0c92f-174">このページから、 **[警告しきい値の設定]** ダイアログ ボックスを起動し、警告しきい値を有効にしたり構成したりできます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-174">From there, the administrator can launch the **Set Warning Thresholds** dialog box to enable and configure one or more warning thresholds.</span></span>  
  
 <span data-ttu-id="0c92f-175">タブの上にあるバナーの詳細ウィンドウには、モニターが最後に状態情報を更新した日時が [**最終更新:**] と表示されます _\<date>_ *\<time>* 。</span><span class="sxs-lookup"><span data-stu-id="0c92f-175">In the banner above the tabs, the detail pane displays the last time the monitor refreshed the status information as, **Last refresh:**_\<date>_*\<time>*.</span></span> <span data-ttu-id="0c92f-176">通常、状態情報は、プリンシパル サーバー インスタンスおよびミラー サーバー インスタンスから別々の時間に取得されます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-176">Usually, the Database Mirroring Monitor retrieves status information from the principal and mirror server instances at different times.</span></span> <span data-ttu-id="0c92f-177">表示されるのは、この 2 つの更新日時の古い方になります。</span><span class="sxs-lookup"><span data-stu-id="0c92f-177">The older of these two refresh times is displayed.</span></span>  
  
## <a name="action-menu"></a><span data-ttu-id="0c92f-178">[アクション] メニュー</span><span class="sxs-lookup"><span data-stu-id="0c92f-178">Action Menu</span></span>  
 <span data-ttu-id="0c92f-179">**[アクション]** メニューには、常に次のコマンドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-179">The **Action** menu always contains the following commands:</span></span>  
  
|<span data-ttu-id="0c92f-180">コマンド</span><span class="sxs-lookup"><span data-stu-id="0c92f-180">Command</span></span>|<span data-ttu-id="0c92f-181">説明</span><span class="sxs-lookup"><span data-stu-id="0c92f-181">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0c92f-182">**[ミラー化されたデータベースの登録]**</span><span class="sxs-lookup"><span data-stu-id="0c92f-182">**Register Mirrored Database...**</span></span>|<span data-ttu-id="0c92f-183">**[ミラー化されたデータベースの登録]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-183">Opens the **Register Mirrored Database** dialog box.</span></span> <span data-ttu-id="0c92f-184">このダイアログ ボックスを使用すると、特定のサーバー インスタンスに対し、ミラー化されたデータベース (複数可) を登録できます。登録は、データベースをデータベース ミラーリング モニターに追加することによって行います。</span><span class="sxs-lookup"><span data-stu-id="0c92f-184">Use this dialog box to register one or more mirrored databases on a given server instance by adding the database or databases to the Database Mirroring Monitor.</span></span> <span data-ttu-id="0c92f-185">データベースを追加すると、データベースとそのパートナーに関する情報、およびパートナーへの接続方法に関する情報が、データベース ミラーリング モニターによってローカルにキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-185">When a database is added, Database Mirroring Monitor locally caches information about the database, its partners, and how to connect to the partners.</span></span>|  
|<span data-ttu-id="0c92f-186">**[サーバー インスタンスの接続管理]**</span><span class="sxs-lookup"><span data-stu-id="0c92f-186">**Manage Server Instance Connections...**</span></span>|<span data-ttu-id="0c92f-187">このコマンドを選択すると、 **[サーバー インスタンスの接続管理]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-187">When you select this command, the **Manage Server Connections** dialog box opens.</span></span> <span data-ttu-id="0c92f-188">ここでサーバー インスタンスを選択し、モニターが特定のパートナーへの接続時に使用する資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="0c92f-188">There, you can choose a server instance for which you want to specify credentials for the monitor to use when connecting to a given partner.</span></span><br /><br /> <span data-ttu-id="0c92f-189">パートナーの資格情報を編集するには、 **[サーバー インスタンス]** グリッドから対応するエントリを探し、その行の **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0c92f-189">To edit the credentials for a partner, locate its entry in the **Server instances** grid, and click **Edit** on that row.</span></span> <span data-ttu-id="0c92f-190">**[サーバーへの接続]** ダイアログ ボックスが開き、現在キャッシュされている値に資格情報が初期化されて表示されます。サーバー インスタンス名は編集できません。</span><span class="sxs-lookup"><span data-stu-id="0c92f-190">The **Connect to Server** dialog box appears with the server instance name fixed and the credential controls initialized to the current cached value.</span></span> <span data-ttu-id="0c92f-191">認証情報を必要に応じて変更し、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0c92f-191">Change the authentication information as necessary and click **Connect**.</span></span> <span data-ttu-id="0c92f-192">その資格情報に十分な特権がある場合は、 **[接続に使用する認証]** 列が新しい資格情報で更新されます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-192">If the credentials have sufficient privileges, the **Connect Using** column is updated with the new credentials.</span></span>|  
  
 <span data-ttu-id="0c92f-193">データベースが選択されている場合、 **[アクション]** メニューには、さらに次のコマンドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-193">If you select a database, the **Action** menu also contains the following commands.</span></span>  
  
|<span data-ttu-id="0c92f-194">コマンド</span><span class="sxs-lookup"><span data-stu-id="0c92f-194">Command</span></span>|<span data-ttu-id="0c92f-195">説明</span><span class="sxs-lookup"><span data-stu-id="0c92f-195">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0c92f-196">**[このデータベースの登録を解除]**</span><span class="sxs-lookup"><span data-stu-id="0c92f-196">**Unregister This Database**</span></span>|<span data-ttu-id="0c92f-197">選択されたデータベースをデータベース ミラーリング モニターから削除します。</span><span class="sxs-lookup"><span data-stu-id="0c92f-197">Removes the selected database from Database Mirroring Monitor.</span></span>|  
|<span data-ttu-id="0c92f-198">**[警告しきい値の設定]**</span><span class="sxs-lookup"><span data-stu-id="0c92f-198">**Set Warning Thresholds...**</span></span>|<span data-ttu-id="0c92f-199">**[警告しきい値の設定]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-199">Opens the **Set Warning Thresholds** dialog box.</span></span> <span data-ttu-id="0c92f-200">ここでは、システム管理者が、各パートナーのデータベースに対する警告の有効/無効を切り替えたり、警告ごとにしきい値を変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="0c92f-200">There a system administrator can enable or disable warnings for the database on each of the partners and change the threshold of each warning.</span></span> <span data-ttu-id="0c92f-201">データベースのフェールオーバーが発生しても警告が保持されるように、警告のしきい値は、両方のパートナーに対して設定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="0c92f-201">We recommend setting a threshold for a given warning on both partners to ensure that the warning persists if the database fails over.</span></span> <span data-ttu-id="0c92f-202">適切なしきい値は、各パートナーのシステムのパフォーマンスによって異なります。</span><span class="sxs-lookup"><span data-stu-id="0c92f-202">The appropriate threshold for each partner depends on the performance capabilities of that partner's system.</span></span><br /><br /> <span data-ttu-id="0c92f-203">イベントがパフォーマンスのイベント ログに書き込まれるのは、状態テーブルの更新時に、該当する値がしきい値以上になった場合だけです。</span><span class="sxs-lookup"><span data-stu-id="0c92f-203">An event is written to the event log for a performance only if its value is at or above its threshold when the status table is being updated.</span></span> <span data-ttu-id="0c92f-204">状態が更新されるまでの間に、一時的にピーク値がしきい値に達した場合、そのピーク値は反映されません。</span><span class="sxs-lookup"><span data-stu-id="0c92f-204">If a peak value reaches the threshold momentarily between status updates that peak is missed.</span></span>|  
  
 <span data-ttu-id="0c92f-205">**SQL Server Management Studio を使用してデータベース ミラーリングを監視するには**</span><span class="sxs-lookup"><span data-stu-id="0c92f-205">**To monitor database mirroring by using SQL Server Management Studio to**</span></span>  
  
-   [<span data-ttu-id="0c92f-206">データベース ミラーリング モニターの起動 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="0c92f-206">Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;</span></span>](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
## <a name="see-also"></a><span data-ttu-id="0c92f-207">参照</span><span class="sxs-lookup"><span data-stu-id="0c92f-207">See Also</span></span>  
 <span data-ttu-id="0c92f-208">[データベース ミラーリングの監視 &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0c92f-208">[Monitoring Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="0c92f-209">データベース ミラーリング セキュリティ構成ウィザードの起動 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="0c92f-209">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
  