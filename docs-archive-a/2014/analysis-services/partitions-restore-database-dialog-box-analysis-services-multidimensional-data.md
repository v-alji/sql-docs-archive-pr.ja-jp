---
title: '[パーティション] ([データベースの復元] ダイアログボックス) (Analysis Services 多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.restoredbdialog.partitions.f1
ms.assetid: 1ad4dde5-4651-4069-875c-7ab73cd8b4f4
author: minewiskan
ms.author: owend
ms.openlocfilehash: b54ac204cd09651a933f1c53c7780fc96ae1bfb6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644187"
---
# <a name="partitions-restore-database-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="17627-102">[パーティション] ([データベースの復元] ダイアログ ボックス) (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="17627-102">Partitions (Restore Database Dialog Box) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="17627-103">**の** [データベースの復元] **ダイアログ ボックスの** [パーティション] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ページを使用すると、ローカル パーティションを復元する場所の指定、リモート パーティションを復元するかどうかの指定、リモート パーティションを復元する際に使用するリモート バックアップ ファイルの指定ができます。</span><span class="sxs-lookup"><span data-stu-id="17627-103">Use the **Partitions** page of the **Restore Database** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to specify the location to restore local partitions, and to specify whether to restore remote partitions and the remote backup files to use when restoring remote partitions.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="17627-104">バックアップ ファイルごとに、復元コマンドを実行するユーザーは、各ファイルに指定されたバックアップ場所から読み取る権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="17627-104">For each backup file, the user who runs the restore command must have permission to read from the backup location specified for each file.</span></span> <span data-ttu-id="17627-105">サーバーにインストールされていない [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースを復元する場合、ユーザーは、その [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスのサーバー ロールのメンバーであることも必要です。</span><span class="sxs-lookup"><span data-stu-id="17627-105">To restore an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database that is not installed on the server, the user must also be a member of the server role for that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="17627-106">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースを上書きするには、ユーザーは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスのサーバー ロールのメンバーか、復元するデータベースに対してフル コントロール (管理者) 権限を持つデータベース ロールのメンバーのいずれかである必要があります。</span><span class="sxs-lookup"><span data-stu-id="17627-106">To overwrite an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, the user must have one of the following roles: a member of the server role for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance, or a member of a database role with Full Control (Administrator) permissions on the database to be restored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="17627-107">既存のデータベースを復元すると、データベースを復元したユーザーは、復元されたデータベースにアクセスできなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="17627-107">After restoring an existing database, the user who restored the database might lose access to the restored database.</span></span> <span data-ttu-id="17627-108">バックアップの実行時に、ユーザーがサーバー ロールのメンバー、またはフル コントロール (管理者) 権限を持つデータベース ロールのメンバーではなかった場合、このようにアクセスできなくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="17627-108">This loss of access can occur if, at the time that the backup was performed, the user was not a member of the server role or was not a member of the database role with Full Control (Administrator) permissions.</span></span>  
  
 <span data-ttu-id="17627-109">**[データベースの復元] ダイアログボックスに [パーティション] ページを表示するには**</span><span class="sxs-lookup"><span data-stu-id="17627-109">**To display the Partitions page in the Restore Database dialog box**</span></span>  
  
-   <span data-ttu-id="17627-110">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]の **オブジェクト エクスプローラー** で、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスの **[データベース]** フォルダー、またはデータベースを右クリックし、 **[データベースの復元]** をクリックします。次に、 **[ページの選択]** で **[パーティション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="17627-110">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], right-click either the **Databases** folder of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance or a database in **Object Explorer**, click **Restore**, and then under **Select a page**, click **Partitions**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="17627-111">Options</span><span class="sxs-lookup"><span data-stu-id="17627-111">Options</span></span>  
 <span data-ttu-id="17627-112">**スクリプト**</span><span class="sxs-lookup"><span data-stu-id="17627-112">**Script**</span></span>  
 <span data-ttu-id="17627-113">ダイアログ ボックスで選択したオプションに基づいた復元スクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="17627-113">Creates a restore script that is based on the options selected in the dialog box.</span></span> <span data-ttu-id="17627-114">復元用スクリプトは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] スクリプト言語 (ASSL) で記述されています。</span><span class="sxs-lookup"><span data-stu-id="17627-114">The restore script is written in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Scripting Language (ASSL).</span></span>  
  
 <span data-ttu-id="17627-115">**[スクリプト]** アイコンをクリックすると、既定では、新しいクエリ ウィンドウに復元スクリプトが送信されます。</span><span class="sxs-lookup"><span data-stu-id="17627-115">Clicking the **Script** icon sends the restore script into a new query window, by default.</span></span>  
  
 <span data-ttu-id="17627-116">**[スクリプト]** の矢印をクリックすると、復元スクリプトの送信先を次の中から選択できるメニューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="17627-116">Clicking the **Script** arrow displays a menu that allows you to choose where to send the restore script:</span></span>  
  
