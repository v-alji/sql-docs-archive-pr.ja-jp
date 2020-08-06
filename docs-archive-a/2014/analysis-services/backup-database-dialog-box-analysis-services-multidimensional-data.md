---
title: '[データベースのバックアップ] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.Backup.f1
ms.assetid: 7811ce7d-6c37-4189-bfa6-ef36fb4932db
author: minewiskan
ms.author: owend
ms.openlocfilehash: 48cf094353c53213864dae656af94ae791442105
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633616"
---
# <a name="backup-database-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="15d2a-102">[データベースのバックアップ] ダイアログ ボックス (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="15d2a-102">Backup Database Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="15d2a-103">**の** [データベースのバックアップ] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ダイアログ ボックスを使用すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースを [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] バックアップ ファイル (.abf) 形式でバックアップ ファイルにバックアップできます。</span><span class="sxs-lookup"><span data-stu-id="15d2a-103">Use the **Backup Database** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to back up an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database to a backup file using the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Backup File (.abf) format.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="15d2a-104">バックアップ ファイルごとに、バックアップ コマンドを実行するユーザーは、各ファイルに指定されたバックアップ場所に対する書き込み権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="15d2a-104">For each backup file, the user who runs the backup command must have permission to write to the backup location specified for each file.</span></span> <span data-ttu-id="15d2a-105">また、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスのサーバー ロールのメンバーであるか、バックアップするデータベースに対してフル コントロール (管理者) 権限を持つデータベース ロールのメンバーであることが条件となります。</span><span class="sxs-lookup"><span data-stu-id="15d2a-105">Also, the user must have one of the following roles: a member of a server role for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance, or a member of a database role with Full Control (Administrator) permissions on the database to be backed up.</span></span>  
  
 <span data-ttu-id="15d2a-106">**[データベースのバックアップ] ダイアログ ボックスを表示するには**</span><span class="sxs-lookup"><span data-stu-id="15d2a-106">**To display the Backup Database dialog box**</span></span>  
  
-   <span data-ttu-id="15d2a-107">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]の **オブジェクト エクスプローラー** で、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスの **[データベース]** フォルダー、またはデータベースを右クリックし、 **[バックアップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15d2a-107">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], right-click either the **Databases** folder of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance or a database in **Object Explorer**, and then click **Backup**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="15d2a-108">Options</span><span class="sxs-lookup"><span data-stu-id="15d2a-108">Options</span></span>  
 <span data-ttu-id="15d2a-109">**スクリプト**</span><span class="sxs-lookup"><span data-stu-id="15d2a-109">**Script**</span></span>  
 <span data-ttu-id="15d2a-110">ダイアログ ボックスで選択したオプションに基づいたバックアップ スクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="15d2a-110">Creates a backup script that is based on the options selected in the dialog box.</span></span> <span data-ttu-id="15d2a-111">復元用スクリプトは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] スクリプト言語 (ASSL) で記述されています。</span><span class="sxs-lookup"><span data-stu-id="15d2a-111">The restore script is written in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Scripting Language (ASSL).</span></span>  
  
 <span data-ttu-id="15d2a-112">**[スクリプト]** アイコンをクリックすると、既定では、新しいクエリ ウィンドウにバックアップ スクリプトが送信されます。</span><span class="sxs-lookup"><span data-stu-id="15d2a-112">Clicking the **Script** icon sends the backup script into a new query window, by default.</span></span>  
  
 <span data-ttu-id="15d2a-113">**[スクリプト]** の矢印をクリックすると、バックアップ スクリプトの送信先を次の中から選択できるメニューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="15d2a-113">Clicking the **Script** arrow displays a menu that allows you to choose where to send the backup script:</span></span>  
  
-   <span data-ttu-id="15d2a-114">新しいクエリ ウィンドウ (既定)。</span><span class="sxs-lookup"><span data-stu-id="15d2a-114">To a new query window (default).</span></span>  
  
-   <span data-ttu-id="15d2a-115">ファイル。</span><span class="sxs-lookup"><span data-stu-id="15d2a-115">To a file.</span></span>  
  
-   <span data-ttu-id="15d2a-116">クリップボード。</span><span class="sxs-lookup"><span data-stu-id="15d2a-116">To the clipboard.</span></span>  
  
