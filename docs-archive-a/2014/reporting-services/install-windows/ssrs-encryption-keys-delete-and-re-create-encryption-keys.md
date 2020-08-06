---
title: 暗号化キーの削除と再作成 (SSRS 構成マネージャー) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- re-creating encryption keys
- encryption keys [Reporting Services]
- deleting encryption keys
- symmetric keys [Reporting Services]
- removing encryption keys
- resetting encryption keys
ms.assetid: 201afe5f-acc9-4a37-b5ec-121dc7df2a61
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8fa5138e4bbb84395bad79a272d2bde31389396b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742934"
---
# <a name="delete-and-re-create-encryption-keys--ssrs-configuration-manager"></a><span data-ttu-id="029a2-102">暗号化キーの削除と再作成 (SSRS 構成マネージャー)</span><span class="sxs-lookup"><span data-stu-id="029a2-102">Delete and Re-create Encryption Keys  (SSRS Configuration Manager)</span></span>
  <span data-ttu-id="029a2-103">暗号化キーの削除および再作成は、日常の暗号化キー メンテナンスには該当しない作業です。</span><span class="sxs-lookup"><span data-stu-id="029a2-103">Deleting and re-creating encryption keys are activities that fall outside of routine encryption key maintenance.</span></span> <span data-ttu-id="029a2-104">レポート サーバーに対する特定の脅威への対処、またはレポート サーバー データベースにアクセスできなくなったときの最後の手段としてこの作業を行ってください。</span><span class="sxs-lookup"><span data-stu-id="029a2-104">You perform these tasks in response to a specific threat to your report server, or as a last resort when you can no longer access a report server database.</span></span>  
  
-   <span data-ttu-id="029a2-105">既存の対称キーに障害が発生したと考えられる場合は対称キーを再作成します。</span><span class="sxs-lookup"><span data-stu-id="029a2-105">Re-create the symmetric key when you believe the existing symmetric key is compromised.</span></span> <span data-ttu-id="029a2-106">セキュリティを重視する場合は、定期的にキーを再作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="029a2-106">You can also re-create the key on a regular basis as a security best practice.</span></span>  
  
-   <span data-ttu-id="029a2-107">対称キーを復元できない場合は、既存の暗号化キーと使用できない暗号化コンテンツを削除します。</span><span class="sxs-lookup"><span data-stu-id="029a2-107">Delete existing encryption keys and unusable encrypted content when you cannot restore the symmetric key.</span></span>  
  
