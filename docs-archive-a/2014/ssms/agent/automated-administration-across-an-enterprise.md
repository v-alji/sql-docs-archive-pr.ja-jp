---
title: エンタープライズ全体の管理の自動化 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- enterprise automatic administration [SQL Server]
- multiserver administration [SQL Server]
- SQL Server Agent jobs, multiserver administration
- jobs [SQL Server Agent], multiserver administration
- master servers [SQL Server], about master servers
- target servers [SQL Server], about target servers
- master servers [SQL Server]
- multiple instances of SQL Server
- target servers [SQL Server]
ms.assetid: 44d8365b-42bd-4955-b5b2-74a8a9f4a75f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8df3e34c2c70c81f9710ade0d6855446b930fb50
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642513"
---
# <a name="automated-administration-across-an-enterprise"></a><span data-ttu-id="c543b-102">エンタープライズ全体の管理の自動化</span><span class="sxs-lookup"><span data-stu-id="c543b-102">Automated Administration Across an Enterprise</span></span>
  <span data-ttu-id="c543b-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の複数のインスタンスにわたって管理を自動化することを *マルチサーバー管理*といいます。</span><span class="sxs-lookup"><span data-stu-id="c543b-103">Automating administration across multiple instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is called *multiserver administration*.</span></span> <span data-ttu-id="c543b-104">次の場合に、マルチサーバー管理を行います。</span><span class="sxs-lookup"><span data-stu-id="c543b-104">Use multiserver administration to do the following:</span></span>  
  
-   <span data-ttu-id="c543b-105">2 台以上のサーバーを管理する場合</span><span class="sxs-lookup"><span data-stu-id="c543b-105">Manage two or more servers.</span></span>  
  
-   <span data-ttu-id="c543b-106">データ ウェアハウジングのために、企業サーバーの情報フローをスケジュールする場合</span><span class="sxs-lookup"><span data-stu-id="c543b-106">Schedule information flows between enterprise servers for data warehousing.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c543b-107">総保有コストを削減するための継続的な取り組みの一環として [!INCLUDE[msCoName](../../includes/msconame-md.md)] 、で [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] は、ポリシーベースの管理と呼ばれるサーバーを管理する方法と、構成サーバーとサーバーグループを使用するマルチサーバークエリの2つの機能が導入されました。</span><span class="sxs-lookup"><span data-stu-id="c543b-107">As part of [!INCLUDE[msCoName](../../includes/msconame-md.md)] ongoing efforts to reduce the total cost of ownership, [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] introduced two features:  a method of managing servers that is called Policy-Based Management, and multiserver queries that use configuration servers and server groups.</span></span> <span data-ttu-id="c543b-108">この 2 つの機能は、ここで説明する機能の一部と組み合わせたり、それらの代わりとして使用したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="c543b-108">These features can be used with, or instead of, some of the features that are described in this topic.</span></span> <span data-ttu-id="c543b-109">詳細については、「[ポリシーベースの管理を使用](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)してサーバーを管理する」および「[中央管理サーバーを使用して複数のサーバーを管理する](../../relational-databases/administer-multiple-servers-using-central-management-servers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c543b-109">For more information, see [Administer Servers by Using Policy-Based Management](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md) and [Administer Multiple Servers Using Central Management Servers](../../relational-databases/administer-multiple-servers-using-central-management-servers.md).</span></span>  
  
 <span data-ttu-id="c543b-110">マルチサーバー管理機能を活用するには、1 台以上のマスター サーバーと 1 台以上のターゲット サーバーが必要です。</span><span class="sxs-lookup"><span data-stu-id="c543b-110">To take advantage of multiserver administration, you must have at least one master server and at least one target server.</span></span> <span data-ttu-id="c543b-111">マスター サーバーは、ターゲット サーバーに対してジョブを分散し、ターゲット サーバーからイベントを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="c543b-111">A master server distributes jobs to, and receives events from, target servers.</span></span> <span data-ttu-id="c543b-112">また、マスター サーバーは、ターゲット サーバーで実行されるジョブについて、ジョブ定義の中央コピーも保存します。</span><span class="sxs-lookup"><span data-stu-id="c543b-112">A master server also stores the central copy of job definitions for jobs that are run on target servers.</span></span> <span data-ttu-id="c543b-113">ターゲット サーバーは、定期的にマスター サーバーに接続して、ジョブのスケジュールを更新します。</span><span class="sxs-lookup"><span data-stu-id="c543b-113">Target servers connect periodically to the master server to update their schedule of jobs.</span></span> <span data-ttu-id="c543b-114">マスター サーバー上に新しいジョブがあれば、ターゲット サーバーはそのジョブをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="c543b-114">If a new job exists on the master server, the target server downloads the job.</span></span> <span data-ttu-id="c543b-115">ターゲット サーバーは、ジョブを完了した後、マスター サーバーに再接続してジョブのステータスをレポートします。</span><span class="sxs-lookup"><span data-stu-id="c543b-115">After the target server completes the job, it reconnects to the master server and reports the status of the job.</span></span>  
  
 <span data-ttu-id="c543b-116">次の図は、マスター サーバーとターゲット サーバーの関係を示します。</span><span class="sxs-lookup"><span data-stu-id="c543b-116">The following illustration shows the relationship between master and target servers:</span></span>  
  
 <span data-ttu-id="c543b-117">![マルチサーバー管理構成](../../database-engine/media/multisvr.gif "マルチサーバー管理構成")</span><span class="sxs-lookup"><span data-stu-id="c543b-117">![Multiserver administration configuration](../../database-engine/media/multisvr.gif "Multiserver administration configuration")</span></span>  
  
 <span data-ttu-id="c543b-118">大企業の複数の部門別サーバーを管理する場合は、次のアイテムを定義できます。</span><span class="sxs-lookup"><span data-stu-id="c543b-118">If you administer departmental servers across a large corporation, you can define the following:</span></span>  
  
