---
title: サーバー ネットワーク プロトコルの有効化または無効化 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- network protocols [SQL Server], disabling
- remote connections [SQL Server], enabling using Configuration Manager
- protocols [SQL Server], enabling using Configuration Manager
- protocols [SQL Server], disabling using Configuration Manager
- disabling network protocols, Configuration Manager
- network protocols [SQL Server], enabling
- enabling network protocols, Configuration Manager
- surface area configuration [SQL Server], connection protocols
- connections [SQL Server], enabling remote using Configuration Manager
ms.assetid: ec5ccb69-61c9-4576-8843-014b976fd46e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 737edae84ff284ed726ade69cb48e574b830611e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715697"
---
# <a name="enable-or-disable-a-server-network-protocol"></a><span data-ttu-id="77fb7-102">サーバー ネットワーク プロトコルの有効化または無効化</span><span class="sxs-lookup"><span data-stu-id="77fb7-102">Enable or Disable a Server Network Protocol</span></span>
  <span data-ttu-id="77fb7-103">すべてのネットワーク プロトコルは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップによってインストールされますが、必ずしも有効になっているとは限りません。</span><span class="sxs-lookup"><span data-stu-id="77fb7-103">All network protocols are installed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup, but may or may not be enabled.</span></span> <span data-ttu-id="77fb7-104">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーまたは PowerShell を使用してサーバー ネットワーク プロトコルを有効または無効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="77fb7-104">This topic describes how to enable or disable a server network protocol in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager or PowerShell.</span></span> <span data-ttu-id="77fb7-105">変更を有効にするために [!INCLUDE[ssDE](../../includes/ssde-md.md)] を停止し、再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="77fb7-105">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] must be stopped and restarted for the change to take effect.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="77fb7-106">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] のセットアップ時に、ログインは BUILTIN\Users グループに追加されます。</span><span class="sxs-lookup"><span data-stu-id="77fb7-106">During setup of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] a login is added for the BUILTIN\Users group.</span></span> <span data-ttu-id="77fb7-107">これにより、コンピューターの認証されたすべてのユーザーが public ロールのメンバーとして [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] のインスタンスにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="77fb7-107">This allows all authenticated users of the computer to access the instance of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] as a member of the public role.</span></span> <span data-ttu-id="77fb7-108">BUILTIN\Users ログインを安全に削除して、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] アクセスを、個別のログインを持つコンピューター ユーザーまたはログインを持つ他の Windows グループのメンバーに制限できます。</span><span class="sxs-lookup"><span data-stu-id="77fb7-108">The BUILTIN\Users login can be safely removed to restrict [!INCLUDE[ssDE](../../includes/ssde-md.md)] access to computer users who have individual logins or are members of other Windows groups with logins.</span></span>  
  
> [!WARNING]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="77fb7-109">および [!INCLUDE[msCoName](../../includes/msconame-md.md)] 向けの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ プロバイダーでは、SSL 3.0、TLS 1.0 がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="77fb7-109">and [!INCLUDE[msCoName](../../includes/msconame-md.md)] data providers for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support TLS 1.0 and SSL 3.0.</span></span> <span data-ttu-id="77fb7-110">オペレーティング システムの SChannel 層を変更して別のプロトコル (TLS 1.1、TLS 1.2 など) を適用すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への接続に失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="77fb7-110">If you enforce a different protocol (such as TLS 1.1 or TLS 1.2) by making changes in the operating system SChannel layer, your connections to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might fail.</span></span>  
  
 <span data-ttu-id="77fb7-111">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="77fb7-111">**In This Topic**</span></span>  
  
