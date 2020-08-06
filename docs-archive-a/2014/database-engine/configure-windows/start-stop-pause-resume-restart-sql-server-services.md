---
title: データベースエンジン、SQL Server エージェント、または SQL Server Browser サービスを開始、停止、一時停止、再開、再起動する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Configuration Manager, start and stop services
- stopping SQL Server Agent
- parameters [SQL Server], startup options
- SQL Server, startup options
- Database Engine [SQL Server], starting and stopping services
- pausing SQL Server
- PowerShell [SQL Server], starting and stopping services
- single-user mode [SQL Server], starting in
- SQL Server Management Studio [SQL Server], starting or stopping services
- stopping SQL Server Browser service
- starting SQL Server Agent
- default instances [SQL Server], starting and stopping
- SQL Server Agent, starting and stopping
- command prompt [SQL Server], starting and stopping SQL Server services
- continuing SQL Server
- starting SQL Server Database Engine
- net stop commands [SQL Server]
- command prompt [SQL Server], SQL Browser service
- Configuration Manager, start and stop services
- resuming SQL Server
- startup options [SQL Server]
- named instances [SQL Server], starting and stopping
- net start commands [SQL Server]
- SQL Server, starting and stopping
- stopping SQL Server
- starting SQL Server Browser service
- SQL Server Database Engine setting startup options
- administering SQL Server, starting and stopping services
- Management Studio [SQL Server], starting or stopping services
ms.assetid: 32660a02-e5a1-411a-9e57-7066ca459df6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f4b102c8fd81923d7386c8e556896e715311a07e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738695"
---
# <a name="start-stop-pause-resume-restart-the-database-engine-sql-server-agent-or-sql-server-browser-service"></a><span data-ttu-id="38dae-102">データベース エンジン、SQL Server エージェント、SQL Server Browser サービスの開始、停止、一時停止、再開、および再起動</span><span class="sxs-lookup"><span data-stu-id="38dae-102">Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service</span></span>
  <span data-ttu-id="38dae-103">このトピックでは、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、コマンドプロンプトからの**Net**コマンド、、または PowerShell を使用して、、エージェント、または Browser サービスを開始、停止、一時停止、再開、または再起動する方法について説明し [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="38dae-103">This topic describes how to start, stop, pause, resume, or restart the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, or the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], **net** commands from a command prompt, [!INCLUDE[tsql](../../includes/tsql-md.md)], or PowerShell.</span></span>  
  
