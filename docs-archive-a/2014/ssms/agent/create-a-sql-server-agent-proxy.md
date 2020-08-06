---
title: SQL Server エージェント プロキシの作成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- proxies [SQL Server Agent], creating
ms.assetid: 142e0c55-a8b9-4669-be49-b9dc602d5988
author: stevestein
ms.author: sstein
ms.openlocfilehash: a7582aef38d57b15de968d96357e56c1974d733e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643077"
---
# <a name="create-a-sql-server-agent-proxy"></a><span data-ttu-id="d48de-102">Create a SQL Server Agent Proxy</span><span class="sxs-lookup"><span data-stu-id="d48de-102">Create a SQL Server Agent Proxy</span></span>
  <span data-ttu-id="d48de-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]で SQL Server エージェント プロキシを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d48de-103">This topic describes how to create a SQL Server Agent proxy in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="d48de-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント プロキシ アカウントは、ジョブ ステップを実行できるセキュリティ コンテキストを定義します。</span><span class="sxs-lookup"><span data-stu-id="d48de-104">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy account defines a security context in which a job step can run.</span></span> <span data-ttu-id="d48de-105">各プロキシには対応するセキュリティ資格情報が 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="d48de-105">Each proxy corresponds to a security credential.</span></span> <span data-ttu-id="d48de-106">特定のジョブ ステップに権限を設定するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サブシステムに必要な権限のあるプロキシを作成し、このプロキシをジョブ ステップに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="d48de-106">To set permissions for a particular job step, create a proxy that has the required permissions for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent subsystem, and then assign that proxy to the job step.</span></span>  
  
 <span data-ttu-id="d48de-107">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="d48de-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d48de-108">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="d48de-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d48de-109">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="d48de-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="d48de-110">Security</span><span class="sxs-lookup"><span data-stu-id="d48de-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d48de-111">**SQL Server エージェント プロキシを作成する方法:**</span><span class="sxs-lookup"><span data-stu-id="d48de-111">**To create a SQL Server Agent proxy, using:**</span></span>  
  
     [<span data-ttu-id="d48de-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d48de-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="d48de-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d48de-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d48de-114">はじめに</span><span class="sxs-lookup"><span data-stu-id="d48de-114">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="d48de-115">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="d48de-115">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="d48de-116">資格情報を用意していない場合は、プロキシを作成する前に、まず資格情報を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d48de-116">You must create a credential before you create a proxy if one is not already available.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d48de-117">エージェント プロキシは、資格情報を使用して Windows ユーザー アカウントに関する情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="d48de-117">Agent proxies use credentials to store information about Windows user accounts.</span></span> <span data-ttu-id="d48de-118">資格情報で指定されているユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているコンピューターで "バッチ ジョブとしてログオン" するためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="d48de-118">The user specified in the credential must have "Log on as a batch job" permission on the computer on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d48de-119">エージェントは、ジョブ ステップを実行するごとに、プロキシからサブシステムへのアクセス許可を確認し、アクセスを確立します。</span><span class="sxs-lookup"><span data-stu-id="d48de-119">Agent checks subsystem access for a proxy and gives access to the proxy each time the job step runs.</span></span> <span data-ttu-id="d48de-120">プロキシにサブシステムへのアクセス許可がない場合、ジョブ ステップは失敗します。</span><span class="sxs-lookup"><span data-stu-id="d48de-120">If the proxy no longer has access to the subsystem, the job step fails.</span></span> <span data-ttu-id="d48de-121">プロキシにアクセス許可がある場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントはプロキシで指定されているユーザーの権限を借用してジョブ ステップを実行します。</span><span class="sxs-lookup"><span data-stu-id="d48de-121">Otherwise, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent impersonates the user that is specified in the proxy and runs the job step.</span></span>  
  
-   <span data-ttu-id="d48de-122">プロキシを作成しても、そのプロキシの資格情報で指定したユーザーの権限は変更されません。</span><span class="sxs-lookup"><span data-stu-id="d48de-122">Creation of a proxy does not change the permissions for the user that is specified in the credential for the proxy.</span></span> <span data-ttu-id="d48de-123">たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続する権限を持たないユーザーのプロキシを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d48de-123">For example, you can create a proxy for a user that does not have permission to connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d48de-124">この場合、このプロキシを使用するジョブ ステップから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に接続することはできません。</span><span class="sxs-lookup"><span data-stu-id="d48de-124">In this case, job steps that use that proxy are unable to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="d48de-125">ユーザーのログインにプロキシへのアクセス許可がある場合、またはプロキシへのアクセス許可のあるロールにユーザーが属している場合、このユーザーはジョブ ステップでプロキシを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d48de-125">If the login for the user has access to the proxy, or the user belongs to any role with access to the proxy, the user can use the proxy in a job step.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d48de-126">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="d48de-126">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d48de-127">Permissions</span><span class="sxs-lookup"><span data-stu-id="d48de-127">Permissions</span></span>  
  
-   <span data-ttu-id="d48de-128">**sysadmin** 固定サーバー ロールのメンバーだけに、プロキシ アカウントを作成、変更、または削除できる権限があります。</span><span class="sxs-lookup"><span data-stu-id="d48de-128">Only members of the **sysadmin** fixed server role have permission to create, modify, or delete proxy accounts.</span></span> <span data-ttu-id="d48de-129">固定サーバー ロール **sysadmin** のメンバーではないユーザーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの** エージェント固定データベース ロールである **SQLAgentUserRole**、 **SQLAgentReaderRole**、または **SQLAgentOperatorRole**のいずれかに追加されないと、プロキシを使用できません。</span><span class="sxs-lookup"><span data-stu-id="d48de-129">Users who are not members of the **sysadmin** fixed server role must be added to one of the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles in the **msdb** database to use proxies: **SQLAgentUserRole**, **SQLAgentReaderRole**, or **SQLAgentOperatorRole**.</span></span>  
  
-   <span data-ttu-id="d48de-130">プロキシに加えて資格情報を作成する場合は、`ALTER ANY CREDENTIAL` 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="d48de-130">Requires `ALTER ANY CREDENTIAL` permission if creating a credential in addition to the proxy.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d48de-131">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="d48de-131">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-sql-server-agent-proxy"></a><span data-ttu-id="d48de-132">SQL Server エージェント プロキシを作成するには</span><span class="sxs-lookup"><span data-stu-id="d48de-132">To create a SQL Server Agent proxy</span></span>  
  
1.  <span data-ttu-id="d48de-133">**オブジェクト エクスプ ローラー**で、SQL Server エージェント プロキシを作成するサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="d48de-133">In **Object Explorer**, click the plus sign to expand the server where you want to create a proxy on SQL Server Agent.</span></span>  
  
2.  <span data-ttu-id="d48de-134">プラス記号をクリックして **[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="d48de-134">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="d48de-135">**[プロキシ]** フォルダーを右クリックし、 **[新しいプロキシ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d48de-135">Right-click the **Proxies** folder and select **New Proxy**.</span></span>  
  
4.  <span data-ttu-id="d48de-136">**[新しいプロキシ アカウント]** ダイアログ ボックスの **[全般]** ページで、 **[プロキシ名]** ボックスにプロキシ アカウントの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="d48de-136">On the **New Proxy Account** dialog box, on the **General** page, enter the name of the proxy account in the **Proxy name** box.</span></span>  
  
5.  <span data-ttu-id="d48de-137">**[資格情報名]** ボックスに、プロキシ アカウントが使用するセキュリティ資格情報の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="d48de-137">In the **Credential name** box, enter the name of the security credential that the proxy account will use.</span></span>  
  
6.  <span data-ttu-id="d48de-138">**[説明]** ボックスに、プロキシ アカウントの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="d48de-138">In the **Description** box, enter a description for the proxy account</span></span>  
  
7.  <span data-ttu-id="d48de-139">**[以下のサブシステムに対してアクティブ]** から、このプロキシ用の適切なサブシステムを選択します (複数選択可能)。</span><span class="sxs-lookup"><span data-stu-id="d48de-139">Under **Active to the following subsystems**, select the appropriate subsystem or subsystems for this proxy.</span></span>  
  
8.  <span data-ttu-id="d48de-140">**[プリンシパル]** ページで、プロキシ アカウントへのアクセスを許可するログインまたはロールを追加するか、あるいは拒否するログインまたはロールを削除します。</span><span class="sxs-lookup"><span data-stu-id="d48de-140">On the **Principals** page, add or remove logins or roles to grant or remove access to the proxy account.</span></span>  
  
9. <span data-ttu-id="d48de-141">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d48de-141">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d48de-142">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="d48de-142">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-sql-server-agent-proxy"></a><span data-ttu-id="d48de-143">SQL Server エージェント プロキシを作成するには</span><span class="sxs-lookup"><span data-stu-id="d48de-143">To create a SQL Server Agent proxy</span></span>  
  
1.  <span data-ttu-id="d48de-144">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="d48de-144">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d48de-145">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d48de-145">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d48de-146">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d48de-146">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- creates credential CatalogApplicationCredential  
    USE msdb ;  
    GO  
    CREATE CREDENTIAL CatalogApplicationCredential WITH IDENTITY = 'REDMOND/TestUser',   
        SECRET = 'G3$1o)lkJ8HNd!';  
    GO  
    -- creates proxy "Catalog application proxy" and assigns the credential 'CatalogApplicationCredential' to it.  
    EXEC dbo.sp_add_proxy  
        @proxy_name = 'Catalog application proxy',  
        @enabled = 1,  
        @description = 'Maintenance tasks on catalog application.',  
        @credential_name = 'CatalogApplicationCredential' ;  
    GO  
    -- grants the proxy "Catalog application proxy" access to the ActiveX Scripting subsystem.  
    EXEC dbo.sp_grant_proxy_to_subsystem  
        @proxy_name = N'Catalog application proxy',  
        @subsystem_id = 2 ;  
    GO  
    ```  
  
 <span data-ttu-id="d48de-147">詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d48de-147">For more information, see:</span></span>  
  
-   [<span data-ttu-id="d48de-148">CREATE CREDENTIAL &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d48de-148">CREATE CREDENTIAL &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-credential-transact-sql)  
  
-   [<span data-ttu-id="d48de-149">sp_add_proxy &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="d48de-149">sp_add_proxy &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-proxy-transact-sql)  
  
-   [<span data-ttu-id="d48de-150">sp_grant_proxy_to_subsystem &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="d48de-150">sp_grant_proxy_to_subsystem &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-grant-proxy-to-subsystem-transact-sql)  
  
  
