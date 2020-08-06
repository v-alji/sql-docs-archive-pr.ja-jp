---
title: サービスアカウント (SSRS ネイティブモード) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.serviceaccount.F1
ms.assetid: face8120-4d32-4c6c-a1e8-99f27d1ff15d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 2734be073896dbf41e3628c43b78ea30f80b6adc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720817"
---
# <a name="service-account-ssrs-native-mode"></a><span data-ttu-id="fc866-102">サービス アカウント (SSRS ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="fc866-102">Service Account (SSRS Native Mode)</span></span>
  <span data-ttu-id="fc866-103">[サービス アカウント] ページを使用すると、レポート サーバー サービスを実行するアカウントを指定できます。</span><span class="sxs-lookup"><span data-stu-id="fc866-103">Use the Service Account page to specify the account under which the Report Server service runs.</span></span> <span data-ttu-id="fc866-104">このアカウントは、最初はセットアップ中に構成されます。</span><span class="sxs-lookup"><span data-stu-id="fc866-104">This account is initially configured during Setup.</span></span> <span data-ttu-id="fc866-105">アカウントまたはパスワードの変更が必要な場合は、変更を加えることができます。</span><span class="sxs-lookup"><span data-stu-id="fc866-105">You can modify it if you want to change the account or password.</span></span> <span data-ttu-id="fc866-106">レポート サーバー Web サービス、レポート マネージャー、およびバックグラウンド処理アプリケーションは、いずれもこのページで指定したサービス ID で実行されます。</span><span class="sxs-lookup"><span data-stu-id="fc866-106">The Report Server Web service, Report Manager, and the background processing application all run under the service identity you specify on this page.</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="fc866-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ネイティブモード。</span><span class="sxs-lookup"><span data-stu-id="fc866-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
 <span data-ttu-id="fc866-108">レポート サーバー サービス用に指定するアカウントには、レジストリ、レポート サーバー プログラム ファイル、およびレポート サーバー データベースにアクセスするための権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="fc866-108">The account you specify for the Report Server service requires permission to access the registry, report server program files, and the report server database.</span></span> <span data-ttu-id="fc866-109">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを使用してアカウントを設定すると、アカウントに対してすべての権限が自動的に構成されます。</span><span class="sxs-lookup"><span data-stu-id="fc866-109">All permissions are configured for the account automatically when you use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager to set the account.</span></span> <span data-ttu-id="fc866-110">サービスアカウントを使用してレポートサーバーデータベースに接続する場合、Configuration Manager によってアカウントのデータベースログインが作成され、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レポートサーバーデータベースをホストするインスタンスの RSExecRole にアカウントが割り当てられてデータベース権限が構成されます。</span><span class="sxs-lookup"><span data-stu-id="fc866-110">If you use the service account to connect to the report server database, the Configuration Manager creates a database login for the account and configures database permissions by assigning the account to the RSExecRole on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that hosts the report server database.</span></span> <span data-ttu-id="fc866-111">レポート サーバー データベースは、レポート サーバーが書き込みを行う唯一のデータ ストアです。</span><span class="sxs-lookup"><span data-stu-id="fc866-111">The report server database is the only data store that a report server writes to.</span></span> <span data-ttu-id="fc866-112">それ以外のデータ ストアに対する権限は、サービス アカウントには必要ありません。</span><span class="sxs-lookup"><span data-stu-id="fc866-112">The service account does not require permissions to any other data stores.</span></span>  
  
 <span data-ttu-id="fc866-113">このページを開くには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを起動して、ナビゲーション ウィンドウでリンクを選択します。</span><span class="sxs-lookup"><span data-stu-id="fc866-113">To open this page, start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager and select the link in the navigation pane.</span></span> <span data-ttu-id="fc866-114">詳細については、「 [Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc866-114">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fc866-115">アカウントまたはパスワードを更新する場合は、常に [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを使用することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fc866-115">Whenever you need to update the account or password, it is strongly recommended that you use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="fc866-116">構成マネージャーを使用してアカウントを更新すると、サービス ID に依存する他の内部設定が自動的に同時に更新されます。</span><span class="sxs-lookup"><span data-stu-id="fc866-116">Using the Configuration Manager to update the account ensures that other internal settings that depend on the service identity are automatically updated at the same time.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fc866-117">Options</span><span class="sxs-lookup"><span data-stu-id="fc866-117">Options</span></span>  
 <span data-ttu-id="fc866-118">**[ビルトイン アカウントを使用する]**</span><span class="sxs-lookup"><span data-stu-id="fc866-118">**Use a built-in account**</span></span>  
 <span data-ttu-id="fc866-119">一覧から **[ネットワーク サービス]**、 **[ローカル システム]**、または **[ローカル サービス]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="fc866-119">Select **Network Service**, **Local System**, or **Local Service** from the list.</span></span> <span data-ttu-id="fc866-120">推奨されるのは **[ネットワーク サービス]** だけですが、使用可能な任意のアカウントを使用するようにアカウントを構成できます。</span><span class="sxs-lookup"><span data-stu-id="fc866-120">Only **Network Service** is recommended; however, you can configure the account to use any account that is available.</span></span>  
  
 <span data-ttu-id="fc866-121">**[他のアカウントを使用する]**</span><span class="sxs-lookup"><span data-stu-id="fc866-121">**Use another account**</span></span>  
 <span data-ttu-id="fc866-122">Windows ユーザー アカウントを指定する場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="fc866-122">Select this option to specify a Windows user account.</span></span> <span data-ttu-id="fc866-123">ローカル Windows ユーザー アカウントまたはドメイン ユーザー アカウントを入力できます。</span><span class="sxs-lookup"><span data-stu-id="fc866-123">You can enter a local Windows user account or domain user account.</span></span> <span data-ttu-id="fc866-124">\* \<domain> \\<ユーザー \> \*の形式でドメインアカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="fc866-124">Specify a domain account in this format: *\<domain>\\<user\>*.</span></span> <span data-ttu-id="fc866-125">ローカル Windows ユーザーアカウントは、 \* \<computer name> \\<user \> \*の形式で指定します。</span><span class="sxs-lookup"><span data-stu-id="fc866-125">Specify a local Windows user account in this format: *\<computer name>\\<user\>*.</span></span> <span data-ttu-id="fc866-126">このとき選択できるのは、既存のアカウントのみです。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成で新しいアカウントを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="fc866-126">You can only select an existing account; you cannot create new accounts in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration.</span></span>  
  
 <span data-ttu-id="fc866-127">アカウントの文字数の上限は 20 文字です。</span><span class="sxs-lookup"><span data-stu-id="fc866-127">The maximum character limit on the account is 20 characters.</span></span>  
  
 <span data-ttu-id="fc866-128">ネットワークが Kerberos 認証を使用している場合に、ドメイン ユーザー アカウントで実行されるようにレポート サーバーを構成するには、サービスをユーザー アカウントに登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fc866-128">If your network uses Kerberos authentication and you configure the report server to run under a domain user account, you must register the service with the user account.</span></span> <span data-ttu-id="fc866-129">詳細については、「[レポート サーバーのサービス プリンシパル名 &#40;SPN&#41; の登録](../../reporting-services/report-server/register-a-service-principal-name-spn-for-a-report-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc866-129">For more information, see [Register a Service Principal Name &#40;SPN&#41; for a Report Server](../../reporting-services/report-server/register-a-service-principal-name-spn-for-a-report-server.md).</span></span>  
  
 <span data-ttu-id="fc866-130">たとえば、ある Windows アカウントを別のアカウントで置き換えたり、ビルトイン アカウントを Windows ドメイン アカウントで置き換えたりするなどしてアカウントの種類を切り替えると、暗号化キーのバックアップ コピーを作成するように求めるプロンプトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="fc866-130">If you switch the account type (for example, replacing one Windows account with another or replacing a built-in account with a Windows domain account), you will be prompted to create a backup copy of the encryption key.</span></span> <span data-ttu-id="fc866-131">新しいアカウントを選択すると、バックアップ コピーが自動的に復元されます。</span><span class="sxs-lookup"><span data-stu-id="fc866-131">The backup copy will be restored automatically when you select the new account.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fc866-132">サービス アカウントを変更するたびに、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーから暗号化キーのバックアップと復元を求められます。</span><span class="sxs-lookup"><span data-stu-id="fc866-132">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration manager prompts you to back up and restore the encryption key whenever you modify the service account.</span></span> <span data-ttu-id="fc866-133">この手順は、暗号化されたデータをレポート サーバーが使用できるようにするために必要です。</span><span class="sxs-lookup"><span data-stu-id="fc866-133">These steps are necessary for ensuring that encrypted data remains available to the report server.</span></span> <span data-ttu-id="fc866-134">これらのアクションの詳細については、「[暗号化キー &#40;SSRS ネイティブモード&#41;](../../../2014/sql-server/install/encryption-keys-ssrs-native-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc866-134">For more information about these actions, see [Encryption Keys &#40;SSRS Native Mode&#41;](../../../2014/sql-server/install/encryption-keys-ssrs-native-mode.md).</span></span>  
  
 <span data-ttu-id="fc866-135">さらに、SharePoint 統合モードで実行するように構成されているレポート サーバーを使用している場合に [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを使用してサービス アカウントを変更するには、SharePoint サーバーの全体管理を開き、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] **[データベース アクセスの許可]** ページを使用してレポート サーバーとインスタンスの設定を再適用する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="fc866-135">Additionally, if you have a report server that is configured to run in SharePoint Integrated mode and you change the service account by using the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager, you must also open SharePoint Central Administration and use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] **Grant Database Access** page to re-apply the report server and instance settings.</span></span> <span data-ttu-id="fc866-136">この操作により、新しいサービス アカウントには、SharePoint データベースへのアクセスが許可されます。これは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を SharePoint の製品またはテクノロジと統合する場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="fc866-136">This step will grant the new service account access to the SharePoint databases, which is required for integrating [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] with a SharePoint product or technology.</span></span> <span data-ttu-id="fc866-137">SharePoint サーバーの全体管理でデータベースへのアクセス権を付与する方法の詳細については、「[レポートサーバーの構成と管理](../../../2014/reporting-services/configure-administer-report-server-reporting-services-sharepoint-mode.md)」を参照してください。 &#40;Reporting Services sharepoint モード&#41;および[Reporting Services Sharepoint モードのインストール &#40;SharePoint 2010 および sharepoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)です。</span><span class="sxs-lookup"><span data-stu-id="fc866-137">For more information about how to grant database access in SharePoint Central Administration, see [Configuration and Administration of a Report Server &#40;Reporting Services SharePoint Mode&#41;](../../../2014/reporting-services/configure-administer-report-server-reporting-services-sharepoint-mode.md) and [Reporting Services SharePoint Mode Installation &#40;SharePoint 2010 and SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md).</span></span>  
  
## <a name="choosing-an-account"></a><span data-ttu-id="fc866-138">アカウントの選択</span><span class="sxs-lookup"><span data-stu-id="fc866-138">Choosing an Account</span></span>  
 <span data-ttu-id="fc866-139">最良の結果を得るには、ネットワーク接続権限があり、ネットワーク ドメイン コントローラーおよび会社の SMTP サーバーまたはゲートウェイにアクセスできるアカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="fc866-139">For best results, specify an account that has network connection permissions, with access to network domain controllers and corporate SMTP servers or gateways.</span></span> <span data-ttu-id="fc866-140">次の表に、アカウントの概要およびアカウントの使用に関する推奨事項を示します。</span><span class="sxs-lookup"><span data-stu-id="fc866-140">The following table summarizes the accounts and provides recommendations for using them.</span></span>  
  
|<span data-ttu-id="fc866-141">Account</span><span class="sxs-lookup"><span data-stu-id="fc866-141">Account</span></span>|<span data-ttu-id="fc866-142">説明</span><span class="sxs-lookup"><span data-stu-id="fc866-142">Explanation</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fc866-143">ドメイン ユーザー アカウント</span><span class="sxs-lookup"><span data-stu-id="fc866-143">Domain user accounts</span></span>|<span data-ttu-id="fc866-144">レポート サーバーの操作に必要な最小限の権限を持つ Windows ドメイン ユーザー アカウントがある場合は、それを使用してください。</span><span class="sxs-lookup"><span data-stu-id="fc866-144">If you have a Windows domain user account that has the minimum permissions required for report server operations, you should use it.</span></span><br /><br /> <span data-ttu-id="fc866-145">レポート サーバー サービスが他のアプリケーションから切り離されるため、ドメイン ユーザー アカウントの使用をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fc866-145">A domain user account is recommended because it isolates the Report Server service from other applications.</span></span> <span data-ttu-id="fc866-146">ネットワーク サービスなどの共有アカウントで複数のアプリケーションを実行すると、悪意のあるユーザーにレポート サーバーを制御されるリスクが増大します。これは、あるアプリケーションに対するセキュリティ侵害が、同じアカウントで実行されるすべてのアプリケーションへと容易に拡大するためです。</span><span class="sxs-lookup"><span data-stu-id="fc866-146">Running multiple applications under a shared account, such as Network Service, increases the risk of a malicious user taking control of the report server because a security breach for any one application can easily extend to all applications that run under the same account.</span></span><br /><br /> <span data-ttu-id="fc866-147">ドメイン ユーザー アカウントが必要となるのは、レポート サーバーで制約付き委任を構成する場合、または、ビルトイン コンピューター アカウントではなくドメイン ユーザー アカウントを必要とする SharePoint 2010 製品との SharePoint 統合モードを構成する場合です。</span><span class="sxs-lookup"><span data-stu-id="fc866-147">A domain user account is required if you are configuring the report server for constrained delegation, or for SharePoint integrated mode with SharePoint 2010 Products which require domain user accounts rather than built-in machine accounts.</span></span><br /><br /> <span data-ttu-id="fc866-148">パスワードの有効期限ポリシーを実施する組織でドメイン ユーザー アカウントを使用する場合は、パスワードを定期的に変更する必要があるので注意してください。</span><span class="sxs-lookup"><span data-stu-id="fc866-148">Note that if you use a domain user account, you will have to change the password periodically if your organization enforces a password expiration policy.</span></span> <span data-ttu-id="fc866-149">また、場合によってはサービスをユーザー アカウントに登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fc866-149">You might also need to register the service with the user account.</span></span> <span data-ttu-id="fc866-150">詳細については、「[レポート サーバーのサービス プリンシパル名 &#40;SPN&#41; の登録](../../reporting-services/report-server/register-a-service-principal-name-spn-for-a-report-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc866-150">For more information, see [Register a Service Principal Name &#40;SPN&#41; for a Report Server](../../reporting-services/report-server/register-a-service-principal-name-spn-for-a-report-server.md).</span></span><br /><br /> <span data-ttu-id="fc866-151">ローカル Windows ユーザー アカウントは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="fc866-151">Avoid using a local Windows user account.</span></span> <span data-ttu-id="fc866-152">一般に、ローカル アカウントには、他のコンピューター上のリソースにアクセスするための十分な権限が与えられていません。</span><span class="sxs-lookup"><span data-stu-id="fc866-152">Local accounts typically do not have sufficient permission to access resources on other computers.</span></span> <span data-ttu-id="fc866-153">ローカル アカウントを使用した場合にレポート サーバーの機能がどのように制限されるかについては、このトピックの「 [ローカル アカウントの使用に関する注意点](#localaccounts) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc866-153">For more information about how using a local account limits report server functionality, see [Considerations for Using Local Accounts](#localaccounts) in this topic.</span></span>|  
|<span data-ttu-id="fc866-154">**ネットワークサービス**</span><span class="sxs-lookup"><span data-stu-id="fc866-154">**Network Service**</span></span>|<span data-ttu-id="fc866-155">**ネットワーク サービス** は、ネットワークへのログオン権限を持つ最小特権のビルトイン アカウントです。</span><span class="sxs-lookup"><span data-stu-id="fc866-155">**Network Service** is a built-in least-privilege account that has network logon permissions.</span></span> <span data-ttu-id="fc866-156">使用できるドメイン ユーザー アカウントがない場合や、パスワード有効期限ポリシーが原因でサービスが中断されないようにする場合は、このアカウントの使用をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fc866-156">This account is recommended if you do not have a domain user account available or if you want to avoid any service disruptions that might occur as a result of password expiration policies.</span></span><br /><br /> <span data-ttu-id="fc866-157">**[ネットワーク サービス]** を選択する場合は、同じアカウントで実行される他のサービスの数を最小限に抑えてください。</span><span class="sxs-lookup"><span data-stu-id="fc866-157">If you select **Network Service**, try to minimize the number of other services that run under the same account.</span></span> <span data-ttu-id="fc866-158">あるアプリケーションに対するセキュリティ侵害が、同じアカウントで実行される他のすべてのアプリケーションのセキュリティを損なうことになります。</span><span class="sxs-lookup"><span data-stu-id="fc866-158">A security breach for any one application will compromise the security of all other applications that run under the same account.</span></span>|  
|<span data-ttu-id="fc866-159">**ローカル サービス**</span><span class="sxs-lookup"><span data-stu-id="fc866-159">**Local Service**</span></span>|<span data-ttu-id="fc866-160">**ローカル サービス** は、認証済みのローカル Windows ユーザー アカウントに似たビルトイン アカウントです。</span><span class="sxs-lookup"><span data-stu-id="fc866-160">**Local Service** is a built-in account that is like an authenticated local Windows user account.</span></span> <span data-ttu-id="fc866-161">**ローカル サービス** アカウントとして実行されるサービスは、資格情報を使用せずに NULL セッションとしてネットワーク リソースにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="fc866-161">Services that run as the **Local Service** account access network resources as a null session with no credentials.</span></span> <span data-ttu-id="fc866-162">イントラネットに配置するシナリオでは、レポート サーバーがレポートを開いたりサブスクリプションを処理したりする前に、リモートのレポート サーバー データベースまたはネットワーク ドメイン コントローラーに接続してユーザーを認証する必要があるため、このアカウントは適していません。</span><span class="sxs-lookup"><span data-stu-id="fc866-162">This account is not appropriate for intranet deployment scenarios where the report server must connect to a remote report server database or a network domain controller to authenticate a user prior to opening a report or processing a subscription.</span></span>|  
|<span data-ttu-id="fc866-163">**ローカル システム**</span><span class="sxs-lookup"><span data-stu-id="fc866-163">**Local System**</span></span>|<span data-ttu-id="fc866-164">**ローカル システム** は、レポート サーバーの実行には必要のない高い特権のアカウントです。</span><span class="sxs-lookup"><span data-stu-id="fc866-164">**Local System** is a highly privileged account that is not required for running a report server.</span></span> <span data-ttu-id="fc866-165">レポート サーバーのインストールにこのアカウントを使用することは避けてください。</span><span class="sxs-lookup"><span data-stu-id="fc866-165">Avoid this account for report server installations.</span></span> <span data-ttu-id="fc866-166">代わりに、ドメイン アカウントまたは **ネットワーク サービス** を使用してください。</span><span class="sxs-lookup"><span data-stu-id="fc866-166">Choose a domain account or **Network Service** instead.</span></span>|  
  
##  <a name="considerations-for-using-local-accounts"></a><a name="localaccounts"></a><span data-ttu-id="fc866-167">ローカルアカウントの使用に関する注意点</span><span class="sxs-lookup"><span data-stu-id="fc866-167">Considerations for Using Local Accounts</span></span>  
 <span data-ttu-id="fc866-168">ローカル アカウントを使用する場合の主な注意点は、レポート サーバーがリモートのデータベース サーバー、メール サーバー、およびドメイン コントローラーにアクセスする必要があるかどうかということです。</span><span class="sxs-lookup"><span data-stu-id="fc866-168">The primary consideration for using local accounts is whether the report server requires access to remote database servers, mail servers, and domain controllers.</span></span> <span data-ttu-id="fc866-169">レポート サーバーをローカル Windows ユーザー アカウント、ローカル サービス、またはローカル システムとして実行されるように構成する場合は、他の構成の設定方法やサブスクリプションの作成と配信に関して次の点を考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fc866-169">If you configure the report server to run as a local Windows user account, Local Service, or Local System, you introduce considerations that must be factored into how you set other configuration settings, and on subscription creation and delivery:</span></span>  
  
-   <span data-ttu-id="fc866-170">ローカル アカウントでサービスを実行すると、後でリモートのレポート サーバー データベースへの接続を構成する場合に選択肢が限られます。</span><span class="sxs-lookup"><span data-stu-id="fc866-170">Running the service under a local account will limit your options later if you configure a connection to a remote report server database.</span></span> <span data-ttu-id="fc866-171">具体的には、リモートのレポート サーバー データベースを使用している場合、リモートの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにログオンする権限のあるドメイン ユーザー アカウントまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース ユーザーを使用するように接続を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fc866-171">Specifically, if you are using a remote report server database, you will have to configure the connection to use a domain user account or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database user that has permission to log on to the remote [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
-   <span data-ttu-id="fc866-172">ローカル アカウントでサービスを実行すると、サブスクリプションの作成に関して新しい要件が発生します。</span><span class="sxs-lookup"><span data-stu-id="fc866-172">Running the service under a local account will introduce new requirements on subscription creation.</span></span> <span data-ttu-id="fc866-173">レポート サーバーでは、サブスクリプションを作成するユーザーに関する情報が保存されます。</span><span class="sxs-lookup"><span data-stu-id="fc866-173">The report server stores information about the user who creates the subscription.</span></span> <span data-ttu-id="fc866-174">ユーザーがドメイン アカウントでログオン中にサブスクリプションを作成すると、サブスクリプションの処理時に、レポート サーバー サービスがドメイン コントローラーに接続してユーザーを認証しようとします。</span><span class="sxs-lookup"><span data-stu-id="fc866-174">If the user creates the subscription while logged on under a domain account, the Report Server service will try to connect to a domain controller to authenticate the user when the subscription is processed.</span></span> <span data-ttu-id="fc866-175">サービスがローカル アカウントで実行されていると、レポート サーバーからリモート ドメイン コントローラーに認証の要求が送信される際にその要求が失敗します。</span><span class="sxs-lookup"><span data-stu-id="fc866-175">If the service runs under a local account, the authentication request will fail when the report server tries to send the request to a remote domain controller.</span></span> <span data-ttu-id="fc866-176">この制限に対処するには、カスタムのフォームベースの認証拡張機能を使用するか、レポート サーバーへのすべてのユーザー接続をローカル ユーザー アカウントで行うようにします。</span><span class="sxs-lookup"><span data-stu-id="fc866-176">To work around this limitation, you can use a custom forms-based authentication extension or have all users connect to a report server under a local user account.</span></span>  
  
-   <span data-ttu-id="fc866-177">ローカル アカウントでサービスを実行すると、サブスクリプションの配信に関して新しい要件が発生します。</span><span class="sxs-lookup"><span data-stu-id="fc866-177">Running the service under a local account will introduce new requirements for subscription delivery.</span></span> <span data-ttu-id="fc866-178">一部の配信拡張機能では、ユーザーのアカウント情報がサブスクリプション定義内に保持されます。</span><span class="sxs-lookup"><span data-stu-id="fc866-178">Some delivery extensions have user account information in the subscription definition.</span></span> <span data-ttu-id="fc866-179">レポート サーバー サービスをローカル アカウントで実行しているときに、ドメイン ユーザー アカウントに基づく電子メール アドレスにレポートを送信すると、サービスがリモート ドメイン コントローラーに接続できず、送信先の電子メール アカウントを解決できません。</span><span class="sxs-lookup"><span data-stu-id="fc866-179">If you are sending reports to e-mail addresses that are based on domain user accounts and you run the Report Server service under a local account, it cannot access a remote domain controller to resolve the target e-mail account.</span></span>  
  
-   <span data-ttu-id="fc866-180">ドメイン コントローラーになっているコンピューターでは、ビルトイン Windows サービス アカウント (Local Service または Network Service) をレポート サーバーのサービス アカウントとして使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="fc866-180">Built-in Windows service accounts (Local Service or Network Service) are not supported as report server service accounts on a computer that is a domain controller.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc866-181">参照</span><span class="sxs-lookup"><span data-stu-id="fc866-181">See Also</span></span>  
 <span data-ttu-id="fc866-182">[レポート サーバー サービス アカウントの構成 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="fc866-182">[Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="fc866-183">[SSRS Configuration Manager &#40;サービスアカウントを構成&#41;](../../../2014/sql-server/install/configure-a-service-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="fc866-183">[Configure a Service Account &#40;SSRS Configuration Manager&#41;](../../../2014/sql-server/install/configure-a-service-account-ssrs-configuration-manager.md) </span></span>  
 [<span data-ttu-id="fc866-184">Reporting Services Configuration Manager F1 ヘルプトピック &#40;SSRS ネイティブモード&#41;</span><span class="sxs-lookup"><span data-stu-id="fc866-184">Reporting Services Configuration Manager F1 Help Topics &#40;SSRS Native Mode&#41;</span></span>](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)  
  
  