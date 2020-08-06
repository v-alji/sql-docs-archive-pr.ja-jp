---
title: リモート Integration Services サーバーへの接続 (SSIS サービス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- service [Integration Services], remote instance
- Integration Services service, connecting
- Integration Services service, remote instance
- service [Integration Services], connecting
ms.assetid: 9487aff1-44d8-42c1-8176-bb9891d4632d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 03c9c4f1c94e4599c2c14f407996431dabd493dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738598"
---
# <a name="connect-to-a-remote-integration-services-server-ssis-service"></a><span data-ttu-id="aeef0-102">リモートの Integration Services サーバーに接続する (SSIS サービス)</span><span class="sxs-lookup"><span data-stu-id="aeef0-102">Connect to a Remote Integration Services Server (SSIS Service)</span></span>
    
> [!IMPORTANT] 
> <span data-ttu-id="aeef0-103">このトピックでは、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを管理するための Windows サービスである [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="aeef0-103">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="aeef0-104">では、以前のリリースの [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]との互換性を維持するために、このサービスをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="aeef0-104">supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="aeef0-105">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]以降では、Integration Services サーバー上のパッケージなどのオブジェクトを管理できます。</span><span class="sxs-lookup"><span data-stu-id="aeef0-105">Starting in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], you can manage objects such as packages on the Integration Services server.</span></span>  
  
 <span data-ttu-id="aeef0-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] または他の管理アプリケーションからリモート サーバー上の [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のインスタンスに接続するには、アプリケーションのユーザーがそのサーバーに対して特定の権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="aeef0-106">Connecting to an instance of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] on a remote server, from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or another management application, requires a specific set of rights on the server for the users of the application.</span></span>  
  
> [!IMPORTANT] 
> <span data-ttu-id="aeef0-107">リモート サーバーに格納されるパッケージを管理するために、そのリモート サーバー上の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスのインスタンスに接続する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="aeef0-107">To manage packages that are stored on a remote server, you do not have to connect to the instance of the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service on that remote server.</span></span> <span data-ttu-id="aeef0-108">代わりに、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスの構成ファイルを編集し、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] でリモート サーバーに格納されているパッケージが表示されるようにします。</span><span class="sxs-lookup"><span data-stu-id="aeef0-108">Instead, edit the configuration file for the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service so that [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] displays the packages that are stored on the remote server.</span></span> <span data-ttu-id="aeef0-109">詳細については、「 [Integration Services サービスの構成 (SSIS サービス)](service/integration-services-service-ssis-service.md)との互換性を維持するために、このサービスをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="aeef0-109">For more information, see [Configuring the Integration Services Service &#40;SSIS Service&#41;](service/integration-services-service-ssis-service.md).</span></span>  
  
## <a name="connecting-to-integration-services-on-a-remote-server"></a><span data-ttu-id="aeef0-110">リモート サーバー上の Integration Services への接続</span><span class="sxs-lookup"><span data-stu-id="aeef0-110">Connecting to Integration Services on a Remote Server</span></span>  
  
#### <a name="to-connect-to-integration-services-on-a-remote-server"></a><span data-ttu-id="aeef0-111">リモート サーバー上の Integration Services に接続するには</span><span class="sxs-lookup"><span data-stu-id="aeef0-111">To connect to Integration Services on a Remote Server</span></span>  
  
1.  <span data-ttu-id="aeef0-112">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]を開きます。</span><span class="sxs-lookup"><span data-stu-id="aeef0-112">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="aeef0-113">**[ファイル]** メニューの **[オブジェクト エクスプローラーを接続]** をクリックして、 **[サーバーへの接続]** ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="aeef0-113">Select **File**, **Connect Object Explorer** to display the **Connect to Server** dialog box.</span></span>  
  
3.  <span data-ttu-id="aeef0-114">**[サーバーの種類]** ボックスの一覧で **[Integration Services]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="aeef0-114">Select **Integration Services** in the **Server type** list.</span></span>  
  
