---
title: '[全般] ([データベースの復元] ダイアログボックス) (Analysis Services 多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.restoredbdialog.f1
ms.assetid: 319e7ef5-c9c7-4e50-8690-02a90aed006f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 25a49e17227fc2ed6b7b18d2e0964cd8812cbdcb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645244"
---
# <a name="general-restore-database-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="f7637-102">[全般] ([データベースの復元] ダイアログ ボックス) (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="f7637-102">General (Restore Database Dialog Box) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="f7637-103">**の** [データベースの復元] **ダイアログ ボックスの** [全般] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ページを使用すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースの復元に使用するバックアップ ファイルおよび全般設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f7637-103">Use the **General** page of the **Restore Database** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to specify the backup file and general settings to use when restoring an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f7637-104">バックアップ ファイルごとに、復元コマンドを実行するユーザーは、各ファイルに指定されたバックアップ場所から読み取る権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f7637-104">For each backup file, the user who runs the restore command must have permission to read from the backup location specified for each file.</span></span> <span data-ttu-id="f7637-105">サーバーにインストールされていない [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースを復元する場合、ユーザーは、その [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスのサーバー ロールのメンバーであることも必要です。</span><span class="sxs-lookup"><span data-stu-id="f7637-105">To restore an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database that is not installed on the server, the user must also be a member of the server role for that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="f7637-106">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースを上書きするには、ユーザーは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスのサーバー ロールのメンバーか、復元するデータベースに対してフル コントロール (管理者) 権限を持つデータベース ロールのメンバーのいずれかである必要があります。</span><span class="sxs-lookup"><span data-stu-id="f7637-106">To overwrite an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, the user must have one of the following roles: a member of the server role for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance, or a member of a database role with Full Control (Administrator) permissions on the database to be restored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f7637-107">既存のデータベースを復元すると、データベースを復元したユーザーは、復元されたデータベースにアクセスできなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f7637-107">After restoring an existing database, the user who restored the database might lose access to the restored database.</span></span> <span data-ttu-id="f7637-108">バックアップの実行時に、ユーザーがサーバー ロールのメンバー、またはフル コントロール (管理者) 権限を持つデータベース ロールのメンバーではなかった場合、このようにアクセスできなくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="f7637-108">This loss of access can occur if, at the time that the backup was performed, the user was not a member of the server role or was not a member of the database role with Full Control (Administrator) permissions.</span></span>  
  
 <span data-ttu-id="f7637-109">**[データベースの復元] ダイアログ ボックスで [全般] ページを表示するには**</span><span class="sxs-lookup"><span data-stu-id="f7637-109">**To display the General page in the Restore Database dialog box**</span></span>  
  
-   <span data-ttu-id="f7637-110">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]の **オブジェクト エクスプローラー** で、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスの **[データベース]** フォルダー、またはデータベースを右クリックし、 **[データベースの復元]** をクリックします。次に、 **[ページの選択]** で **[全般]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f7637-110">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], right-click either the **Databases** folder of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance or a database in **Object Explorer**, click **Restore**, and then under **Select a page**, click **General**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f7637-111">Options</span><span class="sxs-lookup"><span data-stu-id="f7637-111">Options</span></span>  
 <span data-ttu-id="f7637-112">**スクリプト**</span><span class="sxs-lookup"><span data-stu-id="f7637-112">**Script**</span></span>  
 <span data-ttu-id="f7637-113">ダイアログ ボックスで選択したオプションに基づいた復元スクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="f7637-113">Creates a restore script that is based on the options selected in the dialog box.</span></span> <span data-ttu-id="f7637-114">復元用スクリプトは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] スクリプト言語 (ASSL) で記述されています。</span><span class="sxs-lookup"><span data-stu-id="f7637-114">The restore script is written in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Scripting Language (ASSL).</span></span>  
  
 <span data-ttu-id="f7637-115">**[スクリプト]** アイコンをクリックすると、既定では、新しいクエリ ウィンドウに復元スクリプトが送信されます。</span><span class="sxs-lookup"><span data-stu-id="f7637-115">Clicking the **Script** icon sends the restore script into a new query window, by default.</span></span>  
  
 <span data-ttu-id="f7637-116">**[スクリプト]** の矢印をクリックすると、復元スクリプトの送信先を次の中から選択できるメニューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f7637-116">Clicking the **Script** arrow displays a menu that allows you to choose where to send the restore script:</span></span>  
  
-   <span data-ttu-id="f7637-117">新しいクエリ ウィンドウ (既定)。</span><span class="sxs-lookup"><span data-stu-id="f7637-117">To a new query window (default).</span></span>  
  
-   <span data-ttu-id="f7637-118">ファイル。</span><span class="sxs-lookup"><span data-stu-id="f7637-118">To a file.</span></span>  
  
-   <span data-ttu-id="f7637-119">クリップボード。</span><span class="sxs-lookup"><span data-stu-id="f7637-119">To the clipboard.</span></span>  
  