## <a name="re-creating-encryption-keys"></a><span data-ttu-id="029a2-108">暗号化キーの再作成</span><span class="sxs-lookup"><span data-stu-id="029a2-108">Re-creating Encryption Keys</span></span>  
 <span data-ttu-id="029a2-109">対称キーが不正なユーザーに知られた場合、またはレポート サーバーが攻撃を受けたために予防策として対称キーの再設定が必要な場合、対称キーを再作成することができます。</span><span class="sxs-lookup"><span data-stu-id="029a2-109">If you have evidence that the symmetric key is known to unauthorized users, or if your report server has been under attack and you want to reset the symmetric key as a precaution, you can re-create the symmetric key.</span></span> <span data-ttu-id="029a2-110">対称キーを再作成すると、暗号化されたすべての値が新しい値で再暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="029a2-110">When you re-create the symmetric key, all encrypted values will be re-encrypted using the new value.</span></span> <span data-ttu-id="029a2-111">スケールアウト配置で複数のレポート サーバーを実行している場合、対称キーのすべてのコピーが新しい値に更新されます。</span><span class="sxs-lookup"><span data-stu-id="029a2-111">If you are running multiple report servers in a scale-out deployment, all copies of the symmetric key will be updated to the new value.</span></span> <span data-ttu-id="029a2-112">レポート サーバーは利用可能な公開キーを使用して、配置を構成する各サーバーの対称キーを更新します。</span><span class="sxs-lookup"><span data-stu-id="029a2-112">The report server uses the public keys available to it to update the symmetric key for each server in the deployment.</span></span>  
  
 <span data-ttu-id="029a2-113">対称キーを再作成できるのは、レポート サーバーが動作中の場合のみです。</span><span class="sxs-lookup"><span data-stu-id="029a2-113">You can only re-create the symmetric key when the report server is in a working state.</span></span> <span data-ttu-id="029a2-114">暗号化キーの再作成およびコンテンツの再暗号化を実行すると、サーバーの処理が中断されます。</span><span class="sxs-lookup"><span data-stu-id="029a2-114">Re-creating the encryption keys and re-encrypting content disrupts server operations.</span></span> <span data-ttu-id="029a2-115">再暗号化の実行中はサーバーをオフラインにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="029a2-115">You must take the server offline while re-encryption is underway.</span></span> <span data-ttu-id="029a2-116">再暗号化中にレポート サーバーに対して要求を送信することはできません。</span><span class="sxs-lookup"><span data-stu-id="029a2-116">There should be no requests made to the report server during re-encryption.</span></span>  
  
 <span data-ttu-id="029a2-117">対称キーおよび暗号化データを再設定するには、Reporting Services 構成ツールまたは **rskeymgmt** ユーティリティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="029a2-117">You can use the Reporting Services Configuration tool or the **rskeymgmt** utility to reset the symmetric key and encrypted data.</span></span> <span data-ttu-id="029a2-118">対称キーの作成方法の詳細については、「[レポート サーバーの初期化 (SSRS 構成マネージャー)](ssrs-encryption-keys-initialize-a-report-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="029a2-118">For more information about how the symmetric key is created, see [Initialize a Report Server &#40;SSRS Configuration Manager&#41;](ssrs-encryption-keys-initialize-a-report-server.md).</span></span>  
  
#### <a name="how-to-re-create-encryption-keys-reporting-services-configuration-tool"></a><span data-ttu-id="029a2-119">暗号化キーの再作成方法 (Reporting Services 構成ツール)</span><span class="sxs-lookup"><span data-stu-id="029a2-119">How to re-create encryption keys (Reporting Services Configuration Tool)</span></span>  
  
1.  <span data-ttu-id="029a2-120">rsreportserver.confi ファイルで `IsWebServiceEnabled` プロパティを変更することにより、レポート サーバー Web サービスおよび HTTP アクセスを無効にします。</span><span class="sxs-lookup"><span data-stu-id="029a2-120">Disable the Report Server Web service and HTTP access by modifying the `IsWebServiceEnabled` property in the rsreportserver.config file.</span></span> <span data-ttu-id="029a2-121">この手順を実行すると、レポート サーバーへの認証要求の送信が一時的に停止されますが、レポート サーバーが完全にシャットダウンされることはありません。</span><span class="sxs-lookup"><span data-stu-id="029a2-121">This step temporarily stops authentication requests from being sent to the report server without completely shutting down the server.</span></span> <span data-ttu-id="029a2-122">キーを再作成できるように最小限のサービスが必要です。</span><span class="sxs-lookup"><span data-stu-id="029a2-122">You must have minimal service so that you can recreate the keys.</span></span>  
  
     <span data-ttu-id="029a2-123">レポート サーバーのスケールアウト配置に対する暗号化キーを再作成する場合、配置内のすべてのインスタンスでこのプロパティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="029a2-123">If you are recreating encryption keys for a report server scale-out deployment, disable this property on all instances in the deployment.</span></span>  
  
    1.  <span data-ttu-id="029a2-124">Windows エクスプローラーを開き、 *drive*:\Program Files\Microsoft SQL Server\\*report_server_instance*\Reporting Services に移動します。</span><span class="sxs-lookup"><span data-stu-id="029a2-124">Open Windows Explorer and navigate to *drive*:\Program Files\Microsoft SQL Server\\*report_server_instance*\Reporting Services.</span></span> <span data-ttu-id="029a2-125">*drive* は使用しているコンピューターのドライブ文字に置き換え、 *report_server_instance* は Web サービスおよび HTTP アクセスを無効にするレポート サーバー インスタンスに対応するフォルダー名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="029a2-125">Replace *drive* with your drive letter and *report_server_instance* with the folder name that corresponds to the report server instance for which you want to disable the Web service and HTTP access.</span></span> <span data-ttu-id="029a2-126">たとえば、C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services のようになります。</span><span class="sxs-lookup"><span data-stu-id="029a2-126">For example, C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services.</span></span>  
  
    2.  <span data-ttu-id="029a2-127">rsreportserver.config ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="029a2-127">Open the rsreportserver.config file.</span></span>  
  
    3.  <span data-ttu-id="029a2-128">`IsWebServiceEnabled` プロパティに対して `False` を指定し、変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="029a2-128">For the `IsWebServiceEnabled` property, specify `False`, and then save your changes.</span></span>  
  
2.  <span data-ttu-id="029a2-129">Reporting Services 構成ツールを起動して、構成するレポート サーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="029a2-129">Start the Reporting Services Configuration tool, and then connect to the report server instance you want to configure.</span></span>  
  
3.  <span data-ttu-id="029a2-130">[暗号化キー] ページで、 **[変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="029a2-130">On the Encryption Keys page, click **Change**.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
4.  <span data-ttu-id="029a2-131">レポート サーバー Windows サービスを再開します。</span><span class="sxs-lookup"><span data-stu-id="029a2-131">Restart the Report Server Windows service.</span></span> <span data-ttu-id="029a2-132">レポート サーバーのスケールアウト配置に対する暗号化キーを再作成する場合、すべてのインスタンスでサービスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="029a2-132">If you are recreating encryption keys for a scale-out deployment, restart the service on all instances.</span></span>  
  
5.  <span data-ttu-id="029a2-133">rsreportserver.confi ファイルで `IsWebServiceEnabled` プロパティを変更することにより、レポート サーバー Web サービスおよび HTTP アクセスを再び有効にします。</span><span class="sxs-lookup"><span data-stu-id="029a2-133">Re-enable the Web service and HTTP access by modifying the `IsWebServiceEnabled` property in the rsreportserver.config file.</span></span> <span data-ttu-id="029a2-134">スケールアウト配置の場合は、すべてのインスタンスについてこの作業を行います。</span><span class="sxs-lookup"><span data-stu-id="029a2-134">Do this for all instances if you are working with a scale out deployment.</span></span>  
  
#### <a name="how-to-re-create-encryption-keys-rskeymgmt"></a><span data-ttu-id="029a2-135">暗号化キーの再作成方法 (rskeymgmt)</span><span class="sxs-lookup"><span data-stu-id="029a2-135">How to re-create encryption keys (rskeymgmt)</span></span>  
  
1.  <span data-ttu-id="029a2-136">レポート サーバー Web サービスおよび HTTP アクセスを無効にします。</span><span class="sxs-lookup"><span data-stu-id="029a2-136">Disable the Report Server Web service and HTTP access.</span></span> <span data-ttu-id="029a2-137">上記の手順に従って Web サービスの操作を停止します。</span><span class="sxs-lookup"><span data-stu-id="029a2-137">Use the instructions in the previous procedure to stop Web service operations.</span></span>  
  
2.  <span data-ttu-id="029a2-138">レポート サーバーをホストするコンピューターのローカルで **rskeymgmt.exe** を実行します。</span><span class="sxs-lookup"><span data-stu-id="029a2-138">Run **rskeymgmt.exe** locally on the computer that hosts the report server.</span></span> <span data-ttu-id="029a2-139">`-s` 引数を指定して対称キーを再設定します。</span><span class="sxs-lookup"><span data-stu-id="029a2-139">Use the `-s` argument to reset the symmetric key.</span></span> <span data-ttu-id="029a2-140">他の引数は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="029a2-140">No other arguments are required:</span></span>  
  
    ```  
    rskeymgmt -s  
    ```  
  
3.  <span data-ttu-id="029a2-141">Windows サービスを再起動して、Web サービスの操作を有効にします。</span><span class="sxs-lookup"><span data-stu-id="029a2-141">Restart the Windows service and enable Web service operations.</span></span>  
  
## <a name="deleting-unusable-encrypted-content"></a><span data-ttu-id="029a2-142">使用できない暗号化コンテンツの削除</span><span class="sxs-lookup"><span data-stu-id="029a2-142">Deleting Unusable Encrypted Content</span></span>  
 <span data-ttu-id="029a2-143">何らかの理由で暗号化キーを復元できない場合、レポート サーバーはこのキーによって暗号化されたデータの暗号化を解除して使用することができません。</span><span class="sxs-lookup"><span data-stu-id="029a2-143">If for some reason you cannot restore the encryption key, the report server will never be able to decrypt and use any data that is encrypted with that key.</span></span> <span data-ttu-id="029a2-144">レポート サーバーを動作中の状態に戻すには、レポート サーバー データベースに格納されている暗号化された値を削除して、必要な値を手動で再指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="029a2-144">To return the report server to a working state, you must delete the encrypted values that are currently stored in the report server database and then manually re-specify the values you need.</span></span>  
  
 <span data-ttu-id="029a2-145">暗号化キーを削除すると、対称キーの情報がすべてレポート サーバー データベースから削除され、また暗号化されたコンテンツもすべて削除されます。</span><span class="sxs-lookup"><span data-stu-id="029a2-145">Deleting the encryption keys removes all symmetric key information from the report server database and deletes any encrypted content.</span></span> <span data-ttu-id="029a2-146">暗号化されていないデータはそのまま残ります。削除されるのは暗号化されたコンテンツだけです。</span><span class="sxs-lookup"><span data-stu-id="029a2-146">All unencrypted data is left intact; only encrypted content is removed.</span></span> <span data-ttu-id="029a2-147">暗号化キーを削除した場合、レポート サーバーは新しい対称キーを追加することでレポート サーバー自体を自動的に再初期化します。</span><span class="sxs-lookup"><span data-stu-id="029a2-147">When you delete the encryption keys, the report server re-initializes itself automatically by adding a new symmetric key.</span></span> <span data-ttu-id="029a2-148">暗号化されたコンテンツを削除すると、以下の処理が実行されます。</span><span class="sxs-lookup"><span data-stu-id="029a2-148">The following occurs when you delete encrypted content:</span></span>  
  
-   <span data-ttu-id="029a2-149">共有データ ソースの接続文字列が削除されます。</span><span class="sxs-lookup"><span data-stu-id="029a2-149">Connection strings in shared data sources are deleted.</span></span> <span data-ttu-id="029a2-150">レポートを実行しているユーザーに対して "ConnectionString プロパティが初期化されていません。" というエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="029a2-150">Users who run reports get the error "The ConnectionString property has not been initialized."</span></span>  
  
-   <span data-ttu-id="029a2-151">保存されている資格情報が削除されます。</span><span class="sxs-lookup"><span data-stu-id="029a2-151">Stored credentials are deleted.</span></span> <span data-ttu-id="029a2-152">レポートおよび共有データ ソースは、要求された資格情報を使用するように再構成されます。</span><span class="sxs-lookup"><span data-stu-id="029a2-152">Reports and shared data sources are reconfigured to use prompted credentials.</span></span>  
  
-   <span data-ttu-id="029a2-153">モデルを基にしたレポートは実行されません (また、保存されている資格情報を使用するか、または資格情報を使用しないように構成された共有データ ソースを必要とするレポートも実行されません)。</span><span class="sxs-lookup"><span data-stu-id="029a2-153">Reports that are based on models (and require shared data sources configured with stored or no credentials) will not run.</span></span>  
  
-   <span data-ttu-id="029a2-154">サブスクリプションが非アクティブになります。</span><span class="sxs-lookup"><span data-stu-id="029a2-154">Subscriptions are deactivated.</span></span>  
  
 <span data-ttu-id="029a2-155">暗号化されたコンテンツをいったん削除したら、そのコンテンツを復旧することはできません。</span><span class="sxs-lookup"><span data-stu-id="029a2-155">Once you delete encrypted content, you cannot recover it.</span></span> <span data-ttu-id="029a2-156">接続文字列および保存された資格情報を再指定して、サブスクリプションをアクティブにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="029a2-156">You must re-specify connection strings and stored credentials, and you must activate subscriptions.</span></span>  
  
 <span data-ttu-id="029a2-157">値を削除するには、Reporting Services 構成ツールまたは **rskeymgmt** ユーティリティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="029a2-157">You can use the Reporting Services Configuration tool or the **rskeymgmt** utility to remove the values.</span></span>  
  
#### <a name="how-to-delete-encryption-keys-reporting-services-configuration-tool"></a><span data-ttu-id="029a2-158">暗号化キーの削除方法 (Reporting Services 構成ツール)</span><span class="sxs-lookup"><span data-stu-id="029a2-158">How to delete encryption keys (Reporting Services Configuration Tool)</span></span>  
  
1.  <span data-ttu-id="029a2-159">Reporting Services 構成ツールを起動して、構成するレポート サーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="029a2-159">Start the Reporting Services Configuration tool, and then connect to the report server instance you want to configure.</span></span>  
  
2.  <span data-ttu-id="029a2-160">**[暗号化キー]** をクリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="029a2-160">Click **Encryption Keys**, and then click **Delete**.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
3.  <span data-ttu-id="029a2-161">レポート サーバー Windows サービスを再開します。</span><span class="sxs-lookup"><span data-stu-id="029a2-161">Restart the Report Server Windows service.</span></span> <span data-ttu-id="029a2-162">スケールアウト配置の場合は、すべてのレポート サーバー インスタンスについてこの作業を行います。</span><span class="sxs-lookup"><span data-stu-id="029a2-162">For a scale-out deployment, do this on all report server instances.</span></span>  
  
#### <a name="how-to-delete-encryption-keys-rskeymmgt"></a><span data-ttu-id="029a2-163">暗号化キーの削除方法 (rskeymmgt)</span><span class="sxs-lookup"><span data-stu-id="029a2-163">How to delete encryption keys (rskeymmgt)</span></span>  
  
1.  <span data-ttu-id="029a2-164">レポート サーバーをホストするコンピューターのローカルで **rskeymgmt.exe** を実行します。</span><span class="sxs-lookup"><span data-stu-id="029a2-164">Run **rskeymgmt.exe** locally on the computer that hosts the report server.</span></span> <span data-ttu-id="029a2-165">削除用の **-d** 引数を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="029a2-165">You must use the **-d** apply argument.</span></span> <span data-ttu-id="029a2-166">指定する必要がある引数の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="029a2-166">The following example illustrates the argument you must specify:</span></span>  
  
    ```  
    rskeymgmt -d  
    ```  
  
2.  <span data-ttu-id="029a2-167">レポート サーバー Windows サービスを再開します。</span><span class="sxs-lookup"><span data-stu-id="029a2-167">Restart the Report Server Windows service.</span></span> <span data-ttu-id="029a2-168">スケールアウト配置の場合は、すべてのレポート サーバー インスタンスについてこの作業を行います。</span><span class="sxs-lookup"><span data-stu-id="029a2-168">For a scale-out deployment, do this on all report server instances.</span></span>  
  
#### <a name="how-to-re-specify-encrypted-values"></a><span data-ttu-id="029a2-169">暗号化された値を再指定する方法</span><span class="sxs-lookup"><span data-stu-id="029a2-169">How to re-specify encrypted values</span></span>  
  
1.  <span data-ttu-id="029a2-170">各共有データ ソースに対して、接続文字列を再入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="029a2-170">For each shared data source, you must retype the connection string.</span></span>  
  
2.  <span data-ttu-id="029a2-171">保存された資格情報を使用するレポートおよび共有データ ソースごとに、ユーザー名とパスワードを再入力して、これらの情報を保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="029a2-171">For each report and shared data source that uses stored credentials, you must retype the user name and password, and then save.</span></span> <span data-ttu-id="029a2-172">詳細については、 [オンライン ブックの「](../../integration-services/connection-manager/data-sources.md) レポート データ ソースに関する資格情報と接続情報を指定する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="029a2-172">For more information, see [Specify Credential and Connection Information for Report Data Sources](../../integration-services/connection-manager/data-sources.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
3.  <span data-ttu-id="029a2-173">各データ ドリブン サブスクリプションを開いて、資格情報をサブスクリプション データベースに再入力します。</span><span class="sxs-lookup"><span data-stu-id="029a2-173">For each data-driven subscription, open each subscription and retype the credentials to the subscription database.</span></span>  
  
4.  <span data-ttu-id="029a2-174">暗号化されたデータ (ファイル共有の配信拡張機能や暗号化を使用するサードパーティ製の配信拡張機能など) を使用する各サブスクリプションを開いて、資格情報を再入力します。</span><span class="sxs-lookup"><span data-stu-id="029a2-174">For subscriptions that use encrypted data (this includes the File Share delivery extension and any third-party delivery extension that uses encryption), open each subscription and retype credentials.</span></span> <span data-ttu-id="029a2-175">レポート サーバーの電子メール配信を使用するサブスクリプションでは、暗号化されたデータが使用されないため、キーの変更による影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="029a2-175">Subscriptions that use Report Server e-mail delivery do not use encrypted data and are unaffected by the key change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="029a2-176">参照</span><span class="sxs-lookup"><span data-stu-id="029a2-176">See Also</span></span>  
 <span data-ttu-id="029a2-177">[SSRS Configuration Manager &#40;暗号化キーの構成と管理&#41;](ssrs-encryption-keys-manage-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="029a2-177">[Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;](ssrs-encryption-keys-manage-encryption-keys.md) </span></span>  
 [<span data-ttu-id="029a2-178">暗号化されたレポート サーバー データの格納 &#40;SSRS 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="029a2-178">Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-store-encrypted-report-server-data.md)  
  
  
