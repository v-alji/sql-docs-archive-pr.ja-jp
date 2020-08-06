---
title: オフライン ログ ファイルの表示 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Log File Viewer, viewing offline logs
- offline log files
ms.assetid: 9223e474-f224-4907-a4f2-081e11db58f5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2afc1992b54c78f69bfae1fc152b41c20bcd4ea1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643329"
---
# <a name="view-offline-log-files"></a><span data-ttu-id="12147-102">オフライン ログ ファイルの表示</span><span class="sxs-lookup"><span data-stu-id="12147-102">View Offline Log Files</span></span>
  <span data-ttu-id="12147-103">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]以降では、対象となるインスタンスがオフラインの場合または開始できない場合に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログ ファイルを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカルまたはリモート インスタンスから表示できます。</span><span class="sxs-lookup"><span data-stu-id="12147-103">Beginning in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], you can view [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log files from a local or remote instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] when the target instance is offline or cannot start.</span></span>  
  
 <span data-ttu-id="12147-104">登録済みサーバーから、またはプログラムにより WMI および WQL (WMI Query Language) クエリを通じて、オフラインのログ ファイルにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="12147-104">You can access the offline log files from Registered Servers, or programmatically through WMI and WQL (WMI Query Language) queries.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="12147-105">これらの方法によってオンラインのインスタンスに接続することもできますが、ある理由により、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接続で接続することはできません。</span><span class="sxs-lookup"><span data-stu-id="12147-105">You can also use these methods to connect to an instance that is online, but for some reason, you cannot connect through a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connection.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="12147-106">開始する前に</span><span class="sxs-lookup"><span data-stu-id="12147-106">Before you Begin</span></span>  
 <span data-ttu-id="12147-107">オフライン ログ ファイルに接続するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが、オフライン ログ ファイルの表示に使用するコンピューターと、表示するログ ファイルが置かれているコンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="12147-107">To connect to offline log files, an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be installed on the computer that you are using to view the offline log files, and on the computer where the log files that you want to view are located.</span></span> <span data-ttu-id="12147-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが両方のコンピューターにインストールされている場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンス、およびどちらかのコンピューター上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の以前のバージョンを実行しているインスタンスのオフライン ファイルを表示できます。</span><span class="sxs-lookup"><span data-stu-id="12147-108">If an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed on both computers, you can view offline files for instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and for instances that are running earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on either computer.</span></span>  
  
 <span data-ttu-id="12147-109">登録済みサーバーを使用している場合は、接続するインスタンスが **[ローカル サーバー グループ]** または **[中央管理サーバー]** で登録されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="12147-109">If you are using Registered Servers, the instance that you want to connect to must be registered under **Local Server Groups** or under **Central Management Servers**.</span></span> <span data-ttu-id="12147-110">(インスタンスは自身に登録するか、またはサーバー グループのメンバーにすることができます)。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを登録済みサーバーに追加する方法の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="12147-110">(The instance can be registered on its own or be a member of a server group.) For more information about how to add an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to Registered Servers, see the following topics:</span></span>  
  
