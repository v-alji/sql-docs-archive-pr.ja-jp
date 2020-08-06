---
title: sqlcmd ユーティリティ | Microsoft Docs
ms.custom: ''
ms.date: 11/29/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- statements [SQL Server], command prompt
- QUIT command
- Transact-SQL statements, command prompt
- EXIT command
- sqlcmd commands
- ED command
- sqlcmd utility
- command prompt utilities [SQL Server], sqlcmd
- '!! command'
- stored procedures [SQL Server], command prompt
- system stored procedures [SQL Server], command prompt
- sqlcmd utility, about sqlcmd utility
- scripts [SQL Server], command prompt
- RESET command
- GO command
ms.assetid: e1728707-5215-4c04-8320-e36f161b834a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9fbe5a3dcefb2218543e015dad71acfe79aea8e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739018"
---
# <a name="sqlcmd-utility"></a><span data-ttu-id="9f457-102">sqlcmd ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="9f457-102">sqlcmd Utility</span></span>
  <span data-ttu-id="9f457-103">`sqlcmd`ユーティリティを使用すると、 [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメント、システムプロシージャ、およびスクリプトファイルを、コマンドプロンプト、SQLCMD モードの**クエリエディター** 、Windows スクリプトファイル、またはエージェントジョブのオペレーティングシステム (Cmd.exe) ジョブステップで入力でき [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="9f457-103">The `sqlcmd` utility lets you enter [!INCLUDE[tsql](../includes/tsql-md.md)] statements, system procedures, and script files at the command prompt, in **Query Editor** in SQLCMD mode, in a Windows script file or in an operating system (Cmd.exe) job step of a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent job.</span></span> <span data-ttu-id="9f457-104">このユーティリティでは、ODBC を使用して [!INCLUDE[tsql](../includes/tsql-md.md)] バッチを実行します。</span><span class="sxs-lookup"><span data-stu-id="9f457-104">This utility uses ODBC to execute [!INCLUDE[tsql](../includes/tsql-md.md)] batches.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]<span data-ttu-id="9f457-105">は、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] **クエリエディター**の標準モードと SQLCMD モードでの実行に SqlClient を使用します。</span><span class="sxs-lookup"><span data-stu-id="9f457-105">uses the [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]SqlClient for execution in regular and SQLCMD mode in **Query Editor**.</span></span> <span data-ttu-id="9f457-106">コマンド ラインから `sqlcmd` を実行する場合、`sqlcmd` では ODBC ドライバーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-106">When `sqlcmd` is run from the command line, `sqlcmd` uses the ODBC driver.</span></span> <span data-ttu-id="9f457-107">同じクエリでも、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] の SQLCMD モードで実行する場合と `sqlcmd` ユーティリティで実行する場合とでは、適用される既定のオプションが異なるので、動作も異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9f457-107">Because different default options may apply, you might see different behavior when you execute the same query in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] in SQLCMD Mode and in the `sqlcmd` utility.</span></span>  
  
 <span data-ttu-id="9f457-108">現在、`sqlcmd` ではコマンド ライン オプションと値の間に空白を入れる必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9f457-108">Currently, `sqlcmd` does not require a space between the command line option and the value.</span></span> <span data-ttu-id="9f457-109">ただし、将来のリリースでは、コマンド ライン オプションと値の間に空白が必要になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9f457-109">However, in a future release, a space may be required between the command line option and the value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f457-110">構文</span><span class="sxs-lookup"><span data-stu-id="9f457-110">Syntax</span></span>  
  
```  
  
   sqlcmd  
   -a  
   packet_size  
   -A (dedicated administrator connection)  
-b (terminate batch job if there is an error)  
-cbatch_terminator-C (trust the server certificate)  
-ddb_name-e (echo input)  
-E (use trusted connection)  
-fcodepage | i:codepage[,o:codepage] | o:codepage[,i:codepage]  
-hrows_per_header-Hworkstation_name-iinput_file-I (enable quoted identifiers)  
-k[1 | 2] (remove or replace control characters)  
-Kapplication_intent-llogin_timeout-L[c] (list servers, optional clean output)  
-merror_level-Mmultisubnet_failover-N (encrypt connection)  
-ooutput_file-p[1] (print statistics, optional colon format)  
-Ppassword-q "cmdline query"-Q "cmdline query" (and exit)  
-r[0 | 1] (msgs to stderr)  
-R (use client regional settings)  
-scol_separator-S [protocol:]server[\instance_name][,port]  
-tquery_timeout-u (unicode output file)  
-Ulogin_id-vvar = "value"-Verror_severity_level-wcolumn_width-W (remove trailing spaces)  
-x (disable variable substitution)  
-X[1] (disable commands, startup script, environment variables and optional exit)  
-yvariable_length_type_display_width-Yfixed_length_type_display_width-znew_password -Znew_password (and exit)  
  
-? (usage)  
```  
  
