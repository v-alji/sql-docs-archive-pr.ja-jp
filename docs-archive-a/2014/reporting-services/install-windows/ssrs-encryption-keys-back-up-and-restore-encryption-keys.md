---
title: Reporting Services の暗号化キーのバックアップと復元 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- backing up encryption keys [Reporting Services]
- restoring encryption keys [Reporting Services]
- encryption keys [Reporting Services]
- symmetric keys [Reporting Services]
ms.assetid: 6773d5df-03ef-4781-beb7-9f6825bac979
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c8e7e61f58632898fc6150210598a671157639a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742942"
---
# <a name="back-up-and-restore-reporting-services-encryption-keys"></a><span data-ttu-id="3760a-102">Reporting Services の暗号化キーのバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="3760a-102">Back Up and Restore Reporting Services Encryption Keys</span></span>
  <span data-ttu-id="3760a-103">レポート サーバー構成で重要なのは、機密情報の暗号化に使用される対称キーのバックアップ コピーの作成です。</span><span class="sxs-lookup"><span data-stu-id="3760a-103">An important part of report server configuration is creating a backup copy of the symmetric key used for encrypting sensitive information.</span></span> <span data-ttu-id="3760a-104">キーのバックアップ コピーは多くのルーチン処理で必要とされ、キーのバックアップ コピーにより新しいインストールで既存のレポート サーバー データベースを再利用できます。</span><span class="sxs-lookup"><span data-stu-id="3760a-104">A backup copy of the key is required for many routine operations, and enables you to reuse an existing report server database in a new installation.</span></span>  
  
 <span data-ttu-id="3760a-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モード | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モード</span><span class="sxs-lookup"><span data-stu-id="3760a-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native Mode | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>  
  
 <span data-ttu-id="3760a-106">次のいずれかが行われた場合、暗号化キーのバックアップ コピーを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3760a-106">It is necessary to restore the backup copy of the encryption key when any of the following events occur:</span></span>  
  
-   <span data-ttu-id="3760a-107">レポート サーバー Windows サービスのアカウント名の変更またはパスワードの再設定。</span><span class="sxs-lookup"><span data-stu-id="3760a-107">Changing the Report Server Windows service account name or resetting the password.</span></span> <span data-ttu-id="3760a-108">Reporting Services 構成マネージャーを使用する際に、サービス アカウント名の変更操作の一部としてキーをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="3760a-108">When you use the Reporting Services Configuration Manager, backing up the key is part of a service account name change operation.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3760a-109">パスワードの再設定はパスワードの変更とは異なります。</span><span class="sxs-lookup"><span data-stu-id="3760a-109">Resetting the password is not the same as changing the password.</span></span> <span data-ttu-id="3760a-110">パスワードを再設定するには、ドメイン コントローラーでアカウント情報を上書きする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="3760a-110">A password reset requires permission to overwrite account information on the domain controller.</span></span> <span data-ttu-id="3760a-111">パスワードの再設定は、ユーザーが特定のパスワードを忘れた場合、または知らない場合に、システム管理者が行います。</span><span class="sxs-lookup"><span data-stu-id="3760a-111">Password resets are performed by a system administrator when you forget or do not know a particular password.</span></span> <span data-ttu-id="3760a-112">パスワードの再設定にのみ、対称キーの復元が必要となります。</span><span class="sxs-lookup"><span data-stu-id="3760a-112">Only password resets require symmetric key restoration.</span></span> <span data-ttu-id="3760a-113">アカウント パスワードの定期的な変更には、対称キーの再設定は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="3760a-113">Periodically changing an account password does not require you to reset the symmetric key.</span></span>  
  
-   <span data-ttu-id="3760a-114">レポート サーバーをホストするコンピューターまたはインスタンスの名前変更 (レポート サーバー インスタンスは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス名に基づいています)。</span><span class="sxs-lookup"><span data-stu-id="3760a-114">Renaming the computer or instance that hosts the report server (a report server instance is based on a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance name).</span></span>  
  
-   <span data-ttu-id="3760a-115">レポート サーバー インストールの移行または別のレポート サーバー データベースを使用するようにレポート サーバーを構成。</span><span class="sxs-lookup"><span data-stu-id="3760a-115">Migrating a report server installation or configuring a report server to use a different report server database.</span></span>  
  
