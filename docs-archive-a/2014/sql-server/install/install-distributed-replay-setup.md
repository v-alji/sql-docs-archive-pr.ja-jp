---
title: 分散再生のインストール (セットアップ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 64479cdc-661a-4e32-a381-8f8b5a238337
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 029737874fdab53669aab3be25b139d98d2907df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740733"
---
# <a name="install-distributed-replay-setup"></a><span data-ttu-id="7cabb-102">分散再生のインストール (セットアップ)</span><span class="sxs-lookup"><span data-stu-id="7cabb-102">Install Distributed Replay (Setup)</span></span>
  <span data-ttu-id="7cabb-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分散再生機能を [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インストール ウィザードでインストールします。</span><span class="sxs-lookup"><span data-stu-id="7cabb-103">Install the [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay features with the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Installation Wizard.</span></span> <span data-ttu-id="7cabb-104">機能をインストールする場所を計画する際には、以下について検討してください。</span><span class="sxs-lookup"><span data-stu-id="7cabb-104">When planning where to install the features, consider the following:</span></span>  
  
-   <span data-ttu-id="7cabb-105">管理ツールは、分散再生コントローラーと同じコンピューター上、または別のコンピューター上にインストールできます。</span><span class="sxs-lookup"><span data-stu-id="7cabb-105">You can install the administration tool on the same computer as the Distributed Replay controller, or on different computers.</span></span>  
  
-   <span data-ttu-id="7cabb-106">各 分散再生環境には、コントローラーを 1 つだけ置くことができます。</span><span class="sxs-lookup"><span data-stu-id="7cabb-106">There can only be one controller in each Distributed Replay environment.</span></span>  
  
-   <span data-ttu-id="7cabb-107">クライアント サービスは、最大で 16 の (物理または仮想) コンピューター上にインストールできます。</span><span class="sxs-lookup"><span data-stu-id="7cabb-107">You can install the client service on up to 16 (physical or virtual) computers.</span></span>  
  
-   <span data-ttu-id="7cabb-108">分散再生コントローラー コンピューター上には、クライアント サービスのインスタンスを 1 つだけインストールできます。</span><span class="sxs-lookup"><span data-stu-id="7cabb-108">Only one instance of the client service can be installed on the Distributed Replay controller computer.</span></span> <span data-ttu-id="7cabb-109">分散再生環境に複数のクライアントを置く場合は、クライアント サービスをコントローラーと同じコンピューターにインストールすることはお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="7cabb-109">If your Distributed Replay environment will have more than one client, we do not recommend installing the client service on the same computer as the controller.</span></span> <span data-ttu-id="7cabb-110">そのようにすると、分散再生の全体的な速度が低下します。</span><span class="sxs-lookup"><span data-stu-id="7cabb-110">Doing so may decrease the overall speed of the distributed replay.</span></span>  
  
-   <span data-ttu-id="7cabb-111">パフォーマンスのテストのシナリオでは、管理ツール、Distributed Replay コントローラー サービス、またはクライアント サービスを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の対象インスタンスにインストールすることはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="7cabb-111">For performance testing scenarios, we do not recommend installing the administration tool, Distributed Replay controller service, or client service on the target instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7cabb-112">これらのすべての機能をターゲット サーバーにインストールするのは、アプリケーションの互換性に関する機能テストを行うときだけに限定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7cabb-112">Installing all of these features on the target server should be limited to functional testing for application compatibility.</span></span>  
  
-   <span data-ttu-id="7cabb-113">インストール後は、クライアント上で 分散再生クライアント サービスを開始する前に、コントローラー サービスである [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分散再生コントローラーを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7cabb-113">After installation, the controller service, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay controller, must be running before you start the Distributed Replay client service on the clients.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7cabb-114">分散再生の機能を削除または変更するには、 **コントロール パネル** で Windows の **[プログラムと機能]** ウィンドウを使用します。</span><span class="sxs-lookup"><span data-stu-id="7cabb-114">To remove or change the Distributed Replay features, use the Windows **Programs and Features** window in **Control Panel**.</span></span> <span data-ttu-id="7cabb-115">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [プログラムのアンインストールまたは変更] **ウィンドウで** を選択し、 **[削除]** をクリックして [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インストール ウィザードを開きます。</span><span class="sxs-lookup"><span data-stu-id="7cabb-115">Select [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in the **Uninstall or change a program** window, and then click **Remove** to open the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Installation Wizard.</span></span> <span data-ttu-id="7cabb-116">**[機能の選択]** ページで、削除する分散再生機能を選択します。</span><span class="sxs-lookup"><span data-stu-id="7cabb-116">On the **Select Features** page, check the Distributed Replay features you want to remove.</span></span>  
  
 <span data-ttu-id="7cabb-117">**前提条件:**</span><span class="sxs-lookup"><span data-stu-id="7cabb-117">**Prerequisites:**</span></span>  
  
-   <span data-ttu-id="7cabb-118">使用するコンピューターが、「 [分散再生の要件](../../tools/sql-server-profiler/replay-requirements.md)」に記載されている前提条件を満たしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="7cabb-118">Make sure that the computers that you want to use meet the requirements that are described in the topic [Distributed Replay Requirements](../../tools/sql-server-profiler/replay-requirements.md).</span></span>  
  
-   <span data-ttu-id="7cabb-119">この手順を開始する前に、コントローラーおよびクライアントのサービスを実行するためのドメイン ユーザー アカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="7cabb-119">Before you begin this procedure, you create the domain user accounts that the controller and client services will run under.</span></span> <span data-ttu-id="7cabb-120">これらのアカウントは、Windows Administrators グループのメンバーにしないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7cabb-120">We recommend that these accounts are not members of the Windows Administrators group.</span></span> <span data-ttu-id="7cabb-121">詳細については、「 [Distributed Replay のセキュリティ](../../tools/distributed-replay/distributed-replay-security.md) 」の「ユーザーおよびサービス アカウント」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7cabb-121">For more information, see the User and Service Accounts section in the [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md) topic.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7cabb-122">管理ツール、コントローラー サービス、およびクライアント サービスが同じコンピューター上で実行されている場合は、ローカル ユーザー アカウントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="7cabb-122">You can use local user accounts if you are running the administration tool, controller service, and client service on the same computer.</span></span>  
  
 <span data-ttu-id="7cabb-123">**インストール先:**</span><span class="sxs-lookup"><span data-stu-id="7cabb-123">**Installation Locations:**</span></span>  
  
 <span data-ttu-id="7cabb-124">既定のファイルの場所と標準インストールを使用した場合、基本ディレクトリは C:\Program Files \Microsoft SQL Server になります。</span><span class="sxs-lookup"><span data-stu-id="7cabb-124">Assuming you use the default file locations and a standard installation, the base directory is found at C:\Program Files\Microsoft SQL Server.</span></span> <span data-ttu-id="7cabb-125">その下の以下の場所に、バイナリとアセンブリがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="7cabb-125">Within that, following are where the binaries and assemblies are installed to:</span></span>  
  
-   <span data-ttu-id="7cabb-126">32 ビット システムの場合:</span><span class="sxs-lookup"><span data-stu-id="7cabb-126">On a 32-bit system:</span></span>  
  
     [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]<span data-ttu-id="7cabb-127">ツール</span><span class="sxs-lookup"><span data-stu-id="7cabb-127">Tools</span></span>  
  
     <span data-ttu-id="7cabb-128">\- または -</span><span class="sxs-lookup"><span data-stu-id="7cabb-128">\- OR -</span></span>  
  
     <span data-ttu-id="7cabb-129">\<Share Feature Directory>\ ツール \\ (ユーザーが指定した代替の共有機能ディレクトリ)</span><span class="sxs-lookup"><span data-stu-id="7cabb-129">\<Share Feature Directory>\Tools\\(user-supplied alternative shared feature directory)</span></span>  
  
-   <span data-ttu-id="7cabb-130">64 ビット システムの場合:</span><span class="sxs-lookup"><span data-stu-id="7cabb-130">On a 64-bit system:</span></span>  
  
     <span data-ttu-id="7cabb-131">C:\Program files \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (x86) \ 120 \ ツール</span><span class="sxs-lookup"><span data-stu-id="7cabb-131">C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (x86) \120\Tools</span></span>  
  
     <span data-ttu-id="7cabb-132">\- または -</span><span class="sxs-lookup"><span data-stu-id="7cabb-132">\- OR -</span></span>  
  
     <span data-ttu-id="7cabb-133">\<Share Feature Directory (x86)>\ ツール \\ (ユーザーが指定した代替の共有機能 (x86) ディレクトリ)</span><span class="sxs-lookup"><span data-stu-id="7cabb-133">\<Share Feature Directory (x86)>\Tools\\(user-supplied alternative shared feature (x86) directory)</span></span>  
  
### <a name="to-install-distributed-replay-features"></a><span data-ttu-id="7cabb-134">分散再生機能をインストールするには</span><span class="sxs-lookup"><span data-stu-id="7cabb-134">To install Distributed Replay features</span></span>  
  
1.  <span data-ttu-id="7cabb-135">分散再生の機能のインストールを開始するには、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インストール ウィザードを開始します。</span><span class="sxs-lookup"><span data-stu-id="7cabb-135">To start the installation of any of the Distributed Replay features, start the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Installation Wizard.</span></span>  
  
2.  <span data-ttu-id="7cabb-136">**[セットアップ サポート ルール]** ページでは、SQL Server セットアップ サポート ファイルをインストールするときに発生する可能性がある問題が特定されています。</span><span class="sxs-lookup"><span data-stu-id="7cabb-136">The **Setup Support Rules** page identifies issues that might occur when installing the SQL Server Setup support files.</span></span> <span data-ttu-id="7cabb-137">セットアップを続行する前に、セットアップ サポートの失敗を修正する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7cabb-137">You must correct any Setup support failures before continuing with Setup.</span></span>  
  
3.  <span data-ttu-id="7cabb-138">**[プロダクト キー]** ページでオプション ボタンをクリックして、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の無償のエディション、または PID キーを持つ製品版のどちらをインストールするかを指定します。</span><span class="sxs-lookup"><span data-stu-id="7cabb-138">On the **Product Key** page, select an option button to indicate whether you are installing a free edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or a production version of the product that has a PID key.</span></span> <span data-ttu-id="7cabb-139">詳細については、「 [SQL Server 2014 のエディションとコンポーネント](../editions-and-components-of-sql-server-2016.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7cabb-139">For more information, see [Editions and Components of SQL Server 2014](../editions-and-components-of-sql-server-2016.md).</span></span>  
  
4.  <span data-ttu-id="7cabb-140">**[ライセンス条項]** ページで使用許諾契約書を読み、使用許諾条件に同意する場合は対応するチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="7cabb-140">On the **License Terms** page, read the license agreement, and then select the check box to accept the license terms and conditions.</span></span> <span data-ttu-id="7cabb-141">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の機能向上に役立てるため、機能の使用状況オプションを有効にしてレポートを [!INCLUDE[msCoName](../../includes/msconame-md.md)]に送信することもできます。</span><span class="sxs-lookup"><span data-stu-id="7cabb-141">To help improve [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can also enable the feature usage option and send reports to [!INCLUDE[msCoName](../../includes/msconame-md.md)].</span></span>  
  
5.  <span data-ttu-id="7cabb-142">**[セットアップ サポート ファイル]** ページで **[インストール]** をクリックして、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のセットアップ サポート ファイルをインストールまたは更新します。</span><span class="sxs-lookup"><span data-stu-id="7cabb-142">On the **Setup Support Files** page, click **Install** to install or update the Setup Support files for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
6.  <span data-ttu-id="7cabb-143">**[セットアップ ロール]** ページで、 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能のインストール**をクリックし、 **[次へ]** をクリックして **[機能の選択]** ページに進みます。</span><span class="sxs-lookup"><span data-stu-id="7cabb-143">On the **Setup Role** page, select **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Feature Installation**, and then click **Next** to continue to the **Feature Selection** page.</span></span>  
  
7.  <span data-ttu-id="7cabb-144">**[機能の選択]** ページで、どの機能をインストールするかを設定します。</span><span class="sxs-lookup"><span data-stu-id="7cabb-144">On the **Feature Selection** page, configure which features you want to install.</span></span>  
  
    -   <span data-ttu-id="7cabb-145">管理ツールをインストールするには、 **[管理ツール - 基本]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7cabb-145">To install the administration tool, select **Management Tools - Basic**.</span></span>  
  
    -   <span data-ttu-id="7cabb-146">コントローラー サービスをインストールするには、 **[分散再生コントローラー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7cabb-146">To install the controller service, select **Distributed Replay Controller**.</span></span>  
  
    -   <span data-ttu-id="7cabb-147">クライアント サービスをインストールするには、 **[分散再生クライアント]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7cabb-147">To install the client service, select **Distributed Replay Client**.</span></span>  
  
     <span data-ttu-id="7cabb-148">**重要**:分散再生コントローラーを構成するとき、分散再生クライアント サービスの実行に使用する 1 つ以上のユーザー アカウントを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7cabb-148">**Important**: When you configure Distributed Replay controller, you can specify one or more user accounts that will be used to run the Distributed Replay client services.</span></span> <span data-ttu-id="7cabb-149">サポートされているアカウントの一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7cabb-149">The following is the list of supported accounts:</span></span>  
  
    -   <span data-ttu-id="7cabb-150">ドメイン ユーザー アカウント</span><span class="sxs-lookup"><span data-stu-id="7cabb-150">Domain user account</span></span>  
  
    -   <span data-ttu-id="7cabb-151">ユーザーによって作成されたローカル ユーザー アカウント</span><span class="sxs-lookup"><span data-stu-id="7cabb-151">User created local user account</span></span>  
  
    -   <span data-ttu-id="7cabb-152">管理者</span><span class="sxs-lookup"><span data-stu-id="7cabb-152">Administrator</span></span>  
  
    -   <span data-ttu-id="7cabb-153">仮想アカウントおよび管理されたサービス アカウント (MSA)</span><span class="sxs-lookup"><span data-stu-id="7cabb-153">Virtual account and MSA (Managed Service Account)</span></span>  
  
    -   <span data-ttu-id="7cabb-154">ネットワーク サービス、ローカル サービス、およびシステム</span><span class="sxs-lookup"><span data-stu-id="7cabb-154">Network Services, Local Services, and System</span></span>  
  
     <span data-ttu-id="7cabb-155">グループ アカウント (ローカルまたはドメイン) およびその他の組み込みのアカウント (Everyone など) は使用できません。</span><span class="sxs-lookup"><span data-stu-id="7cabb-155">Group accounts (local or domain) and other built-in accounts (like Everyone) are not accepted.</span></span>  
  
8.  <span data-ttu-id="7cabb-156">必要に応じて、省略記号 (...) ボタンをクリックし、共有機能のディレクトリのパスを変更します。</span><span class="sxs-lookup"><span data-stu-id="7cabb-156">Optionally, click the ellipsis (...) button to change the shared feature directory path.</span></span>  
  
    1.  <span data-ttu-id="7cabb-157">32 ビットのコンピューターの場合、既定のインストール パスは **C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\**</span><span class="sxs-lookup"><span data-stu-id="7cabb-157">On 32-bit computers, the default installation path is **C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\**</span></span>  
  
    2.  <span data-ttu-id="7cabb-158">64 ビットのコンピューターの場合、既定のインストール パスは **C:\Program Files (x86)\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\** です。</span><span class="sxs-lookup"><span data-stu-id="7cabb-158">On 64-bit computers, the default installation path is **C:\Program Files (x86)\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\**</span></span>  
  
9. <span data-ttu-id="7cabb-159">構成し終わったら、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7cabb-159">When you are finished, click **Next**.</span></span>  
  
10. <span data-ttu-id="7cabb-160">**[インストール ルール]** ページで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップはコンピューターの構成を検証します。</span><span class="sxs-lookup"><span data-stu-id="7cabb-160">On the **Installation Rules** page, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup validates your computer configuration.</span></span> <span data-ttu-id="7cabb-161">検証プロセスが完了したら、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7cabb-161">Once the validation process is completed, click **Next**.</span></span>  
  
11. <span data-ttu-id="7cabb-162">**[必要なディスク領域]** ページでは、指定した機能に必要なディスク領域が計算されます。</span><span class="sxs-lookup"><span data-stu-id="7cabb-162">The **Disk Space Requirements** page calculates the required disk space for the features that you specify.</span></span> <span data-ttu-id="7cabb-163">その後、必要なディスク領域が使用可能なディスク領域と比較されます。</span><span class="sxs-lookup"><span data-stu-id="7cabb-163">Then it compares the required space to the available disk space.</span></span>  
  
12. <span data-ttu-id="7cabb-164">**[エラー レポート]** ページで、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] に送信する、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の強化に役立つ情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="7cabb-164">On the **Error Reporting** page, specify the information that you want to send to [!INCLUDE[msCoName](../../includes/msconame-md.md)] to help improve [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7cabb-165">既定では、エラー レポートのオプションは有効になっています。</span><span class="sxs-lookup"><span data-stu-id="7cabb-165">By default, option for error reporting is enabled.</span></span>  
  
13. <span data-ttu-id="7cabb-166">**[インストール構成ルール]** ページでは、システム構成チェッカーによって別のルール セットが実行され、コンピューターの構成と指定した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能が検証されます。</span><span class="sxs-lookup"><span data-stu-id="7cabb-166">On the **Installation Configuration Rules** page, the System Configuration Checker will run one more set of rules to validate your computer configuration with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features that you have specified.</span></span>  
  
14. <span data-ttu-id="7cabb-167">**[プログラムインストールの準備完了]** ページで、 **[インストール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7cabb-167">On the **Ready to Install the Program** page, click **Install**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="7cabb-168">分散再生をインストールした後、コントローラー コンピューターとクライアント コンピューターのファイアウォール ルールを作成し、ターゲット サーバー上で各クライアント コンピューターの権限を付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7cabb-168">After you install Distributed Replay you must create firewall rules on the controller and client computers, and grant each client computer permissions on the target server.</span></span> <span data-ttu-id="7cabb-169">詳細については、「 [インストール後の手順の実行](../../tools/distributed-replay/complete-the-post-installation-steps.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7cabb-169">For more information, see [Complete the Post-Installation Steps](../../tools/distributed-replay/complete-the-post-installation-steps.md).</span></span>  
  
 <span data-ttu-id="7cabb-170">以下の追加のトピックでは、分散再生をインストールする他の方法が記載されています。</span><span class="sxs-lookup"><span data-stu-id="7cabb-170">These additional topics document other ways to install Distributed Replay:</span></span>  
  
-   [<span data-ttu-id="7cabb-171">コマンド プロンプトからの分散再生のインストール</span><span class="sxs-lookup"><span data-stu-id="7cabb-171">Install Distributed Replay from the Command Prompt</span></span>](../../tools/distributed-replay/install-distributed-replay-overview.md)  
  
-   [<span data-ttu-id="7cabb-172">構成ファイルを使用した分散再生のインストール</span><span class="sxs-lookup"><span data-stu-id="7cabb-172">Install Distributed Replay Using a Configuration File</span></span>](../../../2014/sql-server/install/install-distributed-replay-using-a-configuration-file.md)  
  
## <a name="net-framework-security"></a><span data-ttu-id="7cabb-173">.NET Framework のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="7cabb-173">.NET Framework Security</span></span>  
 <span data-ttu-id="7cabb-174">分散再生の機能をインストールするには、管理権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="7cabb-174">You must have administrative permissions in order to install any of the Distributed Replay features.</span></span> <span data-ttu-id="7cabb-175">sysadmin 権限を持つ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインのみが、テスト サーバーの sysadmin サーバー ロールにクライアント サービス アカウントを追加できます。</span><span class="sxs-lookup"><span data-stu-id="7cabb-175">Only a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login having sysadmin permissions can add the client service accounts to the sysadmin server role of the test server.</span></span> <span data-ttu-id="7cabb-176">Distributed Replay のセキュリティ上の考慮事項の詳細については、「 [Distributed Replay のセキュリティ](../../tools/distributed-replay/distributed-replay-security.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7cabb-176">For more information about Distributed Replay security considerations, see [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cabb-177">参照</span><span class="sxs-lookup"><span data-stu-id="7cabb-177">See Also</span></span>  
 <span data-ttu-id="7cabb-178">[SQL Server 2014 の各エディションがサポートする機能](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span><span class="sxs-lookup"><span data-stu-id="7cabb-178">[Features Supported by the Editions of SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span></span>  
 <span data-ttu-id="7cabb-179">[SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md) </span><span class="sxs-lookup"><span data-stu-id="7cabb-179">[SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md) </span></span>  
 <span data-ttu-id="7cabb-180">[Distributed Replay Requirements](../../tools/sql-server-profiler/replay-requirements.md) </span><span class="sxs-lookup"><span data-stu-id="7cabb-180">[Distributed Replay Requirements](../../tools/sql-server-profiler/replay-requirements.md) </span></span>  
 <span data-ttu-id="7cabb-181">[管理ツール コマンド ライン オプション &#40;Distributed Replay Utility&#41;](../../tools/distributed-replay/administration-tool-command-line-options-distributed-replay-utility.md) </span><span class="sxs-lookup"><span data-stu-id="7cabb-181">[Administration Tool Command-line Options &#40;Distributed Replay Utility&#41;](../../tools/distributed-replay/administration-tool-command-line-options-distributed-replay-utility.md) </span></span>  
 [<span data-ttu-id="7cabb-182">分散再生の構成</span><span class="sxs-lookup"><span data-stu-id="7cabb-182">Configure Distributed Replay</span></span>](../../tools/distributed-replay/configure-distributed-replay.md)  
  
  
