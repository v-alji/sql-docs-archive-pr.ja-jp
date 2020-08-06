---
title: Analysis Services PowerShell |Microsoft Docs
ms.custom: ''
ms.date: 03/11/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 60bb9610-7229-42eb-a95f-a377268a8720
author: minewiskan
ms.author: owend
ms.openlocfilehash: 56af6f26c29e5c1ddb278b620b6f525c70bd1203
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633653"
---
# <a name="analysis-services-powershell"></a><span data-ttu-id="9370f-102">Analysis Services PowerShell</span><span class="sxs-lookup"><span data-stu-id="9370f-102">Analysis Services PowerShell</span></span>
  [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)]<span data-ttu-id="9370f-103">には、Analysis Services PowerShell (SQLAS) プロバイダーとコマンドレットが含まれています。これにより、Windows PowerShell を使用して Analysis Services オブジェクトの移動、管理、およびクエリを実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="9370f-103">includes an Analysis Services PowerShell (SQLAS) provider and cmdlets so that you can use Windows PowerShell to navigate, administer, and query Analysis Services objects.</span></span>  
  
 <span data-ttu-id="9370f-104">Analysis Services PowerShell は、次の要素で構成されています。</span><span class="sxs-lookup"><span data-stu-id="9370f-104">Analysis Services PowerShell consists of the following:</span></span>  
  
-   <span data-ttu-id="9370f-105">分析管理オブジェクト (AMO) 階層の移動に使用する `SQLAS` プロバイダー。</span><span class="sxs-lookup"><span data-stu-id="9370f-105">`SQLAS` provider used for navigating the Analysis Management Object (AMO) hierarchy.</span></span>  
  
-   <span data-ttu-id="9370f-106">MDX スクリプト、DMX スクリプト、または XMLA スクリプトの実行に使用する `Invoke-ASCmd` コマンドレット。</span><span class="sxs-lookup"><span data-stu-id="9370f-106">`Invoke-ASCmd` cmdlet used for executing MDX, DMX, or XMLA script.</span></span>  
  
-   <span data-ttu-id="9370f-107">処理、ロール管理、パーティション管理、バックアップと復元などの日常的な操作に使用するタスク固有のコマンドレット。</span><span class="sxs-lookup"><span data-stu-id="9370f-107">Task-specific cmdlets for routine operations, such as processing, role management, partition management, backup and restore.</span></span>  
  