## <a name="command-line-options"></a><span data-ttu-id="9f457-111">コマンド ライン オプション</span><span class="sxs-lookup"><span data-stu-id="9f457-111">Command-line Options</span></span>  
 <span data-ttu-id="9f457-112">**ログイン関連のオプション**</span><span class="sxs-lookup"><span data-stu-id="9f457-112">**Login-Related Options**</span></span>  
  <span data-ttu-id="9f457-113">**-A**</span><span class="sxs-lookup"><span data-stu-id="9f457-113">**-A**</span></span>  
 <span data-ttu-id="9f457-114">専用管理者接続 (DAC) を使用して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] にログインします。</span><span class="sxs-lookup"><span data-stu-id="9f457-114">Logs in to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] with a Dedicated Administrator Connection (DAC).</span></span> <span data-ttu-id="9f457-115">この種類の接続は、サーバーのトラブルシューティングで使用されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-115">This kind of connection is used to troubleshoot a server.</span></span> <span data-ttu-id="9f457-116">またこの接続は、DAC をサポートしているサーバー コンピューターでのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="9f457-116">This will only work with server computers that support DAC.</span></span> <span data-ttu-id="9f457-117">DAC が使用できない場合は、`sqlcmd` はエラー メッセージを生成して終了します。</span><span class="sxs-lookup"><span data-stu-id="9f457-117">If DAC is not available, `sqlcmd` generates an error message and then exits.</span></span> <span data-ttu-id="9f457-118">DAC の詳細については、「 [データベース管理者用の診断接続](../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f457-118">For more information about DAC, see [Diagnostic Connection for Database Administrators](../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md).</span></span>  
  
 <span data-ttu-id="9f457-119">**-C**</span><span class="sxs-lookup"><span data-stu-id="9f457-119">**-C**</span></span>  
 <span data-ttu-id="9f457-120">クライアントでこのスイッチを使用して、サーバーの証明書を検証せずに暗黙的に信頼するようにクライアントを構成できます。</span><span class="sxs-lookup"><span data-stu-id="9f457-120">This switch is used by the client to configure it to implicitly trust the server certificate without validation.</span></span> <span data-ttu-id="9f457-121">このオプションは、ADO.NET オプションの `TRUSTSERVERCERTIFICATE = true`と同等です。</span><span class="sxs-lookup"><span data-stu-id="9f457-121">This option is equivalent to the ADO.NET option `TRUSTSERVERCERTIFICATE = true`.</span></span>  
  
 <span data-ttu-id="9f457-122">**-d** _db_name_</span><span class="sxs-lookup"><span data-stu-id="9f457-122">**-d** _db_name_</span></span>  
 <span data-ttu-id="9f457-123">を `USE` 開始するときに*db_name*ステートメントを発行 `sqlcmd` します。</span><span class="sxs-lookup"><span data-stu-id="9f457-123">Issues a `USE` *db_name* statement when you start `sqlcmd`.</span></span> <span data-ttu-id="9f457-124">このオプションにより、`sqlcmd` スクリプト変数 SQLCMDDBNAME が設定されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-124">This option sets the `sqlcmd` scripting variable SQLCMDDBNAME.</span></span> <span data-ttu-id="9f457-125">これにより初期データベースが指定されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-125">This specifies the initial database.</span></span> <span data-ttu-id="9f457-126">既定値は、ログインの既定データベースのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="9f457-126">The default is your login's default-database property.</span></span> <span data-ttu-id="9f457-127">データベースが存在しない場合は、エラー メッセージが生成され、`sqlcmd` は終了します。</span><span class="sxs-lookup"><span data-stu-id="9f457-127">If the database does not exist, an error message is generated and `sqlcmd` exits.</span></span>  
  
 <span data-ttu-id="9f457-128">**-l** _login_timeout_</span><span class="sxs-lookup"><span data-stu-id="9f457-128">**-l** _login_timeout_</span></span>  
 <span data-ttu-id="9f457-129">サーバーに接続を試みたときに、`sqlcmd` が ODBC ドライバーにログインするまでのタイムアウトを秒数で指定します。</span><span class="sxs-lookup"><span data-stu-id="9f457-129">Specifies the number of seconds before a `sqlcmd` login to the ODBC driver times out when you try to connect to a server.</span></span> <span data-ttu-id="9f457-130">このオプションにより、`sqlcmd` スクリプト変数 SQLCMDLOGINTIMEOUT が設定されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-130">This option sets the `sqlcmd` scripting variable SQLCMDLOGINTIMEOUT.</span></span> <span data-ttu-id="9f457-131">`sqlcmd` でのログインに関する既定のタイムアウトは 8 秒です。</span><span class="sxs-lookup"><span data-stu-id="9f457-131">The default time-out for login to `sqlcmd` is eight seconds.</span></span> <span data-ttu-id="9f457-132">ログイン タイムアウトは、0 ～ 65,534 の数値にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9f457-132">The login time-out must be a number between 0 and 65534.</span></span> <span data-ttu-id="9f457-133">指定した値が数値以外の場合、または範囲外の場合、`sqlcmd` はエラー メッセージを生成します。</span><span class="sxs-lookup"><span data-stu-id="9f457-133">If the value supplied is not numeric or does not fall into that range, `sqlcmd` generates an error message.</span></span> <span data-ttu-id="9f457-134">この値に 0 を指定すると、タイムアウトは無制限になります。</span><span class="sxs-lookup"><span data-stu-id="9f457-134">A value of 0 specifies time-out to be infinite.</span></span>  
  
 <span data-ttu-id="9f457-135">**-E**</span><span class="sxs-lookup"><span data-stu-id="9f457-135">**-E**</span></span>  
 <span data-ttu-id="9f457-136">ユーザー名とパスワードを使用せずにセキュリティ接続を使用して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] にログオンします。</span><span class="sxs-lookup"><span data-stu-id="9f457-136">Uses a trusted connection instead of using a user name and password to log on to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9f457-137">既定では、-E を指定しないと、`sqlcmd` ではセキュリティ接続オプションが使用されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-137">By default, without -E specified, `sqlcmd` uses the trusted connection option.</span></span>  
  
 <span data-ttu-id="9f457-138">**-E** オプションを使用すると、SQLCMDPASSWORD などのユーザー名とパスワード用に使用できる環境変数の設定が無視されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-138">The **-E** option ignores possible user name and password environment variable settings such as SQLCMDPASSWORD.</span></span> <span data-ttu-id="9f457-139">**-E** オプションが **-U** オプションまたは **-P** オプションと共に使用されると、エラー メッセージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-139">If the **-E** option is used together with the **-U** option or the **-P** option, an error message is generated.</span></span>  
  
 <span data-ttu-id="9f457-140">**-H** _workstation_name_</span><span class="sxs-lookup"><span data-stu-id="9f457-140">**-H** _workstation_name_</span></span>  
 <span data-ttu-id="9f457-141">ワークステーション名です。</span><span class="sxs-lookup"><span data-stu-id="9f457-141">A workstation name.</span></span> <span data-ttu-id="9f457-142">このオプションにより、`sqlcmd` スクリプト変数 SQLCMDWORKSTATION が設定されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-142">This option sets the `sqlcmd` scripting variable SQLCMDWORKSTATION.</span></span> <span data-ttu-id="9f457-143">ワークステーション名は **sys.processes** カタログ ビューの **hostname** 列に一覧表示され、ストアド プロシージャ **sp_who** を使用して取得できます。</span><span class="sxs-lookup"><span data-stu-id="9f457-143">The workstation name is listed in the **hostname** column of the **sys.processes** catalog view and can be returned using the stored procedure **sp_who**.</span></span> <span data-ttu-id="9f457-144">このオプションが指定されていない場合の既定値は、現在のコンピューター名になります。</span><span class="sxs-lookup"><span data-stu-id="9f457-144">If this option is not specified, the default is the current computer name.</span></span> <span data-ttu-id="9f457-145">この名前は、異なる `sqlcmd` セッションを識別する場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="9f457-145">This name can be used to identify different `sqlcmd` sessions.</span></span>  
  
 <span data-ttu-id="9f457-146">**-K** _application_intent_</span><span class="sxs-lookup"><span data-stu-id="9f457-146">**-K** _application_intent_</span></span>  
 <span data-ttu-id="9f457-147">アプリケーションがサーバーに接続するときのワークロードのタイプを宣言します。</span><span class="sxs-lookup"><span data-stu-id="9f457-147">Declares the application workload type when connecting to a server.</span></span> <span data-ttu-id="9f457-148">現在サポートされている値は、 **ReadOnly**だけです。</span><span class="sxs-lookup"><span data-stu-id="9f457-148">The only currently supported value is **ReadOnly**.</span></span> <span data-ttu-id="9f457-149">**-K** を指定しない場合、sqlcmd ユーティリティでは AlwaysOn 可用性グループのセカンダリ レプリカへの接続がサポートされません。</span><span class="sxs-lookup"><span data-stu-id="9f457-149">If **-K** is not specified, the sqlcmd utility will not support connectivity to a secondary replica in an AlwaysOn availability group.</span></span> <span data-ttu-id="9f457-150">詳細については、「[アクティブなセカンダリ: 読み取り可能なセカンダリレプリカ](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f457-150">For more information, see [Active Secondaries: Readable Secondary Replicas](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).</span></span>  
  
 <span data-ttu-id="9f457-151">`-M`*multisubnet_failover*</span><span class="sxs-lookup"><span data-stu-id="9f457-151">`-M` *multisubnet_failover*</span></span>  
 <span data-ttu-id="9f457-152">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 可用性グループまたは [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] フェールオーバー クラスター インスタンスの可用性グループ リスナーに接続する際には、必ず `-M` を指定してください。</span><span class="sxs-lookup"><span data-stu-id="9f457-152">Always specify `-M` when connecting to the availability group listener of a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] availability group or a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Failover Cluster Instance.</span></span> <span data-ttu-id="9f457-153">`-M` を指定すると、(現在) アクティブなサーバーを迅速に検出して接続できます。</span><span class="sxs-lookup"><span data-stu-id="9f457-153">`-M` provides for faster detection of and connection to the (currently) active server.</span></span> <span data-ttu-id="9f457-154">`-M` が指定されていない場合、`-M` は無効になります。</span><span class="sxs-lookup"><span data-stu-id="9f457-154">If `-M` is not specified, `-M` is off.</span></span> <span data-ttu-id="9f457-155">の詳細について [!INCLUDE[ssHADR](../includes/sshadr-md.md)] は、「[可用性グループリスナー、クライアント接続、およびアプリケーションのフェールオーバー &#40;SQL Server&#41;](../database-engine/listeners-client-connectivity-application-failover.md)、[可用性グループの作成と構成 &#40;SQL Server ](../database-engine/availability-groups/windows/creation-and-configuration-of-availability-groups-sql-server.md)&#41;、[フェールオーバークラスタリングと AlwaysOn 可用性グループ](../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md)&#40;SQL Server&#41;、および[アクティブなセカンダリ: 読み取り可能なセカンダリレプリカ](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f457-155">For more information about [!INCLUDE[ssHADR](../includes/sshadr-md.md)], see [Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../database-engine/listeners-client-connectivity-application-failover.md), [Creation and Configuration of Availability Groups &#40;SQL Server&#41;](../database-engine/availability-groups/windows/creation-and-configuration-of-availability-groups-sql-server.md), [Failover Clustering and AlwaysOn Availability Groups &#40;SQL Server&#41;](../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md), and [Active Secondaries: Readable Secondary Replicas](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) .</span></span>  
  
 <span data-ttu-id="9f457-156">**-N**</span><span class="sxs-lookup"><span data-stu-id="9f457-156">**-N**</span></span>  
 <span data-ttu-id="9f457-157">クライアントでこのスイッチを使用して、暗号化された接続を要求できます。</span><span class="sxs-lookup"><span data-stu-id="9f457-157">This switch is used by the client to request an encrypted connection.</span></span>  
  
 <span data-ttu-id="9f457-158">**-P** _password_</span><span class="sxs-lookup"><span data-stu-id="9f457-158">**-P** _password_</span></span>  
 <span data-ttu-id="9f457-159">ユーザーが指定するパスワードです。</span><span class="sxs-lookup"><span data-stu-id="9f457-159">Is a user-specified password.</span></span> <span data-ttu-id="9f457-160">パスワードでは大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-160">Passwords are case sensitive.</span></span> <span data-ttu-id="9f457-161">-U オプションを使用して **-P**オプションを使用せず、sqlcmdpassword 環境変数が設定されていない場合、は `sqlcmd` ユーザーにパスワードの入力を求めます。</span><span class="sxs-lookup"><span data-stu-id="9f457-161">If the -U option is used and the **-P** option is not used, and the SQLCMDPASSWORD environment variable has not been set, `sqlcmd` prompts the user for a password.</span></span> <span data-ttu-id="9f457-162">**-P**オプションをコマンドプロンプトの最後に使用する場合は、パスワードを使用しないで `sqlcmd` 既定のパスワード (NULL) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-162">If the **-P** option is used at the end of the command prompt without a password `sqlcmd` uses the default password (NULL).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9f457-163">空白のパスワードは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="9f457-163">Do not use a blank password.</span></span> <span data-ttu-id="9f457-164">強力なパスワードを使用してください。</span><span class="sxs-lookup"><span data-stu-id="9f457-164">Use a strong password.</span></span> <span data-ttu-id="9f457-165">詳細については、「 [Strong Passwords](../relational-databases/security/strong-passwords.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f457-165">For more information, see [Strong Passwords](../relational-databases/security/strong-passwords.md).</span></span>  
  
 <span data-ttu-id="9f457-166">パスワード プロンプトは、次のようにパスワード プロンプトをコンソールに出力することによって表示されます。 `Password:`</span><span class="sxs-lookup"><span data-stu-id="9f457-166">The password prompt is displayed by printing the password prompt to the console, as follows: `Password:`</span></span>  
  
 <span data-ttu-id="9f457-167">ユーザーが行った入力は表示されません。</span><span class="sxs-lookup"><span data-stu-id="9f457-167">User input is hidden.</span></span> <span data-ttu-id="9f457-168">つまり、入力時には何も表示されず、カーソルが移動しません。</span><span class="sxs-lookup"><span data-stu-id="9f457-168">This means that nothing is displayed and the cursor stays in position.</span></span>  
  
 <span data-ttu-id="9f457-169">SQLCMDPASSWORD 環境変数を使用して、現在のセッションに既定のパスワードを設定できます。</span><span class="sxs-lookup"><span data-stu-id="9f457-169">The SQLCMDPASSWORD environment variable lets you set a default password for the current session.</span></span> <span data-ttu-id="9f457-170">したがって、パスワードをバッチ ファイルにハード コードする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9f457-170">Therefore, passwords do not have to be hard-coded into batch files.</span></span>  
  
 <span data-ttu-id="9f457-171">次の例では、まずコマンド プロンプトで SQLCMDPASSWORD 変数を設定してから `sqlcmd` ユーティリティにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="9f457-171">The following example first sets the SQLCMDPASSWORD variable at the command prompt and then accesses the `sqlcmd` utility.</span></span> <span data-ttu-id="9f457-172">コマンド プロンプトに、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="9f457-172">At the command prompt, type:</span></span>  
  
 `SET SQLCMDPASSWORD= p@a$$w0rd`  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9f457-173">このとき、コンピューターのモニターにはパスワードが表示されてしまうので、注意してください。</span><span class="sxs-lookup"><span data-stu-id="9f457-173">The password will be visible to anyone who can see your computer monitor.</span></span>  
  
 <span data-ttu-id="9f457-174">次のコマンド プロンプトが表示されたら、次のように入力します:</span><span class="sxs-lookup"><span data-stu-id="9f457-174">At the following command prompt, type:</span></span>  
  
 `sqlcmd`  
  
 <span data-ttu-id="9f457-175">ユーザー名とパスワードの組み合わせが正しくない場合は、エラー メッセージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-175">If the user name and password combination is incorrect, an error message is generated.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f457-176">OSQLPASSWORD 環境変数は旧バージョンとの互換性を維持しています。</span><span class="sxs-lookup"><span data-stu-id="9f457-176">The OSQLPASSWORD environment variable has been kept for backward compatibility.</span></span> <span data-ttu-id="9f457-177">SQLCMDPASSWORD 環境変数は OSQLPASSWORD 環境変数よりも優先されます。つまり `sqlcmd` 、と**osql**を相互に干渉することなく使用でき、古いスクリプトは引き続き機能します。</span><span class="sxs-lookup"><span data-stu-id="9f457-177">The SQLCMDPASSWORD environment variable takes precedence over the OSQLPASSWORD environment variable; this means that `sqlcmd` and **osql** can be used next to each other without interference and that old scripts will continue to work.</span></span>  
  
 <span data-ttu-id="9f457-178">**-P** オプションが **-E** オプションと共に使用されると、エラー メッセージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-178">If the **-P** option is used with the **-E** option, an error message is generated.</span></span>  
  
 <span data-ttu-id="9f457-179">**-P** オプションの後に複数の引数があると、エラー メッセージが生成され、プログラムが終了します。</span><span class="sxs-lookup"><span data-stu-id="9f457-179">If the **-P** option is followed by more than one argument, an error message is generated and the program exits.</span></span>  
  
 <span data-ttu-id="9f457-180">**-S** [*protocol*:]*サーバー*[ **\\** _instance_name_] [**,**_port_]</span><span class="sxs-lookup"><span data-stu-id="9f457-180">**-S** [*protocol*:]*server*[**\\**_instance_name_][**,**_port_]</span></span>  
 <span data-ttu-id="9f457-181">接続先となる [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="9f457-181">Specifies the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to which to connect.</span></span> <span data-ttu-id="9f457-182">このオプションにより、`sqlcmd` スクリプト変数 SQLCMDSERVER が設定されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-182">It sets the `sqlcmd` scripting variable SQLCMDSERVER.</span></span>  
  
 <span data-ttu-id="9f457-183">そのサーバー コンピューター上の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の既定のインスタンスに接続するには、*server_name* を指定します。</span><span class="sxs-lookup"><span data-stu-id="9f457-183">Specify *server_name* to connect to the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on that server computer.</span></span> <span data-ttu-id="9f457-184">*server_name* **\\** サーバーコンピューター上のの名前付きインスタンスに接続するには server_name [ _instance_name_ ] を指定し [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="9f457-184">Specify *server_name* [ **\\**_instance_name_ ] to connect to a named instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on that server computer.</span></span> <span data-ttu-id="9f457-185">サーバー コンピューターを指定しない場合、`sqlcmd` は、ローカル コンピューター上にある [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の既定のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="9f457-185">If no server computer is specified, `sqlcmd` connects to the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on the local computer.</span></span> <span data-ttu-id="9f457-186">このオプションは `sqlcmd` 、ネットワーク上のリモートコンピューターからを実行する場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="9f457-186">This option is required when you execute `sqlcmd` from a remote computer on the network.</span></span>  
  
 <span data-ttu-id="9f457-187">*プロトコル*には、 `tcp` (tcp/ip)、 `lpc` (共有メモリ)、または `np` (名前付きパイプ) を指定できます。</span><span class="sxs-lookup"><span data-stu-id="9f457-187">*protocol* can be `tcp` (TCP/IP), `lpc` (shared memory), or `np` (named pipes).</span></span>  
  
 <span data-ttu-id="9f457-188">を開始するときに*server_name* [instance_name] を指定しない場合 **\\** _instance_name_ `sqlcmd` 、は [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sqlcmdserver 環境変数を確認して使用します。</span><span class="sxs-lookup"><span data-stu-id="9f457-188">If you do not specify a *server_name* [ **\\**_instance_name_ ] when you start `sqlcmd`, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] checks for and uses the SQLCMDSERVER environment variable.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f457-189">OSQLSERVER 環境変数は旧バージョンとの互換性を維持しています。</span><span class="sxs-lookup"><span data-stu-id="9f457-189">The OSQLSERVER environment variable has been kept for backward compatibility.</span></span> <span data-ttu-id="9f457-190">SQLCMDSERVER 環境変数は、OSQLSERVER 環境変数よりも優先されます。つまり `sqlcmd` 、と**osql**を相互に干渉することなく使用でき、古いスクリプトは引き続き機能します。</span><span class="sxs-lookup"><span data-stu-id="9f457-190">The SQLCMDSERVER environment variable takes precedence over the OSQLSERVER environment variable; this means that `sqlcmd` and **osql** can be used next to each other without interference and that old scripts will continue to work.</span></span>  
  
 <span data-ttu-id="9f457-191">**-U** _login_id_</span><span class="sxs-lookup"><span data-stu-id="9f457-191">**-U** _login_id_</span></span>  
 <span data-ttu-id="9f457-192">ユーザーのログイン ID です。</span><span class="sxs-lookup"><span data-stu-id="9f457-192">Is the user login ID.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f457-193">OSQLUSER 環境変数は旧バージョンとの互換性を維持しています。</span><span class="sxs-lookup"><span data-stu-id="9f457-193">The OSQLUSER environment variable is available for backward compatibility.</span></span> <span data-ttu-id="9f457-194">SQLCMDUSER 環境変数は OSQLUSER 環境変数よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-194">The SQLCMDUSER environment variable takes precedence over the OSQLUSER environment variable.</span></span> <span data-ttu-id="9f457-195">これは `sqlcmd` 、と**osql**を相互に干渉せずに使用できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="9f457-195">This means that `sqlcmd` and **osql** can be used next to each other without interference.</span></span> <span data-ttu-id="9f457-196">また、既存の **osql** スクリプトは引き続き実行することができます。</span><span class="sxs-lookup"><span data-stu-id="9f457-196">It also means that existing **osql** scripts will continue to work.</span></span>  
  
 <span data-ttu-id="9f457-197">**-U**オプションも **-P**オプションも指定しない場合、は `sqlcmd` Windows 認証モードを使用して接続を試み [!INCLUDE[msCoName](../includes/msconame-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="9f457-197">If neither the **-U** option nor the **-P** option is specified, `sqlcmd` tries to connect by using [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows Authentication mode.</span></span> <span data-ttu-id="9f457-198">認証は `sqlcmd` を実行しているユーザーの Windows アカウントに基づきます。</span><span class="sxs-lookup"><span data-stu-id="9f457-198">Authentication is based on the Windows account of the user who is running `sqlcmd`.</span></span>  
  
 <span data-ttu-id="9f457-199">**-U** オプションが **-E** オプション (このトピックの後半で説明) と同時に使用されると、エラー メッセージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-199">If the **-U** option is used with the **-E** option (described later in this topic), an error message is generated.</span></span> <span data-ttu-id="9f457-200">**-U** オプションの後に複数の引数があると、エラー メッセージが生成され、プログラムが終了します。</span><span class="sxs-lookup"><span data-stu-id="9f457-200">If the **-U** option is followed by more than one argument, an error message is generated and the program exits.</span></span>  
  
 <span data-ttu-id="9f457-201">**-z** _new_password_</span><span class="sxs-lookup"><span data-stu-id="9f457-201">**-z** _new_password_</span></span>  
 <span data-ttu-id="9f457-202">パスワードの変更:</span><span class="sxs-lookup"><span data-stu-id="9f457-202">Change password:</span></span>  
  
 `sqlcmd -U someuser -P s0mep@ssword -z a_new_p@a$$w0rd`  
  
 <span data-ttu-id="9f457-203">**-Z** _new_password_</span><span class="sxs-lookup"><span data-stu-id="9f457-203">**-Z** _new_password_</span></span>  
 <span data-ttu-id="9f457-204">パスワードの変更と終了:</span><span class="sxs-lookup"><span data-stu-id="9f457-204">Change password and exit:</span></span>  
  
 `sqlcmd -U someuser -P s0mep@ssword -Z a_new_p@a$$w0rd`  
  
 <span data-ttu-id="9f457-205">**入力または出力のオプション**</span><span class="sxs-lookup"><span data-stu-id="9f457-205">**Input/Output Options**</span></span>  
  <span data-ttu-id="9f457-206">**-f** _codepage_ | **i:** _codepage_[ **,o:** _codepage_] | **o:** _codepage_[ **,i:** _codepage_]</span><span class="sxs-lookup"><span data-stu-id="9f457-206">**-f** _codepage_ | **i:**_codepage_[**,o:**_codepage_] | **o:**_codepage_[**,i:**_codepage_]</span></span>  
 <span data-ttu-id="9f457-207">入力と出力のコード ページを指定します。</span><span class="sxs-lookup"><span data-stu-id="9f457-207">Specifies the input and output code pages.</span></span> <span data-ttu-id="9f457-208">コード ページ番号は、インストールされた Windows コード ページを指定する数値です。</span><span class="sxs-lookup"><span data-stu-id="9f457-208">The codepage number is a numeric value that specifies an installed Windows code page.</span></span>  
  
 <span data-ttu-id="9f457-209">コード ページには次の変換規則があります。</span><span class="sxs-lookup"><span data-stu-id="9f457-209">Code-page conversion rules:</span></span>  
  
-   <span data-ttu-id="9f457-210">コード ページを指定しないと、入力ファイルが変換不要の Unicode ファイルでない限り、`sqlcmd` では、入力ファイルと出力ファイルの両方に現在のコード ページが使用されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-210">If no code pages are specified, `sqlcmd` will use the current code page for both input and output files, unless the input file is a Unicode file, in which case no conversion is required.</span></span>  
  
-   <span data-ttu-id="9f457-211">`sqlcmd` では、ビッグ エンディアンとリトル エンディアンの両方の Unicode 入力ファイルが自動的に認識されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-211">`sqlcmd` automatically recognizes both big-endian and little-endian Unicode input files.</span></span> <span data-ttu-id="9f457-212">**-u** オプションを指定すると、出力は常にリトル エンディアン Unicode になります。</span><span class="sxs-lookup"><span data-stu-id="9f457-212">If the **-u** option has been specified, the output will always be little-endian Unicode.</span></span>  
  
-   <span data-ttu-id="9f457-213">出力ファイルを指定しないと、出力コード ページはコンソールのコード ページになります。</span><span class="sxs-lookup"><span data-stu-id="9f457-213">If no output file is specified, the output code page will be the console code page.</span></span> <span data-ttu-id="9f457-214">その結果、コンソールに出力が正しく表示されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-214">This enables the output to be displayed correctly on the console.</span></span>  
  
-   <span data-ttu-id="9f457-215">複数の入力ファイルの場合、同じコード ページが指定されているものと見なされます。</span><span class="sxs-lookup"><span data-stu-id="9f457-215">Multiple input files are assumed to be of the same code page.</span></span> <span data-ttu-id="9f457-216">Unicode 入力ファイルと Unicode 以外の入力ファイルを混在させることができます。</span><span class="sxs-lookup"><span data-stu-id="9f457-216">Unicode and non-Unicode input files can be mixed.</span></span>  
  
 <span data-ttu-id="9f457-217">Cmd.exe のコード ページを確認するには、コマンド プロンプトに「`chcp`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="9f457-217">Enter `chcp` at the command prompt to verify the code page of Cmd.exe.</span></span>  
  
 <span data-ttu-id="9f457-218">**-i** _input_file_[**、**_input_file2_...]</span><span class="sxs-lookup"><span data-stu-id="9f457-218">**-i** _input_file_[**,**_input_file2_...]</span></span>  
 <span data-ttu-id="9f457-219">SQL ステートメントまたはストアド プロシージャのバッチを含むファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="9f457-219">Identifies the file that contains a batch of SQL statements or stored procedures.</span></span> <span data-ttu-id="9f457-220">複数のファイルを指定すると、それらのファイルは順番に読み取られて処理されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-220">Multiple files may be specified that will be read and processed in order.</span></span> <span data-ttu-id="9f457-221">ファイル名とファイル名の間には空白を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="9f457-221">Do not use any spaces between file names.</span></span> <span data-ttu-id="9f457-222">`sqlcmd` により、最初に、指定したすべてのファイルが存在しているかどうかがチェックされます。</span><span class="sxs-lookup"><span data-stu-id="9f457-222">`sqlcmd` will first check to see whether all the specified files exist.</span></span> <span data-ttu-id="9f457-223">1 つ以上のファイルが存在していない場合は、`sqlcmd` は終了します。</span><span class="sxs-lookup"><span data-stu-id="9f457-223">If one or more files do not exist, `sqlcmd` will exit.</span></span> <span data-ttu-id="9f457-224">-i と -Q/-q オプションは同時に使用できません。</span><span class="sxs-lookup"><span data-stu-id="9f457-224">The -i and the -Q/-q options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="9f457-225">パスの例:</span><span class="sxs-lookup"><span data-stu-id="9f457-225">Path examples:</span></span>  
  
 <span data-ttu-id="9f457-226">**-i**C: \\<ファイル名\></span><span class="sxs-lookup"><span data-stu-id="9f457-226">**-i** C:\\<filename\></span></span>  
  
 <span data-ttu-id="9f457-227">**-i** \\ \\<Server \> \\<$>\\<ファイル名を共有します\></span><span class="sxs-lookup"><span data-stu-id="9f457-227">**-i** \\\\<Server\>\\<Share$>\\<filename\></span></span>  
  
 <span data-ttu-id="9f457-228">**-i**"C:\ フォルダー \\<ファイル名 \> "</span><span class="sxs-lookup"><span data-stu-id="9f457-228">**-i** "C:\Some Folder\\<file name\>"</span></span>  
  
 <span data-ttu-id="9f457-229">空白を含むファイル パスは、引用符で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="9f457-229">File paths that contain spaces must be enclosed in quotation marks.</span></span>  
  
 <span data-ttu-id="9f457-230">このオプションは **、-i**_input_file_ **-** i_input_file_のように複数回使用できます。</span><span class="sxs-lookup"><span data-stu-id="9f457-230">This option may be used more than once: **-i**_input_file_ **-I**_I input_file._</span></span>  
  
 <span data-ttu-id="9f457-231">**-o** _output_file_</span><span class="sxs-lookup"><span data-stu-id="9f457-231">**-o** _output_file_</span></span>  
 <span data-ttu-id="9f457-232">`sqlcmd` からの出力を受信するファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="9f457-232">Identifies the file that receives output from `sqlcmd`.</span></span>  
  
 <span data-ttu-id="9f457-233">**-u** が指定されている場合は、 *output_file* は Unicode 形式で格納されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-233">If **-u** is specified, the *output_file* is stored in Unicode format.</span></span> <span data-ttu-id="9f457-234">ファイル名が無効な場合は、エラー メッセージが生成され、`sqlcmd` が終了します。</span><span class="sxs-lookup"><span data-stu-id="9f457-234">If the file name is not valid, an error message is generated, and `sqlcmd` exits.</span></span> <span data-ttu-id="9f457-235">`sqlcmd` は、同じファイルに対する複数の `sqlcmd` プロセスの同時書き込みはサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="9f457-235">`sqlcmd` does not support concurrent writing of multiple `sqlcmd` processes to the same file.</span></span> <span data-ttu-id="9f457-236">出力ファイルが破損するか、または不適切なファイルになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9f457-236">The file output will be corrupted or incorrect.</span></span> <span data-ttu-id="9f457-237">ファイル形式の詳細については、 **-f** スイッチを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f457-237">See the **-f** switch for more information about file formats.</span></span> <span data-ttu-id="9f457-238">このファイルが存在しない場合は作成されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-238">This file will be created if it does not exist.</span></span> <span data-ttu-id="9f457-239">以前の `sqlcmd` セッションで同じ名前のファイルが作成されていた場合は、上書きされます。</span><span class="sxs-lookup"><span data-stu-id="9f457-239">A file of the same name from a prior `sqlcmd` session will be overwritten.</span></span> <span data-ttu-id="9f457-240">ここで指定されるファイルは **stdout** ファイルではありません。</span><span class="sxs-lookup"><span data-stu-id="9f457-240">The file specified here is not the **stdout** file.</span></span> <span data-ttu-id="9f457-241">**Stdout**ファイルが指定されている場合、このファイルは使用されません。</span><span class="sxs-lookup"><span data-stu-id="9f457-241">If a **stdout** file is specified this file will not be used.</span></span>  
  
 <span data-ttu-id="9f457-242">パスの例:</span><span class="sxs-lookup"><span data-stu-id="9f457-242">Path examples:</span></span>  
  
 <span data-ttu-id="9f457-243">**-o**C: \\< ファイル名></span><span class="sxs-lookup"><span data-stu-id="9f457-243">**-o** C:\\< filename></span></span>  
  
 <span data-ttu-id="9f457-244">**-o** \\ \\<Server \> \\<$>\\<ファイル名を共有します\></span><span class="sxs-lookup"><span data-stu-id="9f457-244">**-o** \\\\<Server\>\\<Share$>\\<filename\></span></span>  
  
 <span data-ttu-id="9f457-245">**-o "** C:\ フォルダー \\<ファイル名を指定する (c) \></span><span class="sxs-lookup"><span data-stu-id="9f457-245">**-o "** C:\Some Folder\\<file name\>"</span></span>  
  
 <span data-ttu-id="9f457-246">空白を含むファイル パスは、引用符で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="9f457-246">File paths that contain spaces must be enclosed in quotation marks.</span></span>  
  
 <span data-ttu-id="9f457-247">**-r**[**0** | **1**]</span><span class="sxs-lookup"><span data-stu-id="9f457-247">**-r**[**0** | **1**]</span></span>  
 <span data-ttu-id="9f457-248">エラー メッセージ出力を画面にリダイレクトします (**stderr**)。</span><span class="sxs-lookup"><span data-stu-id="9f457-248">Redirects the error message output to the screen (**stderr**).</span></span> <span data-ttu-id="9f457-249">パラメーターを指定しない場合や、 **0**を指定した場合は、重大度レベル 11 以上のエラー メッセージだけがリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="9f457-249">If you do not specify a parameter or if you specify **0**, only error messages that have a severity level of 11 or higher are redirected.</span></span> <span data-ttu-id="9f457-250">**1**を指定した場合は、PRINT を含むすべてのエラー メッセージ出力がリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="9f457-250">If you specify **1**, all error message output including PRINT is redirected.</span></span> <span data-ttu-id="9f457-251">-o を使用しても効果はありません。</span><span class="sxs-lookup"><span data-stu-id="9f457-251">Has no effect if you use -o.</span></span> <span data-ttu-id="9f457-252">既定では、メッセージは **stdout**に送られます。</span><span class="sxs-lookup"><span data-stu-id="9f457-252">By default, messages are sent to **stdout**.</span></span>  
  
 <span data-ttu-id="9f457-253">**-R**</span><span class="sxs-lookup"><span data-stu-id="9f457-253">**-R**</span></span>  
 <span data-ttu-id="9f457-254">では、 `sqlcmd` [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] クライアントのロケールに基づいてから取得された数値、通貨、日付、および時刻の各列がによってローカライズされます。</span><span class="sxs-lookup"><span data-stu-id="9f457-254">Causes `sqlcmd` to localize numeric, currency, date, and time columns retrieved from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] based on the client's locale.</span></span> <span data-ttu-id="9f457-255">既定では、これらの列はサーバーの地域別設定を使用して表示されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-255">By default, these columns are displayed using the server's regional settings.</span></span>  
  
 <span data-ttu-id="9f457-256">**-u**</span><span class="sxs-lookup"><span data-stu-id="9f457-256">**-u**</span></span>  
 <span data-ttu-id="9f457-257">*input_file* の形式に関係なく、 *output_file*を Unicode 形式で格納するように指定します。</span><span class="sxs-lookup"><span data-stu-id="9f457-257">Specifies that *output_file* is stored in Unicode format, regardless of the format of *input_file*.</span></span>  
  
 <span data-ttu-id="9f457-258">**クエリ実行オプション**</span><span class="sxs-lookup"><span data-stu-id="9f457-258">**Query Execution Options**</span></span>  
  <span data-ttu-id="9f457-259">**-e**</span><span class="sxs-lookup"><span data-stu-id="9f457-259">**-e**</span></span>  
 <span data-ttu-id="9f457-260">入力スクリプトを標準出力デバイス (**stdout**) に書き込みます。</span><span class="sxs-lookup"><span data-stu-id="9f457-260">Writes input scripts to the standard output device (**stdout**).</span></span>  
  
 <span data-ttu-id="9f457-261">**-I**</span><span class="sxs-lookup"><span data-stu-id="9f457-261">**-I**</span></span>  
 <span data-ttu-id="9f457-262">SET QUOTED_IDENTIFIER 接続オプションを ON に設定します。</span><span class="sxs-lookup"><span data-stu-id="9f457-262">Sets the SET QUOTED_IDENTIFIER connection option to ON.</span></span> <span data-ttu-id="9f457-263">既定では、OFF に設定されています。</span><span class="sxs-lookup"><span data-stu-id="9f457-263">By default, it is set to OFF.</span></span> <span data-ttu-id="9f457-264">詳細については、「[SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9f457-264">For more information, see [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql).</span></span>  
  
 <span data-ttu-id="9f457-265">**-q"** _cmdline query_ **"**</span><span class="sxs-lookup"><span data-stu-id="9f457-265">**-q"** _cmdline query_ **"**</span></span>  
 <span data-ttu-id="9f457-266">`sqlcmd` の起動時にクエリを実行しますが、クエリの実行が完了しても `sqlcmd` を終了しません。</span><span class="sxs-lookup"><span data-stu-id="9f457-266">Executes a query when `sqlcmd` starts, but does not exit `sqlcmd` when the query has finished running.</span></span> <span data-ttu-id="9f457-267">セミコロンで区切られた複数のクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="9f457-267">Multiple-semicolon-delimited queries can be executed.</span></span> <span data-ttu-id="9f457-268">次の例で示すように、クエリを引用符で囲みます。</span><span class="sxs-lookup"><span data-stu-id="9f457-268">Use quotation marks around the query, as shown in the following example.</span></span>  
  
 <span data-ttu-id="9f457-269">コマンド プロンプトに、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="9f457-269">At the command prompt, type:</span></span>  
  
 `sqlcmd -d AdventureWorks2012 -q "SELECT FirstName, LastName FROM Person.Person WHERE LastName LIKE 'Whi%';"`  
  
 `sqlcmd -d AdventureWorks2012 -q "SELECT TOP 5 FirstName FROM Person.Person;SELECT TOP 5 LastName FROM Person.Person;"`  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9f457-270">クエリでは GO ターミネータを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="9f457-270">Do not use the GO terminator in the query.</span></span>  
  
 <span data-ttu-id="9f457-271">このオプションと共に `-b` を指定すると、`sqlcmd` はエラーで終了します。</span><span class="sxs-lookup"><span data-stu-id="9f457-271">If `-b` is specified together with this option, `sqlcmd` exits on error.</span></span> <span data-ttu-id="9f457-272">`-b` オプションについては、このトピックの後半で説明します。</span><span class="sxs-lookup"><span data-stu-id="9f457-272">`-b` is described later in this topic.</span></span>  
  
 <span data-ttu-id="9f457-273">**-Q "** _cmdline query_ **"**</span><span class="sxs-lookup"><span data-stu-id="9f457-273">**-Q"** _cmdline query_ **"**</span></span>  
 <span data-ttu-id="9f457-274">`sqlcmd` の起動時にクエリを実行し、`sqlcmd` を即時終了します。</span><span class="sxs-lookup"><span data-stu-id="9f457-274">Executes a query when `sqlcmd` starts and then immediately exits `sqlcmd`.</span></span> <span data-ttu-id="9f457-275">セミコロンで区切られた複数のクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="9f457-275">Multiple-semicolon-delimited queries can be executed.</span></span>  
  
 <span data-ttu-id="9f457-276">次の例で示すように、クエリを引用符で囲みます。</span><span class="sxs-lookup"><span data-stu-id="9f457-276">Use quotation marks around the query, as shown in the following example.</span></span>  
  
 <span data-ttu-id="9f457-277">コマンド プロンプトに、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="9f457-277">At the command prompt, type:</span></span>  
  
 `sqlcmd -d AdventureWorks2012 -Q "SELECT FirstName, LastName FROM Person.Person WHERE LastName LIKE 'Whi%';"`  
  
 `sqlcmd -d AdventureWorks2012 -Q "SELECT TOP 5 FirstName FROM Person.Person;SELECT TOP 5 LastName FROM Person.Person;"`  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9f457-278">クエリでは GO ターミネータを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="9f457-278">Do not use the GO terminator in the query.</span></span>  
  
 <span data-ttu-id="9f457-279">このオプションと共に `-b` を指定すると、`sqlcmd` はエラーで終了します。</span><span class="sxs-lookup"><span data-stu-id="9f457-279">If `-b` is specified together with this option, `sqlcmd` exits on error.</span></span> <span data-ttu-id="9f457-280">`-b` オプションについては、このトピックの後半で説明します。</span><span class="sxs-lookup"><span data-stu-id="9f457-280">`-b` is described later in this topic.</span></span>  
  
 <span data-ttu-id="9f457-281">**-t** _query_timeout_</span><span class="sxs-lookup"><span data-stu-id="9f457-281">**-t** _query_timeout_</span></span>  
 <span data-ttu-id="9f457-282">コマンド (または SQL ステートメント) がタイムアウトするまでの秒数を指定します。このオプションにより、 `sqlcmd` スクリプト変数 SQLCMDSTATTIMEOUT が設定されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-282">Specifies the number of seconds before a command (or SQL statement) times out. This option sets the `sqlcmd` scripting variable SQLCMDSTATTIMEOUT.</span></span> <span data-ttu-id="9f457-283">*time_out* 値を指定しないと、コマンドはタイムアウトしません。*query\*\*time_out* は、1 から 65,534 の数値にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9f457-283">If a *time_out* value is not specified, the command does not time out. The *query\*\*time_out* must be a number between 1 and 65534.</span></span> <span data-ttu-id="9f457-284">指定した値が数値以外の場合、または範囲外の場合、`sqlcmd` はエラー メッセージを生成します。</span><span class="sxs-lookup"><span data-stu-id="9f457-284">If the value supplied is not numeric or does not fall into that range, `sqlcmd` generates an error message.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f457-285">実際のタイムアウト値は、指定した *time_out* 値より数秒異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="9f457-285">The actual time out value may vary from the specified *time_out* value by several seconds.</span></span>  
  
 <span data-ttu-id="9f457-286">**-vvar =** _値_[ **var =** _値_...]</span><span class="sxs-lookup"><span data-stu-id="9f457-286">**-vvar =** _value_[ **var =** _value_...]</span></span>  
 <span data-ttu-id="9f457-287">`sqlcmd`スクリプトで使用できるスクリプト変数を作成し `sqlcmd` ます。</span><span class="sxs-lookup"><span data-stu-id="9f457-287">Creates a `sqlcmd`scripting variable that can be used in a `sqlcmd` script.</span></span> <span data-ttu-id="9f457-288">値に空白が含まれる場合は、値を引用符で囲みます。</span><span class="sxs-lookup"><span data-stu-id="9f457-288">Enclose the value in quotation marks if the value contains spaces.</span></span> <span data-ttu-id="9f457-289">複数の**_var_** = **" *`values`* "** 値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="9f457-289">You can specify multiple **_var_**=**"*`values`*"** values.</span></span> <span data-ttu-id="9f457-290">指定した値にエラーが生じた場合は、`sqlcmd` は、エラー メッセージを生成してから終了します。</span><span class="sxs-lookup"><span data-stu-id="9f457-290">If there are errors in any of the values specified, `sqlcmd` generates an error message and then exits.</span></span>  
  
 `sqlcmd -v MyVar1=something MyVar2="some thing"`  
  
 `sqlcmd -v MyVar1=something -v MyVar2="some thing"`  
  
 <span data-ttu-id="9f457-291">**-x**</span><span class="sxs-lookup"><span data-stu-id="9f457-291">**-x**</span></span>  
 <span data-ttu-id="9f457-292">`sqlcmd` ではスクリプト変数が無視されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-292">Causes `sqlcmd` to ignore scripting variables.</span></span> <span data-ttu-id="9f457-293">これは、$(*variable_name*) などの標準変数と同じ形式の文字列を含む INSERT ステートメントが、スクリプトに多数含まれている場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="9f457-293">This is useful when a script contains many INSERT statements that may contain strings that have the same format as regular variables, such as $(*variable_name*).</span></span>  
  
 <span data-ttu-id="9f457-294">**書式設定のオプション**</span><span class="sxs-lookup"><span data-stu-id="9f457-294">**Formatting Options**</span></span>  
  <span data-ttu-id="9f457-295">**-h** _headers_</span><span class="sxs-lookup"><span data-stu-id="9f457-295">**-h** _headers_</span></span>  
 <span data-ttu-id="9f457-296">列ヘッダーの間に出力する行数を指定します。</span><span class="sxs-lookup"><span data-stu-id="9f457-296">Specifies the number of rows to print between the column headings.</span></span> <span data-ttu-id="9f457-297">既定では、各クエリの結果に対して、ヘッダーは 1 つだけ表示されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-297">The default is to print headings one time for each set of query results.</span></span> <span data-ttu-id="9f457-298">このオプションにより、`sqlcmd` スクリプト変数 SQLCMDHEADERS が設定されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-298">This option sets the `sqlcmd` scripting variable SQLCMDHEADERS.</span></span> <span data-ttu-id="9f457-299">ヘッダーを出力しない場合は、 **-1** を指定します。</span><span class="sxs-lookup"><span data-stu-id="9f457-299">Use **-1** to specify that headers must not be printed.</span></span> <span data-ttu-id="9f457-300">有効でない値があると、`sqlcmd` はエラー メッセージを生成してから終了します。</span><span class="sxs-lookup"><span data-stu-id="9f457-300">Any value that is not valid causes `sqlcmd` to generate an error message and then exit.</span></span>  
  
 <span data-ttu-id="9f457-301">**-k** [**1** | **2**]</span><span class="sxs-lookup"><span data-stu-id="9f457-301">**-k** [**1** | **2**]</span></span>  
 <span data-ttu-id="9f457-302">タブ、改行文字などのすべての制御文字を出力から削除します。</span><span class="sxs-lookup"><span data-stu-id="9f457-302">Removes all control characters, such as tabs and new line characters from the output.</span></span> <span data-ttu-id="9f457-303">これにより、データが返されたときの列の形式が維持されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-303">This preserves column formatting when data is returned.</span></span> <span data-ttu-id="9f457-304">1 を指定した場合、制御文字は 1 つの空白に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="9f457-304">If 1 is specified, the control characters are replaced by a single space.</span></span> <span data-ttu-id="9f457-305">2 を指定すると、連続する制御文字が 1 つの空白に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="9f457-305">If 2 is specified, consecutive control characters are replaced by a single space.</span></span> <span data-ttu-id="9f457-306">**-k** は **-k1**と同じです。</span><span class="sxs-lookup"><span data-stu-id="9f457-306">**-k** is the same as **-k1**.</span></span>  
  
 <span data-ttu-id="9f457-307">**-s** _col_separator_</span><span class="sxs-lookup"><span data-stu-id="9f457-307">**-s** _col_separator_</span></span>  
 <span data-ttu-id="9f457-308">列の区切り文字を指定します。</span><span class="sxs-lookup"><span data-stu-id="9f457-308">Specifies the column-separator character.</span></span> <span data-ttu-id="9f457-309">既定では、空白になっています。</span><span class="sxs-lookup"><span data-stu-id="9f457-309">The default is a blank space.</span></span> <span data-ttu-id="9f457-310">このオプションにより、`sqlcmd` スクリプト変数 SQLCMDCOLSEP が設定されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-310">This option sets the `sqlcmd` scripting variable SQLCMDCOLSEP.</span></span> <span data-ttu-id="9f457-311">アンパサンド (&)、セミコロン (;) など、オペレーティング システムで特別な意味を持つ文字を使用する場合は、その文字を引用符 (") で囲みます。</span><span class="sxs-lookup"><span data-stu-id="9f457-311">To use characters that have special meaning to the operating system such as the ampersand (&), or semicolon (;), enclose the character in quotation marks (").</span></span> <span data-ttu-id="9f457-312">列の区切り文字には、任意の 8 ビットの文字を指定できます。</span><span class="sxs-lookup"><span data-stu-id="9f457-312">The column separator can be any 8-bit character.</span></span>  
  
 <span data-ttu-id="9f457-313">**-w** _column_width_</span><span class="sxs-lookup"><span data-stu-id="9f457-313">**-w** _column_width_</span></span>  
 <span data-ttu-id="9f457-314">出力用の画面幅を指定します。</span><span class="sxs-lookup"><span data-stu-id="9f457-314">Specifies the screen width for output.</span></span> <span data-ttu-id="9f457-315">このオプションにより、`sqlcmd` スクリプト変数 SQLCMDCOLWIDTH が設定されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-315">This option sets the `sqlcmd` scripting variable SQLCMDCOLWIDTH.</span></span> <span data-ttu-id="9f457-316">列幅は 8 よりも大きくかつ 65,536 よりも小さい値にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9f457-316">The column width must be a number greater than 8 and less than 65536.</span></span> <span data-ttu-id="9f457-317">指定した列幅が範囲外の場合、`sqlcmd` はエラー メッセージを生成します。</span><span class="sxs-lookup"><span data-stu-id="9f457-317">If the specified column width does not fall into that range, `sqlcmd` generates and error message.</span></span> <span data-ttu-id="9f457-318">既定の幅は 80 文字です。</span><span class="sxs-lookup"><span data-stu-id="9f457-318">The default width is 80 characters.</span></span> <span data-ttu-id="9f457-319">指定した列幅を超えると、出力行は次の列に折り返されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-319">When an output line exceeds the specified column width, it wraps on to the next line.</span></span>  
  
 <span data-ttu-id="9f457-320">**-W**</span><span class="sxs-lookup"><span data-stu-id="9f457-320">**-W**</span></span>  
 <span data-ttu-id="9f457-321">このオプションは、列から後続の空白を削除します。</span><span class="sxs-lookup"><span data-stu-id="9f457-321">This option removes trailing spaces from a column.</span></span> <span data-ttu-id="9f457-322">他のアプリケーションにエクスポートするデータを準備するときは、 **-s** オプションと同時にこのオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="9f457-322">Use this option together with the **-s** option when preparing data that is to be exported to another application.</span></span> <span data-ttu-id="9f457-323">**-y** または **-Y** オプションと共には使用できません。</span><span class="sxs-lookup"><span data-stu-id="9f457-323">Cannot be used with the **-y** or **-Y** options.</span></span>  
  
 <span data-ttu-id="9f457-324">**-y** _variable_length_type_display_width_</span><span class="sxs-lookup"><span data-stu-id="9f457-324">**-y** _variable_length_type_display_width_</span></span>  
 <span data-ttu-id="9f457-325">`sqlcmd` スクリプト変数 SQLCMDMAXVARTYPEWIDTH が設定されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-325">Sets the `sqlcmd` scripting variable SQLCMDMAXVARTYPEWIDTH.</span></span> <span data-ttu-id="9f457-326">既定値は 256 です。</span><span class="sxs-lookup"><span data-stu-id="9f457-326">The default is 256.</span></span> <span data-ttu-id="9f457-327">長い可変長のデータ型に返される文字数を制限します。</span><span class="sxs-lookup"><span data-stu-id="9f457-327">It limits the number of characters that are returned for the large variable length data types:</span></span>  
  
-   `varchar(max)`  
  
-   `nvarchar(max)`  
  
-   `varbinary(max)`  
  
-   `xml`  
  
-   `UDT (user-defined data types)`  
  
-   `text`  
  
-   `ntext`  
  
-   `image`  
  
> [!NOTE]  
>  <span data-ttu-id="9f457-328">UDT は実装によって固定長にもなります。</span><span class="sxs-lookup"><span data-stu-id="9f457-328">UDTs can be of fixed length depending on the implementation.</span></span> <span data-ttu-id="9f457-329">固定長の UDT の長さが *display_width*よりも短い場合は、返される UDT の値は影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="9f457-329">If this length of a fixed length UDT is shorter that *display_width*, the value of the UDT returned is not affected.</span></span> <span data-ttu-id="9f457-330">ただし、 *display_width*よりも長い場合は、出力は切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="9f457-330">However, if the length is longer than *display_width*, the output is truncated.</span></span>  
  
 
> [!IMPORTANT]  
>  <span data-ttu-id="9f457-331">返されるデータのサイズによって、サーバーとネットワークの両方に重大なパフォーマンスの問題が発生する可能性があるため、 **-y 0** オプションは十分注意して使用してください。</span><span class="sxs-lookup"><span data-stu-id="9f457-331">Use the **-y 0** option with extreme caution because it may cause serious performance issues on both the server and the network, depending on the size of data returned.</span></span>  
  
 <span data-ttu-id="9f457-332">**-Y** _fixed_length_type_display_width_</span><span class="sxs-lookup"><span data-stu-id="9f457-332">**-Y** _fixed_length_type_display_width_</span></span>  
 <span data-ttu-id="9f457-333">`sqlcmd` スクリプト変数 SQLCMDMAXFIXEDTYPEWIDTH が設定されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-333">Sets the `sqlcmd` scripting variable SQLCMDMAXFIXEDTYPEWIDTH.</span></span> <span data-ttu-id="9f457-334">既定値は 0 (無制限) です。</span><span class="sxs-lookup"><span data-stu-id="9f457-334">The default is 0 (unlimited).</span></span> <span data-ttu-id="9f457-335">次のデータ型に返される文字数を制限します。</span><span class="sxs-lookup"><span data-stu-id="9f457-335">Limits the number of characters that are returned for the following data types:</span></span>  
  
-   <span data-ttu-id="9f457-336">`char(`*n* 。 `)` ここで、1<= n<= 8000</span><span class="sxs-lookup"><span data-stu-id="9f457-336">`char(` *n* `)`, where 1<=n<=8000</span></span>  
  
-   <span data-ttu-id="9f457-337">`nchar(n`*n* 。 `)` ここで、1<= n<= 4000</span><span class="sxs-lookup"><span data-stu-id="9f457-337">`nchar(n` *n* `)`, where 1<=n<=4000</span></span>  
  
-   <span data-ttu-id="9f457-338">`varchar(n`*n* 。 `)` ここで、1<= n<= 8000</span><span class="sxs-lookup"><span data-stu-id="9f457-338">`varchar(n` *n* `)`, where 1<=n<=8000</span></span>  
  
-   <span data-ttu-id="9f457-339">`nvarchar(n`*n* 。 `)` ここで、1<= n<= 4000</span><span class="sxs-lookup"><span data-stu-id="9f457-339">`nvarchar(n` *n* `)`, where 1<=n<=4000</span></span>  
  
-   <span data-ttu-id="9f457-340">`varbinary(n`*n* 。 `)` ここで、1<= n<= 4000</span><span class="sxs-lookup"><span data-stu-id="9f457-340">`varbinary(n` *n* `)`, where 1<=n<=4000</span></span>  
  
-   `variant`  
  
 <span data-ttu-id="9f457-341">**エラー報告のオプション**</span><span class="sxs-lookup"><span data-stu-id="9f457-341">**Error Reporting Options**</span></span>  
  `-b`  
 <span data-ttu-id="9f457-342">エラーが発生したときに、`sqlcmd` を終了し、DOS ERRORLEVEL 値を返します。</span><span class="sxs-lookup"><span data-stu-id="9f457-342">Specifies that `sqlcmd` exits and returns a DOS ERRORLEVEL value when an error occurs.</span></span> <span data-ttu-id="9f457-343">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のエラー メッセージの重大度が 10 よりも高い場合、DOS ERRORLEVEL 変数に返される値は **1** です。それ以外の場合は、**0** が返されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-343">The value that is returned to the DOS ERRORLEVEL variable is **1** when the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] error message has a severity level greater than 10; otherwise, the value returned is **0**.</span></span> <span data-ttu-id="9f457-344">`-V` オプションが `-b` と共に設定されている場合、`-V` を使用して設定した値よりも重大度が低いときは、`sqlcmd` はエラーを報告しません。</span><span class="sxs-lookup"><span data-stu-id="9f457-344">If the `-V` option has been set in addition to `-b`, `sqlcmd` will not report an error if the severity level is lower than the values set using `-V`.</span></span> <span data-ttu-id="9f457-345">コマンド プロンプト バッチ ファイルにより ERRORLEVEL の値をテストすることができ、エラーを適切に処理できます。</span><span class="sxs-lookup"><span data-stu-id="9f457-345">Command prompt batch files can test the value of ERRORLEVEL and handle the error appropriately.</span></span> <span data-ttu-id="9f457-346">`sqlcmd` は重大度レベル 10 (情報メッセージ) に対してはエラーを報告しません。</span><span class="sxs-lookup"><span data-stu-id="9f457-346">`sqlcmd` does not report errors for severity level 10 (informational messages).</span></span>  
  
 <span data-ttu-id="9f457-347">`sqlcmd` スクリプトに正しくないコメントや構文エラーが含まれている場合やスクリプト変数が不足している場合、返される ERRORLEVEL は 1 です。</span><span class="sxs-lookup"><span data-stu-id="9f457-347">If the `sqlcmd` script contains an incorrect comment, syntax error, or is missing a scripting variable, ERRORLEVEL returned is 1.</span></span>  
  
 <span data-ttu-id="9f457-348">**-m** _error_level_</span><span class="sxs-lookup"><span data-stu-id="9f457-348">**-m** _error_level_</span></span>  
 <span data-ttu-id="9f457-349">**stdout**に送信されるエラー メッセージを制御します。</span><span class="sxs-lookup"><span data-stu-id="9f457-349">Controls which error messages are sent to **stdout**.</span></span> <span data-ttu-id="9f457-350">重大度レベルがこのレベル以上のメッセージが送信されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-350">Messages that have a severity level greater than or equal to this level are sent.</span></span> <span data-ttu-id="9f457-351">この値を **-1**に設定すると、情報メッセージを含めすべてのメッセージが送信されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-351">When this value is set to **-1**, all messages including informational messages, are sent.</span></span> <span data-ttu-id="9f457-352">**-m** と **-1**の間にスペースは使用できません。</span><span class="sxs-lookup"><span data-stu-id="9f457-352">Spaces are not allowed between the **-m** and **-1**.</span></span> <span data-ttu-id="9f457-353">たとえば、 **-m-1** は有効で、 **-m-1** は有効でありません。</span><span class="sxs-lookup"><span data-stu-id="9f457-353">For example, **-m-1** is valid, and **-m-1** is not.</span></span>  
  
 <span data-ttu-id="9f457-354">このオプションにより、`sqlcmd` スクリプト変数 SQLCMDERRORLEVEL も設定されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-354">This option also sets the `sqlcmd` scripting variable SQLCMDERRORLEVEL.</span></span> <span data-ttu-id="9f457-355">この変数の既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="9f457-355">This variable has a default of 0.</span></span>  
  
 <span data-ttu-id="9f457-356">`-V`*error_severity_level*</span><span class="sxs-lookup"><span data-stu-id="9f457-356">`-V` *error_severity_level*</span></span>  
 <span data-ttu-id="9f457-357">ERRORLEVEL 変数を設定するために使用される重大度レベルを制御します。</span><span class="sxs-lookup"><span data-stu-id="9f457-357">Controls the severity level that is used to set the ERRORLEVEL variable.</span></span> <span data-ttu-id="9f457-358">重大度レベルがこの値以上のエラー メッセージによって、ERRORLEVEL が設定されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-358">Error messages that have severity levels greater than or equal to this value set ERRORLEVEL.</span></span> <span data-ttu-id="9f457-359">0 より小さい値は 0 と報告されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-359">Values that are less than 0 are reported as 0.</span></span> <span data-ttu-id="9f457-360">バッチ ファイルおよび CMD ファイルを使用して、ERRORLEVEL 変数の値をテストできます。</span><span class="sxs-lookup"><span data-stu-id="9f457-360">Batch and CMD files can be used to test the value of the ERRORLEVEL variable.</span></span>  
  
 <span data-ttu-id="9f457-361">**その他のオプション**</span><span class="sxs-lookup"><span data-stu-id="9f457-361">**Miscellaneous Options**</span></span>  
  <span data-ttu-id="9f457-362">**-a** _packet_size_</span><span class="sxs-lookup"><span data-stu-id="9f457-362">**-a** _packet_size_</span></span>  
 <span data-ttu-id="9f457-363">異なるサイズのパケットを要求します。</span><span class="sxs-lookup"><span data-stu-id="9f457-363">Requests a packet of a different size.</span></span> <span data-ttu-id="9f457-364">このオプションにより、`sqlcmd` スクリプト変数 SQLCMDPACKETSIZE が設定されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-364">This option sets the `sqlcmd` scripting variable SQLCMDPACKETSIZE.</span></span> <span data-ttu-id="9f457-365">*packet_size* には、512 ～ 32767 の値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9f457-365">*packet_size* must be a value between 512 and 32767.</span></span> <span data-ttu-id="9f457-366">既定値は 4096 です。</span><span class="sxs-lookup"><span data-stu-id="9f457-366">The default = 4096.</span></span> <span data-ttu-id="9f457-367">大きなパケット サイズを指定すると、GO コマンド間に多数の SQL ステートメントが含まれているスクリプトの実行パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="9f457-367">A larger packet size can enhance performance for execution of scripts that have lots of SQL statements between GO commands.</span></span> <span data-ttu-id="9f457-368">既定値よりも大きいパケット サイズを要求できます。</span><span class="sxs-lookup"><span data-stu-id="9f457-368">You can request a larger packet size.</span></span> <span data-ttu-id="9f457-369">ただし、要求が拒否された場合、`sqlcmd` はサーバーの既定のパケット サイズを使用します。</span><span class="sxs-lookup"><span data-stu-id="9f457-369">However, if the request is denied, `sqlcmd` uses the server default for packet size.</span></span>  
  
 <span data-ttu-id="9f457-370">**-c** _batch_terminator_</span><span class="sxs-lookup"><span data-stu-id="9f457-370">**-c** _batch_terminator_</span></span>  
 <span data-ttu-id="9f457-371">バッチ ターミネータを指定します。</span><span class="sxs-lookup"><span data-stu-id="9f457-371">Specifies the batch terminator.</span></span> <span data-ttu-id="9f457-372">既定では、"GO" だけが入力されている行があると、コマンドが終了したと見なされ、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] に送られます。</span><span class="sxs-lookup"><span data-stu-id="9f457-372">By default, commands are terminated and sent to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by typing the word "GO" on a line by itself.</span></span> <span data-ttu-id="9f457-373">バッチ ターミネータをリセットする場合、[!INCLUDE[tsql](../includes/tsql-md.md)] の予約キーワードやオペレーティング システムで特別な意味を持つ文字は、先頭に円記号が付いているかどうかに関係なく、使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="9f457-373">When you reset the batch terminator, do not use [!INCLUDE[tsql](../includes/tsql-md.md)] reserved keywords or characters that have special meaning to the operating system, even if they are preceded by a backslash.</span></span>  
  
 <span data-ttu-id="9f457-374">**-L** **[c]**</span><span class="sxs-lookup"><span data-stu-id="9f457-374">**-L**[**c**]</span></span>  
 <span data-ttu-id="9f457-375">ローカルに構成されたサーバー コンピューターと、ネットワーク上でブロードキャストしているサーバー コンピューター名の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="9f457-375">Lists the locally configured server computers, and the names of the server computers that are broadcasting on the network.</span></span> <span data-ttu-id="9f457-376">このパラメーターは、他のパラメーターと組み合わせて使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="9f457-376">This parameter cannot be used in combination with other parameters.</span></span> <span data-ttu-id="9f457-377">一覧表示できるサーバー コンピューターの最大数は 3,000 です。</span><span class="sxs-lookup"><span data-stu-id="9f457-377">The maximum number of server computers that can be listed is 3000.</span></span> <span data-ttu-id="9f457-378">バッファーのサイズが原因でサーバーの一覧が切り捨てられる場合は、警告メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-378">If the server list is truncated because of the size of the buffer a warning message is displayed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f457-379">ネットワーク上のブロードキャストの性質により、は、 `sqlcmd` すべてのサーバーからタイムリーな応答を受信できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="9f457-379">Because of the nature of broadcasting on networks, `sqlcmd` may not receive a timely response from all servers.</span></span> <span data-ttu-id="9f457-380">そのため、返されるサーバーのリストは、このオプションの実行ごとに異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9f457-380">Therefore, the list of servers returned may vary for each invocation of this option.</span></span>  
  
 <span data-ttu-id="9f457-381">省略可能なパラメーター **c**が指定されている場合、出力は Servers: ヘッダー行なしで表示され、各サーバー行は先頭にスペースなしで一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-381">If the optional parameter **c** is specified, the output appears without the Servers: header line and each server line is listed without leading spaces.</span></span> <span data-ttu-id="9f457-382">これは、クリーン アウトプットとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="9f457-382">This is referred to as clean output.</span></span> <span data-ttu-id="9f457-383">クリーン アウトプットを使用すると、スクリプト言語の処理パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="9f457-383">Clean output improves the processing performance of scripting languages.</span></span>  
  
 <span data-ttu-id="9f457-384">**-p** **[1]**</span><span class="sxs-lookup"><span data-stu-id="9f457-384">**-p**[**1**]</span></span>  
 <span data-ttu-id="9f457-385">すべての結果セットのパフォーマンス統計を出力します。</span><span class="sxs-lookup"><span data-stu-id="9f457-385">Prints performance statistics for every result set.</span></span> <span data-ttu-id="9f457-386">次は、パフォーマンス統計の形式の例です。</span><span class="sxs-lookup"><span data-stu-id="9f457-386">The following is an example of the format for performance statistics:</span></span>  
  
 `Network packet size (bytes): n`  
  
 `x xact[s]:`  
  
 `Clock Time (ms.): total       t1  avg       t2 (t3 xacts per sec.)`  
  
 <span data-ttu-id="9f457-387">この場合、</span><span class="sxs-lookup"><span data-stu-id="9f457-387">Where:</span></span>  
  
 <span data-ttu-id="9f457-388">`x` = [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] によって処理されるトランザクション数。</span><span class="sxs-lookup"><span data-stu-id="9f457-388">`x` = Number of transactions that are processed by [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="9f457-389">`t1` = すべてのトランザクションにかかる合計時間、</span><span class="sxs-lookup"><span data-stu-id="9f457-389">`t1` = Total time for all transactions.</span></span>  
  
 <span data-ttu-id="9f457-390">`t2` = 単一のトランザクションにかかる平均時間。</span><span class="sxs-lookup"><span data-stu-id="9f457-390">`t2` = Average time for a single transaction.</span></span>  
  
 <span data-ttu-id="9f457-391">`t3` = 1 秒あたりの平均トランザクション数。</span><span class="sxs-lookup"><span data-stu-id="9f457-391">`t3` = Average number of transactions per second.</span></span>  
  
 <span data-ttu-id="9f457-392">すべての時間はミリ秒単位です。</span><span class="sxs-lookup"><span data-stu-id="9f457-392">All times are in milliseconds.</span></span>  
  
 <span data-ttu-id="9f457-393">省略可能なパラメーター **1** を指定した場合は、統計の出力形式は、スプレッドシートへ容易にインポートできる、またはスクリプトによって処理できる、コロンで区切られた形式となります。</span><span class="sxs-lookup"><span data-stu-id="9f457-393">If the optional parameter **1** is specified, the output format of the statistics is in colon-separated format that can be imported easily into a spreadsheet or processed by a script.</span></span>  
  
 <span data-ttu-id="9f457-394">省略可能なパラメーターが**1**以外の値の場合は、エラーが生成され、 `sqlcmd` 終了します。</span><span class="sxs-lookup"><span data-stu-id="9f457-394">If the optional parameter is any value other than **1**, an error is generated and `sqlcmd` exits.</span></span>  
  
 <span data-ttu-id="9f457-395">`-X`[**1**]</span><span class="sxs-lookup"><span data-stu-id="9f457-395">`-X`[**1**]</span></span>  
 <span data-ttu-id="9f457-396">`sqlcmd` がバッチ ファイルから実行される場合に、システムのセキュリティを損なう可能性のあるコマンドを無効にします。</span><span class="sxs-lookup"><span data-stu-id="9f457-396">Disables commands that might compromise system security when `sqlcmd` is executed from a batch file.</span></span> <span data-ttu-id="9f457-397">無効なコマンドも認識されます。`sqlcmd` は警告メッセージを表示して継続します。</span><span class="sxs-lookup"><span data-stu-id="9f457-397">The disabled commands are still recognized; `sqlcmd` issues a warning message and continues.</span></span> <span data-ttu-id="9f457-398">省略可能なパラメーター **1**を指定した場合、は `sqlcmd` エラーメッセージを生成して終了します。</span><span class="sxs-lookup"><span data-stu-id="9f457-398">If the optional parameter **1** is specified, `sqlcmd` generates an error message and then exits.</span></span> <span data-ttu-id="9f457-399">`-X` オプションを使用した場合に無効になるコマンドは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9f457-399">The following commands are disabled when the `-X` option is used:</span></span>  
  
-   <span data-ttu-id="9f457-400">**ED**</span><span class="sxs-lookup"><span data-stu-id="9f457-400">**ED**</span></span>  
  
-   <span data-ttu-id="9f457-401">**!!**</span><span class="sxs-lookup"><span data-stu-id="9f457-401">**!!**</span></span> <span data-ttu-id="9f457-402">_command_</span><span class="sxs-lookup"><span data-stu-id="9f457-402">_command_</span></span>  
  
 <span data-ttu-id="9f457-403">`-X` オプションを指定すると、環境変数が `sqlcmd` に渡されなくなります。</span><span class="sxs-lookup"><span data-stu-id="9f457-403">If the `-X` option is specified, it prevents environment variables from being passed on to `sqlcmd`.</span></span> <span data-ttu-id="9f457-404">また、SQLCMDINI スクリプト変数を使用して指定した、スタートアップ スクリプトも実行できなくなります。</span><span class="sxs-lookup"><span data-stu-id="9f457-404">It also prevents the startup script specified by using the SQLCMDINI scripting variable from being executed.</span></span> <span data-ttu-id="9f457-405">変数のスクリプト作成の詳細につい `sqlcmd` ては、「 [Sqlcmd をスクリプト変数と共に使用する](../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f457-405">For more information about `sqlcmd` scripting variables, see [Use sqlcmd with Scripting Variables](../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md).</span></span>  
  
 <span data-ttu-id="9f457-406">**-?**</span><span class="sxs-lookup"><span data-stu-id="9f457-406">**-?**</span></span>  
 <span data-ttu-id="9f457-407">`sqlcmd` オプションの構文の概要を表示します。</span><span class="sxs-lookup"><span data-stu-id="9f457-407">Displays the syntax summary of `sqlcmd` options.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f457-408">解説</span><span class="sxs-lookup"><span data-stu-id="9f457-408">Remarks</span></span>  
 <span data-ttu-id="9f457-409">オプションは、構文の例に示されている順序に従って使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9f457-409">Options do not have to be used in the order shown in the syntax section.</span></span>  
  
 <span data-ttu-id="9f457-410">複数の結果が返される場合は、`sqlcmd` は同じバッチの各結果セットの間に空白行を 1 行ずつ出力します。</span><span class="sxs-lookup"><span data-stu-id="9f457-410">When multiple results are returned, `sqlcmd` prints a blank line between each result set in a batch.</span></span> <span data-ttu-id="9f457-411">また、"処理された \<x> 行数" メッセージは、実行されたステートメントに適用されない場合には表示されません。</span><span class="sxs-lookup"><span data-stu-id="9f457-411">In addition, the "\<x> rows affected" message does not appear when it does not apply to the statement executed.</span></span>  
  
 <span data-ttu-id="9f457-412">対話的に使用するには `sqlcmd` 、 `sqlcmd` このトピックで前述した1つ以上のオプションを使用して、コマンドプロンプトで「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="9f457-412">To use `sqlcmd` interactively, type `sqlcmd` at the command prompt with any one or more of the options described earlier in this topic.</span></span> <span data-ttu-id="9f457-413">詳細については、「 [sqlcmd ユーティリティの使用](../relational-databases/scripting/sqlcmd-use-the-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f457-413">For more information, see [Use the sqlcmd Utility](../relational-databases/scripting/sqlcmd-use-the-utility.md)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f457-414">**-L**、 **-Q**、 **-Z** 、または **-i**のオプションを実行すると、が `sqlcmd` 終了します。</span><span class="sxs-lookup"><span data-stu-id="9f457-414">The options **-L**, **-Q**, **-Z** or **-i** cause `sqlcmd` to exit after execution.</span></span>  
  
 <span data-ttu-id="9f457-415">コマンド環境 (Cmd.exe) での `sqlcmd` コマンド ライン全体の長さは、すべての引数と拡張変数を含めて、オペレーティング システムの Cmd.exe によって決まります。</span><span class="sxs-lookup"><span data-stu-id="9f457-415">The total length of the `sqlcmd` command line in the command environment (Cmd.exe), including all arguments and expanded variables, is that which is determined by the operating system for Cmd.exe.</span></span>  
  
## <a name="variable-precedence-low-to-high"></a><span data-ttu-id="9f457-416">変数の優先順位 (低から高)</span><span class="sxs-lookup"><span data-stu-id="9f457-416">Variable Precedence (Low to High)</span></span>  
  
1.  <span data-ttu-id="9f457-417">システム レベル環境変数</span><span class="sxs-lookup"><span data-stu-id="9f457-417">System-level environmental variables.</span></span>  
  
2.  <span data-ttu-id="9f457-418">ユーザー レベル環境変数</span><span class="sxs-lookup"><span data-stu-id="9f457-418">User-level environmental variables</span></span>  
  
3.  <span data-ttu-id="9f457-419">コマンドシェル (**set** X = Y) は、実行前にコマンドプロンプトで設定 `sqlcmd` します。</span><span class="sxs-lookup"><span data-stu-id="9f457-419">Command shell (**SET** X=Y) set at command prompt before running `sqlcmd`.</span></span>  
  
4.  <span data-ttu-id="9f457-420">**sqlcmd-v** X=Y</span><span class="sxs-lookup"><span data-stu-id="9f457-420">**sqlcmd-v** X=Y</span></span>  
  
5.  <span data-ttu-id="9f457-421">**:Setvar** X Y</span><span class="sxs-lookup"><span data-stu-id="9f457-421">**:Setvar** X Y</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f457-422">環境変数を表示するには、 **[コントロール パネル]** の **[システム]** アイコンを開き、 **[詳細設定]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9f457-422">To view the environmental variables, in **Control Panel**, open **System**, and then click the **Advanced** tab.</span></span>  
  
## <a name="sqlcmd-scripting-variables"></a><span data-ttu-id="9f457-423">sqlcmd スクリプト変数</span><span class="sxs-lookup"><span data-stu-id="9f457-423">sqlcmd Scripting Variables</span></span>  
  
|<span data-ttu-id="9f457-424">変数</span><span class="sxs-lookup"><span data-stu-id="9f457-424">Variable</span></span>|<span data-ttu-id="9f457-425">関連スイッチ</span><span class="sxs-lookup"><span data-stu-id="9f457-425">Related switch</span></span>|<span data-ttu-id="9f457-426">R/W</span><span class="sxs-lookup"><span data-stu-id="9f457-426">R/W</span></span>|<span data-ttu-id="9f457-427">Default</span><span class="sxs-lookup"><span data-stu-id="9f457-427">Default</span></span>|  
|--------------|--------------------|----------|-------------|  
|<span data-ttu-id="9f457-428">SQLCMDUSER</span><span class="sxs-lookup"><span data-stu-id="9f457-428">SQLCMDUSER</span></span>|<span data-ttu-id="9f457-429">-U</span><span class="sxs-lookup"><span data-stu-id="9f457-429">-U</span></span>|<span data-ttu-id="9f457-430">R</span><span class="sxs-lookup"><span data-stu-id="9f457-430">R</span></span>|<span data-ttu-id="9f457-431">""</span><span class="sxs-lookup"><span data-stu-id="9f457-431">""</span></span>|  
|<span data-ttu-id="9f457-432">SQLCMDPASSWORD</span><span class="sxs-lookup"><span data-stu-id="9f457-432">SQLCMDPASSWORD</span></span>|<span data-ttu-id="9f457-433">-P</span><span class="sxs-lookup"><span data-stu-id="9f457-433">-P</span></span>|--|<span data-ttu-id="9f457-434">""</span><span class="sxs-lookup"><span data-stu-id="9f457-434">""</span></span>|  
|<span data-ttu-id="9f457-435">SQLCMDSERVER</span><span class="sxs-lookup"><span data-stu-id="9f457-435">SQLCMDSERVER</span></span>|<span data-ttu-id="9f457-436">-S</span><span class="sxs-lookup"><span data-stu-id="9f457-436">-S</span></span>|<span data-ttu-id="9f457-437">R</span><span class="sxs-lookup"><span data-stu-id="9f457-437">R</span></span>|<span data-ttu-id="9f457-438">"DefaultLocalInstance"</span><span class="sxs-lookup"><span data-stu-id="9f457-438">"DefaultLocalInstance"</span></span>|  
|<span data-ttu-id="9f457-439">SQLCMDWORKSTATION</span><span class="sxs-lookup"><span data-stu-id="9f457-439">SQLCMDWORKSTATION</span></span>|<span data-ttu-id="9f457-440">-H</span><span class="sxs-lookup"><span data-stu-id="9f457-440">-H</span></span>|<span data-ttu-id="9f457-441">R</span><span class="sxs-lookup"><span data-stu-id="9f457-441">R</span></span>|<span data-ttu-id="9f457-442">"ComputerName"</span><span class="sxs-lookup"><span data-stu-id="9f457-442">"ComputerName"</span></span>|  
|<span data-ttu-id="9f457-443">SQLCMDDBNAME</span><span class="sxs-lookup"><span data-stu-id="9f457-443">SQLCMDDBNAME</span></span>|<span data-ttu-id="9f457-444">-d</span><span class="sxs-lookup"><span data-stu-id="9f457-444">-d</span></span>|<span data-ttu-id="9f457-445">R</span><span class="sxs-lookup"><span data-stu-id="9f457-445">R</span></span>|<span data-ttu-id="9f457-446">""</span><span class="sxs-lookup"><span data-stu-id="9f457-446">""</span></span>|  
|<span data-ttu-id="9f457-447">SQLCMDLOGINTIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9f457-447">SQLCMDLOGINTIMEOUT</span></span>|<span data-ttu-id="9f457-448">-l</span><span class="sxs-lookup"><span data-stu-id="9f457-448">-l</span></span>|<span data-ttu-id="9f457-449">R/W</span><span class="sxs-lookup"><span data-stu-id="9f457-449">R/W</span></span>|<span data-ttu-id="9f457-450">"8" (秒)</span><span class="sxs-lookup"><span data-stu-id="9f457-450">"8" (seconds)</span></span>|  
|<span data-ttu-id="9f457-451">SQLCMDSTATTIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9f457-451">SQLCMDSTATTIMEOUT</span></span>|<span data-ttu-id="9f457-452">-t</span><span class="sxs-lookup"><span data-stu-id="9f457-452">-t</span></span>|<span data-ttu-id="9f457-453">R/W</span><span class="sxs-lookup"><span data-stu-id="9f457-453">R/W</span></span>|<span data-ttu-id="9f457-454">"0" = 無制限に待機</span><span class="sxs-lookup"><span data-stu-id="9f457-454">"0" = wait indefinitely</span></span>|  
|<span data-ttu-id="9f457-455">SQLCMDHEADERS</span><span class="sxs-lookup"><span data-stu-id="9f457-455">SQLCMDHEADERS</span></span>|<span data-ttu-id="9f457-456">-H</span><span class="sxs-lookup"><span data-stu-id="9f457-456">-h</span></span>|<span data-ttu-id="9f457-457">R/W</span><span class="sxs-lookup"><span data-stu-id="9f457-457">R/W</span></span>|<span data-ttu-id="9f457-458">"0"</span><span class="sxs-lookup"><span data-stu-id="9f457-458">"0"</span></span>|  
|<span data-ttu-id="9f457-459">SQLCMDCOLSEP</span><span class="sxs-lookup"><span data-stu-id="9f457-459">SQLCMDCOLSEP</span></span>|<span data-ttu-id="9f457-460">-S</span><span class="sxs-lookup"><span data-stu-id="9f457-460">-s</span></span>|<span data-ttu-id="9f457-461">R/W</span><span class="sxs-lookup"><span data-stu-id="9f457-461">R/W</span></span>|<span data-ttu-id="9f457-462">" "</span><span class="sxs-lookup"><span data-stu-id="9f457-462">" "</span></span>|  
|<span data-ttu-id="9f457-463">SQLCMDCOLWIDTH</span><span class="sxs-lookup"><span data-stu-id="9f457-463">SQLCMDCOLWIDTH</span></span>|<span data-ttu-id="9f457-464">-w</span><span class="sxs-lookup"><span data-stu-id="9f457-464">-w</span></span>|<span data-ttu-id="9f457-465">R/W</span><span class="sxs-lookup"><span data-stu-id="9f457-465">R/W</span></span>|<span data-ttu-id="9f457-466">"0"</span><span class="sxs-lookup"><span data-stu-id="9f457-466">"0"</span></span>|  
|<span data-ttu-id="9f457-467">SQLCMDPACKETSIZE</span><span class="sxs-lookup"><span data-stu-id="9f457-467">SQLCMDPACKETSIZE</span></span>|<span data-ttu-id="9f457-468">-a</span><span class="sxs-lookup"><span data-stu-id="9f457-468">-a</span></span>|<span data-ttu-id="9f457-469">R</span><span class="sxs-lookup"><span data-stu-id="9f457-469">R</span></span>|<span data-ttu-id="9f457-470">"4096"</span><span class="sxs-lookup"><span data-stu-id="9f457-470">"4096"</span></span>|  
|<span data-ttu-id="9f457-471">SQLCMDERRORLEVEL</span><span class="sxs-lookup"><span data-stu-id="9f457-471">SQLCMDERRORLEVEL</span></span>|<span data-ttu-id="9f457-472">-M</span><span class="sxs-lookup"><span data-stu-id="9f457-472">-m</span></span>|<span data-ttu-id="9f457-473">R/W</span><span class="sxs-lookup"><span data-stu-id="9f457-473">R/W</span></span>|<span data-ttu-id="9f457-474">0</span><span class="sxs-lookup"><span data-stu-id="9f457-474">0</span></span>|  
|<span data-ttu-id="9f457-475">SQLCMDMAXVARTYPEWIDTH</span><span class="sxs-lookup"><span data-stu-id="9f457-475">SQLCMDMAXVARTYPEWIDTH</span></span>|<span data-ttu-id="9f457-476">-y</span><span class="sxs-lookup"><span data-stu-id="9f457-476">-y</span></span>|<span data-ttu-id="9f457-477">R/W</span><span class="sxs-lookup"><span data-stu-id="9f457-477">R/W</span></span>|<span data-ttu-id="9f457-478">"256"</span><span class="sxs-lookup"><span data-stu-id="9f457-478">"256"</span></span>|  
|<span data-ttu-id="9f457-479">SQLCMDMAXFIXEDTYPEWIDTH</span><span class="sxs-lookup"><span data-stu-id="9f457-479">SQLCMDMAXFIXEDTYPEWIDTH</span></span>|<span data-ttu-id="9f457-480">-y</span><span class="sxs-lookup"><span data-stu-id="9f457-480">-Y</span></span>|<span data-ttu-id="9f457-481">R/W</span><span class="sxs-lookup"><span data-stu-id="9f457-481">R/W</span></span>|<span data-ttu-id="9f457-482">"0" = 無制限</span><span class="sxs-lookup"><span data-stu-id="9f457-482">"0" = unlimited</span></span>|  
|<span data-ttu-id="9f457-483">SQLCMDEDITOR</span><span class="sxs-lookup"><span data-stu-id="9f457-483">SQLCMDEDITOR</span></span>||<span data-ttu-id="9f457-484">R/W</span><span class="sxs-lookup"><span data-stu-id="9f457-484">R/W</span></span>|<span data-ttu-id="9f457-485">"edit.com"</span><span class="sxs-lookup"><span data-stu-id="9f457-485">"edit.com"</span></span>|  
|<span data-ttu-id="9f457-486">SQLCMDINI</span><span class="sxs-lookup"><span data-stu-id="9f457-486">SQLCMDINI</span></span>||<span data-ttu-id="9f457-487">R</span><span class="sxs-lookup"><span data-stu-id="9f457-487">R</span></span>|<span data-ttu-id="9f457-488">""</span><span class="sxs-lookup"><span data-stu-id="9f457-488">""</span></span>|  
  
 <span data-ttu-id="9f457-489">SQLCMDUSER、SQLCMDPASSWORD、および SQLCMDSERVER は、**:Connect**</span><span class="sxs-lookup"><span data-stu-id="9f457-489">SQLCMDUSER, SQLCMDPASSWORD and SQLCMDSERVER are set when **:Connect**</span></span>  
  
 <span data-ttu-id="9f457-490"> が使用されているときに設定されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-490">is used.</span></span>  
  
 <span data-ttu-id="9f457-491">R は、その値がプログラムの初期化時に一度だけ設定できることを示します。</span><span class="sxs-lookup"><span data-stu-id="9f457-491">R indicates the value can only be set one time during program initialization.</span></span>  
  
 <span data-ttu-id="9f457-492">R/W は、 **setvar** コマンドを使用して値を変更できること、および後続のコマンドに新しい値が反映されることを示します。</span><span class="sxs-lookup"><span data-stu-id="9f457-492">R/W indicates that the value can be modified by using the **setvar** command and subsequent commands will be influenced by the new value.</span></span>  
  
## <a name="sqlcmd-commands"></a><span data-ttu-id="9f457-493">sqlcmd コマンド</span><span class="sxs-lookup"><span data-stu-id="9f457-493">sqlcmd Commands</span></span>  
 <span data-ttu-id="9f457-494">[!INCLUDE[tsql](../includes/tsql-md.md)]内のステートメントに加え `sqlcmd` て、次のコマンドも使用できます。</span><span class="sxs-lookup"><span data-stu-id="9f457-494">In addition to [!INCLUDE[tsql](../includes/tsql-md.md)] statements within `sqlcmd`, the following commands are also available:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9f457-495">**GO** [*count*]</span><span class="sxs-lookup"><span data-stu-id="9f457-495">**GO** [*count*]</span></span>|<span data-ttu-id="9f457-496">**:List**</span><span class="sxs-lookup"><span data-stu-id="9f457-496">**:List**</span></span>|  
|<span data-ttu-id="9f457-497">**[:]** **RESET**</span><span class="sxs-lookup"><span data-stu-id="9f457-497">[**:**] **RESET**</span></span>|<span data-ttu-id="9f457-498">**:Error**</span><span class="sxs-lookup"><span data-stu-id="9f457-498">**:Error**</span></span>|  
|<span data-ttu-id="9f457-499">**[:]** **ED**</span><span class="sxs-lookup"><span data-stu-id="9f457-499">[**:**] **ED**</span></span>|<span data-ttu-id="9f457-500">**:Out**</span><span class="sxs-lookup"><span data-stu-id="9f457-500">**:Out**</span></span>|  
|<span data-ttu-id="9f457-501">[**:**] **!!**</span><span class="sxs-lookup"><span data-stu-id="9f457-501">[**:**] **!!**</span></span>|<span data-ttu-id="9f457-502">**:Perftrace**</span><span class="sxs-lookup"><span data-stu-id="9f457-502">**:Perftrace**</span></span>|  
|<span data-ttu-id="9f457-503">**[:]** **QUIT**</span><span class="sxs-lookup"><span data-stu-id="9f457-503">[**:**] **QUIT**</span></span>|<span data-ttu-id="9f457-504">**:Connect**</span><span class="sxs-lookup"><span data-stu-id="9f457-504">**:Connect**</span></span>|  
|<span data-ttu-id="9f457-505">**[:]** **EXIT**</span><span class="sxs-lookup"><span data-stu-id="9f457-505">[**:**] **EXIT**</span></span>|<span data-ttu-id="9f457-506">**:On Error**</span><span class="sxs-lookup"><span data-stu-id="9f457-506">**:On Error**</span></span>|  
|<span data-ttu-id="9f457-507">**:r**</span><span class="sxs-lookup"><span data-stu-id="9f457-507">**:r**</span></span>|<span data-ttu-id="9f457-508">**:Help**</span><span class="sxs-lookup"><span data-stu-id="9f457-508">**:Help**</span></span>|  
|<span data-ttu-id="9f457-509">**:ServerList**</span><span class="sxs-lookup"><span data-stu-id="9f457-509">**:ServerList**</span></span>|<span data-ttu-id="9f457-510">**:XML** [**ON** &#124; **OFF**]</span><span class="sxs-lookup"><span data-stu-id="9f457-510">**:XML** [**ON** &#124; **OFF**]</span></span>|  
|<span data-ttu-id="9f457-511">**:Setvar**</span><span class="sxs-lookup"><span data-stu-id="9f457-511">**:Setvar**</span></span>|<span data-ttu-id="9f457-512">**:Listvar**</span><span class="sxs-lookup"><span data-stu-id="9f457-512">**:Listvar**</span></span>|  
  
 <span data-ttu-id="9f457-513">`sqlcmd` コマンドを使用するときは、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="9f457-513">Be aware of the following when you use `sqlcmd` commands:</span></span>  
  
-   <span data-ttu-id="9f457-514">GO を除くすべての `sqlcmd` コマンドは、コロン (:) によってプレフィックス指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9f457-514">All `sqlcmd` commands, except GO, must be prefixed by a colon (:).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="9f457-515">既存の **osql** スクリプトとの互換性を保つために、一部のコマンドはコロンなしで認識されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-515">To maintain backward compatibility with existing **osql** scripts, some of the commands will be recognized without the colon.</span></span> <span data-ttu-id="9f457-516">これは、[**:**] によって示されています。</span><span class="sxs-lookup"><span data-stu-id="9f457-516">This is indicated by the [**:**].</span></span>  
  
-   <span data-ttu-id="9f457-517">`sqlcmd` コマンドが認識されるのは、コマンドが行の先頭にある場合のみです。</span><span class="sxs-lookup"><span data-stu-id="9f457-517">`sqlcmd` commands are recognized only if they appear at the start of a line.</span></span>  
  
-   <span data-ttu-id="9f457-518">すべての `sqlcmd` コマンドには、大文字と小文字の区別はありません。</span><span class="sxs-lookup"><span data-stu-id="9f457-518">All `sqlcmd` commands are case insensitive.</span></span>  
  
-   <span data-ttu-id="9f457-519">各コマンドは個別の行に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9f457-519">Each command must be on a separate line.</span></span> <span data-ttu-id="9f457-520">コマンドの後には、[!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントまたは別のコマンドを指定できません。</span><span class="sxs-lookup"><span data-stu-id="9f457-520">A command cannot be followed by a [!INCLUDE[tsql](../includes/tsql-md.md)] statement or another command.</span></span>  
  
-   <span data-ttu-id="9f457-521">コマンドは即座に実行されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-521">Commands are executed immediately.</span></span> <span data-ttu-id="9f457-522">[!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントのように、実行バッファーに配置されません。</span><span class="sxs-lookup"><span data-stu-id="9f457-522">They are not put in the execution buffer as [!INCLUDE[tsql](../includes/tsql-md.md)] statements are.</span></span>  
  
 <span data-ttu-id="9f457-523">**編集コマンド**</span><span class="sxs-lookup"><span data-stu-id="9f457-523">**Editing Commands**</span></span>  
  <span data-ttu-id="9f457-524">**[:]** **ED**</span><span class="sxs-lookup"><span data-stu-id="9f457-524">[**:**] **ED**</span></span>  
 <span data-ttu-id="9f457-525">テキスト エディターを開始します。</span><span class="sxs-lookup"><span data-stu-id="9f457-525">Starts the text editor.</span></span> <span data-ttu-id="9f457-526">このエディターは、現在の [!INCLUDE[tsql](../includes/tsql-md.md)] バッチまたは最後に実行したバッチを編集する場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="9f457-526">This editor can be used to edit the current [!INCLUDE[tsql](../includes/tsql-md.md)] batch, or the last executed batch.</span></span> <span data-ttu-id="9f457-527">最後に実行したバッチを編集するには、最後のバッチの実行が完了した直後に **ED** コマンドを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9f457-527">To edit the last executed batch, the **ED** command must be typed immediately after the last batch has completed execution.</span></span>  
  
 <span data-ttu-id="9f457-528">テキスト エディターは、SQLCMDEDITOR 環境変数で定義したエディターです。</span><span class="sxs-lookup"><span data-stu-id="9f457-528">The text editor is defined by the SQLCMDEDITOR environment variable.</span></span> <span data-ttu-id="9f457-529">既定のエディターは "Edit" です。</span><span class="sxs-lookup"><span data-stu-id="9f457-529">The default editor is 'Edit'.</span></span> <span data-ttu-id="9f457-530">エディターを変更するには、SQLCMDEDITOR 環境変数を設定します。</span><span class="sxs-lookup"><span data-stu-id="9f457-530">To change the editor, set the SQLCMDEDITOR environment variable.</span></span> <span data-ttu-id="9f457-531">たとえば、エディターを [!INCLUDE[msCoName](../includes/msconame-md.md)] メモ帳に設定するには、コマンド プロンプトで次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="9f457-531">For example, to set the editor to [!INCLUDE[msCoName](../includes/msconame-md.md)] Notepad, at the command prompt, type:</span></span>  
  
 `SET SQLCMDEDITOR=notepad`  
  
 <span data-ttu-id="9f457-532">**[:]** **RESET**</span><span class="sxs-lookup"><span data-stu-id="9f457-532">[**:**] **RESET**</span></span>  
 <span data-ttu-id="9f457-533">ステートメント キャッシュをクリアします。</span><span class="sxs-lookup"><span data-stu-id="9f457-533">Clears the statement cache.</span></span>  
  
 <span data-ttu-id="9f457-534">**:List**</span><span class="sxs-lookup"><span data-stu-id="9f457-534">**:List**</span></span>  
 <span data-ttu-id="9f457-535">ステートメント キャッシュの内容を出力します。</span><span class="sxs-lookup"><span data-stu-id="9f457-535">Prints the content of the statement cache.</span></span>  
  
 <span data-ttu-id="9f457-536">**変数**</span><span class="sxs-lookup"><span data-stu-id="9f457-536">**Variables**</span></span>  
  <span data-ttu-id="9f457-537">**: Setvar** \<**var**>[ **"*`value`*"** ]</span><span class="sxs-lookup"><span data-stu-id="9f457-537">**:Setvar** \<**var**> [ **"*`value`*"** ]</span></span>  
 <span data-ttu-id="9f457-538">`sqlcmd` スクリプト変数を定義します。</span><span class="sxs-lookup"><span data-stu-id="9f457-538">Defines `sqlcmd` scripting variables.</span></span> <span data-ttu-id="9f457-539">スクリプト変数は `$(VARNAME)`という形式になります。</span><span class="sxs-lookup"><span data-stu-id="9f457-539">Scripting variables have the following format: `$(VARNAME)`.</span></span>  
  
 <span data-ttu-id="9f457-540">変数名では大文字と小文字が区別されません。</span><span class="sxs-lookup"><span data-stu-id="9f457-540">Variable names are case insensitive.</span></span>  
  
 <span data-ttu-id="9f457-541">スクリプト変数は次の方法で指定できます。</span><span class="sxs-lookup"><span data-stu-id="9f457-541">Scripting variables can be set in the following ways:</span></span>  
  
-   <span data-ttu-id="9f457-542">コマンド ラインのオプションを暗黙的に使用します。</span><span class="sxs-lookup"><span data-stu-id="9f457-542">Implicitly using a command-line option.</span></span> <span data-ttu-id="9f457-543">たとえば、 **-l**オプションを指定すると、SQLCMDLOGINTIMEOUT 変数が設定さ `sqlcmd` れます。</span><span class="sxs-lookup"><span data-stu-id="9f457-543">For example, the **-l** option sets the SQLCMDLOGINTIMEOUT `sqlcmd` variable.</span></span>  
  
-   <span data-ttu-id="9f457-544">**:Setvar** コマンドを明示的に使用します。</span><span class="sxs-lookup"><span data-stu-id="9f457-544">Explicitly by using the **:Setvar** command.</span></span>  
  
-   <span data-ttu-id="9f457-545">`sqlcmd` の実行前に環境変数を定義します。</span><span class="sxs-lookup"><span data-stu-id="9f457-545">By defining an environment variable before you run `sqlcmd`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f457-546">`-X` オプションを使用すると、環境変数が `sqlcmd` に渡されなくなります。</span><span class="sxs-lookup"><span data-stu-id="9f457-546">The `-X` option prevents environment variables from being passed on to `sqlcmd`.</span></span>  
  
 <span data-ttu-id="9f457-547">**:Setvar** を使って定義した変数と環境変数が同じ名前の場合は、 **:Setvar** を使用して定義した変数が優先されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-547">If a variable defined by using **:Setvar** and an environment variable have the same name, the variable defined by using **:Setvar** takes precedence.</span></span>  
  
 <span data-ttu-id="9f457-548">変数名には空白文字を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="9f457-548">Variable names must not contain blank space characters.</span></span>  
  
 <span data-ttu-id="9f457-549">また変数名には、$ (var) のような変数表現と同じ形式を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="9f457-549">Variable names cannot have the same form as a variable expression, such as $(var).</span></span>  
  
 <span data-ttu-id="9f457-550">スクリプト変数の文字列値に空白文字が含まれる場合は、値を引用符で囲みます。</span><span class="sxs-lookup"><span data-stu-id="9f457-550">If the string value of the scripting variable contains blank spaces, enclose the value in quotation marks.</span></span> <span data-ttu-id="9f457-551">スクリプト変数の値を設定していない場合は、そのスクリプト変数は削除されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-551">If a value for a scripting variable is not specified, the scripting variable is dropped.</span></span>  
  
 <span data-ttu-id="9f457-552">**:Listvar**</span><span class="sxs-lookup"><span data-stu-id="9f457-552">**:Listvar**</span></span>  
 <span data-ttu-id="9f457-553">現在設定されているスクリプト変数の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="9f457-553">Displays a list of the scripting variables that are currently set.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f457-554">によって設定されたスクリプト変数 `sqlcmd` と、 **: Setvar**コマンドを使用して設定されたスクリプト変数のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-554">Only scripting variables that are set by `sqlcmd`, and those that are set using the **:Setvar** command will be displayed.</span></span>  
  
 <span data-ttu-id="9f457-555">**出力コマンド**</span><span class="sxs-lookup"><span data-stu-id="9f457-555">**Output Commands**</span></span>  
  <span data-ttu-id="9f457-556">**:Error** </span><span class="sxs-lookup"><span data-stu-id="9f457-556">**:Error** </span></span>  
 <span data-ttu-id="9f457-557">**_\<_** _filename_  **_>|_ STDERR |STDOUT**</span><span class="sxs-lookup"><span data-stu-id="9f457-557">**_\<_** _filename_  **_>|_ STDERR|STDOUT**</span></span>  
 <span data-ttu-id="9f457-558">すべてのエラー出力を、 *file name*によって指定されたファイル、または **stderr** や **stdout**にリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="9f457-558">Redirect all error output to the file specified by *file name*, to **stderr** or to **stdout**.</span></span> <span data-ttu-id="9f457-559">**Error** コマンドは、スクリプト内で複数回使用できます。</span><span class="sxs-lookup"><span data-stu-id="9f457-559">The **Error** command can appear multiple times in a script.</span></span> <span data-ttu-id="9f457-560">既定では、エラー出力は **stderr**に送られます。</span><span class="sxs-lookup"><span data-stu-id="9f457-560">By default, error output is sent to **stderr**.</span></span>  
  
 <span data-ttu-id="9f457-561">*ファイル名*</span><span class="sxs-lookup"><span data-stu-id="9f457-561">*file name*</span></span>  
 <span data-ttu-id="9f457-562">出力を受信するファイルを作成して開きます。</span><span class="sxs-lookup"><span data-stu-id="9f457-562">Creates and opens a file that will receive the output.</span></span> <span data-ttu-id="9f457-563">ファイルが既に存在している場合は、ファイルは 0 バイトに切り詰められます。</span><span class="sxs-lookup"><span data-stu-id="9f457-563">If the file already exists, it will be truncated to zero bytes.</span></span> <span data-ttu-id="9f457-564">権限またはその他の理由でファイルが使用できない場合は、出力は切り替えられず、最後に指定した出力先または既定の出力先に送信されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-564">If the file is not available because of permissions or other reasons, the output will not be switched and will be sent to the last specified or default destination.</span></span>  
  
 <span data-ttu-id="9f457-565">**STDERR**</span><span class="sxs-lookup"><span data-stu-id="9f457-565">**STDERR**</span></span>  
 <span data-ttu-id="9f457-566">エラー出力を **stderr** ストリームに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="9f457-566">Switches error output to the **stderr** stream.</span></span> <span data-ttu-id="9f457-567">ストリームがリダイレクトされている場合は、ストリームがリダイレクトされた対象がエラー出力を受信します。</span><span class="sxs-lookup"><span data-stu-id="9f457-567">If this has been redirected, the target to which the stream has been redirected will receive the error output.</span></span>  
  
 <span data-ttu-id="9f457-568">**STDOUT**</span><span class="sxs-lookup"><span data-stu-id="9f457-568">**STDOUT**</span></span>  
 <span data-ttu-id="9f457-569">エラー出力を **stdout** ストリームに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="9f457-569">Switches error output to the **stdout** stream.</span></span> <span data-ttu-id="9f457-570">ストリームがリダイレクトされている場合は、ストリームがリダイレクトされた対象がエラー出力を受信します。</span><span class="sxs-lookup"><span data-stu-id="9f457-570">If this has been redirected, the target to which the stream has been redirected will receive the error output.</span></span>  
  
 <span data-ttu-id="9f457-571">\*\*: 出力 \<** _filename_ **> \*\* | **STDERR** | **STDOUT**</span><span class="sxs-lookup"><span data-stu-id="9f457-571">**:Out \<** _filename_ **>**| **STDERR**| **STDOUT**</span></span>  
 <span data-ttu-id="9f457-572">すべてのクエリ結果を、 *file name*によって指定されたファイル、または **stderr** や **stdout**に作成してリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="9f457-572">Creates and redirects all query results to the file specified by *file name*, to **stderr** or to **stdout**.</span></span> <span data-ttu-id="9f457-573">既定では、出力は **stdout**に送られます。</span><span class="sxs-lookup"><span data-stu-id="9f457-573">By default, output is sent to **stdout**.</span></span> <span data-ttu-id="9f457-574">ファイルが既に存在している場合は、ファイルは 0 バイトに切り詰められます。</span><span class="sxs-lookup"><span data-stu-id="9f457-574">If the file already exists, it will be truncated to zero bytes.</span></span> <span data-ttu-id="9f457-575">**Out** コマンドは、スクリプト内で複数回使用できます。</span><span class="sxs-lookup"><span data-stu-id="9f457-575">The **Out** command can appear multiple times in a script.</span></span>  
  
 <span data-ttu-id="9f457-576">\*\*:P erftrace \<** _filename_ **> \*\* | **STDERR** | **STDOUT**</span><span class="sxs-lookup"><span data-stu-id="9f457-576">**:Perftrace \<** _filename_ **>**| **STDERR**| **STDOUT**</span></span>  
 <span data-ttu-id="9f457-577">すべてのパフォーマンス トレース情報を、 *file name*によって指定されたファイル、または **stderr** や **stdout**に作成してリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="9f457-577">Creates and redirects all performance trace information to the file specified by *file name*, to **stderr** or to **stdout**.</span></span> <span data-ttu-id="9f457-578">既定では、パフォーマンス トレース出力は **stdout**に送られます。</span><span class="sxs-lookup"><span data-stu-id="9f457-578">By default performance trace output is sent to **stdout**.</span></span> <span data-ttu-id="9f457-579">ファイルが既に存在している場合は、ファイルは 0 バイトに切り詰められます。</span><span class="sxs-lookup"><span data-stu-id="9f457-579">If the file already exists, it will be truncated to zero bytes.</span></span> <span data-ttu-id="9f457-580">**Perftrace** コマンドは、スクリプト内で複数回使用できます。</span><span class="sxs-lookup"><span data-stu-id="9f457-580">The **Perftrace** command can appear multiple times in a script.</span></span>  
  
 <span data-ttu-id="9f457-581">**実行制御コマンド**</span><span class="sxs-lookup"><span data-stu-id="9f457-581">**Execution Control Commands**</span></span>  
  <span data-ttu-id="9f457-582">**: エラー時**[ `exit`  |  `ignore` ]</span><span class="sxs-lookup"><span data-stu-id="9f457-582">**:On Error**[ `exit` | `ignore`]</span></span>  
 <span data-ttu-id="9f457-583">スクリプト実行中またはバッチ実行中のエラー発生時に対応するアクションを設定します。</span><span class="sxs-lookup"><span data-stu-id="9f457-583">Sets the action to be performed when an error occurs during script or batch execution.</span></span>  
  
 <span data-ttu-id="9f457-584">`exit` オプションを使用した場合、`sqlcmd` は該当するエラー値を表示して終了します。</span><span class="sxs-lookup"><span data-stu-id="9f457-584">When the `exit` option is used, `sqlcmd` exits with the appropriate error value.</span></span>  
  
 <span data-ttu-id="9f457-585">`ignore` オプションを使用すると、`sqlcmd` はエラーを無視し、バッチまたはスクリプトの実行を続行します。</span><span class="sxs-lookup"><span data-stu-id="9f457-585">When the `ignore` option is used, `sqlcmd` ignores the error and continues executing the batch or script.</span></span> <span data-ttu-id="9f457-586">既定では、エラー メッセージが出力されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-586">By default, an error message will be printed.</span></span>  
  
 <span data-ttu-id="9f457-587">**[:]** **QUIT**</span><span class="sxs-lookup"><span data-stu-id="9f457-587">[**:**] **QUIT**</span></span>  
 <span data-ttu-id="9f457-588">`sqlcmd` が終了します。</span><span class="sxs-lookup"><span data-stu-id="9f457-588">Causes `sqlcmd` to exit.</span></span>  
  
 <span data-ttu-id="9f457-589">[**:**]**終了**[ **( *`statement`* )** ]</span><span class="sxs-lookup"><span data-stu-id="9f457-589">[**:**] **EXIT**[ **(*`statement`*)** ]</span></span>  
 <span data-ttu-id="9f457-590">では、からの戻り値として SELECT ステートメントの結果を使用でき `sqlcmd` ます。</span><span class="sxs-lookup"><span data-stu-id="9f457-590">Lets you use the result of a SELECT statement as the return value from `sqlcmd`.</span></span> <span data-ttu-id="9f457-591">数値の場合、結果行の最終行の第 1 列は、4 バイトの (長) 整数に変換されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-591">If numeric, the first column of the last result row is converted to a 4-byte integer (long).</span></span> <span data-ttu-id="9f457-592">MS-DOS は、下位バイトを親プロセスやオペレーティング システムのエラー レベルに渡します。</span><span class="sxs-lookup"><span data-stu-id="9f457-592">MS-DOS passes the low byte to the parent process or operating system error level.</span></span> <span data-ttu-id="9f457-593">Windows 200x では、4 バイトの整数全体を渡します。</span><span class="sxs-lookup"><span data-stu-id="9f457-593">Windows 200x passes the whole 4-byte integer.</span></span> <span data-ttu-id="9f457-594">の構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9f457-594">The syntax is:</span></span>  
  
 `:EXIT(query)`  
  
 <span data-ttu-id="9f457-595">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="9f457-595">For example:</span></span>  
  
 `:EXIT(SELECT @@ROWCOUNT)`  
  
 <span data-ttu-id="9f457-596">バッチ ファイルの一部として、 **EXIT** パラメーターを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="9f457-596">You can also include the **EXIT** parameter as part of a batch file.</span></span> <span data-ttu-id="9f457-597">たとえば、コマンド プロンプトで次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="9f457-597">For example, at the command prompt, type:</span></span>  
  
 `sqlcmd -Q "EXIT(SELECT COUNT(*) FROM '%1')"`  
  
 <span data-ttu-id="9f457-598">ユーティリティは、 `sqlcmd` かっこ **()** の間にあるすべての情報をサーバーに送信します。</span><span class="sxs-lookup"><span data-stu-id="9f457-598">The `sqlcmd` utility sends everything between the parentheses **()** to the server.</span></span> <span data-ttu-id="9f457-599">システム ストアド プロシージャで 1 つの値セットを選択し、値を返すように指定した場合、返されるのは選択した値のみです。</span><span class="sxs-lookup"><span data-stu-id="9f457-599">If a system stored procedure selects a set and returns a value, only the selection is returned.</span></span> <span data-ttu-id="9f457-600">かっこ内に何も指定せずに EXIT **()** ステートメントを指定すると、バッチ内のそのステートメントより前にあるものすべてを実行し、戻り値を返さずに終了します。</span><span class="sxs-lookup"><span data-stu-id="9f457-600">The EXIT **()** statement with nothing between the parentheses executes everything before it in the batch and then exits without a return value.</span></span>  
  
 <span data-ttu-id="9f457-601">不適切なクエリを指定すると、`sqlcmd` は戻り値を返さずに終了します。</span><span class="sxs-lookup"><span data-stu-id="9f457-601">When an incorrect query is specified, `sqlcmd` will exit without a return value.</span></span>  
  
 <span data-ttu-id="9f457-602">EXIT の形式を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9f457-602">Here is a list of EXIT formats:</span></span>  
  
-   <span data-ttu-id="9f457-603">:EXIT</span><span class="sxs-lookup"><span data-stu-id="9f457-603">:EXIT</span></span>  
  
 <span data-ttu-id="9f457-604">バッチを実行せずに直ちに終了し、値を返しません。</span><span class="sxs-lookup"><span data-stu-id="9f457-604">Does not execute the batch, and then quits immediately and returns no value.</span></span>  
  
-   <span data-ttu-id="9f457-605">:EXIT ( )</span><span class="sxs-lookup"><span data-stu-id="9f457-605">:EXIT( )</span></span>  
  
 <span data-ttu-id="9f457-606">バッチを実行してから終了し、値を返しません。</span><span class="sxs-lookup"><span data-stu-id="9f457-606">Executes the batch, and then quits and returns no value.</span></span>  
  
-   <span data-ttu-id="9f457-607">:EXIT (query)</span><span class="sxs-lookup"><span data-stu-id="9f457-607">:EXIT(query)</span></span>  
  
 <span data-ttu-id="9f457-608">クエリを含むバッチを実行し、クエリの結果を返して終了します。</span><span class="sxs-lookup"><span data-stu-id="9f457-608">Executes the batch that includes the query, and then quits after it returns the results of the query.</span></span>  
  
 <span data-ttu-id="9f457-609">RAISERROR をスクリプト内で使用 `sqlcmd` し、状態127が発生した場合 `sqlcmd` 、はを終了し、メッセージ ID をクライアントに返します。</span><span class="sxs-lookup"><span data-stu-id="9f457-609">If RAISERROR is used within a `sqlcmd` script and a state of 127 is raised, `sqlcmd` will quit and return the message ID back to the client.</span></span> <span data-ttu-id="9f457-610">例:</span><span class="sxs-lookup"><span data-stu-id="9f457-610">For example:</span></span>  
  
 `RAISERROR(50001, 10, 127)`  
  
 <span data-ttu-id="9f457-611">このエラーが発生すると、`sqlcmd` スクリプトは終了し、メッセージ ID 50001 がクライアントに返されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-611">This error will cause the `sqlcmd` script to end and return the message ID 50001 to the client.</span></span>  
  
 <span data-ttu-id="9f457-612">戻り値 -1 ～ -99 は [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] によって予約済みです。`sqlcmd` では次のような追加の戻り値を定義しています。</span><span class="sxs-lookup"><span data-stu-id="9f457-612">The return values -1 to -99 are reserved by [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]; `sqlcmd` defines the following additional return values:</span></span>  
  
|<span data-ttu-id="9f457-613">戻り値</span><span class="sxs-lookup"><span data-stu-id="9f457-613">Return Values</span></span>|<span data-ttu-id="9f457-614">説明</span><span class="sxs-lookup"><span data-stu-id="9f457-614">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="9f457-615">-100</span><span class="sxs-lookup"><span data-stu-id="9f457-615">-100</span></span>|<span data-ttu-id="9f457-616">戻り値を選択する前に、エラーが発生した。</span><span class="sxs-lookup"><span data-stu-id="9f457-616">Error encountered prior to selecting return value.</span></span>|  
|<span data-ttu-id="9f457-617">-101</span><span class="sxs-lookup"><span data-stu-id="9f457-617">-101</span></span>|<span data-ttu-id="9f457-618">戻り値を選択するときに、行が見つからなかった。</span><span class="sxs-lookup"><span data-stu-id="9f457-618">No rows found when selecting return value.</span></span>|  
|<span data-ttu-id="9f457-619">-102</span><span class="sxs-lookup"><span data-stu-id="9f457-619">-102</span></span>|<span data-ttu-id="9f457-620">戻り値を選択するときに、変換エラーが発生した。</span><span class="sxs-lookup"><span data-stu-id="9f457-620">Conversion error occurred when selecting return value.</span></span>|  
  
 <span data-ttu-id="9f457-621">**GO** [*count*]</span><span class="sxs-lookup"><span data-stu-id="9f457-621">**GO** [*count*]</span></span>  
 <span data-ttu-id="9f457-622">GO は、バッチの終わりとキャッシュされた [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントの実行を知らせます。</span><span class="sxs-lookup"><span data-stu-id="9f457-622">GO signals both the end of a batch and the execution of any cached [!INCLUDE[tsql](../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="9f457-623">*count* の値を指定すると、キャッシュされたステートメントが 1 つのバッチとして *count* の回数だけ実行されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-623">When specifying a value for *count*, the cached statements will be executed *count* times, as a single batch.</span></span>  
  
 <span data-ttu-id="9f457-624">**その他のコマンド**</span><span class="sxs-lookup"><span data-stu-id="9f457-624">**Miscellaneous Commands**</span></span>  
  <span data-ttu-id="9f457-625">**: r\<** _filename_ **>**</span><span class="sxs-lookup"><span data-stu-id="9f457-625">**:r \<** _filename_ **>**</span></span>  
 <span data-ttu-id="9f457-626">[!INCLUDE[tsql](../includes/tsql-md.md)] `sqlcmd` によって指定されたファイルから、ステートメントキャッシュに追加のステートメントとコマンドを解析し **<*`filename`*>** ます。</span><span class="sxs-lookup"><span data-stu-id="9f457-626">Parses additional [!INCLUDE[tsql](../includes/tsql-md.md)] statements and `sqlcmd` commands from the file specified by **<*`filename`*>** into the statement cache.</span></span>  
  
 <span data-ttu-id="9f457-627">**GO** が最後に記述されていない [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントがファイルに含まれている場合は、その行の **:r** の後に **GO** を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9f457-627">If the file contains [!INCLUDE[tsql](../includes/tsql-md.md)] statements that are not followed by **GO**, you must enter **GO** on the line that follows **:r**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f457-628">**\<** _filename_ **>** は、が実行されたスタートアップディレクトリに対して相対的に読み取られ `sqlcmd` ます。</span><span class="sxs-lookup"><span data-stu-id="9f457-628">**\<** _filename_ **>** is read relative to the startup directory in which `sqlcmd` was run.</span></span>  
  
 <span data-ttu-id="9f457-629">ファイルは、バッチ ターミネータが検出された後に読み取られ、実行されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-629">The file will be read and executed after a batch terminator is encountered.</span></span> <span data-ttu-id="9f457-630">**:r** コマンドは複数発行できます。</span><span class="sxs-lookup"><span data-stu-id="9f457-630">You can issue multiple **:r** commands.</span></span> <span data-ttu-id="9f457-631">ファイルには、どのような `sqlcmd` コマンドでも含めることができます。</span><span class="sxs-lookup"><span data-stu-id="9f457-631">The file may include any `sqlcmd` command.</span></span> <span data-ttu-id="9f457-632">これには、バッチ ターミネータの **GO**も含まれます。</span><span class="sxs-lookup"><span data-stu-id="9f457-632">This includes the batch terminator **GO**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f457-633">対話モードで表示される行数は、 **:r** コマンドが検出されるたびに、1 行ずつ増えます。</span><span class="sxs-lookup"><span data-stu-id="9f457-633">The line count that is displayed in interactive mode will be increased by one for every **:r** command encountered.</span></span> <span data-ttu-id="9f457-634">**:r** コマンドは、リスト コマンドの出力に表示されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-634">The **:r** command will appear in the output of the list command.</span></span>  
  
 <span data-ttu-id="9f457-635">**:Serverlist**</span><span class="sxs-lookup"><span data-stu-id="9f457-635">**:Serverlist**</span></span>  
 <span data-ttu-id="9f457-636">ローカルに構成されたサーバーと、ネットワーク上でブロードキャストしているサーバー名の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="9f457-636">Lists the locally configured servers and the names of the servers broadcasting on the network.</span></span>  
  
 <span data-ttu-id="9f457-637">**: Connect** _server_name_[ **\\** _instance_name_] [-l *timeout*] [-U *user_name* [-P *password*]]</span><span class="sxs-lookup"><span data-stu-id="9f457-637">**:Connect** _server_name_[**\\**_instance_name_] [-l *timeout*] [-U *user_name* [-P *password*]]</span></span>  
 <span data-ttu-id="9f457-638">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="9f457-638">Connects to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9f457-639">また、現在の接続を終了します。</span><span class="sxs-lookup"><span data-stu-id="9f457-639">Also closes the current connection.</span></span>  
  
 <span data-ttu-id="9f457-640">タイムアウト オプション :</span><span class="sxs-lookup"><span data-stu-id="9f457-640">Time-out options:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9f457-641">0</span><span class="sxs-lookup"><span data-stu-id="9f457-641">0</span></span>|<span data-ttu-id="9f457-642">待機状態を維持</span><span class="sxs-lookup"><span data-stu-id="9f457-642">wait forever</span></span>|  
|<span data-ttu-id="9f457-643">n>0</span><span class="sxs-lookup"><span data-stu-id="9f457-643">n>0</span></span>|<span data-ttu-id="9f457-644">n 秒間待機</span><span class="sxs-lookup"><span data-stu-id="9f457-644">wait for n seconds</span></span>|  
  
 <span data-ttu-id="9f457-645">SQLCMDSERVER スクリプト変数により、現在のアクティブな接続が反映されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-645">The SQLCMDSERVER scripting variable will reflect the current active connection.</span></span>  
  
 <span data-ttu-id="9f457-646">*timeout* を指定しないと、SQLCMDLOGINTIMEOUT 変数の値が既定値になります。</span><span class="sxs-lookup"><span data-stu-id="9f457-646">If *timeout* is not specified, the value of the SQLCMDLOGINTIMEOUT variable is the default.</span></span>  
  
 <span data-ttu-id="9f457-647">*user_name* のみを指定した場合 (オプションとして指定した場合も、環境変数として指定した場合も)、ユーザーはパスワードの入力を要求されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-647">If only *user_name* is specified (either as an option, or as an environment variable), the user will be prompted to enter a password.</span></span> <span data-ttu-id="9f457-648">SQLCMDUSER 環境変数または SQLCMDPASSWORD 環境変数が設定されている場合は、この限りではありません。</span><span class="sxs-lookup"><span data-stu-id="9f457-648">This is not true if the SQLCMDUSER or SQLCMDPASSWORD environment variables have been set.</span></span> <span data-ttu-id="9f457-649">オプションも環境変数も提供されない場合は、Windows 認証モードを使用してログインします。</span><span class="sxs-lookup"><span data-stu-id="9f457-649">If neither options nor environment variables are provided, Windows Authentication mode is used to login.</span></span> <span data-ttu-id="9f457-650">たとえば、統合セキュリティを使用して、`instance1` である [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンス `myserver` に接続するには、次を使用します。</span><span class="sxs-lookup"><span data-stu-id="9f457-650">For example to connect to an instance, `instance1`, of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], `myserver`, by using integrated security you would use the following:</span></span>  
  
 `:connect myserver\instance1`  
  
 <span data-ttu-id="9f457-651">スクリプト変数を使用して `myserver` の既定のインスタンスに接続するには、次を使用します。</span><span class="sxs-lookup"><span data-stu-id="9f457-651">To connect to the default instance of `myserver` using scripting variables, you would use the following:</span></span>  
  
 `:setvar myusername test`  
  
 `:setvar myservername myserver`  
  
 `:connect $(myservername) $(myusername)`  
  
 <span data-ttu-id="9f457-652">[**:**] **!!**\< *command*></span><span class="sxs-lookup"><span data-stu-id="9f457-652">[**:**] **!!**\< *command*></span></span>  
 <span data-ttu-id="9f457-653">オペレーティング システムのコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9f457-653">Executes operating system commands.</span></span> <span data-ttu-id="9f457-654">オペレーティング システムのコマンドを実行するには、行頭に 2 つの感嘆符 ( **!!** ) を入力し、続けてオペレーティング システムのコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="9f457-654">To execute an operating system command, start a line with two exclamation marks (**!!**) followed by the operating system command.</span></span> <span data-ttu-id="9f457-655">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="9f457-655">For example:</span></span>  
  
 `:!! Dir`  
  
> [!NOTE]  
>  <span data-ttu-id="9f457-656">コマンドは `sqlcmd` を実行中のコンピューター上で実行されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-656">The command is executed on the computer on which `sqlcmd` is running.</span></span>  
  
 <span data-ttu-id="9f457-657">**:XML** [**ON** | **OFF**]</span><span class="sxs-lookup"><span data-stu-id="9f457-657">**:XML** [**ON** | **OFF**]</span></span>  
 <span data-ttu-id="9f457-658">詳細については、このトピックの「XML 出力形式」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f457-658">For more information, see "XML Output Format," later in this topic</span></span>  
  
 <span data-ttu-id="9f457-659">**:Help**</span><span class="sxs-lookup"><span data-stu-id="9f457-659">**:Help**</span></span>  
 <span data-ttu-id="9f457-660">`sqlcmd` コマンドと各コマンドの短い説明を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="9f457-660">Lists `sqlcmd` commands together with a short description of each command.</span></span>  
  
### <a name="sqlcmd-file-names"></a><span data-ttu-id="9f457-661">sqlcmd のファイル名</span><span class="sxs-lookup"><span data-stu-id="9f457-661">sqlcmd File Names</span></span>  
 <span data-ttu-id="9f457-662">`sqlcmd`入力ファイルは、 **-i**オプションまたは **: r**コマンドで指定できます。</span><span class="sxs-lookup"><span data-stu-id="9f457-662">`sqlcmd` input files can be specified with the **-i** option or the **:r** command.</span></span> <span data-ttu-id="9f457-663">出力ファイルは **-o** オプションまたは **:Error**、 **:Out** 、および **:Perftrace** コマンドで指定できます。</span><span class="sxs-lookup"><span data-stu-id="9f457-663">Output files can be specified with the **-o** option or the **:Error**, **:Out** and **:Perftrace** commands.</span></span> <span data-ttu-id="9f457-664">指定するファイルについてのガイドラインを次に示します。</span><span class="sxs-lookup"><span data-stu-id="9f457-664">The following are some guidelines for working with these files:</span></span>  
  
-   <span data-ttu-id="9f457-665">**: Error**、 **: Out**および **:P erftrace**では、別個のを使用する必要があり **<*`filename`*>** ます。</span><span class="sxs-lookup"><span data-stu-id="9f457-665">**:Error**, **:Out** and **:Perftrace** should use separate **<*`filename`*>**.</span></span> <span data-ttu-id="9f457-666">同じが使用されている場合は、 **<*`filename`*>** コマンドからの入力が混在している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9f457-666">If the same **<*`filename`*>** is used, inputs from the commands may be intermixed.</span></span>  
  
-   <span data-ttu-id="9f457-667">ローカル コンピューターの `sqlcmd` からリモート サーバー上の入力ファイルが呼び出され、ファイルに :out c:\OutputFile.txt のようにドライブ パスが含まれていると、</span><span class="sxs-lookup"><span data-stu-id="9f457-667">If an input file that is located on a remote server is called from `sqlcmd` on a local computer and the file contains a drive file path such as :out c:\OutputFile.txt.</span></span> <span data-ttu-id="9f457-668">出力ファイルはリモート サーバーではなく、ローカル コンピューター上に作成されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-668">The output file will be created on the local computer and not on the remote server.</span></span>  
  
-   <span data-ttu-id="9f457-669">有効なファイルパスは次のとおりです: C: \\ **<*`filename`*>** 、 \\ \\<Server \> \\<$>\\ **<*`filename`*>** 、"c:\ フォルダー" を共有し \\ **<*`file name`*>** ます。</span><span class="sxs-lookup"><span data-stu-id="9f457-669">Valid file paths include: C:\\**<*`filename`*>**, \\\\<Server\>\\<Share$>\\**<*`filename`*>** and "C:\Some Folder\\**<*`file name`*>**".</span></span> <span data-ttu-id="9f457-670">パスに空白が含まれる場合は、引用符を使用します。</span><span class="sxs-lookup"><span data-stu-id="9f457-670">If there is a space in the path, use quotation marks.</span></span>  
  
-   <span data-ttu-id="9f457-671">各新規 `sqlcmd` セッションは同じ名前の既存のファイルを上書きします。</span><span class="sxs-lookup"><span data-stu-id="9f457-671">Each new `sqlcmd` session will overwrite existing files that have the same names.</span></span>  
  
### <a name="informational-messages"></a><span data-ttu-id="9f457-672">情報メッセージ</span><span class="sxs-lookup"><span data-stu-id="9f457-672">Informational Messages</span></span>  
 <span data-ttu-id="9f457-673">`sqlcmd` は、サーバーから送信されたすべての情報メッセージを出力します。</span><span class="sxs-lookup"><span data-stu-id="9f457-673">`sqlcmd` prints any informational message that are sent by the server.</span></span> <span data-ttu-id="9f457-674">次の例では、[!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントが実行された後、情報メッセージが出力されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-674">In the following example, after the [!INCLUDE[tsql](../includes/tsql-md.md)] statements are executed, an informational message is printed.</span></span>  
  
 <span data-ttu-id="9f457-675">コマンド プロンプトに次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="9f457-675">At the command prompt, type the following:</span></span>  
  
 `sqlcmd`  
  
 `At the sqlcmd prompt type:`  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 <span data-ttu-id="9f457-676">Enter キーを押すと、次の情報メッセージが出力されます。"データベース コンテキストが 'AdventureWorks2012' に変更されました。"</span><span class="sxs-lookup"><span data-stu-id="9f457-676">When you press ENTER, the following informational message is printed: "Changed database context to 'AdventureWorks2012'."</span></span>  
  
### <a name="output-format-from-transact-sql-queries"></a><span data-ttu-id="9f457-677">Transact-SQL クエリからの出力形式</span><span class="sxs-lookup"><span data-stu-id="9f457-677">Output Format from Transact-SQL Queries</span></span>  
 <span data-ttu-id="9f457-678">まず、`sqlcmd` は SELECT リストで指定した列名を含む列ヘッダーを出力します。</span><span class="sxs-lookup"><span data-stu-id="9f457-678">`sqlcmd` first prints a column header that contains the column names specified in the select list.</span></span> <span data-ttu-id="9f457-679">列名は、SQLCMDCOLSEP で指定された文字を使用して分割されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-679">The column names are separated by using the SQLCMDCOLSEP character.</span></span> <span data-ttu-id="9f457-680">既定では、空白です。</span><span class="sxs-lookup"><span data-stu-id="9f457-680">By default, this is a space.</span></span> <span data-ttu-id="9f457-681">列名が列幅よりも短い場合は、出力は次の列まで空白で埋められます。</span><span class="sxs-lookup"><span data-stu-id="9f457-681">If the column name is shorter than the column width, the output is padded with spaces up to the next column.</span></span>  
  
 <span data-ttu-id="9f457-682">この行の次には区切り行が出力されます。区切り行は、連続したダッシュ文字です。</span><span class="sxs-lookup"><span data-stu-id="9f457-682">This line will be followed by a separator line that is a series of dash characters.</span></span> <span data-ttu-id="9f457-683">次に出力の例を示します。</span><span class="sxs-lookup"><span data-stu-id="9f457-683">The following output shows an example.</span></span>  
  
 <span data-ttu-id="9f457-684">`sqlcmd`を起動します。</span><span class="sxs-lookup"><span data-stu-id="9f457-684">Start `sqlcmd`.</span></span> <span data-ttu-id="9f457-685">`sqlcmd` コマンド プロンプトで次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="9f457-685">At the `sqlcmd` command prompt, type the following:</span></span>  
  
 `USE AdventureWorks2012;`  
  
 `SELECT TOP (2) BusinessEntityID, FirstName, LastName`  
  
 `FROM Person.Person;`  
  
 `GO`  
  
 <span data-ttu-id="9f457-686">Enter キーを押すと、次の結果セットが返されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-686">When you press ENTER, the following result set is returned.</span></span>  
  
 `BusinessEntityID FirstName    LastName`  
  
 `---------------- ------------ ----------`  
  
 `285              Syed         Abbas`  
  
 `293              Catherine    Abel`  
  
 `(2 row(s) affected)`  
  
 <span data-ttu-id="9f457-687">`BusinessEntityID` 列には 4 文字分の幅しかありませんが、長い列名に合わせるため拡張されています。</span><span class="sxs-lookup"><span data-stu-id="9f457-687">Although the `BusinessEntityID` column is only 4 characters wide, it has been expanded to accommodate the longer column name.</span></span> <span data-ttu-id="9f457-688">既定では、出力は 80 文字で終了します。</span><span class="sxs-lookup"><span data-stu-id="9f457-688">By default, output is terminated at 80 characters.</span></span> <span data-ttu-id="9f457-689">この設定は、 **-w** オプションを使用するか、SQLCMDCOLWIDTH スクリプト変数を設定することで変更できます。</span><span class="sxs-lookup"><span data-stu-id="9f457-689">This can be changed by using the **-w** option, or by setting the SQLCMDCOLWIDTH scripting variable.</span></span>  
  
### <a name="xml-output-format"></a><span data-ttu-id="9f457-690">XML 出力形式</span><span class="sxs-lookup"><span data-stu-id="9f457-690">XML Output Format</span></span>  
 <span data-ttu-id="9f457-691">FOR XML 句からの結果である XML 出力は、連続するストリームでフォーマットされずに出力されます。</span><span class="sxs-lookup"><span data-stu-id="9f457-691">XML output that is the result of a FOR XML clause is output, unformatted, in a continuous stream.</span></span>  
  
 <span data-ttu-id="9f457-692">XML 出力を行うには、 `:XML ON`コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="9f457-692">When you expect XML output, use the following command: `:XML ON`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f457-693">`sqlcmd` は、通常の形式のエラー メッセージを返します。</span><span class="sxs-lookup"><span data-stu-id="9f457-693">`sqlcmd` returns error messages in the usual format.</span></span> <span data-ttu-id="9f457-694">エラー メッセージが XML 形式の XML テキスト ストリームで出力されることにも注意してください。</span><span class="sxs-lookup"><span data-stu-id="9f457-694">Notice that the error messages are also output in the XML text stream in XML format.</span></span> <span data-ttu-id="9f457-695">`:XML ON` を使用すると、`sqlcmd` は情報メッセージを表示しません。</span><span class="sxs-lookup"><span data-stu-id="9f457-695">By using `:XML ON`, `sqlcmd` does not display informational messages.</span></span>  
  
 <span data-ttu-id="9f457-696">XML モードをオフにするには、 `:XML OFF`コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="9f457-696">To set the XML mode off, use the following command: `:XML OFF`.</span></span>  
  
 <span data-ttu-id="9f457-697">XML OFF コマンドは `sqlcmd` を行指向の出力に切り替えるので、XML OFF コマンドの実行前に GO コマンドは指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="9f457-697">The GO command should not appear before the XML OFF command is issued because the XML OFF command switches `sqlcmd` back to row-oriented output.</span></span>  
  
 <span data-ttu-id="9f457-698">XML (ストリーム入力) データと行セットのデータは、混在することはできません。</span><span class="sxs-lookup"><span data-stu-id="9f457-698">XML (streamed) data and rowset data cannot be mixed.</span></span> <span data-ttu-id="9f457-699">XML ストリームを出力する [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントの実行前に、XML ON コマンドが実行されていない場合は、正しく出力されません。</span><span class="sxs-lookup"><span data-stu-id="9f457-699">If the XML ON command has not been issued before a [!INCLUDE[tsql](../includes/tsql-md.md)] statement that outputs XML streams is executed, the output will be garbled.</span></span> <span data-ttu-id="9f457-700">XML ON コマンドが実行されている場合は、通常の行セットを出力する [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントは実行できません。</span><span class="sxs-lookup"><span data-stu-id="9f457-700">If the XML ON command has been issued, you cannot execute [!INCLUDE[tsql](../includes/tsql-md.md)] statements that output regular row sets.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f457-701">**:XML** コマンドは SET STATISTICS XML ステートメントをサポートしません。</span><span class="sxs-lookup"><span data-stu-id="9f457-701">The **:XML** command does not support the SET STATISTICS XML statement.</span></span>  
  
## <a name="sqlcmd-best-practices"></a><span data-ttu-id="9f457-702">sqlcmd のベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="9f457-702">sqlcmd Best Practices</span></span>  
 <span data-ttu-id="9f457-703">次の説明を参考にして、セキュリティと効率を最大にしてください。</span><span class="sxs-lookup"><span data-stu-id="9f457-703">Use the following practices to help maximize security and efficiency.</span></span>  
  
-   <span data-ttu-id="9f457-704">統合セキュリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="9f457-704">Use integrated security.</span></span>  
  
-   <span data-ttu-id="9f457-705">自動化された環境では `-X` を使用します。</span><span class="sxs-lookup"><span data-stu-id="9f457-705">Use `-X` in automated environments.</span></span>  
  
-   <span data-ttu-id="9f457-706">適切な NTFS ファイル システム権限を使用して、入力ファイルと出力ファイルのセキュリティを保護します。</span><span class="sxs-lookup"><span data-stu-id="9f457-706">Secure input and output files by using appropriate NTFS file system permissions.</span></span>  
  
-   <span data-ttu-id="9f457-707">パフォーマンスを向上させるには、複数のセッションではなく、1 つの `sqlcmd` セッションの中で、できるだけ作業するようにします。</span><span class="sxs-lookup"><span data-stu-id="9f457-707">To increase performance, do as much in one `sqlcmd` session as you can, instead of in a series of sessions.</span></span>  
  
-   <span data-ttu-id="9f457-708">バッチまたはクエリ実行のタイムアウト値を、推定所要時間よりも長めに設定します。</span><span class="sxs-lookup"><span data-stu-id="9f457-708">Set time-out values for batch or query execution higher than you expect it will take to execute the batch or query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f457-709">参照</span><span class="sxs-lookup"><span data-stu-id="9f457-709">See Also</span></span>  
 <span data-ttu-id="9f457-710">[sqlcmd ユーティリティの起動](../relational-databases/scripting/sqlcmd-start-the-utility.md) </span><span class="sxs-lookup"><span data-stu-id="9f457-710">[Start the sqlcmd Utility](../relational-databases/scripting/sqlcmd-start-the-utility.md) </span></span>  
 <span data-ttu-id="9f457-711">[sqlcmd を使用した Transact-SQL スクリプト ファイルの実行](../relational-databases/scripting/sqlcmd-run-transact-sql-script-files.md) </span><span class="sxs-lookup"><span data-stu-id="9f457-711">[Run Transact-SQL Script Files Using sqlcmd](../relational-databases/scripting/sqlcmd-run-transact-sql-script-files.md) </span></span>  
 <span data-ttu-id="9f457-712">[sqlcmd ユーティリティの使用](../relational-databases/scripting/sqlcmd-use-the-utility.md) </span><span class="sxs-lookup"><span data-stu-id="9f457-712">[Use the sqlcmd Utility](../relational-databases/scripting/sqlcmd-use-the-utility.md) </span></span>  
 <span data-ttu-id="9f457-713">[sqlcmd でのスクリプト変数の使用](../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md) </span><span class="sxs-lookup"><span data-stu-id="9f457-713">[Use sqlcmd with Scripting Variables](../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md) </span></span>  
 <span data-ttu-id="9f457-714">[sqlcmd によるデータベース エンジンへの接続](../relational-databases/scripting/sqlcmd-connect-to-the-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="9f457-714">[Connect to the Database Engine With sqlcmd](../relational-databases/scripting/sqlcmd-connect-to-the-database-engine.md) </span></span>  
 <span data-ttu-id="9f457-715">[クエリ エディターによる SQLCMD スクリプトの編集](../relational-databases/scripting/edit-sqlcmd-scripts-with-query-editor.md) </span><span class="sxs-lookup"><span data-stu-id="9f457-715">[Edit SQLCMD Scripts with Query Editor](../relational-databases/scripting/edit-sqlcmd-scripts-with-query-editor.md) </span></span>  
 <span data-ttu-id="9f457-716">[ジョブ ステップの管理](../ssms/agent/manage-job-steps.md) </span><span class="sxs-lookup"><span data-stu-id="9f457-716">[Manage Job Steps](../ssms/agent/manage-job-steps.md) </span></span>  
 [<span data-ttu-id="9f457-717">CmdExec ジョブ ステップの作成</span><span class="sxs-lookup"><span data-stu-id="9f457-717">Create a CmdExec Job Step</span></span>](../ssms/agent/create-a-cmdexec-job-step.md)  
  
  
