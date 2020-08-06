---
title: リモート サーバー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- server management [SQL Server], remote servers
- remote servers [SQL Server], configuring
- remote servers [SQL Server]
- servers [SQL Server], remote
- remote access option
ms.assetid: abf0fa24-f199-4273-9a1a-e8787ac9bee1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1d42fc2ed6acd4e46e383c0a56afcc8a8b27d3aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641233"
---
# <a name="remote-servers"></a><span data-ttu-id="8a53d-102">リモート サーバー</span><span class="sxs-lookup"><span data-stu-id="8a53d-102">Remote Servers</span></span>
  <span data-ttu-id="8a53d-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、旧バージョンとの互換性を保つ目的でのみ、リモート サーバーがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="8a53d-103">Remote servers are supported in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for backward compatibility only.</span></span> <span data-ttu-id="8a53d-104">新しいアプリケーションでは、リモート サーバーではなく、リンク サーバーを使用してください。</span><span class="sxs-lookup"><span data-stu-id="8a53d-104">New applications should use linked servers instead.</span></span> <span data-ttu-id="8a53d-105">詳しくは、「 [リンク サーバー &#40;データベース エンジン&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a53d-105">For more information, see [Linked Servers &#40;Database Engine&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md).</span></span>  
  
 <span data-ttu-id="8a53d-106">リモート サーバーを構成することによって、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続しているクライアントは、新たに接続を確立することなく、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の別のインスタンスでストアド プロシージャを実行できます。</span><span class="sxs-lookup"><span data-stu-id="8a53d-106">A remote server configuration allows for a client connected to one instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to execute a stored procedure on another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] without establishing a separate connection.</span></span> <span data-ttu-id="8a53d-107">クライアントが接続するサーバーは、クライアントからの要求を受け、この要求をクライアントの代わりにリモート サーバーに送信します。</span><span class="sxs-lookup"><span data-stu-id="8a53d-107">Instead, the server to which the client is connected accepts the client request and sends the request to the remote server on behalf of the client.</span></span> <span data-ttu-id="8a53d-108">リモート サーバーが、要求を処理し、要求を行ったサーバーに結果を返します。</span><span class="sxs-lookup"><span data-stu-id="8a53d-108">The remote server processes the request and returns any results to the original server.</span></span> <span data-ttu-id="8a53d-109">結果を受け取ったサーバーは、結果をクライアントに渡します。</span><span class="sxs-lookup"><span data-stu-id="8a53d-109">This server in turn passes those results to the client.</span></span> <span data-ttu-id="8a53d-110">リモート サーバーを構成する場合は、セキュリティをどのように確立するかを検討する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="8a53d-110">When you set up a remote server configuration, you should also consider how to establish security.</span></span>  
  
 <span data-ttu-id="8a53d-111">サーバー構成を設定して、別のサーバー上のストアド プロシージャを実行できるようにする場合に、まだリモート サーバーを構成していない場合は、リモート サーバーの代わりにリンク サーバーを使用してください。</span><span class="sxs-lookup"><span data-stu-id="8a53d-111">If you want to set up a server configuration to execute stored procedures on another server and do not have existing remote server configurations, use linked servers instead of remote servers.</span></span> <span data-ttu-id="8a53d-112">リンク サーバーではストアド プロシージャと分散クエリの両方を使用できます。これに対して、リモート サーバーで使用できるのはストアド プロシージャだけです。</span><span class="sxs-lookup"><span data-stu-id="8a53d-112">Both stored procedures and distributed queries are allowed against linked servers; however, only stored procedures are allowed against remote servers.</span></span>  
  
