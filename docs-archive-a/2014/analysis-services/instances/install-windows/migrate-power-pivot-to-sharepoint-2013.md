---
title: PowerPivot から SharePoint への移行 2013 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: f698ceb1-d53e-4717-a3a0-225b346760d0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1e59c6d6553cc9c43155b059fedf4eb6e124ca55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713598"
---
# <a name="migrate-powerpivot-to-sharepoint-2013"></a><span data-ttu-id="16933-102">SharePoint 2013 への PowerPivot の移行</span><span class="sxs-lookup"><span data-stu-id="16933-102">Migrate PowerPivot to SharePoint 2013</span></span>


 <span data-ttu-id="16933-103">SharePoint 2013 では、インプレース アップグレードはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="16933-103">SharePoint 2013 does not support in-place upgrade.</span></span> <span data-ttu-id="16933-104">ただし、**データベースアタッチアップグレードの手順はサポートされて**います。</span><span class="sxs-lookup"><span data-stu-id="16933-104">However the procedure of **database-attach upgrade is supported**.</span></span> <span data-ttu-id="16933-105">インプレース アップグレードとデータベース アタッチ アップグレードの 2 つの基本的なアップグレード方法をユーザーが選択できた SharePoint 2010 へのアップグレードとは動作が異なります。</span><span class="sxs-lookup"><span data-stu-id="16933-105">The behavior is different from upgrading to SharePoint 2010, where a customer could choose between the two basic upgrade approaches, in-place upgrade and database-attach upgrade.</span></span>

 <span data-ttu-id="16933-106">SharePoint 2010 と統合された [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] のインストールを使用している場合は、SharePoint サーバーのインプレース アップグレードを行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="16933-106">If you have a [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] installation integrated with SharePoint 2010, you cannot upgrade in-place the SharePoint server.</span></span> <span data-ttu-id="16933-107">ただし、SharePoint 2010 ファームから SharePoint 2013 ファームにコンテンツ データベースとサービス アプリケーション データベースを移行することは可能です。</span><span class="sxs-lookup"><span data-stu-id="16933-107">However you can migrate content databases and service application databases from the SharePoint 2010 farm to a SharePoint 2013 farm.</span></span> <span data-ttu-id="16933-108">このトピックでは、データベース アタッチ アップグレードを完了し、PowerPivot に関連する移行を完了するために必要な手順の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="16933-108">This topic is an overview of the steps required to complete a database-attach upgrade and complete a migration related to PowerPivot:</span></span>

 <span data-ttu-id="16933-109">**[!INCLUDE[applies](../../../includes/applies-md.md)]** SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="16933-109">**[!INCLUDE[applies](../../../includes/applies-md.md)]**  SharePoint 2013</span></span>

### <a name="migration-overview"></a><span data-ttu-id="16933-110">移行の概要</span><span class="sxs-lookup"><span data-stu-id="16933-110">Migration Overview</span></span>

|<span data-ttu-id="16933-111">1</span><span class="sxs-lookup"><span data-stu-id="16933-111">1</span></span>|<span data-ttu-id="16933-112">2</span><span class="sxs-lookup"><span data-stu-id="16933-112">2</span></span>|<span data-ttu-id="16933-113">3</span><span class="sxs-lookup"><span data-stu-id="16933-113">3</span></span>|<span data-ttu-id="16933-114">4</span><span class="sxs-lookup"><span data-stu-id="16933-114">4</span></span>|
|-------|-------|-------|-------|
|<span data-ttu-id="16933-115">SharePoint 2013 ファームを準備する</span><span class="sxs-lookup"><span data-stu-id="16933-115">Prepare the SharePoint 2013 farm</span></span>|<span data-ttu-id="16933-116">データベースをバックアップ、コピー、および復元する</span><span class="sxs-lookup"><span data-stu-id="16933-116">Backup, copy, restore databases.</span></span>|<span data-ttu-id="16933-117">コンテンツ データベースをマウントする</span><span class="sxs-lookup"><span data-stu-id="16933-117">Mount content databases</span></span>|<span data-ttu-id="16933-118">[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] のスケジュールを移行する</span><span class="sxs-lookup"><span data-stu-id="16933-118">Migrate [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] Schedules</span></span>|
||[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]|<span data-ttu-id="16933-119">SharePoint サーバーの全体管理</span><span class="sxs-lookup"><span data-stu-id="16933-119">SharePoint Central Administration</span></span><br /><br /> <span data-ttu-id="16933-120">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="16933-120">Windows PowerShell</span></span>|<span data-ttu-id="16933-121">SharePoint アプリケーション ページ</span><span class="sxs-lookup"><span data-stu-id="16933-121">SharePoint application Pages</span></span><br /><br /> <span data-ttu-id="16933-122">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="16933-122">Windows PowerShell</span></span>|

 <span data-ttu-id="16933-123">**このトピックの内容:**</span><span class="sxs-lookup"><span data-stu-id="16933-123">**In this topic:**</span></span>

