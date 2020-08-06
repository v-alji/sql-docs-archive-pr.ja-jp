---
title: Server Core インストールでの SQL Server の構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- IsHadrEnabled server property
- Server Core Installation [SQL Server]
ms.assetid: ed6e5e94-4b8d-422a-a17e-61b05a4df903
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e74307374e0d07d69107649b42e0bc2f0897e98c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718675"
---
# <a name="configure-sql-server-on-a-server-core-installation"></a><span data-ttu-id="db136-102">Server Core インストールでの SQL Server の構成</span><span class="sxs-lookup"><span data-stu-id="db136-102">Configure SQL Server on a Server Core Installation</span></span>
  <span data-ttu-id="db136-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SP1 の Server Core インストールで [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] を構成する方法について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="db136-103">This topic covers details about configuring [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1.</span></span> 
  
##  <a name="configure-and-manage-server-core-on-windows-server"></a><span data-ttu-id="db136-104">Windows Server の Server Core の構成と管理</span><span class="sxs-lookup"><span data-stu-id="db136-104">Configure and Manage Server Core on Windows Server</span></span>  
 <span data-ttu-id="db136-105">ここでは、Server Core インストールの構成および管理に役立つトピックへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="db136-105">The section provides references to the topics that help configure and manage a Server Core installation.</span></span>  
  
 <span data-ttu-id="db136-106">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の一部の機能は、Server Core モードではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="db136-106">Not all features of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] are supported in Server Core mode.</span></span>  <span data-ttu-id="db136-107">このような一部の機能は、クライアント コンピューター、または Server Core を実行していない別のサーバーにインストールし、Server Core にインストールされているデータベース エンジン サービスに接続できます。</span><span class="sxs-lookup"><span data-stu-id="db136-107">Some of these features can be installed on a client computer or a different server that is not running Server Core, and connected to the Database Engine services installed on Server Core.</span></span>  
  
 <span data-ttu-id="db136-108">Server Core インストールをリモートで構成および管理する方法の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="db136-108">For more information about configuring and managing a Server Core installation remotely, see the following topics:</span></span>  
  