-   <span data-ttu-id="3760a-116">ハードウェア障害による、レポート サーバー インストールの復旧。</span><span class="sxs-lookup"><span data-stu-id="3760a-116">Recovering a report server installation due to hardware failure.</span></span>  
  
 <span data-ttu-id="3760a-117">対称キーに必要なバックアップのコピーは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="3760a-117">You only need to back up one copy of the symmetric key.</span></span> <span data-ttu-id="3760a-118">レポート サーバー データベースと対称キーは、一対一で対応します。</span><span class="sxs-lookup"><span data-stu-id="3760a-118">There is a one-to-one correspondence between a report server database and a symmetric key.</span></span> <span data-ttu-id="3760a-119">必要なバックアップのコピーは 1 つだけですが、スケールアウト配置モデルで複数のレポート サーバーを起動している場合には、複数回キーを復元する必要が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="3760a-119">Although you only need to back up one copy, you might need to restore the key multiple times if you are running multiple report servers in a scale-out deployment model.</span></span> <span data-ttu-id="3760a-120">各レポート サーバー インスタンスは、レポート サーバー データベースでデータをロックおよびロック解除するために対称キーのコピーが必要になります。</span><span class="sxs-lookup"><span data-stu-id="3760a-120">Each report server instance will need its copy of the symmetric key to lock and unlock data in the report server database.</span></span>  
  
  
## <a name="backing-up-the-encryption-keys"></a><span data-ttu-id="3760a-121">暗号化キーのバックアップ</span><span class="sxs-lookup"><span data-stu-id="3760a-121">Backing Up the Encryption Keys</span></span>  
 <span data-ttu-id="3760a-122">対称キーのバックアップは、指定するファイルにキーを書き込み、指定したパスワードを使用してそのキーにスクランブルをかける処理です。</span><span class="sxs-lookup"><span data-stu-id="3760a-122">Backing up the symmetric key is a process that writes the key to a file that you specify, and then scrambles the key using a password that you provide.</span></span> <span data-ttu-id="3760a-123">対称キーが暗号化されていない状態で格納されることはないので、ディスクに格納する際は、キーを暗号化するためのパスワードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3760a-123">The symmetric key can never be stored in an unencrypted state so you must provide a password to encrypt the key when you save it to disk.</span></span> <span data-ttu-id="3760a-124">ファイルの作成後、セキュリティで保護された場所にファイルを保存します。ファイルのロックを解除するために使用する **パスワードを覚えておく** 必要があります。</span><span class="sxs-lookup"><span data-stu-id="3760a-124">After the file is created, you must store it in a secure location **and remember the password** that is used to unlock the file.</span></span> <span data-ttu-id="3760a-125">対称キーをバックアップするために、次のツールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3760a-125">To backup the symmetric key, you can use the following tools:</span></span>  
  
 <span data-ttu-id="3760a-126">**ネイティブ モード:** Reporting Services 構成マネージャーか **rskeymgmt** ユーティリティのどちらか。</span><span class="sxs-lookup"><span data-stu-id="3760a-126">**Native mode:** Either the Reporting Services Configuration Manager or the **rskeymgmt** utility.</span></span>  
  
 <span data-ttu-id="3760a-127">**SharePoint モード:** SharePoint サーバーの全体管理ページまたは PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3760a-127">**SharePoint mode:** SharePoint Central Administration pages or PowerShell.</span></span>  
  
