---
title: 中央管理サーバーとグループを作成する
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- configuration server
ms.assetid: da265482-3953-440a-ac23-0ab7e42a55eb
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f53b75966a14dbc6fd6cdc9bea0929ccac7780c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711529"
---
# <a name="create-a-central-management-server-and-server-group-sql-server-management-studio"></a><span data-ttu-id="1d794-102">中央管理サーバーとサーバー グループの作成 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="1d794-102">Create a Central Management Server and Server Group (SQL Server Management Studio)</span></span>
  <span data-ttu-id="1d794-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のインスタンスを [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]の中央管理サーバーとして指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1d794-103">This topic describes how to designate an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as a central management server in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="1d794-104">中央管理サーバーには、1 つ以上の中央管理サーバー グループに編成される [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの一覧が格納されます。</span><span class="sxs-lookup"><span data-stu-id="1d794-104">Central management servers store a list of instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is organized into one or more central management server groups.</span></span> <span data-ttu-id="1d794-105">中央管理サーバー グループを使用して実行したアクションは、サーバー グループ内のすべてのサーバーに影響します。</span><span class="sxs-lookup"><span data-stu-id="1d794-105">Actions that are taken by using a central management server group act on all servers in the server group.</span></span> <span data-ttu-id="1d794-106">これには、オブジェクト エクスプローラーを使用したサーバーへの接続と、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントやポリシー ベースの管理ポリシーの複数サーバーでの同時実行が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1d794-106">This includes connecting to servers by using Object Explorer and executing [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and Policy-Based Management policies on multiple servers at the same time.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1d794-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] よりも前のバージョンの [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] では、中央管理サーバーを指定できません。</span><span class="sxs-lookup"><span data-stu-id="1d794-107">Versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are earlier than [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] cannot be designated as a central management server.</span></span>  
  
 <span data-ttu-id="1d794-108">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="1d794-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1d794-109">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="1d794-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1d794-110">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="1d794-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1d794-111">**中央管理サーバーおよびサーバー グループを作成するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="1d794-111">**To create a Central Management Server and Server Group, using:**</span></span>  
  
     [<span data-ttu-id="1d794-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1d794-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1d794-113">はじめに</span><span class="sxs-lookup"><span data-stu-id="1d794-113">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1d794-114">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="1d794-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1d794-115">Permissions</span><span class="sxs-lookup"><span data-stu-id="1d794-115">Permissions</span></span>  
 <span data-ttu-id="1d794-116">中央管理サーバーへのアクセスは、msdb データベースの 2 つのデータベース ロールによって許可されます。</span><span class="sxs-lookup"><span data-stu-id="1d794-116">Two database roles in the msdb database grant access to central management servers.</span></span> <span data-ttu-id="1d794-117">中央管理サーバーを管理できるのは、ServerGroupAdministratorRole ロールのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="1d794-117">Only members of the ServerGroupAdministratorRole role can manage the central management server.</span></span> <span data-ttu-id="1d794-118">中央管理サーバーに接続するには、ServerGroupReaderRole ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="1d794-118">Membership in the ServerGroupReaderRole role is required to connect to a central management server.</span></span>  
  
 <span data-ttu-id="1d794-119">中央管理サーバーによって保持される接続は、ユーザーのコンテキスト内で Windows 認証を使用して実行されるため、登録済みサーバーでの有効な権限が変わることがあります。</span><span class="sxs-lookup"><span data-stu-id="1d794-119">Because the connections that are maintained by a central management server execute in the context of the user, by using Windows Authentication, the effective permissions on the registered servers might vary.</span></span> <span data-ttu-id="1d794-120">たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] A のインスタンスでは sysadmin 固定サーバー ロールのメンバーであるユーザーでも、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] B のインスタンスでは権限が限られていることがあります。</span><span class="sxs-lookup"><span data-stu-id="1d794-120">For example, the user might be a member of the sysadmin fixed server role on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] A, but have limited permissions on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] B.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1d794-121">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="1d794-121">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="1d794-122">ここでは、以下の作業の手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="1d794-122">The following procedures describe how to perform the following steps.</span></span>  
  
1.  <span data-ttu-id="1d794-123">中央管理サーバーを作成する。</span><span class="sxs-lookup"><span data-stu-id="1d794-123">Create a central management server.</span></span>  
  
2.  <span data-ttu-id="1d794-124">中央管理サーバーに対してサーバー グループを 1 つ以上追加し、そのサーバー グループに登録済みサーバーを 1 つ以上追加する。</span><span class="sxs-lookup"><span data-stu-id="1d794-124">Add one or more server groups to the central management server and add one or more registered servers to the server groups.</span></span>  
  
#### <a name="create-a-central-management-server"></a><span data-ttu-id="1d794-125">中央管理サーバーを作成する</span><span class="sxs-lookup"><span data-stu-id="1d794-125">Create a central management server</span></span>  
  