-   <span data-ttu-id="15d2a-117">ジョブ。</span><span class="sxs-lookup"><span data-stu-id="15d2a-117">To a job.</span></span>  
  
 <span data-ttu-id="15d2a-118">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="15d2a-118">**Database**</span></span>  
 <span data-ttu-id="15d2a-119">現在選択されている [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="15d2a-119">Displays the name of the currently selected [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="15d2a-120">**[バックアップ ファイル]**</span><span class="sxs-lookup"><span data-stu-id="15d2a-120">**Backup file**</span></span>  
 <span data-ttu-id="15d2a-121">使用するバックアップ ファイルの完全なパスとファイル名を入力します。</span><span class="sxs-lookup"><span data-stu-id="15d2a-121">Type the full path and file name of the backup file to use.</span></span>  
  
 <span data-ttu-id="15d2a-122">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="15d2a-122">**Browse**</span></span>  
 <span data-ttu-id="15d2a-123">クリックすると、**[ファイル名を付けて保存]** ダイアログ ボックスが表示され、使用するバックアップ ファイルのパスおよびファイル名を選択できます。</span><span class="sxs-lookup"><span data-stu-id="15d2a-123">Click to display the **Save File As** dialog box and select the path and file name of the backup file to use.</span></span> <span data-ttu-id="15d2a-124">**[ファイル名を付けて保存]** ダイアログ ボックスの詳細については、「[[ファイル名を付けて保存] ダイアログ ボックス (Analysis Services - 多次元データ)](save-file-as-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="15d2a-124">For more information about the **Save File As** dialog box, see [Save File As Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](save-file-as-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="15d2a-125">**[ファイルの上書きを許可する]**</span><span class="sxs-lookup"><span data-stu-id="15d2a-125">**Allow file overwrite**</span></span>  
 <span data-ttu-id="15d2a-126">選択すると、既存のバックアップ ファイル、またはリモート バックアップ ファイルが存在する場合にファイルが上書きされます。</span><span class="sxs-lookup"><span data-stu-id="15d2a-126">Select to overwrite an existing backup file or remote backup file, if one exists.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="15d2a-127"> このオプションが選択されていない状態で、 **[バックアップ ファイル]** に指定されたバックアップ ファイルまたは **[リモート バックアップ ファイル]** に指定されたリモート バックアップ ファイルが存在する場合は、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="15d2a-127">If this option is not selected and the backup file specified in **Backup file** or a remote backup file specified in **Remote backup file** exists, an error occurs.</span></span>  
  
 <span data-ttu-id="15d2a-128">**[圧縮を適用する]**</span><span class="sxs-lookup"><span data-stu-id="15d2a-128">**Apply compression**</span></span>  
 <span data-ttu-id="15d2a-129">選択すると、バックアップ ファイル (および指定された場合はリモート バックアップ ファイル) の内容が圧縮されます。</span><span class="sxs-lookup"><span data-stu-id="15d2a-129">Select to compress the contents of the backup file and, if specified, remote backup files.</span></span>  
  
 <span data-ttu-id="15d2a-130">**[バックアップ ファイルを暗号化する]**</span><span class="sxs-lookup"><span data-stu-id="15d2a-130">**Encrypt backup file**</span></span>  
 <span data-ttu-id="15d2a-131">選択すると、バックアップ ファイルは **[パスワード]** に指定されたパスワードを使用して暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="15d2a-131">Select to encrypt the backup file using the password supplied in **Password**.</span></span>  
  
 <span data-ttu-id="15d2a-132">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="15d2a-132">**Password**</span></span>  
 <span data-ttu-id="15d2a-133">バックアップ ファイル (および指定された場合はリモート バックアップ ファイル) を暗号化するときに使用するパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="15d2a-133">Type the password to use when encrypting the backup file and, if specified, remote backup files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="15d2a-134"> このオプションは、 **[バックアップ ファイルを暗号化する]** が選択されている場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="15d2a-134">This option is enabled only if **Encrypt backup file** is selected.</span></span>  
  
 <span data-ttu-id="15d2a-135">**パスワードの確認入力**</span><span class="sxs-lookup"><span data-stu-id="15d2a-135">**Confirm Password**</span></span>  
 <span data-ttu-id="15d2a-136">バックアップ ファイル (および指定された場合はリモート バックアップ ファイル) のパスワードを確認するために、 **[パスワード]** に入力したパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="15d2a-136">Type the password entered in **Password** to confirm the password for the backup file and, if specified, remote backup files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="15d2a-137"> このオプションは、 **[バックアップ ファイルを暗号化する]** が選択されている場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="15d2a-137">This option is enabled only if **Encrypt backup file** is selected.</span></span>  
  
 <span data-ttu-id="15d2a-138">**[リモート パーティションのバックアップを作成する]**</span><span class="sxs-lookup"><span data-stu-id="15d2a-138">**Backup remote partition(s)**</span></span>  
 <span data-ttu-id="15d2a-139">選択すると、リモート パーティションの位置情報およびデータをバックアップ ファイルに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="15d2a-139">Select to include location information and data for remote partitions in the backup file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="15d2a-140">このオプションは、現在選択されている [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースでリモート パーティションが使用されている場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="15d2a-140">This option is enabled only if the currently selected [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database uses remote partitions.</span></span>  
  
 <span data-ttu-id="15d2a-141">**[リモート パーティションのバックアップの場所]**</span><span class="sxs-lookup"><span data-stu-id="15d2a-141">**Remote partition backup location**</span></span>  
 <span data-ttu-id="15d2a-142">選択されているデータベースに関連付けられているリモート パーティションの位置と、リモート パーティションのデータおよびメタデータをバックアップするためのリモート バックアップ ファイルを表示します。</span><span class="sxs-lookup"><span data-stu-id="15d2a-142">Displays the location of remote partitions associated with the selected database, as well as the remote backup file used to back up the data and metadata for the remote partitions.</span></span> <span data-ttu-id="15d2a-143">次の列があります。</span><span class="sxs-lookup"><span data-stu-id="15d2a-143">The following columns are available:</span></span>  
  
|<span data-ttu-id="15d2a-144">列</span><span class="sxs-lookup"><span data-stu-id="15d2a-144">Column</span></span>|<span data-ttu-id="15d2a-145">説明</span><span class="sxs-lookup"><span data-stu-id="15d2a-145">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="15d2a-146">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="15d2a-146">**Server**</span></span>|<span data-ttu-id="15d2a-147">リモート パーティションを管理する [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスを表示します。</span><span class="sxs-lookup"><span data-stu-id="15d2a-147">Displays the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance that manages the remote partitions.</span></span>|  
|<span data-ttu-id="15d2a-148">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="15d2a-148">**Database**</span></span>|<span data-ttu-id="15d2a-149">リモート パーティションが格納されている [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースを表示します。</span><span class="sxs-lookup"><span data-stu-id="15d2a-149">Displays the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database that contains the remote partitions.</span></span>|  
|<span data-ttu-id="15d2a-150">**パーティション一覧**</span><span class="sxs-lookup"><span data-stu-id="15d2a-150">**Partition List**</span></span>|<span data-ttu-id="15d2a-151">**[データベース]** に表示されるデータベースに含まれているリモート パーティションの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="15d2a-151">Displays the list of remote partitions contained by the database displayed in **Database**.</span></span>|  
|<span data-ttu-id="15d2a-152">**[リモート バックアップ ファイル]**</span><span class="sxs-lookup"><span data-stu-id="15d2a-152">**Remote backup file**</span></span>|<span data-ttu-id="15d2a-153">使用するリモート バックアップ ファイルの完全なパスとファイル名を入力するか、**[...]** ボタンをクリックして **[ファイル名を付けて保存]** ダイアログ ボックスを表示し、使用するリモート バックアップ ファイルのパスとファイル名を選択します。</span><span class="sxs-lookup"><span data-stu-id="15d2a-153">Type the full path and file name of the remote backup file to use, or click the ellipsis button (**...**) to display the **Save File As** dialog box and select the path and file name of the remote backup file to use.</span></span> <span data-ttu-id="15d2a-154">**[ファイル名を付けて保存]** ダイアログ ボックスの詳細については、「[[ファイル名を付けて保存] ダイアログ ボックス (Analysis Services - 多次元データ)](save-file-as-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="15d2a-154">For more information about the **Save File As** dialog box, see [Save File As Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](save-file-as-dialog-box-analysis-services-multidimensional-data.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="15d2a-155">参照</span><span class="sxs-lookup"><span data-stu-id="15d2a-155">See Also</span></span>  
 <span data-ttu-id="15d2a-156">[多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="15d2a-156">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="15d2a-157">Analysis Services データベースのバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="15d2a-157">Backup and Restore of Analysis Services Databases</span></span>](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