## <a name="remote-server-details"></a><span data-ttu-id="8a53d-113">リモート サーバーの詳細</span><span class="sxs-lookup"><span data-stu-id="8a53d-113">Remote Server Details</span></span>  
 <span data-ttu-id="8a53d-114">リモート サーバーは、組で設定します。</span><span class="sxs-lookup"><span data-stu-id="8a53d-114">Remote servers are set up in pairs.</span></span> <span data-ttu-id="8a53d-115">1 組のリモート サーバーを設定するには、両方のサーバーが相互にリモート サーバーとして認識できるように構成します。</span><span class="sxs-lookup"><span data-stu-id="8a53d-115">To set up a pair of remote servers, configure both servers to recognize each other as remote servers.</span></span>  
  
 <span data-ttu-id="8a53d-116">通常は、リモート サーバーの構成オプションを設定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="8a53d-116">Most of the time, you should not have to set configuration options for remote servers.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8a53d-117">によって、ローカル コンピューターとリモート コンピューターの両方にリモート サーバー接続を可能にする既定値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="8a53d-117">Set sets the defaults on both the local and remote computers to allow for remote server connections.</span></span>  
  
 <span data-ttu-id="8a53d-118">リモート サーバー アクセスが機能するには、ローカルとリモートの両方のコンピューターで **remote access** 構成オプションが 1 に設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a53d-118">For remote server access to work, the **remote access** configuration option must be set to 1 on both the local and remote computers.</span></span> <span data-ttu-id="8a53d-119">(これは既定の設定です)。**remote access** は、リモート サーバーからのログインを制御するオプションです。</span><span class="sxs-lookup"><span data-stu-id="8a53d-119">(This is the default setting.)  **remote access** controls logins from remote servers.</span></span> <span data-ttu-id="8a53d-120">この構成オプションを再設定するには、[!INCLUDE[tsql](../../includes/tsql-md.md)] **sp_configure** ストアド プロシージャまたは [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="8a53d-120">You can reset this configuration option by using either the [!INCLUDE[tsql](../../includes/tsql-md.md)] **sp_configure** stored procedure or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="8a53d-121">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用してこのオプションを設定する場合は、 **[サーバーのプロパティ]** の [接続] ページで **[このサーバーへのリモート接続を許可する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="8a53d-121">To set the option in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **Server Properties Connections** page, use **Allow remote connections to this server**.</span></span> <span data-ttu-id="8a53d-122">**[サーバーのプロパティ]** の [接続] ページにアクセスするには、オブジェクト エクスプローラーでサーバー名を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a53d-122">To reach the **Server Properties Connections** page, in Object Explorer, right-click the server name, and then click **Properties**.</span></span> <span data-ttu-id="8a53d-123">**[サーバーのプロパティ]** ページで、 **[接続]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a53d-123">On the **Server Properties** page, click the **Connections** page.</span></span>  
  
 <span data-ttu-id="8a53d-124">ローカル サーバーからリモート サーバー構成を無効にすると、組になっているリモート サーバー上のユーザーはそのローカル サーバーにアクセスできなくなります。</span><span class="sxs-lookup"><span data-stu-id="8a53d-124">From the local server, you can disable a remote server configuration to prevent access to that local server by users on the remote server with which it is paired.</span></span>  
  
## <a name="security-for-remote-servers"></a><span data-ttu-id="8a53d-125">リモート サーバーのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="8a53d-125">Security for Remote Servers</span></span>  
 <span data-ttu-id="8a53d-126">リモート サーバーに対する RPC (リモート プロシージャ コール) を有効にするには、そのリモート サーバーでログイン マッピングを設定する必要があります。場合によっては、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスを実行しているローカル サーバーでの設定も必要になります。</span><span class="sxs-lookup"><span data-stu-id="8a53d-126">To enable remote procedure calls (RPC) against a remote server, you must set up login mappings on the remote server and possibly on the local server that is running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8a53d-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、RPC は既定で無効になっています。</span><span class="sxs-lookup"><span data-stu-id="8a53d-127">RPC is disabled by default in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8a53d-128">この構成により、攻撃可能な領域を減らしてサーバーのセキュリティを強化できます。</span><span class="sxs-lookup"><span data-stu-id="8a53d-128">This configuration enhances the security of your server by reducing its attackable surface area.</span></span> <span data-ttu-id="8a53d-129">RPC を使用する場合は、事前にこの機能を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a53d-129">Before using RPC you must enable this feature.</span></span> <span data-ttu-id="8a53d-130">詳細については、「 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a53d-130">For more information see [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql).</span></span>  
  
