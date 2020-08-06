---
title: SQL Server エージェントのプロキシの変更 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- proxies [SQL Server Agent], modifying
- modifying SQL Server Agent proxy
ms.assetid: 6e1dfbaa-8089-4813-940c-d5a2e13d8552
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2f86793a8ddcc6fe8f981d6b367d2178c5a794ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634798"
---
# <a name="modify-a-sql-server-agent-proxy"></a><span data-ttu-id="41ede-102">Modify a SQL Server Agent Proxy</span><span class="sxs-lookup"><span data-stu-id="41ede-102">Modify a SQL Server Agent Proxy</span></span>
  <span data-ttu-id="41ede-103">このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は、またはを使用して、でエージェントプロキシを変更する方法について説明し [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="41ede-103">This topic describes how to modify a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="41ede-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="41ede-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="41ede-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="41ede-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="41ede-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="41ede-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="41ede-107">Security</span><span class="sxs-lookup"><span data-stu-id="41ede-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="41ede-108">**SQL Server エージェント プロキシを変更する方法:**</span><span class="sxs-lookup"><span data-stu-id="41ede-108">**To modify a SQL Server Agent proxy, using:**</span></span>  
  
     [<span data-ttu-id="41ede-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="41ede-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="41ede-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="41ede-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="41ede-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="41ede-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="41ede-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="41ede-112">Limitations and Restrictions</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="41ede-113">エージェント プロキシは、資格情報を使用して Windows ユーザー アカウントに関する情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="41ede-113">Agent proxies use credentials to store information about Windows user accounts.</span></span> <span data-ttu-id="41ede-114">資格情報で指定されているユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているコンピューターで "バッチ ジョブとしてログオン" するためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="41ede-114">The user specified in the credential must have "Log on as a batch job" permission on the computer on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="41ede-115">エージェントは、ジョブ ステップを実行するごとに、プロキシからサブシステムへのアクセス許可を確認し、アクセスを確立します。</span><span class="sxs-lookup"><span data-stu-id="41ede-115">Agent checks subsystem access for a proxy and gives access to the proxy each time the job step runs.</span></span> <span data-ttu-id="41ede-116">プロキシにサブシステムへのアクセス許可がない場合、ジョブ ステップは失敗します。</span><span class="sxs-lookup"><span data-stu-id="41ede-116">If the proxy no longer has access to the subsystem, the job step fails.</span></span> <span data-ttu-id="41ede-117">プロキシにアクセス許可がある場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントはプロキシで指定されているユーザーの権限を借用してジョブ ステップを実行します。</span><span class="sxs-lookup"><span data-stu-id="41ede-117">Otherwise, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent impersonates the user that is specified in the proxy and runs the job step.</span></span>  
  
-   <span data-ttu-id="41ede-118">ユーザーのログインにプロキシへのアクセス許可がある場合、またはプロキシへのアクセス許可のあるロールにユーザーが属している場合、このユーザーはジョブ ステップでプロキシを使用できます。</span><span class="sxs-lookup"><span data-stu-id="41ede-118">If the login for the user has access to the proxy, or the user belongs to any role with access to the proxy, the user can use the proxy in a job step.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="41ede-119">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="41ede-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="41ede-120">Permissions</span><span class="sxs-lookup"><span data-stu-id="41ede-120">Permissions</span></span>  
 <span data-ttu-id="41ede-121">プロキシ アカウントを作成、変更、または削除できるのは、 **sysadmin** 固定サーバー ロールのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="41ede-121">Only members of the **sysadmin** fixed server role can create, modify, or delete proxy accounts.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="41ede-122">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="41ede-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-ssnoversion-agent-proxy"></a><span data-ttu-id="41ede-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント プロキシを変更するには</span><span class="sxs-lookup"><span data-stu-id="41ede-123">To modify a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy</span></span>  
  
1.  <span data-ttu-id="41ede-124">**オブジェクト エクスプローラー**で、変更する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント プロキシを含むサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="41ede-124">In **Object Explorer**, click the plus sign to expand the server that contains the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy account that you want to modify.</span></span>  
  
2.  <span data-ttu-id="41ede-125">プラス記号をクリックして **[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="41ede-125">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="41ede-126">プラス記号をクリックして **[プロキシ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="41ede-126">Click the plus sign to expand the **Proxies** folder.</span></span>  
  
4.  <span data-ttu-id="41ede-127">プロキシにサブシステムのノードを展開するプラス記号をクリックします (たとえば **[ActiveX スクリプト]**)。</span><span class="sxs-lookup"><span data-stu-id="41ede-127">Click the plus sign to expand the subsystem node for the proxy (for example, **ActiveX Script**).</span></span>  
  
5.  <span data-ttu-id="41ede-128">変更するプロキシ アカウントを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="41ede-128">Right-click the proxy account you want to modify and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="41ede-129">[ _Proxy_name_**プロキシアカウントのプロパティ**] ダイアログボックスで、必要に応じてプロキシアカウントを変更します。</span><span class="sxs-lookup"><span data-stu-id="41ede-129">In the _proxy_name_**Proxy Account Properties** dialog box, make changes to the proxy account as necessary.</span></span> <span data-ttu-id="41ede-130">このダイアログ ボックスのオプションについては、「 [SQL Server エージェント プロキシの作成](create-a-sql-server-agent-proxy.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="41ede-130">For more information on the options in this dialog box, see [Create a SQL Server Agent Proxy](create-a-sql-server-agent-proxy.md).</span></span>  
  
7.  <span data-ttu-id="41ede-131">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="41ede-131">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="41ede-132">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="41ede-132">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-a-ssnoversion-agent-proxy"></a><span data-ttu-id="41ede-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント プロキシを変更するには</span><span class="sxs-lookup"><span data-stu-id="41ede-133">To modify a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy</span></span>  
  
1.  <span data-ttu-id="41ede-134">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="41ede-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="41ede-135">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="41ede-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="41ede-136">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="41ede-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Disables the proxy named 'Catalog application proxy'.  
    USE msdb ;  
    GO  
    EXEC dbo.sp_update_proxy  
        @proxy_name = 'Catalog application proxy',  
        @enabled = 0;  
    GO  
    ```  
  
 <span data-ttu-id="41ede-137">詳細については、「 [sp_update_proxy &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-proxy-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="41ede-137">For more information, see [sp_update_proxy &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-proxy-transact-sql).</span></span>  
  
  