-   <span data-ttu-id="c543b-119">複数のジョブ ステップから構成される 1 つのバックアップ ジョブ</span><span class="sxs-lookup"><span data-stu-id="c543b-119">One backup job with job steps.</span></span>  
  
-   <span data-ttu-id="c543b-120">バックアップ エラーが発生した場合に通知するオペレーター</span><span class="sxs-lookup"><span data-stu-id="c543b-120">Operators to notify in case of backup failure.</span></span>  
  
-   <span data-ttu-id="c543b-121">バックアップ ジョブの実行スケジュール</span><span class="sxs-lookup"><span data-stu-id="c543b-121">An execution schedule for the backup job.</span></span>  
  
 <span data-ttu-id="c543b-122">マスター サーバーにこのバックアップ ジョブを 1 回書き込んでから、各部門別サーバーをターゲット サーバーとして登録します。</span><span class="sxs-lookup"><span data-stu-id="c543b-122">Write this backup job one time on the master server and then enlist each departmental server as a target server.</span></span> <span data-ttu-id="c543b-123">この登録以降は、ジョブを一度しか定義しなくても、すべての部門別サーバーで同じバックアップ ジョブが実行されます。</span><span class="sxs-lookup"><span data-stu-id="c543b-123">From the time of their enlistment, all the departmental servers run the same backup job, yet you defined the job only once.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c543b-124">マルチサーバー管理機能は、sysadmin ロールのメンバーを対象としています。</span><span class="sxs-lookup"><span data-stu-id="c543b-124">Multiserver administration features are intended for members of the sysadmin role.</span></span> <span data-ttu-id="c543b-125">ただし、ターゲット サーバー上の sysadmin ロールのメンバーは、マスター サーバーから、ターゲット サーバーで実行される操作を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="c543b-125">However, a member of the sysadmin role on the target server cannot edit the operations that are performed on the target server by the master server.</span></span> <span data-ttu-id="c543b-126">このセキュリティ措置によって、ジョブ ステップが誤って削除されたり、ターゲット サーバー上の操作が中断したりすることを防止できます。</span><span class="sxs-lookup"><span data-stu-id="c543b-126">This security measure prevents job steps from being accidentally deleted and operations on the target server from being interrupted.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c543b-127">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="c543b-127">In This Section</span></span>  
 [<span data-ttu-id="c543b-128">マルチサーバー環境の作成</span><span class="sxs-lookup"><span data-stu-id="c543b-128">Create a Multiserver Environment</span></span>](create-a-multiserver-environment.md)  
 <span data-ttu-id="c543b-129">マスター サーバーおよびターゲット サーバーを作成および管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c543b-129">Contains information about how to create and manage master and target servers.</span></span>  
  
 [<span data-ttu-id="c543b-130">マルチサーバー環境に適した SQL Server エージェント サービス アカウントの選択</span><span class="sxs-lookup"><span data-stu-id="c543b-130">Choose the Right SQL Server Agent Service Account for Multiserver Environments</span></span>](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md)  
 <span data-ttu-id="c543b-131">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェント サービスに管理者以外の Windows アカウントまたはローカル システム アカウントを使用することによる、マルチサーバー環境への影響について説明します。</span><span class="sxs-lookup"><span data-stu-id="c543b-131">Contains information about how using nonadministrative Windows accounts or the Local System account for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent service can affect multiserver environments.</span></span>  
  
 [<span data-ttu-id="c543b-132">ターゲット サーバーでの暗号化オプションの設定</span><span class="sxs-lookup"><span data-stu-id="c543b-132">Set Encryption Options on Target Servers</span></span>](set-encryption-options-on-target-servers.md)  
 <span data-ttu-id="c543b-133">ターゲット サーバーの MsxEncryptChannelOptions [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェントのレジストリ サブキーの設定について説明します。</span><span class="sxs-lookup"><span data-stu-id="c543b-133">Contains information about setting the MsxEncryptChannelOptions [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent registry subkey on target servers.</span></span>  
  
 [<span data-ttu-id="c543b-134">エンタープライズ全体におけるジョブの管理</span><span class="sxs-lookup"><span data-stu-id="c543b-134">Manage Jobs Across an Enterprise</span></span>](manage-jobs-across-an-enterprise.md)  
 <span data-ttu-id="c543b-135">ジョブ ステータスの確認、ジョブのターゲット サーバーの変更、ターゲット サーバーのクロックの同期、およびマスター サーバーの現在のジョブ ステータスに対するポーリングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c543b-135">Contains information about checking job status, changing target servers for jobs, synchronizing target server clocks, and polling master servers for their current job status.</span></span>  
  
 [<span data-ttu-id="c543b-136">プロキシを使用するマルチサーバー ジョブのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="c543b-136">Troubleshoot Multiserver Jobs That Use Proxies</span></span>](troubleshoot-multiserver-jobs-that-use-proxies.md)  
 <span data-ttu-id="c543b-137">プロキシを使用しているマルチサーバー ジョブに障害が発生した場合のトラブルシューティングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c543b-137">Contains information about troubleshooting multiserver jobs that use proxies which fail.</span></span>  
  
 [<span data-ttu-id="c543b-138">サーバーのポーリング</span><span class="sxs-lookup"><span data-stu-id="c543b-138">Poll Servers</span></span>](poll-servers.md)  
 <span data-ttu-id="c543b-139">ターゲット サーバーをマスター サーバーに明示的および暗黙的にポーリングして、ジョブ情報の同期をとる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c543b-139">Contains information about how to implicitly and explicitly make target servers poll master servers to synchronize jobs information.</span></span>  
  
 [<span data-ttu-id="c543b-140">イベントの管理</span><span class="sxs-lookup"><span data-stu-id="c543b-140">Manage Events</span></span>](manage-events.md)  
 <span data-ttu-id="c543b-141">ターゲット サーバーからマスター サーバーに転送されるイベントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c543b-141">Contains information about event forwarding from target servers to master servers.</span></span>  
  
 [<span data-ttu-id="c543b-142">企業全体の自動管理のチューニング</span><span class="sxs-lookup"><span data-stu-id="c543b-142">Tune Automated Administration Across an Enterprise</span></span>](tune-automated-administration-across-an-enterprise.md)  
 <span data-ttu-id="c543b-143">マルチサーバー環境で自動化された管理により [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]の自己チューニング機能を活用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c543b-143">Contains information about how automated administration in a multiserver environment takes advantage of the self-tuning features of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c543b-144">参照</span><span class="sxs-lookup"><span data-stu-id="c543b-144">See Also</span></span>  
 <span data-ttu-id="c543b-145">[SQL Server データベース エンジンの旧バージョンとの互換性](../../database-engine/sql-server-database-engine-backward-compatibility.md) </span><span class="sxs-lookup"><span data-stu-id="c543b-145">[SQL Server Database Engine Backward Compatibility](../../database-engine/sql-server-database-engine-backward-compatibility.md) </span></span>  
 <span data-ttu-id="c543b-146">[サーバーの登録](../register-servers/register-servers.md) </span><span class="sxs-lookup"><span data-stu-id="c543b-146">[Register Servers](../register-servers/register-servers.md) </span></span>  
 <span data-ttu-id="c543b-147">[sp_add_targetservergroup &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-targetservergroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c543b-147">[sp_add_targetservergroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-targetservergroup-transact-sql) </span></span>  
 <span data-ttu-id="c543b-148">[sp_delete_targetserver &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-targetserver-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c543b-148">[sp_delete_targetserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-targetserver-transact-sql) </span></span>  
 <span data-ttu-id="c543b-149">[sp_delete_targetservergroup &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-targetservergroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c543b-149">[sp_delete_targetservergroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-targetservergroup-transact-sql) </span></span>  
 <span data-ttu-id="c543b-150">[sp_help_downloadlist &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-downloadlist-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c543b-150">[sp_help_downloadlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-downloadlist-transact-sql) </span></span>  
 <span data-ttu-id="c543b-151">[sp_help_jobserver &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobserver-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c543b-151">[sp_help_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobserver-transact-sql) </span></span>  
 <span data-ttu-id="c543b-152">[sp_help_targetservergroup &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-targetservergroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c543b-152">[sp_help_targetservergroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-targetservergroup-transact-sql) </span></span>  
 <span data-ttu-id="c543b-153">[sp_resync_targetserver &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c543b-153">[sp_resync_targetserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql) </span></span>  
 <span data-ttu-id="c543b-154">[sp_update_targetservergroup &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-targetservergroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c543b-154">[sp_update_targetservergroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-targetservergroup-transact-sql) </span></span>  
 <span data-ttu-id="c543b-155">[dbo.sysjobservers &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/dbo-sysjobservers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c543b-155">[dbo.sysjobservers &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobservers-transact-sql) </span></span>  
 <span data-ttu-id="c543b-156">[Transact-sql&#41;&#40;のログインのsys.sys](/sql/relational-databases/system-compatibility-views/sys-syslogins-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c543b-156">[sys.syslogins &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-syslogins-transact-sql) </span></span>  
 [<span data-ttu-id="c543b-157">dbo.systargetservers &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="c543b-157">dbo.systargetservers &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-tables/dbo-systargetservers-transact-sql)  
  
  