### <a name="setting-up-the-remote-server"></a><span data-ttu-id="8a53d-131">リモート サーバーのセットアップ</span><span class="sxs-lookup"><span data-stu-id="8a53d-131">Setting Up the Remote Server</span></span>  
 <span data-ttu-id="8a53d-132">リモート ログインのマッピングは、リモート サーバーで設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a53d-132">Remote login mappings must be set up on the remote server.</span></span> <span data-ttu-id="8a53d-133">リモート サーバーはこれらのマッピングを使用して、指定のサーバーから RPC 接続用に受信したログインをローカル ログインにマップします。</span><span class="sxs-lookup"><span data-stu-id="8a53d-133">Using these mappings, the remote server maps the incoming login for an RPC connection from a specified server to a local login.</span></span> <span data-ttu-id="8a53d-134">リモート ログインのマッピングは、リモート サーバーで **sp_addremotelogin** ストアド プロシージャを使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="8a53d-134">Remote login mappings can be set up by using the **sp_addremotelogin** stored procedure on the remote server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8a53d-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、 **sp_remoteoption** の **trusted** オプションがサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="8a53d-135">The **trusted** option of  **sp_remoteoption** is not supported in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
### <a name="setting-up-the-local-server"></a><span data-ttu-id="8a53d-136">ローカル サーバーのセットアップ</span><span class="sxs-lookup"><span data-stu-id="8a53d-136">Setting Up the Local Server</span></span>  
 <span data-ttu-id="8a53d-137">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証のローカル ログインの場合、ローカル サーバーでログインのマッピングを設定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="8a53d-137">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authenticated local logins, you do not have to set up a login mapping on the local server.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8a53d-138">によって、リモート サーバーへの接続にローカル ログインとパスワードが使用されます。</span><span class="sxs-lookup"><span data-stu-id="8a53d-138">uses the local login and password to connect to the remote server.</span></span> <span data-ttu-id="8a53d-139">Windows 認証のログインの場合は、ローカル ログインのマッピングをローカル サーバーで設定します。このマッピングでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスがリモート サーバーに RPC 接続する際に使用するログインとパスワードを定義します。</span><span class="sxs-lookup"><span data-stu-id="8a53d-139">For Windows authenticated logins, set up a local login mapping on a local server that defines what login and password are used by an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] when it makes an RPC connection to a remote server.</span></span>  
  
 <span data-ttu-id="8a53d-140">Windows 認証で作成されたログインの場合は、 **sp_addlinkedservlogin** ストアド プロシージャを使用して、ログイン名とパスワードへのマッピングを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a53d-140">For logins created by Windows Authentication, you must create a mapping to a login name and password by using the **sp_addlinkedservlogin** stored procedure.</span></span> <span data-ttu-id="8a53d-141">このログイン名とパスワードは、 **sp_addremotelogin**によって作成され、リモート サーバーが予期していた受信ログイン名とパスワードに一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a53d-141">This login name and password must match the incoming login and password expected by the remote server, as created by **sp_addremotelogin**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8a53d-142">可能な場合は、Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="8a53d-142">When possible, use Windows Authentication.</span></span>  
  
