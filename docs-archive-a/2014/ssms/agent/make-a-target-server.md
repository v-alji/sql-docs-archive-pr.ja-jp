---
title: ターゲット サーバーの作成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.tsxwiz.msx.f1
- sql12.ag.tsxwiz.cover.f1
- sql12.ag.tsxwiz.credentials.f1
- sql12.ag.tsxwiz.complete.f1
helpviewer_keywords:
- Target Server Wizard
- SQL Server Agent jobs, target servers
- target servers [SQL Server], creating
ms.assetid: 13aabe2d-67fe-4c67-8d49-2928dd705b7a
author: stevestein
ms.author: sstein
ms.openlocfilehash: bd60a19234d186bb0912978589fa60fd8e8a8c22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711581"
---
# <a name="make-a-target-server"></a><span data-ttu-id="48733-102">ターゲット サーバーの作成</span><span class="sxs-lookup"><span data-stu-id="48733-102">Make a Target Server</span></span>
  <span data-ttu-id="48733-103">このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../includes/tsql-md.md)]、または SQL Server 管理オブジェクト (SMO) を使用して、ターゲット サーバーを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="48733-103">This topic describes how to make a target server in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects (SMO).</span></span>  
  
 <span data-ttu-id="48733-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="48733-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="48733-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="48733-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="48733-106">Security</span><span class="sxs-lookup"><span data-stu-id="48733-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="48733-107">**ターゲット サーバーを作成するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="48733-107">**To make a target server, using:**</span></span>  
  
     [<span data-ttu-id="48733-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="48733-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="48733-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="48733-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="48733-110">SMO</span><span class="sxs-lookup"><span data-stu-id="48733-110">SMO</span></span>](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="48733-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="48733-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="48733-112">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="48733-112">Security</span></span>  
 <span data-ttu-id="48733-113">プロキシに関連付けられているステップがある分散ジョブは、ターゲット サーバーのプロキシ アカウントのコンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="48733-113">Distributed jobs that have steps which are associated with a proxy run under the context of the proxy account on the target server.</span></span> <span data-ttu-id="48733-114">次の条件を満たしていることを確認してください。満たしていないと、プロキシに関連付けられているジョブ ステップがマスター サーバーから対象サーバーにダウンロードされません。</span><span class="sxs-lookup"><span data-stu-id="48733-114">Make sure that the following conditions are met or job steps that are associated with a proxy will not be downloaded from the master server to the target:</span></span>  
  
-   <span data-ttu-id="48733-115">マスターサーバーレジストリサブキー **\ HKEY_LOCAL_MACHINE \software\microsoft\microsoft SQL Server \\ < *instance_name*> \ SQL server Agent\AllowDownloadedJobsToMatchProxyName** (REG_DWORD) が 1 (true) に設定されています。</span><span class="sxs-lookup"><span data-stu-id="48733-115">The master server registry subkey **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<*instance_name*>\SQL Server Agent\AllowDownloadedJobsToMatchProxyName** (REG_DWORD) is set to 1 (true).</span></span> <span data-ttu-id="48733-116">既定では、この値は 0 (false) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="48733-116">By default, this subkey is set to 0 (false).</span></span>  
  
-   <span data-ttu-id="48733-117">ジョブ ステップを実行するマスター サーバー プロキシ アカウントと同じ名前を持つターゲット サーバーにプロキシ アカウントが存在すること。</span><span class="sxs-lookup"><span data-stu-id="48733-117">A proxy account exists on the target server that has the same name as the master server proxy account under which the job step runs.</span></span>  
  
 <span data-ttu-id="48733-118">マスター サーバーからターゲット サーバーにプロキシ アカウントをダウンロード中に、これらのアカウントを使用するジョブ ステップが失敗した場合は、**msdb** データベースの **sysdownloadlist** テーブルの **error_message** 列を参照して、以下のエラー メッセージの有無を確認します。</span><span class="sxs-lookup"><span data-stu-id="48733-118">If job steps that use proxy accounts fail when downloading them from the master server to the target server, you can check the **error_message** column in the **sysdownloadlist** table in the **msdb** database for the following error messages:</span></span>  
  
-   <span data-ttu-id="48733-119">"ジョブ ステップではプロキシ アカウントが必要ですが、ターゲット サーバーで一致するプロキシが無効です。"</span><span class="sxs-lookup"><span data-stu-id="48733-119">"The job step requires a proxy account, however proxy matching is disabled on the target server."</span></span>  
  
     <span data-ttu-id="48733-120">このエラーを解決するには、 **AllowDownloadedJobsToMatchProxyName** レジストリ サブキーを 1 に設定します。</span><span class="sxs-lookup"><span data-stu-id="48733-120">To resolve this error, set the **AllowDownloadedJobsToMatchProxyName** registry subkey to 1.</span></span>  
  
-   <span data-ttu-id="48733-121">"プロキシ アカウントが見つかりませんでした。"</span><span class="sxs-lookup"><span data-stu-id="48733-121">"Proxy not found."</span></span>  
  
     <span data-ttu-id="48733-122">このエラーを解決するには、ターゲット サーバー上にプロキシ アカウントが存在し、ジョブ ステップを実行するマスター サーバー プロキシ アカウントと同じ名前が付けられているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="48733-122">To resolve this error, make sure a proxy account exists on the target server that has the same name as the master server proxy account under which the job step runs.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="48733-123">Permissions</span><span class="sxs-lookup"><span data-stu-id="48733-123">Permissions</span></span>  
 <span data-ttu-id="48733-124">このプロシージャの実行権限は、既定では `sysadmin` 固定サーバー ロールのメンバーに与えられています。</span><span class="sxs-lookup"><span data-stu-id="48733-124">Permissions to execute this procedure default to members of the `sysadmin` fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="48733-125">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="48733-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-make-a-target-server"></a><span data-ttu-id="48733-126">ターゲット サーバーを作成するには</span><span class="sxs-lookup"><span data-stu-id="48733-126">To make a target server</span></span>  
  
1.  <span data-ttu-id="48733-127">**オブジェクトエクスプローラー**で、のインスタンスに接続し、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="48733-127">In **Object Explorer,** connect to an instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="48733-128">**[SQL Server エージェント]** を右クリックし、 **[マルチ サーバーの管理]** をポイントして、 **[対象サーバーに設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="48733-128">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Make this a Target**.</span></span> <span data-ttu-id="48733-129">**ターゲット サーバー設定ウィザード**を使用して、ターゲット サーバーを設定します。</span><span class="sxs-lookup"><span data-stu-id="48733-129">The **Target Server Wizard** guides you through the process of making a target server.</span></span>  
  
3.  <span data-ttu-id="48733-130">**[マスター サーバーの選択]** ページで、このターゲット サーバーが受け取るジョブの送信元のマスター サーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="48733-130">From the **Select a Master Server** page, select the master server that this target server will receive jobs from.</span></span>  
  
     <span data-ttu-id="48733-131">**[サーバーの選択]**</span><span class="sxs-lookup"><span data-stu-id="48733-131">**Pick Server**</span></span>  
     <span data-ttu-id="48733-132">マスター サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="48733-132">Connect to the master server.</span></span>  
  
     <span data-ttu-id="48733-133">**[このサーバーの説明]**</span><span class="sxs-lookup"><span data-stu-id="48733-133">**Description of this server**</span></span>  
     <span data-ttu-id="48733-134">このターゲット サーバーの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="48733-134">Type a description for this target server.</span></span> <span data-ttu-id="48733-135">この説明はターゲット サーバーからマスター サーバーにアップロードされます。</span><span class="sxs-lookup"><span data-stu-id="48733-135">The target server uploads this description to the master server.</span></span>  
  
4.  <span data-ttu-id="48733-136">**[マスター サーバー ログインの資格情報]** ページで、必要に応じてターゲット サーバーに新しいログインを作成します。</span><span class="sxs-lookup"><span data-stu-id="48733-136">From the **Master Server Login Credentials** page, create a new login on the target server, if necessary.</span></span>  
  
     <span data-ttu-id="48733-137">**[必要に応じて新しいログインを作成し、MSX へのアクセス権を割り当てる]**</span><span class="sxs-lookup"><span data-stu-id="48733-137">**Create a new login if necessary and assign it rights to the MSX**</span></span>  
     <span data-ttu-id="48733-138">指定されたログインが存在しない場合に、新しいログインをターゲット サーバーに作成します。</span><span class="sxs-lookup"><span data-stu-id="48733-138">Create a new login on the target server if the login specified does not already exist.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="48733-139">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="48733-139">Using Transact-SQL</span></span>  
  
#### <a name="to-make-a-target-server"></a><span data-ttu-id="48733-140">ターゲット サーバーを作成するには</span><span class="sxs-lookup"><span data-stu-id="48733-140">To make a target server</span></span>  
  
1.  <span data-ttu-id="48733-141">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="48733-141">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="48733-142">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="48733-142">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="48733-143">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="48733-143">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="48733-144">この例では、現在のサーバーを AdventureWorks1 マスター サーバーに追加します。</span><span class="sxs-lookup"><span data-stu-id="48733-144">This example enlists the current server into the AdventureWorks1 master server.</span></span> <span data-ttu-id="48733-145">現在のサーバーの場所は、Building 21 の Room 309 の Rack 5 です。</span><span class="sxs-lookup"><span data-stu-id="48733-145">The location for the current server is Building 21, Room 309, Rack 5.</span></span>  
  
    ```sql
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_msx_enlist N'AdventureWorks1',   
        N'Building 21, Room 309, Rack 5' ;   
    GO;  
    ```  
  
     <span data-ttu-id="48733-146">詳細については、「 [sp_msx_enlist &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48733-146">For more information, see [sp_msx_enlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects-smo"></a><a name="PowerShellProcedure"></a><span data-ttu-id="48733-147">SQL Server 管理オブジェクト (SMO) の使用</span><span class="sxs-lookup"><span data-stu-id="48733-147">Using SQL Server Management Objects (SMO)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48733-148">参照</span><span class="sxs-lookup"><span data-stu-id="48733-148">See Also</span></span>  
 [<span data-ttu-id="48733-149">エンタープライズ全体の管理の自動化</span><span class="sxs-lookup"><span data-stu-id="48733-149">Automated Administration Across an Enterprise</span></span>](automated-administration-across-an-enterprise.md)  