-   <span data-ttu-id="17627-117">新しいクエリ ウィンドウ (既定)。</span><span class="sxs-lookup"><span data-stu-id="17627-117">To a new query window (default).</span></span>  
  
-   <span data-ttu-id="17627-118">ファイル。</span><span class="sxs-lookup"><span data-stu-id="17627-118">To a file.</span></span>  
  
-   <span data-ttu-id="17627-119">クリップボード。</span><span class="sxs-lookup"><span data-stu-id="17627-119">To the clipboard.</span></span>  
  
-   <span data-ttu-id="17627-120">ジョブ。</span><span class="sxs-lookup"><span data-stu-id="17627-120">To a job.</span></span>  
  
 <span data-ttu-id="17627-121">**[元の場所に復元する]**</span><span class="sxs-lookup"><span data-stu-id="17627-121">**Restore to original locations**</span></span>  
 <span data-ttu-id="17627-122">選択すると、バックアップ ファイルに保存されているローカル パーティションを元の場所に復元します。</span><span class="sxs-lookup"><span data-stu-id="17627-122">Select to restore local partitions contained in the backup file to their original locations.</span></span>  
  
 <span data-ttu-id="17627-123">**[別の場所を選択する]**</span><span class="sxs-lookup"><span data-stu-id="17627-123">**Select different locations**</span></span>  
 <span data-ttu-id="17627-124">ローカル パーティションの復元先として別の場所を指定する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="17627-124">Select to specify different locations in which to restore local partitions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="17627-125">ローカル パーティションにキューブ内の既定の場所以外の場所が指定されている場合にのみ、そのパーティションの復元フォルダーを変更できます。</span><span class="sxs-lookup"><span data-stu-id="17627-125">You can only change the restoration folder of a local partition if a location other than the default location was specified for that partition in the cube.</span></span>  
  
 <span data-ttu-id="17627-126">このオプションを選択した場合、次のグリッドが有効になります。これを使用して、各ローカル パーティションの復元フォルダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="17627-126">The following grid, enabled when this option is selected, is used to specify a restoration folder for each local partition:</span></span>  
  
