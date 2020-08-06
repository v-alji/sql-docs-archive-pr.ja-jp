---
title: SQL Server エージェントのプロキシの削除 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- deleting SQL Server Agent proxies
- proxies [SQL Server Agent], deleting
- removing SQL Server Agent proxies
ms.assetid: 9248841d-7294-47d4-94f3-b34a0521fabc
author: stevestein
ms.author: sstein
ms.openlocfilehash: a672c6392e2ffed3ca2a7ed655b806d9d093b10c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643073"
---
# <a name="delete-a-sql-server-agent-proxy"></a><span data-ttu-id="7d839-102">Delete a SQL Server Agent Proxy</span><span class="sxs-lookup"><span data-stu-id="7d839-102">Delete a SQL Server Agent Proxy</span></span>
  <span data-ttu-id="7d839-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で [!INCLUDE[tsql](../../includes/tsql-md.md)]エージェント プロキシ アカウントを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7d839-103">This topic describes how to delete a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy account in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="7d839-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="7d839-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="7d839-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="7d839-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="7d839-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="7d839-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="7d839-107">Security</span><span class="sxs-lookup"><span data-stu-id="7d839-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="7d839-108">**SQL Server エージェント プロキシ アカウントを削除する方法:**</span><span class="sxs-lookup"><span data-stu-id="7d839-108">**To delete a SQL Server Agent proxy account, using:**</span></span>  
  
     [<span data-ttu-id="7d839-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="7d839-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="7d839-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7d839-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7d839-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="7d839-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="7d839-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="7d839-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="7d839-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのプロキシ アカウントを削除する場合は、そのプロキシがアクティブなジョブ ステップを参照していないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="7d839-113">When you delete a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy account, make sure the proxy does not reference any active job steps.</span></span> <span data-ttu-id="7d839-114">プロキシを参照しているジョブ ステップを確認するには、プロキシを右クリックし、 **[プロパティ]** をクリックします。 _proxy_name_**プロキシ アカウントのプロパティ]** ダイアログ ボックスで、 **[参照]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d839-114">To check for any job steps that reference the proxy, right-click the proxy, select **Properties**, and then, in the _proxy_name_**Proxy Account Properties** dialog box, select the **References** page.</span></span> <span data-ttu-id="7d839-115">プロキシを削除すると、そのプロキシを使用するすべてのジョブ ステップを再割り当てするためのオプションが **[オブジェクトの削除]** ダイアログ ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7d839-115">If you delete a proxy, you are given the option to reassign all job steps that use that proxy in the **Delete Object** dialog box.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7d839-116">エージェント プロキシは、資格情報を使用して Windows ユーザー アカウントに関する情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="7d839-116">Agent proxies use credentials to store information about Windows user accounts.</span></span> <span data-ttu-id="7d839-117">資格情報で指定されているユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているコンピューターで "バッチ ジョブとしてログオン" するためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="7d839-117">The user specified in the credential must have "Log on as a batch job" permission on the computer on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7d839-118">エージェントは、ジョブ ステップを実行するごとに、プロキシからサブシステムへのアクセス許可を確認し、アクセスを確立します。</span><span class="sxs-lookup"><span data-stu-id="7d839-118">Agent checks subsystem access for a proxy and gives access to the proxy each time the job step runs.</span></span> <span data-ttu-id="7d839-119">プロキシにサブシステムへのアクセス許可がない場合、ジョブ ステップは失敗します。</span><span class="sxs-lookup"><span data-stu-id="7d839-119">If the proxy no longer has access to the subsystem, the job step fails.</span></span> <span data-ttu-id="7d839-120">プロキシにアクセス許可がある場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントはプロキシで指定されているユーザーの権限を借用してジョブ ステップを実行します。</span><span class="sxs-lookup"><span data-stu-id="7d839-120">Otherwise, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent impersonates the user that is specified in the proxy and runs the job step.</span></span>  
  
-   <span data-ttu-id="7d839-121">ユーザーのログインにプロキシへのアクセス許可がある場合、またはプロキシへのアクセス許可のあるロールにユーザーが属している場合、このユーザーはジョブ ステップでプロキシを使用できます。</span><span class="sxs-lookup"><span data-stu-id="7d839-121">If the login for the user has access to the proxy, or the user belongs to any role with access to the proxy, the user can use the proxy in a job step.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7d839-122">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="7d839-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7d839-123">Permissions</span><span class="sxs-lookup"><span data-stu-id="7d839-123">Permissions</span></span>  
 <span data-ttu-id="7d839-124">プロキシ アカウントを作成、変更、または削除できるのは、 **sysadmin** 固定サーバー ロールのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="7d839-124">Only members of the **sysadmin** fixed server role can create, modify, or delete proxy accounts.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="7d839-125">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="7d839-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-sql-server-agent-proxy-account"></a><span data-ttu-id="7d839-126">SQL Server エージェント プロキシ アカウントを削除するには</span><span class="sxs-lookup"><span data-stu-id="7d839-126">To delete a SQL Server Agent proxy account</span></span>  
  
1.  <span data-ttu-id="7d839-127">**オブジェクト エクスプローラー**で、削除するプロキシ アカウントを含むサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="7d839-127">In **Object Explorer**, click the plus sign to expand a server that contains the proxy account that you want to delete.</span></span>  
  
2.  <span data-ttu-id="7d839-128">プラス記号をクリックして **[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="7d839-128">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="7d839-129">プラス記号をクリックして **[プロキシ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="7d839-129">Click the plus sign to expand the **Proxies** folder.</span></span>  
  
4.  <span data-ttu-id="7d839-130">削除するプロキシ アカウントを含むサブシステムをプラス記号をクリックして展開します (例: **[ActiveX スクリプト]**)。</span><span class="sxs-lookup"><span data-stu-id="7d839-130">Click the plus sign to expand the subsystem that contains the proxy account you want to delete (for example, **ActiveX Script)**.</span></span>  
  
5.  <span data-ttu-id="7d839-131">削除するプロキシ アカウントを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d839-131">Right-click the proxy account that you want to delete and select **Delete**.</span></span>  
  
6.  <span data-ttu-id="7d839-132">**[オブジェクトの削除]** ダイアログ ボックスで、削除するプロキシ アカウントが選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="7d839-132">In the **Delete Object** dialog box, confirm that the correct proxy account is selected.</span></span> <span data-ttu-id="7d839-133">現在のプロキシ アカウントを参照するジョブ ステップを別のアカウントに再割り当てするには、 **[再割り当て]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="7d839-133">Check the **Reassign to** check box to reassign the job steps that reference this proxy account to another account.</span></span>  
  
7.  <span data-ttu-id="7d839-134">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d839-134">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="7d839-135">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="7d839-135">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-sql-server-agent-proxy-account"></a><span data-ttu-id="7d839-136">SQL Server エージェント プロキシ アカウントを削除するには</span><span class="sxs-lookup"><span data-stu-id="7d839-136">To delete a SQL Server Agent proxy account</span></span>  
  
1.  <span data-ttu-id="7d839-137">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="7d839-137">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="7d839-138">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d839-138">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="7d839-139">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d839-139">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- deletes the proxy "Catalog application proxy"  
    USE msdb ;  
    GO  
    EXEC dbo.sp_delete_proxy  
        @proxy_name = N'Catalog application proxy' ;  
    GO  
    ```  
  
 <span data-ttu-id="7d839-140">詳細については、「 [sp_delete_proxy &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d839-140">For more information, see [sp_delete_proxy &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql).</span></span>  
  
  