-   <span data-ttu-id="38dae-104">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="38dae-104">**Before you begin:**</span></span>  
  
    -   [<span data-ttu-id="38dae-105">これらのサービスの概要</span><span class="sxs-lookup"><span data-stu-id="38dae-105">What are these services?</span></span>](#Services)  
  
    -   [<span data-ttu-id="38dae-106">追加情報</span><span class="sxs-lookup"><span data-stu-id="38dae-106">Additional Information</span></span>](#MoreInformation)  
  
    -   [<span data-ttu-id="38dae-107">Security</span><span class="sxs-lookup"><span data-stu-id="38dae-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="38dae-108">**使用の手順:**</span><span class="sxs-lookup"><span data-stu-id="38dae-108">**Instructions using:**</span></span>  
  
    -   [<span data-ttu-id="38dae-109">SQL Server 構成マネージャー</span><span class="sxs-lookup"><span data-stu-id="38dae-109">SQL Server Configuration Manager</span></span>](#SSCMProcedure)  
  
    -   [<span data-ttu-id="38dae-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="38dae-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
    -   [<span data-ttu-id="38dae-111">コマンド プロンプト ウィンドウからの net コマンド</span><span class="sxs-lookup"><span data-stu-id="38dae-111">net Commands from a Command Prompt window</span></span>](#CommandPrompt)  
  
    -   [<span data-ttu-id="38dae-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="38dae-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
    -   [<span data-ttu-id="38dae-113">PowerShell</span><span class="sxs-lookup"><span data-stu-id="38dae-113">PowerShell</span></span>](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="38dae-114">はじめに</span><span class="sxs-lookup"><span data-stu-id="38dae-114">Before You Begin</span></span>  
  
###  <a name="what-is-the-ssdenoversion-service-the-ssnoversion-agent-service-and-the-ssnoversion-browser-service"></a><a name="Services"></a><span data-ttu-id="38dae-115">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] サービス、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービス、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスの概要</span><span class="sxs-lookup"><span data-stu-id="38dae-115">What is the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] service, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service, and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service?</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="38dae-116">コンポーネントは、Windows サービスとして実行される実行可能プログラムです。</span><span class="sxs-lookup"><span data-stu-id="38dae-116">components are executable programs that run as a Windows service.</span></span> <span data-ttu-id="38dae-117">Windows サービスとして実行されるプログラムは、コンピューター画面にアクティビティを表示することなく動作を続行できます。</span><span class="sxs-lookup"><span data-stu-id="38dae-117">Programs that run as a Windows service can continue to operate without displaying any activity on the computer screen.</span></span>  
  
 <span data-ttu-id="38dae-118">**[!INCLUDE[ssDE](../../includes/ssde-md.md)]処理**</span><span class="sxs-lookup"><span data-stu-id="38dae-118">**[!INCLUDE[ssDE](../../includes/ssde-md.md)] service**</span></span>  
 <span data-ttu-id="38dae-119">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]である実行可能プロセスです。</span><span class="sxs-lookup"><span data-stu-id="38dae-119">The executable process that is the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="38dae-120">[!INCLUDE[ssDE](../../includes/ssde-md.md)] は、既定のインスタンス (1 台のコンピューターにつき 1 つのみ) にすることも、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]の多数の名前付きインスタンスの 1 つにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="38dae-120">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] can be the default instance (limit one per computer), or can be one of many named instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="38dae-121">コンピューターにインストールされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを判別するには、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 構成マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="38dae-121">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to determine which instances of [!INCLUDE[ssDE](../../includes/ssde-md.md)] are installed on the computer.</span></span> <span data-ttu-id="38dae-122">既定のインスタンス (インストールした場合) は、 \*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER)\*\* として表示されます。</span><span class="sxs-lookup"><span data-stu-id="38dae-122">The default instance (if you install it) is listed as **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER)**.</span></span> <span data-ttu-id="38dae-123">名前付きインスタンス (インストールした場合) は、 \*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (<instance_name>)\*\* として表示されます。</span><span class="sxs-lookup"><span data-stu-id="38dae-123">Named instances (if you install them) are listed as **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (<instance_name>)**.</span></span> <span data-ttu-id="38dae-124">既定で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、Express は\*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SQLEXPRESS)\*\* としてインストールされます。</span><span class="sxs-lookup"><span data-stu-id="38dae-124">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express is installed as **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SQLEXPRESS)**.</span></span>  
  
 <span data-ttu-id="38dae-125">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントサービス**</span><span class="sxs-lookup"><span data-stu-id="38dae-125">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service**</span></span>  
 <span data-ttu-id="38dae-126">ジョブおよび警告と呼ばれる管理タスクをスケジュールに従って実行する Windows サービスです。</span><span class="sxs-lookup"><span data-stu-id="38dae-126">A Windows service that executes scheduled administrative tasks, which are called jobs and alerts.</span></span> <span data-ttu-id="38dae-127">詳しくは、「 [SQL Server Agent](../../ssms/agent/sql-server-agent.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="38dae-127">For more information, see [SQL Server Agent](../../ssms/agent/sql-server-agent.md).</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="38dae-128">エージェントは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="38dae-128">Agent is not available in every edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="38dae-129">の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ては、「 [SQL Server 2014 の各エディションがサポートする機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="38dae-129">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="38dae-130">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Browser サービス**</span><span class="sxs-lookup"><span data-stu-id="38dae-130">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service**</span></span>  
 <span data-ttu-id="38dae-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各種リソースに関する着信要求を受信し、コンピューターにインストールされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに関するクライアント情報を提供する Windows サービスです。</span><span class="sxs-lookup"><span data-stu-id="38dae-131">A Windows service that listens for incoming requests for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resources and provides clients information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances installed on the computer.</span></span> <span data-ttu-id="38dae-132">コンピューターにインストールされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのインスタンスに対して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスのインスタンスが 1 つ使用されます。</span><span class="sxs-lookup"><span data-stu-id="38dae-132">A single instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service is used for all instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installed on the computer.</span></span>  
  
###  <a name="additional-information"></a><a name="MoreInformation"></a><span data-ttu-id="38dae-133">追加情報</span><span class="sxs-lookup"><span data-stu-id="38dae-133">Additional Information</span></span>  
  
-   <span data-ttu-id="38dae-134">[!INCLUDE[ssDE](../../includes/ssde-md.md)] サービスを一時停止すると、新しいユーザーは [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続できなくなりますが、既に接続しているユーザーは接続が切断されるまで処理を続行できます。</span><span class="sxs-lookup"><span data-stu-id="38dae-134">Pausing the [!INCLUDE[ssDE](../../includes/ssde-md.md)] service prevents new users from connecting to the [!INCLUDE[ssDE](../../includes/ssde-md.md)], but users who are already connected can continue to work until their connections are broken.</span></span> <span data-ttu-id="38dae-135">ユーザーの処理の完了を待ってからサービスを停止する場合は、一時停止を使用してください。</span><span class="sxs-lookup"><span data-stu-id="38dae-135">Use pause when you want to wait for users to complete work before you stop the service.</span></span> <span data-ttu-id="38dae-136">これにより、ユーザーが実行中のトランザクションを完了できます。</span><span class="sxs-lookup"><span data-stu-id="38dae-136">This enables them to complete transactions that are in progress.</span></span> <span data-ttu-id="38dae-137">再開すると、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] が再び新しい接続を受け入れられるようになります。</span><span class="sxs-lookup"><span data-stu-id="38dae-137">Resume allows the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to accept new connections again.</span></span> <span data-ttu-id="38dae-138">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスを一時停止および再開することはできません。</span><span class="sxs-lookup"><span data-stu-id="38dae-138">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service cannot be paused or resumed.</span></span>  
  
-   <span data-ttu-id="38dae-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーおよび [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] では、次のアイコンを使用してサービスの現在の状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="38dae-139">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager and [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] display the current status of services by using the following icons.</span></span>  
  
     <span data-ttu-id="38dae-140">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Configuration Manager**</span><span class="sxs-lookup"><span data-stu-id="38dae-140">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager**</span></span>  
  
    -   <span data-ttu-id="38dae-141">サービス名の隣にあるアイコン上の緑色の矢印は、サービスが開始されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="38dae-141">A green arrow on the icon next to the service name indicates that the service is started.</span></span>  
  
    -   <span data-ttu-id="38dae-142">サービス名の隣にあるアイコン上の赤い四角形は、サービスが停止していることを示します。</span><span class="sxs-lookup"><span data-stu-id="38dae-142">A red square on the icon next to the service name indicates that the service is stopped.</span></span>  
  
    -   <span data-ttu-id="38dae-143">サービス名の隣にあるアイコン上の 2 本の青い縦線は、サービスが一時停止していることを示します。</span><span class="sxs-lookup"><span data-stu-id="38dae-143">Two vertical blue lines on the icon next to the service name indicates that the service is paused.</span></span>  
  
    -   <span data-ttu-id="38dae-144">[!INCLUDE[ssDE](../../includes/ssde-md.md)]を再起動すると、サービスが停止したことが赤い四角形によって示された後、サービスが正常に開始されたことが緑色の矢印によって示されます。</span><span class="sxs-lookup"><span data-stu-id="38dae-144">When restarting the [!INCLUDE[ssDE](../../includes/ssde-md.md)], a red square will indicate that the service stopped, and then a green arrow will indicate that he service started successfully.</span></span>  
  
     **[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
    -   <span data-ttu-id="38dae-145">サービス名の隣にある緑色の円形のアイコン上の白い矢印は、サービスが開始されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="38dae-145">A white arrow on a green circle icon next to the service name indicates that the service is started.</span></span>  
  
    -   <span data-ttu-id="38dae-146">サービス名の隣にある赤い円形のアイコン上の白い四角形は、サービスが停止していることを示します。</span><span class="sxs-lookup"><span data-stu-id="38dae-146">A white square on a red circle icon next to the service name indicates that the service is stopped.</span></span>  
  
    -   <span data-ttu-id="38dae-147">サービス名の隣にある青い円形のアイコン上の 2 本の白い縦線は、サービスが一時停止していることを示します。</span><span class="sxs-lookup"><span data-stu-id="38dae-147">Two vertical white lines on a blue circle icon next to the service name indicates that the service is paused.</span></span>  
  
-   <span data-ttu-id="38dae-148">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーまたは [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]の使用時は、実行できるオプションのみが利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="38dae-148">When using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], only options that are possible will be available.</span></span> <span data-ttu-id="38dae-149">たとえば、サービスが既に開始されている場合、 **[開始]** は利用できません。</span><span class="sxs-lookup"><span data-stu-id="38dae-149">For example, if the service is already started, **Start** will be unavailable.</span></span>  
  
-   <span data-ttu-id="38dae-150">クラスターで実行中の [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] サービスを管理するには、クラスター アドミニストレーターを使用するのが最適です。</span><span class="sxs-lookup"><span data-stu-id="38dae-150">When running on a cluster, the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] service is best managed by using Cluster Administrator.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="38dae-151">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="38dae-151">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="38dae-152">Permissions</span><span class="sxs-lookup"><span data-stu-id="38dae-152">Permissions</span></span>  
 <span data-ttu-id="38dae-153">サービスを開始、停止、一時停止、再開、または再起動できるのは、既定ではローカル管理者グループのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="38dae-153">By default, only members of the local administrators group can start, stop, pause, resume or restart a service.</span></span> <span data-ttu-id="38dae-154">管理者以外のユーザーがサービスを管理できるようにする方法については、「 [[HOWTO] Windows Server 2003 でサービスを管理する権利をユーザーに付与する](https://support.microsoft.com/kb/325349)」をご覧ください</span><span class="sxs-lookup"><span data-stu-id="38dae-154">To grant non-administrators the ability to manage services, see [How to grant users rights to manage services in Windows Server 2003](https://support.microsoft.com/kb/325349).</span></span> <span data-ttu-id="38dae-155">(Windows の他のバージョンでも処理は同じです)。</span><span class="sxs-lookup"><span data-stu-id="38dae-155">(The process is similar on other versions of Windows.)</span></span>  
  
 <span data-ttu-id="38dae-156">コマンドを使用してを停止するには、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] `SHUTDOWN` **sysadmin**または**serveradmin**固定サーバーロールのメンバーシップが必要です。これは譲渡できません。</span><span class="sxs-lookup"><span data-stu-id="38dae-156">Stopping the [!INCLUDE[ssDE](../../includes/ssde-md.md)] by using the [!INCLUDE[tsql](../../includes/tsql-md.md)]`SHUTDOWN` command requires membership in the **sysadmin** or **serveradmin** fixed server roles, and is not transferable.</span></span>  
  
##  <a name="using-ssnoversion-configuration-manager"></a><a name="SSCMProcedure"></a><span data-ttu-id="38dae-157">Configuration Manager の使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38dae-157">Using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager</span></span>  
  
#### <a name="to-start-stop-pause-resume-or-restart-the-an-instance-of-the-ssdenoversion"></a><span data-ttu-id="38dae-158">インスタンスを開始、停止、一時停止、再開、または再起動するには [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38dae-158">To start, stop, pause, resume, or restart the an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]</span></span>  
  
1.  <span data-ttu-id="38dae-159">**[スタート]** メニューで、 **[すべてのプログラム]** 、[ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]]、 **[構成ツール]** の順にポイントして、 **[SQL Server 構成マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="38dae-159">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="38dae-160">**[ユーザー アカウント制御]** ダイアログ ボックスが表示されたら、 **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="38dae-160">If the **User Account Control** dialog box appears, click **Yes**.</span></span>  
  
3.  <span data-ttu-id="38dae-161">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーの左側のペインで、 **[SQL Server のサービス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="38dae-161">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the left pane, click **SQL Server Services**.</span></span>  
  
4.  <span data-ttu-id="38dae-162">結果ペインで **[SQL Server (MSSQLServer)]** または名前付きインスタンスを右クリックし、 **[開始]** 、 **[停止]** 、 **[一時停止]** 、 **[再開]** 、または **[再起動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="38dae-162">In the results pane, right-click **SQL Server (MSSQLServer)** or a named instance, and then click **Start**, **Stop**, **Pause**, **Resume**, or **Restart**.</span></span>  
  
5.  <span data-ttu-id="38dae-163">**[OK]** をクリックし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを閉じます。</span><span class="sxs-lookup"><span data-stu-id="38dae-163">Click **OK** to close [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="38dae-164">スタートアップ オプションを指定して [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスを開始する方法については、「[サーバーのスタートアップ オプションの構成 &#40;SQL Server 構成マネージャー&#41;](scm-services-configure-server-startup-options.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="38dae-164">To start an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] with startup options, see [Configure Server Startup Options &#40;SQL Server Configuration Manager&#41;](scm-services-configure-server-startup-options.md).</span></span>  
  
#### <a name="to-start-stop-pause-resume-or-restart-the-ssnoversion-browser-or-an-instance-of-the-ssnoversion-agent"></a><span data-ttu-id="38dae-165">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのインスタンスを開始、停止、一時停止、再開、または再起動するには</span><span class="sxs-lookup"><span data-stu-id="38dae-165">To start, stop, pause, resume, or restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser or an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent</span></span>  
  
1.  <span data-ttu-id="38dae-166">**[スタート]** メニューで、 **[すべてのプログラム]** 、[ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]]、 **[構成ツール]** の順にポイントして、 **[SQL Server 構成マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="38dae-166">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="38dae-167">**[ユーザー アカウント制御]** ダイアログ ボックスが表示されたら、 **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="38dae-167">If the **User Account Control** dialog box appears, click **Yes**.</span></span>  
  
3.  <span data-ttu-id="38dae-168">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーの左側のペインで、 **[SQL Server のサービス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="38dae-168">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the left pane, click **SQL Server Services**.</span></span>  
  
4.  <span data-ttu-id="38dae-169">結果ウィンドウで、名前付きインスタンスの [ \*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser**] または [ \*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント (MSSQLServer)** ] または [ \*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント] (<instance_name>)\*\* を右クリックし、[**開始**]、[**停止**]、[**一時停止**]、[**再開**]、または [**再起動**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="38dae-169">In the results pane, right-click **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser**, or **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent (MSSQLServer)** or **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent (<instance_name>)** for a named instance, and then click **Start**, **Stop**, **Pause**, **Resume**, or **Restart**.</span></span>  
  
5.  <span data-ttu-id="38dae-170">**[OK]** をクリックし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを閉じます。</span><span class="sxs-lookup"><span data-stu-id="38dae-170">Click **OK** to close [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="38dae-171">エージェントは一時停止できません。</span><span class="sxs-lookup"><span data-stu-id="38dae-171">Agent cannot be paused.</span></span>  
  
##  <a name="using-ssnoversion-management-studio"></a><a name="SSMSProcedure"></a><span data-ttu-id="38dae-172">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="38dae-172">Using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio</span></span>  
  
#### <a name="to-start-stop-pause-resume-or-restart-the-an-instance-of-the-ssdenoversion"></a><span data-ttu-id="38dae-173">インスタンスを開始、停止、一時停止、再開、または再起動するには [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38dae-173">To start, stop, pause, resume, or restart the an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]</span></span>  
  
1.  <span data-ttu-id="38dae-174">オブジェクト エクスプローラーで、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続し、開始する [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスを右クリックし、 **[開始]**、 **[停止]**、 **[一時停止]**、 **[再開]**、または **[再起動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="38dae-174">In Object Explorer, connect to the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], right-click the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] you want to start, and then click **Start**, **Stop**, **Pause**, **Resume**, or **Restart**.</span></span>  
  
     <span data-ttu-id="38dae-175">または、[登録済みサーバー] で、開始する [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスを右クリックし、 **[サービス コントロール]** をポイントし、 **[開始]**、 **[停止]**、 **[一時停止]**、 **[再開]**、または **[再起動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="38dae-175">Or, in Registered Servers, right-click the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] you want to start, point to **Service Control**, and then click **Start**, **Stop**, **Pause**, **Resume**, or **Restart**.</span></span>  
  
2.  <span data-ttu-id="38dae-176">**[ユーザー アカウント制御]** ダイアログ ボックスが表示されたら、 **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="38dae-176">If the **User Account Control** dialog box appears, click **Yes**.</span></span>  
  
3.  <span data-ttu-id="38dae-177">アクションを実行するかどうかを確認するメッセージが表示されたら、 **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="38dae-177">When prompted if you want to perform the action, click **Yes**.</span></span>  
  
#### <a name="to-start-stop-or-restart-the-an-instance-of-the-ssnoversion-agent"></a><span data-ttu-id="38dae-178">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのインスタンスを開始、停止、または再起動するには</span><span class="sxs-lookup"><span data-stu-id="38dae-178">To start, stop, or restart the an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent</span></span>  
  
1.  <span data-ttu-id="38dae-179">オブジェクトエクスプローラーで、のインスタンスに接続し [!INCLUDE[ssDE](../../includes/ssde-md.md)] 、[ \*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント**] を右クリックして、[**開始**]、[**停止**]、または [**再起動\*\*] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="38dae-179">In Object Explorer, connect to the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], right-click **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent**, and then click **Start**, **Stop**, or **Restart**.</span></span>  
  
2.  <span data-ttu-id="38dae-180">**[ユーザー アカウント制御]** ダイアログ ボックスが表示されたら、 **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="38dae-180">If the **User Account Control** dialog box appears, click **Yes**.</span></span>  
  
3.  <span data-ttu-id="38dae-181">アクションを実行するかどうかを確認するメッセージが表示されたら、 **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="38dae-181">When prompted if you want to perform the action, click **Yes**.</span></span>  
  
##  <a name="from-the-command-prompt-window-using-net-commands"></a><a name="CommandPrompt"></a><span data-ttu-id="38dae-182">コマンドプロンプトウィンドウから net コマンドを使用する</span><span class="sxs-lookup"><span data-stu-id="38dae-182">From the Command Prompt Window using net Commands</span></span>  
 <span data-ttu-id="38dae-183">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows の **net** コマンドを使用して、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを開始、停止、または一時停止できます。</span><span class="sxs-lookup"><span data-stu-id="38dae-183">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services can be started, stopped, or paused by using [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows **net** commands.</span></span>  
  
###  <a name="to-start-the-default-instance-of-the-ssde"></a><a name="dbDefault"></a><span data-ttu-id="38dae-184">の既定のインスタンスを開始するには[!INCLUDE[ssDE](../../includes/ssde-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38dae-184">To start the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)]</span></span>  
  
-   <span data-ttu-id="38dae-185">コマンド プロンプトで、次のいずれかのコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="38dae-185">From a command prompt, enter one of the following commands:</span></span>  
  
     <span data-ttu-id="38dae-186">**net start "SQL Server (MSSQLSERVER)"**</span><span class="sxs-lookup"><span data-stu-id="38dae-186">**net start "SQL Server (MSSQLSERVER)"**</span></span>  
  
     <span data-ttu-id="38dae-187">または</span><span class="sxs-lookup"><span data-stu-id="38dae-187">-or-</span></span>  
  
     <span data-ttu-id="38dae-188">**net start MSSQLSERVER**</span><span class="sxs-lookup"><span data-stu-id="38dae-188">**net start MSSQLSERVER**</span></span>  
  
###  <a name="to-start-a-named-instance-of-the-ssde"></a><a name="dbNamed"></a> <span data-ttu-id="38dae-189">名前付きインスタンスを開始するには [!INCLUDE[ssDE](../../includes/ssde-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38dae-189">To start a named instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)]</span></span>  
  
-   <span data-ttu-id="38dae-190">コマンド プロンプトで、次のいずれかのコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="38dae-190">From a command prompt, enter one of the following commands.</span></span> <span data-ttu-id="38dae-191">*\<instancename>* は、管理するインスタンスの名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="38dae-191">Replace *\<instancename>* with the name of the instance you want to manage.</span></span>  
  
     <span data-ttu-id="38dae-192">**net start "SQL Server (** *instancename* **)"**</span><span class="sxs-lookup"><span data-stu-id="38dae-192">**net start "SQL Server (** *instancename* **)"**</span></span>  
  
     <span data-ttu-id="38dae-193">または</span><span class="sxs-lookup"><span data-stu-id="38dae-193">-or-</span></span>  
  
     <span data-ttu-id="38dae-194">**net start MSSQL$** *instancename*</span><span class="sxs-lookup"><span data-stu-id="38dae-194">**net start MSSQL$** *instancename*</span></span>  
  
###  <a name="to-start-the-ssde-with-startup-options"></a><a name="dbStartup"></a> <span data-ttu-id="38dae-195">スタートアップ オプションを指定して [!INCLUDE[ssDE](../../includes/ssde-md.md)] を開始するには</span><span class="sxs-lookup"><span data-stu-id="38dae-195">To start the [!INCLUDE[ssDE](../../includes/ssde-md.md)] with startup options</span></span>  
  
-   <span data-ttu-id="38dae-196">**net start "SQL Server (MSSQLSERVER)"** ステートメントの末尾に、スタートアップ オプションをスペースで区切って追加します。</span><span class="sxs-lookup"><span data-stu-id="38dae-196">Add startup options to the end of the **net start "SQL Server (MSSQLSERVER)"** statement, separated by a space.</span></span> <span data-ttu-id="38dae-197">**net start**を使用して起動するときは、スタートアップ オプションでハイフン (-) の代わりにスラッシュ (/) を使用します。</span><span class="sxs-lookup"><span data-stu-id="38dae-197">When started using **net start**, startup options use a slash (/) instead of a hyphen (-).</span></span>  
  
     <span data-ttu-id="38dae-198">**net start "SQL Server (MSSQLSERVER)" /f /m**</span><span class="sxs-lookup"><span data-stu-id="38dae-198">**net start "SQL Server (MSSQLSERVER)" /f /m**</span></span>  
  
     <span data-ttu-id="38dae-199">または</span><span class="sxs-lookup"><span data-stu-id="38dae-199">-or-</span></span>  
  
     <span data-ttu-id="38dae-200">**net start MSSQLSERVER /f /m**</span><span class="sxs-lookup"><span data-stu-id="38dae-200">**net start MSSQLSERVER /f /m**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="38dae-201">スタートアップ オプションの詳細については、「 [データベース エンジン サービスのスタートアップ オプション](database-engine-service-startup-options.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="38dae-201">For more information about startup options, see [Database Engine Service Startup Options](database-engine-service-startup-options.md).</span></span>  
  
###  <a name="to-start-the-ssnoversion-agent-on-the-default-instance-of-ssnoversion"></a><a name="agDefault"></a> <span data-ttu-id="38dae-202">スタートアップ オプションを指定して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定のインスタンスの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38dae-202">To start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent on the default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="38dae-203">コマンド プロンプトで、次のいずれかのコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="38dae-203">From a command prompt, enter one of the following commands:</span></span>  
  
     <span data-ttu-id="38dae-204">**net start "SQL Server Agent (MSSQLSERVER)"**</span><span class="sxs-lookup"><span data-stu-id="38dae-204">**net start "SQL Server Agent (MSSQLSERVER)"**</span></span>  
  
     <span data-ttu-id="38dae-205">または</span><span class="sxs-lookup"><span data-stu-id="38dae-205">-or-</span></span>  
  
     <span data-ttu-id="38dae-206">**net start SQLSERVERAGENT**</span><span class="sxs-lookup"><span data-stu-id="38dae-206">**net start SQLSERVERAGENT**</span></span>  
  
###  <a name="to-start-the-ssnoversion-agent-on-a-named-instance-of-ssnoversion"></a><a name="agNamed"></a> <span data-ttu-id="38dae-207">スタートアップ オプションを指定して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の名前付きインスタンスの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38dae-207">To start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent on a named instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="38dae-208">コマンド プロンプトで、次のいずれかのコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="38dae-208">From a command prompt, enter one of the following commands.</span></span> <span data-ttu-id="38dae-209">*instancename* は、管理するインスタンスの名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="38dae-209">Replace *instancename* with the name of the instance you want to manage.</span></span>  
  
     <span data-ttu-id="38dae-210">**net start "SQL Server Agent(** *instancename* **)"**</span><span class="sxs-lookup"><span data-stu-id="38dae-210">**net start "SQL Server Agent(** *instancename* **)"**</span></span>  
  
     <span data-ttu-id="38dae-211">または</span><span class="sxs-lookup"><span data-stu-id="38dae-211">-or-</span></span>  
  
     <span data-ttu-id="38dae-212">**net start SQLAgent$** *instancename*</span><span class="sxs-lookup"><span data-stu-id="38dae-212">**net start SQLAgent$** *instancename*</span></span>  
  
 <span data-ttu-id="38dae-213">トラブルシューティングのために [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを詳細モードで実行する方法については、「 [sqlagent90 アプリケーション](../../tools/sqlagent90-application.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="38dae-213">For information about how to run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in verbose mode for troubleshooting, see [sqlagent90 Application](../../tools/sqlagent90-application.md).</span></span>  
  
###  <a name="to-start-the-ssnoversion-browser"></a><a name="Browser"></a><span data-ttu-id="38dae-214">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser を開始するには</span><span class="sxs-lookup"><span data-stu-id="38dae-214">To start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser</span></span>  
  
-   <span data-ttu-id="38dae-215">コマンド プロンプトで、次のいずれかのコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="38dae-215">From a command prompt, enter one of the following commands:</span></span>  
  
     <span data-ttu-id="38dae-216">**net start "SQL Server Browser"**</span><span class="sxs-lookup"><span data-stu-id="38dae-216">**net start "SQL Server Browser"**</span></span>  
  
     <span data-ttu-id="38dae-217">または</span><span class="sxs-lookup"><span data-stu-id="38dae-217">-or-</span></span>  
  
     <span data-ttu-id="38dae-218">**net start SQLBrowser**</span><span class="sxs-lookup"><span data-stu-id="38dae-218">**net start SQLBrowser**</span></span>  
  
###  <a name="to-pause-or-stop-services-from-the-command-prompt-window"></a><a name="pauseStop"></a> <span data-ttu-id="38dae-219">コマンド プロンプト ウィンドウからサービスを一時停止または停止するには</span><span class="sxs-lookup"><span data-stu-id="38dae-219">To pause or stop services from the Command Prompt window</span></span>  
  
-   <span data-ttu-id="38dae-220">サービスを一時停止または停止するには、次のようにコマンドを変更します。</span><span class="sxs-lookup"><span data-stu-id="38dae-220">To pause or stop services modify the commands in the following ways.</span></span>  
  
    -   <span data-ttu-id="38dae-221">サービスを一時停止するには、 **net start** を **net pause**に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="38dae-221">To pause a service, replace **net start** with **net pause**.</span></span>  
  
    -   <span data-ttu-id="38dae-222">サービスを停止するには、 **net start** を **net stop**に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="38dae-222">To stop a service, replace **net start** with use **net stop**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="38dae-223">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="38dae-223">Using Transact-SQL</span></span>  
 <span data-ttu-id="38dae-224">`SHUTDOWN` ステートメントを使用して、[!INCLUDE[ssDE](../../includes/ssde-md.md)]を停止できます。</span><span class="sxs-lookup"><span data-stu-id="38dae-224">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] can be stopped by using the `SHUTDOWN` statement.</span></span>  
  
#### <a name="to-stop-the-ssde-using-tsql"></a><span data-ttu-id="38dae-225">[!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して [!INCLUDE[ssDE](../../includes/ssde-md.md)] を停止するには</span><span class="sxs-lookup"><span data-stu-id="38dae-225">To stop the [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[tsql](../../includes/tsql-md.md)]</span></span>  
  
-   <span data-ttu-id="38dae-226">現在実行中の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントおよびストアド プロシージャが終了するまで待機してから [!INCLUDE[ssDE](../../includes/ssde-md.md)]を停止するには、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="38dae-226">To wait for currently running [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and stored procedures to finish, and then stop the [!INCLUDE[ssDE](../../includes/ssde-md.md)], execute the following statement.</span></span>  
  
    ```sql  
    SHUTDOWN;   
    ```  
  
-   <span data-ttu-id="38dae-227">[!INCLUDE[ssDE](../../includes/ssde-md.md)]を直ちに停止するには、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="38dae-227">To stop the [!INCLUDE[ssDE](../../includes/ssde-md.md)] immediately, execute the following statement.</span></span>  
  
    ```sql  
    SHUTDOWN WITH NOWAIT;   
    ```  
  
 <span data-ttu-id="38dae-228">ステートメントの詳細については `SHUTDOWN` 、「 [transact-sql&#41;のシャットダウン &#40;](/sql/t-sql/language-elements/shutdown-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="38dae-228">For more information about the `SHUTDOWN` statement, see [SHUTDOWN &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/shutdown-transact-sql).</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a><span data-ttu-id="38dae-229">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="38dae-229">Using PowerShell</span></span>  
  
#### <a name="to-start-and-stop-ssde-services"></a><span data-ttu-id="38dae-230">[!INCLUDE[ssDE](../../includes/ssde-md.md)] サービスを開始および停止するには</span><span class="sxs-lookup"><span data-stu-id="38dae-230">To start and stop [!INCLUDE[ssDE](../../includes/ssde-md.md)] services</span></span>  
  
1.  <span data-ttu-id="38dae-231">コマンド プロンプト ウィンドウで、次のコマンドを実行して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Power Shell を開始します。</span><span class="sxs-lookup"><span data-stu-id="38dae-231">In a Command Prompt window, start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell by executing the following command.</span></span>  
  
    ```ms-dos  
    sqlps  
    ```  
  
2.  <span data-ttu-id="38dae-232">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Power Shell コマンド プロンプトで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="38dae-232">At a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell command prompt, by executing the following command.</span></span> <span data-ttu-id="38dae-233">`computername` は自分のコンピューター名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="38dae-233">Replace `computername` with the name of your computer.</span></span>  
  
    ```powershell  
    # Get a reference to the ManagedComputer class.  
    CD SQLSERVER:\SQL\computername  
    $Wmi = (Get-Item .).ManagedComputer
    ```  
  
3.  <span data-ttu-id="38dae-234">停止または開始するサービスを指定します。</span><span class="sxs-lookup"><span data-stu-id="38dae-234">Identify the service that you want to stop or start.</span></span> <span data-ttu-id="38dae-235">以下のいずれかの行を選択してください。</span><span class="sxs-lookup"><span data-stu-id="38dae-235">Pick one of the following lines.</span></span> <span data-ttu-id="38dae-236">`instancename` は名前付きインスタンスの名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="38dae-236">Replace `instancename` with the name of the named instance.</span></span>  
  
    -   <span data-ttu-id="38dae-237">[!INCLUDE[ssDE](../../includes/ssde-md.md)]の既定のインスタンスへの参照を取得する場合</span><span class="sxs-lookup"><span data-stu-id="38dae-237">To get a reference to the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['MSSQLSERVER']  
        ```  
  
    -   <span data-ttu-id="38dae-238">[!INCLUDE[ssDE](../../includes/ssde-md.md)]の名前付きインスタンスへの参照を取得する場合</span><span class="sxs-lookup"><span data-stu-id="38dae-238">To get a reference to a named instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['MSSQL$instancename']  
        ```  
  
    -   <span data-ttu-id="38dae-239">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定のインスタンスの [!INCLUDE[ssDE](../../includes/ssde-md.md)]エージェント サービスへの参照を取得する場合</span><span class="sxs-lookup"><span data-stu-id="38dae-239">To get a reference to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service on the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['SQLSERVERAGENT']  
        ```  
  
    -   <span data-ttu-id="38dae-240">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の名前付きインスタンスの [!INCLUDE[ssDE](../../includes/ssde-md.md)]エージェント サービスへの参照を取得する場合</span><span class="sxs-lookup"><span data-stu-id="38dae-240">To get a reference to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service on a named instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['SQLAGENT$instancename']  
        ```  
  
    -   <span data-ttu-id="38dae-241">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスへの参照を取得する場合</span><span class="sxs-lookup"><span data-stu-id="38dae-241">To get a reference to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service.</span></span>  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['SQLBROWSER']  
        ```  
  
4.  <span data-ttu-id="38dae-242">例を実行して、選択したサービスを開始し、停止します。</span><span class="sxs-lookup"><span data-stu-id="38dae-242">Complete the example to start and then stop the selected service.</span></span>  
  
    ```powershell  
    # Display the state of the service.  
    $DfltInstance  
    # Start the service.  
    $DfltInstance.Start();  
    # Wait until the service has time to start.  
    # Refresh the cache.  
    $DfltInstance.Refresh();   
    # Display the state of the service.  
    $DfltInstance  
    # Stop the service.  
    $DfltInstance.Stop();  
    # Wait until the service has time to stop.  
    # Refresh the cache.  
    $DfltInstance.Refresh();   
    # Display the state of the service.  
    $DfltInstance  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="38dae-243">参照</span><span class="sxs-lookup"><span data-stu-id="38dae-243">See Also</span></span>  
 <span data-ttu-id="38dae-244">[最小構成で SQL Server を開始する](start-sql-server-with-minimal-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="38dae-244">[Start SQL Server with Minimal Configuration](start-sql-server-with-minimal-configuration.md) </span></span>  
 [<span data-ttu-id="38dae-245">SQL Server 2014 の各エディションがサポートする機能</span><span class="sxs-lookup"><span data-stu-id="38dae-245">Features Supported by the Editions of SQL Server 2014</span></span>](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