### <a name="remote-server-security-example"></a><span data-ttu-id="8a53d-143">リモート サーバーのセキュリティの例</span><span class="sxs-lookup"><span data-stu-id="8a53d-143">Remote Server Security Example</span></span>  
 <span data-ttu-id="8a53d-144">**serverSend** と **serverReceive** という [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストールがあるとします。</span><span class="sxs-lookup"><span data-stu-id="8a53d-144">Consider these [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installations: **serverSend** and **serverReceive**.</span></span> <span data-ttu-id="8a53d-145">**serverReceive** は、 **Sales_Mary**という **serverSend**からの受信ログインを、 **serverReceive** の **Alice** という [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証のログインにマップするように構成されています。</span><span class="sxs-lookup"><span data-stu-id="8a53d-145">**serverReceive** is configured to map an incoming login from **serverSend**, called **Sales_Mary**, to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authenticated login in **serverReceive**, called **Alice**.</span></span> <span data-ttu-id="8a53d-146">**serverSend**からの **Joe**という別の受信ログインは、 **serverReceive**_の_**Joe** という[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証のログインにマップされます。</span><span class="sxs-lookup"><span data-stu-id="8a53d-146">Another incoming login from **serverSend**, called **Joe**, is mapped to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authenticated login in **serverReceive**_,_ called **Joe**.</span></span>  
  
 <span data-ttu-id="8a53d-147">次の Transact-SQL コードの例では、 `serverSend` に対して RPC を実行するように `serverReceive`を構成しています。</span><span class="sxs-lookup"><span data-stu-id="8a53d-147">The following Transact-SQL code example configures `serverSend` to perform RPCs against `serverReceive`.</span></span>  
  
```  
--Create remote server entry for RPCs   
--from serverSend in serverReceive.  
EXEC sp_addserver 'serverSend';  
GO  
  
--Create remote login mapping for login 'Sales_Mary' from serverSend  
--to Alice.  
EXEC sp_addremotelogin 'serverSend', 'Alice', 'Sales_Mary';  
GO  
--Create remote login mapping for login Joe from serverReceive   
--to same login.  
--Assumes same password for Joe in both servers.  
EXEC sp_addremotelogin 'serverSend', 'Joe', 'Joe';  
GO  
```  
  
 <span data-ttu-id="8a53d-148">`serverSend`では、Windows 認証のログイン `Sales\Mary` をログイン `Sales_Mary`に変換するようにローカル ログインのマッピングが作成されます。</span><span class="sxs-lookup"><span data-stu-id="8a53d-148">On `serverSend`, a local login mapping is created for a Windows authenticated login `Sales\Mary` to a login `Sales_Mary`.</span></span> <span data-ttu-id="8a53d-149">`Joe`には `serverReceive` に対するマッピングがあり、既定では同じログイン名とパスワードが使用されるので、 `Joe`のローカル マッピングは不要です。</span><span class="sxs-lookup"><span data-stu-id="8a53d-149">No local mapping is required for `Joe`, because the default is to use the same login name and password, and `serverReceive` has a mapping for `Joe`.</span></span>  
  
```  
--Create a remote server entry for RPCs from serverReceive.  
EXEC sp_addserver 'serverReceive';  
GO  
--Create a local login mapping for the Windows authenticated login.  
--Sales\Mary to Sales_Mary. The password should match the  
--password for the login Sales_Mary in serverReceive.  
EXEC sp_addlinkedsrvlogin 'serverReceive', false, 'Sales\Mary',  
   'Sales_Mary', '430[fj%dk';  
GO  
```  
  
## <a name="viewing-local-or-remote-server-properties"></a><span data-ttu-id="8a53d-150">ローカル サーバーまたはリモート サーバーのプロパティの表示</span><span class="sxs-lookup"><span data-stu-id="8a53d-150">Viewing Local or Remote Server Properties</span></span>  
 <span data-ttu-id="8a53d-151">**xp_msver** 拡張ストアド プロシージャを使用すると、ローカル サーバーまたはリモート サーバーのサーバー属性を確認できます。</span><span class="sxs-lookup"><span data-stu-id="8a53d-151">You can use the **xp_msver** extended stored procedure to review server attributes for local or remote servers.</span></span> <span data-ttu-id="8a53d-152">これらの属性には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のバージョン番号、コンピューターのプロセッサの種類と数、およびオペレーティング システムのバージョンが格納されています。</span><span class="sxs-lookup"><span data-stu-id="8a53d-152">These attributes include the version number of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the type and number of processors in the computer, and the version of the operating system.</span></span> <span data-ttu-id="8a53d-153">リモート サーバーのデータベース、ファイル、ログイン、およびツールを、ローカル サーバーで表示できます。</span><span class="sxs-lookup"><span data-stu-id="8a53d-153">From the local server, you can view databases, files, logins, and tools for a remote server.</span></span> <span data-ttu-id="8a53d-154">詳細については、「[xp_msver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/xp-msver-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a53d-154">For more information, see [xp_msver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/xp-msver-transact-sql).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="8a53d-155">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="8a53d-155">Related Tasks</span></span>  
 [<span data-ttu-id="8a53d-156">リンク サーバー &#40;データベース エンジン&#41;</span><span class="sxs-lookup"><span data-stu-id="8a53d-156">Linked Servers &#40;Database Engine&#41;</span></span>](../../relational-databases/linked-servers/linked-servers-database-engine.md)  
  
## <a name="related-content"></a><span data-ttu-id="8a53d-157">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="8a53d-157">Related Content</span></span>  
 [<span data-ttu-id="8a53d-158">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8a53d-158">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
 [<span data-ttu-id="8a53d-159">remote access サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="8a53d-159">Configure the remote access Server Configuration Option</span></span>](configure-the-remote-access-server-configuration-option.md)  
  
 [<span data-ttu-id="8a53d-160">RECONFIGURE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8a53d-160">RECONFIGURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