-   <span data-ttu-id="f7637-120">ジョブ。</span><span class="sxs-lookup"><span data-stu-id="f7637-120">To a job.</span></span>  
  
 <span data-ttu-id="f7637-121">**データベースの復元**</span><span class="sxs-lookup"><span data-stu-id="f7637-121">**Restore database**</span></span>  
 <span data-ttu-id="f7637-122">復元する [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="f7637-122">Select the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database to restore.</span></span>  
  
 <span data-ttu-id="f7637-123">**復元元のバックアップ ファイル**</span><span class="sxs-lookup"><span data-stu-id="f7637-123">**From backup file**</span></span>  
 <span data-ttu-id="f7637-124">選択された [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースの復元元のバックアップ ファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="f7637-124">Select the backup file from which to restore the selected [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="f7637-125">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="f7637-125">**Browse**</span></span>  
 <span data-ttu-id="f7637-126">クリックすると、**[データベース ファイルの検索]** ダイアログ ボックスが表示され、使用するバックアップ ファイルのパスおよびファイル名を選択できます。</span><span class="sxs-lookup"><span data-stu-id="f7637-126">Click to display the **Locate Database Files** dialog box and select the path and file name of the backup file to use.</span></span> <span data-ttu-id="f7637-127">**[データベース ファイルの検索]** ダイアログ ボックスの詳細については、「[[データベース ファイルの検索] ダイアログ ボックス (Analysis Services - 多次元データ)](locate-database-files-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f7637-127">For more information about the **Locate Database Files** dialog box, see [Locate Database Files Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](locate-database-files-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="f7637-128">**[データベースの上書きを許可する]**</span><span class="sxs-lookup"><span data-stu-id="f7637-128">**Allow database overwrite**</span></span>  
 <span data-ttu-id="f7637-129">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] でこのオプションを選択すると、指定した [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベース内の既存のオブジェクトを、指定のバックアップ ファイルの内容に戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="f7637-129">Select to allow [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to restore the contents of the selected backup file over any existing objects in the selected [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="f7637-130">**[セキュリティ情報を含める]**</span><span class="sxs-lookup"><span data-stu-id="f7637-130">**Include security information**</span></span>  
 <span data-ttu-id="f7637-131">バックアップ ファイルに格納されたすべてのセキュリティ情報を [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースにコピーする場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="f7637-131">Select to copy any security information stored in the backup file to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="f7637-132">このオプションを選択すると有効になるドロップダウン リストで、セキュリティ情報の量を選択できます。</span><span class="sxs-lookup"><span data-stu-id="f7637-132">If this option is selected, you can choose the amount of security information from the drop-down list enabled by selecting this option.</span></span> <span data-ttu-id="f7637-133">次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f7637-133">The following options are available:</span></span>  
  
|<span data-ttu-id="f7637-134">オプション</span><span class="sxs-lookup"><span data-stu-id="f7637-134">Option</span></span>|<span data-ttu-id="f7637-135">説明</span><span class="sxs-lookup"><span data-stu-id="f7637-135">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="f7637-136">**[すべてコピー]**</span><span class="sxs-lookup"><span data-stu-id="f7637-136">**Copy All**</span></span>|<span data-ttu-id="f7637-137">バックアップ ファイルに格納されたデータベース ロール、およびロールに関連付けられたユーザー アカウントを復元します。</span><span class="sxs-lookup"><span data-stu-id="f7637-137">Restores the database roles contained in the backup file, as well as the user accounts associated with the roles.</span></span>|  
|<span data-ttu-id="f7637-138">**メンバーシップのスキップ**</span><span class="sxs-lookup"><span data-stu-id="f7637-138">**Skip Membership**</span></span>|<span data-ttu-id="f7637-139">バックアップ ファイルに格納されたデータベース ロールを復元しますが、ロールに関連付けられたユーザー アカウントは復元しません。</span><span class="sxs-lookup"><span data-stu-id="f7637-139">Restores the database roles contained in the backup file, but does not restore the user accounts associated with the roles.</span></span>|  
  
 <span data-ttu-id="f7637-140">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="f7637-140">**Password**</span></span>  
 <span data-ttu-id="f7637-141">バックアップ ファイルが暗号化されている場合は、バックアップ ファイルの暗号化に使用されたパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="f7637-141">If the backup file is encrypted, type the password used to encrypt the backup file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7637-142">参照</span><span class="sxs-lookup"><span data-stu-id="f7637-142">See Also</span></span>  
 <span data-ttu-id="f7637-143">[[データベースの復元] ダイアログボックス &#40;Analysis Services-多次元データ&#41;](restore-database-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="f7637-143">[Restore Database Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](restore-database-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="f7637-144">[パーティション &#40;[データベースの復元] ダイアログボックス&#41; &#40;Analysis Services-多次元データ&#41;](partitions-restore-database-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="f7637-144">[Partitions &#40;Restore Database Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](partitions-restore-database-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="f7637-145">Analysis Services データベースのバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="f7637-145">Backup and Restore of Analysis Services Databases</span></span>](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