4.  <span data-ttu-id="aeef0-115">**[サーバー名]** テキスト ボックスに [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サーバーの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="aeef0-115">Type the name of a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server in the **Server name** text box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="aeef0-116">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスは、そのインスタンスに固有のものではありません。</span><span class="sxs-lookup"><span data-stu-id="aeef0-116">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is not instance-specific.</span></span> <span data-ttu-id="aeef0-117">このサービスに接続するには、Integration Services サービスが実行されているコンピューターの名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="aeef0-117">You connect to the service by using the name of the computer on which the Integration Services service is running.</span></span>  
  
5.  <span data-ttu-id="aeef0-118">**[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aeef0-118">Click **Connect**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aeef0-119">**[サーバーの参照]** ダイアログ ボックスには、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]のリモート インスタンスは表示されません。</span><span class="sxs-lookup"><span data-stu-id="aeef0-119">The **Browse for Servers** dialog box does not display remote instances of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="aeef0-120">また、 **[サーバーへの接続]** ダイアログ ボックスで **[オプション]** ボタンをクリックしたときに表示される **[接続プロパティ]** タブのオプションは、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] への接続時には適用されません。</span><span class="sxs-lookup"><span data-stu-id="aeef0-120">In addition, the options available on the **Connection Options** tab of the **Connect to Server** dialog box, which is displayed by clicking the **Options** button, are not applicable to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] connections.</span></span>  
  
## <a name="eliminating-the-access-is-denied-error"></a><span data-ttu-id="aeef0-121">"アクセスが拒否されました" エラーの回避</span><span class="sxs-lookup"><span data-stu-id="aeef0-121">Eliminating the "Access Is Denied" Error</span></span>  
 <span data-ttu-id="aeef0-122">十分な権限を持っていないユーザーがリモート サーバー上の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] インスタンスに接続しようとすると、サーバーから "アクセスは拒否されました" というエラー メッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="aeef0-122">When a user without sufficient rights attempts to connect to an instance of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] on a remote server, the server responds with an "Access is denied" error message.</span></span> <span data-ttu-id="aeef0-123">必要な権限がユーザーに与えられていることを確認すれば、このエラー メッセージを回避できます。</span><span class="sxs-lookup"><span data-stu-id="aeef0-123">You can avoid this error message by ensuring that users have the required DCOM permissions.</span></span>  
  
#### <a name="to-configure-rights-for-remote-users-on-windows-server-2003-or-windows-xp"></a><span data-ttu-id="aeef0-124">Windows Server 2003 または Windows XP でリモート ユーザーの権限を構成するには</span><span class="sxs-lookup"><span data-stu-id="aeef0-124">To configure rights for remote users on Windows Server 2003 or Windows XP</span></span>  
  
1.  <span data-ttu-id="aeef0-125">ユーザーがローカルの Administrators グループのメンバーでない場合、そのユーザーを Distributed COM Users グループに追加します。</span><span class="sxs-lookup"><span data-stu-id="aeef0-125">If the user is not a member of the local Administrators group, add the user to the Distributed COM Users group.</span></span> <span data-ttu-id="aeef0-126">この操作は、 **[管理ツール]** メニューからアクセスできるコンピューターの管理 MMC スナップインで実行できます。</span><span class="sxs-lookup"><span data-stu-id="aeef0-126">You can do this in the Computer Management MMC snap-in accessed from the **Administrative Tools** menu.</span></span>  
  
2.  <span data-ttu-id="aeef0-127">コントロール パネルを開き、 **[管理ツール]** 、 **[コンポーネント サービス]** の順にダブルクリックして、コンポーネント サービス MMC スナップインを起動します。</span><span class="sxs-lookup"><span data-stu-id="aeef0-127">Open Control Panel, double-click **Administrative Tools,** and then double-click **Component Services** to start the Component Services MMC snap-in.</span></span>  
  
3.  <span data-ttu-id="aeef0-128">コンソールの左ペインで **[コンポーネント サービス]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="aeef0-128">Expand the **Component Services** node in the left pane of the console.</span></span> <span data-ttu-id="aeef0-129">**[コンピューター]** ノード、 **[マイ コンピューター]** の順に展開し、 **[DCOM の構成]** ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="aeef0-129">Expand the **Computers** node, expand **My Computer**, and then click the **DCOM Config** node.</span></span>  
  
4.  <span data-ttu-id="aeef0-130">**[DCOM の構成]** ノードを選択し、構成できるアプリケーションの一覧から [SQL Server Integration Services 11.0] を選択します。</span><span class="sxs-lookup"><span data-stu-id="aeef0-130">Select the **DCOM Config** node, and then select SQL Server Integration Services 11.0 in the list of applications that can be configured.</span></span>  
  