|<span data-ttu-id="17627-127">列</span><span class="sxs-lookup"><span data-stu-id="17627-127">Column</span></span>|<span data-ttu-id="17627-128">説明</span><span class="sxs-lookup"><span data-stu-id="17627-128">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="17627-129">**Cube**</span><span class="sxs-lookup"><span data-stu-id="17627-129">**Cube**</span></span>|<span data-ttu-id="17627-130">ローカル パーティションが含まれているキューブの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="17627-130">Displays the name of the cube that contains the local partition.</span></span>|  
|<span data-ttu-id="17627-131">**MeasureGroup**</span><span class="sxs-lookup"><span data-stu-id="17627-131">**MeasureGroup**</span></span>|<span data-ttu-id="17627-132">ローカル パーティションが含まれているメジャー グループの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="17627-132">Displays the name of the measure group that contains the local partition.</span></span>|  
|<span data-ttu-id="17627-133">**パーティション**</span><span class="sxs-lookup"><span data-stu-id="17627-133">**Partition**</span></span>|<span data-ttu-id="17627-134">ローカル パーティションの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="17627-134">Displays the name of the local partition.</span></span>|  
|<span data-ttu-id="17627-135">**[サイズ (MB)]**</span><span class="sxs-lookup"><span data-stu-id="17627-135">**Size (MB)**</span></span>|<span data-ttu-id="17627-136">ローカル パーティションのサイズ (MB) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="17627-136">Displays the size, in megabytes, of the local partition.</span></span>|  
|<span data-ttu-id="17627-137">**[元のフォルダー]**</span><span class="sxs-lookup"><span data-stu-id="17627-137">**Original Folder**</span></span>|<span data-ttu-id="17627-138">ローカル パーティションが収められていた元のフォルダーの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="17627-138">Displays the name of the original folder in which the local partition was stored.</span></span>|  
|<span data-ttu-id="17627-139">**[復元フォルダー]**</span><span class="sxs-lookup"><span data-stu-id="17627-139">**Restoration Folder**</span></span>|<span data-ttu-id="17627-140">ローカル パーティションの復元フォルダーの名前を入力するか、参照ボタン (**[...]**) をクリックして **[リモート フォルダーの参照]** ダイアログ ボックスを表示し、使用するフォルダーのパスを選択します。</span><span class="sxs-lookup"><span data-stu-id="17627-140">Type the name of the restoration folder for the local partition, or click the ellipsis button (**...**) to display the **Browse for Remote Folder** dialog box and select the path of the folder to use.</span></span> <span data-ttu-id="17627-141">**[リモート フォルダーの参照]** ダイアログ ボックスの詳細については、「[[リモート フォルダーの参照] ダイアログ ボックス &#40;Analysis Services - 多次元データ&#41;](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17627-141">For more information about the **Browse for Remote Folder** dialog box, see [Browse for Remote Folder Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md).</span></span>|  
  
 <span data-ttu-id="17627-142">**[リモート パーティションを復元する]**</span><span class="sxs-lookup"><span data-stu-id="17627-142">**Restore remote partitions**</span></span>  
 <span data-ttu-id="17627-143">選択すると、リモート バックアップ ファイルに保存されているリモート パーティションを復元します。</span><span class="sxs-lookup"><span data-stu-id="17627-143">Select to restore remote partitions stored in remote backup files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="17627-144">バックアップ ファイルにリモート パーティションへの参照が含まれている場合にのみ、このオプションが有効になります。</span><span class="sxs-lookup"><span data-stu-id="17627-144">This option is enabled only if the backup file contains references to remote partitions.</span></span>  
  
 <span data-ttu-id="17627-145">このオプションを選択した場合、次のグリッドが有効になります。これを使用して、各ローカル パーティションの復元フォルダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="17627-145">The following grid, enabled when this option is selected, is used to specify a restoration folder for each local partition:</span></span>  
  
|<span data-ttu-id="17627-146">列</span><span class="sxs-lookup"><span data-stu-id="17627-146">Column</span></span>|<span data-ttu-id="17627-147">説明</span><span class="sxs-lookup"><span data-stu-id="17627-147">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="17627-148">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="17627-148">**Server**</span></span>|<span data-ttu-id="17627-149">リモート パーティションを管理する [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="17627-149">Displays the name of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance that manages the remote partition.</span></span>|  
|<span data-ttu-id="17627-150">**データ ソース**</span><span class="sxs-lookup"><span data-stu-id="17627-150">**Data Source**</span></span>|<span data-ttu-id="17627-151">バックアップ ファイル内のデータ ソースの名前が表示されます。これは、リモート パーティションを含むデータベースを表します。</span><span class="sxs-lookup"><span data-stu-id="17627-151">Displays the name of the data source in the backup file that represents the database that contains the remote partition.</span></span>|  
|<span data-ttu-id="17627-152">**バックアップファイル**</span><span class="sxs-lookup"><span data-stu-id="17627-152">**Backup File**</span></span>|<span data-ttu-id="17627-153">使用するリモート バックアップ ファイルの完全なパスとファイル名を入力するか、参照ボタン (**[...]**) をクリックして **[データベース ファイルの検索]** ダイアログ ボックスを表示し、使用するリモート バックアップ ファイルのパスとファイル名を選択します。</span><span class="sxs-lookup"><span data-stu-id="17627-153">Type the full path and file name of the remote backup file to use, or click the ellipsis button (**...**) to display the **Locate Database Files** dialog box and select the path and file name of the remote backup file to use.</span></span> <span data-ttu-id="17627-154">**[データベース ファイルの検索]** ダイアログ ボックスの詳細については、「[[データベース ファイルの検索] ダイアログ ボックス (Analysis Services - 多次元データ)](locate-database-files-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17627-154">For more information about the **Locate Database Files** dialog box, see [Locate Database Files Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](locate-database-files-dialog-box-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="17627-155">**...**</span><span class="sxs-lookup"><span data-stu-id="17627-155">**...**</span></span>|<span data-ttu-id="17627-156">クリックすると、**[リモート パーティション - 詳細設定]** ダイアログ ボックスが表示され、リモート パーティションの復元に使用するデータ ソースの接続文字列などの詳細なオプションを変更できます。</span><span class="sxs-lookup"><span data-stu-id="17627-156">Click to display the **Remote Partitions - Advanced Settings** dialog box and modify advanced options, such as the connection string for the data source, for restoring the remote partition.</span></span> <span data-ttu-id="17627-157">**[リモート パーティション - 詳細設定]** ダイアログ ボックスの詳細については、「[[リモート パーティション - 詳細設定] ダイアログ ボックス (Analysis Services - 多次元データ)](remote-partitions-advanced-settings-dialog-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17627-157">For more information about the **Remote Partitions - Advanced Settings** dialog box, see [Remote Partitions - Advanced Settings Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](remote-partitions-advanced-settings-dialog-analysis-services-multidimensional-data.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="17627-158">参照</span><span class="sxs-lookup"><span data-stu-id="17627-158">See Also</span></span>  
 <span data-ttu-id="17627-159">[[データベースの復元] ダイアログボックス &#40;Analysis Services-多次元データ&#41;](restore-database-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="17627-159">[Restore Database Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](restore-database-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="17627-160">[[全般 &#40;[データベースの復元] ダイアログボックス&#41; &#40;Analysis Services-多次元データ&#41;](general-restore-database-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="17627-160">[General &#40;Restore Database Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](general-restore-database-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="17627-161">Analysis Services データベースのバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="17627-161">Backup and Restore of Analysis Services Databases</span></span>](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