## <a name="in-this-article"></a><span data-ttu-id="9370f-108">この記事の内容</span><span class="sxs-lookup"><span data-stu-id="9370f-108">In this article</span></span>  
 [<span data-ttu-id="9370f-109">前提条件</span><span class="sxs-lookup"><span data-stu-id="9370f-109">Prerequisites</span></span>](#bkmk_prereq)  
  
 [<span data-ttu-id="9370f-110">サポートされている Analysis Services のバージョンとモード</span><span class="sxs-lookup"><span data-stu-id="9370f-110">Supported Versions and Modes of Analysis Services</span></span>](#bkmk_vers)  
  
 [<span data-ttu-id="9370f-111">認証要件とセキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="9370f-111">Authentication Requirements and Security Considerations</span></span>](#bkmk_auth)  
  
 [<span data-ttu-id="9370f-112">Analysis Services PowerShell タスク</span><span class="sxs-lookup"><span data-stu-id="9370f-112">Analysis Services PowerShell Tasks</span></span>](#bkmk_tasks)  

<span data-ttu-id="9370f-113">構文と例の詳細については、「 [PowerShell リファレンスの Analysis Services](/sql/analysis-services/powershell/analysis-services-powershell-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9370f-113">For more information about syntax and examples, see [Analysis Services PowerShell Reference](/sql/analysis-services/powershell/analysis-services-powershell-reference).</span></span>

##  <a name="prerequisites"></a><a name="bkmk_prereq"></a> <span data-ttu-id="9370f-114">前提条件</span><span class="sxs-lookup"><span data-stu-id="9370f-114">Prerequisites</span></span>  
 <span data-ttu-id="9370f-115">Windows PowerShell 2.0 がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9370f-115">Windows PowerShell 2.0 must be installed.</span></span> <span data-ttu-id="9370f-116">新しいバージョンの Windows オペレーティング システムでは、既定でインストールされます。</span><span class="sxs-lookup"><span data-stu-id="9370f-116">It is installed by default on newer versions of the Windows operating systems.</span></span> <span data-ttu-id="9370f-117">詳細については、「 [Windows PowerShell 2.0 のインストール](https://msdn.microsoft.com/library/ff637750.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9370f-117">For more information, see [Install Windows PowerShell 2.0](https://msdn.microsoft.com/library/ff637750.aspx)</span></span>

<!-- ff637750.aspx above is linked to by:  (https://go.microsoft.com/fwlink/?LinkId=227613). -->
  
 <span data-ttu-id="9370f-118">SQL Server PowerShell (SQLPS) モジュールとクライアント ライブラリを含んだ SQL Server 機能をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9370f-118">You must install a SQL Server feature that includes the SQL Server PowerShell (SQLPS) module and client libraries.</span></span> <span data-ttu-id="9370f-119">その最も簡単な方法は、SQL Server Management Studio をインストールすることです。SQL Server Management Studio をインストールすると、PowerShell の機能とクライアント ライブラリも自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="9370f-119">The easiest way to do this is by installing SQL Server Management Studio, which includes the PowerShell feature and client libraries automatically.</span></span> <span data-ttu-id="9370f-120">SQL Server PowerShell (SQLPS) モジュールには、Analysis Services オブジェクト階層の移動に使用する SQLASCmdlets モジュールと SQLAS プロバイダーなど、すべての SQL Server 機能用の PowerShell プロバイダーとコマンドレットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="9370f-120">The SQL Server PowerShell (SQLPS) module contains the PowerShell providers and cmdlets for all SQL Server features, including the SQLASCmdlets module and SQLAS provider used for navigating the Analysis Services object hierarchy.</span></span>  
  
 <span data-ttu-id="9370f-121">プロバイダーとコマンドレットを使用するには、 **Sqlps**モジュールをインポートする必要があり `SQLAS` ます。</span><span class="sxs-lookup"><span data-stu-id="9370f-121">You must import the **SQLPS** module before you can use the `SQLAS` provider and cmdlets.</span></span> <span data-ttu-id="9370f-122">SQLAS プロバイダーは、プロバイダーの拡張機能です `SQLServer` 。</span><span class="sxs-lookup"><span data-stu-id="9370f-122">The SQLAS provider is an extension of the `SQLServer` provider.</span></span> <span data-ttu-id="9370f-123">SQLPS モジュールをインポートするには、いくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="9370f-123">There are several ways to import the SQLPS module.</span></span> <span data-ttu-id="9370f-124">詳細については、「 [SQLPS モジュールのインポート](../../2014/database-engine/import-the-sqlps-module.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9370f-124">For more information, see [Import the SQLPS Module](../../2014/database-engine/import-the-sqlps-module.md).</span></span>  
  
 <span data-ttu-id="9370f-125">Analysis Services インスタンスにリモート アクセスするには、リモート管理とファイル共有を有効にしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="9370f-125">Remote access to an Analysis Services instance requires that you enable remote administration and file sharing.</span></span> <span data-ttu-id="9370f-126">詳細については、このトピックの「[リモート管理の有効化](#bkmk_remote)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9370f-126">For more information, see [Enable Remote Administration](#bkmk_remote) in this topic.</span></span>  
  
##  <a name="supported-versions-and-modes-of-analysis-services"></a><a name="bkmk_vers"></a> <span data-ttu-id="9370f-127">サポートされている Analysis Services のバージョンとモード</span><span class="sxs-lookup"><span data-stu-id="9370f-127">Supported Versions and Modes of Analysis Services</span></span>  
 <span data-ttu-id="9370f-128">現在、Analysis Services PowerShell は、Windows Server 2008 R2、Windows Server 2008 SP1、または Windows 7 で動作する [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Analysis Services のすべてのエディションでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="9370f-128">Currently, Analysis Services PowerShell is supported on any edition of [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Analysis Services running on Windows Server 2008 R2, Windows Server 2008 SP1, or Windows 7.</span></span>  
  
 <span data-ttu-id="9370f-129">次の表に、さまざまなコンテキストで利用可能な Analysis Services PowerShell の機能を示します。</span><span class="sxs-lookup"><span data-stu-id="9370f-129">The following table shows the availability of Analysis Services PowerShell in different contexts.</span></span>  
  
|<span data-ttu-id="9370f-130">コンテキスト</span><span class="sxs-lookup"><span data-stu-id="9370f-130">Context</span></span>|<span data-ttu-id="9370f-131">PowerShell の利用可能な機能</span><span class="sxs-lookup"><span data-stu-id="9370f-131">PowerShell Feature Availability</span></span>|  
|-------------|-------------------------------------|  
|<span data-ttu-id="9370f-132">多次元のインスタンスとデータベース</span><span class="sxs-lookup"><span data-stu-id="9370f-132">Multidimensional instances and databases</span></span>|<span data-ttu-id="9370f-133">ローカルおよびリモート管理でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="9370f-133">Supported for local and remote administration.</span></span><br /><br /> <span data-ttu-id="9370f-134">Merge-partition にはローカル接続が必要です。</span><span class="sxs-lookup"><span data-stu-id="9370f-134">Merge-partition requires a local connection.</span></span>|  
|<span data-ttu-id="9370f-135">表形式のインスタンスとデータベース</span><span class="sxs-lookup"><span data-stu-id="9370f-135">Tabular instances and databases</span></span>|<span data-ttu-id="9370f-136">ローカルおよびリモート管理でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="9370f-136">Supported for local and remote administration.</span></span><br /><br /> <span data-ttu-id="9370f-137">詳細については、「 [PowerShell を使用したテーブルモデルの管理](https://go.microsoft.com/fwlink/?linkID=227685)」の2011年8月のブログを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9370f-137">For more information, see an August 2011 blog about [Manage Tabular Models Using PowerShell](https://go.microsoft.com/fwlink/?linkID=227685).</span></span>|  
|<span data-ttu-id="9370f-138">PowerPivot for SharePoint のインスタンスとデータベース</span><span class="sxs-lookup"><span data-stu-id="9370f-138">PowerPivot for SharePoint instances and databases</span></span>|<span data-ttu-id="9370f-139">制限付きサポート。</span><span class="sxs-lookup"><span data-stu-id="9370f-139">Limited support.</span></span> <span data-ttu-id="9370f-140">HTTP 接続と SQLAS プロバイダーを使用して、インスタンスとデータベースの情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="9370f-140">You can use HTTP connections and the SQLAS provider to view instance and database information.</span></span><br /><br /> <span data-ttu-id="9370f-141">ただし、コマンドレットの使用はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="9370f-141">However, using the cmdlets is not supported.</span></span> <span data-ttu-id="9370f-142">インメモリ PowerPivot データベースのバックアップと復元に Analysis Services PowerShell は使用しないでください。また、ロールの追加や削除、データの処理、任意の XMLA スクリプトの実行にも使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="9370f-142">You must not use Analysis Services PowerShell to backup and restore in-memory PowerPivot database, nor should you add or remove roles, process data, or run arbitrary XMLA script.</span></span><br /><br /> <span data-ttu-id="9370f-143">PowerPivot for SharePoint には、構成のために個別に提供される組み込みの PowerShell サポートがあります。</span><span class="sxs-lookup"><span data-stu-id="9370f-143">For configuration purposes, PowerPivot for SharePoint has built-in PowerShell support that is provided separately.</span></span> <span data-ttu-id="9370f-144">詳細については、「 [PowerShell Reference for PowerPivot for SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9370f-144">For more information, see [PowerShell Reference for PowerPivot for SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint).</span></span>|  
|<span data-ttu-id="9370f-145">ローカル キューブへのネイティブ接続</span><span class="sxs-lookup"><span data-stu-id="9370f-145">Native connections to local cubes</span></span><br /><br /> <span data-ttu-id="9370f-146">"Data Source = c:\backup\test.cub"</span><span class="sxs-lookup"><span data-stu-id="9370f-146">"Data Source=c:\backup\test.cub"</span></span>|<span data-ttu-id="9370f-147">サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="9370f-147">Not supported.</span></span>|  
|<span data-ttu-id="9370f-148">SharePoint 内の BI セマンティック モデル (.bism) 接続ファイルへの HTTP 接続</span><span class="sxs-lookup"><span data-stu-id="9370f-148">HTTP connections to BI semantic model (.bism) connection files in SharePoint</span></span><br /><br /> <span data-ttu-id="9370f-149">"Data Source = http://server/shared_docs/name.bism "</span><span class="sxs-lookup"><span data-stu-id="9370f-149">"Data Source=http://server/shared_docs/name.bism"</span></span>|<span data-ttu-id="9370f-150">サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="9370f-150">Not supported.</span></span>|  
|<span data-ttu-id="9370f-151">PowerPivot データベースへの埋め込み接続</span><span class="sxs-lookup"><span data-stu-id="9370f-151">Embedded connections to PowerPivot databases</span></span><br /><br /> <span data-ttu-id="9370f-152">"Data Source = $Embedded $"</span><span class="sxs-lookup"><span data-stu-id="9370f-152">"Data Source=$Embedded$"</span></span>|<span data-ttu-id="9370f-153">サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="9370f-153">Not supported.</span></span>|  
|<span data-ttu-id="9370f-154">Analysis Services ストアド プロシージャ内のローカル サーバーのコンテキスト</span><span class="sxs-lookup"><span data-stu-id="9370f-154">Local server context in Analysis Services stored procedures</span></span><br /><br /> <span data-ttu-id="9370f-155">"Data Source = \*"</span><span class="sxs-lookup"><span data-stu-id="9370f-155">"Data Source=\*"</span></span>|<span data-ttu-id="9370f-156">サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="9370f-156">Not supported.</span></span>|  
  
##  <a name="authentication-requirements-and-security-considerations"></a><a name="bkmk_auth"></a><span data-ttu-id="9370f-157">認証要件とセキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="9370f-157">Authentication Requirements and Security Considerations</span></span>  
 <span data-ttu-id="9370f-158">Analysis Services に接続する際は、Windows のユーザー ID を使用して接続を確立する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9370f-158">When connecting to Analysis Services, you must make the connection using a Windows user identity.</span></span> <span data-ttu-id="9370f-159">大半の接続は Windows 統合セキュリティを使用して確立されます。この場合、サーバーの動作するセキュリティ コンテキストは、現在のユーザーの ID によって設定されます。</span><span class="sxs-lookup"><span data-stu-id="9370f-159">For the most part, a connection is made using Windows integrated security, where the identity of the current user sets the security context under which server operations are performed.</span></span> <span data-ttu-id="9370f-160">ただし、Analysis Services への HTTP アクセスを構成すると、その他の認証方法も利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="9370f-160">However, additional authentication methods become available when you configure HTTP access to Analysis Services.</span></span> <span data-ttu-id="9370f-161">このセクションでは、使用できる認証オプションが、接続の種類に応じてどのように変わるかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9370f-161">This section explains how the type of connection determines which authentication options you can use.</span></span>  
  
 <span data-ttu-id="9370f-162">Analysis Services への接続は、大きくネイティブ接続と HTTP 接続とに分けられます。</span><span class="sxs-lookup"><span data-stu-id="9370f-162">Connections to Analysis Services are characterized as either native connections or HTTP connections.</span></span> <span data-ttu-id="9370f-163">ネイティブ接続は、クライアント アプリケーションからサーバーへの直接接続です。</span><span class="sxs-lookup"><span data-stu-id="9370f-163">A native connection is a direct connection from a client application to the server.</span></span> <span data-ttu-id="9370f-164">PowerShell セッションでは、PowerShell クライアントが OLE DB Provider for Analysis Services を使用して直接 Analysis Services インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="9370f-164">In a PowerShell session, the PowerShell client uses the OLE DB provider for Analysis Services to connect directly to an Analysis Services instance.</span></span> <span data-ttu-id="9370f-165">ネイティブ接続は常に Windows 統合セキュリティを使用して行われます。この場合、Analysis Services PowerShell は、現在のユーザーとして実行されます。</span><span class="sxs-lookup"><span data-stu-id="9370f-165">A native connection is always made using Windows integrated security, where Analysis Services PowerShell executes as the current user.</span></span> <span data-ttu-id="9370f-166">Analysis Services では、権限借用はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="9370f-166">Analysis Services does not support impersonation.</span></span> <span data-ttu-id="9370f-167">特定のユーザーとして操作を実行するには、そのユーザーとして PowerShell セッションを開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9370f-167">If you want to perform an operation as a specific user, you must start the PowerShell session as that user.</span></span>  
  
 <span data-ttu-id="9370f-168">HTTP 接続は IIS を通じて間接的に確立されるため、他の認証オプション (基本認証など) を使用して、Analysis Services インスタンスに接続することができます。</span><span class="sxs-lookup"><span data-stu-id="9370f-168">HTTP connections are made indirectly through IIS, allowing for additional authentication options, such as Basic authentication, to connect to an Analysis Services instance.</span></span> <span data-ttu-id="9370f-169">IIS では権限借用がサポートされます。IIS で使用する資格情報を接続文字列に追加し、接続の確立時にその接続文字列を指定することで、権限を借用することができます。</span><span class="sxs-lookup"><span data-stu-id="9370f-169">Because IIS supports impersonation, you can provide a connection string that includes credentials IIS will use to impersonate when making a connection.</span></span> <span data-ttu-id="9370f-170">資格情報を指定するには、-Credential パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="9370f-170">To provide credentials, you can use the -Credential parameter.</span></span>  
  
 <span data-ttu-id="9370f-171">**PowerShell で-Credential パラメーターを使用する**</span><span class="sxs-lookup"><span data-stu-id="9370f-171">**Using the -Credential Parameter in PowerShell**</span></span>  
  
 <span data-ttu-id="9370f-172">-Credential パラメーターは、ユーザー名とパスワードを指定する PSCredential オブジェクトを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="9370f-172">The -Credential parameter takes a PSCredential object that specifies a user name and password.</span></span> <span data-ttu-id="9370f-173">Analysis Services PowerShell では、既存の接続のコンテキスト内で実行されるコマンドレットとは対照的に、-Credential パラメーターを使用して、Analysis Services への接続要求を行うコマンドレットを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9370f-173">In Analysis Services PowerShell, the -Credential parameter is available for cmdlets that make a connection request to Analysis Services, as opposed to cmdlets that run within the context of an existing connection.</span></span> <span data-ttu-id="9370f-174">接続要求を行うコマンドレットとしては、Invoke-ASCmd、Backup-ASDatabase、Restore-ASDatabase などが挙げられます。</span><span class="sxs-lookup"><span data-stu-id="9370f-174">Cmdlets that make a connection request include Invoke-ASCmd, Backup-ASDatabase, and Restore-ASDatabase.</span></span> <span data-ttu-id="9370f-175">これらのコマンドレットでは、次の条件が満たされている場合、-Credential パラメーターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9370f-175">For these cmdlets, the -Credential parameter can be used, assuming the following criteria are met:</span></span>  
  
1.  <span data-ttu-id="9370f-176">サーバーが HTTP アクセス用に構成されている (つまり、Analysis Services に接続する際は、IIS が接続を処理し、ユーザー名とパスワードを読み取り、対応するユーザー ID の権限を借用する)。</span><span class="sxs-lookup"><span data-stu-id="9370f-176">The server is configured for HTTP access, which means that IIS handles the connection, reads the user name and password, and impersonates that user identity when connecting to Analysis Services.</span></span> <span data-ttu-id="9370f-177">詳細については、「 [インターネット インフォメーション サービス &#40;IIS&#41; 8.0 上の Analysis Services への HTTP アクセスの構成](instances/configure-http-access-to-analysis-services-on-iis-8-0.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9370f-177">For more information, see [Configure HTTP Access to Analysis Services on Internet Information Services &#40;IIS&#41; 8.0](instances/configure-http-access-to-analysis-services-on-iis-8-0.md).</span></span>  
  
2.  <span data-ttu-id="9370f-178">Analysis Services の HTTP アクセス用に作成された IIS 仮想ディレクトリが、基本認証を使用するように構成されている。</span><span class="sxs-lookup"><span data-stu-id="9370f-178">The IIS virtual directory that was created for Analysis Services HTTP access is configured for Basic authentication.</span></span>  
  
3.  <span data-ttu-id="9370f-179">資格情報オブジェクトによって指定されたユーザー名とパスワードが、Windows ユーザー ID へと解決される。</span><span class="sxs-lookup"><span data-stu-id="9370f-179">The user name and password provided by the credential object resolves to a Windows user identity.</span></span> <span data-ttu-id="9370f-180">Analysis Services は、この ID を現在のユーザーとして使用します。</span><span class="sxs-lookup"><span data-stu-id="9370f-180">Analysis Services uses this identity as the current user.</span></span> <span data-ttu-id="9370f-181">Windows ユーザーでない場合、または要求された操作を実行するための十分な権限がそのユーザーにない場合、要求は失敗します。</span><span class="sxs-lookup"><span data-stu-id="9370f-181">If the user is not a Windows user, or lacks sufficient permissions to perform the requested operation, the request will fail.</span></span>  
  
 <span data-ttu-id="9370f-182">資格情報オブジェクトを作成するには、Get-Credential コマンドレットを使用して、対象のオペレーターの資格情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="9370f-182">To create a credential object, you can use the Get-Credential cmdlet to collect the credentials from the operator.</span></span> <span data-ttu-id="9370f-183">この資格情報オブジェクトを Analysis Services への接続コマンドに使用できます。</span><span class="sxs-lookup"><span data-stu-id="9370f-183">You can then use the credential object on a command that connects to Analysis Services.</span></span> <span data-ttu-id="9370f-184">次の例は、1つの方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="9370f-184">The following example illustrates one approach.</span></span> <span data-ttu-id="9370f-185">この例では、 `SQLSERVER:\SQLAS\HTTP_DS` HTTP アクセス用に構成されたローカルインスタンス () への接続です。</span><span class="sxs-lookup"><span data-stu-id="9370f-185">In this example, the connection is to a local instance (`SQLSERVER:\SQLAS\HTTP_DS`) configured for HTTP access.</span></span>  
  
```powershell
$cred = Get-Credential adventureworks\dbadmin  
Invoke-ASCmd -Inputfile:"c:\discoverconnections.xmla" -Credential:$cred  
```  
  
 <span data-ttu-id="9370f-186">基本認証を使用する際は、暗号化された接続を介してユーザー名とパスワードが送信されるように、必ず HTTPS と SSL を使用してください。</span><span class="sxs-lookup"><span data-stu-id="9370f-186">When using Basic authentication, you should always use HTTPS with SSL so that username and passwords are sent over an encrypted connection.</span></span> <span data-ttu-id="9370f-187">詳細については、「 [IIS 7.0 で Secure Sockets Layer を構成する](https://go.microsoft.com/fwlink/?linkID=184299)」および「[基本認証を構成する (iis 7)](https://go.microsoft.com/fwlink/?LinkId=230776)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9370f-187">For more information, see [Configure Secure Sockets Layer in IIS 7.0](https://go.microsoft.com/fwlink/?linkID=184299) and [Configure Basic Authentication (IIS 7)](https://go.microsoft.com/fwlink/?LinkId=230776).</span></span>  
  
 <span data-ttu-id="9370f-188">PowerShell で指定した資格情報、クエリ、およびコマンドは、そのままトランスポート層に渡されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9370f-188">Remember that credentials, queries, and commands that you provide in PowerShell are passed unchanged to the transport layer.</span></span> <span data-ttu-id="9370f-189">機密性の高いコンテンツがスクリプトに含まれていると、悪質なインジェクション攻撃のリスクが増大します。</span><span class="sxs-lookup"><span data-stu-id="9370f-189">Including sensitive content in your scripts increases the risk of a malicious injection attack.</span></span>  
  
 <span data-ttu-id="9370f-190">**Microsoft.Secure.String オブジェクトでのパスワードの指定**</span><span class="sxs-lookup"><span data-stu-id="9370f-190">**Providing a password as a Microsoft.Secure.String object**</span></span>  
  
 <span data-ttu-id="9370f-191">バックアップや復元など、一部の操作については、コマンドにパスワードを指定した場合にアクティブ化される暗号化オプションがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="9370f-191">Some operations, such as backup and restore, support encryption options that are activated when you provide a password in the command.</span></span> <span data-ttu-id="9370f-192">パスワードを指定すると、バックアップ ファイルを暗号化 (または暗号化を解除) するように、Analysis Services 伝えられます。</span><span class="sxs-lookup"><span data-stu-id="9370f-192">Providing the password signals Analysis Services to encrypt or decrypt the backup file.</span></span> <span data-ttu-id="9370f-193">このパスワードは、Analysis Services において、セキュリティで保護された文字列オブジェクトとしてインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="9370f-193">In Analysis Services, this password is instantiated as a secure string object.</span></span> <span data-ttu-id="9370f-194">次の例では、オペレーターから実行時にパスワードを収集します。</span><span class="sxs-lookup"><span data-stu-id="9370f-194">The following example provides an illustration of how to collect a password from the operator at run time.</span></span>  
  
```powershell
$pwd = read-host -AsSecureString -Prompt "Password"  
$pwd -is [System.IDisposable]  
```  
  
 <span data-ttu-id="9370f-195">これで、password パラメーターに $pwd 変数を渡すことによって、暗号化されたデータベース ファイルをバックアップまたは復元することができます。</span><span class="sxs-lookup"><span data-stu-id="9370f-195">You can now backup or restore an encrypted database file, passing the $pwd variable to the password parameter.</span></span> <span data-ttu-id="9370f-196">この図と他のコマンドレットを組み合わせた完全な例については、「 [Backup-ASDatabase コマンド](/powershell/module/sqlserver/backup-asdatabase)レット」と「 [Restore-asdatabase コマンドレット](/powershell/module/sqlserver/restore-asdatabase)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9370f-196">To view a complete example that combines this illustration with other cmdlets, see [Backup-ASDatabase cmdlet](/powershell/module/sqlserver/backup-asdatabase) and [Restore-ASDatabase cmdlet](/powershell/module/sqlserver/restore-asdatabase).</span></span>
  
 <span data-ttu-id="9370f-197">最後に、パスワードと変数の両方をセッションから削除します。</span><span class="sxs-lookup"><span data-stu-id="9370f-197">As a follow up step, remove both the password and variable from the session.</span></span>  
  
```powershell
$pwd.Dispose()  
Remove-Variable -Name pwd  
```  
  
##  <a name="analysis-services-powershell-tasks"></a><a name="bkmk_tasks"></a><span data-ttu-id="9370f-198">PowerShell タスクの Analysis Services</span><span class="sxs-lookup"><span data-stu-id="9370f-198">Analysis Services PowerShell Tasks</span></span>  
 <span data-ttu-id="9370f-199">Analysis Services PowerShell は、Windows PowerShell 管理シェルまたは Windows コマンド プロンプトから実行できます。</span><span class="sxs-lookup"><span data-stu-id="9370f-199">You can run Analysis Services PowerShell from the Windows PowerShell management shell or a Windows command prompt.</span></span> <span data-ttu-id="9370f-200">Analysis Services PowerShell を [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] から実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="9370f-200">Running Analysis Services PowerShell from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] is not supported.</span></span>  
  
 <span data-ttu-id="9370f-201">ここでは、Analysis Services PowerShell を使用する一般的なタスクについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9370f-201">This section describes common tasks for using Analysis Services PowerShell.</span></span>  
  
-   [<span data-ttu-id="9370f-202">Analysis Services プロバイダーとコマンドレットの読み込み</span><span class="sxs-lookup"><span data-stu-id="9370f-202">Load the Analysis Services Provider and Cmdlets</span></span>](#bkmk_load)  
  
-   [<span data-ttu-id="9370f-203">リモート管理の有効化</span><span class="sxs-lookup"><span data-stu-id="9370f-203">Enable Remote Administration</span></span>](#bkmk_remote)  
  
-   [<span data-ttu-id="9370f-204">Analysis Services オブジェクトへの接続</span><span class="sxs-lookup"><span data-stu-id="9370f-204">Connect to an Analysis Services Object</span></span>](#bkmk_connect)  
  
-   [<span data-ttu-id="9370f-205">サービスを管理する</span><span class="sxs-lookup"><span data-stu-id="9370f-205">Administer the Service</span></span>](#bkmk_admin)  
  
-   [<span data-ttu-id="9370f-206">Analysis Services PowerShell のヘルプ</span><span class="sxs-lookup"><span data-stu-id="9370f-206">Get Help for Analysis Services PowerShell</span></span>](#bkmk_help)  
  
###  <a name="load-the-analysis-services-provider-and-cmdlets"></a><a name="bkmk_load"></a><span data-ttu-id="9370f-207">Analysis Services プロバイダーとコマンドレットを読み込む</span><span class="sxs-lookup"><span data-stu-id="9370f-207">Load the Analysis Services Provider and Cmdlets</span></span>  
 <span data-ttu-id="9370f-208">Analysis Services プロバイダーは、SQLPS モジュールをインポートすると利用可能になる SQL Server ルート プロバイダーの拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="9370f-208">The Analysis Services provider is an extension of the SQL Server root provider that becomes available when you import the SQLPS module.</span></span> <span data-ttu-id="9370f-209">Analysis Services コマンドレットも同時に読み込まれます。プロバイダーなしでコマンドレットを使用する場合は、コマンドレットを別に読み込むこともできます。</span><span class="sxs-lookup"><span data-stu-id="9370f-209">Analysis Services cmdlets are loaded simultaneously; you can also load them independently if you want to use them without the provider.</span></span>  
  
-   <span data-ttu-id="9370f-210">Import-module コマンドレットを実行して、Analysis Services PowerShell のすべての機能を含む SQLPS を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="9370f-210">Run the Import-module cmdlet to load SQLPS that includes all of the Analysis Services PowerShell functionality.</span></span> <span data-ttu-id="9370f-211">モジュールをインポートできない場合は、モジュールを読み込む目的で、一時的に実行ポリシーを無制限に変更することができます。</span><span class="sxs-lookup"><span data-stu-id="9370f-211">If you cannot import the module, you can temporarily change the execution policy to unrestricted for the purpose of the loading the module.</span></span> <span data-ttu-id="9370f-212">詳細については、「 [SQLPS モジュールのインポート](../../2014/database-engine/import-the-sqlps-module.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9370f-212">For more information, see [Import the SQLPS Module](../../2014/database-engine/import-the-sqlps-module.md).</span></span>  
  
    ```powershell
    Import-Module "sqlps"  
    ```  
  
     <span data-ttu-id="9370f-213">または、`import-module "sqlps" -disablenamechecking` を使用して、承認されていない動詞の名前についての警告を抑制します。</span><span class="sxs-lookup"><span data-stu-id="9370f-213">Alternatively, use `import-module "sqlps" -disablenamechecking` to suppress the warning about unapproved verb names.</span></span>  
  
-   <span data-ttu-id="9370f-214">Analysis Services プロバイダーも Invoke-ASCmd コマンドレットも読み込まずに、タスク固有の Analysis Services コマンドレットのみを読み込むには、独立した操作として SQLASCmdlets モジュールを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="9370f-214">To load just the task-specific Analysis Services cmdlets, without the Analysis Services provider or the Invoke-ASCmd cmdlet, you can load the SQLASCmdlets module as an independent operation.</span></span>  
  
    ```powershell
    Import-Module "sqlascmdlets"  
    ```  
  
###  <a name="enable-remote-administration"></a><a name="bkmk_remote"></a><span data-ttu-id="9370f-215">リモート管理を有効にする</span><span class="sxs-lookup"><span data-stu-id="9370f-215">Enable Remote Administration</span></span>  
 <span data-ttu-id="9370f-216">リモートの Analysis Services インスタンスと共に Analysis Services PowerShell を使用するには、まずリモート管理とファイル共有を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9370f-216">Before you can use Analysis Services PowerShell with a remote Analysis Services instance, you must first enable remote administration and file sharing.</span></span> <span data-ttu-id="9370f-217">次のエラーは、ファイアウォールの構成に問題があることを示します。 "RPC サーバーは使用できません。</span><span class="sxs-lookup"><span data-stu-id="9370f-217">The following error indicates a firewall configuration issue: "The RPC server is unavailable.</span></span> <span data-ttu-id="9370f-218">(HRESULT からの例外: 0x800706BA)"。</span><span class="sxs-lookup"><span data-stu-id="9370f-218">(Exception from HRESULT: 0x800706BA)".</span></span>  
  
1.  <span data-ttu-id="9370f-219">ローカル コンピューターとリモート コンピューターの両方で、クライアント ツールとサーバー ツールが [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] のバージョンであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9370f-219">Verify that both local and remote computers have the [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] versions of the client and server tools.</span></span>  
  
2.  <span data-ttu-id="9370f-220">Analysis Services インスタンスをホストしているリモート サーバーで、Windows ファイアウォールの TCP ポート 2383 を開きます。</span><span class="sxs-lookup"><span data-stu-id="9370f-220">On the remote server that is hosting an Analysis Services instance, open TCP port 2383 in Windows Firewall.</span></span> <span data-ttu-id="9370f-221">Analysis Services を名前付きインスタンスとしてインストールした場合やカスタム ポートを使用している場合は、ポート番号は異なります。</span><span class="sxs-lookup"><span data-stu-id="9370f-221">If you installed Analysis Services as a named instance or are using a custom port, the port number will be different.</span></span> <span data-ttu-id="9370f-222">詳細については、「 [Configure the Windows Firewall to Allow Analysis Services Access](instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)」をご参照ください。</span><span class="sxs-lookup"><span data-stu-id="9370f-222">For more information, see [Configure the Windows Firewall to Allow Analysis Services Access](instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).</span></span>  
  
3.  <span data-ttu-id="9370f-223">リモート サーバーで、リモート プロシージャ コール (RPC) サービス、TCP/IP NetBIOS Helper サービス、WMI (Windows Management Instrumentation) サービス、Windows リモート管理 (WS-Management) サービスが開始されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9370f-223">On the remote server, verify that the followings services are started:  Remote Procedure Call (RPC) service, TCP/IP NetBIOS Helper service, Windows Management Instrumentation (WMI) service, Windows Remote Management (WS-Management) service.</span></span>  
  
4.  <span data-ttu-id="9370f-224">リモート サーバーで、グループ ポリシー オブジェクト エディター スナップイン (gpedit.msc) を起動します。</span><span class="sxs-lookup"><span data-stu-id="9370f-224">On the remote server, start the Group Policy Object Editor snap-in (gpedit.msc).</span></span>  
  
5.  <span data-ttu-id="9370f-225">[コンピューターの構成]、[管理用テンプレート]、[ネットワーク]、[ネットワーク接続]、[Windows ファイアウォール]、[ドメイン プロファイル] の順に開きます。</span><span class="sxs-lookup"><span data-stu-id="9370f-225">Open Computer Configuration, open Administrative Templates, open Network, open Network Connections, open Windows Firewall, and then open Domain Profile.</span></span>  
  
6.  <span data-ttu-id="9370f-226">[ **Windows ファイアウォール: 着信リモート管理の例外を許可する**] をダブルクリックし、[**有効**] を選択して、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9370f-226">Double-click **Windows Firewall: Allow inbound remote administration exception**, select **Enabled**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="9370f-227">[ **Windows ファイアウォール: 着信ファイルとプリンターの共有の例外を許可する**] をダブルクリックし、[**有効**] を選択して、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9370f-227">Double-click **Windows Firewall: Allow inbound file and printer sharing exception**, select **Enabled**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="9370f-228">クライアントツールがあるローカルコンピューターで、次のコマンドレットを使用してリモート管理を確認し、*リモートサーバー名*のプレースホルダーの実際のサーバー名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="9370f-228">On the local computer that has the client tools, use the following cmdlets to verify remote administration, substituting the actual server name for the *remote-server-name* placeholder.</span></span> <span data-ttu-id="9370f-229">Analysis Services が既定のインスタンスとしてインストールされている場合は、インスタンス名は省略します。</span><span class="sxs-lookup"><span data-stu-id="9370f-229">Omit the instance name if Analysis Services is installed as the default instance.</span></span> <span data-ttu-id="9370f-230">このコマンドが機能するためには、事前に SQLPS モジュールをインポートしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="9370f-230">You must have previously imported the SQLPS module in order for the command to work.</span></span>  
  
    ```
    PS SQLSERVER:\> cd sqlas
    PS SQLSERVER:\sqlas> cd <remote-server-name\instance-name>  
    PS SQLSERVER:\sqlas\<remote-server-name\instance-name> dir  
    ```  
  
 <span data-ttu-id="9370f-231">場合によっては、追加的な構成が必要になることもあります。</span><span class="sxs-lookup"><span data-stu-id="9370f-231">In some cases, additional configuration might be necessary.</span></span> <span data-ttu-id="9370f-232">たとえば、リモート サーバーに対して別のコンピューターからコマンドを実行するには、リモート サーバーで次のコマンドを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9370f-232">You might need to type the following on the remote server before you can issue commands to it from another computer:</span></span>  
  
```powershell
Enable-PSRemoting  
```  
  
  
###  <a name="connect-to-an-analysis-services-object"></a><a name="bkmk_connect"></a><span data-ttu-id="9370f-233">Analysis Services オブジェクトへの接続</span><span class="sxs-lookup"><span data-stu-id="9370f-233">Connect to an Analysis Services Object</span></span>  
 <span data-ttu-id="9370f-234">Analysis Services PowerShell プロバイダーは、Analysis Services オブジェクト階層の移動をサポートし、コマンド実行のコンテキストを設定します。</span><span class="sxs-lookup"><span data-stu-id="9370f-234">The Analysis Services PowerShell provider supports navigation of the Analysis Services object hierarchy and sets the context for running commands.</span></span> <span data-ttu-id="9370f-235">プロバイダーは、SQLPS モジュールを通じて利用できる SQLSERVER ルート プロバイダーの拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="9370f-235">The provider is an extension of the SQLSERVER root provider available through the SQLPS module.</span></span> <span data-ttu-id="9370f-236">SQLPS モジュールを読み込むと、パスを移動できます。</span><span class="sxs-lookup"><span data-stu-id="9370f-236">After you load the SQLPS module, you can navigate the path.</span></span>  
  
 <span data-ttu-id="9370f-237">ローカルまたはリモートのインスタンスに接続できますが、一部のコマンドレットはローカル インスタンス (マージ パーティション) のみで動作します。</span><span class="sxs-lookup"><span data-stu-id="9370f-237">You can connect to a local or remote instance, but some cmdlets only run on a local instance (namely, merge-partition).</span></span> <span data-ttu-id="9370f-238">ネイティブ接続、または HTTP アクセス用に構成した Analysis Services サーバーの HTTP 接続を使用できます。</span><span class="sxs-lookup"><span data-stu-id="9370f-238">You can use a native connection or an HTTP connection for Analysis Services servers that you configured for HTTP access.</span></span> <span data-ttu-id="9370f-239">次の図は、ネイティブ接続と HTTP 接続のナビゲーション パスを示しています。</span><span class="sxs-lookup"><span data-stu-id="9370f-239">The following illustrations show the navigation path for native and HTTP connections.</span></span> <span data-ttu-id="9370f-240">次の図は、ネイティブ接続と HTTP 接続のナビゲーション パスを示しています。</span><span class="sxs-lookup"><span data-stu-id="9370f-240">The following illustrations show the navigation path for native and HTTP connections.</span></span>  
  
 <span data-ttu-id="9370f-241">**Analysis Services へのネイティブ接続**</span><span class="sxs-lookup"><span data-stu-id="9370f-241">**Native Connections to Analysis Services**</span></span>  
  
 <span data-ttu-id="9370f-242">![Analysis Services へのネイティブ接続](media/ssas-powershell-nativeconnection.gif "Analysis Services へのネイティブ接続")</span><span class="sxs-lookup"><span data-stu-id="9370f-242">![Native connection to Analysis Services](media/ssas-powershell-nativeconnection.gif "Native connection to Analysis Services")</span></span>  
  
 <span data-ttu-id="9370f-243">次の例は、ネイティブ接続を使用してオブジェクト階層を移動する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="9370f-243">The following example is a demonstration of how to use a native connection to navigate object hierarchy.</span></span> <span data-ttu-id="9370f-244">プロバイダーから `dir` を実行して、インスタンスの情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="9370f-244">From the provider, you can issue a `dir` to view instance information.</span></span> <span data-ttu-id="9370f-245">`cd` を使用して、そのインスタンスのオブジェクトを表示できます。</span><span class="sxs-lookup"><span data-stu-id="9370f-245">You can use `cd` to view objects of that instance.</span></span>  
  
```  
PS SQLSERVER:> cd sqlas  
PS SQLSERVER\sqlas:> dir  
PS SQLSERVER\sqlas:> cd localhost\default  
PS SQLSERVER\sqlas\localhost\default:> dir  
```  
  
 <span data-ttu-id="9370f-246">アセンブリ、データベース、ロール、トレースの各コレクションを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9370f-246">You should see the following collections: Assemblies, Databases, Roles, and Traces.</span></span> <span data-ttu-id="9370f-247">`cd` と `dir` を引き続き使用して、各コレクションの内容を表示できます。</span><span class="sxs-lookup"><span data-stu-id="9370f-247">Continuing to use `cd` and `dir`, you can view the contents of each collection.</span></span>  
  
 <span data-ttu-id="9370f-248">**Analysis Services への HTTP 接続**</span><span class="sxs-lookup"><span data-stu-id="9370f-248">**HTTP Connections to Analysis Services**</span></span>  
  
 <span data-ttu-id="9370f-249">![Analysis Services への HTTP 接続](media/ssas-powershell-httpconnection.gif "Analysis Services への HTTP 接続")</span><span class="sxs-lookup"><span data-stu-id="9370f-249">![HTTP Connection to Analysis Services](media/ssas-powershell-httpconnection.gif "HTTP Connection to Analysis Services")</span></span>  
  
 <span data-ttu-id="9370f-250">Http 接続は、このトピックの手順を使用して http アクセス用にサーバーを構成した場合に役立ちます。[インターネットインフォメーションサービス &#40;IIS&#41; 8.0 の Analysis Services への Http アクセスの構成](instances/configure-http-access-to-analysis-services-on-iis-8-0.md)</span><span class="sxs-lookup"><span data-stu-id="9370f-250">HTTP connections are useful if you configured your server for HTTP access using the instructions in this topic: [Configure HTTP Access to Analysis Services on Internet Information Services &#40;IIS&#41; 8.0](instances/configure-http-access-to-analysis-services-on-iis-8-0.md)</span></span>  
  
 <span data-ttu-id="9370f-251">サーバーの URL がの場合 http://localhost/olap/msmdpump.dll 、接続は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="9370f-251">Assuming a server URL of http://localhost/olap/msmdpump.dll, a connection might look like the following:</span></span>  
  
```  
PS SQLSERVER\sqlas:> cd http_ds  
PS SQLSERVER\sqlas\http_ds:> $Url=Encode-SqlName "http://localhost/olap/msmdpump.dll"  
PS SQLSERVER\sqlas\http_ds:> cd $Url  
PS SQLSERVER\sqlas\http_ds\http%3A%2F%2Flocalhost%2olap%2msmdpump%2Edll:> dir  
```  
  
 <span data-ttu-id="9370f-252">アセンブリ、データベース、ロール、トレースの各コレクションを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9370f-252">You should see the following collections: Assemblies, Databases, Roles, and Traces.</span></span> <span data-ttu-id="9370f-253">これらのコレクションの内容を表示できない場合は、OLAP 仮想ディレクトリの認証設定を確認します。</span><span class="sxs-lookup"><span data-stu-id="9370f-253">If you cannot view the contents of these collections, check the authentication settings on the OLAP virtual directory.</span></span> <span data-ttu-id="9370f-254">匿名アクセスが無効になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9370f-254">Make sure that Anonymous Access is disabled.</span></span> <span data-ttu-id="9370f-255">Windows 認証を使用する場合は、Windows ユーザー アカウントが Analysis Services インスタンスに対する管理権限を持っていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9370f-255">If you are using Windows Authentication, be sure that your Windows user account has administrative permissions on the Analysis Services instance.</span></span>  
  
###  <a name="administer-the-service"></a><a name="bkmk_admin"></a><span data-ttu-id="9370f-256">サービスを管理する</span><span class="sxs-lookup"><span data-stu-id="9370f-256">Administer the Service</span></span>  
 <span data-ttu-id="9370f-257">サービスが実行されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9370f-257">Verify the service is running.</span></span> <span data-ttu-id="9370f-258">Analysis Services (MSSQLServerOLAPService) とデータベース エンジンを含む、SQL Server サービスの状態、名前、表示名が返されます。</span><span class="sxs-lookup"><span data-stu-id="9370f-258">Returns status, name, and display name for SQL Server services, including Analysis Services (MSSQLServerOLAPService) and the Database Engine.</span></span>  
  
```powershell
Get-Service mssql*  
```  
  
 <span data-ttu-id="9370f-259">プロセス ID、ハンドル数、メモリ使用量を含むプロセスのプロパティが返されます。</span><span class="sxs-lookup"><span data-stu-id="9370f-259">Returns properties about a process, including process ID, handle count, and memory usage:</span></span>  
  
```powershell
Get-Process msmdsrv  
```  
  
 <span data-ttu-id="9370f-260">管理者シェルから次のコマンドレットを実行すると、サービスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="9370f-260">Restarts the service when you issue the following cmdlet from the administrator shell:</span></span>  
  
```powershell
Restart-Service mssqlserverolapservice  
```  
  
###  <a name="get-help-for-analysis-services-powershell"></a><a name="bkmk_help"></a><span data-ttu-id="9370f-261">PowerShell の Analysis Services に関するヘルプを表示する</span><span class="sxs-lookup"><span data-stu-id="9370f-261">Get Help for Analysis Services PowerShell</span></span>  
 <span data-ttu-id="9370f-262">次のコマンドレットを使用して、コマンドレットの機能を確認したり、サービス、プロセス、およびオブジェクトの詳細情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="9370f-262">Use any of the following cmdlets to verify cmdlet availability and to get more information about services, processes, and objects.</span></span>  
  
1.  <span data-ttu-id="9370f-263">`Get-Help` は、Analysis Services コマンドレットの組み込みのヘルプ (例を含む) を返します。</span><span class="sxs-lookup"><span data-stu-id="9370f-263">`Get-Help` returns the built-in help for an Analysis Services cmdlet, including examples:</span></span>  
  
    ```powershell
    Get-Help invoke-ascmd -Examples  
    ```  
  
2.  <span data-ttu-id="9370f-264">`Get-Command` は、11 個の Analysis Services PowerShell コマンドレットの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="9370f-264">`Get-Command` returns a list of the eleven Analysis Services PowerShell cmdlets:</span></span>  
  
    ```powershell
    Get-Command -module SQLASCmdlets  
    ```  
  
3.  <span data-ttu-id="9370f-265">`Get-Member` は、サービスまたはプロセスのプロパティやメソッドを返します。</span><span class="sxs-lookup"><span data-stu-id="9370f-265">`Get-Member` returns properties or methods of a service or process.</span></span>  
  
    ```powershell
    Get-Service mssqlserverolapservice | Get-Member -Type Property  
    ```  
  
    ```powershell
    Get-Service mssqlserverolapservice | Get-Member -Type Method  
    ```  
  
    ```powershell
    Get-Process msmdsrv | Get-Member -Type Property  
    ```  
  
4.  <span data-ttu-id="9370f-266">`Get-Member` には、サーバー インスタンスを指定する SQLAS プロバイダーを使用してオブジェクトのプロパティやメソッド (サーバー オブジェクトの AMO メソッドなど) を返すという使用方法もあります。</span><span class="sxs-lookup"><span data-stu-id="9370f-266">`Get-Member` can also be used to return properties or methods of an object (for example, AMO methods on the server object) using the SQLAS provider to specify the server instance.</span></span>  
  
    ```
    PS SQLSERVER:\sqlas\localhost\default > $serverObj = New-Object Microsoft.AnalysisServices.Server  
    PS SQLSERVER:\sqlas\localhost\default > $serverObj = | Get-Member -Type Method  
    ```  
  
5.  <span data-ttu-id="9370f-267">`Get-PSdrive` は、現在インストールされているプロバイダーの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="9370f-267">`Get-PSdrive` returns a list of the providers that are currently installed.</span></span> <span data-ttu-id="9370f-268">SQLPS モジュールをインポートしてあると、`SQLServer` プロバイダーが一覧に表示されます (SQLAS は SQLServer プロバイダーの一部であり、個別に一覧には表示されません)。</span><span class="sxs-lookup"><span data-stu-id="9370f-268">If you imported the SQLPS module, you will see the `SQLServer` provider in the list (SQLAS is part of the SQLServer provider and never appears separately in the list):</span></span>  
  
    ```powershell
    Get-PSDrive  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9370f-269">参照</span><span class="sxs-lookup"><span data-stu-id="9370f-269">See Also</span></span>  
 <span data-ttu-id="9370f-270">[SQL Server PowerShell のインストール](../database-engine/install-windows/install-sql-server-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="9370f-270">[Install SQL Server PowerShell](../database-engine/install-windows/install-sql-server-powershell.md) </span></span>  
 <span data-ttu-id="9370f-271">[PowerShell を使用したテーブルモデルの管理 (ブログ)](https://go.microsoft.com/fwlink/?linkID=227685) </span><span class="sxs-lookup"><span data-stu-id="9370f-271">[Manage Tabular Models Using PowerShell (blog)](https://go.microsoft.com/fwlink/?linkID=227685) </span></span>  
 [<span data-ttu-id="9370f-272">インターネット インフォメーション サービス (IIS) 8.0 上の Analysis Services への HTTP アクセスの構成</span><span class="sxs-lookup"><span data-stu-id="9370f-272">Configure HTTP Access to Analysis Services on Internet Information Services &#40;IIS&#41; 8.0</span></span>](instances/configure-http-access-to-analysis-services-on-iis-8-0.md)  
  
  