5.  <span data-ttu-id="aeef0-131">[SQL Server Integration Services 11.0] を右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="aeef0-131">Right-click on SQL Server Integration Services 11.0 and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="aeef0-132">**[SQL Server Integration Services 11.0 のプロパティ]** ダイアログ ボックスで、 **[セキュリティ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="aeef0-132">In the **SQL Server Integration Services 11.0 Properties** dialog box, select the **Security** tab.</span></span>  
  
7.  <span data-ttu-id="aeef0-133">**[起動とアクティブ化のアクセス許可]** で **[カスタマイズ]** を選択し、 **[編集]** をクリックして **[起動許可]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="aeef0-133">Under **Launch and Activation Permissions**, select **Customize**, then click **Edit** to open the **Launch Permission** dialog box.</span></span>  
  
8.  <span data-ttu-id="aeef0-134">**[起動許可]** ダイアログ ボックスで、ユーザーを追加または削除し、適切なアクセス許可を適切なユーザーとグループに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="aeef0-134">In the **Launch Permission** dialog box, add or delete users, and assign the appropriate permissions to the appropriate users and groups.</span></span> <span data-ttu-id="aeef0-135">使用可能なアクセス許可は、[ローカルからの起動]、[リモートからの起動]、[ローカルからのアクティブ化]、[リモートからのアクティブ化] です。</span><span class="sxs-lookup"><span data-stu-id="aeef0-135">The available permissions are Local Launch, Remote Launch, Local Activation, and Remote Activation.</span></span> <span data-ttu-id="aeef0-136">起動権限ではサービスを開始および停止するアクセス許可を許可または拒否し、アクティブ化権限ではサービスに接続するアクセス許可を許可または拒否します。</span><span class="sxs-lookup"><span data-stu-id="aeef0-136">The Launch rights grant or deny permission to start and stop the service; the Activation rights grant or deny permission to connect to the service.</span></span>  
  
9. <span data-ttu-id="aeef0-137">[OK] をクリックして、ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="aeef0-137">Click OK to close the dialog box.</span></span>  
  
10. <span data-ttu-id="aeef0-138">**[アクセス許可]** で手順 7. ～ 8. を繰り返し、適切なユーザーとグループに適切なアクセス許可を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="aeef0-138">Under **Access Permissions**, repeat steps 7 and 8 to assign the appropriate permissions to the appropriate users and groups.</span></span>  
  
11. <span data-ttu-id="aeef0-139">MMC スナップインを閉じます。</span><span class="sxs-lookup"><span data-stu-id="aeef0-139">Close the MMC snap-in.</span></span>  
  
12. <span data-ttu-id="aeef0-140">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスを再開します。</span><span class="sxs-lookup"><span data-stu-id="aeef0-140">Restart the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span>  
  
#### <a name="to-configure-rights-for-remote-users-on-windows-2000-with-the-latest-service-packs"></a><span data-ttu-id="aeef0-141">最新の Service Pack が適用されている Windows 2000 でリモート ユーザーの権限を構成するには</span><span class="sxs-lookup"><span data-stu-id="aeef0-141">To configure rights for remote users on Windows 2000 with the latest service packs</span></span>  
  
1.  <span data-ttu-id="aeef0-142">コマンド プロンプトで **dcomcnfg.exe** を実行します。</span><span class="sxs-lookup"><span data-stu-id="aeef0-142">Run **dcomcnfg.exe** at the command prompt.</span></span>  
  
2.  <span data-ttu-id="aeef0-143">**[分散 COM の構成のプロパティ]** ダイアログ ボックスの **[アプリケーション]** ページで、[SQL Server Integration Services 11.0] をクリックして **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aeef0-143">On the **Applications** page of the **Distributed COM Configuration Properties** dialog box, select SQL Server Integration Services 11.0 and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="aeef0-144">**[セキュリティ]** ページを選択します。</span><span class="sxs-lookup"><span data-stu-id="aeef0-144">Select the **Security** page.</span></span>  
  
4.  <span data-ttu-id="aeef0-145">2 つのダイアログ ボックスを使用して、 **[アクセスの許可]** と **[起動の許可]** を構成します。</span><span class="sxs-lookup"><span data-stu-id="aeef0-145">Use the two separate dialog boxes to configure **Access Permissions** and **Launch Permissions**.</span></span> <span data-ttu-id="aeef0-146">リモートとローカルのアクセスは区別できません。アクセスの許可にはローカルとリモートのアクセス権が含まれており、起動の権限にはローカルとリモートの起動権限が含まれています。</span><span class="sxs-lookup"><span data-stu-id="aeef0-146">You cannot distinguish between remote and local access - Access permissions include local and remote access, and Launch permissions include local and remote launch.</span></span>  
  
5.  <span data-ttu-id="aeef0-147">ダイアログ ボックスを閉じ、 **dcomcnfg.exe**を閉じます。</span><span class="sxs-lookup"><span data-stu-id="aeef0-147">Close the dialog boxes and **dcomcnfg.exe**.</span></span>  
  
6.  <span data-ttu-id="aeef0-148">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスを再開します。</span><span class="sxs-lookup"><span data-stu-id="aeef0-148">Restart the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span>  
  
## <a name="connecting-by-using-a-local-account"></a><span data-ttu-id="aeef0-149">ローカル アカウントを使用した接続</span><span class="sxs-lookup"><span data-stu-id="aeef0-149">Connecting by using a Local Account</span></span>  
 <span data-ttu-id="aeef0-150">クライアント コンピューターのローカル Windows アカウントで作業している場合、リモート コンピューターの [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスに接続できるのは、同じ名前、同じパスワード、および十分な権限が設定されたローカル アカウントがリモート コンピューター上に存在する場合だけです。</span><span class="sxs-lookup"><span data-stu-id="aeef0-150">If you are working in a local Windows account on a client computer, you can connect to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service on a remote computer only if a local account that has the same name and password and the appropriate rights exists on the remote computer.</span></span>  
  
## <a name="by-default-the-ssis-service-does-not-support-delegation"></a><span data-ttu-id="aeef0-151">既定では SSIS サービスは委任をサポートしない</span><span class="sxs-lookup"><span data-stu-id="aeef0-151">By default the SSIS service does not support delegation</span></span>  
<span data-ttu-id="aeef0-152">既定では、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスは資格情報の委任をサポートしていません。また、ダブルホップと呼ばれることもあります。</span><span class="sxs-lookup"><span data-stu-id="aeef0-152">By default the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service does not support the delegation of credentials, or what is sometimes referred to as a double hop.</span></span> <span data-ttu-id="aeef0-153">たとえば、ユーザーがクライアント コンピューターで作業しており、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] が別のコンピューターで実行されているとします。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] はさらに別のコンピューターで実行されています。</span><span class="sxs-lookup"><span data-stu-id="aeef0-153">In this scenario, you are working on a client computer, the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is running on a second computer, and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is running on a third computer.</span></span> <span data-ttu-id="aeef0-154">まず、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] がクライアント コンピューターから [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスが実行されている 2 番目のコンピューターに資格情報を渡します。</span><span class="sxs-lookup"><span data-stu-id="aeef0-154">First, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] successfully passes your credentials from the client computer to the second computer on which the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is running.</span></span> <span data-ttu-id="aeef0-155">ただし、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスは 2 番目のコンピューターから [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] が実行されている 3 番目のコンピューターに資格情報を委任できません。</span><span class="sxs-lookup"><span data-stu-id="aeef0-155">Then, however, the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service cannot delegate your credentials from the second computer to the third computer on which [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is running.</span></span>

<span data-ttu-id="aeef0-156">資格情報の委任は、 **[任意のサービスへの委任でこのユーザーを信頼する (Kerberos のみ)]** の権限を SQL Server のサービス アカウントで有効にできます。これにより、子プロセスとして Integration Services サービス (ISServerExec.exe) が起動します。</span><span class="sxs-lookup"><span data-stu-id="aeef0-156">You can enable delegation of credentials by granting the **Trust this user for delegation to any service (Kerberos Only)** right to the SQL Server service account, which launches the Integration Services service (ISServerExec.exe) as a child process.</span></span> <span data-ttu-id="aeef0-157">この権限を付与する前に、組織のセキュリティ要件を満たしているかどうかを検討してください。</span><span class="sxs-lookup"><span data-stu-id="aeef0-157">Before you grant this right, consider whether it meets the security requirements of your organization.</span></span>

<span data-ttu-id="aeef0-158">詳細については、「 [Getting Cross Domain Kerberos and Delegation working with SSIS Package](https://blogs.msdn.microsoft.com/psssql/2014/06/26/getting-cross-domain-kerberos-and-delegation-working-with-ssis-package/)」(SSIS パッケージで機能するクロス ドメイン Kerberos の取得) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aeef0-158">For more info, see [Getting Cross Domain Kerberos and Delegation working with SSIS Package](https://blogs.msdn.microsoft.com/psssql/2014/06/26/getting-cross-domain-kerberos-and-delegation-working-with-ssis-package/).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="aeef0-159">参照</span><span class="sxs-lookup"><span data-stu-id="aeef0-159">See Also</span></span>  
 [<span data-ttu-id="aeef0-160">SSIS サービスにアクセスするように Windows ファイアウォールを構成する</span><span class="sxs-lookup"><span data-stu-id="aeef0-160">Configure a Windows Firewall for Access to the SSIS Service</span></span>](../../2014/integration-services/configure-a-windows-firewall-for-access-to-the-ssis-service.md)  
  
  
