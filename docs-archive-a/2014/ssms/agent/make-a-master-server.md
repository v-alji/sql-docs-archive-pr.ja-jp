---
title: マスター サーバーの作成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.msxwiz.complete.f1
- sql12.ag.msxwiz.target.f1
- sql12.ag.msxwiz.login.f1
- sql12.ag.msxwiz.cover.f1
- sql12.ag.msxwiz.operator.f1
helpviewer_keywords:
- master servers [SQL Server], creating
- wizards [SQL Server Management Studio], Master Server Wizard
- SQL Server Agent jobs, master servers
- Master Server Wizard
ms.assetid: 05739a73-1fdf-4d9d-92a6-70f328380322
author: stevestein
ms.author: sstein
ms.openlocfilehash: ce8e7428aaf8ba459bcf6831988c61da3f192bac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640319"
---
# <a name="make-a-master-server"></a><span data-ttu-id="4efef-102">Make a Master Server</span><span class="sxs-lookup"><span data-stu-id="4efef-102">Make a Master Server</span></span>
  <span data-ttu-id="4efef-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用してマスター サーバー [!INCLUDE[tsql](../../includes/tsql-md.md)]を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4efef-103">This topic describes how to make a master server [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="4efef-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="4efef-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4efef-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="4efef-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4efef-106">Security</span><span class="sxs-lookup"><span data-stu-id="4efef-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4efef-107">**マスター サーバーを作成するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="4efef-107">**To make a master server, using:**</span></span>  
  
     [<span data-ttu-id="4efef-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4efef-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4efef-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4efef-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4efef-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="4efef-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4efef-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="4efef-111">Security</span></span>  
 <span data-ttu-id="4efef-112">プロキシに関連付けられているステップがある分散ジョブは、ターゲット サーバーのプロキシ アカウントのコンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="4efef-112">Distributed jobs that have steps which are associated with a proxy run under the context of the proxy account on the target server.</span></span> <span data-ttu-id="4efef-113">次の条件を満たしていることを確認してください。満たしていないと、プロキシに関連付けられているジョブ ステップがマスター サーバーから対象サーバーにダウンロードされません。</span><span class="sxs-lookup"><span data-stu-id="4efef-113">Make sure that the following conditions are met or job steps that are associated with a proxy will not be downloaded from the master server to the target:</span></span>  
  
-   <span data-ttu-id="4efef-114">マスターサーバーレジストリサブキー **\ HKEY_LOCAL_MACHINE \software\microsoft\microsoft SQL Server \\ < *instance_name*> \ SQL server Agent\AllowDownloadedJobsToMatchProxyName** (REG_DWORD) が 1 (true) に設定されています。</span><span class="sxs-lookup"><span data-stu-id="4efef-114">The master server registry subkey **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<*instance_name*>\SQL Server Agent\AllowDownloadedJobsToMatchProxyName** (REG_DWORD) is set to 1 (true).</span></span> <span data-ttu-id="4efef-115">既定では、この値は 0 (false) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="4efef-115">By default, this subkey is set to 0 (false).</span></span>  
  
-   <span data-ttu-id="4efef-116">ジョブ ステップを実行するマスター サーバー プロキシ アカウントと同じ名前を持つターゲット サーバーにプロキシ アカウントが存在すること。</span><span class="sxs-lookup"><span data-stu-id="4efef-116">A proxy account exists on the target server that has the same name as the master server proxy account under which the job step runs.</span></span>  
  
 <span data-ttu-id="4efef-117">マスター サーバーからターゲット サーバーにプロキシ アカウントをダウンロード中に、これらのアカウントを使用するジョブ ステップが失敗した場合は、**msdb** データベースの **sysdownloadlist** テーブルの **error_message** 列を参照して、以下のエラー メッセージの有無を確認します。</span><span class="sxs-lookup"><span data-stu-id="4efef-117">If job steps that use proxy accounts fail when downloading them from the master server to the target server, you can check the **error_message** column in the **sysdownloadlist** table in the **msdb** database for the following error messages:</span></span>  
  
-   <span data-ttu-id="4efef-118">"ジョブ ステップではプロキシ アカウントが必要ですが、ターゲット サーバーで一致するプロキシが無効です。"</span><span class="sxs-lookup"><span data-stu-id="4efef-118">"The job step requires a proxy account, however proxy matching is disabled on the target server."</span></span>  
  
     <span data-ttu-id="4efef-119">このエラーを解決するには、 **AllowDownloadedJobsToMatchProxyName** レジストリ サブキーを 1 に設定します。</span><span class="sxs-lookup"><span data-stu-id="4efef-119">To resolve this error, set the **AllowDownloadedJobsToMatchProxyName** registry subkey to 1.</span></span>  
  
-   <span data-ttu-id="4efef-120">"プロキシ アカウントが見つかりませんでした。"</span><span class="sxs-lookup"><span data-stu-id="4efef-120">"Proxy not found."</span></span>  
  
     <span data-ttu-id="4efef-121">このエラーを解決するには、ターゲット サーバー上にプロキシ アカウントが存在し、ジョブ ステップを実行するマスター サーバー プロキシ アカウントと同じ名前が付けられているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="4efef-121">To resolve this error, make sure a proxy account exists on the target server that has the same name as the master server proxy account under which the job step runs.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4efef-122">Permissions</span><span class="sxs-lookup"><span data-stu-id="4efef-122">Permissions</span></span>  
 <span data-ttu-id="4efef-123">このプロシージャの実行権限は、既定では `sysadmin` 固定サーバー ロールのメンバーに与えられています。</span><span class="sxs-lookup"><span data-stu-id="4efef-123">Permissions to execute this procedure default to members of the `sysadmin` fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4efef-124">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="4efef-124">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-make-a-master-server"></a><span data-ttu-id="4efef-125">マスター サーバーを作成するには</span><span class="sxs-lookup"><span data-stu-id="4efef-125">To make a master server</span></span>  
  
1.  <span data-ttu-id="4efef-126">**オブジェクトエクスプローラー**で、のインスタンスに接続し、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="4efef-126">In **Object Explorer,** connect to an instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="4efef-127">**[SQL Server エージェント]** を右クリックし、 **[マルチサーバーの管理]** をポイントして、 **[マスター サーバーに設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4efef-127">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Make this a Master**.</span></span> <span data-ttu-id="4efef-128">**マスター サーバー ウィザード** を使用してマスター サーバーを作成し、ターゲット サーバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="4efef-128">The **Master Server Wizard** guides you through the process of making a master server and adding target servers.</span></span>  
  
3.  <span data-ttu-id="4efef-129">**[マスター サーバー オペレーター]** ページで、マスター サーバーのオペレーターを設定します。電子メールまたはポケットベルを使用してオペレーターに通知を送信するには、電子メールが送信されるように [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを設定しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="4efef-129">From the **Master Server Operator** page, configure an operator for the master server To send notifications to operators by using e-mail or pagers, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to send e-mail.</span></span> <span data-ttu-id="4efef-130">**net send**を使用してオペレーターに通知を送信するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントが置かれているサーバーで Messenger サービスが実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="4efef-130">To send notifications to operators by using **net send**, the Messenger service must be running on the server where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent resides.</span></span>  
  
     <span data-ttu-id="4efef-131">**電子メールアドレス**</span><span class="sxs-lookup"><span data-stu-id="4efef-131">**E-mail address**</span></span>  
     <span data-ttu-id="4efef-132">オペレーターの電子メール アドレスを設定します。</span><span class="sxs-lookup"><span data-stu-id="4efef-132">Sets the e-mail address for the operator.</span></span>  
  
     <span data-ttu-id="4efef-133">**[ポケットベル アドレス]**</span><span class="sxs-lookup"><span data-stu-id="4efef-133">**Pager address**</span></span>  
     <span data-ttu-id="4efef-134">オペレーターのポケットベル メール アドレスを設定します。</span><span class="sxs-lookup"><span data-stu-id="4efef-134">Sets the pager e-mail address for the operator.</span></span>  
  
     <span data-ttu-id="4efef-135">**[Net Send アドレス]**</span><span class="sxs-lookup"><span data-stu-id="4efef-135">**Net send address**</span></span>  
     <span data-ttu-id="4efef-136">オペレーターの **net send** アドレスを設定します。</span><span class="sxs-lookup"><span data-stu-id="4efef-136">Sets the **net send** address for the operator.</span></span>  
  
4.  <span data-ttu-id="4efef-137">**[ターゲット サーバー]** ページで、マスター サーバーのターゲット サーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="4efef-137">From the **Target Server** page, select target servers for the master server.</span></span>  
  
     <span data-ttu-id="4efef-138">**[登録済みサーバー]**</span><span class="sxs-lookup"><span data-stu-id="4efef-138">**Registered Servers**</span></span>  
     <span data-ttu-id="4efef-139">Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] に登録されているサーバーで、まだターゲット サーバーになっていないものを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="4efef-139">Lists the servers registered in Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] that are not already target servers.</span></span>  
  
     <span data-ttu-id="4efef-140">**対象サーバー**</span><span class="sxs-lookup"><span data-stu-id="4efef-140">**Target Servers**</span></span>  
     <span data-ttu-id="4efef-141">ターゲット サーバーであるサーバーを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="4efef-141">Lists the servers that are target servers.</span></span>  
  
     **>**  
     <span data-ttu-id="4efef-142">選択したサーバーをターゲット サーバーの一覧に移動します。</span><span class="sxs-lookup"><span data-stu-id="4efef-142">Move the selected server to the target server list.</span></span>  
  
     **>>**  
     <span data-ttu-id="4efef-143">すべてのサーバーをターゲット サーバーの一覧に移動します。</span><span class="sxs-lookup"><span data-stu-id="4efef-143">Move all servers to the target server list.</span></span>  
  
     **<**  
     <span data-ttu-id="4efef-144">選択したサーバーをターゲット サーバーの一覧から削除します。</span><span class="sxs-lookup"><span data-stu-id="4efef-144">Remove the selected server from the target server list.</span></span>  
  
     **<<**  
     <span data-ttu-id="4efef-145">すべてのサーバーをターゲット サーバーの一覧から削除します。</span><span class="sxs-lookup"><span data-stu-id="4efef-145">Remove all servers from the target server list.</span></span>  
  
     <span data-ttu-id="4efef-146">**[接続の追加]**</span><span class="sxs-lookup"><span data-stu-id="4efef-146">**Add connection**</span></span>  
     <span data-ttu-id="4efef-147">サーバーを登録せずにターゲット サーバーの一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="4efef-147">Add a server to the target server list without registering the server.</span></span>  
  
     <span data-ttu-id="4efef-148">**接続**</span><span class="sxs-lookup"><span data-stu-id="4efef-148">**Connection**</span></span>  
     <span data-ttu-id="4efef-149">選択したサーバーの接続プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="4efef-149">Change the connection properties for the selected server.</span></span>  
  
5.  <span data-ttu-id="4efef-150">**[マスター サーバー ログインの資格情報]** ページで、必要に応じてターゲット サーバーの新しいログインを作成してマスター サーバーへの権利を割り当てるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="4efef-150">From the **Master Server Login Credentials** page to specify if you want to create a new login for the target server, if necessary, and assign it rights to the master server.</span></span>  
  
     <span data-ttu-id="4efef-151">**[必要に応じて新しいログインを作成し、MSX へのアクセス権を割り当てる]**</span><span class="sxs-lookup"><span data-stu-id="4efef-151">**Create a new login if necessary and assign it rights to the MSX**</span></span>  
     <span data-ttu-id="4efef-152">指定されたログインが存在しない場合に、新しいログインをターゲット サーバーに作成します。</span><span class="sxs-lookup"><span data-stu-id="4efef-152">Create a new login on the target server if the login specified does not already exist.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4efef-153">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="4efef-153">Using Transact-SQL</span></span>  
  
#### <a name="to-make-a-master-server"></a><span data-ttu-id="4efef-154">マスター サーバーを作成するには</span><span class="sxs-lookup"><span data-stu-id="4efef-154">To make a master server</span></span>  
  
1.  <span data-ttu-id="4efef-155">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="4efef-155">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4efef-156">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4efef-156">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4efef-157">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4efef-157">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="4efef-158">この例では、現在のサーバーを AdventureWorks1 マスター サーバーに追加します。</span><span class="sxs-lookup"><span data-stu-id="4efef-158">This example enlists the current server into the AdventureWorks1 master server.</span></span> <span data-ttu-id="4efef-159">現在のサーバーの場所は、Building 21 の Room 309 の Rack 5 です。</span><span class="sxs-lookup"><span data-stu-id="4efef-159">The location for the current server is Building 21, Room 309, Rack 5.</span></span>  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_msx_enlist N'AdventureWorks1',   
    N'Building 21, Room 309, Rack 5' ;   
GO;  
```  
  
 <span data-ttu-id="4efef-160">詳細については、「 [sp_msx_enlist &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4efef-160">For more information, see [sp_msx_enlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4efef-161">参照</span><span class="sxs-lookup"><span data-stu-id="4efef-161">See Also</span></span>  
 <span data-ttu-id="4efef-162">[マルチサーバー環境の作成](create-a-multiserver-environment.md) </span><span class="sxs-lookup"><span data-stu-id="4efef-162">[Create a Multiserver Environment](create-a-multiserver-environment.md) </span></span>  
 [<span data-ttu-id="4efef-163">エンタープライズ全体の管理の自動化</span><span class="sxs-lookup"><span data-stu-id="4efef-163">Automated Administration Across an Enterprise</span></span>](automated-administration-across-an-enterprise.md)  
  
  