1.  <span data-ttu-id="1d794-126">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 **[表示]** メニューの **[登録済みサーバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d794-126">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Registered Servers**.</span></span>  
  
2.  <span data-ttu-id="1d794-127">[登録済みサーバー] で、 **[データベース エンジン]** を展開して **[中央管理サーバー]** を右クリックし、 **[中央管理サーバーの登録]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d794-127">In Registered Servers, expand **Database Engine**, right-click **Central Management Servers**, and then  click **Register Central Management Server**.</span></span>  
  
3.  <span data-ttu-id="1d794-128">**[新規サーバーの登録]** ダイアログ ボックスで、ドロップダウン リストにあるサーバーから、中央管理サーバーにする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを選択します。</span><span class="sxs-lookup"><span data-stu-id="1d794-128">In the **New Server Registration** dialog box, select the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you want to become the central management server from the drop-down list of servers.</span></span> <span data-ttu-id="1d794-129">中央管理サーバーに対して Windows 認証を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1d794-129">You must use Windows Authentication for the central management server.</span></span>  
  
4.  <span data-ttu-id="1d794-130">**[登録済みサーバー]** で、サーバー名と説明 (省略可) を入力します。</span><span class="sxs-lookup"><span data-stu-id="1d794-130">In **Registered Server**, enter a server name and optional description.</span></span>  
  
5.  <span data-ttu-id="1d794-131">**[接続プロパティ]** タブで、ネットワークと接続のプロパティを確認または変更します。</span><span class="sxs-lookup"><span data-stu-id="1d794-131">From the **Connection Properties** tab, review or modifiy the network  and connection properties.</span></span> <span data-ttu-id="1d794-132">詳細については、「[[サーバーへの接続] &#40;[接続プロパティ] ページ&#41; データベース エンジン](../f1-help/connect-to-server-connection-properties-page-database-engine.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d794-132">For more information, see [Connect to Server &#40;Connection Properties Page&#41; Database Engine](../f1-help/connect-to-server-connection-properties-page-database-engine.md)</span></span>  
  
6.  <span data-ttu-id="1d794-133">**[テスト]** をクリックして接続をテストします。</span><span class="sxs-lookup"><span data-stu-id="1d794-133">Click **Test**, to test the connection.</span></span>  
  
7.  <span data-ttu-id="1d794-134">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d794-134">Click **Save**.</span></span> <span data-ttu-id="1d794-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが **[中央管理サーバー]** フォルダーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="1d794-135">The instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will appear under the **Central Management Servers** folder.</span></span>  
  
#### <a name="create-a-new-server-group-and-add-servers-to-the-group"></a><span data-ttu-id="1d794-136">新しいサーバー グループを作成し、グループにサーバーを追加する</span><span class="sxs-lookup"><span data-stu-id="1d794-136">Create a new server group and add servers to the group</span></span>  
  
1.  <span data-ttu-id="1d794-137">**[登録済みサーバー]** で、 **[中央管理サーバー]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="1d794-137">From **Registered Servers**, expand **Central Management Servers**.</span></span> <span data-ttu-id="1d794-138">上に挙げた手順で追加した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを右クリックし、 **[新しいサーバー グループ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1d794-138">Right-click the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] added in the procedure above and select **New Server Group**.</span></span>  
  
2.  <span data-ttu-id="1d794-139">**[新しいサーバー グループのプロパティ]** で、グループの名前と説明 (省略可) を入力します。</span><span class="sxs-lookup"><span data-stu-id="1d794-139">In **New Server Group Properties**, enter a group name and optional description.</span></span>  
  
3.  <span data-ttu-id="1d794-140">**[登録済みサーバー]** で、サーバー グループを右クリックし、 **[新規サーバーの登録]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d794-140">From **Registered Servers**, right-click the server group and click **New Server Registration**.</span></span>  
  
4.  <span data-ttu-id="1d794-141">[新規サーバーの登録] で、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを選択します。</span><span class="sxs-lookup"><span data-stu-id="1d794-141">From New Server Registration, select an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1d794-142">詳細については、「[新しい登録済みサーバーの作成 &#40;SQL Server Management Studio&#41;](create-a-new-registered-server-sql-server-management-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d794-142">For more information, see [Create a New Registered Server &#40;SQL Server Management Studio&#41;](create-a-new-registered-server-sql-server-management-studio.md).</span></span> <span data-ttu-id="1d794-143">必要に応じてサーバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="1d794-143">Add more servers as appropriate.</span></span>  
  
#### <a name="to-execute-queries-against-several-configuration-targets-at-the-same-time"></a><span data-ttu-id="1d794-144">複数の構成対象に対してクエリを同時に実行するには</span><span class="sxs-lookup"><span data-stu-id="1d794-144">To execute queries against several configuration targets at the same time</span></span>  
  
-   <span data-ttu-id="1d794-145">1 つの中央管理サーバー、1 つ以上のサーバー グループ、および 1 つ以上の登録済みサーバーを作成すると、グループ全体に対してクエリを同時に実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="1d794-145">After you create a central management server, one or more server groups, and one or more registered servers, you can execute queries against a whole group at the same time.</span></span> <span data-ttu-id="1d794-146">サーバー グループ内の複数サーバーで [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを同時に実行する方法の詳細については、「[複数のサーバーに対してステートメントを同時に実行する方法 &#40;SQL Server Management Studio&#41;](execute-statements-against-multiple-servers-simultaneously.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d794-146">For more information about how to execute [!INCLUDE[tsql](../../includes/tsql-md.md)] statements on the servers in a server group at the same time, see [Execute Statements Against Multiple Servers Simultaneously &#40;SQL Server Management Studio&#41;](execute-statements-against-multiple-servers-simultaneously.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d794-147">参照</span><span class="sxs-lookup"><span data-stu-id="1d794-147">See Also</span></span>  
 [<span data-ttu-id="1d794-148">中央管理サーバーを使用した複数のサーバーの管理</span><span class="sxs-lookup"><span data-stu-id="1d794-148">Administer Multiple Servers Using Central Management Servers</span></span>](../../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  
