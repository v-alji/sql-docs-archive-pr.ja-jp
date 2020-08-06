---
title: 分散再生の要件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 6fffee7d-891f-4d9d-b2c3-dd19855a1c2c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 66be93534756360e722fcccaf405815e14ffa7ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640287"
---
# <a name="distributed-replay-requirements"></a><span data-ttu-id="fd9c5-102">Distributed Replay Requirements</span><span class="sxs-lookup"><span data-stu-id="fd9c5-102">Distributed Replay Requirements</span></span>
  <span data-ttu-id="fd9c5-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分散再生機能を使用する前に、このトピックで説明する製品の要件を検討してください。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-103">Before using the [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay feature, consider the product requirements that are outlined in this topic.</span></span>  
  
## <a name="input-trace-requirements"></a><span data-ttu-id="fd9c5-104">入力トレースの要件</span><span class="sxs-lookup"><span data-stu-id="fd9c5-104">Input Trace Requirements</span></span>  
 <span data-ttu-id="fd9c5-105">トレース データを正常に再生するには、バージョンと形式の要件を満たし、必要なイベントと列が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-105">To successfully replay trace data, it must meet the requirements for version and format, and contain the required events and columns.</span></span>  
  
### <a name="input-trace-versions"></a><span data-ttu-id="fd9c5-106">入力トレースのバージョン</span><span class="sxs-lookup"><span data-stu-id="fd9c5-106">Input Trace Versions</span></span>  
 <span data-ttu-id="fd9c5-107">分散再生は、次のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で収集される入力トレース データをサポートします。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-107">Distributed Replay supports input trace data that is collected on the following versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]  
  
### <a name="input-trace-formats"></a><span data-ttu-id="fd9c5-108">入力トレースの形式</span><span class="sxs-lookup"><span data-stu-id="fd9c5-108">Input Trace Formats</span></span>  
 <span data-ttu-id="fd9c5-109">次のいずれかの形式の入力トレース データを使用できます。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-109">The input trace data can be in any of the following formats:</span></span>  
  
-   <span data-ttu-id="fd9c5-110">`.trc` 拡張子を持つ 1 つのトレース ファイル。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-110">A single trace file that has the `.trc` extension.</span></span>  
  
-   <span data-ttu-id="fd9c5-111">ファイル ロールオーバー名前付け規則に準拠したロールオーバー トレース ファイルのセット。例: `<TraceFile>.trc`、`<TraceFile>_1.trc`、`<TraceFile>_2.trc`、`<TraceFile>_3.trc`、... `<TraceFile>_n.trc`。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-111">A set of rollover trace files that follow the file rollover naming convention, for example: `<TraceFile>.trc`, `<TraceFile>_1.trc`, `<TraceFile>_2.trc`, `<TraceFile>_3.trc`, ... `<TraceFile>_n.trc`.</span></span>  
  
### <a name="input-trace-events-and-columns"></a><span data-ttu-id="fd9c5-112">入力トレースのイベントと列</span><span class="sxs-lookup"><span data-stu-id="fd9c5-112">Input Trace Events and Columns</span></span>  
 <span data-ttu-id="fd9c5-113">入力トレース データには、分散再生で再生される特定のイベントと列を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-113">The input trace data must contain specific events and columns to be replayed by Distributed Replay.</span></span> <span data-ttu-id="fd9c5-114">**内の** TSQL_Replay [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] テンプレートには、すべての必要なイベントおよび列と、追加情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-114">The **TSQL_Replay** template in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] contains all of the required events and columns, in addition to extra information.</span></span> <span data-ttu-id="fd9c5-115">このテンプレートの詳細については、「 [再生を実行するための必要条件](../sql-server-profiler/replay-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-115">For more information about that template, see [Replay Requirements](../sql-server-profiler/replay-requirements.md).</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="fd9c5-116">**TSQL_Replay** テンプレートを使用して入力トレース データをキャプチャしない場合、または入力トレースの要件が満たされない場合、予期しない再生結果となる場合があります。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-116">If you do not use the **TSQL_Replay** template to capture the input trace data, or if the input trace requirements are not satisfied, you may receive unexpected replay results.</span></span>  
  
 <span data-ttu-id="fd9c5-117">また、次のイベントが含まれる場合に限り、カスタム トレース テンプレートを作成し、それを使用して分散再生でイベントを再生することもできます。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-117">You can also create a custom trace template and use it to replay events with Distributed Replay, as long as it contains the following events:</span></span>  
  
-   <span data-ttu-id="fd9c5-118">Audit Login</span><span class="sxs-lookup"><span data-stu-id="fd9c5-118">Audit Login</span></span>  
  
-   <span data-ttu-id="fd9c5-119">Audit Logout</span><span class="sxs-lookup"><span data-stu-id="fd9c5-119">Audit Logout</span></span>  
  
-   <span data-ttu-id="fd9c5-120">ExistingConnection</span><span class="sxs-lookup"><span data-stu-id="fd9c5-120">ExistingConnection</span></span>  
  
-   <span data-ttu-id="fd9c5-121">RPC Output Parameter</span><span class="sxs-lookup"><span data-stu-id="fd9c5-121">RPC Output Parameter</span></span>  
  
-   <span data-ttu-id="fd9c5-122">RPC:Completed</span><span class="sxs-lookup"><span data-stu-id="fd9c5-122">RPC:Completed</span></span>  
  
-   <span data-ttu-id="fd9c5-123">RPC:Starting</span><span class="sxs-lookup"><span data-stu-id="fd9c5-123">RPC:Starting</span></span>  
  
-   <span data-ttu-id="fd9c5-124">SQL:BatchCompleted</span><span class="sxs-lookup"><span data-stu-id="fd9c5-124">SQL:BatchCompleted</span></span>  
  
-   <span data-ttu-id="fd9c5-125">SQL:BatchStarting</span><span class="sxs-lookup"><span data-stu-id="fd9c5-125">SQL:BatchStarting</span></span>  
  
 <span data-ttu-id="fd9c5-126">サーバー側カーソルを再生している場合は、次のイベントも必要です。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-126">If you are replaying server-side cursors, the following events are also required:</span></span>  
  
-   <span data-ttu-id="fd9c5-127">CursorClose</span><span class="sxs-lookup"><span data-stu-id="fd9c5-127">CursorClose</span></span>  
  
-   <span data-ttu-id="fd9c5-128">CursorExecute</span><span class="sxs-lookup"><span data-stu-id="fd9c5-128">CursorExecute</span></span>  
  
-   <span data-ttu-id="fd9c5-129">CursorOpen</span><span class="sxs-lookup"><span data-stu-id="fd9c5-129">CursorOpen</span></span>  
  
-   <span data-ttu-id="fd9c5-130">CursorPrepare</span><span class="sxs-lookup"><span data-stu-id="fd9c5-130">CursorPrepare</span></span>  
  
-   <span data-ttu-id="fd9c5-131">CursorUnprepare</span><span class="sxs-lookup"><span data-stu-id="fd9c5-131">CursorUnprepare</span></span>  
  
 <span data-ttu-id="fd9c5-132">サーバー側の準備された SQL ステートメントを再生している場合は、次のイベントも必要です。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-132">If you are replaying server-side prepared SQL statements, the following events are also required:</span></span>  
  
-   <span data-ttu-id="fd9c5-133">Exec Prepared SQL</span><span class="sxs-lookup"><span data-stu-id="fd9c5-133">Exec Prepared SQL</span></span>  
  
-   <span data-ttu-id="fd9c5-134">Prepare SQL</span><span class="sxs-lookup"><span data-stu-id="fd9c5-134">Prepare SQL</span></span>  
  
 <span data-ttu-id="fd9c5-135">すべての入力トレース データに、次の列を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-135">All input trace data must contain the following columns:</span></span>  
  
-   <span data-ttu-id="fd9c5-136">Event Class</span><span class="sxs-lookup"><span data-stu-id="fd9c5-136">Event Class</span></span>  
  
-   <span data-ttu-id="fd9c5-137">EventSequence</span><span class="sxs-lookup"><span data-stu-id="fd9c5-137">EventSequence</span></span>  
  
-   <span data-ttu-id="fd9c5-138">TextData</span><span class="sxs-lookup"><span data-stu-id="fd9c5-138">TextData</span></span>  
  
-   <span data-ttu-id="fd9c5-139">アプリケーション名</span><span class="sxs-lookup"><span data-stu-id="fd9c5-139">Application Name</span></span>  
  
-   <span data-ttu-id="fd9c5-140">LoginName</span><span class="sxs-lookup"><span data-stu-id="fd9c5-140">LoginName</span></span>  
  
-   <span data-ttu-id="fd9c5-141">DatabaseName</span><span class="sxs-lookup"><span data-stu-id="fd9c5-141">DatabaseName</span></span>  
  
-   <span data-ttu-id="fd9c5-142">データベース ID</span><span class="sxs-lookup"><span data-stu-id="fd9c5-142">Database ID</span></span>  
  
-   <span data-ttu-id="fd9c5-143">HostName</span><span class="sxs-lookup"><span data-stu-id="fd9c5-143">HostName</span></span>  
  
-   <span data-ttu-id="fd9c5-144">Binary Data</span><span class="sxs-lookup"><span data-stu-id="fd9c5-144">Binary Data</span></span>  
  
-   <span data-ttu-id="fd9c5-145">SPID</span><span class="sxs-lookup"><span data-stu-id="fd9c5-145">SPID</span></span>  
  
-   <span data-ttu-id="fd9c5-146">開始時刻</span><span class="sxs-lookup"><span data-stu-id="fd9c5-146">Start Time</span></span>  
  
-   <span data-ttu-id="fd9c5-147">EndTime</span><span class="sxs-lookup"><span data-stu-id="fd9c5-147">EndTime</span></span>  
  
-   <span data-ttu-id="fd9c5-148">IsSystem</span><span class="sxs-lookup"><span data-stu-id="fd9c5-148">IsSystem</span></span>  
  
## <a name="supported-input-trace-and-target-server-combinations"></a><span data-ttu-id="fd9c5-149">サポートされている入力トレースとターゲット サーバーの組み合わせ</span><span class="sxs-lookup"><span data-stu-id="fd9c5-149">Supported Input Trace and Target Server Combinations</span></span>  
 <span data-ttu-id="fd9c5-150">次の表に、サポートされているトレース データのバージョンと、データを再生可能なサポートされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンを示します。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-150">The following table lists the supported versions of trace data, and for each, the supported versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that data can be replayed against.</span></span>  
  
|<span data-ttu-id="fd9c5-151">入力トレース データのバージョン</span><span class="sxs-lookup"><span data-stu-id="fd9c5-151">Version of Input Trace Data</span></span>|<span data-ttu-id="fd9c5-152">ターゲット サーバー インスタンスでサポートされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョン</span><span class="sxs-lookup"><span data-stu-id="fd9c5-152">Supported Versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for the Target Server Instance</span></span>|  
|---------------------------------|------------------------------------------------------------------------------------|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]<span data-ttu-id="fd9c5-153">, [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd9c5-153">, [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]<span data-ttu-id="fd9c5-154">, [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd9c5-154">, [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="fd9c5-155">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd9c5-155">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]<span data-ttu-id="fd9c5-156">, [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd9c5-156">, [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
  
## <a name="operating-system-requirements"></a><span data-ttu-id="fd9c5-157">オペレーティング システムの要件</span><span class="sxs-lookup"><span data-stu-id="fd9c5-157">Operating System Requirements</span></span>  
 <span data-ttu-id="fd9c5-158">管理ツールおよびコントローラーとクライアント サービスを実行するためにサポートされるオペレーティング システムは、使用している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスと同じです。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-158">Supported operating systems for running the administration tool and the controller and client services is the same as your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="fd9c5-159">インスタンスでサポートされているオペレーティングシステムの詳細については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、「 [SQL Server 2014 をインストールするためのハードウェアおよびソフトウェアの要件](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-159">For more information about which operating systems are supported for your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, see [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).</span></span>  
  
 <span data-ttu-id="fd9c5-160">分散再生機能は、x86 ベースおよび x64 ベースの両方のオペレーティング システムでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-160">Distributed Replay features are supported on both x86-based and x64-based operating systems.</span></span> <span data-ttu-id="fd9c5-161">x64 ベース オペレーティング システムでは、Windows on Windows (WOW) モードのみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-161">For x64-based operating systems, only Windows on Windows (WOW) mode is supported.</span></span>  
  
## <a name="installation-limitations"></a><span data-ttu-id="fd9c5-162">インストールの制限</span><span class="sxs-lookup"><span data-stu-id="fd9c5-162">Installation Limitations</span></span>  
 <span data-ttu-id="fd9c5-163">コンピューター 1 台につき、分散再生機能がインストールされている 1 つのインスタンスのみを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-163">Any one computer can only have a single instance of each Distributed Replay feature installed.</span></span> <span data-ttu-id="fd9c5-164">次の表に、1 つの分散再生環境における各機能のインストール数の上限を示します。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-164">The following table lists how many installations of each feature are allowed in a single Distributed Replay environment.</span></span>  
  
|<span data-ttu-id="fd9c5-165">分散再生機能</span><span class="sxs-lookup"><span data-stu-id="fd9c5-165">Distributed Replay Feature</span></span>|<span data-ttu-id="fd9c5-166">再生環境ごとのインストール数の上限</span><span class="sxs-lookup"><span data-stu-id="fd9c5-166">Maximum Installations Per Replay Environment</span></span>|  
|--------------------------------|--------------------------------------------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="fd9c5-167">分散再生コントローラー サービス</span><span class="sxs-lookup"><span data-stu-id="fd9c5-167">Distributed Replay controller service</span></span>|<span data-ttu-id="fd9c5-168">1</span><span class="sxs-lookup"><span data-stu-id="fd9c5-168">1</span></span>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="fd9c5-169">分散再生クライアント サービス</span><span class="sxs-lookup"><span data-stu-id="fd9c5-169">Distributed Replay client service</span></span>|<span data-ttu-id="fd9c5-170">16 (物理コンピューターまたは仮想コンピューター)</span><span class="sxs-lookup"><span data-stu-id="fd9c5-170">16 (physical or virtual computers)</span></span>|  
|<span data-ttu-id="fd9c5-171">管理ツール</span><span class="sxs-lookup"><span data-stu-id="fd9c5-171">Administration tool</span></span>|<span data-ttu-id="fd9c5-172">無制限</span><span class="sxs-lookup"><span data-stu-id="fd9c5-172">Unlimited</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="fd9c5-173">1 台のコンピューターにインストールできる管理ツールのインスタンスは 1 つだけですが、管理ツールの複数のインスタンスを開始できます。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-173">Although only one instance of the administration tool can be installed on a single computer, you can start multiple instances of the administration tool.</span></span> <span data-ttu-id="fd9c5-174">複数の管理ツールから発行されたコマンドは、受信された順に解決されます。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-174">Commands issued from multiple administration tools are resolved in the order in which they are received.</span></span>  
  
## <a name="data-access-provider"></a><span data-ttu-id="fd9c5-175">データ アクセス プロバイダー</span><span class="sxs-lookup"><span data-stu-id="fd9c5-175">Data Access Provider</span></span>  
 <span data-ttu-id="fd9c5-176">分散再生は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC データ アクセス プロバイダーのみをサポートします。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-176">Distributed Replay only supports the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC data access provider.</span></span>  
  
## <a name="target-server-preparation-requirements"></a><span data-ttu-id="fd9c5-177">ターゲット サーバーの準備要件</span><span class="sxs-lookup"><span data-stu-id="fd9c5-177">Target Server Preparation Requirements</span></span>  
 <span data-ttu-id="fd9c5-178">ターゲット サーバーはテスト環境に配置することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-178">We recommend that the target server be located in a test environment.</span></span> <span data-ttu-id="fd9c5-179">最初に記録されたものと異なる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに対してトレース データを再生するには、ターゲット サーバーが次の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-179">To replay trace data against a different instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] than it was originally recorded, make sure that the following has been done to the target server:</span></span>  
  
-   <span data-ttu-id="fd9c5-180">トレース データに含まれるすべてのログインとユーザーが、ターゲット サーバー上の同一のデータベースに存在すること。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-180">All logins and users that are contained in the trace data must be present in the same database on the target server.</span></span>  
  
-   <span data-ttu-id="fd9c5-181">ターゲット サーバー上のすべてのログインとユーザーに、元のサーバー上で与えられているものと同じ権限が与えられていること。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-181">All logins and users on the target server must have the same permissions they had on the original server.</span></span>  
  
-   <span data-ttu-id="fd9c5-182">ターゲット コンピューター上のデータベース ID が、ソース コンピューター上のデータベース ID と同じであること。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-182">The database IDs on the target ideally should be the same as those on the source.</span></span> <span data-ttu-id="fd9c5-183">ただし、これらが同じでない場合、トレース内に **DatabaseName** が存在すれば、それに基づいて一致させることができます。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-183">However, if they are not the same, matching can be performed based on **DatabaseName** if it is present in the trace.</span></span>  
  
-   <span data-ttu-id="fd9c5-184">トレース データに含まれている各ログインの既定データベースが、ターゲット サーバー上で、ログインの対象データベースにそれぞれ設定されていること。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-184">The default database for each login that is contained in the trace data must be set (on the target server) to the respective target database of the login.</span></span> <span data-ttu-id="fd9c5-185">たとえば、再生されるトレース データが、 **の元のインスタンス上のデータベース**Fred_Db **に対する、ログイン** Fred [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の利用状況を含むとします。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-185">For example, the trace data to be replayed contains activity for the login, **Fred**, in the database **Fred_Db** on the original instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="fd9c5-186">この場合、ターゲット サーバー上では、ログイン **Fred** の既定データベースが、**Fred_Db** に一致するデータベースに設定されていなければなりません (データベース名が異なる場合も同様)。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-186">Therefore, on the target server, the default database for the login, **Fred**, must be set to the database that matches **Fred_Db** (even if the database name is different).</span></span> <span data-ttu-id="fd9c5-187">ログインの既定データベースを設定するには、 `sp_defaultdb` システム ストアド プロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-187">To set the default database of the login, use the `sp_defaultdb` system stored procedure.</span></span>  
  
 <span data-ttu-id="fd9c5-188">失われたログインや不正なログインに関連付けられたイベントを再生すると、再生エラーとなります。ただし、再生の処理は継続されます。</span><span class="sxs-lookup"><span data-stu-id="fd9c5-188">Replaying events associated with missing or incorrect logins results in replay errors, but the replay operation continues.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd9c5-189">参照</span><span class="sxs-lookup"><span data-stu-id="fd9c5-189">See Also</span></span>  
 <span data-ttu-id="fd9c5-190">[SQL Server Distributed Replay](sql-server-distributed-replay.md) </span><span class="sxs-lookup"><span data-stu-id="fd9c5-190">[SQL Server Distributed Replay](sql-server-distributed-replay.md) </span></span>  
 <span data-ttu-id="fd9c5-191">[分散再生のセキュリティ](distributed-replay-security.md) </span><span class="sxs-lookup"><span data-stu-id="fd9c5-191">[Distributed Replay Security](distributed-replay-security.md) </span></span>  
 [<span data-ttu-id="fd9c5-192">分散再生のインストール</span><span class="sxs-lookup"><span data-stu-id="fd9c5-192">Install Distributed Replay</span></span>](install-distributed-replay-overview.md)  
  
  