####  <a name="backup-sharepoint-mode-report-servers"></a><a name="bkmk_backup_sharepoint"></a> <span data-ttu-id="3760a-128">SharePoint モードのレポート サーバーのバックアップ</span><span class="sxs-lookup"><span data-stu-id="3760a-128">Backup SharePoint Mode Report Servers</span></span>  
 <span data-ttu-id="3760a-129">SharePoint モードのレポート サーバーの場合は、PowerShell コマンドを使用するか、または [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションの管理ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="3760a-129">For SharePoint mode report servers you can either use PowerShell commands or use the management pages for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="3760a-130">詳細については、「[Reporting Services SharePoint サービス アプリケーションの管理](../manage-a-reporting-services-sharepoint-service-application.md)」の「キー管理」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3760a-130">For more information, see the "Key Management" section of [Manage a Reporting Services SharePoint Service Application](../manage-a-reporting-services-sharepoint-service-application.md)</span></span>  
  
####  <a name="back-up-encryption-keys--reporting-services-configuration-manager-native-mode"></a><a name="bkmk_backup_configuration_manager"></a> <span data-ttu-id="3760a-131">暗号化キーのバックアップ - Reporting Services 構成マネージャー (ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="3760a-131">Back up encryption keys -Reporting Services Configuration Manager (Native Mode)</span></span>  
  
1.  <span data-ttu-id="3760a-132">Reporting Services 構成マネージャーを起動して、構成するレポート サーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="3760a-132">Start the Reporting Services Configuration Manager, and then connect to the report server instance you want to configure.</span></span>  
  
2.  <span data-ttu-id="3760a-133">**[暗号化キー]** をクリックし、次に **[バックアップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3760a-133">Click **Encryption Keys**, and then click **Back Up**.</span></span>  
  
3.  <span data-ttu-id="3760a-134">複雑なパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="3760a-134">Type a strong password.</span></span>  
  
4.  <span data-ttu-id="3760a-135">格納されたキーを含むファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="3760a-135">Specify a file to contain the stored key.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="3760a-136">では、ファイルに .snk ファイル拡張子が付けられます。</span><span class="sxs-lookup"><span data-stu-id="3760a-136">appends a .snk file extension to the file.</span></span> <span data-ttu-id="3760a-137">このファイルを、レポート サーバーとは別のディスクに保存することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="3760a-137">Consider storing the file on a disk separate from the report server.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
####  <a name="back-up-encryption-keys--rskeymgmt-native-mode"></a><a name="bkmk_backup_rskeymgmt"></a><span data-ttu-id="3760a-138">暗号化キーのバックアップ-rskeymgmt (ネイティブモード)</span><span class="sxs-lookup"><span data-stu-id="3760a-138">Back up encryption keys -rskeymgmt (Native Mode)</span></span>  
  
1.  <span data-ttu-id="3760a-139">レポート サーバーをホストするコンピューターのローカルで **rskeymgmt.exe** を実行します。</span><span class="sxs-lookup"><span data-stu-id="3760a-139">Run **rskeymgmt.exe** locally on the computer that hosts the report server.</span></span> <span data-ttu-id="3760a-140">抽出用の `-e` 引数を使用してキーをコピーし、ファイル名を入力して、パスワードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3760a-140">You must use the `-e` extract argument to copy the key, provide a file name, and specify a password.</span></span> <span data-ttu-id="3760a-141">指定する必要がある引数の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3760a-141">The following example illustrates the arguments you must specify:</span></span>  
  
    ```cmd
    rskeymgmt -e -f d:\rsdbkey.snk -p<password>  
    ```  
  
## <a name="restore-encryption-keys"></a><span data-ttu-id="3760a-142">暗号化キーの復元</span><span class="sxs-lookup"><span data-stu-id="3760a-142">Restore Encryption Keys</span></span>  
 <span data-ttu-id="3760a-143">対称キーを復元すると、レポート サーバー データベースに格納されている既存の対称キーを上書きします。</span><span class="sxs-lookup"><span data-stu-id="3760a-143">Restoring the symmetric key overwrites the existing symmetric key that is stored in the report server database.</span></span> <span data-ttu-id="3760a-144">暗号化キーを復元すると、使用できないキーが以前ディスクに格納したコピーと置き換わります。</span><span class="sxs-lookup"><span data-stu-id="3760a-144">Restoring an encryption key replaces an unusable key with a copy that you previously saved to disk.</span></span> <span data-ttu-id="3760a-145">暗号化キーを復元することにより、次の処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="3760a-145">Restoring encryption keys results in the following actions:</span></span>  
  
-   <span data-ttu-id="3760a-146">パスワードで保護されたバックアップ ファイルで対称キーが開きます。</span><span class="sxs-lookup"><span data-stu-id="3760a-146">The symmetric key is opened from the password protected backup file.</span></span>  
  
-   <span data-ttu-id="3760a-147">レポート サーバー Windows サービスの公開キーを使用して、対称キーが暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="3760a-147">The symmetric key is encrypted using the public key of the Report Server Windows service.</span></span>  
  
-   <span data-ttu-id="3760a-148">暗号化された対称キーがレポート サーバー データベースに格納されます。</span><span class="sxs-lookup"><span data-stu-id="3760a-148">The encrypted symmetric key is stored in the report server database.</span></span>  
  
-   <span data-ttu-id="3760a-149">以前格納した対称キー データ (以前の配置から既にレポート サーバー データベースにあったキー情報など) は削除されます。</span><span class="sxs-lookup"><span data-stu-id="3760a-149">The previously stored symmetric key data (for example, key information that was already in the report server database from a previous deployment) is deleted.</span></span>  
  
 <span data-ttu-id="3760a-150">暗号化キーを復元するには、暗号化キーのコピーがファイルにある必要があります。</span><span class="sxs-lookup"><span data-stu-id="3760a-150">To restore the encryption key, you must have a copy of the encryption key on file.</span></span> <span data-ttu-id="3760a-151">また、格納したコピーのロックを解除するパスワードを知っている必要もあります。</span><span class="sxs-lookup"><span data-stu-id="3760a-151">You must also know the password that unlocks the stored copy.</span></span> <span data-ttu-id="3760a-152">キーおよびパスワードがある場合、Reporting Services 構成ツールまたは **rskeymgmt** ユーティリティを実行して、キーを復元できます。</span><span class="sxs-lookup"><span data-stu-id="3760a-152">If you have the key and the password, you can run the Reporting Services Configuration tool or **rskeymgmt** utility to restore the key.</span></span> <span data-ttu-id="3760a-153">対称キーは、レポート サーバー データベースに現在格納されている暗号化されたデータをロックおよびロック解除するキーと同じものである必要があります。</span><span class="sxs-lookup"><span data-stu-id="3760a-153">The symmetric key must be the same one that locks and unlocks encrypted data currently stored in the report server database.</span></span> <span data-ttu-id="3760a-154">有効ではないコピーを復元すると、レポート サーバーは、レポート サーバー データベースに現在格納されている暗号化されたデータにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="3760a-154">If you restore a copy that is not valid, the report server cannot access the encrypted data currently stored in the report server database.</span></span> <span data-ttu-id="3760a-155">暗号化されたデータにアクセスできず、有効なキーを復元できない場合、すべての暗号化された値を削除する必要が生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="3760a-155">If this occurs, you might need to delete all encrypted values if you cannot restore a valid key.</span></span> <span data-ttu-id="3760a-156">なんらかの理由で暗号化キーを復元できない場合 (バックアップ コピーがない場合など)、既存のキーおよび暗号化されたコンテンツを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3760a-156">If for some reason you cannot restore the encryption key (for example, if you do not have a backup copy), you must delete the existing key and encrypted content.</span></span> <span data-ttu-id="3760a-157">詳細については、「[暗号化キーの削除と再作成 (SSRS 構成マネージャー)](ssrs-encryption-keys-delete-and-re-create-encryption-keys.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3760a-157">For more information, see [Delete and Re-create Encryption Keys  &#40;SSRS Configuration Manager&#41;](ssrs-encryption-keys-delete-and-re-create-encryption-keys.md).</span></span> <span data-ttu-id="3760a-158">対称キーの作成の詳細については、「[レポート サーバーの初期化 &#40;SSRS 構成マネージャー&#41;](ssrs-encryption-keys-initialize-a-report-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3760a-158">For more information about creating symmetric keys, see [Initialize a Report Server &#40;SSRS Configuration Manager&#41;](ssrs-encryption-keys-initialize-a-report-server.md).</span></span>  
  
####  <a name="restore-encryption-keys--reporting-services-configuration-manager-native-mode"></a><a name="bkmk_restore_configuration_manager"></a><span data-ttu-id="3760a-159">暗号化キーの復元-Reporting Services Configuration Manager (ネイティブモード)</span><span class="sxs-lookup"><span data-stu-id="3760a-159">Restore encryption keys -Reporting Services Configuration Manager (Native Mode)</span></span>  
  
1.  <span data-ttu-id="3760a-160">Reporting Services 構成マネージャーを起動して、構成するレポート サーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="3760a-160">Start the Reporting Services Configuration Manager, and then connect to the report server instance you want to configure.</span></span>  
  
2.  <span data-ttu-id="3760a-161">[暗号化キー] ページで、[**復元**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3760a-161">On the Encryption Keys page, click **Restore**.</span></span>  
  
3.  <span data-ttu-id="3760a-162">バックアップ コピーを含む .snk ファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="3760a-162">Select the .snk file that contains the back up copy.</span></span>  
  
4.  <span data-ttu-id="3760a-163">ファイルのロックを解除するパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="3760a-163">Type the password that unlocks the file.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
####  <a name="restore-encryption-keys---rskeymgmt-native-mode"></a><a name="bkmk_restore_rskeymgmt"></a><span data-ttu-id="3760a-164">暗号化キーの復元-rskeymgmt (ネイティブモード)</span><span class="sxs-lookup"><span data-stu-id="3760a-164">Restore encryption keys - rskeymgmt (Native Mode)</span></span>  
  
1.  <span data-ttu-id="3760a-165">レポート サーバーをホストするコンピューターのローカルで **rskeymgmt.exe** を実行します。</span><span class="sxs-lookup"><span data-stu-id="3760a-165">Run **rskeymgmt.exe** locally on the computer that hosts the report server.</span></span> <span data-ttu-id="3760a-166">キーを復元するには、`-a` 引数を使用します。</span><span class="sxs-lookup"><span data-stu-id="3760a-166">Use the `-a` argument to restore the keys.</span></span> <span data-ttu-id="3760a-167">完全修飾ファイル名を入力し、パスワードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3760a-167">You must provide a fully-qualified file name and specify a password.</span></span> <span data-ttu-id="3760a-168">指定する必要がある引数の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3760a-168">The following example illustrates the arguments you must specify:</span></span>  
  
    ```cmd
    rskeymgmt -a -f d:\rsdbkey.snk -p<password>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3760a-169">参照</span><span class="sxs-lookup"><span data-stu-id="3760a-169">See Also</span></span>  
 [<span data-ttu-id="3760a-170">暗号化キーの構成と管理 &#40;SSRS 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="3760a-170">Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-manage-encryption-keys.md)  