-   <span data-ttu-id="db136-109">[Windows server 2008 R2: Server Core 展開のベストプラクティス](https://go.microsoft.com/fwlink/?LinkID=245957)(https://go.microsoft.com/fwlink/?LinkID=245957)</span><span class="sxs-lookup"><span data-stu-id="db136-109">[Windows Server 2008 R2: Best Practices for Server Core Deployments](https://go.microsoft.com/fwlink/?LinkID=245957) (https://go.microsoft.com/fwlink/?LinkID=245957)</span></span>  
  
-   <span data-ttu-id="db136-110">[Server Core インストールの構成: 概要](https://go.microsoft.com/fwlink/?LinkId=245958)(https://go.microsoft.com/fwlink/?LinkId=245958)</span><span class="sxs-lookup"><span data-stu-id="db136-110">[Configuring a Server Core installation: Overview](https://go.microsoft.com/fwlink/?LinkId=245958) (https://go.microsoft.com/fwlink/?LinkId=245958)</span></span>  
  
-   <span data-ttu-id="db136-111">[Sconfig.cmd を使用して Windows server 2008 R2 の Server Core インストールを構成](https://go.microsoft.com/fwlink/?LinkId=245959)する (https://go.microsoft.com/fwlink/?LinkId=245959)</span><span class="sxs-lookup"><span data-stu-id="db136-111">[Configuring a Server Core installation of Windows Server 2008 R2 with Sconfig.cmd](https://go.microsoft.com/fwlink/?LinkId=245959) (https://go.microsoft.com/fwlink/?LinkId=245959)</span></span>  
  
-   <span data-ttu-id="db136-112">[Windows server 2008 R2 の Server Core インストールを実行しているサーバーへのサーバーロールのインストール: 概要](https://go.microsoft.com/fwlink/?LinkId=245960)(https://go.microsoft.com/fwlink/?LinkId=245960)</span><span class="sxs-lookup"><span data-stu-id="db136-112">[Installing a server role on a server running a Server Core installation of Windows Server 2008 R2: Overview](https://go.microsoft.com/fwlink/?LinkId=245960) (https://go.microsoft.com/fwlink/?LinkId=245960)</span></span>  
  
-   <span data-ttu-id="db136-113">Windows [server 2008 R2 の Server Core インストールを実行しているサーバーへの Windows 機能のインストール: 概要](https://go.microsoft.com/fwlink/?LinkId=245961)(https://go.microsoft.com/fwlink/?LinkId=245961)</span><span class="sxs-lookup"><span data-stu-id="db136-113">[Installing Windows Features on a server running a Server Core installation of Windows Server 2008 R2: Overview](https://go.microsoft.com/fwlink/?LinkId=245961) (https://go.microsoft.com/fwlink/?LinkId=245961)</span></span>  
  
-   <span data-ttu-id="db136-114">[Server Core インストールの管理: 概要](https://go.microsoft.com/fwlink/?LinkId=245962)(https://go.microsoft.com/fwlink/?LinkId=245962)</span><span class="sxs-lookup"><span data-stu-id="db136-114">[Managing a Server Core installation: Overview](https://go.microsoft.com/fwlink/?LinkId=245962) (https://go.microsoft.com/fwlink/?LinkId=245962)</span></span>  
  
-   <span data-ttu-id="db136-115">[Server Core インストールの管理](https://go.microsoft.com/fwlink/?LinkId=245963)(https://go.microsoft.com/fwlink/?LinkId=245963)</span><span class="sxs-lookup"><span data-stu-id="db136-115">[Administering a Server Core installation](https://go.microsoft.com/fwlink/?LinkId=245963) (https://go.microsoft.com/fwlink/?LinkId=245963)</span></span>  
  
##  <a name="install-updates"></a><span data-ttu-id="db136-116">の更新プログラムをインストールする</span><span class="sxs-lookup"><span data-stu-id="db136-116">Install updates</span></span>  
 <span data-ttu-id="db136-117">ここでは、Windows Server Core コンピューターに [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の更新プログラムをインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="db136-117">This section provides information about installing updates for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on a Windows Server Core machine.</span></span> <span data-ttu-id="db136-118">常に最新のセキュリティ更新プログラムがインストールされた状態になるように、適切なタイミングで最新の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更新プログラムを評価してインストールすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="db136-118">We recommend that customers evaluate and install latest [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] updates in a timely manner to make sure that systems are up-to-date with the most recent security updates.</span></span> <span data-ttu-id="db136-119">Windows Server Core コンピューターへののインストールの詳細について [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は、「 [Install SQL Server 2014 On Server core](install-sql-server-on-server-core.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db136-119">For more information about installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on a Windows Server Core machine, see [Install SQL Server 2014 on Server Core](install-sql-server-on-server-core.md).</span></span>  
  
 <span data-ttu-id="db136-120">製品の更新プログラムをインストールするための 2 つのシナリオを次に示します。</span><span class="sxs-lookup"><span data-stu-id="db136-120">The following are the two scenarios for installing product updates:</span></span>  
  
-   [<span data-ttu-id="db136-121">新規インストール時に SQL Server 2014 の更新プログラムをインストールする</span><span class="sxs-lookup"><span data-stu-id="db136-121">Installing Updates for SQL Server 2014 During a New Installation</span></span>](#installing-updates-during-a-new-installation) 
  
-   [<span data-ttu-id="db136-122">インストール後に SQL Server 2014 の更新プログラムをインストールする</span><span class="sxs-lookup"><span data-stu-id="db136-122">Installing Updates for SQL Server 2014 After It Has Been Installed</span></span>](#installing-updates-after-installation) 
  
### <a name="installing-updates-during-a-new-installation"></a><span data-ttu-id="db136-123">新規インストール中の更新プログラムのインストール</span><span class="sxs-lookup"><span data-stu-id="db136-123">Installing updates during a new installation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="db136-124">セットアップでは、コマンド プロンプトによる Server Core オペレーティング システムへのインストールのみがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="db136-124">Setup supports only command prompt installations on Server Core operating system.</span></span> <span data-ttu-id="db136-125">詳細については、「[コマンド プロンプトからの SQL Server 2014 のインストール](install-sql-server-from-the-command-prompt.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db136-125">For more information, see [Install SQL Server 2014 from the Command Prompt](install-sql-server-from-the-command-prompt.md).</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="db136-126">セットアップでは、メインの製品とそれに適用可能な更新プログラムが同時にインストールされるように、最新の製品の更新プログラムとメインの製品のインストールが統合されています。</span><span class="sxs-lookup"><span data-stu-id="db136-126">setup integrates the latest product updates with the main product installation so that the main product and its applicable updates are installed at the same time.</span></span>  
  
 <span data-ttu-id="db136-127">セットアップで最新バージョンの適用可能な更新プログラムが検出されると、ダウンロードが実行されて、現在の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップ プロセスと統合されます。</span><span class="sxs-lookup"><span data-stu-id="db136-127">After Setup finds the latest versions of the applicable updates, it downloads and integrates them with the current [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] setup process.</span></span> <span data-ttu-id="db136-128">製品の更新プログラムは、累積更新プログラム、サービス パック、またはサービス パックと累積更新プログラムに取り込むことができます。</span><span class="sxs-lookup"><span data-stu-id="db136-128">Product Update can pull in a cumulative update, service pack, or service pack plus cumulative update.</span></span>  
  
 <span data-ttu-id="db136-129">メインの製品のインストールに最新の製品の更新プログラムを含めるには、UpdateEnabled パラメーターと UpdateSource パラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="db136-129">Specify the UpdateEnabled, and UpdateSource parameters to include the latest product updates with the main product installation.</span></span> <span data-ttu-id="db136-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップ時に製品の更新プログラムを有効にする場合は、次の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db136-130">Refer the following example to enable product updates during the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup:</span></span>  
  
```cmd 
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,Replication /INSTANCENAME=MSSQLSERVER /SQLSVCACCOUNT="<DomainName\UserName>" /SQLSVCPASSWORD="<StrongPassword>" /SQLSYSADMINACCOUNTS="<DomainName\UserName>" /AGTSVCACCOUNT="NT AUTHORITY\Network Service" /UpdateEnabled=True /UpdateSource="<SourcePath>" /IACCEPTSQLSERVERLICENSETERMS  
```  
  
### <a name="installing-updates-after-installation"></a><span data-ttu-id="db136-131">インストール後の更新プログラムのインストール</span><span class="sxs-lookup"><span data-stu-id="db136-131">Installing updates after installation</span></span> 
 <span data-ttu-id="db136-132">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のインストール済みインスタンスでは、一般配布リリース (GDR) やサービス パック (SP) を含む最新のセキュリティ更新プログラムと重要な更新プログラムを適用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="db136-132">On an installed instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], we recommend that you apply the latest security updates and critical updates including General Distribution Releases (GDRs), and Service Packs (SPs).</span></span> <span data-ttu-id="db136-133">個々の累積更新プログラムとセキュリティ更新プログラムは、状況に応じて "必要なときに" に適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="db136-133">Individual Cumulative updates and security updates should be adopted on a case-by-case, "as-needed" basis.</span></span> <span data-ttu-id="db136-134">更新プログラムを評価し、必要な場合は適用します。</span><span class="sxs-lookup"><span data-stu-id="db136-134">Evaluate the update; if it's needed, then apply it.</span></span>  
  
 <span data-ttu-id="db136-135">コマンド プロンプトで更新プログラムを適用する際に、<package_name> の部分は実際の更新プログラム パッケージの名前に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="db136-135">Apply an update at a command prompt, replacing <package_name> with the name of your update package:</span></span>  
  
-   <span data-ttu-id="db136-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の 1 つのインスタンスとすべての共有コンポーネントを更新します。</span><span class="sxs-lookup"><span data-stu-id="db136-136">Update a single instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and all shared components.</span></span> <span data-ttu-id="db136-137">InstanceName パラメーターまたは InstanceID パラメーターを使用してインスタンスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="db136-137">You can specify the instance either by using the InstanceName parameter or the InstanceID parameter.</span></span>  
  
    ```  
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /InstanceName=MyInstance  
    ```  
  
-   <span data-ttu-id="db136-138">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 共有コンポーネントのみを更新します。</span><span class="sxs-lookup"><span data-stu-id="db136-138">Update [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] shared components only:</span></span>  
  
    ```  
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch  
    ```  
  
-   <span data-ttu-id="db136-139">コンピューター上のすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスと、すべての共有コンポーネントを更新します。</span><span class="sxs-lookup"><span data-stu-id="db136-139">Update all instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the computer and all shared components:</span></span>  
  
    ```  
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /AllInstances  
    ```  
  
##  <a name="startstop-sql-server-service"></a><span data-ttu-id="db136-140">サービスの開始/停止 SQL Server</span><span class="sxs-lookup"><span data-stu-id="db136-140">Start/Stop SQL Server service</span></span>  
 <span data-ttu-id="db136-141">コマンド プロンプトから [sqlservr アプリケーション](../../tools/sqlservr-application.md) を使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを起動、停止、一時停止、または続行します。</span><span class="sxs-lookup"><span data-stu-id="db136-141">The [sqlservr Application](../../tools/sqlservr-application.md) application starts, stops, pauses, and continues an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a command prompt.</span></span>  
  
 <span data-ttu-id="db136-142">また、Net サービスを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを起動および停止することもできます。</span><span class="sxs-lookup"><span data-stu-id="db136-142">You can also use Net services to start and stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services.</span></span>  
  
## <a name="enable-alwayson-availability-groups"></a><span data-ttu-id="db136-143">AlwaysOn 可用性グループの有効化</span><span class="sxs-lookup"><span data-stu-id="db136-143">Enable AlwaysOn Availability Groups</span></span>  
 <span data-ttu-id="db136-144">AlwaysOn 可用性グループが有効になっていることは、サーバー インスタンスが高可用性ディザスター リカバリー ソリューションとして可用性グループを使用するための前提条件です。</span><span class="sxs-lookup"><span data-stu-id="db136-144">Being enabled for AlwaysOn Availability Groups is a prerequisite for a server instance to use availability groups as a high availability and disaster recovery solution.</span></span> <span data-ttu-id="db136-145">AlwaysOn 可用性グループの管理に関する詳細については、「[AlwaysOn 可用性グループの有効化と無効化 &#40;SQL Server&#41;](../availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)」参照してください。</span><span class="sxs-lookup"><span data-stu-id="db136-145">For more information about managing the AlwaysOn Availability Groups, see [Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;](../availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md).</span></span>  
  
### <a name="using-sql-server-configuration-manager-remotely"></a><span data-ttu-id="db136-146">リモートでの SQL Server 構成マネージャーの使用</span><span class="sxs-lookup"><span data-stu-id="db136-146">Using SQL Server Configuration Manager Remotely</span></span>  
 <span data-ttu-id="db136-147">次の手順は、[!INCLUDE[win7](../../includes/win7-md.md)] 以降のクライアント エディションを実行している PC、またはサーバー グラフィック シェルがインストールされている別のサーバー ([!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] の完全インストールやサーバー グラフィック シェル機能を有効にした Windows Server 8 インストールなど) に対して実行してください。</span><span class="sxs-lookup"><span data-stu-id="db136-147">These steps are meant to be performed on a PC running the client edition of [!INCLUDE[win7](../../includes/win7-md.md)] or later, or another server that has the Server Graphical Shell installed (i.e. a full installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] or a Windows Server 8 installation with the Server Graphical Shell feature enabled).</span></span>  
  
1.  <span data-ttu-id="db136-148">[コンピューターの管理] を開きます。</span><span class="sxs-lookup"><span data-stu-id="db136-148">Open Computer Management.</span></span> <span data-ttu-id="db136-149">[コンピューターの管理] を開くには、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="db136-149">To open Computer Management do one of the following:</span></span>  
  
    1.  <span data-ttu-id="db136-150">[!INCLUDE[win7](../../includes/win7-md.md)]、Windows Server 2008、または [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]の場合:</span><span class="sxs-lookup"><span data-stu-id="db136-150">On [!INCLUDE[win7](../../includes/win7-md.md)], Windows Server 2008, or [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]:</span></span>  
  
        1.  <span data-ttu-id="db136-151">[スタート] ボタンをクリックし、[すべてのプログラム]、[管理ツール] の順にクリックして、[コンピューターの管理] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="db136-151">Click Start, click All Programs, click Administrative Tools, and then click Computer Management.</span></span>  
  
        2.  <span data-ttu-id="db136-152">[スタート] ボタンをクリックし、[ファイル名を指定して実行] をクリックして「COMPMGMT.MSC」と入力し、[OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="db136-152">Click Start, click Run, type COMPMGMT.MSC, and then click OK.</span></span>  
  
    2.  <span data-ttu-id="db136-153">サーバー グラフィック シェルを有効にした Windows 8 の場合:</span><span class="sxs-lookup"><span data-stu-id="db136-153">On Windows 8 with Server Graphical Shell enabled:</span></span>  
  
        1.  <span data-ttu-id="db136-154">マウス ポインターを画面の左下隅に移動し、[スタート] のオーバーレイが表示されたら右クリックします。</span><span class="sxs-lookup"><span data-stu-id="db136-154">Move your mouse to the bottom-left corner of the screen and right-click when you see the Start overlay.</span></span>  
  
        2.  <span data-ttu-id="db136-155">コンテキスト メニューの [コンピューターの管理] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="db136-155">Select Computer Management  from the context menu.</span></span>  
  
2.  <span data-ttu-id="db136-156">コンソール ツリーで、[コンピューターの管理] を右クリックし、[別のコンピューターへ接続] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="db136-156">In the console tree, right-click Computer Management, and then click Connect to another computer.</span></span>  
  
3.  <span data-ttu-id="db136-157">[コンピューターの選択] ダイアログ ボックスで、管理する Server Core コンピューターの名前を入力するか、[参照] をクリックして目的のコンピューターを探し、[OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="db136-157">In the Select Computer dialog box, type the name of the Server Core machine that you want to manage, or click Browse to find it, and then click OK.</span></span>  
  
4.  <span data-ttu-id="db136-158">コンソール ツリーで、選択した Server Core コンピューターの [コンピューターの管理] の下にある [サービスとアプリケーション] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="db136-158">In the console tree, under Computer Management of the Server Core machine, click Services and Applications.</span></span>  
  
5.  <span data-ttu-id="db136-159">[ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャー] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="db136-159">Double click [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
6.  <span data-ttu-id="db136-160">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Configuration Manager で、[サービス] をクリックし、[ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ()] を右クリックし [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<instance name> ます。ここで、 \<instance name> は AlwaysOn 可用性グループを有効にするローカルサーバーインスタンスの名前です。 [プロパティ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="db136-160">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, click [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Services, right-click [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (\<instance name>), where \<instance name> is the name of a local server instance for which you want to enable AlwaysOn Availability Groups, and click Properties.</span></span>  
  
7.  <span data-ttu-id="db136-161">[AlwaysOn 高可用性] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="db136-161">Select the AlwaysOn High Availability tab.</span></span>  
  
8.  <span data-ttu-id="db136-162">[Windows フェールオーバー クラスター名] フィールドに、ローカル フェールオーバー クラスター ノードの名前が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="db136-162">Verify that Windows failover cluster name field contains the name of the local failover cluster node.</span></span> <span data-ttu-id="db136-163">このフィールドが空白の場合、現在、このサーバー インスタンスでは AlwaysOn 可用性グループがサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="db136-163">If this field is blank, this server instance currently does not support AlwaysOn Availability Groups.</span></span> <span data-ttu-id="db136-164">ローカル コンピューターがクラスター ノードではないか、WSFC クラスターがシャットダウンされているか、このエディションの [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では AlwaysOn 可用性グループがサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="db136-164">Either the local computer is not a cluster node, the WSFC cluster has been shut down, or this edition of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] that does not support AlwaysOn Availability Groups.</span></span>  
  
9. <span data-ttu-id="db136-165">[AlwaysOn 可用性グループを有効にする] チェック ボックスをオンにし、[OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="db136-165">Select the Enable AlwaysOn Availability Groups check box, and click OK.</span></span>  
  
10. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="db136-166">構成マネージャーによって変更内容が保存されます。</span><span class="sxs-lookup"><span data-stu-id="db136-166">Configuration Manager saves your change.</span></span> <span data-ttu-id="db136-167">その後、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを手動で再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="db136-167">Then, you must manually restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="db136-168">業務上の要件に合った時間帯を選んで再起動することができます。</span><span class="sxs-lookup"><span data-stu-id="db136-168">This enables you to choose a restart time that is best for your business requirements.</span></span> <span data-ttu-id="db136-169">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスが再起動されると、AlwaysOn が有効になり、IsHadrEnabled サーバー プロパティが 1 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="db136-169">When the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service restarts, AlwaysOn will be enabled, and the IsHadrEnabled server property will be set to 1.</span></span>  
  
> [!NOTE]
>  -   <span data-ttu-id="db136-170">ターゲット コンピューターに接続するには、適切なユーザー権限を持っているか、そのコンピューターに対する適切な権限が委任されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="db136-170">You must have the appropriate user rights or you must have been delegated the appropriate authority on the target computer to connect to that computer.</span></span>  
> -   <span data-ttu-id="db136-171">管理しているコンピューターの名前は、コンソール ツリーの [コンピューターの管理] の横に、かっこで囲まれて表示されます。</span><span class="sxs-lookup"><span data-stu-id="db136-171">The name of the computer that you are managing appears in parentheses next to Computer Management in the console tree.</span></span>  
  
### <a name="using-powershell-cmdlets-to-enable-alwayson-availability-groups"></a><span data-ttu-id="db136-172">PowerShell コマンドレットを使用して AlwaysOn 可用性グループを有効にする</span><span class="sxs-lookup"><span data-stu-id="db136-172">Using PowerShell Cmdlets to Enable AlwaysOn Availability Groups</span></span>

 <span data-ttu-id="db136-173">PowerShell コマンドレット Enable-SqlAlwaysOn を使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスの AlwaysOn 可用性グループを有効にします。</span><span class="sxs-lookup"><span data-stu-id="db136-173">The PowerShell Cmdlet, Enable-SqlAlwaysOn, is used to enable AlwaysOn Availability Group on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="db136-174">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスの実行中に AlwaysOn 可用性グループを有効にした場合は、変更を完了するために、データベース エンジン サービスを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="db136-174">If AlwaysOn Availability Groups is enable while the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service is running, the Database Engine service must be restarted for the change to complete.</span></span> <span data-ttu-id="db136-175">-Force パラメーターを指定しない限り、サービスを再起動するかどうかを確認するメッセージが表示されます。キャンセルすると、操作は実行されません。</span><span class="sxs-lookup"><span data-stu-id="db136-175">Unless you specify the -Force parameter, the cmdlet prompts you to ask whether you wish to restart the service; if cancelled, no operation occurs.</span></span>  
  
 <span data-ttu-id="db136-176">このコマンドレットを実行するには、管理者権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="db136-176">You must have Administrator permissions to execute this cmdlet.</span></span>  
  
 <span data-ttu-id="db136-177">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスで AlwaysOn 可用性グループを有効にするには、次のいずれかの構文を使用できます。</span><span class="sxs-lookup"><span data-stu-id="db136-177">You can use one of the following syntaxes to enable AlwaysOn Availability Groups for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
```  
Enable-SqlAlwaysOn [-Path <string>] [-Credential <PSCredential>] [-Force] [-NoServiceRestart] [-Confirm] [-WhatIf] [<Commom Parameters>]  
```  
  
```  
Enable-SqlAlwaysOn -InputObject <Server> [-Credential <PSCredential>] [-Force] [-NoServiceRestart] [-Confirm] [-WhatIf] [<Commom Parameters>]  
```  
  
```  
Enable-SqlAlwaysOn [-ServerInstance <string>] [-Credential <PSCredential>] [-Force] [-NoServiceRestart] [-Confirm] [-WhatIf] [<Commom Parameters>]  
```  
  
 <span data-ttu-id="db136-178">次の PowerShell コマンドは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス (Machine\Instance) の AlwaysOn 可用性グループを有効にします。</span><span class="sxs-lookup"><span data-stu-id="db136-178">The following PowerShell command enables AlwaysOn Availability Groups on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (Machine\Instance):</span></span>  
  
```powershell
Enable-SqlAlwaysOn -Path SQLSERVER:\SQL\Machine\Instance  
```  
  
## <a name="configuring-remote-access-of-sql-server-running-on-server-core"></a><span data-ttu-id="db136-179">Server Core で実行されている SQL Server のリモートアクセスの構成</span><span class="sxs-lookup"><span data-stu-id="db136-179">Configuring remote access of SQL Server running on Server Core</span></span>  
 <span data-ttu-id="db136-180">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Server Core SP1 で実行している [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] インスタンスのリモート アクセスを構成するには、以下で説明する操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="db136-180">Perform the actions described below to configure remote access of a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] instance that is running on [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1.</span></span>  
  
### <a name="enable-remote-connections-on-an-instance-of-sql-server"></a><span data-ttu-id="db136-181">SQL Server のインスタンスでリモート接続を有効にする</span><span class="sxs-lookup"><span data-stu-id="db136-181">Enable remote connections on an instance of SQL Server</span></span> 
 <span data-ttu-id="db136-182">リモート接続を有効にするには、SQLCMD.exe をローカルで使用して、Server Core インスタンスに対して次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="db136-182">To enable remote connections, use SQLCMD.exe locally and execute the following statements against the Server Core instance:</span></span>  
  
-   `EXEC sys.sp_configure N'remote access', N'1'`  
  
     `GO`  
  
-   `RECONFIGURE WITH OVERRIDE`  
  
     `GO`  
  
### <a name="enable-and-start-the-sql-server-browser-service"></a><span data-ttu-id="db136-183">SQL Server Browser サービスを有効にして開始する</span><span class="sxs-lookup"><span data-stu-id="db136-183">Enable and start the SQL Server Browser service</span></span>  
 <span data-ttu-id="db136-184">Browser サービスは、既定では無効になっています。</span><span class="sxs-lookup"><span data-stu-id="db136-184">By default, the Browser service is disabled.</span></span>  <span data-ttu-id="db136-185">Server Core で実行している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスで無効になっている場合、このサービスを有効にするには、コマンド プロンプトから次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="db136-185">If it is disabled on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on Server Core, run the following command from the command prompt to enable it:</span></span>  
  
 `sc config SQLBROWSER start= auto`  
  
 <span data-ttu-id="db136-186">有効にした後は、コマンド プロンプトから次のコマンドを実行して、サービスを開始します。</span><span class="sxs-lookup"><span data-stu-id="db136-186">After it is enabled, run the following command from the command prompt to start the service:</span></span>  
  
 `net start SQLBROWSER`  
  
### <a name="create-exceptions-in-windows-firewall"></a><span data-ttu-id="db136-187">Windows ファイアウォールで例外を作成する</span><span class="sxs-lookup"><span data-stu-id="db136-187">Create exceptions in Windows Firewall</span></span>  
 <span data-ttu-id="db136-188">Windows ファイアウォールで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アクセスの例外を作成するには、「 [SQL Server のアクセスを許可するための Windows ファイアウォールの構成](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)」で指定されている手順に従います。</span><span class="sxs-lookup"><span data-stu-id="db136-188">To create exceptions for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] access in Windows Firewall, follow the steps specified in [Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
### <a name="enable-tcpip-on-an-instance-of-sql-server"></a><span data-ttu-id="db136-189">SQL Server のインスタンスで TCP/IP を有効にする</span><span class="sxs-lookup"><span data-stu-id="db136-189">Enable TCP/IP on an instance of SQL Server</span></span>
 <span data-ttu-id="db136-190">Server Core 上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに対して TCP/IP プロトコルを有効にするには、Windows PowerShell を使用します。</span><span class="sxs-lookup"><span data-stu-id="db136-190">The TCP/IP protocol can be enabled through Windows PowerShell for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on Server Core.</span></span> <span data-ttu-id="db136-191">次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="db136-191">Follow these steps:</span></span>  
  
1.  <span data-ttu-id="db136-192">Windows Server 2008 R2 Server Core SP1 を搭載しているコンピューターで、タスク マネージャーを起動します。</span><span class="sxs-lookup"><span data-stu-id="db136-192">On the computer that is running Windows Server 2008 R2 Server Core SP1, launch Task Manager.</span></span>  
  
2.  <span data-ttu-id="db136-193">**[アプリケーション]** タブで、 **[新しいタスク]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="db136-193">On the **Applications** tab, click **New Task**.</span></span>  
  
3.  <span data-ttu-id="db136-194">**[新しいタスクの作成]** ダイアログ ボックスで、 **[開く]** フィールドに **sqlps.exe** と入力して、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="db136-194">In the **Create New Task** dialog box, type **sqlps.exe** in the **Open** field and then click **OK**.</span></span> <span data-ttu-id="db136-195">**[Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell]** ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="db136-195">This opens the **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell** window.</span></span>  
  
4.  <span data-ttu-id="db136-196">**[Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell]** ウィンドウで、次のスクリプトを実行して TCP/IP プロトコルを有効にします。</span><span class="sxs-lookup"><span data-stu-id="db136-196">In the **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell** window, run the following script to enable the TCP/IP protocol:</span></span>  
  
```powershell
$smo = 'Microsoft.SqlServer.Management.Smo.'  
$wmi = new-object ($smo + 'Wmi.ManagedComputer')  
# Enable the TCP protocol on the default instance.  If the instance is named, replace MSSQLSERVER with the instance name in the following line.  
$uri = "ManagedComputer[@Name='" + (get-item env:\computername).Value + "']/ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Tcp']"  
$Tcp = $wmi.GetSmoObject($uri)  
$Tcp.IsEnabled = $true  
$Tcp.Alter()  
$Tcp  
```  
  
##  <a name="sql-server-profiler"></a><span data-ttu-id="db136-197">SQL Server プロファイラー</span><span class="sxs-lookup"><span data-stu-id="db136-197">SQL Server Profiler</span></span>  
 <span data-ttu-id="db136-198">リモート コンピューターで、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を起動し、[ファイル] メニューの [新しいトレース] をクリックすると、[サーバーへの接続] ダイアログ ボックスが表示されます。このダイアログ ボックスでは、Server Core コンピューター上にある接続先の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="db136-198">On a remote machine, start [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] and select New Trace from the File menu, the application displays a Connect to Server dialog box where you can specify the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, residing on the Server Core machine, to which you want to connect.</span></span> <span data-ttu-id="db136-199">詳細については、「 [SQL Server Profiler の起動](../../tools/sql-server-profiler/start-sql-server-profiler.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db136-199">For more information, see [Start SQL Server Profiler](../../tools/sql-server-profiler/start-sql-server-profiler.md).</span></span>  
  
 <span data-ttu-id="db136-200">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]の実行に必要な権限の詳細については、「 [SQL Server Profiler の実行に必要な権限](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db136-200">For more information on the permissions required to run [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], see [Permissions Required to Run SQL Server Profiler](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md).</span></span>  
  
 <span data-ttu-id="db136-201">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]の詳細については、「 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db136-201">For additional details about [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], see [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md).</span></span>  
  
##  <a name="sql-server-auditing"></a><span data-ttu-id="db136-202">SQL Server 監査</span><span class="sxs-lookup"><span data-stu-id="db136-202">SQL Server Auditing</span></span>  
 <span data-ttu-id="db136-203">監査は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)] をリモートで使用して定義できます。</span><span class="sxs-lookup"><span data-stu-id="db136-203">You can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)] remotely to define an audit.</span></span> <span data-ttu-id="db136-204">監査を作成して有効にすると、ターゲットがエントリを受け取るようになります。</span><span class="sxs-lookup"><span data-stu-id="db136-204">After the audit is created and enabled, the target will receive entries.</span></span> <span data-ttu-id="db136-205">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 監査の作成および管理の詳細については、「[SQL Server Audit &#40;データベース エンジン&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db136-205">For more information about creating and managing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] audits, see [SQL Server Audit &#40;Database Engine&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).</span></span>  
  
##  <a name="sql-servevr-command-prompt-utilities"></a><span data-ttu-id="db136-206">SQL server のコマンドプロンプトユーティリティ</span><span class="sxs-lookup"><span data-stu-id="db136-206">SQL Servevr Command Prompt Utilities</span></span>  
 <span data-ttu-id="db136-207">次のコマンド プロンプト ユーティリティを使用すると、Server Core コンピューターでの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 操作のスクリプトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="db136-207">You can use the following command prompt utilities that enable you to script [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] operations on a Server Core machine.</span></span> <span data-ttu-id="db136-208">次の表は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に付属する、Server Core 用のコマンド プロンプト ユーティリティの一覧です。</span><span class="sxs-lookup"><span data-stu-id="db136-208">The following table contains a list of command prompt utilities that ship with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for Server Core:</span></span>  
  
|<span data-ttu-id="db136-209">**Utility**</span><span class="sxs-lookup"><span data-stu-id="db136-209">**Utility**</span></span>|<span data-ttu-id="db136-210">**説明**</span><span class="sxs-lookup"><span data-stu-id="db136-210">**Description**</span></span>|<span data-ttu-id="db136-211">**インストール先**</span><span class="sxs-lookup"><span data-stu-id="db136-211">**Installed in**</span></span>|  
|-----------------|---------------------|----------------------|  
|[<span data-ttu-id="db136-212">bcp ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="db136-212">bcp Utility</span></span>](../../tools/bcp-utility.md)|<span data-ttu-id="db136-213">ユーザー指定の形式で、 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスとデータ ファイルとの間でデータをコピーします。</span><span class="sxs-lookup"><span data-stu-id="db136-213">Used to copy data between an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and a data file in a user-specified format.</span></span>|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]<span data-ttu-id="db136-214">Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="db136-214">Tools\Binn</span></span>|  
|[<span data-ttu-id="db136-215">dtexec ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="db136-215">dtexec Utility</span></span>](../../integration-services/packages/dtexec-utility.md)|<span data-ttu-id="db136-216">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを構成および実行します。</span><span class="sxs-lookup"><span data-stu-id="db136-216">Used to configure and execute an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package.</span></span>|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]<span data-ttu-id="db136-217">DTS\Binn</span><span class="sxs-lookup"><span data-stu-id="db136-217">DTS\Binn</span></span>|  
|[<span data-ttu-id="db136-218">dtutil ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="db136-218">dtutil Utility</span></span>](../../integration-services/dtutil-utility.md)|<span data-ttu-id="db136-219">SSIS パッケージを管理します。</span><span class="sxs-lookup"><span data-stu-id="db136-219">Used to manage SSIS packages.</span></span>|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]<span data-ttu-id="db136-220">DTS\Binn</span><span class="sxs-lookup"><span data-stu-id="db136-220">DTS\Binn</span></span>|  
|[<span data-ttu-id="db136-221">osql ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="db136-221">osql Utility</span></span>](../../tools/osql-utility.md)|<span data-ttu-id="db136-222">[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント、システム プロシージャ、およびスクリプト ファイルをコマンド プロンプトで入力できるようになります。</span><span class="sxs-lookup"><span data-stu-id="db136-222">Allows you to enter [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, system procedures, and script files at the command prompt.</span></span>|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]<span data-ttu-id="db136-223">Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="db136-223">Tools\Binn</span></span>|  
|[<span data-ttu-id="db136-224">sqlagent90 アプリケーション</span><span class="sxs-lookup"><span data-stu-id="db136-224">sqlagent90 Application</span></span>](../../tools/sqlagent90-application.md)|<span data-ttu-id="db136-225">コマンド プロンプトから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを開始します。</span><span class="sxs-lookup"><span data-stu-id="db136-225">Used to start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent from a command prompt.</span></span>|<span data-ttu-id="db136-226">\<drive>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\<*instance_name*>\MSSQL\Binn</span><span class="sxs-lookup"><span data-stu-id="db136-226">\<drive>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\<*instance_name*>\MSSQL\Binn</span></span>|  
|[<span data-ttu-id="db136-227">sqlcmd Utility</span><span class="sxs-lookup"><span data-stu-id="db136-227">sqlcmd Utility</span></span>](../../tools/sqlcmd-utility.md)|<span data-ttu-id="db136-228">[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント、システム プロシージャ、およびスクリプト ファイルをコマンド プロンプトで入力できるようになります。</span><span class="sxs-lookup"><span data-stu-id="db136-228">Allows you to enter [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, system procedures, and script files at the command prompt.</span></span>|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]<span data-ttu-id="db136-229">Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="db136-229">Tools\Binn</span></span>|  
|[<span data-ttu-id="db136-230">SQLdiag ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="db136-230">SQLdiag Utility</span></span>](../../tools/sqldiag-utility.md)|<span data-ttu-id="db136-231">[!INCLUDE[msCoName](../../includes/msconame-md.md)] カスタマー サポート サービス用の診断情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="db136-231">Used to collect diagnostic information for [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support.</span></span>|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]<span data-ttu-id="db136-232">Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="db136-232">Tools\Binn</span></span>|  
|[<span data-ttu-id="db136-233">sqlmaint ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="db136-233">sqlmaint Utility</span></span>](../../tools/sqlmaint-utility.md)|<span data-ttu-id="db136-234">以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で作成されたデータベース メンテナンス プランを実行します。</span><span class="sxs-lookup"><span data-stu-id="db136-234">Used to execute database maintenance plans created in previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|<span data-ttu-id="db136-235">\<drive>: \MSSQL12. ファイルの場合 \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]MSSQLSERVER\MSSQL\Binn</span><span class="sxs-lookup"><span data-stu-id="db136-235">\<drive>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.MSSQLSERVER\MSSQL\Binn</span></span>|  
|[<span data-ttu-id="db136-236">sqlps ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="db136-236">sqlps Utility</span></span>](../../tools/sqlps-utility.md)|<span data-ttu-id="db136-237">PowerShell コマンドおよびスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="db136-237">Used to run PowerShell commands and scripts.</span></span> <span data-ttu-id="db136-238">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell プロバイダーおよびコマンドレットの読み込みと登録を行います。</span><span class="sxs-lookup"><span data-stu-id="db136-238">Loads and registers the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell provider and cmdlets.</span></span>|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]<span data-ttu-id="db136-239">Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="db136-239">Tools\Binn</span></span>|  
|[<span data-ttu-id="db136-240">sqlservr アプリケーション</span><span class="sxs-lookup"><span data-stu-id="db136-240">sqlservr Application</span></span>](../../tools/sqlservr-application.md)|<span data-ttu-id="db136-241">トラブルシューティングを行うために、コマンド プロンプトから [!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスを開始および停止します。</span><span class="sxs-lookup"><span data-stu-id="db136-241">Used to start and stop an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] from the command prompt for troubleshooting.</span></span>|<span data-ttu-id="db136-242">\<drive>: \MSSQL12. ファイルの場合 \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]MSSQLSERVER\MSSQL\Binn</span><span class="sxs-lookup"><span data-stu-id="db136-242">\<drive>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.MSSQLSERVER\MSSQL\Binn</span></span>|  
  
##  <a name="use-troubleshooting-tools"></a><span data-ttu-id="db136-243">トラブルシューティング ツールの使用</span><span class="sxs-lookup"><span data-stu-id="db136-243">Use troubleshooting tools</span></span>  
 <span data-ttu-id="db136-244">[SQLdiag ユーティリティ](../../tools/sqldiag-utility.md) を使用すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] やその他の種類のサーバーからログ ファイルやデータ ファイルを収集したり、サーバーを一定期間にわたって監視したり、サーバーに関する特定の問題をトラブルシューティングしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="db136-244">You can use [SQLdiag Utility](../../tools/sqldiag-utility.md) to collect logs and data files from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and other types of servers, and use it to monitor your servers over time or troubleshoot specific problems with your servers.</span></span> <span data-ttu-id="db136-245">SQLdiag は、マイクロソフト カスタマー サポート サービスによる診断情報収集の高速化と簡素化を目的としたユーティリティです。</span><span class="sxs-lookup"><span data-stu-id="db136-245">SQLdiag is intended to expedite and simplify diagnostic information gathering for Microsoft Customer Support Services.</span></span>  
  
 <span data-ttu-id="db136-246">このユーティリティは、「 [SQLdiag ユーティリティ](../../tools/sqldiag-utility.md)」で指定されている構文を使用して、Server Core の管理者のコマンド プロンプトで起動できます。</span><span class="sxs-lookup"><span data-stu-id="db136-246">You can launch the utility on the administrator command prompt on the Server Core, using the syntax specified in the topic: [SQLdiag Utility](../../tools/sqldiag-utility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db136-247">参照</span><span class="sxs-lookup"><span data-stu-id="db136-247">See Also</span></span>  
 <span data-ttu-id="db136-248">[Server Core に SQL Server 2014 をインストールする](install-sql-server-on-server-core.md) </span><span class="sxs-lookup"><span data-stu-id="db136-248">[Install SQL Server 2014 on Server Core](install-sql-server-on-server-core.md) </span></span>  
 [<span data-ttu-id="db136-249">インストール方法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="db136-249">Installation How-to Topics</span></span>](../../sql-server/install/installation-how-to-topics.md)  
