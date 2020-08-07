---
title: プライマリ ログ配布サーバーとセカンダリ ログ配布サーバー間でのロールの変更 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], role changes
- secondary data files [SQL Server], roles changed between
- primary databases [SQL Server]
- initial role changes [SQL Server]
- log shipping [SQL Server], failover
- failover [SQL Server], log shipping
ms.assetid: 2d7cc40a-47e8-4419-9b2b-7c69f700e806
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 52ddb89bfd18eef4cd2140bc67cf93d1800138f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718669"
---
# <a name="change-roles-between-primary-and-secondary-log-shipping-servers-sql-server"></a><span data-ttu-id="3825b-102">プライマリ ログ配布サーバーとセカンダリ ログ配布サーバー間でのロールの変更 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3825b-102">Change Roles Between Primary and Secondary Log Shipping Servers (SQL Server)</span></span>
  <span data-ttu-id="3825b-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログ配布構成をセカンダリ サーバーにフェールオーバーした後、プリイマリ データベースとして機能するようにセカンダリ データベースを構成できます。</span><span class="sxs-lookup"><span data-stu-id="3825b-103">After you have failed over a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log shipping configuration to a secondary server, you can configure your secondary database to act as the primary database.</span></span> <span data-ttu-id="3825b-104">その後、プライマリ データベースとセカンダリ データベースを必要に応じて切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="3825b-104">Then, you will be able to swap primary and secondary databases as needed.</span></span>  
  
## <a name="performing-the-initial-role-change"></a><span data-ttu-id="3825b-105">初期ロール切り替えの実行</span><span class="sxs-lookup"><span data-stu-id="3825b-105">Performing the Initial Role Change</span></span>  
 <span data-ttu-id="3825b-106">初めてセカンダリ データベースにフェールオーバーし、これを新しいプライマリ データベースとして使用する場合は、次の一連の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3825b-106">The first time you want to fail over to the secondary database and make it your new primary database, there is a series of steps you must take.</span></span> <span data-ttu-id="3825b-107">この初期手順を実行した後、プライマリ データベースとセカンダリ データベース間でロールを簡単に切り替えることができるようになります。</span><span class="sxs-lookup"><span data-stu-id="3825b-107">After you have followed these initial steps, you will be able to swap roles between the primary database and the secondary database easily.</span></span>  
  
