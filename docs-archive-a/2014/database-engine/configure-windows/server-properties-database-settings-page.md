---
title: サーバーのプロパティ ([データベースの設定] ページ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.databasesettings.f1
ms.assetid: 1cebdbd3-cbfd-4a02-bba6-a5addf4e3ada
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3beb2b6aa9a34982cccdfb252941c1c779a16121
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738701"
---
# <a name="server-properties-database-settings-page"></a><span data-ttu-id="2fc3b-102">[サーバーのプロパティ] ([データベースの設定] ページ)</span><span class="sxs-lookup"><span data-stu-id="2fc3b-102">Server Properties (Database Settings Page)</span></span>
  <span data-ttu-id="2fc3b-103">このページを使用すると、データベースの設定を表示したり、変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-103">Use this page to view or modify your database settings.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2fc3b-104">Options</span><span class="sxs-lookup"><span data-stu-id="2fc3b-104">Options</span></span>  
 <span data-ttu-id="2fc3b-105">**[既定のインデックス FILL FACTOR]**</span><span class="sxs-lookup"><span data-stu-id="2fc3b-105">**Default index fill factor**</span></span>  
 <span data-ttu-id="2fc3b-106">既存のデータを使用して新しいインデックスを作成する際に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 全体で各ページを作成する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-106">Specifies how full [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should make each page when it creates a new index using existing data.</span></span> <span data-ttu-id="2fc3b-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では各ページを埋めるときにページの分割に時間がかかるため、FILL FACTOR で指定する割合はパフォーマンスに影響します。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-107">The fill factor affects performance because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must take time to split pages when they fill up.</span></span>  
  
 <span data-ttu-id="2fc3b-108">既定値は 0 です。有効な値の範囲は 0 ～ 100 です。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-108">The default value is 0; valid values range from 0 through 100.</span></span> <span data-ttu-id="2fc3b-109">FILL FACTOR が 0 または 100 の場合、クラスター化インデックスと完全なデータ ページ、および非クラスター化インデックスと完全なリーフ ページが作成されますが、インデックス ツリーの上位レベルにはスペースが少し残されます。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-109">A fill factor of 0 or 100 creates clustered indexes with full data pages and nonclustered indexes with full leaf pages, but it leaves some space within the upper level of the index tree.</span></span> <span data-ttu-id="2fc3b-110">FILL FACTOR 値 0 と 100 は、すべての面でまったく同じ結果になります。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-110">Fill factor values 0 and 100 are identical in all respects.</span></span>  
  
 <span data-ttu-id="2fc3b-111">FILL FACTOR の値を小さくすると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でのインデックスの作成時に充てん率の低いページが数多く作成されます。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-111">Small fill factor values cause [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to create indexes with pages that are not full.</span></span> <span data-ttu-id="2fc3b-112">各インデックスに必要な保存領域が大きくなりますが、以降の挿入に使用できる領域は大きくなり、ページ分割は不要になります。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-112">Each index takes more storage space, but there is more room for subsequent insertions without requiring page splits.</span></span>  
  
 <span data-ttu-id="2fc3b-113">**[ロードされるまで待つ]**</span><span class="sxs-lookup"><span data-stu-id="2fc3b-113">**Wait indefinitely**</span></span>  
 <span data-ttu-id="2fc3b-114">新しいバックアップ テープが用意されるまでの間、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がタイムアウトしないように指定します。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-114">Specifies that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will never time out while waiting for a new backup tape.</span></span>  
  
 <span data-ttu-id="2fc3b-115">**[一度だけ再試行する]**</span><span class="sxs-lookup"><span data-stu-id="2fc3b-115">**Try once**</span></span>  
 <span data-ttu-id="2fc3b-116">バックアップ テープが必要なときに使用できない場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がタイムアウトするように指定します。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-116">Specifies that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will time out if a backup tape is not available when needed.</span></span>  
  
 <span data-ttu-id="2fc3b-117">**[試行期間]**</span><span class="sxs-lookup"><span data-stu-id="2fc3b-117">**Try for minute(s)**</span></span>  
 <span data-ttu-id="2fc3b-118">指定された時間内にバックアップ テープが使用できなかった場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がタイムアウトするように指定します。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-118">Specifies that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will time out if a backup tape is not available within the period specified.</span></span>  
  
 <span data-ttu-id="2fc3b-119">**[バックアップ メディアの既定の保有期間 (日)]**</span><span class="sxs-lookup"><span data-stu-id="2fc3b-119">**Default backup media retention (in days)**</span></span>  
 <span data-ttu-id="2fc3b-120">データベースまたはトランザクション ログのバックアップに使用した各バックアップ メディアの保有期間を日数で指定します。ここで指定した日数は、システム全体での保有期間の既定値になります。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-120">Provides a system-wide default for the length of time to retain each backup medium after it has been used for a database or transaction log backup.</span></span> <span data-ttu-id="2fc3b-121">このオプションを利用して、指定した日数が経過するまでバックアップが上書きされないように保護できます。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-121">This option helps protect backups from being overwritten until the specified number of days has elapsed.</span></span>  
  
 <span data-ttu-id="2fc3b-122">**[バックアップを圧縮する]**</span><span class="sxs-lookup"><span data-stu-id="2fc3b-122">**Compress backup**</span></span>  
 <span data-ttu-id="2fc3b-123">[!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (またはそれ以降のバージョン) での、 **backup compression default** オプションの現在の設定を示します。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-123">In [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (or later versions), indicates the current setting of the **backup compression default** option.</span></span> <span data-ttu-id="2fc3b-124">このオプションによって、バックアップの圧縮についてのサーバー レベルの既定値が次のように決定されます。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-124">This option determines the server-level default for compressing backups, as follows:</span></span>  
  
-   <span data-ttu-id="2fc3b-125">**[バックアップを圧縮する]** チェック ボックスがオフの場合、既定では新しいバックアップは圧縮されません。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-125">If the **Compress backup** box is blank, new backups are uncompressed by default.</span></span>  
  
-   <span data-ttu-id="2fc3b-126">**[バックアップを圧縮する]** チェック ボックスがオンの場合、既定で新しいバックアップが圧縮されます。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-126">If the **Compress backup** box is checked, new backups are compressed by default.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="2fc3b-127">既定の設定では、圧縮によって CPU 使用率が著しく増加し、圧縮処理によって CPU がさらに消費されるために、同時に実行される操作が悪影響を受ける場合があります。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-127">By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely affect concurrent operations.</span></span> <span data-ttu-id="2fc3b-128">このため、 [リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)によって CPU 使用率が制限されるセッションでは、優先度の低い圧縮バックアップを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-128">Therefore, you might want to create low-priority compressed backups in a session whose CPU usage is limited by [Resource Governor](../../relational-databases/resource-governor/resource-governor.md).</span></span> <span data-ttu-id="2fc3b-129">詳細については、「 [リソース ガバナーを使用してバックアップの圧縮による CPU 使用率を制限する方法 &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-129">For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).</span></span>  
  
 <span data-ttu-id="2fc3b-130">**sysadmin** 固定サーバー ロールまたは **serveradmin** 固定サーバー ロールのメンバーである場合は、 **[バックアップを圧縮する]** ボックスをオンにして設定を変更できます。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-130">If you are a member of the **sysadmin** or **serveradmin** fixed server role, you can change the setting by clicking the **Compress backup** box.</span></span>  
  
 <span data-ttu-id="2fc3b-131">詳細については、「[backup compression default サーバー構成オプションの表示または構成](view-or-configure-the-backup-compression-default-server-configuration-option.md)」および「[バックアップの圧縮 &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-compression-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-131">For more information, see [View or Configure the backup compression default Server Configuration Option](view-or-configure-the-backup-compression-default-server-configuration-option.md) and [Backup Compression &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-compression-sql-server.md).</span></span>  
  
 <span data-ttu-id="2fc3b-132">**[復旧間隔 (分単位)]**</span><span class="sxs-lookup"><span data-stu-id="2fc3b-132">**Recovery interval (minutes)**</span></span>  
 <span data-ttu-id="2fc3b-133">データベースごとに、データベースの復旧にかける最長時間を分単位で設定します。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-133">Sets the maximum number of minutes per database to recover databases.</span></span> <span data-ttu-id="2fc3b-134">既定値は 0 です。0 の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]によって自動的に構成されます。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-134">The default is 0, indicating automatic configuration by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2fc3b-135">実際には、復旧時間が 1 分未満で、アクティブなデータベースのチェックポイントは約 1 分間隔になります。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-135">In practice, this means a recovery time of less than one minute and a checkpoint approximately every one minute for active databases.</span></span> <span data-ttu-id="2fc3b-136">詳細については、「 [recovery interval サーバー構成オプションの構成](configure-the-recovery-interval-server-configuration-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-136">For more information, see [Configure the recovery interval Server Configuration Option](configure-the-recovery-interval-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="2fc3b-137">**データ**</span><span class="sxs-lookup"><span data-stu-id="2fc3b-137">**Data**</span></span>  
 <span data-ttu-id="2fc3b-138">データ ファイルの既定の位置を指定します。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-138">Specifies the default location for data files.</span></span> <span data-ttu-id="2fc3b-139">参照ボタンをクリックして、新しい既定の位置を指定します。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-139">Click the browse button to navigate to a new default location.</span></span> <span data-ttu-id="2fc3b-140">変更内容を有効にするには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-140">Does not take effect until [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is restarted.</span></span>  
  
 <span data-ttu-id="2fc3b-141">**Log**</span><span class="sxs-lookup"><span data-stu-id="2fc3b-141">**Log**</span></span>  
 <span data-ttu-id="2fc3b-142">ログ ファイルの既定の位置を指定します。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-142">Specifies the default location for log files.</span></span> <span data-ttu-id="2fc3b-143">参照ボタンをクリックして、新しい既定の位置を指定します。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-143">Click the browse button to navigate to a new default location.</span></span> <span data-ttu-id="2fc3b-144">変更内容を有効にするには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-144">Does not take effect until [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is restarted.</span></span>  
  
 <span data-ttu-id="2fc3b-145">**[構成した値]**</span><span class="sxs-lookup"><span data-stu-id="2fc3b-145">**Configured Values**</span></span>  
 <span data-ttu-id="2fc3b-146">このペインの各オプションに構成されている値を表示します。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-146">Displays the configured values for the options on this pane.</span></span> <span data-ttu-id="2fc3b-147">これらの値を変更した場合は、 **[実行中の値]** をクリックして、変更後の値が反映されているかどうかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-147">If you change these values, click **Running Values** to see whether the changes have taken effect.</span></span> <span data-ttu-id="2fc3b-148">値が反映されていない場合、先に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを再指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-148">If they have not, the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be restated first.</span></span>  
  
 <span data-ttu-id="2fc3b-149">**[実行中の値]**</span><span class="sxs-lookup"><span data-stu-id="2fc3b-149">**Running Values**</span></span>  
 <span data-ttu-id="2fc3b-150">このペイン上のオプションの、現在実行中の値を表示します。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-150">View the currently running values for the options on this pane.</span></span> <span data-ttu-id="2fc3b-151">これらの値は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="2fc3b-151">These values are read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fc3b-152">参照</span><span class="sxs-lookup"><span data-stu-id="2fc3b-152">See Also</span></span>  
 <span data-ttu-id="2fc3b-153">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2fc3b-153">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="2fc3b-154">インデックスの FILL FACTOR の指定</span><span class="sxs-lookup"><span data-stu-id="2fc3b-154">Specify Fill Factor for an Index</span></span>](../../relational-databases/indexes/specify-fill-factor-for-an-index.md)  
  
  
