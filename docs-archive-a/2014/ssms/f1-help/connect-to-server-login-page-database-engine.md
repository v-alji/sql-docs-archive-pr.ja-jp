---
title: '[サーバーへの接続] ([ログイン] ページ) (データベース エンジン) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttosqlserver.login.f1
ms.assetid: e08cfbc3-bed5-4401-a13b-1c66d902fe32
author: stevestein
ms.author: sstein
ms.openlocfilehash: 665a5c491b0bea1145c60d15f1006de97281a30d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717259"
---
# <a name="connect-to-server-login-page-database-engine"></a><span data-ttu-id="44650-102">[サーバーへの接続] ([ログイン] ページ) (データベース エンジン)</span><span class="sxs-lookup"><span data-stu-id="44650-102">Connect to Server (Login Page) Database Engine</span></span>
  <span data-ttu-id="44650-103">このタブを使用すると、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] に接続するときのオプションを表示または指定できます。</span><span class="sxs-lookup"><span data-stu-id="44650-103">Use this tab to view or specify options when connecting to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="44650-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証で接続するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証モードと Windows 認証モードで構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="44650-104">To connect with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be configured in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows Authentication mode.</span></span> <span data-ttu-id="44650-105">認証モードの決定方法と認証モードの変更方法の詳細については、「[サーバーの認証モードの変更](../../database-engine/configure-windows/change-server-authentication-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="44650-105">For more information about how to determine the authentication mode and to change the authentication mode, see [Change Server Authentication Mode](../../database-engine/configure-windows/change-server-authentication-mode.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="44650-106">Options</span><span class="sxs-lookup"><span data-stu-id="44650-106">Options</span></span>  
 <span data-ttu-id="44650-107">**サーバーの種類**</span><span class="sxs-lookup"><span data-stu-id="44650-107">**Server type**</span></span>  
 <span data-ttu-id="44650-108">オブジェクト エクスプローラーからサーバーを登録するときに、接続するサーバーの種類 ( [!INCLUDE[ssDE](../../includes/ssde-md.md)]、Analysis Services、Reporting Services、または Integration Services) を選択します。</span><span class="sxs-lookup"><span data-stu-id="44650-108">When registering a server from Object Explorer, select the type of server to connect to: [!INCLUDE[ssDE](../../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services.</span></span> <span data-ttu-id="44650-109">ダイアログ ボックスのその他の領域には、選択したサーバーの種類に該当するオプションだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="44650-109">The rest of the dialog box shows only the options that apply to the selected server type.</span></span> <span data-ttu-id="44650-110">[登録済みサーバー] を使用してサーバーを登録する場合、 **[サーバーの種類]** ボックスは読み取り専用になり、[登録済みサーバー] コンポーネントに表示されているサーバーの種類と一致する値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="44650-110">When registering a server from Registered Servers, the **Server type** box is read-only, and matches the type of server displayed in the Registered Servers component.</span></span> <span data-ttu-id="44650-111">別の種類のサーバーを登録するには、新しいサーバーの登録を開始する前に、[登録済みサーバー] ツール バーの [ [!INCLUDE[ssDE](../../includes/ssde-md.md)]]、[Analysis Services]、[Reporting Services]、または [Integration Services] を選択します。</span><span class="sxs-lookup"><span data-stu-id="44650-111">To register a different type of server, select [!INCLUDE[ssDE](../../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services from the Registered Servers toolbar before starting to register a new server.</span></span>  
  
 <span data-ttu-id="44650-112">[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] を通じて [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース エンジンのインスタンスに接続する場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用し、 **[サーバーへの接続]** ダイアログ ボックスの **[接続プロパティ]** タブでデータベースを指定する必要があります。 **[暗号化接続]** チェック ボックスがオンになっていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="44650-112">When connecting to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine through [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], you must use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication and specify a database in the **Connect to Server** dialog box, on the **Connection Properties** tab. Ensure that you select the **Encrypt connection** checkbox.</span></span>  
  
 <span data-ttu-id="44650-113">既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は **master**に接続されます。</span><span class="sxs-lookup"><span data-stu-id="44650-113">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connects to **master**.</span></span> <span data-ttu-id="44650-114">ユーザー データベースを指定すると、オブジェクト エクスプローラーにそのデータベースとそのオブジェクトのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="44650-114">If you specify a user database, you will only see that database and its objects in Object Explorer.</span></span> <span data-ttu-id="44650-115">**master**に接続すると、すべてのデータベースを表示できるようになります。</span><span class="sxs-lookup"><span data-stu-id="44650-115">If you connect to **master**, you will be able to see all databases.</span></span> <span data-ttu-id="44650-116">詳細については、「 [Azure SQL Database の概要](/azure/sql-database/sql-database-technical-overview)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="44650-116">For more information, see the [Azure SQL Database Overview](/azure/sql-database/sql-database-technical-overview).</span></span>  
  
 <span data-ttu-id="44650-117">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="44650-117">**Server name**</span></span>  
 <span data-ttu-id="44650-118">接続するサーバー インスタンスを選択します。</span><span class="sxs-lookup"><span data-stu-id="44650-118">Select the server instance to connect to.</span></span> <span data-ttu-id="44650-119">既定では、最後に接続していたサーバー インスタンスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="44650-119">The server instance last connected to is displayed by default.</span></span>  
  
 <span data-ttu-id="44650-120">**認証**</span><span class="sxs-lookup"><span data-stu-id="44650-120">**Authentication**</span></span>  
 <span data-ttu-id="44650-121">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続する際には、2 つの認証モードのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="44650-121">Two authentication modes are available when connecting to an instance of [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
 <span data-ttu-id="44650-122">[!INCLUDE[ssSDS](../../includes/sssds-md.md)] を通じて [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース エンジンのインスタンスに接続する場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用し、 **[サーバーへの接続]** ダイアログ ボックスの **[接続プロパティ]** タブでデータベースを指定する必要があります。 **[暗号化接続]** チェック ボックスがオンになっていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="44650-122">When connecting to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine through [!INCLUDE[ssSDS](../../includes/sssds-md.md)], you must use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication and specify a database in the **Connect to Server** dialog box, on the **Connection Properties** tab. Ensure that you select the **Encrypt connection** checkbox.</span></span>  
  
 <span data-ttu-id="44650-123">既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は **master**に接続されます。</span><span class="sxs-lookup"><span data-stu-id="44650-123">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connects to **master**.</span></span> <span data-ttu-id="44650-124">ユーザー データベースを指定すると、オブジェクト エクスプローラーにそのデータベースとそのオブジェクトのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="44650-124">If you specify a user database, you will only see that database and its objects in Object Explorer.</span></span> <span data-ttu-id="44650-125">**master**に接続すると、すべてのデータベースを表示できるようになります。</span><span class="sxs-lookup"><span data-stu-id="44650-125">If you connect to **master**, you will be able to see all databases.</span></span> <span data-ttu-id="44650-126">詳細については、「 [Azure SQL Database の概要](/azure/sql-database/sql-database-technical-overview)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="44650-126">For more information, see the [Azure SQL Database Overview](/azure/sql-database/sql-database-technical-overview).</span></span>  
  
 <span data-ttu-id="44650-127">**Windows 認証モード ([Windows 認証])**</span><span class="sxs-lookup"><span data-stu-id="44650-127">**Windows Authentication Mode (Windows Authentication)**</span></span>  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="44650-128">Windows 認証モードを使用すると、ユーザーは Windows ユーザー アカウントを使用して接続できます。</span><span class="sxs-lookup"><span data-stu-id="44650-128">Windows Authentication mode allows a user to connect through a Windows user account.</span></span>  
  
 <span data-ttu-id="44650-129">**SQL Server 認証**</span><span class="sxs-lookup"><span data-stu-id="44650-129">**SQL Server Authentication**</span></span>  
 <span data-ttu-id="44650-130">指定されたログイン名とパスワードを使用して、信頼関係の低い接続から接続した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン アカウントが設定されているかどうか、指定されたパスワードが以前に記録されたパスワードと一致しているかどうかを確認することで認証を行います。</span><span class="sxs-lookup"><span data-stu-id="44650-130">When a user connects with a specified login name and password from a non-trusted connection, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs the authentication itself by checking to see if a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login account has been set up and if the specified password matches the one previously recorded.</span></span> <span data-ttu-id="44650-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にログイン アカウントが設定されていない場合、認証は失敗し、エラー メッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="44650-131">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not have a login account set, authentication fails, and the user receives an error message.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="44650-132">可能な場合は、Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="44650-132">When possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="44650-133">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="44650-133">**User name**</span></span>  
 <span data-ttu-id="44650-134">接続に使用するユーザー名を入力します。</span><span class="sxs-lookup"><span data-stu-id="44650-134">Enter the user name to connect with.</span></span> <span data-ttu-id="44650-135">このオプションは、Windows 認証を使用した接続を選択した場合のみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="44650-135">This option is only available if you have selected to connect using Windows Authentication.</span></span>  
  
 <span data-ttu-id="44650-136">**Login**</span><span class="sxs-lookup"><span data-stu-id="44650-136">**Login**</span></span>  
 <span data-ttu-id="44650-137">接続に使用するログインを入力します。</span><span class="sxs-lookup"><span data-stu-id="44650-137">Enter the login to connect with.</span></span> <span data-ttu-id="44650-138">このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用した接続が指定されている場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="44650-138">This option is only available if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="44650-139">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="44650-139">**Password**</span></span>  
 <span data-ttu-id="44650-140">ログインのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="44650-140">Enter the password for the login.</span></span> <span data-ttu-id="44650-141">このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用した接続を選択した場合のみ編集できます。</span><span class="sxs-lookup"><span data-stu-id="44650-141">This option is only editable if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="44650-142">**パスワードの記録**</span><span class="sxs-lookup"><span data-stu-id="44650-142">**Remember password**</span></span>  
 <span data-ttu-id="44650-143">入力したパスワードを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に記憶させるには、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="44650-143">Click to have [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] store the password you have entered.</span></span> <span data-ttu-id="44650-144">このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用した接続を選択した場合だけ表示されます。</span><span class="sxs-lookup"><span data-stu-id="44650-144">This option is only displayed if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="44650-145">**のインスタンスに接続するときには、**</span><span class="sxs-lookup"><span data-stu-id="44650-145">**Connect**</span></span>  
 <span data-ttu-id="44650-146">クリックすると、上記で選択したサーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="44650-146">Click to connect to the server selected above.</span></span>  
  
 <span data-ttu-id="44650-147">**Options**</span><span class="sxs-lookup"><span data-stu-id="44650-147">**Options**</span></span>  
 <span data-ttu-id="44650-148">クリックすると、ダイアログ ボックスが切り替わり、パスワードの保存などの追加のサーバー接続オプションが非表示になります。</span><span class="sxs-lookup"><span data-stu-id="44650-148">Click to change the dialog box and hide the additional server connection options, such as remembering the password.</span></span>  
  
  
