---
title: レポート サーバー サービス アカウントの構成 (SSRS 構成マネージャー) | Microsoft Docs
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.prod: sql-server-2014
ms.technology: ''
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/10/2018
ms.openlocfilehash: b860a9c916f7dd9c1bdef4f5218845c66239ebe2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712798"
---
# <a name="configure-the-report-server-service-account-ssrs-configuration-manager"></a><span data-ttu-id="ad5a4-102">レポート サーバー サービス アカウントの構成 (SSRS 構成マネージャー)</span><span class="sxs-lookup"><span data-stu-id="ad5a4-102">Configure the Report Server Service Account (SSRS Configuration Manager)</span></span>

  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="ad5a4-103">は、レポート サーバー Web サービス、レポート マネージャー、およびスケジュールされたレポート処理とサブスクリプションの配信に使用されるバックグラウンド処理アプリケーションを含んだ単一のサービスとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-103">is implemented as a single service that contains a Report Server Web service, Report Manager, and a background processing application that is used for scheduled report processing and subscription delivery.</span></span> <span data-ttu-id="ad5a4-104">このトピックでは、サービス アカウントを最初に構成する方法と、Reporting Services 構成ツールを使用してアカウントやパスワードを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-104">This topic explains how the service account is initially configured and how to modify the account or password using the Reporting Services Configuration tool.</span></span>  
  
## <a name="initial-configuration"></a><span data-ttu-id="ad5a4-105">初期構成</span><span class="sxs-lookup"><span data-stu-id="ad5a4-105">Initial Configuration</span></span>

 <span data-ttu-id="ad5a4-106">レポート サーバー サービスのアカウントは、セットアップ時に定義されます。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-106">The Report Server service account is defined during Setup.</span></span> <span data-ttu-id="ad5a4-107">このサービスは、ドメイン ユーザー アカウントまたは `NetworkService` などのビルトイン アカウントで実行できます。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-107">You can run the service under a domain user account or a built-in such as `NetworkService` account.</span></span> <span data-ttu-id="ad5a4-108">既定のアカウントはありません。インストールウィザードの [サーバーの[構成-サービスアカウント](../../sql-server/install/server-configuration-service-accounts.md)] ページで指定したアカウントは、レポートサーバーサービスの初期アカウントになります。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-108">There is no default account; whatever account you specify in the [Server Configuration - Service Accounts](../../sql-server/install/server-configuration-service-accounts.md) page of the Installation Wizard becomes the initial account of the Report Server service.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ad5a4-109">レポート サーバー Web サービスとレポート マネージャーは [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] アプリケーションですが、[!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] アカウントでは実行されません。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-109">Although the Report Server Web service and Report Manager are [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] applications, they do not run under the [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] account.</span></span> <span data-ttu-id="ad5a4-110">単一のサービス アーキテクチャによって、両方の ASP.NET アプリケーションが同じレポート サーバー プロセス ID で実行されます。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-110">The single service architecture runs both ASP.NET applications within the same Report Server process identity.</span></span> <span data-ttu-id="ad5a4-111">これは以前のリリースからの重要な変更です。以前のリリースでは、レポート サーバー Web サービスとレポート マネージャーの両方が、IIS で指定された [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] ワーカー プロセス ID で実行されていました。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-111">This is an important change from previous releases, where both the Report Server Web service and Report Manager ran under the [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] worker process identity specified in IIS.</span></span>
  
