---
title: 暗号化キー (SSRS ネイティブモード) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.encryptionkeypanel.F1
ms.assetid: cc7e6f84-80e1-4b5e-9409-d0e074edd147
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 78e9816a9e779459cd1388c1f7f10257c89b1ae5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643152"
---
# <a name="encryption-keys-ssrs-native-mode"></a><span data-ttu-id="2aae6-102">暗号化キー (SSRS ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="2aae6-102">Encryption Keys (SSRS Native Mode)</span></span>
  <span data-ttu-id="2aae6-103">[暗号化キー] ページを使用すると、レポート サーバーでデータの暗号化と暗号化解除に使用される対称キーを管理できます。</span><span class="sxs-lookup"><span data-stu-id="2aae6-103">Use the Encryption Keys page to manage the symmetric key that is used to encrypt and decrypt data in a report server.</span></span> <span data-ttu-id="2aae6-104">暗号化キーの管理は、レポート サーバーの構成で重要な位置を占めています。</span><span class="sxs-lookup"><span data-stu-id="2aae6-104">Managing the encryption keys is an important part of report server configuration.</span></span> <span data-ttu-id="2aae6-105">対称キーはレポート サーバー データベースを作成する際に自動的に作成されて適用されますが、</span><span class="sxs-lookup"><span data-stu-id="2aae6-105">The symmetric key is created and applied automatically when you create the report server database.</span></span> <span data-ttu-id="2aae6-106">定期的なメンテナンス操作を実行できるように、対称キーのバックアップ コピーを作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="2aae6-106">Create a backup copy of the symmetric key so that you can perform routine maintenance operations.</span></span> <span data-ttu-id="2aae6-107">次に示すメンテナンス タスクを実行するには、対称キーの有効なコピーが必要です。</span><span class="sxs-lookup"><span data-stu-id="2aae6-107">The following maintenance tasks require that you have a valid copy of the symmetric key:</span></span>  
  
-   <span data-ttu-id="2aae6-108">レポート サーバー サービスのサービス アカウントを変更する。</span><span class="sxs-lookup"><span data-stu-id="2aae6-108">Changing the service account for the Report Server service.</span></span>  
  
-   <span data-ttu-id="2aae6-109">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インストールを別のコンピューターに移行する。</span><span class="sxs-lookup"><span data-stu-id="2aae6-109">Migrating a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation to a different computer.</span></span>  
  