1.  <span data-ttu-id="3825b-108">プライマリ データベースからセカンダリ データベースに手動でフェールオーバーします。</span><span class="sxs-lookup"><span data-stu-id="3825b-108">Manually fail over from the primary database to a secondary database.</span></span> <span data-ttu-id="3825b-109">NORECOVERY 句を使用して、プライマリ サーバー上のアクティブなトランザクション ログを必ずバックアップしてください。</span><span class="sxs-lookup"><span data-stu-id="3825b-109">Be sure to back up the active transaction log on your primary server with NORECOVERY.</span></span> <span data-ttu-id="3825b-110">詳細については、「 [ログ配布のセカンダリへのフェールオーバー &#40;SQL Server&#41;](fail-over-to-a-log-shipping-secondary-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3825b-110">For more information, see [Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;](fail-over-to-a-log-shipping-secondary-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="3825b-111">元のプライマリ サーバー上のログ配布バックアップ ジョブと、元のセカンダリ サーバー上のコピーおよび復元ジョブを無効にします。</span><span class="sxs-lookup"><span data-stu-id="3825b-111">Disable the log shipping backup job on the original primary server, and the copy and restore jobs on the original secondary server.</span></span>  
  
3.  <span data-ttu-id="3825b-112">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、セカンダリ データベース (新しいプライマリにするデータベース) でログ配布を構成します。</span><span class="sxs-lookup"><span data-stu-id="3825b-112">On your secondary database (the database you want to be the new primary), configure log shipping using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="3825b-113">詳細については、「 [ログ配布の構成 &#40;SQL Server&#41;](configure-log-shipping-sql-server.md)で導入されました。</span><span class="sxs-lookup"><span data-stu-id="3825b-113">For more information, see [Configure Log Shipping &#40;SQL Server&#41;](configure-log-shipping-sql-server.md).</span></span> <span data-ttu-id="3825b-114">手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3825b-114">Include the following steps:</span></span>  
  
    1.  <span data-ttu-id="3825b-115">元のプライマリ サーバーについて作成したときと同じ共有を使用してバックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="3825b-115">Use the same share for creating backups that you created for the original primary server.</span></span>  
  
    2.  <span data-ttu-id="3825b-116">セカンダリ データベースを追加するときは、 **[セカンダリ データベースの設定]** ダイアログ ボックスの **[セカンダリ データベース]** ボックスに元のプライマリ データベースの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="3825b-116">When adding the secondary database, in the **Secondary Database Settings** dialog box, enter the name of the original primary database in the **Secondary database** box.</span></span>  
  
    3.  <span data-ttu-id="3825b-117">**[セカンダリ データベースの設定]** ダイアログ ボックスで、 **[いいえ、セカンダリ データベースは初期化されています]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3825b-117">In the **Secondary Database Settings** dialog box, select **No, the secondary database is initialized**.</span></span>  
  
4.  <span data-ttu-id="3825b-118">ログ配布モニターが以前のログ配布構成で有効になっていた場合は、新しいログ配布構成を監視するようにログ配布モニターを再構成します。</span><span class="sxs-lookup"><span data-stu-id="3825b-118">If log shipping monitoring was enabled on your former log shipping configuration, reconfigure log shipping monitoring to monitor the new log shipping configuration.</span></span>  <span data-ttu-id="3825b-119">*database_name* をデータベースの名前に置き換えて、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="3825b-119">Execute the following commands, replacing *database_name* with the name of your database:</span></span>  
  
    1.  <span data-ttu-id="3825b-120">**新しいプライマリ サーバーで、**</span><span class="sxs-lookup"><span data-stu-id="3825b-120">**On the new primary server**</span></span>  
  
         <span data-ttu-id="3825b-121">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="3825b-121">Execute the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
        ```  
        -- Statement to execute on the new primary server  
        USE msdb  
        GO  
        EXEC master.dbo.sp_change_log_shipping_secondary_database @secondary_database = N'database_name', @threshold_alert_enabled = 0;  
        GO  
        ```  
  
    2.  <span data-ttu-id="3825b-122">**新しいセカンダリ サーバーで、**</span><span class="sxs-lookup"><span data-stu-id="3825b-122">**On the new secondary server**</span></span>  
  
         <span data-ttu-id="3825b-123">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="3825b-123">Execute the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
        ```  
        -- Statement to execute on the new secondary server  
        USE msdb  
        GO  
        EXEC master.dbo.sp_change_log_shipping_primary_database @database=N'database_name', @threshold_alert_enabled = 0;  
        GO  
        ```  
  
## <a name="swapping-roles"></a><span data-ttu-id="3825b-124">ロールの切り替え</span><span class="sxs-lookup"><span data-stu-id="3825b-124">Swapping Roles</span></span>  
 <span data-ttu-id="3825b-125">上記の初期ロール切り替えの手順が完了したら、このセクションの手順に従って、プライマリ データベースとセカンダリ データベース間のロールを切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="3825b-125">After you have completed the steps above for the initial role change, you can change roles between the primary database and the secondary database by following the steps in this section.</span></span> <span data-ttu-id="3825b-126">ロールを切り替えるには、次の一般的な手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="3825b-126">To perform a role change, follow these general steps:</span></span>  
  
1.  <span data-ttu-id="3825b-127">セカンダリ データベースをオンラインにし、NORECOVERY 句を使用してプライマリ サーバー上のトランザクション ログをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="3825b-127">Bring the secondary database online, backing up the transaction log on the primary server with NORECOVERY.</span></span>  
  
2.  <span data-ttu-id="3825b-128">元のプライマリ サーバー上のログ配布バックアップ ジョブと、元のセカンダリ サーバー上のコピーおよび復元ジョブを無効にします。</span><span class="sxs-lookup"><span data-stu-id="3825b-128">Disable the log shipping backup job on the original primary server, and the copy and restore jobs on the original secondary server.</span></span>  
  
3.  <span data-ttu-id="3825b-129">セカンダリ サーバー (新しいプライマリ サーバー) 上のログ配布バックアップ ジョブを有効にし、プライマリ サーバー (新しいセカンダリ サーバー) 上のコピーおよび復元ジョブを有効にします。</span><span class="sxs-lookup"><span data-stu-id="3825b-129">Enable the log shipping backup job on the secondary server (the new primary server), and the copy and restore jobs on the primary server (the new secondary server).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3825b-130">セカンダリ データベースをプライマリ データベースに変更するときは、ユーザーおよびアプリケーションに一貫した使用環境を提供するために、新しいプライマリ サーバー インスタンスで、ログインやジョブなどのデータベースのメタデータの一部またはすべてを作成し直す必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="3825b-130">When you change a secondary database to the primary database, to provide a consistent experience to users and applications, you might have to re-create some or all of the metadata for the database, such as logins and jobs, on the new primary server instance.</span></span> <span data-ttu-id="3825b-131">詳細については、「 [データベースを別のサーバー インスタンスで使用できるようにするときのメタデータの管理 &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3825b-131">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="3825b-132">関連タスク</span><span class="sxs-lookup"><span data-stu-id="3825b-132">Related Tasks</span></span>  
  
-   [<span data-ttu-id="3825b-133">ログ配布のセカンダリへのフェールオーバー &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3825b-133">Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;</span></span>](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
-   [<span data-ttu-id="3825b-134">役割の交代後のログインとジョブの管理 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3825b-134">Management of Logins and Jobs After Role Switching &#40;SQL Server&#41;</span></span>](../../sql-server/failover-clusters/management-of-logins-and-jobs-after-role-switching-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="3825b-135">参照</span><span class="sxs-lookup"><span data-stu-id="3825b-135">See Also</span></span>  
 [<span data-ttu-id="3825b-136">ログ配布テーブルとストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="3825b-136">Log Shipping Tables and Stored Procedures</span></span>](log-shipping-tables-and-stored-procedures.md)  
  
  