## <a name="changing-the-service-account"></a><span data-ttu-id="ad5a4-112">サービス アカウントの変更</span><span class="sxs-lookup"><span data-stu-id="ad5a4-112">Changing the Service Account</span></span>

 <span data-ttu-id="ad5a4-113">サービス アカウント情報の表示と再構成には、常に [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-113">To view and reconfigure service account information, always use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool.</span></span> <span data-ttu-id="ad5a4-114">サービス ID 情報は、内部の複数の場所に保存されています。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-114">Service identity information is stored internally in multiple locations.</span></span> <span data-ttu-id="ad5a4-115">このツールを使用することで、アカウントまたはパスワードを変更するたびに、すべての参照がその変更に対応して確実に更新されます。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-115">Using the tool ensures that all references are updated accordingly whenever you change the account or password.</span></span> <span data-ttu-id="ad5a4-116">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールは、次に示す追加手順を実行することで、レポート サーバーを利用可能な状態に維持します。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-116">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool performs the following additional steps to ensure the report server remains available:</span></span>  
  
- <span data-ttu-id="ad5a4-117">ローカル コンピューター上に作成されたレポート サーバー グループに、新しいアカウントを自動的に追加します。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-117">Automatically adds the new account to the report server group created on the local computer.</span></span> <span data-ttu-id="ad5a4-118">このグループは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ファイルをセキュリティで保護するアクセス制御リスト (ACL) 内で指定されます。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-118">This group is specified in the access control lists (ACLs) that secure [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] files.</span></span>  
  
- <span data-ttu-id="ad5a4-119">レポート サーバー データベースをホストするために使用される [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスのログイン権限を自動的に更新します。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-119">Automatically updates the login permissions on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance used to host the report server database.</span></span> <span data-ttu-id="ad5a4-120">新しいアカウントは **RSExecRole**に追加されます。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-120">The new account will be added to the **RSExecRole**.</span></span>  
  
     <span data-ttu-id="ad5a4-121">古いアカウントのデータベース ログインは自動的に削除されません。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-121">The database login for the old account will not be removed automatically.</span></span> <span data-ttu-id="ad5a4-122">使用されなくなったするアカウントは削除するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-122">Be sure to remove accounts that are no longer in use.</span></span> <span data-ttu-id="ad5a4-123">詳細については、SQL Server オンラインブックの「[レポート サーバー データベースの管理 &#40;SSRS ネイティブ モード&#41;](../report-server/report-server-database-ssrs-native-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-123">For more information, see [Administer a Report Server Database &#40;SSRS Native Mode&#41;](../report-server/report-server-database-ssrs-native-mode.md) in SQL Server Books Online.</span></span>  
  
     <span data-ttu-id="ad5a4-124">新しいサービス アカウントにデータベース権限が与えられるのは、そのサービス アカウントを最初に使用するようにレポート サーバー データベース接続を構成した場合に限られます。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-124">Granting database permissions to new service account only occurs if you configured the report server database connection to use the service account in the first place.</span></span> <span data-ttu-id="ad5a4-125">ドメイン ユーザー アカウントまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース ログインを使用するようにレポート サーバー データベース接続を構成した場合は、サービス アカウントを更新しても接続情報には影響しません。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-125">If you configured the report server database connection to use a domain user account or a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database login, the connection information is not affected by the service account update.</span></span>  
  
- <span data-ttu-id="ad5a4-126">暗号化キーを自動的に更新し、新しいアカウントのプロファイル情報を取り込みます。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-126">Automatically updates the encryption key to include the profile information of the new account.</span></span>  
  
    > [!NOTE]  
    > <span data-ttu-id="ad5a4-127">レポート サーバーがスケールアウト配置の一部である場合、更新するレポート サーバーのみが影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-127">If the report server is part of the scale-out deployment, only the report server that you are updating is affected.</span></span> <span data-ttu-id="ad5a4-128">配置内の他のレポート サーバーの暗号化キーは、サービス アカウントを変更しても影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-128">The encryption keys for other report servers in the deployment are unaffected by the service account change.</span></span>  
  
 <span data-ttu-id="ad5a4-129">アカウントを設定する方法については、「[サービスアカウント &#40;SSRS Configuration Manager&#41;を構成](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-129">For instructions on how to set the account, see [Configure a Service Account &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md).</span></span>  
  
## <a name="choosing-an-account"></a><span data-ttu-id="ad5a4-130">アカウントの選択</span><span class="sxs-lookup"><span data-stu-id="ad5a4-130">Choosing an Account</span></span>

 <span data-ttu-id="ad5a4-131">レポート サーバー サービスは、次に示すアカウントの種類のいずれかで実行するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-131">You can configure the Report Server service to run under any of these account types:</span></span>  
  
- <span data-ttu-id="ad5a4-132">最も特権の少ない Windows ユーザー アカウント</span><span class="sxs-lookup"><span data-stu-id="ad5a4-132">Least-privileged Windows user account</span></span>  
  
- <span data-ttu-id="ad5a4-133">NetworkService</span><span class="sxs-lookup"><span data-stu-id="ad5a4-133">NetworkService</span></span>  
  
- <span data-ttu-id="ad5a4-134">LocalSystem</span><span class="sxs-lookup"><span data-stu-id="ad5a4-134">LocalSystem</span></span>  
  
- <span data-ttu-id="ad5a4-135">LocalService</span><span class="sxs-lookup"><span data-stu-id="ad5a4-135">LocalService</span></span>  
  
 <span data-ttu-id="ad5a4-136">アカウントの種類の選択については最適な方法が 1 つだけ存在するわけではなく、</span><span class="sxs-lookup"><span data-stu-id="ad5a4-136">There is no single best approach for choosing an account type.</span></span> <span data-ttu-id="ad5a4-137">アカウントごとに考慮する必要がある利点と欠点があります。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-137">Each account has advantages and disadvantages that you must consider.</span></span> <span data-ttu-id="ad5a4-138">実稼働サーバーに [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を配置する場合のベスト プラクティスは、共有アカウントが悪意のあるユーザーによって悪用された場合に被害が拡大しないように、サービスをドメイン ユーザー アカウントで実行することです。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-138">If you are deploying [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] on a production server, best practices suggest that you configure the service to run under a domain user account so that you can avoid widespread damage if a shared account is compromised by a malicious user.</span></span> <span data-ttu-id="ad5a4-139">これによって、このアカウントのログオンの利用状況も容易に監査できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-139">It also makes it easier to audit the logon activity for this account.</span></span> <span data-ttu-id="ad5a4-140">Windows ユーザー アカウントを使用する場合のトレードオフとして、Kerberos 認証を使用するネットワークに [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を配置する場合、このユーザー アカウントでサービスを登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-140">A trade-off to using a Windows user account is that if you are deploying [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in a network that uses Kerberos authentication, you must register the service with the user account.</span></span> <span data-ttu-id="ad5a4-141">詳細については、「[レポート サーバーのサービス プリンシパル名 &#40;SPN&#41; の登録](../report-server/register-a-service-principal-name-spn-for-a-report-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-141">For more information, see [Register a Service Principal Name &#40;SPN&#41; for a Report Server](../report-server/register-a-service-principal-name-spn-for-a-report-server.md).</span></span>  
  
 <span data-ttu-id="ad5a4-142">次に示すガイドラインとリンクは、配置に最適な方法を決定するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-142">The following guidelines and links in this section can help you decide on an approach that is best for your deployment.</span></span>  
  
- <span data-ttu-id="ad5a4-143">[サービスアカウント &#40;SSRS ネイティブモード&#41;](../../sql-server/install/service-account-ssrs-native-mode.md)です。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-143">[Service Account &#40;SSRS Native Mode&#41;](../../sql-server/install/service-account-ssrs-native-mode.md).</span></span>  
  
- <span data-ttu-id="ad5a4-144">SQL Server のオンライン ブックの「[Windows サービス アカウントと権限の構成](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md) 」。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-144">[Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md) in SQL Server Books Online.</span></span>  
  
- <span data-ttu-id="ad5a4-145">[サービスおよびサービス アカウントのセキュリティ計画ガイド](http://usergroup.doubletake.com/file_cabinet/download/0x000021733)。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-145">[The Services and Service Accounts Security Planning Guide](http://usergroup.doubletake.com/file_cabinet/download/0x000021733).</span></span>  
  
## <a name="updating-an-expired-password"></a><span data-ttu-id="ad5a4-146">期限切れのパスワードの更新</span><span class="sxs-lookup"><span data-stu-id="ad5a4-146">Updating an Expired Password</span></span>

 <span data-ttu-id="ad5a4-147">レポート サーバー サービスがドメイン アカウントで実行されている場合に、Reporting Services 構成ツールでパスワードを更新する前にパスワードの有効期限が切れると、新しいパスワードを指定するまでこのサービスが開始されなくなります。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-147">If the Report Server service runs under a domain account and the password expires before you can update it in the Reporting Services Configuration tool, the service will not start until you specify a new password.</span></span> <span data-ttu-id="ad5a4-148">サービスを開始できないと、Reporting Services 構成ツールを使用してサーバーに接続できなくなり、アカウントを更新できません。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-148">If the service cannot be started, you cannot use the Reporting Services Configuration tool to connect to that server to update the account.</span></span> <span data-ttu-id="ad5a4-149">この場合は、複数のツールを併用してサーバーをオンラインに戻す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-149">In this case, you must use a combination of tools to bring the server back online.</span></span>  
  
 <span data-ttu-id="ad5a4-150">パスワードをリセットするには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-150">To reset the password, do the following:</span></span>  
  
1. <span data-ttu-id="ad5a4-151">[**スタート**] ボタンをクリックし、[**コントロールパネル**]、[**管理ツール**] の順にポイントして、[**サービス**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-151">On the **Start** menu, point to **Control Panel**, point to **Administrator Tools**, and click **Services**.</span></span>  
  
2. <span data-ttu-id="ad5a4-152">**SQL Server Reporting Services**を右クリックし、[**プロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-152">Right-click **SQL Server Reporting Services**, select **Properties**.</span></span>  
  
3. <span data-ttu-id="ad5a4-153">[**ログオン**] をクリックし、新しいパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-153">Click **Log On**, and type the new password.</span></span>  
  
4. <span data-ttu-id="ad5a4-154">パスワードを変更したら、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールを起動し、[サービス アカウント] ページでパスワードを更新します。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-154">After you update the password, start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and update the password in the Service Account page.</span></span> <span data-ttu-id="ad5a4-155">この追加の手順は、レポート サーバーによって内部的に保存されているアカウント情報を更新するために必要です。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-155">This additional step is necessary to update the account information that is stored internally by the report server.</span></span>  
  
 <span data-ttu-id="ad5a4-156">[!INCLUDE[ssDE](../../includes/ssde-md.md)]のサービス アカウントのパスワードの有効期限が切れると、レポート サーバーへの接続時に `rsReportServerDatabaseUnavailable` エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-156">If the service account password for the [!INCLUDE[ssDE](../../includes/ssde-md.md)] expires, the `rsReportServerDatabaseUnavailable` error occurs when you try to connect to the report server.</span></span> <span data-ttu-id="ad5a4-157">パスワードを再設定すると、このエラーは解決されます。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-157">Resetting the password resolves this error.</span></span>  
  
## <a name="configuring-the-report-server-service-for-a-sharepoint-integrated-report-server"></a><span data-ttu-id="ad5a4-158">SharePoint 統合レポート サーバーのレポート サーバー サービスの構成</span><span class="sxs-lookup"><span data-stu-id="ad5a4-158">Configuring the Report Server Service for a SharePoint Integrated Report Server</span></span>

 <span data-ttu-id="ad5a4-159">SharePoint 統合モードでレポート サーバーを実行している場合は、次のいずれかの状況のときに、SharePoint 構成データベースに保存されているサービス アカウント情報を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-159">If you are running a report server in SharePoint integrated mode, you must update the service account information that is stored in the SharePoint configuration database if either of the following conditions are true:</span></span>  
  
- <span data-ttu-id="ad5a4-160">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アカウントを変更する場合 (たとえば、NetworkService からドメイン ユーザー アカウントに切り替える場合など)。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-160">Modifying the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service account (for example, switching from NetworkService to a domain user account).</span></span>  
  
- <span data-ttu-id="ad5a4-161">SharePoint ファームを拡張して追加の SharePoint Web アプリケーションを組み込む場合。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-161">Extending a SharePoint farm to include an additional SharePoint Web application.</span></span> <span data-ttu-id="ad5a4-162">サーバー ファームがレポート サーバー統合用に構成されている場合に、新たに追加されたアプリケーションがファーム内の他のアプリケーションとは異なるユーザー アカウントで実行されるように構成されているときは、データベース アクセス情報を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-162">If the server farm is configured for report server integration, and newly added application is configured to run under a different user account than other applications in the farm, you must update the database access information.</span></span>  
  
 <span data-ttu-id="ad5a4-163">データベース アクセス情報を再設定した後は、古い接続が引き続き使用されないように [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] サービスを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-163">After you reset the database access information, you should then restart the [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] service to ensure that the old connection is no longer used.</span></span>  
  
1. <span data-ttu-id="ad5a4-164">[**管理ツール**] で、[ **SharePoint 2010 サーバーの全体管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-164">In **Administrative Tools**, click **SharePoint 2010 Central Administration**.</span></span>  
  
2. <span data-ttu-id="ad5a4-165">[**アプリケーション管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-165">Click **Application Management**.</span></span>  
  
3. <span data-ttu-id="ad5a4-166">[Reporting Services] セクションで、[**データベースアクセスの許可**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-166">In the Reporting Services section, click **Grant Database Access**.</span></span>  
  
4. <span data-ttu-id="ad5a4-167">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-167">Click **OK**.</span></span> <span data-ttu-id="ad5a4-168">[資格情報の入力] ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-168">The Enter Credentials dialog box appears.</span></span>  
  
5. <span data-ttu-id="ad5a4-169">レポート サーバーをホストするコンピューター上のローカルの管理者グループに属しているユーザーの資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-169">Enter the credentials of a user who is a member of the Local Administrator's group on the computer that hosts the report server.</span></span> <span data-ttu-id="ad5a4-170">この資格情報は、サービス アカウント情報を取得する目的のために、レポート サーバー コンピューターへの一度だけの接続に使用されます。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-170">The credentials will be used for a one-time connection to the report server computer for the purpose of retrieving service account information.</span></span> <span data-ttu-id="ad5a4-171">各サービス アカウントに対して作成されたデータベース ログインは、SharePoint データベース内で更新されます。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-171">The database login that is created for each service account will be updated in SharePoint databases.</span></span>  
  
6. <span data-ttu-id="ad5a4-172">サービスを再起動するには、[**操作**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-172">To restart the service, click **Operations**.</span></span>  
  
7. <span data-ttu-id="ad5a4-173">[トポロジおよびサービス] で、[**サーバーのサービス**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-173">In Topology and Services, click **Services on Server**.</span></span>  
  
8. <span data-ttu-id="ad5a4-174">Windows SharePoint Services Web アプリケーションの場合は、[**停止**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-174">For Windows SharePoint Services Web Application, click **Stop**.</span></span>  
  
9. <span data-ttu-id="ad5a4-175">サービスが停止するまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-175">Wait for the service stop.</span></span>  
  
10. <span data-ttu-id="ad5a4-176">**[開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-176">Click **Start**.</span></span>  
  
> [!NOTE]  
> <span data-ttu-id="ad5a4-177">SharePoint 製品およびテクノロジでは、reporting services SharePoint モードのようなサービス構成のためにドメインアカウントが必要です。</span><span class="sxs-lookup"><span data-stu-id="ad5a4-177">SharePoint products and technologies require domain accounts for service configuration like reporting services SharePoint mode.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ad5a4-178">次の手順</span><span class="sxs-lookup"><span data-stu-id="ad5a4-178">Next Steps</span></span>

 <span data-ttu-id="ad5a4-179">Ssrs [Configuration Manager&#41;サービスアカウントのサービスアカウントを構成 &#40;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md) Ssrs[ネイティブモード &#40;](../../sql-server/install/service-account-ssrs-native-mode.md) [レポートサーバーの url&#41;Ssrs &#40;Configuration Manager](configure-report-server-urls-ssrs-configuration-manager.md)&#41;Reporting Services Configuration Manager[ネイティブモード &#40;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)</span><span class="sxs-lookup"><span data-stu-id="ad5a4-179">[Configure a Service Account &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md) [Service Account &#40;SSRS Native Mode&#41;](../../sql-server/install/service-account-ssrs-native-mode.md) [Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](configure-report-server-urls-ssrs-configuration-manager.md) [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)</span></span>