-   <span data-ttu-id="2aae6-110">既存のレポート サーバー データベースを共有または使用するように、新しいレポート サーバー インスタンスを構成する。</span><span class="sxs-lookup"><span data-stu-id="2aae6-110">Configuring a new report server instance to share or use an existing report server database.</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="2aae6-111">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ネイティブモード。</span><span class="sxs-lookup"><span data-stu-id="2aae6-111">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2aae6-112">セキュリティを高めるために、Reporting Services の暗号化キーは定期的に変更することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2aae6-112">Periodically changing the Reporting Services encryption key is a security best practice.</span></span> <span data-ttu-id="2aae6-113">キーを変更する推奨されるタイミングは、Reporting Services のメジャー バージョンのアップグレードの直後です。</span><span class="sxs-lookup"><span data-stu-id="2aae6-113">A recommended time to change the key is immediately following a major version upgrade of Reporting Services.</span></span> <span data-ttu-id="2aae6-114">アップグレード後であれば、アップグレード サイクル以外での Reporting Services の暗号化キーの変更に伴う他のサービスの中断を最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="2aae6-114">Changing the key after an upgrade minimizes additional service interruption caused by changing the Reporting Services encryption key outside of the upgrade cycle.</span></span>  
  
 <span data-ttu-id="2aae6-115">レポート サーバー サービスのユーザー アカウントを更新し、アカウントの変更に [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャー以外のツールを使用した場合、またはインストールしたレポート サーバーを新しいサーバーに移行しようとしている場合は、対称キーの復元が必要です。</span><span class="sxs-lookup"><span data-stu-id="2aae6-115">Restoring the symmetric key is necessary if you updated the user account of the Report Server service (and you used a tool other than the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager to change the account), or if you are migrating a report server installation to a new server.</span></span>  
  
 <span data-ttu-id="2aae6-116">不正なアクセスを防ぐために、対称キーはレポート サーバー サービスの秘密キーを使用して暗号化されており、</span><span class="sxs-lookup"><span data-stu-id="2aae6-116">To protect the symmetric key from unauthorized access, the symmetric key is encrypted using the private key of the Report Server service.</span></span> <span data-ttu-id="2aae6-117">レポート サーバー サービスのみが、機密データをレポート サーバー データベースに格納する目的で、対称キーをロック解除して使用できます。</span><span class="sxs-lookup"><span data-stu-id="2aae6-117">Only the Report Server service is able to unlock and use the symmetric key to store sensitive data in the report server database.</span></span> <span data-ttu-id="2aae6-118">レポート サーバー サービスの ID を変更した場合や、レポート サーバーを新しいコンピューターに移行した場合は、レポート サーバー サービスの秘密キーで対称キーをロック解除できなくなります。</span><span class="sxs-lookup"><span data-stu-id="2aae6-118">If you change the identity of the Report Server service, or if you migrate the report server to a new computer, the private key of the Report Server service will no longer be able to unlock the symmetric key.</span></span> <span data-ttu-id="2aae6-119">対称キーへのアクセスを復元するには、新しいレポート サーバー サービス ID の秘密キーを使用して対称キーを再暗号化します。</span><span class="sxs-lookup"><span data-stu-id="2aae6-119">To restore access to the symmetric key, re-encrypt the symmetric key using the private key of the new Report Server service identity.</span></span> <span data-ttu-id="2aae6-120">対称キーの復元処理によって、再暗号化が行われます。</span><span class="sxs-lookup"><span data-stu-id="2aae6-120">Restoring the symmetric key is the process by which the re-encryption occurs.</span></span>  
  
 <span data-ttu-id="2aae6-121">対称キーを復元するのは、レポート サーバー データベース内のデータの暗号化と暗号解除に現在使用されているキーと同じキーである場合だけです。</span><span class="sxs-lookup"><span data-stu-id="2aae6-121">Only restore a symmetric key if it is the same key that is currently used to encrypt and decrypt data in the report server database.</span></span> <span data-ttu-id="2aae6-122">不適切な対称キーを復元すると、機密データにアクセスできなくなります。</span><span class="sxs-lookup"><span data-stu-id="2aae6-122">If you restore a symmetric key that is not valid, you can no longer access sensitive data.</span></span> <span data-ttu-id="2aae6-123">そのような場合は、対称キーを削除して再作成します。</span><span class="sxs-lookup"><span data-stu-id="2aae6-123">In this case, delete and re-create the key.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2aae6-124">対称キーの削除と再作成の操作は、取り消したり元に戻したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="2aae6-124">The action of deleting and recreating the symmetric key cannot be reversed or undone.</span></span> <span data-ttu-id="2aae6-125">キーを削除または再作成すると、現在のインストールに重大な影響を及ぼす可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2aae6-125">Deleting or recreating the key can have important ramifications on your current installation.</span></span> <span data-ttu-id="2aae6-126">対称キーを削除すると、その対称キーを使用して暗号化されている既存のデータも削除されます。</span><span class="sxs-lookup"><span data-stu-id="2aae6-126">If you delete the key, any existing data encrypted by the symmetric key will also deleted.</span></span> <span data-ttu-id="2aae6-127">たとえば、外部のレポート データ ソースへの接続文字列、保存されている接続文字列、サブスクリプション情報の一部が削除されることがあります。</span><span class="sxs-lookup"><span data-stu-id="2aae6-127">Deleted data includes connection strings to external report data sources, stored connection strings, and some subscription information.</span></span>  
  
 <span data-ttu-id="2aae6-128">このページを開くには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを起動して、ナビゲーション ウィンドウでリンクを選択します。</span><span class="sxs-lookup"><span data-stu-id="2aae6-128">To open this page, start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager and select the link in the navigation pane.</span></span> <span data-ttu-id="2aae6-129">詳細については、「 [Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2aae6-129">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="2aae6-130">Options</span><span class="sxs-lookup"><span data-stu-id="2aae6-130">Options</span></span>  
 <span data-ttu-id="2aae6-131">**Backup**</span><span class="sxs-lookup"><span data-stu-id="2aae6-131">**Backup**</span></span>  
 <span data-ttu-id="2aae6-132">指定したファイルに対称キーをコピーします。</span><span class="sxs-lookup"><span data-stu-id="2aae6-132">Copies the symmetric key to a file that you specify.</span></span> <span data-ttu-id="2aae6-133">対称キーはプレーン テキストのまま保存しないでください。</span><span class="sxs-lookup"><span data-stu-id="2aae6-133">The symmetric key is never stored in plain text.</span></span> <span data-ttu-id="2aae6-134">パスワードを入力してファイルを保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2aae6-134">You must type a password to protect the file.</span></span>  
  
 <span data-ttu-id="2aae6-135">**復元**</span><span class="sxs-lookup"><span data-stu-id="2aae6-135">**Restore**</span></span>  
 <span data-ttu-id="2aae6-136">以前に保存された対称キーのコピーを、レポート サーバー データベースに適用します。</span><span class="sxs-lookup"><span data-stu-id="2aae6-136">Applies a previously saved copy of the symmetric key to the report server database.</span></span> <span data-ttu-id="2aae6-137">ファイルのロックを解除するパスワードを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2aae6-137">You must provide the password to unlock the file.</span></span>  
  
 <span data-ttu-id="2aae6-138">現在接続しているレポート サーバー インスタンスの以前の対称キーは、復元された対称キーによって上書きされます。</span><span class="sxs-lookup"><span data-stu-id="2aae6-138">The previous copy of the symmetric key for the report server instance you are currently connected to is overwritten by the restored version.</span></span> <span data-ttu-id="2aae6-139">対称キーを復元した後、そのレポート サーバー データベースを利用するレポート サーバーをすべて初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2aae6-139">After you restore the symmetric key, you must initialize all the report servers that use the report server database.</span></span> <span data-ttu-id="2aae6-140">レポートサーバーの初期化の詳細については、「[レポートサーバーの初期化 &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2aae6-140">For more information about initializing report servers, see [Initialize a Report Server &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md).</span></span>  
  
 <span data-ttu-id="2aae6-141">**変更**</span><span class="sxs-lookup"><span data-stu-id="2aae6-141">**Change**</span></span>  
 <span data-ttu-id="2aae6-142">対称キーを再作成し、レポート サーバー データベース内の暗号化された値を再暗号化します。</span><span class="sxs-lookup"><span data-stu-id="2aae6-142">Recreates the symmetric key and re-encrypts all encrypted values in the report server database.</span></span> <span data-ttu-id="2aae6-143">対称キーを再作成する前に、レポート サーバー サービスを必ず停止してください。</span><span class="sxs-lookup"><span data-stu-id="2aae6-143">Be sure to stop the Report Server service before recreating the symmetric key.</span></span>  
  
 <span data-ttu-id="2aae6-144">スケールアウト配置では、すべての対称キーが新しいバージョンに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="2aae6-144">In a scale-out deployment, all copies of the symmetric key are replaced with newer versions.</span></span> <span data-ttu-id="2aae6-145">対称キーを変更する前に、スケールアウト配置に含まれているサーバーの一覧を確認して、有効なレポート サーバー インスタンスにのみ、新しいキーへのアクセスが許可されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="2aae6-145">Before changing the symmetric key, be sure to review the list of servers that are joined to the scale-out deployment to verify that only valid report server instances are given access to the new key.</span></span> <span data-ttu-id="2aae6-146">スケールアウト配置に含まれるサーバーは、 **[スケールアウト配置]** ページに一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="2aae6-146">The servers that are part of a scale-out deployment are listed in the **Scale-out Deployment** page.</span></span> <span data-ttu-id="2aae6-147">キーを再作成する前に、配置に含まれる各レポート サーバーのサービスを停止してください。</span><span class="sxs-lookup"><span data-stu-id="2aae6-147">Stop the service on each report server in the deployment before recreating the key.</span></span>  
  
 <span data-ttu-id="2aae6-148">データ ソースとサブスクリプションが多数存在する場合、対称キーの再作成に長い時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="2aae6-148">Note that regenerating the symmetric key can be a long-running process if you have many data sources and subscriptions.</span></span>  
  
 <span data-ttu-id="2aae6-149">**削除**</span><span class="sxs-lookup"><span data-stu-id="2aae6-149">**Delete**</span></span>  
 <span data-ttu-id="2aae6-150">接続文字列や保存されている資格情報を含むすべての暗号化コンテンツと、対称キーを削除します。</span><span class="sxs-lookup"><span data-stu-id="2aae6-150">Deletes the symmetric key and all encrypted content, including connection strings and stored credentials.</span></span> <span data-ttu-id="2aae6-151">対称キーは、復元できない場合にのみ削除してください。</span><span class="sxs-lookup"><span data-stu-id="2aae6-151">You should only delete the symmetric key if you cannot restore it.</span></span>  
  
 <span data-ttu-id="2aae6-152">対称キーを削除すると、レポートおよび共有データ ソース内に接続文字列や保存されている資格情報が存在しなくなるため、その値を再入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2aae6-152">Once you delete the symmetric key, you must re-enter the missing connection strings and stored credentials in the reports and shared data sources that no longer have these values.</span></span> <span data-ttu-id="2aae6-153">さらに、暗号化データを保存する配信拡張機能が使用されるサブスクリプションをすべて更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2aae6-153">You must also update all subscriptions that use delivery extensions that store encrypted data.</span></span> <span data-ttu-id="2aae6-154">これには、ファイル共有配信拡張機能や、暗号化された値を使用するサード パーティの拡張機能が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2aae6-154">This includes the file share delivery extension and any third-party delivery extension that use encrypted value.</span></span>  
  
 <span data-ttu-id="2aae6-155">この情報を自動的に更新する方法はありません。</span><span class="sxs-lookup"><span data-stu-id="2aae6-155">There is no automated way to update this information.</span></span> <span data-ttu-id="2aae6-156">保存されている資格情報や接続文字列を使用する各レポート、サブスクリプション、共有データ ソースを、一度に 1 つずつ更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2aae6-156">Each report, subscription, and shared data source that uses stored credentials and connection strings must be updated one at a time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2aae6-157">参照</span><span class="sxs-lookup"><span data-stu-id="2aae6-157">See Also</span></span>  
 <span data-ttu-id="2aae6-158">[Reporting Services Configuration Manager F1 ヘルプトピック &#40;SSRS ネイティブモード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="2aae6-158">[Reporting Services Configuration Manager F1 Help Topics &#40;SSRS Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="2aae6-159">[Reporting Services の暗号化キーのバックアップと復元](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="2aae6-159">[Back Up and Restore Reporting Services Encryption Keys](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md) </span></span>  
 <span data-ttu-id="2aae6-160">[暗号化キーの削除と再作成  &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="2aae6-160">[Delete and Re-create Encryption Keys  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md) </span></span>  
 <span data-ttu-id="2aae6-161">[レポート サーバーの初期化 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="2aae6-161">[Initialize a Report Server &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md) </span></span>  
 [<span data-ttu-id="2aae6-162">暗号化されたレポート サーバー データの格納 &#40;SSRS 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="2aae6-162">Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;</span></span>](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md)  
  
  