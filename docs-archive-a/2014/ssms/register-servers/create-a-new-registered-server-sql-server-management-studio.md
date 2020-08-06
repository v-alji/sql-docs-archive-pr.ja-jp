---
title: 新しい登録済みサーバーの作成
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.registerserver.general.sqlce.f1
- sql12.swb.registerserver.general.sqlserver.f1
helpviewer_keywords:
- Registered Servers [SQL Server], creating new registered servers
ms.assetid: 716ea070-a3b5-4514-9de2-82ce8a96514b
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 43cdb06179531a739f6595dc5ade9eeb79ea65ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630763"
---
# <a name="create-a-new-registered-server-sql-server-management-studio"></a><span data-ttu-id="8c4e8-102">新しい登録済みサーバーの作成 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="8c4e8-102">Create a New Registered Server (SQL Server Management Studio)</span></span>
  <span data-ttu-id="8c4e8-103">このトピックでは、サーバーを [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]の 登録済みサーバー コンポーネントに登録することによって、頻繁にアクセスするサーバーの接続情報を保存する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-103">This topic describes how to save the connection information for servers that you access frequently, by registering the server in the Registered Servers component of [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="8c4e8-104">サーバーの登録は、接続する前か、またはオブジェクト エクスプローラーから接続するときに実行できます。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-104">A server can be registered before connecting, or when connecting from Object Explorer.</span></span> <span data-ttu-id="8c4e8-105">ローカル コンピューターのサーバー インスタンスを登録するには、特殊なメニュー オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-105">There is a special menu option to register the server instances on the local computer.</span></span>  
  
 <span data-ttu-id="8c4e8-106">登録済みサーバーには、次の 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-106">There are two kinds of registered servers:</span></span>  
  