-   [<span data-ttu-id="12147-111">サーバー グループの作成または編集 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="12147-111">Create or Edit a Server Group &#40;SQL Server Management Studio&#41;</span></span>](../../ssms/register-servers/create-or-edit-a-server-group-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="12147-112">接続済みのサーバーの登録 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="12147-112">Register a Connected Server &#40;SQL Server Management Studio&#41;</span></span>](../../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="12147-113">中央管理サーバーとサーバー グループの作成 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="12147-113">Create a Central Management Server and Server Group &#40;SQL Server Management Studio&#41;</span></span>](../../ssms/register-servers/create-a-central-management-server-and-server-group.md)  
  
 <span data-ttu-id="12147-114">プログラムにより WMI および WQL クエリでオフライン ログ ファイルを表示する方法の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="12147-114">For more information about how to view offline log files programmatically through WMI and WQL queries, see the following topics:</span></span>  
  
-   <span data-ttu-id="12147-115">[SqlErrorLogEvent Class](../wmi-provider-configuration-classes/sqlerrorlogevent-class.md) (このトピックでは、特定のログ ファイルで記録されたイベントの値を取得する方法について説明しています。)</span><span class="sxs-lookup"><span data-stu-id="12147-115">[SqlErrorLogEvent Class](../wmi-provider-configuration-classes/sqlerrorlogevent-class.md) (This topic shows how to retrieve values for logged events in a specified log file.)</span></span>  
  
-   <span data-ttu-id="12147-116">[SqlErrorLogFile Class](../wmi-provider-configuration-classes/sqlerrorlogfile-class.md) (このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の指定されたインスタンス上のすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログ ファイルに関する情報を取得する方法について説明しています。)</span><span class="sxs-lookup"><span data-stu-id="12147-116">[SqlErrorLogFile Class](../wmi-provider-configuration-classes/sqlerrorlogfile-class.md) (This topic shows how to retrieve information about all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log files on a specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)</span></span>  
  
##  <a name="permissions"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="12147-117">Permissions</span><span class="sxs-lookup"><span data-stu-id="12147-117">Permissions</span></span>  
 <span data-ttu-id="12147-118">オフラインのログ ファイルに接続するには、ローカルおよびリモートの両方のコンピューターで次の権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="12147-118">To connect to an offline log file, you must have the following permissions on both the local and remote computers:</span></span>  
  
-   <span data-ttu-id="12147-119">**Root\Microsoft\SqlServer\ComputerManagement12** WMI 名前空間への読み取りアクセス。</span><span class="sxs-lookup"><span data-stu-id="12147-119">Read access to the **Root\Microsoft\SqlServer\ComputerManagement12** WMI namespace.</span></span> <span data-ttu-id="12147-120">既定では、すべてのユーザーがアカウントの有効化権限による読み取りアクセスを持ちます。</span><span class="sxs-lookup"><span data-stu-id="12147-120">By default, everyone has read access through the Enable Account permission.</span></span> <span data-ttu-id="12147-121">詳細については、このセクションで後述する「WMI 権限を確認するには」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="12147-121">For more information, see the "To verify WMI permissions" procedure later in this section.</span></span>  
  
-   <span data-ttu-id="12147-122">エラー ログ ファイルを含むフォルダーへの読み取り権限。</span><span class="sxs-lookup"><span data-stu-id="12147-122">Read permission to the folder that contains the error log files.</span></span> <span data-ttu-id="12147-123">既定では、エラー ログ ファイルは次のパスにあります (\<*Drive>\* は[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール先ドライブ、\<*InstanceName*> は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス名です)。</span><span class="sxs-lookup"><span data-stu-id="12147-123">By default the error log files are located in the following path (where \<*Drive>\* represents the drive where you installed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and \<*InstanceName*> is the name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]):</span></span>  
  
     <span data-ttu-id="12147-124">**\<Drive>: Server\MSSQL12. \<InstanceName> : SQL\MSSQL\Log**</span><span class="sxs-lookup"><span data-stu-id="12147-124">**\<Drive>:\Program Files\Microsoft SQL Server\MSSQL12.\<InstanceName>\MSSQL\Log**</span></span>  
  
 <span data-ttu-id="12147-125">WMI 名前空間のセキュリティ設定を確認するには、WMI コントロール スナップインを使用します。</span><span class="sxs-lookup"><span data-stu-id="12147-125">To verify WMI namespace security settings, you can use the WMI Control snap-in.</span></span>  
  
#### <a name="to-verify-wmi-permissions"></a><span data-ttu-id="12147-126">WMI 権限を確認するには</span><span class="sxs-lookup"><span data-stu-id="12147-126">To verify WMI permissions</span></span>  
  
1.  <span data-ttu-id="12147-127">WMI コントロール スナップインを開きます。</span><span class="sxs-lookup"><span data-stu-id="12147-127">Open the WMI Control snap-in.</span></span> <span data-ttu-id="12147-128">これを行うには、次のいずれかの操作を実行します (オペレーティング システムによって異なります)。</span><span class="sxs-lookup"><span data-stu-id="12147-128">To do this, do either of the following, depending on the operating system:</span></span>  
  
    -   <span data-ttu-id="12147-129">[**スタート**] ボタンをクリックし、[ `wmimgmt.msc` **検索の開始**] ボックスに「」と入力して、enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="12147-129">Click **Start**, type `wmimgmt.msc` in the **Start Search** box, and then press ENTER.</span></span>  
  
    -   <span data-ttu-id="12147-130">[**スタート**] ボタンをクリックし、[**実行**] をクリックして「」と入力し、 `wmimgmt.msc` enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="12147-130">Click **Start**, click **Run**, type `wmimgmt.msc`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="12147-131">既定では、WMI コントロール スナップインはローカル コンピューターを管理します。</span><span class="sxs-lookup"><span data-stu-id="12147-131">By default, the WMI Control snap-in manages the local computer.</span></span>  
  
     <span data-ttu-id="12147-132">リモート コンピューターに接続する場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="12147-132">If you want to connect to a remote computer, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="12147-133">**[WMI コントロール (ローカル)]** を右クリックし、 **[別のコンピューターへ接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="12147-133">Right-click **WMI Control (Local)**, and then click **Connect to another computer**.</span></span>  
  
    2.  <span data-ttu-id="12147-134">**[管理するコンピューターの変更]** ダイアログ ボックスで **[別のコンピューター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="12147-134">In the **Change managed computer** dialog box, click **Another computer**.</span></span>  
  
    3.  <span data-ttu-id="12147-135">リモート コンピューター名を入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="12147-135">Enter the remote computer name, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="12147-136">[ **Wmi コントロール (ローカル)** ] または [ **Wmi コントロール (***RemoteComputerName***)**] を右クリックし、[**プロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="12147-136">Right-click **WMI Control (Local)** or **WMI Control (***RemoteComputerName***)**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="12147-137">**[WMI コントロールのプロパティ]** ダイアログ ボックスで、 **[セキュリティ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="12147-137">In the **WMI Control Properties** dialog box, click the **Security** tab.</span></span>  
  
5.  <span data-ttu-id="12147-138">名前空間ツリーで、次の名前空間を探してクリックします。</span><span class="sxs-lookup"><span data-stu-id="12147-138">In the namespace tree, locate and then click the following namespace:</span></span>  
  
     <span data-ttu-id="12147-139">**Root\Microsoft\SqlServer\ComputerManagement10**</span><span class="sxs-lookup"><span data-stu-id="12147-139">**Root\Microsoft\SqlServer\ComputerManagement10**</span></span>  
  
6.  <span data-ttu-id="12147-140">**[セキュリティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="12147-140">Click **Security**.</span></span>  
  
7.  <span data-ttu-id="12147-141">使用するアカウントに **[アカウントの有効化]** 権限があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="12147-141">Make sure that the account that will be used has the **Enable Account** permission.</span></span> <span data-ttu-id="12147-142">この権限により、WMI オブジェクトへの読み取りアクセスが許可されます。</span><span class="sxs-lookup"><span data-stu-id="12147-142">This permission allows Read access to WMI objects.</span></span>  
  
### <a name="view-log-files"></a><span data-ttu-id="12147-143">ログ ファイルの表示</span><span class="sxs-lookup"><span data-stu-id="12147-143">View Log Files</span></span>  
 <span data-ttu-id="12147-144">次の手順は、登録済みサーバーを使用してオフラインのログ ファイルを表示する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="12147-144">The following procedure shows how to view offline log files through Registered Servers.</span></span> <span data-ttu-id="12147-145">この手順の前提条件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="12147-145">The procedure assumes the following:</span></span>  
  
 <span data-ttu-id="12147-146">接続する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが登録済みサーバーに登録されていること。</span><span class="sxs-lookup"><span data-stu-id="12147-146">The instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you want to connect to is already registered in Registered Servers.</span></span>  
  
##### <a name="to-view-log-files-for-instances-that-are-offline"></a><span data-ttu-id="12147-147">オフラインのインスタンスのログ ファイルを表示するには</span><span class="sxs-lookup"><span data-stu-id="12147-147">To view log files for instances that are offline</span></span>  
  
1.  <span data-ttu-id="12147-148">ローカル インスタンス上のオフライン ログ ファイルを表示するには、高度な権限で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を起動してください</span><span class="sxs-lookup"><span data-stu-id="12147-148">If you want to view offline log files on a local instance, make sure that you start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] with elevated permissions.</span></span> <span data-ttu-id="12147-149">そのためには、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]を起動するときに、 **[SQL Server Management Studio]** を右クリックして、 **[管理者として実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="12147-149">To do this, when you start [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], right-click **SQL Server Management Studio**, and then click **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="12147-150">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 **[表示]** メニューの **[登録済みサーバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="12147-150">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Registered Servers**.</span></span>  
  
3.  <span data-ttu-id="12147-151">コンソール ツリーで、オフライン ファイルを表示するインスタンスを特定します。</span><span class="sxs-lookup"><span data-stu-id="12147-151">In the console tree, locate the instance on which you want to view the offline files.</span></span>  
  
4.  <span data-ttu-id="12147-152">次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="12147-152">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="12147-153">インスタンスが **[ローカル サーバー グループ]** の下にある場合は、 **[ローカル サーバー グループ]** を展開し、サーバー グループを展開します (インスタンスがグループのメンバーである場合)。次に、インスタンスを右クリックして **[SQL Server ログの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="12147-153">If the instance is under **Local Server Groups**, expand **Local Server Groups**, expand the server group (if the instance is a member of a group), right-click the instance, and then click **View SQL Server Log**.</span></span>  
  
    -   <span data-ttu-id="12147-154">インスタンスが中央管理サーバーである場合は、 **[中央管理サーバー]** を展開し、インスタンスを右クリックして **[中央管理サーバーのアクション]** をポイントし、 **[SQL Server ログの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="12147-154">If the instance is the Central Management Server itself, expand **Central Management Servers**, right-click the instance, point to **Central Management Server Actions**, and then click **View SQL Server Log**.</span></span>  
  
    -   <span data-ttu-id="12147-155">インスタンスが **[中央管理サーバー]** の下にある場合は、 **[中央管理サーバー]** を展開し、中央管理サーバーを展開してインスタンスを右クリックし (またはサーバー グループを展開してインスタンスを右クリックし)、 **[SQL Server ログの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="12147-155">If the instance is under **Central Management Servers**, expand **Central Management Servers**, expand the Central Management Server, right-click the instance (or expand a server group and right-click the instance), and then click **View SQL Server Log**.</span></span>  
  
5.  <span data-ttu-id="12147-156">ローカル インスタンスに接続している場合は、現在のユーザー資格情報を使用して接続が行われます。</span><span class="sxs-lookup"><span data-stu-id="12147-156">If you are connecting to a local instance, the connection is made using the current user credentials.</span></span>  
  
     <span data-ttu-id="12147-157">リモート インスタンスに接続している場合は、 **[ログ ファイルの表示 - 接続するユーザー]** ダイアログ ボックスで、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="12147-157">If you are connecting to a remote instance, in the **Log File Viewer - Connect As** dialog box, do either of the following:</span></span>  
  
    -   <span data-ttu-id="12147-158">現在のユーザーとして接続するには、 **[別のユーザーとして接続する]** チェック ボックスがオフになっていることを確認し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="12147-158">To connect as the current user, make sure that the **Connect as another user** check box is cleared, and then click **OK**.</span></span>  
  
    -   <span data-ttu-id="12147-159">別のユーザーとして接続するには、 **[別のユーザーとして接続する]** チェック ボックスをオンにし、 **[ユーザーを設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="12147-159">To connect as another user, select the **Connect as another user** check box, and then click **Set User**.</span></span> <span data-ttu-id="12147-160">ユーザー資格情報を求められたら入力し (ユーザー名を *domain_name*\\*user_name*の形式で入力します)、 **[OK]** をクリックします。再度 **[OK]** をクリックして接続します。</span><span class="sxs-lookup"><span data-stu-id="12147-160">When you are prompted, enter the user credentials (with the user name in the format *domain_name*\\*user_name*), click **OK**, and then click **OK** again to connect.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="12147-161">ログ ファイルの読み込みに時間がかかりすぎる場合は、[ログ ファイルの表示] ツール バーの **[停止]** をクリックできます。</span><span class="sxs-lookup"><span data-stu-id="12147-161">If the log files take too long to load, you can click **Stop** on the Log File Viewer toolbar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12147-162">参照</span><span class="sxs-lookup"><span data-stu-id="12147-162">See Also</span></span>  
 [<span data-ttu-id="12147-163">ログ ファイルの表示</span><span class="sxs-lookup"><span data-stu-id="12147-163">Log File Viewer</span></span>](log-file-viewer.md)  
  
  