-   <span data-ttu-id="77fb7-112">**サーバー ネットワーク プロトコルを有効または無効にするための方法:**</span><span class="sxs-lookup"><span data-stu-id="77fb7-112">**To enable or disable a server network protocol using:**</span></span>  
  
     [<span data-ttu-id="77fb7-113">SQL Server 構成マネージャー</span><span class="sxs-lookup"><span data-stu-id="77fb7-113">SQL Server Configuration Manager</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="77fb7-114">PowerShell</span><span class="sxs-lookup"><span data-stu-id="77fb7-114">PowerShell</span></span>](#PowerShellProcedure)  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="77fb7-115">SQL Server 構成マネージャーの使用</span><span class="sxs-lookup"><span data-stu-id="77fb7-115">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-enable-a-server-network-protocol"></a><span data-ttu-id="77fb7-116">サーバー ネットワーク プロトコルを有効にするには</span><span class="sxs-lookup"><span data-stu-id="77fb7-116">To enable a server network protocol</span></span>  
  
1.  <span data-ttu-id="77fb7-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーのコンソール ペインで、 **[SQL Server ネットワークの構成]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="77fb7-117">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the console pane, expand **SQL Server  Network Configuration**.</span></span>  
  
2.  <span data-ttu-id="77fb7-118">コンソール ペインで、 **[** *\<instance name> のプロトコル]* をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77fb7-118">In the console pane, click **Protocols for** *\<instance name>*.</span></span>  
  
3.  <span data-ttu-id="77fb7-119">詳細ペインで、変更するプロトコルを右クリックし、 **[有効化]** または **[無効化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77fb7-119">In the details pane, right-click the protocol you want to change, and then click **Enable** or **Disable**.</span></span>  
  
4.  <span data-ttu-id="77fb7-120">コンソール ペインで、 **[再起動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77fb7-120">In the console pane, click **SQL Server Services**.</span></span>  
  
5.  <span data-ttu-id="77fb7-121">詳細ウィンドウで、[ **SQL Server ( ***\<instance name>*** )**] を右クリックし、[**再起動**] をクリックしてサービスを停止し、再起動し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="77fb7-121">In the details pane, right-click **SQL Server (***\<instance name>***)**, and then click **Restart**, to stop and restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
##  <a name="using-sql-server-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="77fb7-122">SQL Server PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="77fb7-122">Using SQL Server PowerShell</span></span>  
  
#### <a name="to-enable-a-server-network-protocol-using-powershell"></a><span data-ttu-id="77fb7-123">PowerShell を使用してサーバー ネットワーク プロトコルを有効にするには</span><span class="sxs-lookup"><span data-stu-id="77fb7-123">To Enable a Server Network Protocol Using PowerShell</span></span>  
  
1.  <span data-ttu-id="77fb7-124">管理者権限を使用してコマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="77fb7-124">Using administrator permissions open a command prompt.</span></span>  
  
2.  <span data-ttu-id="77fb7-125">タスク バーから Windows PowerShell 2.0 を起動するか、[スタート] ボタンをクリックし、[すべてのプログラム]、[アクセサリ]、[Windows PowerShell]、[Windows PowerShell] の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="77fb7-125">Start Windows PowerShell 2.0 from the taskbar, or click Start, then All Programs, then Accessories, then Windows PowerShell, then Windows PowerShell.</span></span>  
  
3.  <span data-ttu-id="77fb7-126">「」と入力して**sqlps**モジュールをインポートします。`Import-Module "sqlps"`</span><span class="sxs-lookup"><span data-stu-id="77fb7-126">Import the **sqlps** module by entering `Import-Module "sqlps"`</span></span>  
  
4.  <span data-ttu-id="77fb7-127">次のステートメントを実行して TCP プロトコルおよび名前付きパイプ プロトコルの両方を有効にします。</span><span class="sxs-lookup"><span data-stu-id="77fb7-127">Execute the following statements to enable both the TCP and named pipes protocols.</span></span> <span data-ttu-id="77fb7-128">`<computer_name>` を、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を実行しているコンピューターの名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="77fb7-128">Replace `<computer_name>` with the name of the computer that is running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="77fb7-129">名前付きインスタンスを構成する場合は、 `MSSQLSERVER` をインスタンス名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="77fb7-129">If you are configuring a named instance, replace `MSSQLSERVER` with the instance name.</span></span>  
  
     <span data-ttu-id="77fb7-130">プロトコルを無効にするには、 `IsEnabled` プロパティを `$false`に設定します。</span><span class="sxs-lookup"><span data-stu-id="77fb7-130">To disable protocols, set the `IsEnabled` properties to `$false`.</span></span>  
  
    ```powershell
    $smo = 'Microsoft.SqlServer.Management.Smo.'  
    $wmi = new-object ($smo + 'Wmi.ManagedComputer').  
  
    # List the object properties, including the instance names.  
    $Wmi  
  
    # Enable the TCP protocol on the default instance.  
    $uri = "ManagedComputer[@Name='<computer_name>']/ ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Tcp']"  
    $Tcp = $wmi.GetSmoObject($uri)  
    $Tcp.IsEnabled = $true  
    $Tcp.Alter()  
    $Tcp  
  
    # Enable the named pipes protocol for the default instance.  
    $uri = "ManagedComputer[@Name='<computer_name>']/ ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Np']"  
    $Np = $wmi.GetSmoObject($uri)  
    $Np.IsEnabled = $true  
    $Np.Alter()  
    $Np  
    ```  
  
#### <a name="to-configure-the-protocols-for-the-local-computer"></a><span data-ttu-id="77fb7-131">ローカル コンピューターのプロトコルを構成するには</span><span class="sxs-lookup"><span data-stu-id="77fb7-131">To configure the protocols for the local computer</span></span>  
  
-   <span data-ttu-id="77fb7-132">スクリプトをローカルで実行してローカル コンピューターを構成する場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell ではローカル コンピューター名を動的に判断でき、スクリプトの柔軟性が向上します。</span><span class="sxs-lookup"><span data-stu-id="77fb7-132">When the script is run locally and configures the local computer, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell can make the script more flexible by dynamically determining the local computer name.</span></span> <span data-ttu-id="77fb7-133">ローカル コンピューター名を取得するには、 `$uri` 変数の行の設定を次の行に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="77fb7-133">To retrieve the local computer name, replace the line setting the `$uri` variable with the following line.</span></span>  
  
    ```powershell
    $uri = "ManagedComputer[@Name='" + (Get-Item env:\computername).Value + "']/ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Tcp']"  
    ```  
  
#### <a name="to-restart-the-database-engine-by-using-sql-server-powershell"></a><span data-ttu-id="77fb7-134">SQL Server PowerShell を使用してデータベース エンジンを再起動するには</span><span class="sxs-lookup"><span data-stu-id="77fb7-134">To restart the Database Engine by using SQL Server PowerShell</span></span>  
  
-   <span data-ttu-id="77fb7-135">プロトコルを有効または無効にした後は、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] を停止してから再起動して、変更を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="77fb7-135">After you enable or disable protocols, you must stop and restart the [!INCLUDE[ssDE](../../includes/ssde-md.md)] for the change to take effect.</span></span> <span data-ttu-id="77fb7-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell で既定のインスタンスを停止してから起動するには、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="77fb7-136">Execute the following statements to stop and start the default instance by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell.</span></span> <span data-ttu-id="77fb7-137">名前付きインスタンスを停止してから起動するには、 `'MSSQLSERVER'` を `'MSSQL$<instance_name>'`に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="77fb7-137">To stop and start a named instance replace `'MSSQLSERVER'` with `'MSSQL$<instance_name>'`.</span></span>  
  
    ```powershell
    # Get a reference to the ManagedComputer class.  
    CD SQLSERVER:\SQL\<computer_name>  
    $Wmi = (Get-Item .).ManagedComputer  
    # Get a reference to the default instance of the Database Engine.  
    $DfltInstance = $Wmi.Services['MSSQLSERVER']  
    # Display the state of the service.  
    $DfltInstance  
    # Stop the service.  
    $DfltInstance.Stop();  
    # Wait until the service has time to stop.  
    # Refresh the cache.  
    $DfltInstance.Refresh();   
    # Display the state of the service.  
    $DfltInstance  
    # Start the service again.  
    $DfltInstance.Start();  
    # Wait until the service has time to start.  
    # Refresh the cache and display the state of the service.  
    $DfltInstance.Refresh(); $DfltInstance  
    ```  