-   <span data-ttu-id="8c4e8-107">ローカル サーバー グループ</span><span class="sxs-lookup"><span data-stu-id="8c4e8-107">Local server groups</span></span>  
  
     <span data-ttu-id="8c4e8-108">ローカル サーバー グループを使用すると、管理頻度の高いサーバーに簡単に接続できます。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-108">Use local server groups to easily connect to servers that you frequently manage.</span></span> <span data-ttu-id="8c4e8-109">ローカル サーバーとローカル以外のサーバーは、どちらもローカル サーバー グループに登録されます。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-109">Both local and non-local servers are registered into local server groups.</span></span> <span data-ttu-id="8c4e8-110">ローカル サーバー グループは各ユーザーに固有です。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-110">Local server groups are unique to each user.</span></span> <span data-ttu-id="8c4e8-111">登録済みサーバーの情報を共有する方法については、「 [登録済みサーバー情報のエクスポート &#40;SQL Server Management Studio&#41;](export-registered-server-information-sql-server-management-studio.md) 」および「 [登録済みサーバー情報のインポート &#40;SQL Server Management Studio&#41;](import-registered-server-information-sql-server-management-studio.md)の 登録済みサーバー コンポーネントに登録することによって、頻繁にアクセスするサーバーの接続情報を保存する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-111">For information about how to share registered server information, see [Export Registered Server Information &#40;SQL Server Management Studio&#41;](export-registered-server-information-sql-server-management-studio.md) and [Import Registered Server Information &#40;SQL Server Management Studio&#41;](import-registered-server-information-sql-server-management-studio.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8c4e8-112">可能な限り Windows 認証を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-112">We recommend that you use Windows Authentication whenever possible.</span></span>  
  
-   <span data-ttu-id="8c4e8-113">中央管理サーバー</span><span class="sxs-lookup"><span data-stu-id="8c4e8-113">Central Management Servers</span></span>  
  
     <span data-ttu-id="8c4e8-114">サーバー登録は、ファイル システムではなく中央管理サーバーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-114">Central Management Servers store server registrations in the Central Management Server instead of on the file system.</span></span> <span data-ttu-id="8c4e8-115">中央管理サーバーおよび従属登録済みサーバーは、Windows 認証を使用しないと登録できません。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-115">Central Management Servers and subordinate registered servers can be registered only by using Windows Authentication.</span></span> <span data-ttu-id="8c4e8-116">中央管理サーバーを登録すると、そのサーバーに関連する登録済みサーバーが自動的に表示されます。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-116">After a Central Management Server has been registered, its associated registered servers will be automatically displayed.</span></span> <span data-ttu-id="8c4e8-117">中央管理サーバーの詳細については、「 [中央管理サーバーを使用した複数のサーバーの管理](../../relational-databases/administer-multiple-servers-using-central-management-servers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-117">For more information about Central Management Servers, see [Administer Multiple Servers Using Central Management Servers](../../relational-databases/administer-multiple-servers-using-central-management-servers.md).</span></span> <span data-ttu-id="8c4e8-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] よりも前のバージョンの [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] では、中央管理サーバーを指定できません。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-118">Versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are earlier than [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] cannot be designated as a Central Management Server.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8c4e8-119">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="8c4e8-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-automatically-register-the-local-server-instances"></a><span data-ttu-id="8c4e8-120">ローカル サーバー インスタンスを自動的に登録するには</span><span class="sxs-lookup"><span data-stu-id="8c4e8-120">To automatically register the local server instances</span></span>  
  
-   <span data-ttu-id="8c4e8-121">[登録済みサーバー] で、[登録済みサーバー] ツリーの任意のノードを右クリックし、 **[ローカル サーバーの登録情報を更新]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-121">In Registered Servers, right-click any node in the Registered Servers tree, and then click **Update Local Server Registration**.</span></span>  
  
#### <a name="to-create-a-new-registered-server"></a><span data-ttu-id="8c4e8-122">新しい登録済みサーバーを作成するには</span><span class="sxs-lookup"><span data-stu-id="8c4e8-122">To create a new registered server</span></span>  
  
1.  <span data-ttu-id="8c4e8-123">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で [登録済みサーバー] が表示されていない場合は、 **[表示]** メニューの **[登録済みサーバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-123">If Registered Servers is not visible in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Registered Servers**.</span></span>  
  
     <span data-ttu-id="8c4e8-124">**サーバーの種類**</span><span class="sxs-lookup"><span data-stu-id="8c4e8-124">**Server type**</span></span>  
     <span data-ttu-id="8c4e8-125">[登録済みサーバー] を使用してサーバーを登録する場合、 **[サーバーの種類]** ボックスは読み取り専用になり、[登録済みサーバー] ペインに表示されているサーバーの種類と一致する値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-125">When a server is registered from Registered Servers, the **Server type** box is read-only, and matches the type of server displayed in the Registered Servers pane.</span></span> <span data-ttu-id="8c4e8-126">別の種類のサーバーを登録するには、新しいサーバーの登録を開始する前に、 **[登録済みサーバー]** ツール バーの **[データベース エンジン]** 、 **[分析サーバー]** 、 **[Reporting Services]** 、または **[Integration Services]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-126">To register a different type of server, click **Database Engine**, **Analysis Server**, **Reporting Services**, or **Integration Services** on the **Registered Servers** toolbar before starting to register a new server.</span></span>  
  
     <span data-ttu-id="8c4e8-127">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="8c4e8-127">**Server name**</span></span>  
     <span data-ttu-id="8c4e8-128">登録するサーバーインスタンスを [] という形式で選択し *\<servername>* \\ *\<instancename>* ます。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-128">Select the server instance to register in the format: *\<servername>*[\\*\<instancename>*].</span></span>  
  
     <span data-ttu-id="8c4e8-129">**認証**</span><span class="sxs-lookup"><span data-stu-id="8c4e8-129">**Authentication**</span></span>  
     <span data-ttu-id="8c4e8-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続する際には、2 つの認証モードのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-130">Two authentication modes are available when connecting to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="8c4e8-131">**[Windows 認証]**</span><span class="sxs-lookup"><span data-stu-id="8c4e8-131">**Windows Authentication**</span></span>  
     <span data-ttu-id="8c4e8-132">Windows 認証モードを使用すると、ユーザーは [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ユーザー アカウントを使用して接続できます。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-132">Windows Authentication mode allows a user to connect through a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows user account.</span></span>  
  
     <span data-ttu-id="8c4e8-133">**SQL Server 認証**</span><span class="sxs-lookup"><span data-stu-id="8c4e8-133">**SQL Server Authentication**</span></span>  
     <span data-ttu-id="8c4e8-134">指定されたログイン名とパスワードを使用して、信頼関係の低い接続から接続した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン アカウントが設定されているかどうか、指定されたパスワードが以前に記録されたパスワードと一致しているかどうかを確認することで認証を行います。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-134">When a user connects with a specified login name and password from a nontrusted connection, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs the authentication itself by checking whether a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login account has been set up and whether the specified password matches the one previously recorded.</span></span> <span data-ttu-id="8c4e8-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にログイン アカウントが設定されていない場合、認証は失敗し、エラー メッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-135">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not have a login account set, authentication fails, and the user receives an error message.</span></span>  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)] <span data-ttu-id="8c4e8-136">詳細については、「 [認証モードの選択](../../relational-databases/security/choose-an-authentication-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-136">For more information, see [Choose an Authentication Mode](../../relational-databases/security/choose-an-authentication-mode.md).</span></span>  
  
     <span data-ttu-id="8c4e8-137">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="8c4e8-137">**User name**</span></span>  
     <span data-ttu-id="8c4e8-138">接続に使用されている、現在のユーザー名を表示します。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-138">Shows the current user name you are connecting with.</span></span> <span data-ttu-id="8c4e8-139">この読み取り専用オプションは、Windows 認証を使用した接続が指定されている場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-139">This read-only option is only available if you have selected to connect using Windows Authentication.</span></span> <span data-ttu-id="8c4e8-140">**[ユーザー名]** を変更するには、別のユーザーとしてコンピューターにログインします。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-140">To change **User names**, log in to the computer as a different user.</span></span>  
  
     <span data-ttu-id="8c4e8-141">**Login**</span><span class="sxs-lookup"><span data-stu-id="8c4e8-141">**Login**</span></span>  
     <span data-ttu-id="8c4e8-142">接続に使用するログインを入力します。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-142">Enter the login to connect with.</span></span> <span data-ttu-id="8c4e8-143">このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用した接続を選択した場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-143">This option is available only if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
     <span data-ttu-id="8c4e8-144">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="8c4e8-144">**Password**</span></span>  
     <span data-ttu-id="8c4e8-145">ログインのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-145">Enter the password for the login.</span></span> <span data-ttu-id="8c4e8-146">このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用した接続を選択した場合にのみ編集できます。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-146">This option can be edited only if you have selected to connect by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
     <span data-ttu-id="8c4e8-147">**[パスワードを保存する]**</span><span class="sxs-lookup"><span data-stu-id="8c4e8-147">**Remember password**</span></span>  
     <span data-ttu-id="8c4e8-148">入力したパスワードを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で暗号化して保存する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-148">Select to have [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] encrypt and store the password you have entered.</span></span> <span data-ttu-id="8c4e8-149">このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用した接続を選択した場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-149">This option is displayed only if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8c4e8-150">パスワードの保存を止めるには、このチェック ボックスをオフにして **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-150">If you have stored the password and want to stop storing it, clear this check box, and then click **Save**.</span></span>  
  
     <span data-ttu-id="8c4e8-151">**[登録済みサーバーの名前]**</span><span class="sxs-lookup"><span data-stu-id="8c4e8-151">**Registered server name**</span></span>  
     <span data-ttu-id="8c4e8-152">[登録済みサーバー] に表示する名前です。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-152">The name you want to appear in Registered Servers.</span></span> <span data-ttu-id="8c4e8-153">この名前は、 **[サーバー名]** ボックスの名前と一致する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-153">This name does not have to match the **Server name** box.</span></span>  
  
     <span data-ttu-id="8c4e8-154">**[登録済みサーバーの説明]**</span><span class="sxs-lookup"><span data-stu-id="8c4e8-154">**Registered server description**</span></span>  
     <span data-ttu-id="8c4e8-155">サーバーの説明をオプションで入力します。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-155">Enter an optional description of the server.</span></span>  
  
     <span data-ttu-id="8c4e8-156">**テスト**</span><span class="sxs-lookup"><span data-stu-id="8c4e8-156">**Test**</span></span>  
     <span data-ttu-id="8c4e8-157">クリックすると、 **[サーバー名]** で選択されたサーバーへの接続をテストします。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-157">Click to test the connection to the server selected in **Server name**.</span></span>  
  
     <span data-ttu-id="8c4e8-158">**および**</span><span class="sxs-lookup"><span data-stu-id="8c4e8-158">**Save**</span></span>  
     <span data-ttu-id="8c4e8-159">クリックすると、登録済みサーバーの設定を保存します。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-159">Click to save the registered server settings.</span></span>  
  
## <a name="multiserver-queries"></a><span data-ttu-id="8c4e8-160">マルチサーバー クエリ</span><span class="sxs-lookup"><span data-stu-id="8c4e8-160">Multiserver Queries</span></span>  
 <span data-ttu-id="8c4e8-161">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のクエリ エディター ウィンドウを使用すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の複数のインスタンスに同時に接続してクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-161">The Query Editor window in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] can connect to and query multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] at the same time.</span></span> <span data-ttu-id="8c4e8-162">クエリから返された結果は、マージして 1 つの結果ペインに表示することも、別々の結果ペインに表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-162">The results that are returned by the query can be merged into a single results pane, or they can be returned in separate results panes.</span></span> <span data-ttu-id="8c4e8-163">クエリ エディターには、各行を生成したサーバーの名前と、各行を提供したサーバーへの接続に使用されたログインを表示する列をオプションで追加できます。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-163">As an option, Query Editor can include columns that provide the name of the server that produced each row, and also the login that was used to connect to the server that provided each row.</span></span> <span data-ttu-id="8c4e8-164">マルチサーバー クエリを実行する方法については、「[複数のサーバーに対してステートメントを同時に実行する方法 &#40;SQL Server Management Studio&#41;](execute-statements-against-multiple-servers-simultaneously.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-164">For more information about how to execute multiserver queries, see [Execute Statements Against Multiple Servers Simultaneously &#40;SQL Server Management Studio&#41;](execute-statements-against-multiple-servers-simultaneously.md).</span></span>  
  
 <span data-ttu-id="8c4e8-165">ローカル サーバー グループ内のすべてのサーバーに対してクエリを実行するには、サーバー グループを右クリックし、 **[接続]** をポイントして、 **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-165">To execute queries against all the servers in a local server group, right-click the server group, point to click **Connect**, and then click **New Query**.</span></span> <span data-ttu-id="8c4e8-166">新しいクエリ エディター ウィンドウで実行したクエリは、ユーザー認証コンテキストなど保存されている接続情報を使用して、グループ内のすべてのサーバーに対して実行されます。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-166">When queries are executed in the new Query Editor window, they will execute against all servers in the group, using the stored connection information including the user authentication context.</span></span> <span data-ttu-id="8c4e8-167">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用して登録されていても、パスワードが保存されていないサーバーは接続できません。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-167">Servers registered by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication but not saving the password will fail to connect.</span></span>  
  
 <span data-ttu-id="8c4e8-168">中央管理サーバーに登録されているすべてのサーバーに対してクエリを実行するには、中央管理サーバーを展開し、サーバー グループを右クリックして、 **[接続]** をポイントし、 **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-168">To execute queries against all the servers that are registered with a Central Management Server, expand the Central Management Server, right-click the server group, point to click **Connect**, and then click **New Query**.</span></span> <span data-ttu-id="8c4e8-169">新しいクエリ エディター ウィンドウで実行したクエリは、保存されている接続情報およびユーザーの Windows 認証コンテキストを使用して、サーバー グループ内のすべてのサーバーに対して実行されます。</span><span class="sxs-lookup"><span data-stu-id="8c4e8-169">When queries are executed in the new Query Editor window, they will execute against all of the servers in the server group, using the stored connection information and using the Windows Authentication context of the user.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c4e8-170">参照</span><span class="sxs-lookup"><span data-stu-id="8c4e8-170">See Also</span></span>  
 <span data-ttu-id="8c4e8-171">[オブジェクト エクスプローラーのシステム オブジェクトの非表示](../object/hide-system-objects-in-object-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="8c4e8-171">[Hide System Objects in Object Explorer](../object/hide-system-objects-in-object-explorer.md) </span></span>  
 <span data-ttu-id="8c4e8-172">[登録済みサーバー情報のエクスポート &#40;SQL Server Management Studio&#41;](export-registered-server-information-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="8c4e8-172">[Export Registered Server Information &#40;SQL Server Management Studio&#41;](export-registered-server-information-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="8c4e8-173">登録済みサーバー情報のインポート &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="8c4e8-173">Import Registered Server Information &#40;SQL Server Management Studio&#41;</span></span>](import-registered-server-information-sql-server-management-studio.md)  
  
  