-   [<span data-ttu-id="16933-124">1) SharePoint 2013 ファームを準備する</span><span class="sxs-lookup"><span data-stu-id="16933-124">1) Prepare the SharePoint 2013 Farm</span></span>](#bkmk_prepare_sharepoint2013)

-   [<span data-ttu-id="16933-125">2) データベースをバックアップ、コピー、および復元する</span><span class="sxs-lookup"><span data-stu-id="16933-125">2) Backup, Copy, Restore the Databases</span></span>](#bkmk_backup_restore)

-   [<span data-ttu-id="16933-126">3) Web アプリケーションを準備して、コンテンツ データベースをマウントする</span><span class="sxs-lookup"><span data-stu-id="16933-126">3) Prepare Web Applications and Mount Content Databases</span></span>](#bkmk_prepare_mount_databases)

-   [<span data-ttu-id="16933-127">4) PowerPivot のスケジュールをアップグレードする</span><span class="sxs-lookup"><span data-stu-id="16933-127">4) Upgrade PowerPivot Schedules</span></span>](#bkmk_upgrade_powerpivot_schedules)

-   [<span data-ttu-id="16933-128">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="16933-128">Additional Resources</span></span>](#bkmk_additional_resources)

##  <a name="1-prepare-the-sharepoint-2013-farm"></a><a name="bkmk_prepare_sharepoint2013"></a><span data-ttu-id="16933-129">1) SharePoint 2013 ファームを準備する</span><span class="sxs-lookup"><span data-stu-id="16933-129">1) Prepare the SharePoint 2013 Farm</span></span>

1.  > [!TIP]
    >  <span data-ttu-id="16933-130">既存の Web アプリケーション用に構成されている認証方法を確認します。</span><span class="sxs-lookup"><span data-stu-id="16933-130">Review the authentication method your existing web applications are configured for.</span></span> <span data-ttu-id="16933-131">SharePoint 2013 Web アプリケーションの既定値は、要求ベースの認証です。</span><span class="sxs-lookup"><span data-stu-id="16933-131">SharePoint 2013 web applications default to claims-based authentication.</span></span> <span data-ttu-id="16933-132">クラシック モード認証用に構成された SharePoint 2010 Web アプリケーションでは、SharePoint 2010 から SharePoint 2013 にデータベースを移行する追加の手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="16933-132">SharePoint 2010 web applications configured for classic-mode authentication require additional steps to migrate databases from SharePoint 2010 to SharePoint 2013.</span></span> <span data-ttu-id="16933-133">Web アプリケーションがクラシック モード認証用に構成されている場合は、SharePoint 2013 のドキュメントを確認してください。</span><span class="sxs-lookup"><span data-stu-id="16933-133">If your web applications are configured for classic-mode authentication, review the SharePoint 2013 documentation.</span></span>

2.  <span data-ttu-id="16933-134">新しい SharePoint Server 2013 ファームをインストールします。</span><span class="sxs-lookup"><span data-stu-id="16933-134">Install a new SharePoint Server 2013 farm.</span></span>

3.  <span data-ttu-id="16933-135">サーバーのインスタンスを [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] SharePoint モードでインストールします。</span><span class="sxs-lookup"><span data-stu-id="16933-135">Install an instance of a [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server in SharePoint mode.</span></span> <span data-ttu-id="16933-136">詳しくは、「 [PowerPivot for SharePoint 2013 Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="16933-136">For more information, see [PowerPivot for SharePoint 2013 Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode).</span></span>

4.  <span data-ttu-id="16933-137">SharePoint ファーム内の各サーバーで [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 2013 のインストール パッケージ **spPowerPivot.msi** を実行します。</span><span class="sxs-lookup"><span data-stu-id="16933-137">Run the [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 2013 installation package **spPowerPivot.msi** on each server in the SharePoint farm.</span></span> <span data-ttu-id="16933-138">詳細については、「 [SharePoint 2013&#41;&#40;PowerPivot for SharePoint アドインをインストールまたはアンインストールする](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16933-138">For more information, see [Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013).</span></span>

5.  <span data-ttu-id="16933-139">SharePoint 2013 サーバーの全体管理で、前の手順で作成した SharePoint モードの [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サーバーを使用するように Excel Services サービス アプリケーションを構成します。</span><span class="sxs-lookup"><span data-stu-id="16933-139">In SharePoint 2013 Central Administration, configure the Excel Services service application to use the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] SharePoint mode server created in the previous step.</span></span> <span data-ttu-id="16933-140">詳細については、「 [PowerPivot for SharePoint 2013 インストール](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode)」の「基本的な Analysis Services SharePoint 統合の構成」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="16933-140">For more information, see the "Configure Basic Analysis Services SharePoint Integration" section of [PowerPivot for SharePoint 2013 Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode).</span></span>

##  <a name="2-backup-copy-restore-the-databases"></a><a name="bkmk_backup_restore"></a><span data-ttu-id="16933-141">2) データベースをバックアップ、コピー、復元する</span><span class="sxs-lookup"><span data-stu-id="16933-141">2) Backup, Copy, Restore the Databases</span></span>
 <span data-ttu-id="16933-142">"SharePoint のデータベースアタッチアップグレード" プロセスは、PowerPivot 関連のコンテンツとサービスアプリケーションデータベースを SharePoint 2013 ファームにバックアップ、コピー、および復元する一連の手順です。</span><span class="sxs-lookup"><span data-stu-id="16933-142">The "SharePoint database-attach upgrade" process is a sequence of steps to back up, copy, and restore PowerPivot related content and service application databases to the SharePoint 2013 farm.</span></span>

1.  <span data-ttu-id="16933-143">**データベースを読み取り専用に設定する** : [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]で、データベース名を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16933-143">**Set Database to read-only:** In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], right-click the database name and click **Properties**.</span></span> <span data-ttu-id="16933-144">**[オプション]** ページで、 **[読み取り専用データベース]** プロパティを **[True]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="16933-144">On the **Options** page, set the **Database read-Only** property to **True**.</span></span>

2.  <span data-ttu-id="16933-145">**バックアップする** : SharePoint 2013 ファームに移行する各コンテンツ データベースとサービス アプリケーション データベースをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="16933-145">**Back up:** Back up each content database and service application database that you want to migrate to the SharePoint 2013 farm.</span></span> <span data-ttu-id="16933-146">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]で、データベース名を右クリックし、 **[タスク]**、 **[バックアップ]** を順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="16933-146">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], right-click the database name, click **Tasks**, and click **Back up**.</span></span>

3.  <span data-ttu-id="16933-147">データベース バックアップ ファイル (.bak) をバックアップ先サーバーにファイル コピーします。</span><span class="sxs-lookup"><span data-stu-id="16933-147">File copy the database backup files (.bak) to the desired destination server.</span></span>

4.  <span data-ttu-id="16933-148">**復元する** : データベースを復元先の [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]に復元します。</span><span class="sxs-lookup"><span data-stu-id="16933-148">**Restore:** Restore the databases to the destination [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="16933-149">この手順は、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]を使用して行うことができます。</span><span class="sxs-lookup"><span data-stu-id="16933-149">This step can be completed using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>

5.  <span data-ttu-id="16933-150">**データベースを読み取り/書き込み用に設定する** : **[読み取り専用データベース]** を **[False]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="16933-150">**Set Database to read-write:** Set the **Database read-Only** to **False**.</span></span>

##  <a name="3-prepare-web-applications-and-mount-content-databases"></a><a name="bkmk_prepare_mount_databases"></a><span data-ttu-id="16933-151">3) Web アプリケーションを準備し、コンテンツデータベースをマウントする</span><span class="sxs-lookup"><span data-stu-id="16933-151">3) Prepare Web Applications and Mount Content Databases</span></span>
 <span data-ttu-id="16933-152">次の手順の詳細については、「 [sharepoint 2010 から sharepoint 2013 にデータベースをアップグレードする](https://go.microsoft.com/fwlink/p/?LinkId=256690)」 (を参照してください https://go.microsoft.com/fwlink/p/?LinkId=256690) 。</span><span class="sxs-lookup"><span data-stu-id="16933-152">For a more detailed explanation of the following procedures, see [Upgrade databases from SharePoint 2010 to SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256690) (https://go.microsoft.com/fwlink/p/?LinkId=256690).</span></span>

1.  <span data-ttu-id="16933-153">**データベースをオフラインにする**</span><span class="sxs-lookup"><span data-stu-id="16933-153">**Take Databases Offline:**</span></span>

     <span data-ttu-id="16933-154">SharePoint サーバーの全体管理を使用して、SharePoint 2013 の各コンテンツ データベースをオフラインにします。</span><span class="sxs-lookup"><span data-stu-id="16933-154">Take each SharePoint 2013 content database offline, using SharePoint Central Administration.</span></span> <span data-ttu-id="16933-155">コンテンツ データベースを、コピーしたデータベースに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="16933-155">The content databases are replaced by the databases you copied over.</span></span> <span data-ttu-id="16933-156">使用環境にとってどのシーケンスが最適かを検討してください。</span><span class="sxs-lookup"><span data-stu-id="16933-156">Consider what is the best sequence for your environment.</span></span> <span data-ttu-id="16933-157">次のコンテンツ データベースをオフラインにする前に、各データベースをオフラインにして、関連する置換データベースをマウントすることを検討します。</span><span class="sxs-lookup"><span data-stu-id="16933-157">Consider taking each database offline and mount its relevant replacement database before taking the next content database offline.</span></span> <span data-ttu-id="16933-158">もう 1 つの方法として、すべてのコンテンツ データベースをグループとしてオフラインにします。</span><span class="sxs-lookup"><span data-stu-id="16933-158">Another option is to take all the content databases offline as a group.</span></span>

    1.  <span data-ttu-id="16933-159">SharePoint サーバーの全体管理で、 **[アプリケーション構成の管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16933-159">In SharePoint Central Administration, click **Application Management**.</span></span>

    2.  <span data-ttu-id="16933-160">**[コンテンツ データベースの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16933-160">Click **Manage Content Databases**.</span></span>

    3.  <span data-ttu-id="16933-161">データベース名をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16933-161">Click the name of the database.</span></span>

    4.  <span data-ttu-id="16933-162">**[コンテンツ データベース設定の管理]** で、 **[データベースの状態]** を **[オフライン]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="16933-162">On the **Manage Content Database Settings**, set **Database status** to **Offline**.</span></span>

    5.  <span data-ttu-id="16933-163">**[コンテンツ データベースの削除]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="16933-163">Select **Remove Content Database**.</span></span> <span data-ttu-id="16933-164">コンテンツ データベースに格納されているサイトにアクセスできなくなるという警告に注意してください。</span><span class="sxs-lookup"><span data-stu-id="16933-164">Note the warning that sites stored in the content database will no longer be accessible.</span></span>

-   <span data-ttu-id="16933-165">**コンテンツ データベースをマウントする:**</span><span class="sxs-lookup"><span data-stu-id="16933-165">**Mount content databases:**</span></span>

     <span data-ttu-id="16933-166">移行したコンテンツ データベースをマウントするには、SharePoint 2013 管理シェルで PowerShell コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="16933-166">Use PowerShell cmdlets in the SharePoint 2013 Management shell to mount the migrated content database.</span></span> <span data-ttu-id="16933-167">サービスアプリケーションデータベースは、コンテンツデータベースのみをマウントする必要はありません。 ![PowerShell 関連コンテンツ](../../../reporting-services/media/rs-powershellicon.jpg "PowerShell 関連コンテンツ")</span><span class="sxs-lookup"><span data-stu-id="16933-167">The service application database does not need to be mounted, only the content databases: ![PowerShell related content](../../../reporting-services/media/rs-powershellicon.jpg "PowerShell related content")</span></span>

    ```powershell
    Mount-SPContentDatabase "SharePoint_Content_O14-KJSP1" -DatabaseServer "[server name]\powerpivot" -WebApplication [web application URL]
    ```

     <span data-ttu-id="16933-168">詳細については、「[コンテンツデータベースを接続またはデタッチする (SharePoint Server 2010)](https://technet.microsoft.com/library/ff628582.aspx) 」 (「」を参照してください https://technet.microsoft.com/library/ff628582.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="16933-168">For more information, see [Attach or detach content databases (SharePoint Server 2010)](https://technet.microsoft.com/library/ff628582.aspx) (https://technet.microsoft.com/library/ff628582.aspx).</span></span>

     <span data-ttu-id="16933-169">**手順の完了後の状態**  : マウント操作が完了すると、前のコンテンツ データベースに格納されていたファイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="16933-169">**Status when the step is complete:**  When the mount operation is complete, users can see files that were in the old content database.</span></span> <span data-ttu-id="16933-170">そのため、ユーザーはドキュメント ライブラリのブックを表示して開くことができます。</span><span class="sxs-lookup"><span data-stu-id="16933-170">Therefore users can see and open the workbooks in the document library.</span></span>

    > [!TIP]
    >  <span data-ttu-id="16933-171">移行したブックの新しいスケジュールは、移行プロセスのこの時点で作成することができます。</span><span class="sxs-lookup"><span data-stu-id="16933-171">It is possible at this point in the migration process to create new schedules for the migrated workbooks.</span></span> <span data-ttu-id="16933-172">ただし、スケジュールは、前の SharePoint ファームからコピーしたデータベースではなく、新しい [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] サービス アプリケーション データベースで作成されるため、</span><span class="sxs-lookup"><span data-stu-id="16933-172">However, the schedules are created in the new [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] service application database, and not the database you copied from the old SharePoint farm.</span></span> <span data-ttu-id="16933-173">古いスケジュールは含められません。</span><span class="sxs-lookup"><span data-stu-id="16933-173">Therefore it will not contain any of the old schedules.</span></span> <span data-ttu-id="16933-174">前のデータベースを使用して古いスケジュールを移行する次の手順を完了すると、新しいスケジュールは使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="16933-174">After you complete the following steps to use the old database and migrate the old schedules, the new schedules are not available.</span></span>

### <a name="troubleshoot-issues-when-you-attempt-to-mount-databases"></a><span data-ttu-id="16933-175">データベースをマウントしようとすると発生する問題のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="16933-175">Troubleshoot issues when you attempt to mount databases</span></span>
 <span data-ttu-id="16933-176">ここでは、データベースをマウントするときに発生する可能性のある問題についてまとめます。</span><span class="sxs-lookup"><span data-stu-id="16933-176">This section summarizes possible issues encountered when mounting the database.</span></span>

1.  <span data-ttu-id="16933-177">**認証エラー** : 認証関連のエラーが発生する場合は、元の Web アプリケーションで使用している認証モードを確認します。</span><span class="sxs-lookup"><span data-stu-id="16933-177">**Authentication errors:** If you see errors related to authentication, review what authentication mode the source web applications are using.</span></span> <span data-ttu-id="16933-178">エラーは、SharePoint 2013 と SharePoint 2010 の Web アプリケーション間の認証の不一致によって発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="16933-178">The error could be caused by a mismatch in authentication between the SharePoint 2013 web application and the SharePoint 2010 web application.</span></span> <span data-ttu-id="16933-179">詳細については、「 [1) SharePoint 2013 ファームを準備する](#bkmk_prepare_sharepoint2013) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16933-179">See the [1) Prepare the SharePoint 2013 Farm](#bkmk_prepare_sharepoint2013) for more information.</span></span>

2.  <span data-ttu-id="16933-180">**PowerPivot ファイルの不足:** PowerPivot の .dll ファイルの不足に関連するエラーが発生する場合は、 **spPowerPivot.msi** がインストールされていないか、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 構成ツールを使用して PowerPivot が構成されていません。</span><span class="sxs-lookup"><span data-stu-id="16933-180">**Missing PowerPivot.Files:** If you see errors related to missing PowerPivot .dlls, the **spPowerPivot.msi** has not been installed or the [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] Configuration Tool has not been used to configure PowerPivot.</span></span>

##  <a name="4-upgrade-powerpivot-schedules"></a><a name="bkmk_upgrade_powerpivot_schedules"></a><span data-ttu-id="16933-181">4) PowerPivot のスケジュールをアップグレードする</span><span class="sxs-lookup"><span data-stu-id="16933-181">4) Upgrade PowerPivot Schedules</span></span>
 <span data-ttu-id="16933-182">ここでは、PowerPivot のスケジュールの移行に関する詳細とオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="16933-182">This section describes the details and options for migrating PowerPivot schedules.</span></span> <span data-ttu-id="16933-183">スケジュールを移行するには、2 つの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="16933-183">Schedule migration is a two-step process.</span></span> <span data-ttu-id="16933-184">まず、移行したサービス アプリケーション データベースを使用するように PowerPivot サービス アプリケーションを構成し、</span><span class="sxs-lookup"><span data-stu-id="16933-184">First configure the PowerPivot service application to use the migrated service application database.</span></span> <span data-ttu-id="16933-185">次に、スケジュールを移行する 2 つの方法のうちいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="16933-185">Second, choose one of two options for schedule migration.</span></span>

 <span data-ttu-id="16933-186">**移行したサービス アプリケーション データベースを使用するようにサービス アプリケーションを構成する**</span><span class="sxs-lookup"><span data-stu-id="16933-186">**Configure the service application to use the migrated service application database.**</span></span>

 <span data-ttu-id="16933-187">SharePoint サーバーの全体管理で、コピーした前のサービス アプリケーション データベースを使用するように PowerPivot サービス アプリケーションを構成します。</span><span class="sxs-lookup"><span data-stu-id="16933-187">In SharePoint Central Administration to configure the PowerPivot services application to use the old service application database you copied over.</span></span> <span data-ttu-id="16933-188">PowerPivot サービスによって、サービス アプリケーション データベースが新しいスキーマにアップグレードされます。</span><span class="sxs-lookup"><span data-stu-id="16933-188">The PowerPivot Service upgrades the service application database to the new schema.</span></span>

1.  <span data-ttu-id="16933-189">SharePoint サーバーの全体管理で **[サービス アプリケーションの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16933-189">In SharePoint Central Administration, click **Manage Service Applications**.</span></span>

2.  <span data-ttu-id="16933-190">PowerPivot サービスアプリケーション ("既定の PowerPivot サービスアプリケーション" など) を探し、サービスアプリケーションの名前をクリックし、SharePoint リボンで [**プロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16933-190">Find the PowerPivot service application, for example "Default PowerPivot Service Application", click the name of the service application and click **Properties** in the SharePoint ribbon.</span></span>

3.  <span data-ttu-id="16933-191">データベース サーバーの名前付きインスタンスとデータベース名を、</span><span class="sxs-lookup"><span data-stu-id="16933-191">Update the database server name-instance and the database name.</span></span> <span data-ttu-id="16933-192">バックアップ、コピー、および復元したデータベースの正しい名前に更新します。</span><span class="sxs-lookup"><span data-stu-id="16933-192">To the correct names for the database you backed up, copied, and restored.</span></span> <span data-ttu-id="16933-193">**[OK]** をクリックすると、サービス アプリケーション データベースがアップグレードされます。</span><span class="sxs-lookup"><span data-stu-id="16933-193">Once you click **Ok**, the service application database is upgraded.</span></span> <span data-ttu-id="16933-194">エラーは ULS ログに格納されます。</span><span class="sxs-lookup"><span data-stu-id="16933-194">Errors will be in the ULS log.</span></span>

 <span data-ttu-id="16933-195">**PowerPivot のスケジュールをアップグレードする**</span><span class="sxs-lookup"><span data-stu-id="16933-195">**Upgrade PowerPivot schedules**</span></span>

 <span data-ttu-id="16933-196">更新スケジュールを移行するには、PowerPivot サービス アプリケーションを構成します。</span><span class="sxs-lookup"><span data-stu-id="16933-196">Configure the PowerPivot service application to migrate refresh schedules.</span></span>

-   <span data-ttu-id="16933-197">**スケジュールを移行するオプション 1: SharePoint ファームの管理者**</span><span class="sxs-lookup"><span data-stu-id="16933-197">**Migrate Schedules option1: SharePoint farm administrator**</span></span>

    1.  <span data-ttu-id="16933-198">SharePoint 2013 管理で、スイッチを使用してコマンドレットを実行し、 `Set-PowerPivotServiceApplication` `-StartMigratingRefreshSchedules` オンデマンドでの自動移行![PowerShell 関連コンテンツ](../../../reporting-services/media/rs-powershellicon.jpg "PowerShell 関連コンテンツ")を有効にします。</span><span class="sxs-lookup"><span data-stu-id="16933-198">In the SharePoint 2013 Management Run the `Set-PowerPivotServiceApplication` cmdlet with the `-StartMigratingRefreshSchedules` switch to enable automatic on demand schedule migration ![PowerShell related content](../../../reporting-services/media/rs-powershellicon.jpg "PowerShell related content").</span></span> <span data-ttu-id="16933-199">次の Windows PowerShell スクリプトは、PowerPivot サービス アプリケーションが 1 つだけであることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="16933-199">The following Windows PowerShell script assumes that there is only one PowerPivot service application.</span></span>

        ```powershell
        $app = Get-PowerPivotServiceApplication
        Set-PowerPivotServiceApplication $app -StartMigratingRefreshSchedules
        ```

         <span data-ttu-id="16933-200">この Windows PowerShell スクリプトを実行すると、スケジュールがアクティブになり、次回の適切なタイミングで実行されるようになります。</span><span class="sxs-lookup"><span data-stu-id="16933-200">After the Windows PowerShell script is run, the schedules are active and the schedules will run at the next appropriate time.</span></span> <span data-ttu-id="16933-201">ただし、定期更新ページ上の状態は有効になりません。</span><span class="sxs-lookup"><span data-stu-id="16933-201">However, the status one the schedule refresh page is not enabled.</span></span> <span data-ttu-id="16933-202">スケジュールは初めて実行するときに移行され、定期更新ページで **[有効]**  が [True] に変わります。</span><span class="sxs-lookup"><span data-stu-id="16933-202">When the schedule runs the first time it will be migrated and on the schedule refresh page, **Enabled**  will be true.</span></span>

    2.  <span data-ttu-id="16933-203">StartMigratingRefreshSchedules プロパティの現在値を確認する場合は、次の PowerShell スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="16933-203">If you want to check the current value of the StartMigratingRefreshSchedules property, run the following PowerShell script.</span></span> <span data-ttu-id="16933-204">このスクリプトは、すべての PowerPivot サービス アプリケーション オブジェクトをループし、名前とプロパティ値を表示します。</span><span class="sxs-lookup"><span data-stu-id="16933-204">The Script loops through all PowerPivot service application objects and display the name and property values:</span></span>

        ```powershell
        $apps = Get-PowerPivotServiceApplication
        foreach ($app in $apps){ Get-PowerPivotServiceApplication $app | Format-Table -Property displayname, id, StartMigratingRefreshSchedules }
        ```

     <span data-ttu-id="16933-205">**スケジュールを移行するオプション 2: ユーザーが各ブックを更新する**</span><span class="sxs-lookup"><span data-stu-id="16933-205">**Migrate Schedules option2: User updates each workbook**</span></span>

    1.  <span data-ttu-id="16933-206">スケジュールを移行するもう 1 つの方法は、ブックごとに定期更新を有効にすることです。</span><span class="sxs-lookup"><span data-stu-id="16933-206">Another option to migrate schedules is to enable the schedule refresh for each workbook.</span></span> <span data-ttu-id="16933-207">ブックがあるドキュメント ライブラリに移動します。</span><span class="sxs-lookup"><span data-stu-id="16933-207">Navigate to the document library that contains the workbooks.</span></span>

    2.  <span data-ttu-id="16933-208">ショートカット メニューを開き、 **[PowerPivot のデータ更新の管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16933-208">Open the context menu and click **Manage PowerPivot Data Refresh**.</span></span>

    3.  <span data-ttu-id="16933-209">**[定期更新]** セクションで、 **[有効化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16933-209">In the **schedule refresh** section, click **Enable**.</span></span>

    4.  <span data-ttu-id="16933-210">**[さらに、できるだけ早く更新を行います]** を選択できます。</span><span class="sxs-lookup"><span data-stu-id="16933-210">You can select **Also refresh as soon as possible**.</span></span> <span data-ttu-id="16933-211">このオプションでは、[OK] をクリックするとすぐに更新のインスタンスが 1 つキューに追加されます。</span><span class="sxs-lookup"><span data-stu-id="16933-211">This option adds one instance of the refresh to the queue as soon as you click ok.</span></span> <span data-ttu-id="16933-212">通常の更新スケジュールも適切な時間にトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="16933-212">The regular refresh schedule still triggers at the appropriate time.</span></span>

    5.  <span data-ttu-id="16933-213">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16933-213">Click **Ok**.</span></span> <span data-ttu-id="16933-214">これで、更新ページに更新履歴が表示されるようになり、スケジュールは通常の時間に実行されます。</span><span class="sxs-lookup"><span data-stu-id="16933-214">The refresh history is now visible in the refresh page, the schedule will fire at the normal time.</span></span>

 <span data-ttu-id="16933-215">**SQL Server 2008 R2 PowerPivot ブック**</span><span class="sxs-lookup"><span data-stu-id="16933-215">**SQL Server 2008 R2 PowerPivot workbooks**</span></span>

-   <span data-ttu-id="16933-216">SQL Server 2008 R2 PowerPivot ブックを SQL Server 2012 SP1 PowerPivot for SharePoint 2013 で使用している場合は、自動的にはアップグレードされません。</span><span class="sxs-lookup"><span data-stu-id="16933-216">SQL Server 2008 R2 PowerPivot workbooks do not automatically upgrade when they are used in SQL Server 2012 SP1 PowerPivot for SharePoint 2013.</span></span> <span data-ttu-id="16933-217">2008 R2 ブックが格納されたコンテンツ データベースを移行すると、ブックを使用できるようにはなりますが、スケジュールはアップグレードされません。</span><span class="sxs-lookup"><span data-stu-id="16933-217">After you migrate a content database containing the 2008 R2 workbooks, you can use the workbooks but the schedules do not upgrade.</span></span>

-   <span data-ttu-id="16933-218">詳細については、「 [ブックのアップグレードと定期データ更新 &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16933-218">For more information, see [Upgrade Workbooks and Scheduled Data Refresh &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013).</span></span>

##  <a name="additional-resources"></a><a name="bkmk_additional_resources"></a> <span data-ttu-id="16933-219">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="16933-219">Additional Resources</span></span>

> [!NOTE]
>  <span data-ttu-id="16933-220">[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] および SharePoint データベース アタッチ アップグレードの詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16933-220">For more information on [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] and SharePoint database-attach upgrade, see the following:</span></span>

-   <span data-ttu-id="16933-221">[ブックのアップグレードと定期データ更新 &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013)</span><span class="sxs-lookup"><span data-stu-id="16933-221">[Upgrade Workbooks and Scheduled Data Refresh &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013).</span></span>

-   <span data-ttu-id="16933-222">[SharePoint 2013 へのアップグレードプロセスの概要](https://go.microsoft.com/fwlink/p/?LinkId=256688)( https://go.microsoft.com/fwlink/p/?LinkId=256688) .</span><span class="sxs-lookup"><span data-stu-id="16933-222">[Overview of the upgrade process to SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256688) (https://go.microsoft.com/fwlink/p/?LinkId=256688).</span></span>

-   <span data-ttu-id="16933-223">[SharePoint 2013 (にアップグレードする前に準備を整える](https://go.microsoft.com/fwlink/p/?LinkId=256689) https://go.microsoft.com/fwlink/p/?LinkId=256689) 。</span><span class="sxs-lookup"><span data-stu-id="16933-223">[Clean up preparations before an upgrade to SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256689) (https://go.microsoft.com/fwlink/p/?LinkId=256689).</span></span>

-   <span data-ttu-id="16933-224">[Sharepoint 2010 から sharepoint 2013 (にデータベースをアップグレード](https://go.microsoft.com/fwlink/p/?LinkId=256690) https://go.microsoft.com/fwlink/p/?LinkId=256690) します。</span><span class="sxs-lookup"><span data-stu-id="16933-224">[Upgrade databases from SharePoint 2010 to SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256690) (https://go.microsoft.com/fwlink/p/?LinkId=256690).</span></span>