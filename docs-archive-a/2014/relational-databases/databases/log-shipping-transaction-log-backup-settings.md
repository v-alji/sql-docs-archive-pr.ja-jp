---
title: '[トランザクション ログのバックアップの設定] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.logshipping.settings.tlogback.f1
ms.assetid: 9a6e6c16-7f71-412b-bba6-7bffac001277
author: stevestein
ms.author: sstein
ms.openlocfilehash: b5420f3032cd2477d23028a2e27c1ce89c4e0525
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742182"
---
# <a name="log-shipping-transaction-log-backup-settings"></a><span data-ttu-id="a777f-102">[トランザクション ログのバックアップの設定]</span><span class="sxs-lookup"><span data-stu-id="a777f-102">Log Shipping Transaction Log Backup Settings</span></span>
  <span data-ttu-id="a777f-103">このダイアログ ボックスを使用すると、ログ配布構成のトランザクション ログ バックアップ設定を構成および変更できます。</span><span class="sxs-lookup"><span data-stu-id="a777f-103">Use this dialog box to configure and modify the transaction log backup settings for a log shipping configuration.</span></span>  
  
 <span data-ttu-id="a777f-104">ログ配布の概念については、「 [ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a777f-104">For an explanation of log shipping concepts, see [About Log Shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="a777f-105">Options</span><span class="sxs-lookup"><span data-stu-id="a777f-105">Options</span></span>  
 <span data-ttu-id="a777f-106">**[バックアップ フォルダーのネットワーク パス (例: \\\\primaryserver\\backup)]**</span><span class="sxs-lookup"><span data-stu-id="a777f-106">**Network path to the backup folder**</span></span>  
 <span data-ttu-id="a777f-107">このボックスに、バックアップ フォルダーへのネットワーク共有を入力します。</span><span class="sxs-lookup"><span data-stu-id="a777f-107">Type the network share to your backup folder in this box.</span></span> <span data-ttu-id="a777f-108">トランザクション ログ バックアップが保存されるローカル フォルダーを共有することにより、ログ配布コピー ジョブでこれらのファイルをセカンダリ サーバーにコピーできます。</span><span class="sxs-lookup"><span data-stu-id="a777f-108">The local folder where your transaction log backups are saved must be shared so that the log shipping copy jobs can copy these files to the secondary server.</span></span> <span data-ttu-id="a777f-109">セカンダリ サーバー インスタンスでコピー ジョブを実行できるように、このネットワーク共有での読み取り権限をプロキシ アカウントに与えてください。</span><span class="sxs-lookup"><span data-stu-id="a777f-109">You must grant read permissions on this network share to the proxy account under which the copy job will run at the secondary server instance.</span></span> <span data-ttu-id="a777f-110">既定では、このアカウントは、セカンダリ サーバー インスタンスの SQLServer エージェント サービス アカウントですが、管理者はジョブに対して別のプロキシ アカウントを選択できます。</span><span class="sxs-lookup"><span data-stu-id="a777f-110">By default, this is the SQLServerAgent service account of the secondary server instance, but an administrator can choose another proxy account for the job.</span></span>  
  
 <span data-ttu-id="a777f-111">**[バックアップ フォルダーがプライマリ サーバーに存在する場合は、バックアップ フォルダーのローカル パスを入力 (例: c:\\backup)]**</span><span class="sxs-lookup"><span data-stu-id="a777f-111">**If the backup folder is located on the primary server, type the local path to the folder**</span></span>  
 <span data-ttu-id="a777f-112">バックアップ フォルダーがプライマリ サーバーにある場合は、ローカル ドライブ名およびバックアップ フォルダーへのパスを入力します。</span><span class="sxs-lookup"><span data-stu-id="a777f-112">Type the local drive letter and path to the backup folder if the backup folder is located on the primary server.</span></span> <span data-ttu-id="a777f-113">バックアップ フォルダーがプライマリ サーバーにない場合は、空白のままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="a777f-113">If the backup folder is not located on the primary server, you can leave this blank.</span></span>  
  
 <span data-ttu-id="a777f-114">ここにローカル パスを指定すると、BACKUP コマンドはこのパスを使用して、トランザクション ログ バックアップを作成します。ローカル パスを指定しなかった場合、BACKUP コマンドは **[バックアップ フォルダーのネットワーク パス (例: \\\\primaryserver\\backup)]** ボックスで指定されたネットワーク パスを使用します。</span><span class="sxs-lookup"><span data-stu-id="a777f-114">If you specify a local path here, the BACKUP command will use this path to create the transaction log backups; otherwise, if no local path is specified, the BACKUP command will use the network path specified in the **Network path to the backup folder** box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a777f-115">実行中の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントがプライマリ サーバーのローカル システム アカウントの場合は、バックアップ フォルダーをプライマリ サーバーに作成し、そのフォルダーのローカル パスをここに入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a777f-115">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account is running under the local system account on the primary server, you must create the backup folder on the primary server and specify the local path to that folder here.</span></span> <span data-ttu-id="a777f-116">プライマリ サーバー インスタンスの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントには、このフォルダーの読み取り権限と書き込み権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="a777f-116">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account of the primary server instance must have Read and Write permissions on this folder.</span></span>  
  
 <span data-ttu-id="a777f-117">**[次の期間を経過したファイルを削除する]**</span><span class="sxs-lookup"><span data-stu-id="a777f-117">**Delete files older than**</span></span>  
 <span data-ttu-id="a777f-118">トランザクション ログ バックアップを削除する前に、バックアップ ディレクトリに保持する期間を指定します。</span><span class="sxs-lookup"><span data-stu-id="a777f-118">Specify the length of time you want transaction log backups to remain in your backup directory before being deleted.</span></span>  
  
 <span data-ttu-id="a777f-119">**[バックアップが次の期間内に行われない場合は警告する]**</span><span class="sxs-lookup"><span data-stu-id="a777f-119">**Alert if no backup occurs within**</span></span>  
 <span data-ttu-id="a777f-120">トランザクション ログ バックアップが発生していないという警告を生成する前に、ログ配布が待機する期間を指定します。</span><span class="sxs-lookup"><span data-stu-id="a777f-120">Specify the amount of time you want log shipping to wait before raising an alert that no transaction log backups have occurred.</span></span>  
  
 <span data-ttu-id="a777f-121">**ジョブ名**</span><span class="sxs-lookup"><span data-stu-id="a777f-121">**Job name**</span></span>  
 <span data-ttu-id="a777f-122">ログ配布用のトランザクション ログ バックアップを作成する際に使用される SQL Server エージェント ジョブの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="a777f-122">Displays the name of the SQL Server Agent job that is used to create the transaction log backups for log shipping.</span></span> <span data-ttu-id="a777f-123">最初にジョブを作成するときに、ボックスに別の名前を入力して名前を変更できます。</span><span class="sxs-lookup"><span data-stu-id="a777f-123">When first creating the job, you can modify the name by typing in the box.</span></span>  
  
 <span data-ttu-id="a777f-124">**[スケジュール]**</span><span class="sxs-lookup"><span data-stu-id="a777f-124">**Schedule**</span></span>  
 <span data-ttu-id="a777f-125">プライマリ データベースのトランザクション ログのバックアップに関する現在のスケジュールを表示します。</span><span class="sxs-lookup"><span data-stu-id="a777f-125">Displays the current schedule for backing up the transaction logs of the primary database.</span></span> <span data-ttu-id="a777f-126">バックアップ ジョブが作成される前に、 **[スケジュール]** をクリックしてこのスケジュールを変更できます。バックアップ ジョブが作成された後は、 **[ジョブの編集]** をクリックしてこのスケジュールを変更できます。</span><span class="sxs-lookup"><span data-stu-id="a777f-126">Before the backup job has been created, You can modify this schedule by clicking **Schedule...**. After the job has been created, you can modify this schedule by clicking **Edit Job...**.</span></span>  
  
### <a name="backup-job"></a><span data-ttu-id="a777f-127">バックアップ ジョブ</span><span class="sxs-lookup"><span data-stu-id="a777f-127">Backup Job</span></span>  
 <span data-ttu-id="a777f-128">**[スケジュール]**</span><span class="sxs-lookup"><span data-stu-id="a777f-128">**Schedule...**</span></span>  
 <span data-ttu-id="a777f-129">SQL Server エージェント ジョブの作成時に作成されたスケジュールを変更します。</span><span class="sxs-lookup"><span data-stu-id="a777f-129">Modify the schedule that is created when the SQL Server Agent job is created.</span></span>  
  
 <span data-ttu-id="a777f-130">**[ジョブの編集]**</span><span class="sxs-lookup"><span data-stu-id="a777f-130">**Edit Job...**</span></span>  
 <span data-ttu-id="a777f-131">プライマリ データベースのトランザクション ログ バックアップを実行するジョブの SQL Server エージェント ジョブ パラメーターを変更します。</span><span class="sxs-lookup"><span data-stu-id="a777f-131">Modify the SQL Server Agent job parameters for the job that performs transaction log backups on the primary database.</span></span>  
  
 <span data-ttu-id="a777f-132">**[このジョブを無効にする]**</span><span class="sxs-lookup"><span data-stu-id="a777f-132">**Disable this job**</span></span>  
 <span data-ttu-id="a777f-133">SQL Server エージェント ジョブのトランザクション ログ バックアップ作成を無効にします。</span><span class="sxs-lookup"><span data-stu-id="a777f-133">Disable the SQL Server Agent job from creating transaction log backups.</span></span>  
  
### <a name="compression"></a><span data-ttu-id="a777f-134">圧縮</span><span class="sxs-lookup"><span data-stu-id="a777f-134">Compression</span></span>  
 [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="a777f-135">(またはそれ以降のバージョン) では、 [バックアップの圧縮](../backup-restore/backup-compression-sql-server.md)がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="a777f-135">(or a later version) supports [backup compression](../backup-restore/backup-compression-sql-server.md).</span></span>  
  
 <span data-ttu-id="a777f-136">**[バックアップの圧縮の設定]**</span><span class="sxs-lookup"><span data-stu-id="a777f-136">**Set backup compression**</span></span>  
 <span data-ttu-id="a777f-137">[!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (またはそれ以降のバージョン) で、このログ配布構成のログ バックアップについて、バックアップの圧縮の値を次の中から 1 つ選択します。</span><span class="sxs-lookup"><span data-stu-id="a777f-137">In [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (or a later version), select one the following backup compression values for the log backups of this log shipping configuration:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a777f-138">**[既定のサーバー設定を使用する]**</span><span class="sxs-lookup"><span data-stu-id="a777f-138">**Use the default server setting**</span></span>|<span data-ttu-id="a777f-139">オンにすると、サーバー レベルの既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a777f-139">Click to use the server-level default.</span></span><br /><br /> <span data-ttu-id="a777f-140">この既定値は、 **backup compression default** サーバー構成オプションで設定されます。</span><span class="sxs-lookup"><span data-stu-id="a777f-140">This default is set by the **backup compression default** server-configuration option.</span></span> <span data-ttu-id="a777f-141">このオプションの現在の設定を表示する方法については、「 [backup compression default サーバー構成オプションの表示または構成](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a777f-141">For information about how to view the current setting of this option, see [View or Configure the backup compression default Server Configuration Option](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).</span></span>|  
|<span data-ttu-id="a777f-142">**[バックアップを圧縮する]**</span><span class="sxs-lookup"><span data-stu-id="a777f-142">**Compress backup**</span></span>|<span data-ttu-id="a777f-143">オンにすると、サーバー レベルの既定値に関係なく、バックアップが圧縮されます。</span><span class="sxs-lookup"><span data-stu-id="a777f-143">Click to compress the backup, regardless of the server-level default.</span></span><br /><br /> <span data-ttu-id="a777f-144">**\*\* 重要 \*\*** 既定の設定では、圧縮によって CPU 使用率が著しく増加し、圧縮処理によって CPU がさらに消費されるために、同時に実行される操作が悪影響を受ける場合があります。</span><span class="sxs-lookup"><span data-stu-id="a777f-144">**\*\* Important \*\*** By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely impact concurrent operations.</span></span> <span data-ttu-id="a777f-145">このため、 [リソース ガバナー](../resource-governor/resource-governor.md)によって CPU 使用率が制限されるセッションで、優先度の低い圧縮バックアップを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="a777f-145">Therefore, you might want to create low-priority compressed backups in a session whose CPU usage is limited by the [Resource Governor](../resource-governor/resource-governor.md).</span></span> <span data-ttu-id="a777f-146">詳細については、「 [リソース ガバナーを使用してバックアップの圧縮による CPU 使用率を制限する方法 &#40;Transact-SQL&#41;](../backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a777f-146">For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](../backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).</span></span>|  
|<span data-ttu-id="a777f-147">**[バックアップを圧縮しない]**</span><span class="sxs-lookup"><span data-stu-id="a777f-147">**Do not compress backup**</span></span>|<span data-ttu-id="a777f-148">オンにすると、サーバー レベルの既定値に関係なく、圧縮されていないバックアップが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a777f-148">Click to create an uncompressed backup, regardless of the server-level default.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a777f-149">参照</span><span class="sxs-lookup"><span data-stu-id="a777f-149">See Also</span></span>  
 <span data-ttu-id="a777f-150">[SQL Server エージェント ジョブ ステップを作成および管理するユーザーの構成](../../ssms/agent/configure-a-user-to-create-and-manage-sql-server-agent-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="a777f-150">[Configure a User to Create and Manage SQL Server Agent Jobs](../../ssms/agent/configure-a-user-to-create-and-manage-sql-server-agent-jobs.md) </span></span>  
 [<span data-ttu-id="a777f-151">ログ配布について &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a777f-151">About Log Shipping &#40;SQL Server&#41;</span></span>](../../database-engine/log-shipping/about-log-shipping-sql-server.md)  
  
  
